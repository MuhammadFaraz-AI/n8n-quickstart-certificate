# 03. Data Warehouse Report Automation

The Section 1 business case workflow. This is where the course stops being isolated node demos and starts looking like something you'd actually build for a client: pull real business data, branch on conditions, calculate totals, store results, and notify a team.

## What it does

On a weekly schedule (or manually, for testing), pulls order records from a company data warehouse, checks whether each order is still "processing," stores the ones that are in a data table, calculates totals for the rest, and posts a weekly summary to Discord.

## Nodes used

| Node | Purpose |
|---|---|
| Manual Trigger / Schedule Trigger | Two ways to start the same workflow, manual for testing, scheduled for production (every Monday 9am) |
| HTTP Request | Pulls order data from the warehouse API, authenticated with a header credential |
| IF | Branches the flow based on whether an order's status is "processing" |
| Set | Shapes the branch-specific fields before storing them |
| Data Table (upsert) | Writes processing orders into a persistent data table, insert if new, update if it already exists |
| Code (x2) | Calculates order counts and total booked value across all incoming items |
| Discord | Posts the weekly summary message to a Discord channel |

## What this teaches

- Combining a manual trigger and a schedule trigger on the same workflow for testing versus production
- Branching logic with IF, and doing different things with each branch
- The difference between "insert" and "upsert" when writing to a data table
- Aggregating data with a Code node instead of a UI-only node, useful when the built-in nodes don't do exactly what you need
- Sending a formatted, dynamic message to a team channel as the final automation step

## Note on setup

The HTTP Request node calls n8n's own training sandbox API (`learn.app.n8n.cloud`), so it needs your own course assessment ID and Header Auth credential to run for real. The Data Table and Discord nodes are also pointed at placeholders, wire up your own before running this end to end.

## How to use this

1. Import `workflow.json`
2. Add a Header Auth credential with your own assessment ID from the Quickstart course
3. Point the Data Table node at a table with `orderID` (number) and `employeeName` (string) columns
4. Add your own Discord webhook credential
5. Run manually first to confirm the branch logic, then activate the schedule trigger
