# Week 3: Cross-Cultural Market Basket Analysis

**Research question:** Does the rule **Dates → Milk** behave differently during **Ramadan** than in **baseline** (non-event) baskets in Istanbul and Dubai?

| Context | N | Support | Confidence | Lift |
|---|---|---|---|---|
| Ramadan | 99 | 0.323 | 0.744 | 1.535 |
| Baseline | 132 | 0.000 | 0.000 | 0.000 |

## Files

| File | Content |
|---|---|
| `analysis.ipynb` | Full analysis: data prep, Apriori, rule comparison, charts, interpretation, BI action, limitations |
| `rule_comparison.csv` | Rule comparison table (created by the notebook) |
| `fig_rules_per_confidence.png` | Number of rules per confidence threshold, per group |
| `fig_rule_comparison.png` | Support, confidence and lift for Dates → Milk |
| `Cross Cultural Market Basket Dataset v2.xlsx` | Data (sheet `Transactions` only) |

## How to run

1. Install the packages:
   ```bash
   pip install pandas==3.0.6 numpy==2.5.3 mlxtend==0.25.0 matplotlib==3.11.2 openpyxl==3.1.5 jupyter
   ```
2. Keep the notebook and the `.xlsx` file in the same folder.
3. Open `analysis.ipynb` and choose **Run All**, or run from the terminal:
   ```bash
   jupyter nbconvert --to notebook --execute --inplace analysis.ipynb
   ```
   This recreates the CSV and the two PNG figures.

## Environment

| Package | Version |
|---|---|
| Python | 3.13.7 |
| pandas | 3.0.6 |
| numpy | 2.5.3 |
| mlxtend | 0.25.0 |
| matplotlib | 3.11.2 |
| openpyxl | 3.1.5 |

## Settings

| Setting | Value |
|---|---|
| Markets | `TR_Istanbul`, `AE_Dubai` |
| Context A | `Cultural_Event == "Ramadan"` (N = 99) |
| Context B | `Cultural_Event == "None"` (N = 132) |
| Excluded | Eid baskets in the same markets (N = 69) |
| `MIN_SUPPORT` | 0.05 (same for both groups) |
| `MIN_CONFIDENCE` | 0.3 (same for both groups) |
| Algorithm | Apriori (`mlxtend.frequent_patterns`) |
| Seed | 42. Apriori is deterministic, so the results do not depend on it. The dataset itself was generated with seed 20260916. |
| Missing values | Read with `keep_default_na=False` so `"None"` stays a real category |
