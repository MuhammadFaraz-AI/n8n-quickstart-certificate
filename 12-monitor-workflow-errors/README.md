# 12. Monitor Workflow Errors

Error handling as its own dedicated workflow, the professional pattern for catching failures across every other workflow in your instance.

## What it does

Listens for errors from any workflow that's configured to use it as an error workflow, builds a readable alert message with the failing workflow's name, error message, and last executed node, then posts that alert to Discord.

## Nodes used

| Node | Purpose |
|---|---|
| Error Trigger | Fires automatically whenever a linked workflow fails, instead of being triggered manually |
| Set | Builds a single formatted string combining workflow name, error message, last node, and a link to the failed execution |
| Discord | Posts the alert to a Discord channel |

## What this teaches

- The Error Trigger node, and the standard n8n pattern of having one shared "error workflow" that other workflows point to in their settings
- Pulling structured data out of `$json.execution` and `$json.workflow` to build a useful, actionable alert instead of a generic failure notice
- Why production automations need visibility into failures, not just for you, but for anyone else relying on the workflow

## How to use this

1. Import `workflow.json`
2. Add your own Discord webhook credential
3. In any other workflow's Settings, set this workflow as its "Error Workflow"
4. Trigger a failure in that workflow to confirm the alert arrives in Discord
