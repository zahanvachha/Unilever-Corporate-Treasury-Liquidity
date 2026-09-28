# Unilever-Corporate-Treasury-Liquidity
# Corporate Treasury & Liquidity Optimisation Engine — Unilever plc

A public-data corporate treasury project analysing how a multinational can manage liquidity, funding, surplus cash and FX exposure under different operating scenarios.

**Model-selected robust liquidity buffer: €3.5bn**

> The €3.5bn figure is a model output under stated assumptions and is **not** a claim about Unilever's internal treasury policy or actual liquidity target.

---

## Project Overview

This project asks:

> **How should a multinational allocate and manage liquidity so that it maintains sufficient cash while minimising unnecessary funding, FX and opportunity costs?**

The analysis uses publicly available Unilever financial information to build a historical financial model, a 13-week liquidity forecast and an independent Python analysis layer.

The project focuses on the practical treasury problem of **when liquidity is needed, how much is required, and what the cost of maintaining that protection may be.**

---

## Key Results

| Scenario | Model-selected liquidity buffer |
|---|---:|
| Base | €1.0bn |
| Downside | €1.2bn |
| Severe | €3.5bn |
| **Robust across scenarios** | **€3.5bn** |

These are model outputs under the assumptions described in the project report.

### Main findings

- Annual free cash flow does not eliminate short-term liquidity risk: the timing of receipts and payments can create significant temporary cash requirements.
- Customer collection timing is the most important individual liquidity stress driver in the model.
- A **€3.5bn buffer** is selected as the smallest tested buffer that satisfies the liquidity constraint across the modelled scenarios.
- The buffer selection is **constraint-driven rather than rate-driven**: changing funding rates or investment yields did not change the selected buffer within the tested ranges.
- Python independently reproduces the Excel model and provides additional sensitivity and robustness analysis.

---

## What Was Built

### 1. Historical Financial Model

Five years of publicly reported financial data were reconciled across:

- Income statement
- Balance sheet
- Cash flow statement
- Working capital
- Financial liabilities
- Net debt
- Free cash flow

The model also controls for the distinction between **2023 original reported results and 2023 continuing-operations results** following subsequent reporting changes.

### 2. 13-Week Liquidity Forecast

The Excel treasury model forecasts weekly liquidity under:

- Base
- Downside
- Severe

scenarios.

The model incorporates:

- Customer collections
- Supplier payments
- Payroll
- Tax
- Capex
- Interest
- Dividends
- Share buybacks
- Debt refinancing
- Funding requirements
- Surplus cash investment
- FX liquidity effects

### 3. Liquidity Buffer Analysis

The model constructs a transparent liquidity-buffer methodology based on stressed operating outflows, a three-week coverage period and restricted cash.

The methodology is a **project assumption**, not a disclosed Unilever treasury policy.

### 4. Funding & Surplus Cash

The model analyses the trade-off between:

- Holding additional liquidity
- Drawing or arranging funding
- Investing surplus cash
- The resulting treasury cost

Funding assumptions are anchored to publicly disclosed Unilever borrowing information but are **not intended to represent actual bank pricing**.

### 5. FX Liquidity Analysis

Illustrative operating cash-flow currency assumptions are used to test the impact of non-EUR currency movements on liquidity.

These assumptions are explicitly modelled proxies and should not be interpreted as Unilever-disclosed operating cash-flow currency percentages.

### 6. Python Validation & Robustness

Python independently reproduces the Excel model and tests:

- Scenario outputs
- Buffer optimisation
- Funding requirements
- Treasury costs
- Sensitivity analysis
- Robustness to changes in key assumptions

The Python validation matched the Excel model across **842 tested items**, with a maximum numerical difference of approximately **1e-11**.

---

## Visual Results

### 13-Week Liquidity Profile

![13-Week Liquidity Profile](./charts/liquidity_profile.png)

### Liquidity Buffer vs. Treasury Cost

![Liquidity Buffer vs. Treasury Cost](./charts/buffer_vs_cost.png)

### Liquidity Buffer Sensitivity

![Liquidity Buffer Sensitivity](./charts/buffer_sensitivity.png)

---

## Technology

- **Microsoft Excel** — financial modelling, scenario analysis and treasury model
- **Python** — independent model reproduction, optimisation and robustness analysis
- **pandas / NumPy** — data handling and numerical analysis
- **SciPy** — optimisation and stress testing
- **Matplotlib** — visualisation

---

## Repository Structure

```text
├── README.md
│
├── report/
│   └── Unilever_Corporate_Treasury_Liquidity_Project.pdf
│
├── excel/
│   └── Unilever_Treasury_Liquidity_Model.xlsx
│
├── python/
│   ├── run_all.py
│   ├── treasury_engine.py
│   ├── config.py
│   ├── 01_import_excel.py
│   ├── 02_validate_excel.py
│   ├── 03_reproduce_excel.py
│   ├── 04_buffer_analysis.py
│   ├── 05_sensitivity.py
│   ├── 06_robustness.py
│   └── 07_outputs.py
│
├── results/
│   └── Unilever_Treasury_Python_Results.xlsx
│
└── charts/
    ├── liquidity_profile.png
    ├── buffer_vs_cost.png
    └── buffer_sensitivity.png
