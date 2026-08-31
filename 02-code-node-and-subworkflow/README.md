# 02. Code Node and Sub-workflow Call

This lesson introduces two ideas at once: writing custom JavaScript inside a workflow, and calling one workflow from another.

## What it does

Generates a sample customer name with messy spacing using a Code node, then hands that data off to a separate sub-workflow ("Sub - Format Customer Name") that cleans it up.

## Nodes used

| Node | Purpose |
|---|---|
| Manual Trigger | Starts the workflow |
| Code | Runs raw JavaScript to produce test data with messy spacing |
| Execute Workflow | Calls a separate, reusable sub-workflow and passes data into it |

## What this teaches

- Writing JavaScript in the Code node to shape data exactly how you need it
- Why splitting logic into sub-workflows makes automations reusable and easier to maintain, instead of one giant workflow doing everything
- How the Execute Workflow node connects two independent workflows together

## Note on the sub-workflow reference

The `workflowId` field in `workflow.json` is set to a placeholder. To run this yourself, build a small sub-workflow that trims whitespace from a name and point this node at it, or swap in any sub-workflow you have.

## How to use this

1. Import `workflow.json`
2. Create or point to a sub-workflow named "Sub - Format Customer Name" that accepts `firstName` and `lastName` and trims them
3. Execute the workflow and confirm the sub-workflow receives and processes the data
