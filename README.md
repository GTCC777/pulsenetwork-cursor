# PulseNetwork for Cursor

**Give your Cursor agent a wallet and 900+ pay-per-call intelligence APIs.**

One install adds:

- **MCP server** (`@pulsenetwork/mcp` via npx): `pulse_discover` (free catalog search),
  `pulse_call` (paid, USDC on Base via x402), `pulse_balance`, `pulse_report`,
  `pulse_guardrail`
- **Zero-config wallet**: generated on first use (standard BIP-39, imports into
  MetaMask), stored locally at `~/.pulsepay/` — fund it with a few dollars of USDC on
  Base and paid calls just work

> **No wallet? No problem.** [PulseNetwork Intel on MCPize](https://mcpize.com/mcp/pulsenetwork-intel)
> offers our 8 most-bought tools (token safety, macro, geopolitical) as a hosted MCP server
> with a free tier and plain monthly subscription — no crypto required.
- **Spend safety**: $0.50/call and $5/day caps enforced *in code, below the model* — the
  agent has no tool to raise them; only you can, by editing `~/.pulsepay/config.json`.
  The wallet only ever pays PulseNetwork hosts.
- **Skills + always-on spend-safety rule** teaching the agent to discover first, quote
  prices, and never route around a guardrail block

## What's in the catalog

74 verticals, ~900 endpoints, mostly $0.01–$0.25 per call: token safety scans, flight
compensation checks, product recalls, merchant trust scores, clinical trials, FX and
macro data, filings, layoffs, climate, immigration, grants, government spending, and more.
Full catalog: https://pulse.theaslangroupllc.com/.well-known/pulse-catalog.json

## Try it

> "Is this token safe? 0x… on Base"

> "Would a 5-hour delayed FRA→JFK flight qualify for EU261 compensation?"

> "Any EU recalls for baby teethers this year?"

MIT © The Aslan Group LLC
