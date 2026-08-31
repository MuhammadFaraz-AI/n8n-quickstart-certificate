# 04. Downloading and Editing an Image

Introduces binary data, everything up to this point has been JSON. Images, PDFs, and files work differently in n8n, and this is the first workflow that touches that.

## What it does

Fetches a random dog image URL from an API, downloads the actual image as binary data, then rotates it 180 degrees.

## Nodes used

| Node | Purpose |
|---|---|
| Manual Trigger | Starts the workflow |
| HTTP Request (Get Dog URL) | Calls an API that returns a JSON object containing an image URL |
| HTTP Request (Get Dog Image) | Downloads the actual image file as binary data from that URL |
| Edit Image | Rotates the downloaded image 180 degrees |

## What this teaches

- The difference between JSON data and binary data in n8n
- Chaining two HTTP Request nodes, one to get a reference (the URL), one to fetch the actual resource
- Using an expression (`{{ $json.message }}`) to pass a value from one node into the URL of the next
- Basic image manipulation with the Edit Image node

## How to use this

1. Import `workflow.json`
2. Execute the workflow
3. Check the binary output on the Edit Image node, download it to confirm the rotation worked
