# 10. Merging Data With Data Tables

The second merging lesson, this time using n8n's Data Table feature as a real, persistent data source instead of hardcoded test data, and writing the result back.

## What it does

Pulls a list of countries (with region and subregion info) from an API, pulls existing customer records from a data table, merges the two by matching customer country to country name, then updates each customer record in the table with its region and subregion.

## Nodes used

| Node | Purpose |
|---|---|
| Manual Trigger | Starts the workflow |
| HTTP Request | Fetches country and region reference data |
| Data Table (get) | Reads existing customer records |
| Merge (combine, advanced field matching) | Joins customers to their country's region data using different field names on each side (`customerCountry` to `name`) |
| Data Table (update) | Writes the merged region and subregion values back into each customer's row |

## What this teaches

- Using Data Tables as a real, queryable and writable data store inside n8n, not just an external database
- Merge's advanced field-matching mode, useful when the two sides of a merge don't share an identical column name
- A full read, transform, write cycle against persistent data, which is the shape of most real client automations

## Note on setup

Both Data Table nodes are pointed at a placeholder ID. Point them at your own customers table with `customerID`, `customerCountry`, `region`, and `subregion` columns to run this.

## How to use this

1. Import `workflow.json`
2. Create a data table with the columns above and some sample rows
3. Update both Data Table nodes to point at it
4. Execute and confirm each customer row gets a region and subregion filled in
