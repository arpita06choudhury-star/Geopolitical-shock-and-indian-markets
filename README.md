# Geopolitical Shock & Indian Markets
### A Quantitative Event Study of the April 2026 Iran-Israel-US Crisis

## Overview

In April 2026, escalating military tensions between Iran, Israel, and the United States triggered a measurable shock across Indian financial markets. This project quantifies that shock using a Python-based event study framework, analyzing how the crisis propagated from crude oil into Indian equities through currency and commodity transmission channels.

**Key finding:** Brent Crude alone explains **51.5% of Nifty 50's daily return variance** during the crisis window (R² = 0.51, p = 0.0058), with the relationship occurring same-day rather than predictively — confirming Indian equity markets price in oil-shock information efficiently and immediately.

## Assets analyzed

| Asset | Ticker | Why included |
|---|---|---|
| Nifty 50 | ^NSEI | Benchmark Indian equity index |
| Nifty IT | ^CNXIT | Most exposed sector |
| Nifty Energy | ^CNXENERGY | Directly affected by crude spike |
| Nifty FMCG | ^CNXFMCG | Defensive sector control |
| Nifty Metal | ^CNXMETAL | Global demand sensitive |
| Brent Crude | BZ=F | Primary shock variable |
| USD/INR | USDINR=X | Currency transmission mechanism |

## Methodology

The analysis follows a standard event study framework, dividing April 2026 into three windows:
- **Pre-event** (Apr 1–12): baseline market behavior
- **Event** (Apr 13–14): the initial crash
- **Post-event** (Apr 15–27): aftermath and second-wave dynamics

Data was sourced via the `yfinance` API. Both simple and log returns were computed — log returns for all inferential statistics (correlation, regression, volatility, lag analysis), since they are additive across time and standard practice in quantitative finance.

## Analysis performed

1. **Cumulative returns** — compounded performance across all seven assets over the event window
2. **Correlation matrix** — quantifying pairwise relationships (e.g., Brent Crude vs Nifty 50: −0.64)
3. **Sector rotation analysis** — identifying winners (Energy, Metal) and losers (IT) during the crisis
4. **Drawdown analysis** — measuring peak-to-trough pain, including pre-crash price drift
5. **Rolling volatility** — a 5-day rolling window showing fear building before public news
6. **Event timing analysis** — comparing average returns/volatility across pre/event/post windows
7. **Regression analysis** — single-factor (crude only) and multi-factor (crude + USD/INR) OLS models
8. **Lag analysis** — testing whether crude oil has predictive power over next-day Nifty returns, or only moves simultaneously with it

## Key results

- **Single-factor regression (Crude → Nifty):** Beta = −0.154, R² = 0.515, p = 0.0058
- **Multi-factor regression (Crude + USD/INR):** R² improves marginally to 0.527 — the two factors are largely collinear during this crisis
- **Lag analysis:** Same-day R² = 0.515 vs 1-day lag R² = 0.024 (p = 0.628, not significant) — confirming the crude-Nifty relationship is simultaneous, not predictive
- **Sector dispersion:** A 16.5 percentage point gap between the best (Nifty Energy, +12.7%) and worst (Nifty IT, −3.8%) performing sectors over the same one-month window

## Tools and libraries

| Library | Purpose |
|---|---|
| `yfinance` | Historical price data |
| `pandas` | Data manipulation and DataFrame construction |
| `numpy` | Log return calculations and matrix operations |
| `scipy` | Regression (beta, R², p-value) |
| `matplotlib` | Visualizations |
| `seaborn` | Correlation heatmap |

## Repository structure

```
geopolitical-shock-project/
├── README.md
├── requirements.txt
├── analysis.py              # Main analysis script
├── report.pdf               # Full written report with charts and commentary
└── figures/                 # Exported chart images
```

## Limitations

- Brent Crude was used as a proxy for oil prices rather than Dubai Crude, which is more representative of India's import mix, though the two are highly correlated
- Small sample size (April 2026 only) — results are directionally reliable but would benefit from validation over a longer time series
- The regression model captures only two factors (crude, USD/INR); a fuller model would incorporate FII flows, domestic bond yields, and sector-specific earnings data
- FII flow data ($12.7B outflow in March, $5B+ in April 2026) was researched qualitatively but not incorporated quantitatively due to data alignment constraints

See the full report (`report.pdf`) for a complete discussion of limitations and methodology.

