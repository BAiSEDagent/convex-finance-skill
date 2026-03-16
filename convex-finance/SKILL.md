---
name: convex-finance
description: Use when an agent needs to understand or operate around Convex Finance: boosted Curve LP staking, cvxCRV, CVX rewards, Convex pool discovery, wallet position tracking, claimable reward checks, Convex contract references, or APY comparisons across Convex, Curve, Frax, and f(x). Trigger on phrases like 'Convex Finance', 'Convex pools', 'boosted staking', 'cvxCRV', 'claimable CRV', 'CVX rewards', 'Convex APY', 'track my Convex position', or 'how does Convex work'.
---

# Convex Finance

Use this skill when the user is asking about the **Convex protocol itself**, not just the `convex-mcp` implementation.

Use this skill for:
- boosted staking on top of Curve
- CVX and cvxCRV reward flows
- pool discovery and position analysis
- protocol-level stats and contract references
- when to use Convex MCP vs direct onchain inspection

Do **not** use this skill as the primary skill when the user is really asking to:
- execute a transaction
- build or debug the MCP server itself
- deploy a smart contract
- do a full Solidity security audit

In those cases, route to the transaction-capable integration, MCP-builder flow, or Ethereum security/audit workflow instead.

## Core mental model

Convex sits on top of Curve and related ecosystems to make reward boosting easier.

Simple framing:
1. A user deposits supported LP tokens into Convex.
2. Convex stakes those LP tokens through its boost machinery.
3. The user earns boosted CRV plus CVX, and sometimes extra incentive tokens.
4. The user does not need to directly manage veCRV to access boosted rewards.

Related paths:
- Deposit CRV -> receive `cvxCRV`
- Stake `cvxCRV` -> earn platform fees / rewards
- Stake `CVX` -> earn platform fee share in `cvxCRV`

Use this framing first unless the user asks for deeper contract mechanics.

## When to use Convex MCP vs direct protocol reasoning

Use a Convex MCP server when the user needs:
- live pool lists
- wallet position data
- claimable reward checks
- APY projections
- protocol summary stats

Use direct protocol reasoning plus official docs when the user needs:
- conceptual explanations
- contract references
- architecture understanding
- docs-backed answers about Convex, Curve, Frax, or f(x)
- high-level strategy comparisons

If both are needed, explain the protocol first, then use the MCP for live data.

## Recommended answer patterns

### 1. User asks: what is Convex
Answer in one paragraph:
- Convex simplifies Curve reward boosting
- LPs can earn boosted CRV without managing veCRV themselves
- Users may also earn CVX and extra incentives
- Convex also has staking routes around cvxCRV and CVX

### 2. User asks: should I use Convex or Curve directly
Compare on these axes:
- simplicity
- boost management burden
- reward composition
- liquidity / withdrawal flexibility
- strategic exposure to CVX or cvxCRV

Do not give financial advice. Explain tradeoffs.

### 3. User asks about a wallet or pool
1. Use MCP if available.
2. If MCP is not available, fall back to direct onchain inspection.
3. Report staked amount, reward components, and whether the pool appears active or shutdown.

### 4. User asks for APY comparison
Break APY into:
- base yield
- CRV rewards
- CVX rewards
- extra incentives if present

Make it explicit that APY is time-sensitive and not guaranteed.

## Protocol surface map

Keep these surfaces distinct:
- **Curve / main Convex path:** boosted LP staking, CVX, cvxCRV, lockers, reward contracts
- **Frax path:** separate booster / voter / staking contracts around cvxFXS
- **f(x) path:** separate booster / voter / staking contracts around cvxFXN
- **MCP layer:** read-only analytics and workflow support, not execution

If the user says "Convex" without more detail, assume they mean the main Curve-centric flow first.
If they mention FXS, cvxFXS, FXN, or cvxFXN, load the wider address table in `references/contract-addresses.md` and answer against that surface specifically.

## Canonical protocol facts

Use official Convex docs and verified contract sources for these references.

Ethereum mainnet addresses commonly needed:
- Booster: `0xF403C135812408BFbE8713b5A23a04b3D48AAE31`
- Booster Owner: `0x3cE6408F923326f81A7D7929952947748180f1E6`
- Voter Proxy: `0x989AEb4d175e16225E39E87d0D97A3360524AD80`
- Multisig: `0xa3C5A1e09150B75ff251c1a7815A07182c3de2FB`
- CVX: `0x4e3FBD56CD56c3e72c1403e103b45Db9da5B9D2B`
- cvxCRV: `0x62B9c7356A2Dc64a1969e19C23e4f579F9810Aa7`
- CRV Depositor: `0x8014595F2AB54cD7c604B00E9fb932176fDc86Ae`
- CVX Rewards: `0xCF50b810E57Ac33B91dCF525C6ddd9881B139332`
- cvxCRV Rewards: `0x3Fe65692bfCD0e6CF84cB1E7d24108E434A7587e`
- Pool Manager: `0x782BcE229a8b603c99161e867A49D5426da37f95`
- Claim Zap v3: `0x3f29cB4111CbdA8081642DA1f75B3c12DECf2516`
- CVX Locker: `0x72a19342e8F1838460eBFCCEf09F6585e32db86E`

Read `references/contract-addresses.md` when you need a wider address table across Curve mainnet, Frax, f(x), Arbitrum, or Polygon.

For execution-critical or production-facing answers, recommend quick verification before acting:
- confirm the address against official Convex docs
- confirm the block explorer page is verified
- if available, confirm a simple read such as `symbol()`, `owner()`, or `poolLength()` matches expectations

## Workflow references

Read `references/workflows.md` when the user needs any of these:
- enumerate Convex pools
- inspect a wallet position
- compare Convex APY to alternatives
- explain cvxCRV / CVX staking routes
- create monitoring or reporting around Convex stats
- use Convex MCP in a structured way

## Response style

- Lead with the conclusion.
- Use plain English before raw JSON.
- Keep the protocol explanation tight.
- Mention uncertainty when yields or stats are moving.
- Distinguish clearly between:
  - protocol facts
  - live MCP data
  - estimates / projections

Good pattern:

```text
Convex is the simpler route if you want boosted Curve exposure without managing veCRV yourself.

In practice:
- deposit supported LP tokens
- earn boosted CRV + CVX
- sometimes receive extra incentive tokens
- withdraw without the user having to run a separate veCRV strategy
```

## Safety and correctness

- Do not claim yields are fixed.
- Do not imply this skill can execute transactions.
- Do not hallucinate unsupported pools or reward tokens.
- Prefer official docs, verified contracts, and live MCP data over memory.
- Surface shutdown status and risk caveats when discussing pools.
- If the user asks for execution, hand off to the relevant transaction-capable tool or integration instead of pretending this skill can do it.

## Failure modes and how to respond

### MCP data missing or stale
- Say the live data path is unavailable or may be stale.
- Fall back to protocol explanation and contract references.
- Do not invent pool stats.

### User does not know the pool id
- Start from pool discovery.
- If MCP is unavailable, ask for the LP token or strategy name instead of guessing.

### User asks for best yield or what they should do
- Do not give financial advice.
- Reframe into factual comparison: simplicity, reward mix, liquidity, and execution risk.

### Docs and live data disagree
- Prefer the freshest verified live read for current state.
- Prefer official docs for contract identity and architecture.
- Call out the discrepancy explicitly.

## Sources

Primary references:
- `https://docs.convexfinance.com/convexfinance`
- `https://docs.convexfinance.com/convexfinance/faq/contract-addresses`
- `https://github.com/convex-eth/platform`
- `https://github.com/BAiSEDagent/convex-mcp`
