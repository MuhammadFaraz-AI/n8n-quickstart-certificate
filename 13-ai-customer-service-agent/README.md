# 13. AI Customer Service Agent

The final workflow in the program, and the whole reason "Quickstart" ends with AI rather than just automation. This is a working conversational agent with memory and two real data tools.

## What it does

A chat-triggered AI agent that answers customer service questions by looking up real customer records and order data, and remembers context across a conversation.

## Nodes used

| Node | Purpose |
|---|---|
| Chat Trigger | Opens a chat interface and starts the agent on each incoming message |
| Google Gemini Chat Model | The LLM powering the agent's reasoning (Gemini 2.5 Flash) |
| AI Agent | The core agent node, holds the system prompt and decides which tool to call based on the user's question |
| Simple Memory (Buffer Window) | Keeps recent conversation turns so the agent has context across multiple messages |
| Data Table Tool (GetCustomers) | Lets the agent query customer records directly as a callable tool |
| HTTP Request Tool (GetOrderData) | Lets the agent call an external API for order, pricing, and employee data as a second callable tool |

## What this teaches

- The core AI Agent pattern in n8n: one agent node, one language model, and one or more tools it can choose to call
- Writing a system prompt that tells the agent exactly when to use which tool, this is what keeps an agent from guessing or hallucinating instead of looking things up
- Turning a Data Table and a plain HTTP Request into agent-callable tools, not just static workflow nodes
- Adding conversational memory so the agent handles multi-turn conversations, not just one-off questions

## Note on setup

This needs your own Google Gemini API credential, a customers data table, and your own assessment ID for the order data tool.

## How to use this

1. Import `workflow.json`
2. Add a Google Gemini (or swap in any supported chat model) credential
3. Point GetCustomers at your own customers data table
4. Add your assessment ID and a Header Auth credential to GetOrderData
5. Open the chat interface and ask it something like "what did customer 12 order last month?"
