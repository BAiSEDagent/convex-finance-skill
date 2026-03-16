# Workflows

Use this file when the user needs concrete process guidance around Convex usage, analysis, or tooling.

## Quick trigger examples

This reference is especially useful for prompts like:
- "What is Convex and why do people use it?"
- "Check my Convex position"
- "Compare Convex vs Curve"
- "What rewards do I earn from cvxCRV?"
- "Is this Convex pool still active?"
- "Estimate APY for 10k in Convex"

## 1. Explain Convex quickly

Use this structure:
1. Convex simplifies boosted Curve participation.
2. Users deposit supported LP tokens into Convex.
3. Convex routes staking through its boost system.
4. Users earn boosted CRV, CVX, and sometimes extra incentives.
5. Users avoid directly managing veCRV for that boosted exposure.

Short version:

```text
Convex is a reward-boosting layer around Curve and related ecosystems. It lets LPs access boosted rewards and additional incentive flows without having to actively manage veCRV themselves.
```

## 2. Compare Convex vs Curve directly

Compare on:
- simplicity
- boost management complexity
- reward composition
- exposure to CVX / cvxCRV
- flexibility and withdrawal behavior

Good summary pattern:

```text
Curve direct gives you more raw control, but Convex is usually the simpler route if you want boosted rewards without running your own veCRV strategy.
```

## 3. Analyze a user position with Convex MCP

If a Convex MCP server is available:
1. Identify the wallet address.
2. Identify the pool id if known.
3. If pool id is unknown, start with pool discovery.
4. Fetch position data.
5. Return:
   - staked amount
   - estimated USD value
   - earned CRV
   - earned CVX
   - claimable value
   - whether the pool appears active or shutdown

Suggested answer shape:

```text
Your Convex position:
- Staked: ...
- Claimable CRV: ...
- Claimable CVX: ...
- Estimated claimable value: ...
- Pool status: active / shutdown
```

## 4. Compare APY

When a user asks whether a pool looks attractive:
1. Get the target pool.
2. Break projected return into:
   - base yield
   - CRV rewards
   - CVX rewards
   - extra incentives if available
3. Explain what is structural vs variable.
4. State clearly that APY is a moving estimate.

Good phrasing:

```text
The headline APY is useful, but the more important question is what drives it. In Convex, that usually means base pool yield plus CRV emissions plus CVX emissions, all of which can move over time.
```

## 5. Protocol reporting

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

## 6. Use direct protocol references safely

When the user asks for contracts, addresses, or architecture:
1. Start from official Convex docs.
2. Use the contract-addresses reference.
3. If the answer is execution-critical, recommend re-verification against a block explorer.
4. Avoid guessing if an address is uncertain.

## 7. When not to overreach

Do not pretend this skill can:
- deposit to Convex
- claim rewards
- withdraw funds
- sign transactions
- guarantee yield outcomes

If the user asks for execution, route to the correct transaction-capable system or say that this skill is analytical / guidance-only.
