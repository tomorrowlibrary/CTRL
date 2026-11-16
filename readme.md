

the design: 
at the top drop the "TOMORROW / KNOWLEDGE & METHODS" and the "capital research", ...
leave just a reference to the library, but keep "Ctrl+Alt+DefeatTheMarket" as the logo and stuff.
Replace with menu bars "Data", "Alphas", "Risk", "Inventory", "Execution"

Have the logo
<img width="999" height="263" alt="image" src="https://github.com/user-attachments/assets/4629e6e8-5438-4fbe-b98a-f53c6b6afaf2" />
and than the little orderbook, markets screen 
<img width="1427" height="654" alt="image" src="https://github.com/user-attachments/assets/b80b7bc4-c8a7-419a-aa95-0795526d997e" />

Drop the references back to the rest of the library
<img width="394" height="63" alt="image" src="https://github.com/user-attachments/assets/77ceaa08-239b-4c00-a114-f245ade25986" />


We want the title to be something like

big title - "Ctrl+Alt+DefeatTheMarket"
sup title - "The unofficial guide to IMC's prosperity challenge."

hero/animation/video

---

# Introductions 

Dear reader, for the last two years, I have participated in the IMC Prosperity competitions and last year I decided to build out a guide for how to get started and how to get helped into reaching a decent score. The guide took off quickly and so this year, I have decided to expand and do the guide the justice, I felt I couldn't last year. Despite the fine compliments, reviews and the guide even becoming a dedicated AI skill *somehow?!*, I did not myself feel it was up to par for what the challenge correctly deserves. I have therefore updated it and combined it with my own work to share notes, research and resources. A larger task I have had going for a long while.

Note from the author:
This year, for IMC prosperity 5, 2027, I will not be participating much.\
After having scored to my own satisfaction on a range of challenges over the years,\
Wunderfund RNN, Connectome and IMC 4 as the last ones. I have taken the opportunity to do my own algorithmic trading in the markets.\
This, as you may understand, requires more focus and attention than the IMC challenge.

As interesting and worthwhile as IMC Prosperity is, it is sadly in no way equal to the actual\
challenge of participating in the markets in real time. I do however STRONGLY recommend participation in\
IMC Prosperity, it is a genuinely beautiful setup and helps you move from 0 to hero in no time.

```Text
So without further ado, here are the secrets to the universe as we know it...
```

Quick links for the bored individual?


---

## No story telling please!
*Note: I was recently told by my partner, that I am a fucking storyteller and sometimes we just need a bloody summary, rather than a story. So here is a summary for my fellow ADHD'ers*\

We are here to trade(underline), nothing more, nothing less. \
But we really like certainty, not big returns on 1 off event predictions \
So we think using mathematics and science can help make things more CERTAIN.\
But dont delude yourself to believe that beautiful and complex mathematics wins here \
your 1 billion parameter model may be the same as a coin toss or may only give you 1pp predictive edge\
We only want trading-edge(underline) and sometimes being right 60% of the time, may be worse than being right 40%\
How do you measure trading edge?

$$
\text{Edge} \approx \underbrace{\mathbb{E}[\text{exit price} \mid \text{future counterparties}] - \text{entry price}}_{\text{gap you capture}}  - \underbrace{\text{impact}(q, \text{depth})}_{\text{your own footprint}} - \text{costs}
$$

or in otherwords

$$
\text{Edge} \approx \underbrace{\mathbb{E}[\text{R} \mid \text{fture and current state}]}_{\text{gap you capture}}  
$$

This, in its essence, is the generalisation of "buy low sell high" or "sell high buyback low" or "prices arent matching on currency pairs, buy one hedge the other". You get the idea by now...\

Now once again, First and foremost we are TRADERS, than we are mathematicians, computer scientists and physicists\
Alphas are simply ideas that have edge, when we find good ideas, we want to reduce the risks of adverse events. \
Which will happen! Regardless of what your professors have been trying to teach you. \
The world is ugly and chaotic, sometimes 2-2=4 and sometimes 2+2= -3. \
IMC is kind when they let you have some alphas off the bat for free. In reality 55% trading edge is fucking great.\
That is after accounting for adjustments, parameter calibrations, months of research, adjustable stoploss rules, take profit, selecting specific assets, venues and times of trading, accounting for costs, paying upfront subscription fees to lower your trading fees and adding on payments for additional data purchases. \
"just do market making" or "just do buy and hold" with a near 100% edge right off the bat, will make you feel really good about yourself. \
Having access to both price LOB and trades logs essentially hands you the success right off the bat. \
All you need to do now is propose valid trading ideas, those can start out as scientific hypothesis, but must become trading ideas.\
Or search through the massive pile of Alphas accessible here, for one that fits and than improve on it. \
After that you must also look into inventory and execution, but I'd guestimate that alpha and baseline implementation will take you 75% of the way.

One final note, don't use AIs for alpha hunting, beautiful and useful as they are, they have literally no f-ing clue,
Use them instead to speed up EVERYTHING, let them help you test your hypothesis, take the results, evaluate, improve.
If you simply try to jam in "I WANT MEEEAN REVERSION, WHY NO MEAN REVERSION?!!???!?", you will likely get an answer similar to. "The ADF test and Hurst Exponent invalidate your hypothesis", but if you look at the scores they may very likely be close to approved, but far off enough, for the hypothesis to be clearly invalid. This is due the chaotic nature of the markets, accept that defeat, test further, what idiot ideas would survive the chaos and noise?
AI will only do EXACTLY what you ask of it. It can't think on its own, no matter how much OpenAI and Anthropic wants it to.

```text
I hope you all CTRL+ALT+DEFEAT THE MARKET guys and girls.
```

# A long story about markets

## IMC Prosperity what the Fuf is it?
Like sea voyeurs in ancient times before us, we now reach the sandy beaches of "What the Fuf is this?" \
and this time discover it is "IMC Prosperity 5", IMC 3 was beachy sandy and islandy, IMC 4 was Spacy, starry and like landing on a planet.\
Who knows what adventure awaits us in IMC 5 and beyond.

The simple answer, it is an algorithmic trading competition, and likely the second most elaborate one available(footnote).\
A better answer after this, one you will have to think hard about, is: It isn't a mathematics or science competition.\
But a business case competition. I know this is hard for you to understand the meaning and depth to this controversy.\
Because most likely you are a math, computer science, mechanical engineering or physics major and not a "business studies" kind of person.

But this is in fact not a mathematics competition, mathematics plays a large part, but the core skill we are looking for \
is a blend, mathematics helps you refine certain processes in this part, but it is in fact a competition in TRADING.
That must be made abundantly clear and hopefully by the end, it will be ingrained into your soul.

```Text
We are simply doing trading
```

footnote: doing FTMO paper trading demo accounts is likely the closest you will get without actually running an account in the markets. Yes you can also do algo setups here and get your ass handed to you in such a massive way, you would feel like you were run down by a train.

## What the flying fuf do you mean it is about trading?

Trading, unlike what we experience in our physics, mathematics, computer science or engineering courses, is a business subject.
Much more akin to accounting, or supermarket management, than to particle physics at CERN or development of new suspension for cars.
But due to the increasingly optimal use of science in every aspect of our lives, trading, business management and sales have all
benefitted massively from the use of methods we are all learning about in courses in our STEM educations.

What we must discern however is the textbook and academic nature many participants may be arriving with.
Trading, like everything in business and the real world outside of the sheltered lovely life in academia, is ABSOLUTE FUCKING CHAOS, the politeness of "fuf" to cover up fuck must be dropped here. Because reality outside is a warzone.

Where my course instructors and professors may have told me, 2+2 is always 4, you will experience that this is infact only true some of the time.
Which is why we have the analogy with trading edge, preditive edge and alphas.
Those that are able to find the right results from the patterns may also not be the ones that are able to take advantage of it.
Market making for example. Doesn't necessarily rely on correctly predicting next moves, it simply relies on posting the right bids and asks.
Trend following does however depend on predicting when the trend starts and ends. But trend following doesn't actually have to involve profit.

We are therefore not necessarily looking for the best descriptions of the market, we don't need to capture complexity and whether your model is interesting or not, does not really matter. All we want is profit in the real markets.

For a while I had the opportunity of getting the be the acquaintance and drinking buddy of a high ranking quantitative developer in my home country and albeit I didn't understand the deeper meaning at the time, I think it is worth sharing this.

One night while we were out chatting and drinking, he told me that one of our country men who had been working in some top firms were returning home to our country to build his own fund from scratch, this man, one of the highest ranking quants in our country, was freaking starstruck, was considering moving over to that firm. because, and get this, the fella returning home was a specialist in DENOISING processes. He was so sure that this would be a gold mine. To me it sounded like the most boring thing in the world, believing that alpha research was the key to solve all problems.

```
Today I know I was wrong and why Denoising is the gold mine.
```

## So what is the thing with the 2+2 is not 4?

Most of the time, in the markets






**fair value depends on who else is in the market.** The asset is worth whatever the next counterparty will pay, and that depends on whether anyone shows up, how many show up, and how well informed they are.

## The core statement

> **Trading is the act of standing between counterparties whose valuations disagree, and capturing part of the gap. How big a gap exists, and how much of it you keep, depends on how much interest there is and how much competition you face.**

Or more compactly: *buy from those who value it less than the next buyer will; sell to those who value it more than the last seller did.*

## The two axes

Your three scenarios fit on two dimensions:

| | **Low competition** | **High competition** |
|---|---|---|
| **High interest** | *Price setter.* You're the only one supplying liquidity, so you set the spread and earn a rent. Your own impact is the dominant force. | *Error harvester.* The price is roughly efficient, and you profit only from mismatches between buyers and sellers. Your edge shrinks as more skilled players join. |
| **Low interest** | *Illiquid.* There's nobody to trade with. Price is undefined or meaningless, and any trade happens at a large discount or premium. | *Crowded and dead.* Many traders chase a few counterparties. Spreads collapse and nobody makes money. |

**Interest** sets how much flow exists. **Competition** sets who captures it.

## The errors you harvest in the competitive quadrant

These are the drifts and reversions you described. They come from three sources:

1. **Information errors.** A counterparty doesn't know something yet: news, an event, a structural fact.
2. **Behavioural errors.** A counterparty knows but reacts badly: overreaction, anchoring, herding, panic.
3. **Constraint errors.** A counterparty knows and reacts rationally, but is *forced* to trade at a bad price: margin calls, rebalancing, mandates, inventory limits, needing immediacy.

Each source shows up at different horizons. Constraint and behavioural errors dominate at short horizons (microstructure, flow). Information errors tend to play out at medium and long horizons (repricing on fundamentals, regime shifts).

## Two refinements

- **Errors are relative.** You don't need to be right. You only need to be *less wrong than the person on the other side*, by more than your costs and your own price impact. That means edge isn't absolute. It's a function of your counterparties, which closes the loop back to "it depends on your audience."
- **You are part of the market.** In the monopoly and thin-market cases, your own trading moves the exit price. Strictly, the question isn't "is this price good versus fair value?" It's "is this price good versus the price I can *exit* at, given that I'm the one exiting?"

## As a single expression

$$
\text{Edge} \approx \underbrace{\mathbb{E}[\text{exit price} \mid \text{future counterparties}] - \text{entry price}}_{\text{gap you capture}}  - \underbrace{\text{impact}(q, \text{depth})}_{\text{your own footprint}} - \text{costs}
$$

Here the expected exit price depends on interest (is anyone there?) and competition (how much of the gap survives others getting to it first?).

If you want formal anchors for this, two classic models from market microstructure each formalise part of it. Kyle (1985) covers informed traders versus noise traders and how price impact depends on depth. Glosten–Milgrom (1985) explains why spreads exist when some counterparties know more than others. Your framing essentially generalises both by letting participation and competition vary.


*Note: We are therefore looking to hit these ideas best*\

reference   v[i,t] = a[i] + b[i]·F[t]              b from a trailing window\
deviation   d[i,t] = p[i,t] − v[i,t]               scaled by its own trailing volatility\
state       s[t]                                   two or three states at most\
forecast    E[r(i, t→t+h)] = b[i]·E[r(F) | s] − (1 − exp(−κ(s)·h))·d[i,t]


