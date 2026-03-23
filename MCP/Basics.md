
## What is MCP?
MCP allows Clients like agents to connect to external tools


## What happens under the hood ? (for stdin/stdout MCP commn)

The MCP server communicates using stdin/stdout — the same input/output channels that a terminal uses.

stdin = "standard input" — where a program reads incoming data (like you typing into a terminal)
stdout = "standard output" — where a program writes its responses
JSON-RPC is just a format for sending requests as JSON. It looks like this:

```
{"jsonrpc":"2.0", "id":1, "method":"tools/call", "params":{"name":"tool_name", "arguments":{"arg1":"value1"}}}
```

That's it — it's a JSON object that says "call the list_selectors tool with appName: outlook".

## How it works normally
When Copilot Chat uses the MCP server, here's what happens invisibly:

```
Copilot Chat  ──(writes JSON-RPC to stdin)──▶  mcp-server.ts
Copilot Chat  ◀──(reads JSON-RPC from stdout)──  mcp-server.ts
```

## What "pipe to stdin" means
When you run the server standalone (without Copilot), there's no client sending requests. So you become the client by literally typing/pasting JSON into the terminal:

```
1. You start the server:    npx tsx ./ai-test-agent/mcp-server.ts
2. The server starts and waits for input on stdin...
3. You paste this into the terminal and press Enter:
   {"jsonrpc":"2.0","id":1,"method":"tools/list","params":{}}
4. The server reads it, processes it, and prints the response to stdout
```

**"Piping"** just means sending text into a program's input. You can do it by:

Typing/pasting directly into the terminal
Using a pipe: echo '{"jsonrpc":"2.0"...}' | npx tsx mcp-server.ts
