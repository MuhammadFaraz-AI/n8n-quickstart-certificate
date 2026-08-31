# 11. Generating Regional Sales Reports

The Section 2 capstone workflow, and the most complex one in the program. This ties together nearly every concept from earlier lessons into one real reporting pipeline.

## What it does

Pulls order data and customer data, merges them, calculates each order's total, sorts and filters for a Europe-only CSV report, uploads that report, and separately builds a region-by-region sales summary that gets posted to Discord.

## Nodes used

| Node | Purpose |
|---|---|
| Manual Trigger | Starts the workflow |
| HTTP Request (Get Order Data) | Pulls raw order records from the company data API |
| Data Table (Get Customers) | Pulls customer records to merge in |
| Merge | Joins orders to customers on `customerID` |
| Set (Calculate Total) | Computes `orderTotal` as price times quantity |
| Sort | Orders results by total value, descending |
| Filter (Europe Only) | Keeps only orders where region is Europe, for one specific report |
| Code | Sums the filtered totals into a single number |
| Convert to File (x2) | Turns both the filtered order list and the regional summary into CSV files |
| HTTP Request (Upload Report) | Sends the generated CSV back to the course's reporting endpoint |
| Summarize | Groups all orders by region and sums totals per region, a completely separate branch from the Europe-only report |
| Sort | Ranks regions by total sales, descending |
| Set (Build Discord Message) | Formats a human-readable summary string |
| Discord | Posts the regional summary to a Discord channel |

## What this teaches

- Combining two data sources with Merge before doing any calculation
- Deriving new fields with Set, then sorting and filtering on them, the same pattern used in almost every reporting workflow
- Two different aggregation approaches in the same workflow: manual summation in a Code node, and the built-in Summarize node for group-by style totals
- Fanning one workflow into two separate outputs (a filtered CSV report and a Discord summary) from the same underlying data
- Uploading a generated file back to an external API as the final automation step

## Note on setup

The HTTP Request nodes call the course's sandbox API and need your own assessment ID. The Data Table node needs a `customers` table with a `customerID` column. Discord needs your own webhook credential.

## How to use this

1. Import `workflow.json`
2. Add your assessment ID and a Header Auth credential
3. Point the Data Table node at your customers table
4. Add a Discord webhook credential
5. Execute and check both output branches, the CSV upload and the Discord message
