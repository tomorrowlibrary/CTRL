# Alpha list

> A field guide to alpha hypotheses I have worked with or would encourage students to investigate for IMC Prosperity and systematic trading. These are **research candidates, not promised profitable strategies**. Historical Prosperity examples and extensions are identified in context.

**86 ideas across 8 categories.**

An alpha starts as a falsifiable proposal. It earns the name *validated alpha* only after signal, fills, risk and costs hold up out of sample. A good directional forecast can still lose money; a spread or market-making strategy need not forecast the absolute market direction.

For every idea, write: **what you observe → what you predict → how you trade → when you exit → what could make you wrong**. When backtesting resting orders from candles, a high/low touch is not a confirmed fill.

## Categories

- [Microstructure & liquidity](#microstructure--liquidity) — 15 ideas
- [Mean reversion & dislocations](#mean-reversion--dislocations) — 13 ideas
- [Trend following & continuation](#trend-following--continuation) — 12 ideas
- [Statistical & relative-value arbitrage](#statistical--relative-value-arbitrage) — 15 ideas
- [Volatility, jumps & crises](#volatility-jumps--crises) — 10 ideas
- [Seasonality, events & information](#seasonality-events--information) — 7 ideas
- [Derivatives, options & carry](#derivatives-options--carry) — 6 ideas
- [IMC Prosperity-specific opportunities](#imc-prosperity-specific-opportunities) — 8 ideas

## How to read the list

Each hypothesis includes a first experiment, the data required and a failure mode. Studies in the attached notes found several statistically interesting patterns but did **not** establish a general net-profitable live strategy.

## Microstructure & liquidity

Where matching, depth, competition and adverse selection produce opportunities.

### MI-01 — Order-flow imbalance

Net aggressive buying versus selling can predict the next price movement.

**First test:** Condition the next 1–60 seconds or minute return on signed taker-flow imbalance.  
**Failure mode:** The information is already in price, or the signal reverses before execution.  
**Data:** Trades + aggressor side
**Research note:** In supplied flow tests, 1-minute effects existed, then reversed at longer horizons.

### MI-02 — Best-quote / microprice imbalance

More depth at one best quote than the other can tilt the expected next mid-price.

**First test:** Compare the microprice with the mid-price and predict the next tick.  
**Failure mode:** Displayed size is cancelled or the move is too small for fees.  
**Data:** L1 order book

### MI-03 — Queue depletion

A nearly exhausted best bid or ask can signal an imminent quote change.

**First test:** Estimate depletion probability from queue size and arrival/cancellation intensity.  
**Failure mode:** Replenishment changes the queue, or the order is behind others.  
**Data:** L2 order book

### MI-04 — Order-book pull imbalance

Rapid cancellations on one side may precede a directional price move.

**First test:** Measure bid-versus-ask withdrawn depth before each mid-price change.  
**Failure mode:** Cancellations are reactive, timestamp quality is insufficient.  
**Data:** L2 book updates
**Research note:** Preliminary short-book samples only; broader out-of-sample testing is needed.

### MI-05 — Absorption of aggressive flow

Heavy aggressive trading with little price movement may reveal deep opposing liquidity.

**First test:** Find high-taker-flow/low-impact events; test next move and replenishment.  
**Failure mode:** Absorption is not confirmed and the next move is continuation.  
**Data:** Trades + L2 book

### MI-06 — Iceberg and hidden-liquidity replenishment

Repeated executions at one level without visible depletion suggest reserve liquidity.

**First test:** Detect repeated prints at the same level with refreshed displayed size.  
**Failure mode:** Hidden size is not identifiable from the available feed.  
**Data:** Trade + book messages

### MI-07 — Wide-spread market making

Post a bid and an ask and collect spread when uninformed takers cross.

**First test:** Compare captured spread with 1-, 10-, and 60-second post-fill markout.  
**Failure mode:** One-sided informed flow creates losses larger than spread captured.  
**Data:** L2 order book

### MI-08 — Inventory-skewed quoting

Shift bid/ask quotes to encourage trades that rebalance inventory.

**First test:** Compare symmetric quotes with inventory-aware quotes at fixed limits.  
**Failure mode:** The inventory penalty overwhelms spread revenue.  
**Data:** L2 order book

### MI-09 — Reference-price market making

Quote around a fair-value estimate rather than the current mid.

**First test:** Compare constant anchor, weighted-mid and external-reference estimators.  
**Failure mode:** The reference is stale or differs structurally from local value.  
**Data:** Trade + book

### MI-10 — Liquidity-void / gap capture

Keep passive orders in thin zones where a temporary sweep may reach them.

**First test:** Measure actual fills, markouts and reversion after depth disappears.  
**Failure mode:** No one reaches the quote, or the gap is justified repricing.  
**Data:** L2 order book

### MI-11 — Whale-sweep wick ladder

Rest orders several volatility units away and refill after a large market order.

**First test:** Compare touch versus trade-through fills after extreme intrabar wicks.  
**Failure mode:** The sweep starts a crash or a price shift that never refills.  
**Data:** 1m bars + L2 validation
**Research note:** A promising-looking touch-fill is not proof of an executable maker edge.

### MI-12 — Sweep continuation

Large one-sided aggressive flow may signal more pressure rather than reversion.

**First test:** After depth-consuming events, test continuation against matched non-sweeps.  
**Failure mode:** The initial sweep exhausts demand and price reverses.  
**Data:** Trades + L2 order book

### MI-13 — Spread normalization

An abnormally wide quoted spread may narrow once liquidity returns.

**First test:** Post passively when spread widens; measure realized spread and fill risk.  
**Failure mode:** One side fills first during further adverse repricing.  
**Data:** L1/L2 order book

### MI-14 — Price-impact and resiliency

Markets that absorb or refill volume quickly may offer different execution edges.

**First test:** Estimate impact per unit signed notional and speed of recovery.  
**Failure mode:** Changing impact estimates are noisy and quote timing is unrealistic.  
**Data:** Trades + order book

### MI-15 — Counterparty-informed trades

Repeated trades by the same identifiable participant may reveal skill or intent.

**First test:** If identities exist, compare returns after different participant histories.  
**Failure mode:** IDs are missing, anonymized, or chosen after inspecting the future.  
**Data:** IMC trade observations

## Mean reversion & dislocations

Where temporary deviations may be followed by a return towards a reference.

### ME-01 — Dip and refill

Buy a price drop with a passive bid; sell when price returns to the old reference.

**First test:** Try 0.5%, 1% and 2% resting depths with 1–4 hour exits.  
**Failure mode:** Large losses on non-refilling drops outweigh frequent small wins.  
**Data:** 1m bars + fill model
**Research note:** The flagship worked example; gross fills should not be confused with true queue fills.

### ME-02 — Thin-volume drop reversal

A sharp fall with unusually low participation might be temporary.

**First test:** Condition -0.3%, -0.5% and -1% drops on trailing volume percentile.  
**Failure mode:** Low volume can indicate absent demand; prior tests were negative.  
**Data:** 1m bars
**Research note:** Not supported as a general strategy in the supplied cross-market studies.

### ME-03 — Capitulation / high-volume bounce

An extreme downside move with heavy participation may exhaust sellers.

**First test:** Compare high- versus low-participation drops, with fixed future horizons.  
**Failure mode:** Heavy trading may signal genuine information and more downside.  
**Data:** 1m bars
**Research note:** Observed in some discovery samples, but did not persist in the supplied non-crypto holdout.

### ME-04 — Rolling Bollinger-band fade

Fade price deviations of 2–3 standard deviations from a rolling mean.

**First test:** Specify past-only 20/50/100-bar bands, entry, target and time exit.  
**Failure mode:** Price trends instead of reverting; time-varying mean leaks.  
**Data:** 1m bars
**Research note:** Simple unconditional sigma fades largely failed in the supplied tests.

### ME-05 — Detrended log-price fade

Remove a trailing trend before trading extreme deviations around it.

**First test:** Use an expanding or rolling past-only trend fit and residual z-score.  
**Failure mode:** The trend and intercept change abruptly.  
**Data:** 1m bars

### ME-06 — Ornstein–Uhlenbeck residual reversion

If a spread behaves like a stationary process, use its speed of reversion.

**First test:** Fit dX = kappa(mu-X)dt + sigma dW; test half-life and exits.  
**Failure mode:** The fitted mean or relationship is not stable.  
**Data:** Paired price bars

### ME-07 — RSI exhaustion

Overbought and oversold readings may foreshadow a reversal.

**First test:** Test RSI threshold fades with trend and volatility controls.  
**Failure mode:** Oversold markets remain oversold through a strong trend.  
**Data:** 1m or 1h bars

### ME-08 — VWAP deviation fade

Return towards a session or rolling volume-weighted reference.

**First test:** Measure incremental reversion relative to matched-distance mirror levels.  
**Failure mode:** VWAP is not a magnet and reference is endogenous.  
**Data:** OHLCV
**Research note:** A general VWAP magnet was not supported in the supplied research log.

### ME-09 — Range-edge maker orders

Place quotes around repeated highs and lows in a stable range.

**First test:** Compare reversals from tested range edges to random equivalent levels.  
**Failure mode:** The range breaks exactly when inventory accumulates.  
**Data:** OHLCV + L2

### ME-10 — Failed-breakout reversal

A break above resistance that quickly returns inside may reverse.

**First test:** Define break and failed acceptance using only completed bars.  
**Failure mode:** False breakouts cannot be identified until too late.  
**Data:** OHLCV

### ME-11 — Post-jump partial retracement

An abrupt short-term jump may partially unwind before resuming.

**First test:** Measure 1-, 5-, 10-minute jump retracements by size and sign.  
**Failure mode:** The price move is an information update, not an overreaction.  
**Data:** 1m bars

### ME-12 — Slope-flattening / zero-tangent reversal

A turning trend slope may precede a short-term price rebound.

**First test:** Measure past-only EMA/regression slope approaching zero after an extreme.  
**Failure mode:** Flattening is merely a lagging description.  
**Data:** OHLCV

### ME-13 — Denoised spread / SSA reversion

Extract a lower-noise relative-value residual before trading deviations.

**First test:** Compare rolling SSA residuals with plain spread z-scores.  
**Failure mode:** Full-sample smoothing leaks future data; denoising removes real moves.  
**Data:** Paired price bars

## Trend following & continuation

Where information or persistent flows make a movement continue.

### TR-01 — Moving-average crossover

Follow a trend when a faster average crosses above a slower average.

**First test:** Compare 5/20/40, 16/64 and 28/56-day versions after costs.  
**Failure mode:** Whipsaw and high turnover.  
**Data:** OHLCV

### TR-02 — Time-series momentum

A strong positive trailing return may continue over the next horizon.

**First test:** Rank forecast horizons from minutes to months using future net returns.  
**Failure mode:** Persistence is weaker than fees or reverses by regime.  
**Data:** OHLCV

### TR-03 — Cross-sectional momentum

Buy stronger assets and sell or underweight weaker ones.

**First test:** Rank by 28/56-day total and risk-adjusted returns; compare equal weight.  
**Failure mode:** Common market beta dominates, or ranking reverts.  
**Data:** Multi-asset bars
**Research note:** Cross-market tests in the supplied report were not consistently positive out of sample.

### TR-04 — Donchian channel breakout

Trade when price breaks above a trailing high or below a trailing low.

**First test:** Use causal 20/50/100-bar highs/lows; assess false breaks.  
**Failure mode:** False breakouts during flat, volatile trading.  
**Data:** OHLCV

### TR-05 — Volume-confirmed level push

A move through resistance on persistent volume might continue.

**First test:** Contrast rising, falling and constant volume at matched price levels.  
**Failure mode:** Volume is concurrent not predictive; direct study failed.  
**Data:** OHLCV
**Research note:** Rising-volume pushes did not outperform faded-volume pushes in supplied non-crypto tests.

### TR-06 — Quiet pullback in an uptrend

A temporary lull inside an established trend may precede continuation.

**First test:** Condition pullbacks on recent efficiency and low volume.  
**Failure mode:** The lull marks the beginning of reversal.  
**Data:** OHLCV
**Research note:** Quiet stretches inside trends preceded continuation in one supplied research test.

### TR-07 — Range expansion with directional efficiency

The shift from choppy oscillations to displacement may mark a new trend.

**First test:** Compare range, net return, and efficiency ratio before next 1–4 hours.  
**Failure mode:** Breakout signal arrives too late or exhausts itself.  
**Data:** OHLCV

### TR-08 — Post-jump follow-through

A large price jump may forecast further movement in the same direction.

**First test:** Measure direction and follow-through over 1, 5, 15 and 60 minutes.  
**Failure mode:** Aftershocks are mostly volatility without directional predictability.  
**Data:** 1m bars

### TR-09 — Higher-low / higher-high structure

Confirmed swing lows and highs may identify trend continuation.

**First test:** Mark pivots only after they can be known and record signal delay.  
**Failure mode:** Pivot labels repaint when discovered after the fact.  
**Data:** OHLCV

### TR-10 — Trend acceleration / change point

An online detector may find persistent drift shifts earlier than moving averages.

**First test:** Compare causal CUSUM alerts with momentum of identical lookback.  
**Failure mode:** False alarms and detector lag.  
**Data:** OHLCV

### TR-11 — Breadth-confirmed trend

A trend accompanied by broad participation may persist longer.

**First test:** Compare index returns with percentage of components moving the same way.  
**Failure mode:** Members simply share exposure to the same market factor.  
**Data:** Multi-asset bars

### TR-12 — Momentum across timescales

Alignment of short, medium and long horizons may predict continuation.

**First test:** Test whether multi-horizon agreement adds to the strongest single horizon.  
**Failure mode:** Overlapping bars mechanically produce agreement.  
**Data:** OHLCV

## Statistical & relative-value arbitrage

Where connected prices disagree, temporarily or structurally.

### ST-01 — Cointegrated pairs Z-score

Trade two related assets when a stationary spread departs from equilibrium.

**First test:** Estimate hedge ratio on the past; z-score the spread, trade both legs.  
**Failure mode:** Correlation is not cointegration; spread relation breaks.  
**Data:** Paired bars

### ST-02 — Lead–lag jumps

A leader jumps before a slower follower fully reprices.

**First test:** After leader jumps, test executable follower returns at 1–60 seconds/minutes.  
**Failure mode:** Follower adjusts before an order could arrive.  
**Data:** Multi-asset tick/trades
**Research note:** BTC-to-alt propagation was small in the supplied test and may not survive costs.

### ST-03 — Lead–lag trends

A follower drifts behind a leader over a longer horizon.

**First test:** Model delayed beta-adjusted moves and compare to common-factor returns.  
**Failure mode:** The apparent lag is just correlated simultaneous movement.  
**Data:** Multi-asset bars

### ST-04 — Basket / ETF premium

The basket price diverges from the sum of its priced components.

**First test:** Calculate a value-matched basket spread; test convergence and hedge both sides.  
**Failure mode:** Fees, conversions, and contract terms make fair values inconsistent.  
**Data:** Constituent prices

### ST-05 — One-asset basket mispricing

One component temporarily disagrees with a common basket move.

**First test:** Predict the residual to a trailing factor benchmark, not just raw prices.  
**Failure mode:** Idiosyncratic repricing is permanent.  
**Data:** Multi-asset bars

### ST-06 — Cross-exchange price dislocation

Buy on the cheaper venue and sell on the more expensive one.

**First test:** Calculate synchronized executable bid/ask spreads net of fees and transfer risk.  
**Failure mode:** Quotes are stale, inventory sits on wrong venue, or arbitrage is faster.  
**Data:** Cross-venue L1

### ST-07 — Latency / news repricing

One venue or asset has not yet reflected public information.

**First test:** Use publication/receipt timestamps and executable post-news order prices.  
**Failure mode:** Information was already priced or venue latency cannot be beaten.  
**Data:** Tick + event times

### ST-08 — Triangular FX parity

Three exchange rates imply a small inconsistent conversion cycle.

**First test:** Multiply executable conversion rates, then subtract three spreads and fees.  
**Failure mode:** Inconsistent timestamps and settlement frictions.  
**Data:** FX bid/ask

### ST-09 — Spot–futures basis

Spot and futures prices may converge according to contract and carry.

**First test:** Estimate basis net of rates, financing, funding and settlement.  
**Failure mode:** Basis is compensation for risk and capital constraints.  
**Data:** Spot + futures

### ST-10 — Perpetual–spot funding spread

Funding and basis may pay for a hedged cash-and-carry position.

**First test:** Recompute future net funding with fees, hedge costs and mark-to-market risk.  
**Failure mode:** Funding flips and liquidations cause losses.  
**Data:** Spot + perps

### ST-11 — Factor-neutral residual reversion

Hedge common market, sector and style factors to isolate a mispriced residual.

**First test:** Estimate rolling beta and spread; test residual half-life in unseen dates.  
**Failure mode:** Factor loading changes or residual does not mean-revert.  
**Data:** Multi-asset bars

### ST-12 — Relative-value dispersion trade

A highly dispersed set of related assets may reconverge.

**First test:** Sort factor-neutral residuals; buy cheap, sell rich, control beta.  
**Failure mode:** Dispersion reflects diverging fundamentals.  
**Data:** Multi-asset bars

### ST-13 — Cross-sectional sector rotation

Leadership migrates between sectors or coin groups as market states change.

**First test:** Predict future group-relative returns using only prior breadth and factor signals.  
**Failure mode:** Estimated leadership is too slow or overfit.  
**Data:** Multi-asset bars

### ST-14 — Cross-venue futures leads spot

Futures price discovery may precede spot adjustment.

**First test:** Time-align sub-second quote changes and simulate realistic order delay.  
**Failure mode:** The adjustment is faster than connectivity and feed latency.  
**Data:** Cross-venue tick
**Research note:** A short preliminary sample in the supplied notes showed sub-second lead, not a tradable edge.

### ST-15 — Relative value around external reference

One venue temporarily diverges from a reference adjusted for systematic differences.

**First test:** Post at an offset from reference; observe fill markout and convergence.  
**Failure mode:** Reference is stale, basis is legitimate, or only bad fills execute.  
**Data:** Cross-venue L1 + L2

## Volatility, jumps & crises

Where the distribution, intensity or propagation of movement changes.

### VO-01 — Jump clustering / aftershock intensity

A large shock can raise the conditional probability of another shock.

**First test:** Compare the jump hazard after 0, 1 and multiple recent shocks.  
**Failure mode:** Higher jump risk has no predictable direction.  
**Data:** 1m bars
**Research note:** Strong statistical shock clustering in supplied tests, not yet a validated alpha.

### VO-02 — Seismic precursor

Widening ranges, volume ramping and path efficiency may precede a large jump.

**First test:** Predict jump occurrence using lagged features against a volatility-only model.  
**Failure mode:** The warning is simultaneous with the move or too broad to trade.  
**Data:** 1m bars
**Research note:** Multiple precursors showed statistical association in the six-coin study.

### VO-03 — Cross-asset shock contagion

Shocks in leaders can be followed by shocks in peer assets.

**First test:** Count peers shocked before each target-asset event; predict hazard.  
**Failure mode:** All assets react simultaneously to common news.  
**Data:** Multi-asset 1m

### VO-04 — Volatility breakout

Low recent realized volatility followed by rising participation may precede larger moves.

**First test:** Estimate future range/variance; test a directional variant separately.  
**Failure mode:** Higher volatility has no predictable sign.  
**Data:** 1m bars

### VO-05 — Volatility contraction after panic

Extreme variance may normalize as forced trading subsides.

**First test:** Forecast future realized volatility and choose exposure to variance decline.  
**Failure mode:** Shock clustering keeps volatility elevated.  
**Data:** OHLCV + options if trading vol

### VO-06 — Volatility term-structure stress

Short-horizon volatility outpacing long-horizon volatility may identify stress.

**First test:** Compare short/long vol ratio to future jump and tail-loss frequency.  
**Failure mode:** Ratio increases mechanically from temporary noise.  
**Data:** 1m bars

### VO-07 — Downside versus upside semivariance

Negative shocks may have different future effects than equal positive shocks.

**First test:** Condition next volatility and return on signed realized semivariance.  
**Failure mode:** Direction disappears after controlling current volatility.  
**Data:** 1m bars

### VO-08 — Tail-dependence risk-off

Simultaneous extreme losses may make diversification fail.

**First test:** Estimate lower-tail co-exceedance and future multi-asset drawdown.  
**Failure mode:** Sample too small to estimate tails reliably.  
**Data:** Multi-asset bars

### VO-09 — Regime transition hazard

Market stress may build before a switch from calm to turbulent.

**First test:** Compare calibrated state-transition hazard against simple vol and CUSUM.  
**Failure mode:** Model warns late or exits every ordinary pullback.  
**Data:** Multi-asset bars

### VO-10 — Volatility-scaled resting quotes

Quotes placed at volatility-expected excursion distances may catch swings.

**First test:** Compare fixed-percent and vol-scaled maker ladders with queue simulation.  
**Failure mode:** Predicted excursion comes with permanently adverse movement.  
**Data:** OHLCV + L2

## Seasonality, events & information

Where timing or uneven access to new information changes who trades.

### IN-01 — Time-of-day liquidity cycle

Participation and spread vary across trading hours.

**First test:** Estimate time-of-week normalized fill, markout and spread by hour.  
**Failure mode:** Seasonality is already anticipated by quoting competition.  
**Data:** Trades + book

### IN-02 — Session-open momentum or reversal

Opening participation may change expected moves after market opens.

**First test:** Compare first 1–30 minutes after US/Europe opens to matched control hours.  
**Failure mode:** Macro releases confound the session effect.  
**Data:** OHLCV + calendar
**Research note:** Simple US-open trading rules were not supported in the supplied log.

### IN-03 — News surprise drift

A surprising announcement may drive continued repricing.

**First test:** Compare released value against timestamped pre-release consensus.  
**Failure mode:** News was anticipated or market reacts before you receive it.  
**Data:** Timestamped news + ticks

### IN-04 — Earnings / event post-announcement drift

Stocks sometimes continue to adjust after an earnings surprise.

**First test:** Use point-in-time earnings surprise and next-session excess returns.  
**Failure mode:** Survivorship, borrow costs and post-release lookahead.  
**Data:** Fundamentals + equities

### IN-05 — Sentiment-flow imbalance

Extreme news or social sentiment may correlate with later returns.

**First test:** Time-stamp document availability; compare sentiment to return/vol controls.  
**Failure mode:** Bots, selection effects and delayed ingestion destroy the lead.  
**Data:** News / social + bars

### IN-06 — Calendar rebalancing demand

Index changes or predictable portfolio flows may move prices temporarily.

**First test:** Study events known ahead of time and executable pre/post flow.  
**Failure mode:** Trades are pre-anticipated by many faster participants.  
**Data:** Event calendar + prices

### IN-07 — Funding/settlement-clock effects

Clock-based settlement, funding and auction schedules change trading incentives.

**First test:** Compare spread and price behaviour around known funding/auction timestamps.  
**Failure mode:** Payment rules differ by product or costs dominate.  
**Data:** Contract schedule + prices

## Derivatives, options & carry

Where related contracts or volatility exposures have a measurable relative value.

### DE-01 — Options volatility smile dislocation

An option quote may be cheap/rich relative to a fitted volatility surface.

**First test:** Fit the smile without the evaluated quote; delta-hedge and score residuals.  
**Failure mode:** Surface fit, inventory and hedge costs overwhelm residual.  
**Data:** Options chain + underlying

### DE-02 — Put–call parity

Equivalent call, put and forward positions should satisfy pricing relationships.

**First test:** Compute executable parity bounds, include exercise and financing.  
**Failure mode:** American exercise, dividends and spread cause apparent violations.  
**Data:** Options chain

### DE-03 — Calendar-spread relative value

Option or futures maturities disagree with a coherent term structure.

**First test:** Compare net maturity spreads conditional on carry and volatility.  
**Failure mode:** Different maturities carry different legitimate risk premia.  
**Data:** Options or futures

### DE-04 — Delta-hedged implied vs realized volatility

Trade volatility when implied variance differs from realistically forecast realized variance.

**First test:** Backtest delta-hedged option PnL with discrete hedges and fees.  
**Failure mode:** Volatility risk premium, jumps and hedge costs dominate.  
**Data:** Options + underlying

### DE-05 — Gamma scalping

Re-hedge a long-gamma position as price oscillates.

**First test:** Compute realized hedging gains against option theta and trades.  
**Failure mode:** Realized movement insufficient to cover premium and hedging.  
**Data:** Options + ticks

### DE-06 — Conversion / creation arbitrage

Transform products at contractual conversion rates when implied values disagree.

**First test:** Check full conversion mapping, timing and resulting inventory.  
**Failure mode:** Conversion caps or settlement rules make profit unavailable.  
**Data:** Contract rules + books

## IMC Prosperity-specific opportunities

Where a competition mechanic, observation or designed product creates an exploitable rule.

### IM-01 — Fixed fair-value anchor

A competition product may trade around a known or nearly fixed fair price.

**First test:** Infer a constant anchor from early data and quote around it.  
**Failure mode:** The anchor changes across rounds or products.  
**Data:** Prosperity historic books
**Research note:** The CTRL site lists the fixed 10,000 anchor as a historical pattern.

### IM-02 — Large-quote weighted mid (wall-mid)

Big posted quotes may provide better information about fair value than the raw midpoint.

**First test:** Compare quoted size-weighted mid to later traded prices.  
**Failure mode:** Walls are strategic or can be cancelled.  
**Data:** Prosperity order books
**Research note:** Historically discussed by past Prosperity teams.

### IM-03 — Basket versus constituents

Products with fixed recipes may diverge from their ingredient value.

**First test:** Build exact basket valuation from specifications, then hedge mispricing.  
**Failure mode:** Recipe, conversion rules or position limits change.  
**Data:** Prosperity product books
**Research note:** The CTRL site lists basket premium patterns.

### IM-04 — Volatility-smile options

Options priced inconsistently across strikes may offer relative value.

**First test:** Fit strike-dependent IV and compute executable spread portfolios.  
**Failure mode:** Delta/vega risk and product-specific settlement dominate.  
**Data:** Prosperity options books
**Research note:** The CTRL site lists volatility-smile scalping.

### IM-05 — Conversion against local market

Buy/sell on one market and convert to another representation or location.

**First test:** Compute all conversion costs and limits per round.  
**Failure mode:** Conversion is capped, delayed or contingent.  
**Data:** Prosperity rules + books
**Research note:** Prosperity examples include Orchids-style conversion opportunities.

### IM-06 — Counterparty ID / informed participant

Some identifiable bots may have systematically informative trading.

**First test:** Track participant-conditioned future prices only from already observed trades.  
**Failure mode:** The counterparty is absent or pattern is a historical coincidence.  
**Data:** Prosperity trade records
**Research note:** Past solutions discuss Olivia/Rhianna-style signals.

### IM-07 — Repeated historical price path

A product or order book may repeat an earlier edition’s data.

**First test:** Match partial current history to prior editions without peeking ahead.  
**Failure mode:** The next edition changes the pattern or timestamps.  
**Data:** Historical Prosperity files
**Research note:** The public CTRL site mentions repeated historical order books.

### IM-08 — Daily extreme / known participant behavior

A recurrent bot may appear near session lows or highs.

**First test:** Identify real-time observable participant behavior, then benchmark extremes.  
**Failure mode:** Daily lows/highs are known only after the session.  
**Data:** Prosperity trade records
**Research note:** The CTRL research page discusses historical day-extreme participants.

## Not alphas by themselves: useful overlays

These can improve the reliability of a strategy, but the mathematical model alone is not a trading edge.

- **Market-state filters:** Only activate a strategy when a causal trend/volatility/liquidity state supports it.
- **Risk-off crash alarms:** Reduce exposure when calibrated jump or tail risk is high.
- **Time-varying correlations:** Avoid pretending a basket is diversified when strategies share a stress exposure.
- **Path signatures / wavelets:** Ask whether path order or time-frequency information improves a specified forecast.
- **Portfolio volatility targeting:** Choose size and risk budgets; do not present reduced drawdown as return alpha.
- **Execution routing / TWAP / VWAP:** Improve fills and market impact for an already-chosen trade; not a predictive alpha by itself.
- **ML, neural nets, HMMs and RL:** These are tools for estimating signals or policies, not inherently profitable alphas.

## What our previous experiments caution against

- **Low-volume dips, simple 2–3σ fades and volume-confirmed level pushes** did not reliably make money in the supplied cross-market tests. Retest a revised mechanism, not the original unprofitable rule.
- **BTC-to-altcoin lead–lag and taker-flow effects** were measurable in some windows, but often tiny, short-lived or reversed later; prediction is not sufficient after costs.
- **Shock clustering and range/volume precursors** are meaningful statistical features, but predicting volatility is not the same thing as predicting a profitable direction.
- **Maker backtests on one-minute OHLCV** can overstate profitability by granting fills at a mere touch. Queue priority, trade-through tests, partial fills and adverse selection belong in every realistic test.
- **Historical IMC patterns** are clues about mechanics to check again, not assurances that the next competition reuses them.

## Student research card template

```text
Name and category:
Mechanism (who pays, and why?):
Observable signal at decision time:
Expected sign or distribution / horizon:
Entry, exit, size, inventory limits:
Data, timestamps, and actual fill rule:
Fees, spread, impact, conversion or hedge costs:
Null: random/side-flipped/simpler model:
Split: discovery → validation → untouched test:
Failure regimes and worst adverse excursion:
Net bps/trade, Sharpe, drawdown, capacity:
Decision: reject / revise / paper trade / deploy:
```

Related: [Market dynamics](../market-dynamics/index.html) · [CTRL overview](../index.html) · [Data](../data/index.html) · [Execution](../execution-backtesting/index.html).
