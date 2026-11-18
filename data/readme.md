May the gods be merciful towards anyone working in this part of the industry. 
The fucking bravery a man or woman must have to battle the data streams, is unimaginable even to me.

Now before you get another deep and meaningful explanation. Here is a link straight to the data library, so you can get your claws on a bunch of that premium freshly cooked market data.





Now here is why. Genuine data coming out of the markets is noisy, actually, noisy is an understatement in that department.
Exchanges may, swap around orders, may drop connectivity for varying lengths of timehorizons. Say you send an order to the exchange.
you send it off at time T, it arrives at the exchange at time T+1, it matches at time T+2, the exchange sends it back to you at T+3...
As matched at time T+13. This is an exaggerated example to explain to you that time. Is not necessarily a common phenomenon.

Orders in the market may be cancelled, posted, matched, ignored, cancelled after being matched, matched out of thin air. That is called iceberg orders.
It may be matched with nothing, you buy into nothing, that is called synthetic orders. It's like the exchange simply goes "hey we had a couple of thousand microsoft stocks laying around from yesterday, do you want them?"

It is the job of the massively, collossaly brave data engineers in the quant firms, to clean this complete asshattery coming out of the exchanges.
It can usually be cleaned up relatively well with the tick data. What I'm talking about here is the LOB data. 

Now to show you what I mean, I may also have to genuinely show you the datasets.

Most individuals starting out with data in mind, look up a graph of one of the big stocks in their time period.
When I started out it was Microsoft, today it is thankfully still microsoft. But in a few years it may be Anthropic or Nvidia.
Believe it or not, Nvidia was a completely random choice back when I started. It was still just a random ass company making graphics cards for gamers.

A graph would look like this...
<img width="490" height="416" alt="image" src="https://github.com/user-attachments/assets/8348d651-4b3a-45e7-b5e1-10dbc5123be1" />
Right off the bat you'd get the idea that "buy and hold" was a decent enough strategy. 
If you wanted to be cool you'd think to yourself "I can buy the dip than sell the top". And in fact that is the coolest idea WE all know of.
"Buy low sell high", tada you reinvented trading.

Now after some searching you'd either figure out that you could get .csv files with historical data, open high low close maybe volume.
Later python and Yfinance, god bless Ran Aroussi! https://github.com/ranaroussi, made my life 10x easier. Made all of you smucks so privilegde, you can't even imagine what it is like to scour google for days and days just to find a .csv file of like 1 year worth of OHLCV data. I thought it was a fucking pirate treasure at the time. Today you can simply go 
```python

import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import yfinance as yf


## import some f-ing msft data over the last 10 years

df = yf.download("msft", start="2016-01-01", end="2026-01-01")

plt.plot(df["close"])
plt.show()
````

and you get a freak clean graph of just the close prices.
Than if you get curious after that you can look at correlations between stocks by loading more in, you can look at autocorrelations of prices for each asset.
Than you can check on simple trading strategies by just proposing buys and sells based on some random condition, like the smucks we are.
Buy when SMA cross, sell when SMA cross. So on and so on.

Now if you want to go a step further, you'd ask about hour by hour data or minute by minute data, which is also quite clean, but starts to show some of that nitty gritty.

Try this on for size, cryptos are lovely in that way.
```python

import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import ccxt


## import some crypto data, I dare you ;)

- ccxt command load in btcusdt

plt.plot(df["close"])
plt.show()
````

By looking over this you should notice a larger amount of noise, than for the day by day stocks.
Now I can't tell you how many times I've heard someone tell me "you should smooth it", statisticians with Phds have told me that. 
I am sorry to tell you, smoothing DOES NOT WORK, I understand that it should, but lovely bubu, it doesn't work.
Yes, there are lots of useful behaviors in the smoothing, but what most forget is this, that noise isn't random noise, it is intentional.

Now I have genuinely had a range of chats with data engineers in the markets. The amount of times they can tell me the same thing.
Markets are noisy, we can't effectively determine "which price is the right one", that one is the genuine game of big algo firms, that in many ways is their edge.
This is also quite revealing. 




