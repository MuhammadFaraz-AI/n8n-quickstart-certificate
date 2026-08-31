# 09. Batch Processing RSS Feeds

Introduces the Loop Over Items (Split In Batches) node, one of the most important nodes for handling lists safely in n8n.

## What it does

Builds a small list of two RSS feed URLs, then loops through them one at a time, reading each feed individually rather than trying to process both at once.

## Nodes used

| Node | Purpose |
|---|---|
| Manual Trigger | Starts the workflow |
| Code | Generates a list of RSS feed URLs to process |
| Loop Over Items (Split In Batches) | Feeds items into the rest of the workflow one batch at a time, then loops back until all items are processed |
| RSS Feed Read | Reads and parses an RSS feed from a URL |

## What this teaches

- Why looping matters: some nodes or downstream APIs can't handle a full list of items at once
- How the Loop Over Items node's two outputs work, one carries the current batch forward, the other signals "done" once every item has been processed
- The loop-back connection pattern: RSS Read feeds its result back into Loop Over Items to continue the cycle

## How to use this

1. Import `workflow.json`
2. Execute the workflow
3. Watch the Loop Over Items node run twice, once per feed URL, before completing
