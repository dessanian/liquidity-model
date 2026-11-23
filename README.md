# Liquidity Model

## Methodology & System Overview
Before diving into the findings, here is a quick overview of what we built to construct this model:

Data Ingestion: Integrated daily macro data from FRED (Fed Target Rate, EFFR, Fed Balance Sheet, Overnight Reverse Repos, Treasury General Account, and Corporate Credit Spreads) alongside market data from Yahoo Finance (VIX, Dollar Index, major currency pairs, and index ETFs).

Feature Engineering: Standardized rolling 52-week (1-year) Z-scores of each metric, mapping them directionally so that a positive value indicates expanding market liquidity and a negative value represents tightening liquidity.

Scaling & Normalization: Clipped and scaled each metric to a standard  [−10,10]  boundary to avoid distortion from extreme macro shocks.

Composite Score & Regimes: Created a single unified Composite Liquidity Score mapped to a  [−100,100]  range, dividing market conditions into 5 regimes (Strong Risk-On, Risk-On, Neutral, Defensive, and Deleveraging).

**Summary of Findings & Key Tactical Takeaways**

**Current Regime Alignment:**
As of the latest data point (November 22, 2026), the Composite Liquidity Score is -48.07, classifying the current market environment under a Deleveraging regime. This represents a progressive deterioration from the Neutral and Defensive scores observed earlier in late 2026, signaling that systemic conditions have reached an acute phase of liquidity tightening (driven by high real yields, Fed balance sheet contraction, and rising global dollar strength).

2. Backtest Asset Performance Analysis
Our historical backtest (2015–2026) validates the model's structural design by confirming how differently asset classes behave under varying liquidity constraints:

**Risk-On / Neutral Regimes (Score > -10):**

Equities: High-beta and growth sectors thrive. The Nasdaq (QQQ) leads with an average forward weekly return of +0.474% under Risk-On and +0.419% under Neutral conditions.

Commodities: Copper (economic growth proxy) delivers its best returns during Neutral environments (+0.540% weekly return), reflecting robust industrial demand without the headwinds of restrictive liquidity.

**Defensive Regimes (Score between -10 and -40):**

Equity Performance Flattens: SPY returns compress to +0.031% weekly, while QQQ (-0.321%) and IWM (-0.355%) enter negative territory.
Commodity Drawdowns: Copper and Gold show severe average weekly losses (-1.010% and -2.312%, respectively), signaling asset liquidations and deflationary pressures as liquidity starts to dry up.

**Deleveraging Regimes (Score < -40):**

Severe Equity Drawdowns: Broad equities experience steep losses. Nasdaq (QQQ) plummets with an average weekly forward return of -4.981%.
Industrial Hard Stop: Copper drops an average of -3.724% weekly, confirming the absolute destruction of growth and cyclical demand.
Gold as the Ultimate Safe-Haven: Gold shines during deleveraging spikes, delivering an outstanding average forward weekly return of +4.514%. This behavior highlights its role as a premier systemic insurance asset during structural liquidity crises.


### 3. Tactical Asset Allocation Rule-of-Thumb

| Composite Score Range | Liquidity Regime | Preferred Asset Exposure | Asset Classes to Avoid / Underweight |
| :--- | :--- | :--- | :--- |
| **>= 40** | **Strong Risk-On** | High-Beta Equities (QQQ, IWM), Industrial Metals (Copper), Credit | Long-Duration Treasuries, Cash |
| **10 to 40** | **Risk-On** | Equities (SPY, QQQ), Corporate Bonds (HYG) | Cash, Gold |
| **-10 to 10** | **Neutral** | Broad Equities (SPY), Gold, Copper | None (Balanced allocation) |
| **-40 to -10** | **Defensive** | High Quality Corporate Credit (HYG), Cash | Small Caps (IWM), Cyclical Commodities |
| **< -40** | **Deleveraging** | **Gold**, Cash, Long-Duration Treasuries | Equities (QQQ, SPY), Industrial Metals (Copper) |
