# Sample data: construction project portfolio (synthetic)

All names, values and transactions here are **made up** for the tutorial. There's no client or company data. Data runs to 31 Oct 2026, with amounts in AED.

| File | Rows | Grain | Key columns |
|---|---|---|---|
| `dim_project.csv` | 8 | one per project | ProjectID, ProjectName, Sector, City, StartDate, PlannedFinish, ContractValueAED, ProjectManager |
| `dim_cost_code.csv` | 6 | one per cost code | CostCode, CostCategory, Discipline |
| `fact_budget.csv` | 48 | project × cost code | ProjectID, CostCode, BudgetAED |
| `fact_cost.csv` | 4,333 | one per cost transaction | TransactionID, PostingDate, ProjectID, CostCode, Vendor, CostType, AmountAED |
| `fact_progress.csv` | 160 | project × month end | ProjectID, MonthEnd, PlannedPctComplete, ActualPctComplete (cumulative, 0–1) |

## What the video asks Claude to build

1. Load the 5 CSVs and set data types.
2. Create a Date table in DAX and mark it as the date table.
3. Relationships: projects and cost codes to the fact tables; Date to PostingDate and MonthEnd.
4. Measures: Budget, Actual Cost, Cost Variance, Planned Value, Earned Value, CPI, SPI, Estimate at Completion.
5. Measure descriptions and display folders, plus a best-practice check.

The story built into the data: some projects run over budget and some run behind schedule, so the model has real findings to show, such as the Community Sports Centre and Logistics Hub Phase 2 being over budget.
