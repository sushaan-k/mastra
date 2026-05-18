---
'@mastra/mcp': patch
---

Close the previous transport when `InternalMastraMCPClient` receives a server-triggered connection close. Previously the SDK `onclose` handler only cleared `isConnected`, so the next `connect()` would assign a fresh transport while the old one's EventSource kept reconnecting in the background, growing the MCP server's session map over time.
