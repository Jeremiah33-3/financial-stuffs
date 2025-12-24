## TOC
- [Key Concepts & Equations](#key-concepts--equations)
- [Valuation Techniques](#valuation-techniques)
  - [DCF](#dcf)
  - [Precedent Transactions](#precedent-transactions)
- [Private Firms Valuation](#private-firms-valuation)

## Key Concepts & Equations

### Beta
The beta (β) of an investment security (i.e., a stock) is a measurement of its volatility of returns relative to the entire market, typically benchmarked against a broad market index, like the S&P 500.
> Beta = Covariance (Re, Rm) / Variance (Rm)

Levered beta, also known as equity beta or stock beta, is the volatility of returns for a stock, taking into account the impact of the company’s leverage from its capital structure. It compares the volatility (risk) of a levered company to the risk of the market. Levered beta includes both business risk and the risk that comes from taking on debt. It is also commonly referred to as “equity beta” because it is the volatility of an equity based on its capital structure.
> Unlevered β = Levered β / ((1 + (1 – Tax Rate) * (Debt / Equity))

Asset beta, or unlevered beta, on the other hand, shows the risk of an unlevered company relative to the market. It includes business risk but does not include leverage risk.
> Levered Beta = Unlevered Beta * ((1 + (1 – Tax Rate) * (Debt / Equity))

Equation is related to [Hamada Equation](https://www.investopedia.com/terms/h/hamadaequation.asp).

### Types of cash flows
Cash Flow (CF) is the increase or decrease in the amount of money a business, institution, or individual has. In finance, the term is used to describe the amount of cash (currency) that is generated or consumed in a given time period.

1. Operating CF
OCF = Net Income + Depre & Amort +/- non-cash items +/- changes in net working capital

2. Investing CF
Investing CF = Net capital expenditure (CAPEX)

3. Financing CF
Financing CF = + net debt proceeds + net equity proceeds

4. Free CF to Firm (FCFF) or Unlevered CF
UCF = Net income + depre & amort +/- non cash items +/- changes in net working capital - net capital expenditure + interest exp * (1 - t)
OR UCF = EBIT(1 -t) + depre & amort +/- non cash items +/- changes in net working capital - net capital expenditure

5. Free Cash flow to equity (FCFE) or Levered Free CF (LCF)
FCFE = Net Income + depre & amort +/- non cash items +/- changes in net working capital - net capital expenditure +/- net debt proceeds

### cost of debt, equity, capital

**Cost of capital**: Cost of capital is a broad term for the required rate of return a firm must earn on its investments to satisfy its providers of finance; its main components are the cost of equity and the cost of debt. Cost of equity is the return required by shareholders, while cost of debt is the effective interest rate the firm pays to lenders, usually adjusted for tax.
- usually estimated by - weighted average cost of capital (WACC): The overall blended cost of capital combining equity, debt, and sometimes preferred stock, weighted by their proportions in the capital structure

_Other metrics for cost of capital includes:_

Adjusted Present Value (APV)

- APV separates the value of a project into its unlevered value plus financing side effects, using the unlevered cost of equity (or asset beta-based rate) instead of WACC. Firms apply it for projects with changing debt levels, where WACC assumes static proportions.

Flow-to-Equity (FTE)

- FTE discounts levered free cash flows directly at the cost of equity, bypassing WACC's blending of debt and equity costs. It suits scenarios with highly variable leverage, like LBOs, by focusing solely on equity returns after debt service.

Multi-Factor Models

- Alternatives like Fama-French three-factor or Arbitrage Pricing Theory (APT) replace CAPM within WACC for cost of equity estimation, incorporating size, value, or multiple risk factors. Regulators sometimes cross-check WACC with these for better risk capture beyond single-beta CAPM.

**Cost of equity:** Cost of equity is the required rate of return that investors expect for providing capital in the form of common shares, reflecting dividends, expected price appreciation, and the risk of the business. In practice it is often estimated with CAPM or with dividend models such as  when stable dividends and growth can be assumed.

**Cost of debt**: Cost of debt is the return required by debt holders, typically proxied by the interest rate or yield the firm must pay on its bonds and loans.
For valuation and WACC, the relevant measure is usually the after‑tax cost of debt, because interest is tax-deductible and reduces the firm’s effective financing cost.

## Valuation Techniques

### DCF

> Discounted cash flow analysis helps to determine the value of an investment based on its future cash flows.
> The present value of expected future cash flows is calculated using a projected discount rate.
> If the DCF is higher than the current cost of the investment, the opportunity could result in positive returns and may be worthwhile.
> Companies typically use the weighted average cost of capital (WACC) for the discount rate because it accounts for the rate of return expected by shareholders.
> A disadvantage of DCF is its reliance on estimations of future cash flows, which could prove inaccurate.

> [!TIP]
> Use Financial Calculator NPV function to quickly get present values

#### Terminal Value 

> Terminal value in a DCF is the estimated value of the business after the explicit forecast period, usually representing the bulk of total enterprise value (often 60–80%+ in practice). It captures all future cash flows from year n+1 to infinity, collapsed into a single value at the end of the forecast horizon.

Value of the company from the end of the explicit forecast (e.g., year 5 or 10) onward, assuming the firm reaches a steady state. Used because forecasting year‑by‑year cash flows indefinitely is impossible; you model a few years explicitly, then use terminal value to approximate the rest.

2 Main Calculations for calcuating terminal value: 

1) Exit multiple
Assumes the business could be sold at the end of the forecast period for a market multiple (e.g., EV/EBITDA, EV/EBIT, EV/FCF) based on comparable companies or transactions.​

Formula at year n: `TVn = Metricn × Exit Multiple` 
- e.g.  `TV5= EBITDA5 × EV/EBITDA`

2) perpetuity (gordon growth) method
Assumes free cash flow grows at a constant rate g forever. Typical choice: a conservative rate at or below long‑term GDP/inflation (~1–3% in mature markets).

Formula at end of year n = `TVn = FCFn+1/(WACC - g) = FCFn × (1 + g) / (WACC - g)`

### Precedent Transaction Analysis (PTA) & Comparable Company Analysis (Trading/Peer Comps)

Both are relative valuation methods which use multiples, but one looks at deal prices in past M&A, while the other looks at market prices of similar publicly traded companies today.

| PTA | CCA |
| :--- | :--- |
| Values a company using prices and multiples paid in past M&A deals for similar targets (transaction comps). | Values a company using current trading multiples of similar listed peers (public comps). |
| What it values: Implied value to a buyer acquiring control. | What it values: Standalone market value for minority investors. |
| Uses deal EV/EBITDA, EV/Revenue, P/E at signing/announcement (including control premiums). | Uses live market EV/EBITDA, EV/Revenue, P/E, etc., based on current share prices and consensus estimates. |
| Includes control premium and expected synergies | Excludes control and explicit synergy value. |
| Reflect what strategic/financial buyers actually paid to buy control, often including a control premium over the unaffected share price (e.g., 20–40%). | Reflect what the market pays for a small (non‑controlling) stake in comparable companies, assuming no deal or synergies. |
| Best use for M&A, fairness opinions, takeover bids. | Best use for IPOs, equity research, benchmarking, “public market” view. |

To calculate ending value, find multiples from the data then find median/mean. The ending value triangulates these ranges into a "football field" chart showing low/high bounds, often with precedents yielding higher values due to control premiums. We can apply median multiples to target's metrics: e.g., `median 10x EV/EBITDA × target $150M EBITDA = $1.5B EV implied value.` For PTA, can adjusting for synergies/premiums if disclosed.

> [!NOTE]
> EV (enterprise value) = Market Capitalization + Total Debt + Preferred Shares + Minority Interest − Cash and Cash Equivalents

## Private Firms Valuation

To determines return from CAPM, beta of a stock/portfolio needs to be fonud. Beta measures the systematic risk or volatility of a portfolio or individual security as it compares to the market as a whole. Beta = Covariance(Ri,Rm) / Variance(Rm)

Due to the lack of market data on the stock prices of private companies, it is not possible to estimate stock beta via regression of stock beta.

To determines beta of private companies, there are two main approached 

### industry betas
Use the average beta of similar public companies for industry comparison. Adjust the beta of comparable companies (unlevering the levered beta) using the private company's target debt-to-equity ratio. 

To find: weighted betas, weighted average D/E --> then unlever it and relever it with the Hamada Equation.

_**Details**_: we first need to find the average beta of the publicly traded companies that generate income from similar operations as the private company. This will be a proxy for the industry average levered beta. Second, we need to unlever the average beta using the average debt-to-equity (D/E) ratio for these comparable companies. The final step is to re-lever beta, using the private company’s target debt-to-equity ratio.

### regression analysis 
Earnings beta considers historical earnings changes against market returns as a proxy for private companies. Beta, specifically, is the slope coefficient obtained through regression analysis of the stock return against the market return. 

This method is especially suitable for large, listed companies operating in more than one segment, and problematic to find firm whose beta would adequately represent the business beta of the private company being valued. 

When it is difficult to obtain reliable comparable beta, a company’s earnings beta can be used as a proxy for the levered beta. In this method, the company’s historical earnings changes are regressed against the market returns. An appropriate market index can be used as a proxy for the market. For instance, if the company is operating in the U.S. market, the S&P 500 can be used as a proxy. (Credits: [Investopedia](https://www.investopedia.com/articles/personal-finance/050515/how-calculate-beta-private-company.asp))

Beta obtained from historical data needs to be adjusted to make sure that it reflects the company’s expected future performance. To reflect the mean-reverting feature of beta (beta tends to revert to one in the long run), we can estimate an adjusted beta via smoothing factors and mathematical equations.

### For publicly traded companies
With publicly available betas: 
`ΔSi = α + βi × ΔM + e`
where:
- ΔSi=change in price of stock i
- α=intercept value of the regression
- βi=beta of the i stock return
- ΔM=change in the market price
- e=residual error term
