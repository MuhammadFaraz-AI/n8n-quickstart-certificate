# 08. Merging Data (Basic)

The first of two merging lessons in this program. This one covers the fundamentals: combining two separate item lists by matching a shared field.

## What it does

Pulls customer records from the training data source, generates a second, unrelated list of fictional characters in a Code node, then merges the two lists together by matching on the `name` field.

## Nodes used

| Node | Purpose |
|---|---|
| Manual Trigger | Starts the workflow |
| n8n Training Customer Datastore | Returns sample customer records |
| Code | Generates a second list of test data to merge against |
| Merge (combine mode) | Joins two separate item lists into one, matching rows where `name` is equal |

## What this teaches

- The Merge node's "combine" mode, and how field-matching works
- Why you'd merge two branches of a workflow rather than just running them one after another
- This is the simpler cousin of lesson 10, which does the same concept against a real data table instead of hardcoded test data

## How to use this

1. Import `workflow.json`
2. This uses the built-in training data source, so it runs immediately without extra credentials
3. Execute and inspect the Merge node's output, only names that exist in both lists will combine
