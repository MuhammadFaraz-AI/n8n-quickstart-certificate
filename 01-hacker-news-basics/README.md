# 01. Hacker News Basics

The very first workflow in the n8n Quickstart program. This is where you learn the two things every n8n workflow needs: a trigger and a node that does something.

## What it does

Fetches the 10 most recent articles from Hacker News and returns them as workflow items.

## Nodes used

| Node | Purpose |
|---|---|
| Manual Trigger | Starts the workflow when you click "Execute workflow" in the editor |
| Hacker News | Calls the Hacker News API and returns the latest 10 articles |

## What this teaches

- How to add a trigger node, every workflow needs one
- How to configure a node's parameters (resource, limit)
- How to run a workflow manually and inspect the output
- How to save a workflow

## How to use this

1. Import `workflow.json` into your n8n instance
2. Click "Execute workflow"
3. Check the output on the Hacker News node, you should see 10 articles with title, url, and score
