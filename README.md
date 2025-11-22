# Rajasthan Royals IPL 2026 Hackathon Submission 🏏

This repository contains the data analysis and squad optimization logic for the Rajasthan Royals (RR) IPL 2026 Mock Auction. Using real IPL data (2023-2025), this project automates squad selection to maximize "Wins Above Replacement" (WAR) within strict budget and roster constraints.

📄 **Full Methodology:** [rr_hackthon_akshat_mittal.pdf](rr_hackthon_akshat_mittal.pdf)

## 🎯 Project Goal
RR enters the 2026 auction with a strong core but specific gaps. The objective is to fill **2–9 squad slots** (max 1 Overseas) using a remaining purse of **₹16.05 Cr**, specifically targeting:
1.  **Lead Spinner:** To replace Yuzvendra Chahal (Targeting Economy < 8).
2.  **Finisher:** High strike-rate lower-middle order batter (Targeting SR > 140).

## 🧠 Strategy: "Stars and Scrubs"
We utilize a greedy optimization algorithm focused on Utility scores.
* **The Approach:** Allocate ~95% of the budget to 2-3 proven stars (High Utility) and fill remaining slots with high-value uncapped players.
* **Projected Impact:** Increases squad WAR significantly, boosting the projected win rate.

## 📂 Repository Structure
* `datasets/`: Contains raw data (2025 auction results, player stats 2023-25, and current RR retained squad).
* `solution/`:
    * `makes_Datatset.ipynb`: Data cleaning pipeline. Merges raw CSVs, normalizes prices, and calculates median stats.
    * `solution.ipynb`: The optimization engine. Assigns roles, calculates "Proven Scores," and selects the final squad.

## 🚀 How to Run

### 1. Setup Environment
You will need Python 3.8+ and Jupyter Notebook.

```bash
git clone [https://github.com/smartplay28/rr_hackthon.git](https://github.com/smartplay28/rr_hackthon.git)
cd rr_hackthon
pip install pandas numpy jupyter openpyxl
```

### 2. Generate Data (Important)
You must run the data processing script before the optimizer.
1. Open `solution/makes_Datatset.ipynb` in Jupyter.
2. Run all cells.
3. **Output:** This creates `merged_dataset.csv` from the raw files in the `datasets/` folder.

### 3. Run Optimization
1. Open `solution/solution.ipynb`.
2. Run all cells.
3. **Output:** The notebook reads the merged data, applies the "Proven Score" algorithm, and prints the final squad table.

## ⚖️ Rules & Constraints

The optimization logic strictly follows the specific Hackathon limitations:

* **Budget:** Must stay under **₹16.05 Cr** (Total Purse - Retention Cost).
* **Roster Size:** Must add between **2 and 9 players** (Targeting a total squad size of 18-25).
* **Overseas Limit:** Can add maximum **1 Overseas player** (RR already has 7 retained; limit is 8).

## 🏆 Projected Squad Additions

| Player | Role | Category | Bid (₹ Cr) | WAR Boost |
| :--- | :--- | :--- | :--- | :--- |
| **Ravi Bishnoi** | Lead Spinner | Indian | 8.80 | +1.8 |
| **Andre Russell** | Finisher | Overseas | 6.40 | +2.1 |
| **Akshat Raghuwanshi** | Middle-Order | Indian | 0.80 | +0.3 |
| **Total** | | | **16.00** | **+4.2** |

## ⚠️ Limitations
* **Data Scope:** Analysis is based on historical stats (2023-2025) and does not account for real-time injury updates.
* **Price Logic:** Bids are derived directly from historical valuations and base prices (no inflation assumed).
