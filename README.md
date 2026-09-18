# Fig for Cursor

First-time setup for agents: fetch https://figaeo.com/llms.txt (optional https://figaeo.com/install.md). The bundle contains Fig MCP plus six specialist SEO/AEO skills. Start with `fig-seo-aeo`, then call on `fig-site-audit`, `fig-search-research`, `fig-answer-research`, `fig-content-strategy`, and `fig-content-validation` as needed.

Install the Fig plugin, or add a remote MCP server, then ask in chat.

- URL: `https://figaeo.com/mcp`
- Transport: Streamable HTTP
- Auth: complete MCP OAuth 2.1 in the connect card with GitHub or Google

## Plugin

Manifest: `plugin.json` (Agent Plugins) and `.cursor-plugin/plugin.json` (Cursor). MCP: `mcp.json` (`type: streamable-http` at `https://figaeo.com/mcp`). There is no `.mcp.json` in this package.

Cursor Marketplace: this repo’s `.cursor-plugin/marketplace.json` points at `packages/cursor`. Until the listing is live, Settings → MCP → Add remote server, or install this plugin locally, then complete OAuth.

## First lookup

Ask Cursor: “Look up keywords acmeauth.dev already ranks for in the United States, then suggest related ideas from the strongest terms.”

If remaining usage is $0, Cursor should call `create_checkout` (default $20, minimum $10). Your agent starts Checkout and gives a short figaeo.com/pay link. Pay on your own computer. On Grok, Stripe Link can complete payment after you connect Link. Never paste a checkout.stripe.com hash URL into chat. Taxes are added at Checkout. Then retry the same tool.

About 2,000 live SERPs (top 10) per $10. About 250 keyword-idea lookups per $10 at the default of 20 ideas.

$20 is the recommended pack: about 4,000 live SERPs (top 10) or about 500 keyword-idea lookups (20 ideas each)—enough to research, act on, and recheck one website for about four weeks. Call create_checkout() with no amount to buy $20; minimum is $10. Deeper SERPs and site: queries cost more.

A typical website can use about 20 idea lookups and about 120 SERPs per two weeks (about 30 keywords, 3 snapshots). A $20 pack leaves substantial room for research, changes, and validation.

## Boundaries

Cursor uses Fig’s live research and specialist skills to improve the website in the same workspace.
