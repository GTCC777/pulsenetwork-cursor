---
name: pulsenetwork-status
description: Report the PulseNetwork wallet status — address, USDC balance, spend caps, and recent spending. Use when the user asks about their agent wallet, balance, funding, or what the agent has spent.
---

# Wallet status report

1. `pulse_balance` — address + Base USDC balance.
2. `pulse_guardrail` — per-call cap, daily cap, spent in last 24h, config file location.
3. `pulse_report {days: 7}` — calls and USD by vertical.
4. Summarize in 3–4 lines. If the balance is 0, include the address and note it needs
   USDC **on Base** (not Ethereum mainnet, not Solana) to enable paid calls.
