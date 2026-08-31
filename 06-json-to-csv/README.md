# 06. Converting JSON to a CSV File

A short, focused lesson on file conversion, going from API data straight to a downloadable file.

## What it does

Fetches a list of countries as JSON from an API, then converts that JSON array into a CSV file.

## Nodes used

| Node | Purpose |
|---|---|
| Manual Trigger | Starts the workflow |
| HTTP Request | Fetches country data as JSON |
| Convert to File | Converts JSON items into a CSV file as binary data |

## What this teaches

- How the Convert to File node turns structured JSON into a downloadable file format
- Why this matters in real automations: reports, exports, and email attachments are almost always files, not raw JSON

## How to use this

1. Import `workflow.json`
2. Execute the workflow
3. Download the binary output from the Convert to File node to see the generated CSV
