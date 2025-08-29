# 🚀 **Sequential Swing Low–High–Low Breakout Strategy with Dual Stop-Loss & Volume-Climax Exit**

## 📝 Strategy Description

This algorithm is a **swing-pattern breakout strategy** designed to capture **trend continuation opportunities** while enforcing strict **risk management** and **profit-protection mechanisms**.

It identifies **sequential swing structures (Low–High–Low)**, validates them against trend health, and executes trades with **layered stop-losses** and **volume-based exits** to prevent premature reversals.

---

### 🔑 **Core Logic of the Strategy**

1. **Trend Labeling**

   * Classifies short-term windows of closing prices:

     * `1 → Uptrend`
     * `0 → Downtrend`
     * `-1 → Neutral`

2. **Swing Structure Extraction**

   * Detects and stores **local swing lows** and **swing highs**.
   * Creates a sequence to track breakout opportunities.

3. **Pattern Recognition: Low–High–Low (L–H–L)**

   * Valid buy setup only if:

     ```
     L1 < H1 < L2   (with correct chronological order)
     ```
   * Ensures pattern occurs within a **healthy uptrend**.

4. **Buy Execution & Capital Deployment**

   * Buys only if pattern confirms AND volume doesn’t signal distribution.
   * Capital allocation:

     * **3% of capital** → Initial buy.
     * **5% of capital** → Averaging down below last buy price.

5. **Dual Stop-Loss Design**

   * **8% price buffer stop-loss** (relative to entry).
   * **Structural stop-loss** (if price breaches last swing low).
   * Whichever is **stricter** is applied.

6. **Exit Strategy**

   * **Volume-Climax Exit:**

     * If current volume > 105% of 3-bar average & price closes higher → exit.
   * **Structure Breakdown Exit:**

     * If number of valid swing lows decreases → force market sell.

---

### 📊 **Trading Takeaways**

* 📌 **Entry Logic:** Breakout confirmation through sequential swing validation.
* 📌 **Position Sizing:** Conservative scaling (3%–5%) to protect capital.
* 📌 **Stop-Loss Design:** Dual approach prevents both sharp losses & structural breakdowns.
* 📌 **Exit Logic:** Volume exhaustion & swing failure ensure disciplined profit-taking.
* 📌 **Objective:** Ride strong trends while systematically cutting losses.

---

## 📚 Libraries Used

* **AlgoAPI**

  * `AlgoAPIUtil` → For order handling & stop-loss automation.
  * `AlgoAPI_Backtest` → For data feed & backtesting simulation.

* **datetime**

  * Generates unique order IDs.
  * Tracks timing for trade references.

* **Python Built-ins**

  * Lists, loops, conditions for pattern recognition, swing labeling, and capital tracking.


