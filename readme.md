# Ctrl+Alt+DefeatTheMarket

**The unofficial guide to IMC's Prosperity challenge.**

---

## Introduction

Stop a person on the street and ask them, "What is the greatest human endeavour?", and they will pick the one nearest and dearest to them: feeding everyone, medicine, mathematics, leaving Earth, the written word, big cooperative science, or our moral and political experiments. Ask an AI and it will simply spout the entire list.

All great endeavours. But as a human and an "influencer", it is my job to tell you that my answer is the one that matters, and I already know I am right. *Wink, wink.*

The greatest human endeavour is algorithmic trading. Before that it was simply trading, and before that it was bartering.

Most of us reading this are scientifically minded, so many of us just silently yelled "CERN!" Convincing a scientist that a business subject is the greatest endeavour of our species is like convincing a bird to breathe underwater.

And unlike many other finance bros, I am not going to tell you that the reason is "MONEY!!!" I have not grown rich. I am a tiny enthusiast who endeavoured to build his own setup because nobody else wanted to hire him, and my goal with this guide is to give you, the random undergrad, grad student or PhD who stumbled in here, the courage, the tools and the core reason to outpace me by next year. If one day the student runs the master through with a broadsword, I will be one happy teacher.

The reason algorithmic trading is the greatest human endeavour is the friends we make along the way.

Hahaha, no.

It is the greatest because it encompasses all the others. It is the dance of supply and demand, action and reaction, good times and bad, across all of time and space. Every tick is a decision stepping out of the darkness: a market order to buy, a hedge fund dropping its position in Microsoft, a new meme coin pumping and dumping like a street trick played on an unsuspecting tourist. We try to read it all as particle streams, mean field games and fluid flow. We say we are looking for edges, but in reality we are looking for the laws that govern not only particles but all of our minds. And when a competitor gets the best computer system ever imagined, we somehow have to outcompete them with a laptop and a shoddy internet connection, by finding a better interpretation of those laws. Only the competitively best understanding of the universe and of ourselves is left standing.

---

## So what the fuf is algorithmic trading?

I must bow to my own stupidity. That was a passionate, inspirational letter about something I never explained.

*Algorithmic* comes from al-Khwarizmi, a ninth-century Persian mathematician whose textbook was so popular that medieval Europe made a word out of his name. *Trade* comes from an old Dutch and Low German word for a path, a cousin of the Danish *træde*, to step. So, being Danish, let me take you down the trading path.

Algorithmic trading is simply trading, with mathematics, systems and algorithms added to enhance an already profitable kind of business. Take the engineers and scientists of CERN and point them at asset prices rather than particle streams. And I am nearly entirely sure of this about you, dear reader: you love mathematics, you would happily study for your entire life, and you would also like a holiday every once in a while. So CERN is on the back burner and Two Sigma is at the front.

The trouble is that the majority of us come out of academia knowing just about squat about trading. So what the flying fuf is trading?

We have all scrolled past the finance bruva on Instagram, showing off his 15th Jaguar (vroom, vroom) and the two cardboard boxes he calls his mansion. Take away his pump-and-dump scam and his idea is the whole of trading: buy low, sell high. The goal is profit. Wow! Give this man a Nobel Prize! Yeah, anyhow. You can make that profit by matching buyers and sellers (market making), by knowing the correct price when the market has it wrong (relative value), by being the fastest to a wrong price (latency arbitrage), by knowing how assets move together (statistical arbitrage), or by knowing how the crowd behaves (trend following).

Now for what your degree did not prepare you for. Trading is a business subject, much more akin to accounting or supermarket management than to particle physics, and the real world outside the lovely, sheltered life of academia is ABSOLUTE FUCKING CHAOS. The politeness of "fuf" must be dropped here. Your professors told you that 2 + 2 is always 4. In the markets that is only true some of the time, because an asset is worth whatever the next counterparty will pay. Your one-billion-parameter model may be no better than a coin toss, and being right 60% of the time can be worse than being right 40% of the time.

So we do not even need to be right. We only need to be less wrong than the bloke on the other side of the trade, by more than it costs us to trade. That is called **edge**:

$$
\text{Edge} \approx \underbrace{\mathbb{E}[\text{exit price} \mid \text{future counterparties}] - \text{entry price}}_{\text{the gap you capture}} - \underbrace{\text{impact}(q, \text{depth})}_{\text{your own footprint}} - \text{costs}
$$

First and foremost we are TRADERS. Then we are mathematicians, computer scientists and physicists.

---

## The process: no storytelling, please!

*I was recently told by my partner that I am a fucking storyteller, and that sometimes we just need a bloody summary rather than a story. So here is the summary. The stories are behind the links.*

Algorithmic trading goes beyond stating "edge is buy low, sell high". It is about demonstrating, statistically, that an idea is real and gives you an advantage over the markets (read: every idiot under the sun trading with or against you). The work follows a pipeline:

- **Data.** Everything starts with what you can see: prices, order books, trade logs. I used to think denoising was the most boring thing in the world. Today I know it is the gold mine. [→ Data](https://tomorrowlibrary.github.io/CTRL/data/index.html)
- **Alpha.** An idea that has edge, in three rough flavours: providing liquidity, exploiting inefficiencies (sometimes the market is simply filled with idiots), and following the inevitabilities that arrive without anyone's consent. [→ Alpha](https://tomorrowlibrary.github.io/CTRL/market-dynamics/index.html)
- **Risk.** It helps you correct yourself and keeps you from losing money unnecessarily. Adverse events will happen! Regardless of what your professors have been trying to teach you. [→ Risk](https://tomorrowlibrary.github.io/CTRL/inventory-risk/index.html)
- **Inventory.** Every trade leaves you holding something: what, how much and for how long, per asset and then as a portfolio. [→ Inventory](https://tomorrowlibrary.github.io/CTRL/inventory-risk/index.html)
- **Execution.** Where the idea finally meets the order book. Every order leaves a footprint, and every trade costs something. [→ Execution](https://tomorrowlibrary.github.io/CTRL/execution-backtesting/index.html)
- **Research.** How a scientific hypothesis becomes a trading idea. Do not use AIs for alpha hunting: beautiful and useful as they are, they have literally no f-ing clue. Use them to speed up EVERYTHING else. [→ Research](https://tomorrowlibrary.github.io/CTRL/research/index.html)

I would guesstimate that alpha and a baseline implementation take you 75% of the way. If you would rather start from an existing idea, there is [a massive pile of alphas](https://tomorrowlibrary.github.io/CTRL/alphas/index.html) to search through and improve on.

---

## Go and test it

Reading about trading only takes you so far.

**[IMC Prosperity](https://prosperity.imc.com/)** is the reason this guide exists. Prosperity 3 was beachy, sandy and islandy, Prosperity 4 was spacey and starry, and who knows what adventure awaits us in Prosperity 5. It is an algorithmic trading competition, and likely the second most elaborate one available. (The first is an [FTMO free-trial account](https://ftmo.com/en/ftmo-free-trial/): the closest you will get without actually running an account in the markets, and a place to get your ass handed to you so massively that you feel like you were run down by a train.) Prosperity runs once a year, you enter alone or in a team of up to five, and although it is built for university students, anyone can sign up to learn.

One thing must be ingrained in your soul before you start: it is not a mathematics competition. It is a competition in TRADING. IMC is kind, and lets you have some alphas for free, right off the bat. In the real markets, winning 55% of the time is fucking great.

More places to test your ideas: the [WorldQuant International Quant Championship](https://www.worldquant.com/brain/iqc/), [Numerai](https://numer.ai/), the finance competitions on [Kaggle](https://www.kaggle.com/competitions), the [UChicago](https://tradingcompetition.uchicago.edu) and [Rotman](https://ritc.rotman.utoronto.ca) trading competitions, and the rest of the [competition directory](https://tomorrowlibrary.github.io/competitions.html).

---

## A note from the author

I have taken part in IMC Prosperity for the last two years. Last year I wrote a guide on how to get started and reach a decent score, and it took off: compliments, reviews, and it even became a dedicated AI skill (*somehow?!*). I did not feel it was up to what the challenge deserves, so this is the expanded version, combined with my own notes, research and resources.

I will not be participating much in Prosperity 5. Having scored to my own satisfaction in Prosperity 4 and a few other challenges, I am now doing my own algorithmic trading in the markets. As worthwhile as Prosperity is, it is sadly in no way equal to that challenge. I still STRONGLY recommend it. It is a genuinely beautiful setup, and it takes you from zero to hero in no time.

> I hope you all CTRL+ALT+DEFEAT THE MARKET, guys and girls.

---

## Contact

You can find my other works at [Tomorrow Capital Research](https://tomorrowcapitalresearch.github.io/), in the [Tomorrow Library](https://tomorrowlibrary.github.io/index.html) and on [GitHub](https://github.com/MarkBrezina). If you want to contact me, write to [tomorrowcapitalresearch@gmail.com](mailto:tomorrowcapitalresearch@gmail.com).
