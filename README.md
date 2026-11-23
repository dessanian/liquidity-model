# Liquidity Model

## Methodology & System Overview
Before diving into the findings, here is a quick overview of what we built to construct this model:

Data Ingestion: Integrated daily macro data from FRED (Fed Target Rate, EFFR, Fed Balance Sheet, Overnight Reverse Repos, Treasury General Account, and Corporate Credit Spreads) alongside market data from Yahoo Finance (VIX, Dollar Index, major currency pairs, and index ETFs).

Feature Engineering: Standardized rolling 52-week (1-year) Z-scores of each metric, mapping them directionally so that a positive value indicates expanding market liquidity and a negative value represents tightening liquidity.

Scaling & Normalization: Clipped and scaled each metric to a standard  [−10,10]  boundary to avoid distortion from extreme macro shocks.

Composite Score & Regimes: Created a single unified Composite Liquidity Score mapped to a  [−100,100]  range, dividing market conditions into 5 regimes (Strong Risk-On, Risk-On, Neutral, Defensive, and Deleveraging).

## Summary of Findings & Key Tactical Takeaways

### 1. Current Regime Alignment:
As of the latest data point (November 22, 2026), the Composite Liquidity Score is -48.07, classifying the current market environment under a Deleveraging regime. This represents a progressive deterioration from the Neutral and Defensive scores observed earlier in late 2026, signaling that systemic conditions have reached an acute phase of liquidity tightening (driven by high real yields, Fed balance sheet contraction, and rising global dollar strength).

### 2. Backtest Asset Performance Analysis
Our historical backtest (2015–2026) validates the model's structural design by confirming how differently asset classes behave under varying liquidity constraints:

### Risk-On / Neutral Regimes (Score > -10):

* Equities: High-beta and growth sectors thrive. The Nasdaq (QQQ) leads with an average forward weekly return of +0.474% under Risk-On and +0.419% under Neutral conditions.

* Commodities: Copper (economic growth proxy) delivers its best returns during Neutral environments (+0.540% weekly return), reflecting robust industrial demand without the headwinds of restrictive liquidity.

### Defensive Regimes (Score between -10 and -40):

* Equity Performance Flattens: SPY returns compress to +0.031% weekly, while QQQ (-0.321%) and IWM (-0.355%) enter negative territory.

* Commodity Drawdowns: Copper and Gold show severe average weekly losses (-1.010% and -2.312%, respectively), signaling asset liquidations and deflationary pressures as liquidity starts to dry up.

### Deleveraging Regimes (Score < -40):

* Severe Equity Drawdowns: Broad equities experience steep losses. Nasdaq (QQQ) plummets with an average weekly forward return of -4.981%.

* Industrial Hard Stop: Copper drops an average of -3.724% weekly, confirming the absolute destruction of growth and cyclical demand.

* Gold as the Ultimate Safe-Haven: Gold shines during deleveraging spikes, delivering an outstanding average forward weekly return of +4.514%. This behavior highlights its role as a premier systemic insurance asset during structural liquidity crises.


## Tactical Asset Allocation Rule-of-Thumb

| Composite Score Range | Liquidity Regime | Preferred Asset Exposure | Asset Classes to Avoid / Underweight |
| :--- | :--- | :--- | :--- |
| **>= 40** | **Strong Risk-On** | High-Beta Equities (QQQ, IWM), Industrial Metals (Copper), Credit | Long-Duration Treasuries, Cash |
| **10 to 40** | **Risk-On** | Equities (SPY, QQQ), Corporate Bonds (HYG) | Cash, Gold |
| **-10 to 10** | **Neutral** | Broad Equities (SPY), Gold, Copper | None (Balanced allocation) |
| **-40 to -10** | **Defensive** | High Quality Corporate Credit (HYG), Cash | Small Caps (IWM), Cyclical Commodities |
| **< -40** | **Deleveraging** | **Gold**, Cash, Long-Duration Treasuries | Equities (QQQ, SPY), Industrial Metals (Copper) |


### Optimal Asset Allocation Guide

Based on historical backtest returns and liquidity-transmission mechanisms, here is the structured strategic guide for portfolio allocation across each of our five mapped regimes:

| Liquidity Regime | Primary Objective | Preferred Long Assets | Hedges / Underweights | Key Macro Rationale |
| :--- | :--- | :--- | :--- | :--- |
| **1. Strong Risk-On** | Aggressive Capital Growth | High-Beta Equities (**QQQ**, **IWM**), Industrial Metals (**Copper**), Emerging Markets | Cash, Gold, Long-Duration Treasuries | Abundant fiat liquidity and low spreads drive capital to the farthest corners of the risk curve. |
| **2. Risk-On** | Core Equity Growth | Broad Equities (**SPY**, **QQQ**), High-Yield Corporate Credit (**HYG**) | Short Duration Cash, Gold | Positive systemic liquidity supports earnings and compresses corporate spreads. |
| **3. Neutral** | Balanced / Relative Value | Multi-Asset (Balanced **SPY**), **Gold**, Trend-Following Commodities | None (Benchmark target weights) | Liquidity conditions are balanced; asset performance is driven primarily by idiosyncratic fundamentals. |
| **4. Defensive** | Capital Preservation & Yield | Cash, High-Quality Corporate Bonds, Long-Duration Treasuries | Small Caps (**IWM**), Cyclical Commodities | Net liquidity begins to drain; spreads widen slightly, making risk-taking less mathematically favorable. |
| **5. Deleveraging** | Crisis Risk Mitigation | **Gold**, Cash Reserves, Overnight Treasury Bills | Broad Equities (**SPY**, **QQQ**), Copper, Leveraged Loans | Forced liquidations dominate. High risk of systemic contraction. Gold thrives on flight-to-safety flows and expectations of eventual central bank intervention. |

### Dynamic Allocation Backtest and Drawdown Analysis

Let's implement a dynamic quantitative strategy based on our **Optimal Asset Allocation Guide** rules and calculate its maximum drawdown compared to a passive S&P 500 Buy-and-Hold strategy.

#### Strategy Allocation Rules:
1. **Strong Risk-On**: 100% Nasdaq (QQQ)
2. **Risk-On**: 100% S&P 500 (SPY)
3. **Neutral**: 60% S&P 500 (SPY) + 40% Gold (GOLD)
4. **Defensive**: 100% Cash / High Yield Bonds (HYG)
5. **Deleveraging**: 100% Gold (GOLD)

We will align the regime score of each week to determine the asset allocation for the *following* week (avoiding look-ahead bias), calculate the cumulative returns, and plot the rolling drawdowns.



### Per Dollar Backtest vs S&P 500 
<img width="1187" height="590" alt="image" src="https://github.com/user-attachments/assets/7c476cdb-a7a4-4382-bb61-7a91c0f8d404" />

### Risk Backtest Showing Max Drawdown 
<img width="1188" height="590" alt="image" src="https://github.com/user-attachments/assets/d8600bb5-948e-423b-af2a-221691349b36" />

### Distribution of Composite Liquidity Scores and Regime Thresholds 
<img width="1189" height="490" alt="image" src="https://github.com/user-attachments/assets/853f4641-f815-4850-ac49-03acb47236d9" />

### Asset Class Performance Matrix 
<img width="1088" height="590" alt="image" src="https://github.com/user-attachments/assets/4ed1fffd-92d0-43a9-bf4e-7cdcea2c19a3" />


### Stress Testing Across Key Decades (2000 - Present)

To thoroughly evaluate the strategy through different economic cycles (the 2000 Dot-com crash, the 2008 Global Financial Crisis, the 2020 pandemic crash, and the 2022 inflationary tightening), we will:
1. Re-fetch all FRED and Yahoo Finance data starting from **January 1, 2000**.
2. Recompute our weekly rolling 1-year Z-scores and Composite Liquidity Score over this complete history.
3. Split the data into three historical sub-periods: **2000–2010**, **2010–2020**, and **2020–Present**.
4. Run independent performance and maximum drawdown analyses on all three sub-periods.


## 2000 - 2010 Results 
<img width="1189" height="790" alt="image" src="https://github.com/user-attachments/assets/e0c5b0b0-9ac9-4410-9e92-7a89fa6b642a" />

## 2010 - 2020 Results 
<img width="1189" height="790" alt="image" src="https://github.com/user-attachments/assets/e5fcc5c4-7069-412a-acc0-f8c01a3b7023" />

## 2020 - Present 
<img width="1190" height="790" alt="image" src="https://github.com/user-attachments/assets/18b2e115-67c8-4597-94d5-e2fb68c5c246" />
