# FigAEO for Cursor

Public Cursor plugin for the hosted FigAEO MCP.

- URL: `https://figaeo.com/mcp`
- Transport: Streamable HTTP
- Auth: MCP OAuth 2.1 in the connect card (GitHub or Google)

The first session is two browser hops at $0: OAuth, then Stripe Checkout. Then retry the same tool. This is not one-click paid access.

## Install

Install this plugin from the Cursor Marketplace, or add a remote MCP server in Settings → MCP.

Manifest: `plugin.json` (Agent Plugins) and `.cursor-plugin/plugin.json` (Cursor). MCP: `mcp.json` (`type: streamable-http` at `https://figaeo.com/mcp`).

## First lookup

Ask Cursor: “Look up keywords example.com already ranks for in the United States, then suggest related ideas from the strongest terms.”

If remaining usage is $0, Cursor should call `create_checkout` (default $20, minimum $10). You confirm Stripe Checkout in the browser. Stripe Link is faster Checkout, not Agent payment. Taxes are added at Checkout. Then retry the same tool.

About 2,000 live SERPs (top 10) per $10. About 250 keyword-idea lookups per $10 at the default of 20 ideas. $20 is the recommended pack.

## Boundaries

FigAEO returns data. Cursor decides how to use it. No ranking guarantees.
