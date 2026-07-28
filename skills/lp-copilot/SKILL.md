---
name: lp-copilot
description: LP copilot for concentrated-liquidity positions — list a wallet's LP position NFTs on 7 chains for free, then buy deterministic analytics per call (range backtests, IL forecasts, position health, points-campaign EV, $0.05–$0.25 via x402). Use when the user asks about their liquidity positions, being in/out of range, impermanent loss, re-ranging, or points/airdrop farming EV.
---

# LP Copilot

Concentrated-liquidity tooling over the AirdropPulse x402 endpoints. Same local wallet and
spend caps as the PulseNetwork server (`~/.pulsepay` — fund once, both pay).

## Tools

| Tool | Cost | Purpose |
|---|---|---|
| `lp_positions` | FREE | Enumerate a wallet's v3-style position NFTs (Ethereum, Base, Arbitrum, Optimism, Polygon, BSC, Robinhood Chain/GigaDex) |
| `lp_catalog` | FREE | The paid endpoints: ids, prices, params |
| `lp_call` | $0.05–$0.25 | One analytics call by endpoint id |
| `lp_wallet` | FREE | Wallet address + USDC balance |
| `lp_guardrail` | FREE | Active spend caps |

## Mental model

`lp_positions` (whose positions, which chain) → `lp_catalog` → quote the price →
`lp_call` with the cheapest endpoint that answers. Positions staked in farming vaults are
owned by the vault and will NOT enumerate — query those by `token_id` via `position-health`
or `position-audit`.

## Recipes

**"Am I still in range?"** — `lp_positions {address, chain}` → for each position of
interest, `lp_call {endpoint: "position-health", params: {token_id, chain}}` ($0.05).

**"What range should I model?"** — `lp_call {endpoint: "range-model", params: {pool, chain}}`
($0.25) returns a backtested scenario table (time-in-range and fee capture per candidate
width). Present it as scenarios — it is decision support, never a recommendation.

**"Is this points campaign worth farming?"** — `lp_call {endpoint: "pool-ev"}` ($0.15) for
points-per-$1k-TVL by pool, `campaign-status` ($0.05) for the campaign clock.

## Rules

- Results are backtested/simulated scenario tables and observed facts. Relay them as data;
  never convert them into "you should" instructions.
- If a call is blocked by a spend guardrail, stop and tell the user — do not retry or
  route around it. Caps are raised only by the user editing `~/.pulsepay/config.json`.
- This server never signs or submits on-chain transactions — it cannot move positions.
