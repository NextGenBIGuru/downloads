# Prompt pack: Power BI MCP Server with Claude

These are the 11 prompts from the video, in the order they appear on screen.

**Before you start**
- Install Claude for Desktop (claude.ai/download), Node.js, and the Power BI MCP server (`npm install -g @microsoft/powerbi-modeling-mcp`), then add the server to `claude_desktop_config.json` and restart Claude.
- Open a blank report in Power BI Desktop, save it as a Power BI project (.pbip) named "Construction Portfolio", and turn off Auto date/time (File > Options and settings > Options > Current file > Data load).
- Put the five CSV files from the download in a folder, and use that folder's full path in prompt 2.
- The server changes your model directly. Always work on a copy.

| # | Prompt |
|---|---|
| 1 | Connect to the Power BI Desktop file I have open, Construction Portfolio, and tell me what's in the model. |
| 2 | Load the five CSV files in `<your data folder>` as tables named Project, Cost Code, Budget, Cost and Progress. Store the folder path in a parameter called DataFolder. Set the data types: dates as Date, money as Decimal, percentages as Decimal. Then refresh and give me the row count of each table. |
| 3 | Create a Date table from 1 Jan 2025 to 31 Dec 2027 with Year, Quarter, Month and Month End columns, and mark it as the date table. |
| 4 | Create the relationships: Project and Cost Code to the fact tables, and Date to Cost[PostingDate] and Progress[MonthEnd]. All one-to-many, single direction. Then list them. |
| 5 | Create a Key Measures table. In a "Cost" folder, add Total Budget, Actual Cost, and Actual Cost to Date (cumulative cost up to the selected date). |
| 6 | Write a one-line description for every measure, and hide the ID columns. |
| 7 | Run a best-practice check on the model and fix anything important. |
| 8 | Now the earned-value measures, in an "EVM" folder: Planned Value and Earned Value (per project, budget × the latest cumulative planned or actual % complete up to the selected date), Planned and Actual % Complete, CPI, SPI, Cost and Schedule Variance, Estimate at Completion (budget ÷ CPI per project), Variance at Completion and Cost Variance %. Then add a Project Health measure in a "Status" folder: On track, Watch or At risk, based on CPI and SPI. |
| 9 | Run a best-practice check on the model and fix anything important. (Same as prompt 7: run it again after big changes.) |
| 10 | Which projects are over budget and behind schedule as of 31 Oct 2026? Run a DAX query and show me CPI and SPI for each project. |
| 11 | Same question, but as of 30 June 2026. |

Claude's answers will not match the video word for word, and it may fix things in a different order. Check the row counts (8, 6, 48, 4,333, 160), the 7 relationships and the CPI/SPI figures against the video.
