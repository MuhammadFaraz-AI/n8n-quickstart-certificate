# 07. Splitting API Results

Many APIs return one item that contains an array buried inside it, not a clean list of items. This lesson fixes that.

## What it does

Calls the PokeAPI for a list of 5 Pokemon, then splits the nested `results` array out into individual, separate items.

## Nodes used

| Node | Purpose |
|---|---|
| Manual Trigger | Starts the workflow |
| HTTP Request | Calls the public PokeAPI, returns one item containing a `results` array |
| Split Out | Turns each entry in the `results` array into its own separate item |

## What this teaches

- Why a single API response is often not "n8n-ready" out of the box
- Using Split Out to turn nested arrays into individual items you can loop over, filter, or process one at a time
- This is one of the most common data-shaping problems you'll hit in real client integrations

## How to use this

1. Import `workflow.json`
2. Execute the workflow
3. Compare the single item from Get Pokemon against the 5 separate items produced by Split Pokemon
