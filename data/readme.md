"""

<img width="1638" height="433" alt="image" src="https://github.com/user-attachments/assets/310d22ce-3e24-47d5-86bc-e895639f69c2" />
I want to only call this tab "data".

"""
If you came here straight after the introduction, welcome. If you skipped ahead to the alphas first, you did exactly what I expected and hoped you wouldn't. Why? Because data is your bedrock. It is the most important piece of any quant or algorithmic pipeline: you build your ideas from it, and you trade on it.

## Start with what you can trade

I understand, like any bloke, that the scientific method starts with a hypothesis. You can do that here too, but then you have to go and find data that matches your idea. In trading it mostly runs the other way round. We are not truly scientists, we are business people: we look at what we *can* trade and then look for ideas in it.

Here is a genuine example.

1. I am a small backroom trader with $100. First and foremost I want to be able to trade *something*. It doesn't matter what.
2. I look over what is on offer: equities, currencies (euro to dollar, kroner to euro, yen to rupee) and cryptocurrencies like Bitcoin and Ethereum.
3. I check my conditions. What can my hardware handle, and how quickly can I react? Can I get data and an exchange connection to match that speed? Can I only buy, or also sell short? Do I have derivatives? Leverage?
4. I check the fees on every round trip. If I have to wait for a 2% move before a trade even breaks even, my "trading" setup has quietly become a long-only buy-and-hold investment.

Every one of these has bitten me, and more besides. That is why I recommend looking at the data first and proposing hypotheses second. Do it the other way if you like, but don't fool yourself that a beautiful alpha with a magnificent Sharpe on daily MSFT bars is actually profitable. It can teach you something about the market. It may very well not make money. I have jumped into that hole many times.

## Clean data, dirty results

The data you can pull from Yahoo Finance, Google or ccxt is clean. It is clean to a degree most new quants don't appreciate, because the market it came from is not.

The second trap is lookahead bias, and nearly everyone adds it by accident: to their features, their hypotheses and their backtests. Reality looks more like this: the data arrives at time T, you can trade at T+2, and by then the price has moved 1% the wrong way. On top of that come trading fees, currency conversion and account costs. A strategy with a Sharpe above 3 in a backtest can easily come out at 0.5 once fees and slippage are in.

I once had a strategy with a Sharpe of 34. Yes, it was too good to be true even when I first saw it. No slippage, no fees, and it bought and sold on the same bar that triggered the signal. Here is how easy that mistake is to make. One simple signal, long or short Bitcoin depending on whether its 15-minute moving average is rising, tested on minute bars from {{data:lookahead.period}}:

<!-- ctrl:figure data-lookahead | The same signal five ways. Trading on the bar that produced the signal turns a Sharpe of 1.4 into one above 100. A cost of 1 basis point per trade, a tenth of Binance's standard spot fee, turns it negative: the signal flips about {{data:lookahead.flips_per_day|int}} times a day. -->

The first two rows are not a strategy. They are a bug. If your backtest looks like them, look for the line of code that lets tomorrow leak into today.

## What the exchange actually sends

May the gods be merciful to anyone working in this part of the industry. The bravery it takes to battle the raw data streams is beyond even me.

Genuine market data is noisy, and "noisy" is an understatement. Messages arrive late, in bursts, and sometimes not at all. Say you send an order at time T. It reaches the exchange at T+1, it matches at T+2, the confirmation leaves at T+3, and it lands back with you, stamped as matched, at T+13. That is exaggerated, but not by as much as you'd hope. On the day below, most trade messages reached the recorder about {{data:latency.trades.p50|1}} ms after the exchange stamped them. One in a hundred took more than {{data:latency.trades.p99|int}} ms, and one in a thousand more than {{data:latency.trades.p999|int}} ms.

<!-- ctrl:figure btc-latency | Delay between the exchange's timestamp and the moment the message was received, Binance BTCUSDT, {{data:day}}. Amber bars are delays of 100 ms or more. -->

Orders get posted, cancelled, partly filled, re-posted and filled again, often within the same millisecond. Some of the size you trade against was never visible: an *iceberg* order shows only a sliver of its real size and refills as it is hit. From your side of the screen, trades appear out of thin air. It is the job of the colossally brave data engineers in quant firms to clean all of this up. Trades (tick data) can usually be cleaned reasonably well. The limit order book (LOB) is the hard part.

## Four views of the same market

To show you what I mean, I have to show you the data itself. Everything below is Bitcoin against Tether (BTCUSDT) on Binance, from the coarsest view to the finest.

<!-- ctrl:figure data-granularity | The four datasets side by side. Lag-1 autocorrelation is how strongly one return predicts the next; at every scale it is close to zero. -->

### Daily bars

Most people starting out look up a chart of one of the big stocks of their time. When I started it was Microsoft, and today it is thankfully still Microsoft. In a few years it may be Anthropic or Nvidia. Believe it or not, Nvidia was a completely random choice when I started: just a company making graphics cards for gamers.

Then you find out you can get CSV files of open, high, low, close and volume (OHLCV). Later came Python and [yfinance](https://github.com/ranaroussi/yfinance). God bless Ran Aroussi, he made my life ten times easier. You lot are so privileged you can't imagine scouring Google for days to find a CSV with a single year of daily OHLCV. I thought it was pirate treasure at the time. Today you can simply go:

```python
import matplotlib.pyplot as plt
import yfinance as yf

# ten years of daily Microsoft prices
df = yf.Ticker("MSFT").history(start="2016-01-01", end="2026-01-01")
df["Close"].plot()
plt.show()
```

and you get a beautifully clean chart of closing prices. Here is the same view for Bitcoin, one point a day:

<!-- ctrl:figure btc-daily | BTCUSDT daily close, {{data:daily.start}} to {{data:daily.end}}, built from Binance minute bars. -->

Right off the bat you'd think buy and hold is a decent strategy. If you wanted to be cool, you'd think "I can buy the dip and sell the top". That is the coolest idea we all know: buy low, sell high. Tada, you reinvented trading.

<!-- ctrl:figure sample-daily | Daily bars: one row per day. -->

If you get curious, you load more assets and look at correlations between them, or at the autocorrelation of each asset's returns. Then you test simple strategies with buys and sells on some arbitrary condition, like the schmucks we all are. Buy when the moving averages cross, sell when they cross back. And so on.

### Minute bars

Go a step further and you ask for hourly or minute-by-minute data. It is still fairly clean, but the nitty-gritty starts to show. Crypto is lovely for this, because the exchanges give it away:

```python
import ccxt
import matplotlib.pyplot as plt
import pandas as pd

# one day of BTC/USDT minute bars from Binance, 1,000 bars per request
ex = ccxt.binance()
since, end = ex.parse8601("2026-08-01T00:00:00Z"), ex.parse8601("2026-08-02T00:00:00Z")
rows = []
while since < end:
    batch = ex.fetch_ohlcv("BTC/USDT", timeframe="1m", since=since, limit=1000)
    if not batch:
        break
    rows += batch
    since = batch[-1][0] + 60_000

df = pd.DataFrame(rows, columns=["time", "open", "high", "low", "close", "volume"])
df["time"] = pd.to_datetime(df["time"], unit="ms", utc=True)
df = df[df["time"] < pd.Timestamp(end, unit="ms", tz="UTC")].set_index("time")
df["close"].plot()
plt.show()
```

<!-- ctrl:figure sample-minute | Minute bars: 1,440 rows per day. Binance adds the number of trades and the volume bought by takers. -->

Even this clean file has holes. In the five-year minute history behind these charts, {{data:gaps.minutes|int}} minutes are missing across {{data:gaps.episodes}} stretches, the longest {{data:gaps.largest.0.minutes}} minutes from {{data:gaps.largest.0.start}} UTC. They were filled with the previous close and zero volume, which is a choice, and it is not the only one. Find out how your data was filled before you trust a backtest on it.

### Trades

Below the bars sits every single trade: price, size, time, and which side was the aggressor. That last field is the *order flow*. On {{data:day}} Binance printed {{data:trades.rows|int}} BTCUSDT trades. The median trade was {{data:trades.size_quantiles_btc.p50}} BTC, a few dollars, and {{data:trades.same_timestamp_share|pct}} of trades share their timestamp with the one before. That is one aggressive order eating several resting orders, printed as many separate trades.

<!-- ctrl:figure sample-trades | Trades from the Tardis.dev CSV format. timestamp is the exchange's clock; local_timestamp is when the message arrived. -->

Order flow is the most honest data you can get: it is what people actually did, not what they said they would do. But be careful what you conclude from it. Buy-heavy minutes go up and sell-heavy minutes go down, which is close to a tautology. Whether the *next* minute follows is a different question:

<!-- ctrl:figure btc-flow | Order flow imbalance against the same minute's return and the next minute's, {{data:flow.minutes|int}} minutes of August 2026 (700 shown). -->

### The order book

The order book is the list of resting buy (bid) and sell (ask) orders waiting to be hit. This file holds the best five levels on each side, snapshotted about every {{data:book.median_interval_ms|int}} ms. Bitcoin is so heavily traded that the spread was one tick ($0.01) in {{data:book.spread_one_tick_share|pct2}} of snapshots. Look at where the size sits, though: almost all of it is at the best price, and the next four levels hold crumbs.

<!-- ctrl:figure btc-book | The best five levels on each side. Bars are BTC, at the same scale within each panel. -->

<!-- ctrl:figure sample-book | Book snapshots, the first two of five levels. -->

### From a day down to a minute

Now put it together. Take one day, find its busiest minute, and zoom in:

<!-- ctrl:figure btc-zoom | Hover a candle or a trade for its numbers. Trades that share a timestamp and side are drawn as one mark: a single order sweeping the book. -->

In the minute from {{data:zoom.minute}} UTC, Binance printed {{data:zoom.trade_rows|int}} trades. {{data:zoom.largest_sweep.snapshot_before.t|1}} seconds into that minute, the book showed {{data:zoom.largest_sweep.snapshot_before.visible_bid_qty|2}} BTC across all five bid levels, the best bid at ${{data:zoom.largest_sweep.snapshot_before.best_bid|2}}. Before the next snapshot, {{data:zoom.largest_sweep.gap_ms|int}} ms later, a single sell order traded {{data:zoom.largest_sweep.qty}} BTC at ${{data:zoom.largest_sweep.lo|2}} to ${{data:zoom.largest_sweep.hi|2}}, in {{data:zoom.largest_sweep.prints}} separate prints. None of that size was in any snapshot. It was resting deeper than five levels, or it arrived between two pictures of the book. That is what you are up against.

## On smoothing

Look at the minute chart and you'll see far more noise than in the daily one. I can't tell you how many times I've been told "you should smooth it", including by statisticians with PhDs. I'm sorry to tell you, lovely bubu: smoothing does not do what you hope.

It is useful for looking at a chart. But a centred moving average uses prices from the future, which is exactly the first row of the table above. A trailing one lags, so by the time it turns, the move has happened. And much of what looks like noise isn't random at all. It is the mechanics of the book: one order printed in hundreds of pieces, quotes pulled and refilled within milliseconds, liquidity you could not see. Throw it away and you throw away the part that tells you how trading actually happens.

I have talked with a fair number of data engineers in the markets, and they keep telling me the same thing. Markets are noisy, and nobody can say for certain which price is the right one. Getting closer to that answer than everyone else is the real game of the big algorithmic firms, and in many ways it is their edge.

## Get the data

For IMC Prosperity, backtesting and analysis, I will share the order book data and the minute-by-minute data I have collected here. The Prosperity datasets and data from other competitions are here too, so the keen observers among you can find the patterns that repeat between competitions and get a leg up.

<!-- ctrl:link https://tomorrowlibrary.github.io/CTRL/datasets/index.html | Prosperity historical data | Every IMC Prosperity file from four editions, profiled round by round. -->
<!-- ctrl:link https://tomorrowlibrary.github.io/data.html | The Library's data catalogue | Datasets with sources, licences and download links. -->
<!-- ctrl:link https://data.binance.vision/ | Binance public data | Daily and monthly files of klines and trades for every Binance market. -->
<!-- ctrl:link https://docs.tardis.dev/downloadable-csv-files | Tardis.dev datasets | Tick-level trades and order books. The first day of every month is free. -->

The trades and book snapshots on this page are the free Tardis.dev files for {{data:day}}, and the minute bars come from Binance. Every number and chart on this page is produced by `ctrl_data_showcase.py`, so you can rerun it on any other day.


"""
We now need to add the datasets setup and structuring of the different notebooks for loading in data and such.
I imagine that those are divided in something like a table of tables, such that you first get some buttons with dropdown menus, 
So you for example press "cryptocurrencies", which leads to a drop down menu on assets, than day-by-day or minute-by-minute or orderbook.
Such that a student can press those and get the data they need for the different assets from say 2016 to now. 

Similarly they can press "IMC" and press Prosperity 1, 2, 3, 4 and than get zip files with round 1, 2, 3, 4, 5. For each of those.
"""
