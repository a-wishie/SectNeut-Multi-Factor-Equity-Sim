# Multi-Factor Equity Index — Quality, Value & Momentum

A systematic factor-based index construction model applied to a 
94-stock S&P 500 universe, comparing raw vs sector-neutralised 
factor portfolios against the S&P 500 benchmark (2020–2024).

## Methodology

### Factors
- **Quality:** ROE and debt-to-equity (winsorised, z-scored)
- **Value:** P/E and P/B ratios (inverse scored — lower = better value)
- **Momentum:** 12-1 month price return (standard cross-sectional momentum)

### Construction
1. Winsorise each factor at 5th/95th percentile to remove outliers
2. Z-score normalise within full universe (raw) and within sectors (neutralised)
3. Equal-weight composite score across three factors
4. Long top quintile, short bottom quintile

### Key Design Decision — Sector Neutralisation
Raw factor scores were adjusted within each GICS sector rather than 
across the full universe. This isolates stock-specific alpha from 
sector-level noise.

## Results

| Metric | Raw | Sector-Neutralised | S&P 500 |
|--------|-----|-------------------|---------|
| Annualised Return | 20.97% | 21.22% | 14.37% |
| Annualised Volatility | 24.88% | 20.32% | 21.00% |
| Sharpe Ratio | 0.64 | 0.80 | 0.45 |
| Max Drawdown | -37.14% | -31.53% | -33.72% |
| Tracking Error | 9.91% | 7.44% | — |
| Active Return | +6.60% | +6.85% | — |
| Information Ratio | 0.67 | 0.92 | — |
| Sector HHI | 0.266 | 0.109 | — |

## Key Findings

**Factor independence:** Correlation analysis confirmed the three 
factors are largely orthogonal. Quality-value correlation was -0.35 
(reflecting the known growth-value tension), while momentum showed 
near-zero correlation with both, validating it as an independent 
return source.

**Sector neutralisation impact:** Without neutralisation, the long 
portfolio concentrated 44% in Financial Services — the model was 
inadvertently capturing a sector bet. After neutralisation, all 11 
sectors received representation (HHI reduced from 0.266 to 0.109).

**Performance improvement:** Sector neutralisation improved Sharpe 
ratio from 0.64 to 0.80, reduced volatility by 456bps, reduced max 
drawdown by 561bps, and raised the information ratio from 0.67 to 
0.92 — demonstrating that diversified factor exposure generates more 
robust risk-adjusted returns than concentrated factor bets.

## Files
- `multifactor_index.ipynb` — full analysis notebook
- `multifactor_results_full.png` — six-panel research dashboard

## Tech Stack
Python, Pandas, NumPy, yfinance, Matplotlib, Seaborn

