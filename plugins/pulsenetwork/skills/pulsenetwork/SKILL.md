---
name: pulsenetwork
description: Use PulseNetwork — 900+ pay-per-call intelligence APIs (finance, crypto, health, law, travel, climate, safety) with a local agent wallet. Discover for free, pay per call in USDC on Base via x402. Use when the user asks for live data, checks, or intelligence that a paid API could answer.
---

# PulseNetwork

PulseNetwork is a fleet of 74 intelligence verticals (~900 endpoints) paid per call via
x402 micropayments — no accounts or API keys. The MCP server manages a local wallet and
enforces spend caps in code.

## Tools

| Tool | Cost | Purpose |
|---|---|---|
| `pulse_discover` | FREE | Keyword search over the catalog: returns endpoints with price, params, description |
| `pulse_call` | endpoint price | Call an endpoint (params as strings); pays automatically |
| `pulse_balance` | FREE | Wallet address + Base USDC balance |
| `pulse_report` | FREE | What this wallet spent recently |
| `pulse_guardrail` | FREE | Active spend caps |

## Mental model

`pulse_discover` → pick the cheapest endpoint that answers → quote price to user →
`pulse_call`. Never call without discovering first: the catalog gives you the exact param
names and examples.

## Recipes

**Answer a data question**
1. `pulse_discover {query: "flight compensation"}`
2. Pick the best hit (price + params are in the result).
3. `pulse_call {vertical: "travelpulse", path: "/api/rights/check", params: {from: "FRA", to: "JFK", delay_hours: "5", ...}}`

**First-run setup (wallet empty)**
1. `pulse_balance` → if USDC is 0, show the user the address and ask them to send a few
   dollars of USDC **on Base**. A dollar buys 20–100 calls.

**Weekly spend check**
1. `pulse_report {days: 7}` and `pulse_guardrail` → summarize total, by vertical, and caps.

## Catalog highlights (all discoverable via pulse_discover)

- **Crypto/onchain**: token safety scans, wallet snapshots, RWA data, stablecoin health,
  options greeks, DEX pairs
- **Finance/macro**: FX (ECB), commodities, filings/8-K, fund 13F checks, layoffs
- **Consumer protection**: flight/transit compensation checks, product recalls (CPSC+EU),
  merchant trust scores, wage/insurance/council-tax/subscription rights checks
- **Health/clinical**: clinical trials, drug interactions, nutrition, longevity
- **World**: climate, geopolitics, immigration points, grants, government spending

Prices are mostly $0.01–$0.25; letter-drafting products run $2–$5 (these exceed the
default $0.50 per-call cap by design — the user must raise the cap to buy them).
