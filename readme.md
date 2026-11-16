

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

Note from the author:
This year, for IMC prosperity 5, 2027, I will not be participating much.\
After having scored to my own satisfaction on a range of challenges over the years,\
Wunderfund RNN, Connectome and IMC 4 as the last ones. I have taken the opportunity to do my own algorithmic trading in the markets.\
This, as you may understand, requires more focus and attention than the IMC challenge.

As interesting and worthwhile as IMC Prosperity is, it is sadly in no way equal to the actual\
challenge of participating in the markets in real time. I do however STRONGLY recommend participation in\
IMC Prosperity, it is a genuinely beautiful setup and helps you move from 0 to hero in no time.

So without further ado, here are the secrets to the universe as we know it...

---

## No story telling please!
*Note: I was recently told by my partner, that I am a fucking storyteller and sometimes we just need a bloody summary, rather than a story. So here is a summary for my fellow ADHD'ers*\

We are here to trade, nothing more, nothing less. \
We like mathematics and certainty, not big returns on 1 time event predictions \
Do not delude yourself to believe that beautiful and complex mathematics wins here \
your 1 billion parameter model may be the same as a coin toss or may only give you 1pp predictive edge\
We only want trading edge and sometimes being right 60% of the time, may be worse than being right 40%\
How do you measure trading edge?

$$
\text{Edge} \approx \underbrace{\mathbb{E}[\text{exit price} \mid \text{future counterparties}] - \text{entry price}}_{\text{gap you capture}}  - \underbrace{\text{impact}(q, \text{depth})}_{\text{your own footprint}} - \text{costs}
$$

or in otherwords

$$
\text{Edge} \approx \underbrace{\mathbb{E}[\text{R_{+}} \mid \text{fture and current state}]}_{\text{gap you capture}}  
$$

This in its essence is the generalisation of "buy low sell high" or "sell high buyback low" or "prices arent matching on currency pairs, buy one hedge the other". You get the idea by now...\
First and foremost we are TRADERS, than we are mathematicians, computer scientists and physicists\
Alphas are simply ideas that have edge,










## IMC Prosperity what the F- is it?
Like sea voyeurs in ancient times before us, we now reach the sandy beaches of "What the F-f is this?" 
and this time discover it is "IMC Prosperity 5", IMC 3 was beachy sandy and islandy, IMC 4 was Spacy, starry and like landing on a planet.
Who knows what adventure awaits us in IMC 5 and beyond.

The simple answer, it is an algorithmic trading competition, and likely the second most elaborate one available.
A better answer after this, one you will have to think hard about, is. It isn't a mathematics or science competition.
But a business case competition. I know this is hard for you to understand the meaning and depth to this controversy.
Because most likely you are a math, computer science, mechanical engineering or physics major and not a "business studies" kind of person.

But this is in fact not a mathematics competition, mathematics plays a large part, but the core skill we are looking for
is a blend, mathematics helps you refine certain processes in this part, but it is in fact a competition in TRADING.
That must be made abundantly clear and hopefully by the end, it will be ingrained into your soul.

### What the flying fuf do you mean it is about trading?




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













data

research

alpha

risk

inventory

execution
