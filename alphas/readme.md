If you went to the data page first, thank you, if you went straight for the throat, alphas!
Welcome here, we will introduce you to the wonderful world of pain.

Alphas as mentioned in the introduction are the ideas presented, tested and survived in the market that fulfills this.

$$
\text{Edge} \approx \underbrace{\mathbb{E}[\text{exit price} \mid \text{future counterparties}] - \text{entry price}}_{\text{the gap you capture}} - \underbrace{\text{impact}(q, \text{depth})}_{\text{your own footprint}} - \text{costs}
$$

Or, in other words:

$$
\text{Edge} \approx \mathbb{E}[\,\text{net return} \mid \text{what you know now}\,]
$$

In essence edge must be above 0. We must earn money from the idea presented in an alpha.
The simple idea, everyone likes to spout is, "buy low sell high", but what that doesn't mention is how we don't need it to be exactly like that.
We need to be able to predict direction, the absolute size of the return to be above fees and for the probability of fills to be high on both entry and exit.
If we can predict downwards move, we can short instead of go long. Essentially "sell high, buy low". 

So that is our essential idea. We now need to be able to figure out an edge. 
We can go straight at it or we can go about it as scientists.
I will do a combination of both just to show what I mean with both.


If I want to go straight at it, I simply propose a trading idea.
"buy low sell high", is the idiot version of this, the more descriptive could be.
"If I post a limit order(meaning 0% fees) at the current price(X) - 1%"
"Than immediately post a limit order(meaning 0% fees) at the current price(X) + 1%"
I should essentially earn 2% on each round trip. Given those orders get matched in the market.

The likelihood of that scenario being filled is 0%, it would take an astronomical event.
The price falls by 1% instantenously, than it rebounces instantenously, but wait... !
This completely ludacrious scenario... Does happen in the markets?

Actually it does, as absurd as it sounds this type of "liquidity drop and refill" actually does occur in the markets.
It was one of the completely insane alphas I used in IMC prosperity 4.

The most common explanation is this one.
The orderbook at time T is filled with passive orders, people have put in their bids and are totally satisfied simply providing matches at certain prices.
Than at time T+k someone decides, today I need 1000 pieces of X stock, and they chew through all the bids or asks leading to a drop in price.
You having been savvy, left your buy and sell order in the book being matched first when the whale came threw with his massive order, than you matched again when the whale disappeared and the book bounced back to fill the hole.

Now what my little story misses, is the adverse scenario.
What if the book drops with intent? What if trump decided to add tariffs only to chevron products?
Than the price of Chevron stock would drop, with good reason?
Buy at current price - 1% would be a shit move by than, what do you do about that kind of risk?
Your alpha always needs correction for regimes, risks, false positives.

This is why a scientific study of your alpha and its adverse moves, is important.
You can now propose a hypothesis.

"If I post limit orders at current price(X) - 1%", how often will I lose a trade, how often will I win a trade, what is the expected value after fees for time 
horizon T of backtests? These ideas can be tested and they thankfully lead to even more questions afterwards.

In which regimes is the likelihood of loss below 50%?
In which regimes is the likelihood of winning above 50%?

What conditions are significant for a period with above 50% winrate?
Are there conditions that are significant for a high expected value with a low winrate?

All of these can be phrased into a proper hypothesis and tested properly.
But you may also do the reverse.




Here is a good example, that is easy and known to nearly everyone.

Hypothesis. prices are mean reverting for stock XYZ.
You will, immediately be clubbered over the head with every test returning "rejected".

So you improve your hypothesis.
log prices are mean reverting for stock XYZ.
Which again will beat you senseless with every test returning "Rejected".

So you try even harder.
log prices are mean reverting for stock XYZ, in periods "2016-01-01" to "2018-05-15".
Which now reads, 7 out of 15 tests returned "Accepted".

So you think you've gotten the idea.
log prices are mean reverting for stock XYZ, in regimes A, B, C and D, but not in ... You get the idea.
Which now reads 31 out of 35 tests returned "Accepted".
And you are satisfied for now.

You try to convert it into a trading strategy.
"Buy the SMA Cross, when XYZ is in regimes A, B, C and D, but not in ..."
This however returns... Guess what? "not profitable after fees, barely profitable before fees, sharpe 2 in the period you ran your tests on, but sharpe 0.3 in the period you're in now".

And you now know what alpha decay is.
Your idea, as great and hard as you've worked on it, while being true, has already been discovered by at least a dozen of us before, some of us have lower fees, better understanding, better compute and setups. So we are simply outcompeting that edge already.

To me the two ways into an alpha do not matter, if you choose a trading perspective first or a scientific perspective first, as long as you can translate, you will do fine. In order to setup and improve an alpha or strategy you will have to do both. 
I also do apologise that I went a bit on the nose with the scientific approach to a strategy, often you will have better ideas as of how to implement a mean reversion strategy rather than simply doing "SMA cross", mean reversion strength, calculations on half-life, expected future return lead directionly form the idea of testing for the mean reversion. But many newbies I've chatted with are excited about the simplicity of a SMA cross. even if it is an unlikely candidate.












