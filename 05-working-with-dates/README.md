# 05. Working With Dates

Dates are one of the most common sources of bugs in automation. This lesson works through rounding, comparing, and adding to dates using n8n's Date & Time node.

## What it does

Pulls customer records from the training data source, rounds each customer's "created" date up, checks whether that date is after 1960, then either adds 5 days (true branch) or adds 20 years (false branch) to demonstrate two different date operations.

## Nodes used

| Node | Purpose |
|---|---|
| Manual Trigger | Starts the workflow |
| n8n Training Customer Datastore | Returns sample customer records (a data source built into the course sandbox) |
| Date & Time (Round Date) | Rounds a date value up to the nearest unit |
| IF | Branches based on a date comparison (after 1960) |
| Date & Time (Add 5 Days) | Adds 5 days to a date on the true branch |
| Set (Add 20 Years) | Uses a Luxon date expression directly in a Set node to add 20 years, an alternate way to manipulate dates |

## What this teaches

- Rounding dates up or down to clean units
- Comparing dates with the IF node's dateTime operator
- Two different ways to do date math in n8n: the dedicated Date & Time node, and inline Luxon expressions in a Set node
- Why `includeInputFields` matters when you want to keep the rest of your data alongside a new calculated field

## How to use this

1. Import `workflow.json`
2. This uses the built-in n8n training data source, so it should run immediately without extra credentials
3. Execute and compare the two branches to see the different date math applied
