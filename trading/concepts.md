***
_Powered by Gemini_
***

# Table of content
- [Order Book Matching](#Order-Book-Matching)

## Order Book Matching

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
