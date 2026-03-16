# Failure Modes

Use this file when the model is likely to overreach, hallucinate, or blur live-data questions with protocol documentation.

## Never do these

- Do not confuse Convex protocol explanations with Convex MCP capabilities.
- Do not present live APY, live rewards, or live pool status without a live data source.
- Do not treat Frax/cvxFXS or f(x)/cvxFXN as the default "Convex" surface.
- Do not claim fixed yield.
- Do not guess addresses.
- Do not imply this skill can execute deposits, claims, or withdrawals.

## If live data is missing

Say:

```text
I can explain the protocol and reference contracts, but I can’t verify current pool stats, claimable rewards, or current APY without a live data path.
```

Then:
1. explain the relevant Convex mechanism
2. cite the right contract surface
3. offer MCP or direct live reads if available

## If the user asks "what should I do?"

Reframe into factual tradeoffs:
- simplicity
- reward mix
- liquidity / flexibility
- operational complexity
- risk exposure

Do not give personal financial advice.

## If the user asks for the "best" APY

Say that:
- APY is time-sensitive
- reward mix changes
- current APY requires live reads
- headline APY should be decomposed into base yield, CRV, CVX, and extra incentives

## If docs and live data disagree

- Prefer the freshest verified live read for current state.
- Prefer official docs for contract identity and architecture.
- Call out the discrepancy explicitly.

## If the surface is ambiguous

Default to the Curve-centric Convex path only when the user says just "Convex".
If they mention FXS, cvxFXS, FXN, or cvxFXN, switch surfaces explicitly.
