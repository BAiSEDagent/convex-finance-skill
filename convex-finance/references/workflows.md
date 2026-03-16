# Workflows

Use this file when the user needs concrete process guidance around Convex usage, analysis, or tooling.

## Quick trigger examples

This reference is useful for prompts like:
- "What is Convex and why do people use it?"
- "Check my Convex position"
- "Compare Convex vs Curve"
- "What rewards do I earn from cvxCRV?"
- "Is this Convex pool still active?"
- "Estimate APY for 10k in Convex"

## Workflow: explain Convex to a new user

Goal: answer in one paragraph with no jargon overload.

Required facts:
- Convex sits on top of Curve and related reward systems.
- Users deposit supported LP tokens.
- Convex handles reward boosting mechanics.
- Users can earn boosted CRV, CVX, and sometimes extra incentives.
- Users do not need to manage veCRV directly.

Avoid:
- claiming rewards are guaranteed
- overexplaining locker mechanics unless asked
- mixing in MCP details unless the user asks for live data

Short version:

```text
Convex is a reward-boosting layer around Curve and related ecosystems. It lets LPs access boosted rewards and additional incentive flows without having to actively manage veCRV themselves.
```

## Workflow: compare Convex vs Curve direct

Frame the answer across:
- simplicity
- control
- reward composition
- boost-management burden
- liquidity / flexibility
- exposure to CVX / cvxCRV
- fee structure and who captures protocol revenue

Required disclaimer:
- this is a factual tradeoff comparison, not financial advice

Important context:
- for Curve LPs on Convex, official docs currently describe a 17% fee on CRV revenue
- that fee is split across cvxCRV stakers, CVX stakers, treasury, and the harvest caller
- do not compare gross Curve rewards to net Convex rewards without mentioning this

Good summary pattern:

```text
Curve direct gives you more raw control, but Convex is usually the simpler route if you want boosted rewards without running your own veCRV strategy.
```

## Workflow: analyze a wallet or pool

Preferred order:
1. Use MCP for live wallet data if available.
2. If MCP is unavailable, say so clearly.
3. Fall back to protocol explanation and contract references.
4. Never invent claimable balances or APY.

Return shape:
- pool / strategy
- staked amount
- reward components
- pool status
- any uncertainty or stale-data caveat

Suggested answer shape:

```text
Your Convex position:
- Staked: ...
- Claimable CRV: ...
- Claimable CVX: ...
- Estimated claimable value: ...
- Pool status: active / shutdown
```

## Workflow: answer APY questions

Always decompose projected return into:
- base yield
- CRV rewards
- CVX rewards
- extra incentives

Always say:
- APY is time-sensitive
- reward mix can change
- headline APY is an estimate, not a promise

Good phrasing:

```text
The headline APY is useful, but the more important question is what drives it. In Convex, that usually means base pool yield plus CRV emissions plus CVX emissions, all of which can move over time.
```

## Workflow: protocol reporting

For dashboards or periodic reporting, emphasize:
- TVL
- protocol revenue
- treasury value
- emissions metrics
- CVX / cvxCRV price context if available

Keep reports concise:

```text
Convex snapshot:
- TVL: ...
- 14d emissions controlled: ...
- platform revenue: ...
- treasury: ...
```

## Workflow: vlCVX vote-locking loop

Use this when the user asks about long-term Convex participation, vlCVX, gauge voting, or bribe markets.

Core loop:
1. Lock `CVX` into the current vlCVX locker.
2. Receive vote-locked governance power (`vlCVX`).
3. Use that voting power on the biweekly cadence to influence gauge weights.
4. Earn fee exposure and potentially external vote incentives / bribes through systems like Votium or Hidden Hand.

Required facts:
- vlCVX is a governance / coordination surface, not just a passive staking product.
- The locker address changed historically; use the current locker, not the old one.
- Bribe and vote markets are part of the Convex power-user loop.

Avoid:
- implying bribes are guaranteed
- implying voting cadence is arbitrary
- confusing CVX staking with vlCVX locking

Good summary pattern:

```text
The Convex power-user loop is: lock CVX for vlCVX, use that voting power on the recurring gauge-weight cycle, and capture protocol fee exposure plus any external vote incentives if you participate in the bribe markets.
```

## Workflow: use direct protocol references safely

When the user asks for contracts, addresses, or architecture:
1. Start from official Convex docs.
2. Use `contract-addresses.md`.
3. If the answer is execution-critical, recommend re-verification against a block explorer.
4. Avoid guessing if an address is uncertain.
