## What an alpha is

An alpha, as the introduction put it, is an idea that has been proposed, tested and has survived in the market. It survives because it has edge:

$$
\text{Edge} \approx \underbrace{\mathbb{E}[\text{exit price} \mid \text{future counterparties}] - \text{entry price}}_{\text{the gap you capture}} - \underbrace{\text{impact}(q, \text{depth})}_{\text{your own footprint}} - \text{costs}
$$

Or, in other words:

$$
\text{Edge} \approx \mathbb{E}[\text{net return} \mid \text{what you know now}\]
$$

Edge must be above zero: the idea has to make money. Everyone likes to spout "buy low, sell high", but it doesn't have to be exactly that. Three things have to hold. You predict the direction. The move is bigger than your fees. And your orders actually get filled, on the way in and on the way out. If you can predict a fall, you short instead of going long: sell high, buy low.

So that is the essential idea. Now we have to find an edge. We can go straight at it as traders, or come at it as scientists. I will do both, to show what I mean by each.

## Going straight at it: the dip and refill

Going straight at it means proposing a trade. "Buy low, sell high" is the idiot's version. A more precise one:

> Post a limit buy at the current price minus 1%. Then post a limit sell at the current price plus 1%. If both fill, I earn 2% on every round trip.

Assume for now that limit orders cost nothing. In IMC Prosperity they don't. On a real exchange, resting (maker) orders are cheaper than aggressive ones but rarely free.

Surely the chance of both filling is 0%? It would take an astronomical event: the price falls 1% in an instant, then bounces straight back. But wait. Does that completely ludicrous scenario happen in the markets?

It does. As absurd as it sounds, this "liquidity drop and refill" really occurs, and it was one of the completely insane alphas I used in IMC Prosperity 4. Here is how often it happens in Bitcoin. Every hour from {{alpha:period}}, I posted a buy limit some distance below the price. If it filled within the hour, I sold it back at the old price (the refill), or after four hours, whichever came first.

<!-- ctrl:figure dip-table | Every hour, a buy limit below the last BTCUSDT price on Binance minute bars, {{alpha:period}}. "± trips" counts hours where a buy at −depth and then a sell at +depth both filled. The refill sells back at the old price within four hours. Fees are per round trip. -->

The full ±1% round trip came round about {{alpha:dip.rows.2.round_trips_per_30_days|1}} times a month. Not astronomical at all.

The usual explanation goes like this. At time T the book is full of passive orders: people have put in their bids and are perfectly happy to wait for a match at their price. Then at T+k someone decides they need 1,000 units of X *today*, and they chew through the bids, so the price drops. You, being savvy, left your buy order in the book. You were filled while the whale came through, and you sold again when the whale left and the book refilled the hole.

## The adverse scenario

What my little story misses is the adverse case. What if the book drops *with intent*? Imagine a new tariff aimed at one company's products. Its stock falls, and for good reason. Buying at the current price minus 1% would be a terrible move, because there is no refill coming.

In Bitcoin it looks like this. At 0.5% below the price, the refill comes {{alpha:dip.rows.1.win|pct}} of the time, and every win is small, about +{{alpha:dip.outcomes_05.refill_bp|int}} bp. The other {{alpha:dip.outcomes_05.loss_share_of_fills|pct}} are where the money goes:

<!-- ctrl:figure dip-outcomes | {{alpha:dip.rows.1.fills|int}} fills of a buy limit 0.5% below the price. Amber: trades that did not refill within four hours and closed at a loss. The worst lost {{alpha:dip.outcomes_05.worst.0.pct|abs}}%, in the crash of 19 May 2021. -->

A win rate of {{alpha:dip.rows.1.win|pct}} averaged {{alpha:dip.rows.1.mean_bp.0|bp}} a trade before fees and {{alpha:dip.rows.1.mean_bp.20|bp}} after a standard 10 bp a side. Your alpha always needs correcting for regimes, risks and false positives.

## Coming at it as a scientist

This is why a scientific study of your alpha and its adverse moves matters. Turn the trade into hypotheses: "If I post a limit buy at the current price minus 1%, how often do I lose, how often do I win, and what is the expected value after fees over a horizon T?" These can be tested, and thankfully they lead to more questions. In which regimes is the chance of a loss below 50%? Which conditions go with a high win rate? And are there conditions with a *low* win rate but a high expected value?

The table above already answers the last one. At 2% below the price the refill wins only {{alpha:dip.rows.3.win|pct}} of the time, yet it has the best average, {{alpha:dip.rows.3.mean_bp.0|bp}}. Split the 0.5% version by the market it was posted into:

<!-- ctrl:figure dip-regimes | The 0.5% dip and refill, split into thirds by what the market did just before the order was posted. Both splits use only information available at that moment. -->

After a wild hour the refill wins most often, and that is also where the worst loss sits. After a calm hour it wins least, and loses on average. Every row is a new hypothesis to test on data you have not looked at yet.

## The scientific road the other way: mean reversion

You can also start from a hypothesis. Here is the example nearly everyone knows. Hypothesis: prices are mean-reverting. You will immediately be clubbed over the head, with every test saying "rejected". So you refine it: *log* prices are mean-reverting. Beaten senseless again. So you try harder, and narrow it to certain periods, then to certain regimes. Here is that ladder for Bitcoin, using the augmented Dickey-Fuller (ADF) test, where a p-value below 0.05 counts as mean-reverting:

<!-- ctrl:figure mr-ladder | Each row narrows the hypothesis. {{alpha:period}}. -->

Look at the stretches one by one and some of them pass:

<!-- ctrl:figure mr-windows | ADF p-values for BTC's hourly log price in consecutive 30-day windows. Amber dots pass the test. -->

{{alpha:ladder.windows.accepted}} of {{alpha:ladder.windows.n}} windows pass, where pure chance would give about {{alpha:ladder.windows.expected_by_chance|1}}. That is some evidence. But look at the next two rows of the table. Pick the quiet stretches *after the fact* and the pass rate rises. Pick them with what you knew at the start, and it gets worse. A regime only helps you trade if you can know it at the moment you trade.

Satisfied for now, you turn it into a strategy: fade the price when it strays two standard deviations from its 24-hour average. And it returns... guess what?

<!-- ctrl:figure mr-years | The same rule each calendar year, before and after fees. -->

It lost in five years out of six. Had you found it at the end of 2025, you would have had a backtest Sharpe of {{alpha:ladder.strategy.sharpe_no_fees.2025|2}}, and you would have watched it turn into {{alpha:ladder.strategy.sharpe_no_fees.2026|2}} the following year, or {{alpha:ladder.strategy.sharpe_10bp.2026|2}} after fees.

And now you know what alpha decay is. Your idea may be true, and you may have worked hard on it, but at least a dozen of us found it before you. Some of us have lower fees, a better understanding, more compute and better setups, so we are already competing that edge away.

## Both roads lead to the same place

To me, it doesn't matter which way you come into an alpha, trader first or scientist first, as long as you can translate between the two. To set up and improve a strategy you will have to do both.

I apologise for going a bit on the nose with the scientific approach. There are better ways to trade mean reversion than a moving-average cross. In fact a cross is a *trend* signal: fading it is the mean-reversion version. Estimate how strongly the price reverts, compute its half-life, and derive the expected return directly from the test. But many newcomers I've chatted with are excited by the simplicity of an SMA cross, even though it is an unlikely candidate.

<!-- ctrl:link https://tomorrowlibrary.github.io/CTRL/alphas/index.html | Known alphas | Patterns that paid in earlier Prosperity editions, with day-one tests and failure modes. -->
<!-- ctrl:link https://tomorrowlibrary.github.io/CTRL/data/index.html | Data first | What the exchange actually sends, and why a clean backtest lies. -->
<!-- ctrl:study 002 -->

Every number on this page is produced by `ctrl_alpha_studies.py` from Binance BTCUSDT minute bars. Fills are judged on each minute's high and low, which ignores your place in the queue, so real fills would be fewer.
