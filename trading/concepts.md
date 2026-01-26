***
_Powered by Gemini and GPT_
***

# Table of content
- [Order Book Matching](#Order-Book-Matching)
- [Sharpe Ratio](#Sharpe-Ratio)

# Order Book Matching

At its core, order book matching is the engine that powers stock exchanges (like Nasdaq, NYSE) and crypto exchanges. It is the automated process of pairing a buyer with a seller so a trade can happen.

The "Order Book" is simply a digital list of everyone waiting to buy or sell a specific asset, organized by price.
- Bids (Buys): People who want to buy. They want the lowest price possible.
- Asks (Sells): People who want to sell. They want the highest price possible.

The Matching Engine is the algorithm that scans this list. Whenever a buyer's price meets a seller's price (or crosses it), the engine "matches" them and executes a trade.

To understand order book matching, we should understand some important concepts.

### Types of markets
**Direct search**
- Buyers and Sellers seek each other directly

**Brokered markets**
- Brokers search out buyers and sellers

**Dealer markets**
- Dealers have inventories of assets from which they buy and sell

**Auction markets**
- Traders converge at one “place” to trade

### Types of order

**Market order**: execute immediately at best price available when the order reaches the trading floor
- aggressive orders
- You say, "I want to buy 100 shares RIGHT NOW at whatever price is available."

**Limit order**: price-contingent order (there is a condition before the order gets executed)
- Passive orders
- e.g. You say, "I will buy 100 shares, but ONLY if the price drops to $99."

| Action ↓ / Condition → | Price below the limit | Price above the limit |
| :--- | :--- | :--- |
| **Buy**                | Limit-Buy Order       | Stop-Buy Order        |
| **Sell**               | Stop-Loss Order       | Limit-Sell Order      |

### Algorithms 

#### 1. The Standard Algorithm: Price/Time Priority (FIFO)
Most equity (stock) markets use Price/Time Priority. This is often called FIFO (First-In-First-Out).

The Rules:
- Price is King: The best price always gets filled first. (Highest Bid or Lowest Ask).
- Time is Tie-Breaker: If two people offer the exact same price, the person who arrived first gets filled first.

**Visual Example: The Queue**

Imagine an order book for "Stock X" looks like this currently:

| Buy Orders (Bids)        | Price    | Sell Orders (Asks)                               |
|--------------------------|----------|--------------------------------------------------|
|                          | $100.05  | Seller C: 50 shares (Arrived 10:05 AM)           |
|                          | $100.02  | Seller A: 100 shares (Arrived 10:01 AM)          |
|                          | $100.02  | Seller B: 50 shares (Arrived 10:03 AM)           |
| **Spread ($0.01)**       |          |                                                  |
| Buyer X: 200 shares      | $100.01  |                                                  |
| Buyer Y: 50 shares       | $100.00  |                                                  |

(Note: Seller A and Seller B are at the same price, but Seller A is ahead in the queue because they arrived earlier.)

**Scenario A: A Simple Match**

An aggressive buyer enters a Market Order to buy 120 shares.
1. The engine looks for the cheapest Seller. That is $100.02.
2. Seller A has 100 shares. The buyer takes all of them.
3. The buyer still needs 20 shares. The engine looks at the next person at $100.02, which is Seller B.
4. The buyer takes 20 shares from Seller B.

Result:
- Seller A is sold out (fully filled).
- Seller B has 30 shares left (partially filled).
- The trade price was $100.02.

#### 2. The Futures Algorithm: Pro-Rata Matching

Some markets, especially Futures (like interest rates or commodities), use Pro-Rata matching. In these markets, "Time" matters less. If multiple sellers are at the best price, the engine splits the incoming order among them based on size, not who came first.

**The Logic**: This encourages traders to post massive orders (adding liquidity) because a bigger order guarantees a bigger chunk of the trade.

**Visual Example: The Split**

Imagine the Order Book for a Corn Future contract. An aggressive buyer wants 100 contracts at $50.00.

There are three sellers waiting at $50.00:
- Seller Big: Selling 800 contracts.
- Seller Small: Selling 200 contracts.
- Total Available: 1,000 contracts.

If this were FIFO: Seller Big would get everything if they arrived 1 millisecond earlier. In Pro-Rata: The engine calculates percentages.
- Seller Big owns 80% of the available liquidity (800/1000).
- Seller Small owns 20% of the available liquidity (200/1000).

The Match:The buyer's order of 100 contracts is split:
- Seller Big sells 80 contracts (80% of the buy order).
- Seller Small sells 20 contracts (20% of the buy order).

# Sharpe Ratio

The **Sharpe Ratio** is one of the most widely used measures of **risk-adjusted return**. It answers a simple but fundamental question:

> *How much excess return am I receiving for each unit of risk I take?*

Formally, the Sharpe Ratio is defined as:

$$
\text{Sharpe Ratio} = \frac{E[R_p] - R_f}{\sigma_p}
$$

where:

* $(E[R_p])$ = expected return of the portfolio
* $(R_f)$ = risk-free rate
* $(\sigma_p)$ = standard deviation of portfolio returns (volatility)

---

### **Economic Intuition**

Raw returns alone are not meaningful without considering risk. A strategy that earns 20% annually but fluctuates wildly is not necessarily better than one earning 12% with low volatility. The Sharpe Ratio standardizes performance by penalizing volatility:

* **High Sharpe Ratio** → Efficient conversion of risk into return
* **Low Sharpe Ratio** → Poor compensation for risk

In practical terms:

* Sharpe ≈ 0.5 → weak
* Sharpe ≈ 1.0 → good
* Sharpe ≈ 2.0 → very good
* Sharpe ≥ 3.0 → exceptional

In institutional investing, a Sharpe above 1 is typically considered investable, while many top hedge funds target Sharpe ratios above 1.5–2 over long horizons.

---

### **Why Volatility Is Treated as Risk**

The Sharpe Ratio assumes investors dislike **variability of outcomes**, regardless of direction. Both large gains and large losses increase volatility, so both are treated as “risk.” This is a simplification, but it makes the metric mathematically convenient and broadly applicable.

This assumption works reasonably well for:

* Market-neutral strategies
* Statistical arbitrage
* Factor portfolios
* Long-only funds

But it can misrepresent risk for strategies with skewed or fat-tailed distributions.

---

### **Sharpe Ratio and Portfolio Construction**

Sharpe Ratio plays a central role in optimization. If we assume returns are approximately normally distributed and investors care only about mean and variance, then:

> Maximizing Sharpe Ratio ≡ Finding the tangency portfolio in mean–variance space.

This is the portfolio that lies on the efficient frontier with the highest slope relative to the risk-free rate.

In quantitative trading, many optimizers directly aim to maximize expected Sharpe:

$$
\max_w \frac{w^T \mu}{\sqrt{w^T \Sigma w}}
$$

where:

* $(w)$ = portfolio weights
* $(\mu)$ = expected returns
* $(\Sigma)$ = covariance matrix

---

### **Sharpe Ratio in Market-Neutral Strategies**

For market-neutral or factor-neutral strategies:

* Market beta ≈ 0
* Industry beta ≈ 0
* Other factor betas ≈ 0

Since systematic risk is stripped away, **most remaining volatility comes from idiosyncratic noise**, not rewarded risk premia. Therefore, a high Sharpe Ratio is interpreted as strong evidence of genuine alpha.

This is why hedge funds often emphasize Sharpe more than raw returns.

---

### **Limitations**

* Penalizes upside volatility
* Assumes normality
* Sensitive to estimation error
* Can be inflated by smoothing or illiquid assets

Despite these weaknesses, Sharpe remains the industry’s first-pass metric.

### **Key Takeaway**

The Sharpe Ratio measures **skill per unit of uncertainty**. It tells us how efficiently a strategy transforms risk into excess return, making it the cornerstone of quantitative performance evaluation.
