

## Why MCP?
1. MCP shifts the burden to write, test, mantain and execute code from our app server to another server(ie MCP server). So, the MCP server can be thought of as an interface to an outside dervice.<br>
2. Example: we might have a GitHub MCP server that provide access to GitHub functionality.

## Transport Protocol
The Communicaation b/w MCP Client and MCP server id transport protocol agnostic ie Communication can be done over different protocols like Stdio(local), Websockets, HTPP etc.

MCP specification defines different types of mesages that can be exchanged. Example- ListToolRequest, ListToolResult, CallToolRequest, CallTooResult

## MCP SDKs
1. Defines tools: The MCP project provides SDKs for building servers and clients in variaty of languages

### Server


### Client


### MCP Inspector
Used to test MCP server 
