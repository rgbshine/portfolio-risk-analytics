# Portfolio Risk Analytics — Project Specification

## 1. Project Objective

The objective of this project is to build an institutional-style portfolio risk analytics framework for a diversified multi-asset portfolio.

The framework will measure total portfolio risk, identify the major sources of risk, evaluate diversification benefits, quantify potential losses under normal and stressed market conditions, and assess whether portfolio construction can be improved.

The project is designed around the following investment-risk question:

> **What are the major risks in the portfolio, where are those risks coming from, and how would the portfolio behave under adverse market conditions?**

The analysis will cover:

* Portfolio performance and volatility
* Correlation and diversification
* Value at Risk (VaR)
* Expected Shortfall (ES)
* Drawdown analysis
* Risk contribution and risk decomposition
* Historical and hypothetical stress testing
* Factor exposure analysis
* Portfolio optimization and risk-aware portfolio construction

---

## 2. Portfolio Definition

The analysis assumes a hypothetical **USD 10 million diversified multi-asset portfolio**.

Liquid exchange-traded funds (ETFs) are used as proxies for major asset classes to ensure transparent and reproducible market data.

| Asset Class                | Proxy |   Weight | Initial Market Value |
| -------------------------- | ----- | -------: | -------------------: |
| US Equities                | SPY   |      30% |           $3,000,000 |
| US Technology Equities     | QQQ   |      15% |           $1,500,000 |
| European Equities          | VGK   |      10% |           $1,000,000 |
| Emerging Market Equities   | EEM   |      10% |           $1,000,000 |
| US Intermediate Treasuries | IEF   |      15% |           $1,500,000 |
| US Long-Term Treasuries    | TLT   |       5% |             $500,000 |
| Gold                       | GLD   |      10% |           $1,000,000 |
| US Real Estate             | VNQ   |       5% |             $500,000 |
| **Total**                  |       | **100%** |      **$10,000,000** |

The portfolio intentionally contains exposure to multiple risk drivers, including:

* Equity market risk
* Geographic equity risk
* Technology/growth concentration
* Interest-rate and duration risk
* Emerging-market risk
* Real-estate risk
* Gold/commodity exposure

This allows the project to examine both standalone asset risk and cross-asset diversification.

---

## 3. Benchmark

Portfolio performance will be compared with a traditional **60/40 equity-bond benchmark**:

* 60% SPY — US equities
* 40% AGG — US investment-grade bonds

The benchmark provides a simple reference portfolio against which the risk-adjusted performance, drawdowns, volatility and diversification characteristics of the multi-asset portfolio can be evaluated.

---

## 4. Base Currency

The portfolio base currency is **USD**.

ETF prices and portfolio values will therefore initially be analyzed in USD.

The first version of the framework will not explicitly model FX exposure. Currency risk can be incorporated as a later extension of the project.

---

## 5. Analysis Period

The initial analysis period is:

**January 2018 to the latest available market data.**

This period is chosen because it includes several distinct market regimes and stress episodes, including:

* The Q4 2018 equity sell-off
* The COVID-19 market shock in 2020
* The subsequent monetary and fiscal stimulus period
* The 2022 inflation and interest-rate shock
* The post-2022 market environment

Using multiple market regimes allows the analysis to demonstrate that correlations, volatility and diversification benefits are not constant through time.

---

## 6. Data Frequency

The primary analysis will use **daily adjusted market prices**.

Daily total-return-consistent price data will be used where available so that distributions and corporate actions do not artificially distort calculated returns.

Daily returns will be calculated as:

$$
r_{i,t} = \frac{P_{i,t}}{P_{i,t-1}} - 1
$$

where:

* \(r_{i,t}\) = return of asset \(i\) on day \(t\)
* \(P_{i,t}\) = adjusted price of asset \(i\) on day \(t\)

Log returns may also be evaluated where mathematically appropriate.

---

## 7. Portfolio Rebalancing Assumption

The strategic portfolio weights defined above represent target weights.

The base-case analysis will assume **monthly rebalancing** back to the target allocation.

Where useful, results may also be compared with a buy-and-hold portfolio to evaluate the effect of the rebalancing assumption.

Transaction costs and taxes are excluded from the initial model.

---

## 8. Risk Measurement Horizon

The primary market-risk measurement horizon will be:

**1 trading day**

VaR and Expected Shortfall will initially be estimated at:

* 95% confidence
* 99% confidence

Longer horizons may subsequently be examined for portfolio-management applications.

---

## 9. Core Risk Metrics

### 9.1 Performance and Risk

The framework will calculate:

* Cumulative return
* Annualized return
* Annualized volatility
* Sharpe ratio
* Maximum drawdown
* Rolling volatility
* Rolling returns

These metrics establish the basic risk-return characteristics of the portfolio.

### 9.2 Correlation and Diversification

The framework will examine:

* Asset return correlations
* Covariance matrix
* Rolling correlations
* Portfolio volatility
* Diversification effects
* Changes in correlation during stressed markets

Particular attention will be paid to situations where correlations increase during market stress and diversification becomes less effective.

### 9.3 Value at Risk

Portfolio VaR will be estimated using multiple methodologies:

1. Historical Simulation VaR
2. Parametric / Variance-Covariance VaR
3. Monte Carlo VaR

Results will be compared across methodologies to understand the assumptions and limitations of each approach.

### 9.4 Expected Shortfall

Expected Shortfall will estimate the average portfolio loss conditional on losses exceeding the VaR threshold.

This provides information about tail-loss severity that VaR alone does not capture.

### 9.5 Risk Contribution

Portfolio risk will be decomposed to determine which positions are responsible for overall portfolio volatility.

Measures will include:

* Marginal Contribution to Risk
* Component Contribution to Risk
* Percentage Contribution to Risk

The analysis will distinguish between **capital allocation** and **risk allocation**.

An asset with a relatively small portfolio weight may still represent a disproportionately large share of total portfolio risk.

---

## 10. Drawdown Analysis

The framework will identify major portfolio drawdowns and calculate:

* Drawdown magnitude
* Drawdown duration
* Time to recovery
* Asset-level contribution during major drawdowns

Historical drawdown analysis will help evaluate how the portfolio behaves during periods of sustained market stress.

---

## 11. Stress Testing

Both historical and hypothetical stress scenarios will be considered.

### Historical Scenarios

Potential historical stress windows include:

* Q4 2018 equity sell-off
* COVID-19 market shock
* 2022 inflation and interest-rate shock

For each scenario, the analysis will examine:

* Portfolio loss
* Asset-level performance
* Contribution to portfolio loss
* Changes in diversification behavior

### Hypothetical Scenarios

Illustrative hypothetical scenarios may include:

* Global equity market shock
* Technology-sector sell-off
* Parallel interest-rate shock
* Equity-bond simultaneous sell-off
* Emerging-market shock
* Gold price shock

The objective is not to predict future crises but to understand portfolio vulnerability to plausible adverse market moves.

---

## 12. Factor Risk Analysis

A later stage of the project will investigate whether apparently diversified positions share common underlying risk factors.

Potential factors include:

* Broad equity market exposure
* Interest-rate exposure
* Growth/technology exposure
* Geographic exposure
* Emerging-market exposure
* Inflation-sensitive exposure

The purpose is to distinguish diversification by **number of holdings** from diversification by **underlying risk factor**.

---

## 13. Portfolio Construction Analysis

The existing strategic allocation will be compared with alternative portfolio construction approaches.

Potential approaches include:

* Minimum-variance portfolio
* Mean-variance optimization
* Risk-parity allocation
* Equal-weight portfolio

The objective is not simply to maximize historical return.

Instead, the analysis will examine whether portfolio risk can be allocated more efficiently while maintaining reasonable diversification and avoiding unrealistic concentration.

---

## 14. Risk Monitoring Dashboard

The final project will include a portfolio risk dashboard summarizing key information such as:

* Portfolio value
* Performance
* Volatility
* VaR
* Expected Shortfall
* Maximum drawdown
* Asset allocation
* Risk contribution
* Correlation
* Stress-test results

The dashboard will be designed from the perspective of a portfolio risk analyst communicating risk information to portfolio managers and senior investment stakeholders.

---

## 15. Model Validation

Risk calculations will be validated wherever practical.

Validation may include:

* Independent calculation checks
* VaR backtesting
* Comparison across VaR methodologies
* Sensitivity analysis
* Data-quality controls
* Weight and portfolio-value reconciliation
* Unit tests for reusable risk functions

Model assumptions and limitations will be documented explicitly.

---

## 16. Key Assumptions and Limitations

The initial framework makes several simplifying assumptions:

* ETFs are used as proxies for asset-class exposure.
* The portfolio is hypothetical.
* The base currency is USD.
* Transaction costs and taxes are excluded.
* Liquidity risk is not explicitly modeled in the initial implementation.
* FX risk is not separately modeled.
* ETF tracking error is ignored.
* Historical relationships may not persist in future market regimes.
* VaR and Expected Shortfall are estimates rather than maximum possible losses.
* Stress scenarios are simplified representations of market shocks.

These limitations will be considered when interpreting model outputs.

---

## 17. Project Deliverables

The completed repository is expected to contain:

1. A reproducible market-data pipeline
2. Clean portfolio and market datasets
3. Portfolio performance analytics
4. VaR and Expected Shortfall models
5. Risk decomposition analysis
6. Drawdown analytics
7. Historical and hypothetical stress tests
8. Factor-risk analysis
9. Portfolio construction analysis
10. Risk dashboard
11. Model validation and tests
12. Final portfolio risk report
13. Complete GitHub documentation

---

## 18. Project Structure

```text
portfolio-risk-analytics/
│
├── README.md
├── .gitignore
├── requirements.txt
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│
├── src/
│
├── reports/
│   ├── project_specification.md
│   └── figures/
│
└── tests/
```

The notebooks will primarily be used for exploration, visualization and presentation.

Reusable calculations will progressively be moved into Python modules under `src/`, while `tests/` will contain validation and unit tests.

---

## 19. Development Roadmap

The project will be developed incrementally:

**Phase 1 — Project Setup and Specification**

Define repository structure, portfolio assumptions, benchmark and analytical objectives.

**Phase 2 — Market Data Pipeline**

Acquire, clean, validate and store historical market data.

**Phase 3 — Portfolio Analytics**

Construct portfolio returns and calculate core performance statistics.

**Phase 4 — Market Risk Measurement**

Implement volatility, VaR and Expected Shortfall models.

**Phase 5 — Risk Decomposition**

Measure marginal and component contributions to portfolio risk.

**Phase 6 — Drawdown and Stress Testing**

Analyze historical drawdowns and adverse market scenarios.

**Phase 7 — Factor Risk**

Investigate common underlying drivers of portfolio risk.

**Phase 8 — Portfolio Construction**

Compare the strategic allocation with alternative risk-aware allocations.

**Phase 9 — Dashboard and Reporting**

Develop a concise portfolio-risk dashboard and final risk report.

**Phase 10 — Validation and Documentation**

Backtest risk models, implement tests, document limitations and prepare the repository for public presentation.
