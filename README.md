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
## Key Findings
## Interpretation
## Limitations and Extentions
