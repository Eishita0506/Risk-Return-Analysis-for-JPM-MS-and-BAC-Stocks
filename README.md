# TITLE:
### Risk-Adjusted Performance and Factor Attribution of an Equity Portfolio under Time-Varying Market Conditions

## Overview
This project conducts a quantitative analysis of equity portfolio performance through the rigorous application of asset pricing models and a comprehensive suite of risk metrics. The methodology is structured in two primary analytical streams:

#### 1. Return Decomposition & Factor Attribution:
- It investigates whether the risk-adjusted returns of large U.S. banks (JPMorgan Chase, Morgan Stanley, and Bank of America) are driven by managerial skill (alpha) or by systematic factor exposuresExcess returns are systematically decomposed using the Capital Asset Pricing Model (CAPM) and the Fama-French Three-Factor framework. This analysis isolates the contributions of systematic risk exposures (market, size, value) from idiosyncratic (alpha) returns.

#### 2. Advanced Risk Assessment: 
- Portfolio risk is evaluated using both standard and downside/tail-risk-adjusted performance metrics. These include the Sharpe, Sortino, and Treynor ratios, Maximum Drawdown (MDD), and probabilistic tail risk estimates via Historical and Parametric Value-at-Risk (VaR) and Expected Shortfall (CVaR).

- To capture temporal dynamics and structural breaks in risk exposures and performance, all estimations are implemented using a rolling-window framework. This approach provides a time-varying perspective on alpha generation, factor loadings, and the evolution of portfolio risk characteristics.

## Research Question
- Attribution: Alpha or Beta?
Are the observed risk-adjusted returns driven by persistent managerial skill (alpha) or by exposure to systematic risk factors (market, size, value)?

- Resilience: Performance Under Stress
How does the portfolio behave in adverse markets? We quantify this through downside risk metrics, including maximum drawdown and tail-risk measures (VaR/CVaR).

- Stability: Time-Varying Dynamics
Are the portfolio's factor loadings and risk characteristics stable over time, or do they exhibit significant structural breaks, particularly around periods of financial stress?

## Data Description
- Asset Returns 
- Market Index of JP Morgan, Morgan Stanley and Bank of America
- Risk Free rate(0.04)
- Factor data(Fama-French)

The analysis uses daily returns for a constructed equity portfolio, corresponding market returns, and risk-free rates. Fama–French three-factor data (Market, SMB, HML) are used for factor attribution. All datasets are aligned by date and cleaned for missing values.

## Methodology and Metric Definition
### 1. 
Imported all required packages and downloaded the data for three major investment banks i.e. JP Morgan, Morgan Stanley and Bank of America alongwith S&P 500 Data considered as benchmark
### 2. Return Calculation and Analysis
- Simple Return - It is the percentage change in asset price overtime. It tells us how much our investment grew/shrank. Simple return is used when we want a quick and intuitive view of daily, weekly or monthly gains or loses.
- Log Return- It is the natural logarithm of the price ratio between two time points. It assumes continuous compounding.
- Annualized Return- Also known as Compound Annual Growth Rate(CAGR), is the average yearly growth rate of an investment over a specific period.
- Volatility-Volatility is a measurement of how varied the returns of a given security or market index are over time. It is often measured from either the standard deviation or variance between those returns. In most cases, the higher the volatility, the riskier the security.
- The distribution of the Returns were analysed through pairwise correlation of asset returns, visual analysis, skew, kurtosis, volatility etc.
### 3. The Capital Asset Pricing Model(CAPM) Model and analysis
- Alpha- It tells us how much better or worse our investment did compared to what was expected after considering the risk it took
- Beta- It measures how much your investment moves in relation to the market
- The Capital Asset Pricing Model (CAPM): It is a model that describes the relationship between the expected return and risk of investing in a security. It shows that the expected return on a security is equal to the risk-free return plus a risk premium, which is based on the beta of that security.It is based on the idea of systematic risk (otherwise known as non-diversifiable risk) that investors need to be compensated for in the form of a risk premium. A risk premium is a rate of return greater than the risk-free rate. When investing, investors desire a higher risk premium when taking on more risky investments. CAPM posits that an asset's expected return compensates investors for the time value of money, represented by the risk-free rate, and for bearing systematic risk, measured by its beta. The model serves as an equilibrium benchmark to determine whether an asset is fairly valued relative to its expected return, given its exposure to market risk.
- Expected Return-Expected return is a long-term assumption about how an investment will play out over its entire life.
- Risk Free Rate-
- Market Risk Premium- It represents the additional return over and above the risk-free rate, which is required to compensate investors for investing in a riskier asset class. The more volatile a market or an asset class is, the higher the market risk premium will be.
- OLS regression is used to estimate the CAPM's alpha and beta from historical return data, as the theoretical model relies on unobservable expected returns. It provides statistically efficient estimates of the realized relationship between an asset and the market while also quantifying the precision of these estimates through standard errors, enabling formal hypothesis tests on their significance.
- Bootstrap resampling is employed to estimate the CAPM alpha's statistical properties more robustly when the standard OLS assumptions, particularly normally distributed errors may be violated. By repeatedly resampling the data with replacement, the bootstrap generates an empirical distribution of the estimated alpha. This allows for the construction of more reliable confidence intervals and hypothesis tests, especially in cases with non-normal returns, small sample sizes, or potential outliers.
- Next, a rolling CAPM is employed because the core assumption of static CAPM, that beta and alpha are constant over time is empirically weak, especially in real financial markets. Rolling CAPM relaxes this assumption and lets risk–return relationships evolve through time. Rolling CAPM estimates CAPM repeatedly over moving time windows. It helps identify Bull vs bear market behavior, crisis-driven beta spikes, structural breaks etc.

### 4. Fama French 3 (FF 3) Model
- It enhances the traditional capital asset pricing model (CAPM) by incorporating size and value risk factors alongside market risk. This model acknowledges that small-cap and value stocks consistently outperform the broader market. By integrating these additional factors, the Three-Factor Model offers a more refined evaluation tool for portfolio performance, adjusting for the typical outperformance of these stock categories.
- It indicates that excess returns are accompanied by higher volatility and periods of short-term underperformance. Investors with long investment horizons (15+ years) are better positioned to capture these factor premia. Given that the model can explain up to 95% of returns in diversified equity portfolios, investors can systematically tailor expected returns by adjusting their exposure to underlying risk factors
- Applied to capture time-varying exposure to market, size, and value 
In the Fama–French three-factor model, OLS is used to estimate average exposures to the market, size, and value factors and to decompose returns into systematic risk and alpha. Rolling-window OLS relaxes the assumption of constant factor loadings by capturing time-varying and regime-dependent behavior. Bootstrapping is employed to test the robustness and statistical significance of alpha without strong distributional assumptions, reducing the risk of spurious inference.

### 5. Performance Metrics
- Sortino Ratio: It measures how much return you are earning for every unit of downside risk you take
- Sharpe Ratio: It tell you how much return you are getting for each unit of risk you take
- Maximum Drawdown: Maximum loss from  a portfolio's peak to its lowest
- Calmer Ratio: It tells you how much return you are earning for every unit of worst risk
- Treynor Ratio: It is a risk-adjusted return matrix that evaluates how much excess return an investment earns per unit of systematic risk
- Value at Risk(VaR):VaR is a risk measure that quantifies the extent of financial loss within a portfolio over a specific time frame at a specific confidence interval
- Expected shortfall: It is a measure of the expected loss when loss goes beyond VaR

## Interpretation
### 1. Visualization of the Closing Prices of the stocks
- Dominant systematic risk exposure:
The near-parallel price paths of BAC, JPM, and MS indicate a high degree of common variation driven by broad market dynamics, consistent with a strong market beta. This visual evidence supports the use of CAPM as a first-order benchmark for explaining bank equity returns before introducing additional factors.

- Evidence of conditional idiosyncratic behavior:
While overall co-movement remains strong, localized deviations—particularly during transitional phases in mid-2024—suggest firm-specific shocks or time-varying sensitivities to secondary risk factors such as size and value. These deviations motivate formal alpha testing and multi-factor model extensions.

- Indications of regime-dependent return dynamics:
The synchronized inflection point and accelerated price appreciation from November 2024 onward point to a potential structural shift in the return-generating process, plausibly linked to changes in macroeconomic or interest-rate expectations. This underscores the necessity of rolling-window or sub-period regressions to capture evolving betas and alphas.

- Volatility clustering and inference implications:
The clustering of heightened price fluctuations during mid-2024 reflects persistent volatility regimes rather than i.i.d. behavior. This has direct econometric implications, as standard OLS inference may be unreliable, motivating the use of heteroskedasticity-robust standard errors or GARCH-type volatility modeling within the factor framework.

### Correlation Matrix for Pairwise correlation of Asset Returns
- Strong systematic co-movement:
High positive correlations among BAC, JPM, and MS indicate that returns are largely driven by common market and macroeconomic factors rather than firm-specific risk.

- Limited intra-sector diversification:
The elevated correlation structure implies minimal diversification benefits within large U.S. banking stocks, especially during market stress.

- Support for factor models:
The observed co-movement justifies the use of CAPM and Fama–French models, as systematic risk dominates idiosyncratic variation.

- Risk management implication:
Effective risk reduction requires cross-sector or cross-asset diversification, while hedging should focus on market-level exposures.

### Simple and Log Return Distributions
1. For Portfolio simple returns:
- Skew=1.4582203054240233
- Kurtosis=13.854703937492957
2. For Portfolio log returns:
- Skew=1.1902109737376572
- Kurtosis=11.932547061995942

- Central tendency and return symmetry:
Both simple and log returns are centered close to zero, indicating no strong unconditional drift over the sample period and suggesting that average returns are modest relative to short-term volatility.

- Approximate normality with fat tails:
The distributions are roughly bell-shaped but exhibit mild skewness and excess kurtosis, reflecting the presence of extreme return observations beyond what a normal distribution would predict.

- Central tendency and return symmetry:
Both simple and log returns are centered close to zero, indicating no strong unconditional drift over the sample period and suggesting that average returns are modest relative to short-term volatility.

-Approximate normality with fat tails:
The distributions are roughly bell-shaped but exhibit mild skewness and excess kurtosis, reflecting the presence of extreme return observations beyond what a normal distribution would predict.

### Static CAPM Model Analysis
1. CAPM Alpha: 0.0005734341249099438
2. CAPM Beta: 0.897568395380774
3. CAPM Alpha p-value: 0.43359124021212314

- The portfolio’s beta of 0.8976 indicates slightly lower market sensitivity than the overall market. A 1% change in market excess returns is associated with an approximate 0.9% change in portfolio returns, on average.This suggests the portfolio behaves as a near-market portfolio, with marginally defensive characteristics.
- The estimated alpha(0.00057) is positive but economically small. The p-value (0.434) indicates that alpha is not statistically significant, implying no reliable evidence of abnormal performance beyond market risk.This supports the CAPM prediction that expected excess returns are fully explained by beta.
- The model explains approximately 28% of the variation in portfolio returns. While statistically meaningful, this indicates that a large portion of return variability is driven by non-market factors or idiosyncratic risk.
- The highly significant F-statistic (p ≈ 2.2e-19) confirms that market returns have strong explanatory power for portfolio returns.
- High skewness (1.35) and kurtosis (12.77) strongly reject the normality assumption.The Jarque–Bera test confirms significant non-normality, implying the presence of fat tails and asymmetric risk.
- Durbin–Watson ≈ 2.08 indicates no meaningful autocorrelation in residuals.

### Bootstrap Distribution of CAPM Alpha
- The 95% confidence interval for the CAPM alpha, spanning from -0.0009 to 0.0019 and containing zero, indicates that the portfolio's excess returns are fully explained by its market exposure, with no statistically significant evidence of managerial skill. While the mean bootstrap estimate of 0.0005 suggests a negligible positive average residual return, the interval's width reveals substantial estimation uncertainty, implying that any observed alpha is likely noise rather than persistent outperformance. This result economically means the portfolio did not generate meaningful risk-adjusted returns beyond the compensation for bearing systematic market risk.

### Rolling CAPM Analysis
- The chart shows that the portfolio's market risk (beta) is highly volatile over time, ranging significantly from about 0.5 to 1.5. This means the portfolio’s sensitivity to the overall market is unstable—sometimes it moves less than the market (beta < 1) and sometimes much more (beta > 1). This instability suggests that the portfolio's risk profile changes frequently, which can complicate risk management and performance attribution.

- In contrast, the alpha—the measure of excess return not explained by the market—remains consistently close to zero and fluctuates within a very tight band. This implies that, in any given short-term period, the portfolio is not reliably generating returns beyond what its market risk would justify. There are brief moments of small positive or negative alpha, but none persist, meaning there's no clear evidence of sustained skill or consistent mispricing.

- Together, this indicates the portfolio’s returns are dominated by time-varying market exposure, not by skill. Investors are primarily compensated for taking on shifting levels of market risk, not for the portfolio manager's stock-picking ability during this period.

## Static Fama French 3 Model
1. Static FF Alpha: -0.009356032499512444
2. Static FF Alpha p-value: 0.018738759230772103
3. Static FF R-squared: 0.8271300629582513
- Model Fit and Systematic Dominance: The high R-squared of 0.827 indicates that over 82% of the portfolio's return variation is explained by the three Fama-French factors (Market, Size, Value). This confirms that the returns are overwhelmingly driven by systematic risk exposures, not stock-specific events.
- Negative and Significant Alpha: The static alpha is -0.009 and statistically significant (p-value ≈ 0.019). This is a critical finding: after accounting for exposures to market, size, and value factors, the portfolio underperformed by approximately 0.9% per period (e.g., monthly). This significant negative alpha suggests the portfolio destroyed value on a risk-adjusted basis over the full sample.
- Factor Exposure Profile: The factor loadings reveal the portfolio's systematic biases:
MKT (Market, ~1.0): High and positive, confirming a strong, market-like core.
SMB (Size, ~0.05): Very small positive loading, indicating a negligible tilt toward small-cap stocks.
HML (Value, ~0.14): A meaningful positive loading, showing a clear and consistent value tilt. The portfolio behaves like it holds value-oriented stocks.

### Bootstrap Distribution of FF 3 Alpha
- The CAPM bootstrap showed that alpha was statistically indistinguishable from zero, meaning market risk (beta) alone explains returns—no skill is evident. It revealed a statistically significant negative alpha of approximately -0.9% per period. The tight, entirely negative bootstrap confidence interval confirms this underperformance is real and not due to chance. After fully accounting for exposures to the market, size, and value factors, the portfolio consistently delivered less return than its risk profile warranted. This indicates the portfolio destroyed value rather than generating alpha.

### Rolling FF 3 Model
- Alpha is consistently negative and deteriorating.This suggests that any brief periods of neutral performance captured in the static model were not sustained, and underperformance intensified during this specific sample.
- The betas for the Market (MKT), Size (SMB), and Value (HML) factors exhibit significant volatility over short periods.
- Insufficient Data for a rolling window of 60 or 30, caused inability to distinguish signal from noise and estimation error

### Comparison of the CAPM and FF Model
- CAPM explains average market exposure but underestimates risk during changing market conditions.
- Fama–French 3 improves explanatory power by incorporating additional risk dimensions.
- Rolling CAPM reveals that systematic risk is not constant, highlighting periods where static models may misrepresent risk.

| Metric               | CAPM                             | Fama–French (FF-3)                            |
| -------------------- | -------------------------------- | --------------------------------------------- |
| Alpha (α)            | **0.00057**                      | **−0.00936**                                  |
| Alpha p-value        | **0.434** (not significant)      | **0.0187** (significant)                      |
| Beta (Market)        | **0.8976**                       | Implicit via MKT factor                       |
| R-squared (R²)       | **0.278**                        | **0.827**                                     |
| Factors Included     | Market                           | Market, Size (SMB), Value (HML)               |
| Alpha Interpretation | No abnormal returns              | Statistically significant underperformance    |
| Model Insight        | Captures average market exposure | Explains returns via multi-factor risk premia |


### Performance Metrices
##### 1. Sharpe Ratio = 1.641289092233764
- This portfolio delivers 1.64 units of excess return per unit of total risk, indicating efficient risk compensation.
- Benchmark logic:
< 1.0: Weak risk-adjusted performance
1.0–1.5: Acceptable
> 1.5: Strong
> 2.0: Exceptional

#### 2. Sortino Ratio = 2.5867977749506013
- The Sortino ratio substantially exceeds the Sharpe ratio, implying that volatility is mostly on the upside.Downside risk is well-contained relative to returns, which is desirable for investors sensitive to losses.
- Benchmark logic:
< 1.0: Poor downside risk control
1.0–2.0: Good
> 2.0: Excellent downside-adjusted performance

#### 3. Maximum Drawdown = 13.32%
- A drawdown of ~13% is moderate for an equity-heavy banking portfolio.Indicates that losses, while present, were not severe or prolonged, supporting portfolio resilience.
- Benchmark logic:
< 10%: Low drawdown
10–20%: Moderate
> 30%: High / distress-level risk

#### 4. Calmar Ratio = 3.173221874484494
- A Calmar ratio above 3 signals strong return generation relative to worst-case losses. Suggests that the portfolio recovers efficiently from drawdowns and rewards drawdown risk well.
- Benchmark logic:
< 1.0: Poor drawdown compensation
1.0–2.0: Acceptable
> 3.0: Strong
> 5.0: Exceptional

#### 5. Treynor Ratio = 0.39
- A positive and relatively high Treynor ratio indicates that the portfolio is efficiently compensated for market risk.Aligns with CAPM results showing significant beta exposure and limited alpha.
- Benchmark logic:
Negative: Underperforming market risk
Low positive: Weak market-risk compensation
High positive: Efficient systematic risk pricing

#### 6. Value at Risk (Historical VaR)
- VaR 90% = −12,293
With 90% confidence, the portfolio is not expected to lose more than ₹12.3k (or currency units) over the specified horizon under normal market conditions.
- VaR 95% = −19,627
At the 95% confidence level, potential losses increase substantially, indicating sensitivity to tail events beyond typical market fluctuations.
- VaR 99% = −28,841
Extreme losses, while rare (1% probability), are materially larger, highlighting significant exposure to tail risk.

#### 7. Expected Shortfall = −27,558
- CVaR measures the average loss given that VaR is breached.
- The fact that CVaR exceeds VaR 95 by a wide margin indicates fat-tailed loss behavior, where extreme losses are substantially worse than the VaR threshold suggests.
- This implies that VaR alone understates downside risk, making CVaR a more informative risk metric for this portfolio.

#### 8. Rolling VaR and cVaR
- The portfolio's tail risk (both VaR and CVaR) increased significantly from mid-2024, peaking around October-November, before moderating slightly by year-end. This shows a period of heightened market stress and volatility for the banking sector during that window.
- The fact that CVaR is substantially worse than VaR  means that when the portfolio has a very bad day, the average loss is much deeper than the VaR threshold predicts. This highlights the portfolio's exposure to extreme downside events and the inadequacy of VaR alone for capturing true worst-case risk.

#### 9. Cross-Metric Consistency 
- High Sharpe + High Sortino = returns are strong and downside risk is well-controlled
- Moderate drawdown + High Calmar = losses are manageable relative to performance
- Positive Treynor = returns are primarily driven by systematic market exposure, consistent with CAPM
- The steep increase from VaR 90% → 95% → 99% reflects non-linear tail risk, typical of equity portfolios.
- The proximity of CVaR to VaR 99% suggests that once losses enter the tail, they escalate quickly.

## Conclusion
The portfolio's returns are overwhelmingly explained by systematic risk exposures, and it underperformed on a risk-adjusted basis, with no evidence of managerial skill.
1. Attribution: Beta, Not Alpha
The portfolio's performance is driven by systematic risk, not skill. The CAPM model found no significant alpha, and the superior Fama-French model revealed a statistically significant negative alpha (-0.9% per period). The bootstrap confidence intervals confirmed this underperformance is not due to chance. The high R-squared (82.7%) confirms that market, size, and value factors explain most return variation.
2. Resilience: Moderate Stress Performance with Significant Tail Risk
While traditional metrics (Sharpe: 1.64, Sortino: 2.59) suggest good risk-adjusted returns, tail risk analysis reveals vulnerability. The portfolio experienced a moderate maximum drawdown (13.3%), but rolling VaR/CVaR shows risk spiked during late 2024. Critically, CVaR was substantially worse than VaR, indicating that when losses occur, they tend to be severe—a risk not captured by standard deviation alone.
3. Stability: Time-Varying Exposures
Both rolling CAPM and Fama-French analyses show that factor loadings, particularly beta, are unstable over time. This time-varying risk profile complicates static risk assessment and highlights the importance of dynamic monitoring. The portfolio's value tilt (positive HML loading) was consistent but insufficient to generate positive alpha.