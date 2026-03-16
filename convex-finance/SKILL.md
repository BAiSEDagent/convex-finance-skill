---
name: convex-finance
description: "Use when an agent needs to understand or operate around Convex Finance: boosted Curve LP staking, cvxCRV, CVX rewards, Convex pool discovery, wallet position tracking, claimable reward checks, contract references, or APY comparisons across Convex, Curve, Frax, and f(x). Trigger on phrases like 'Convex Finance', 'Convex pools', 'boosted staking', 'cvxCRV', 'claimable CRV', 'CVX rewards', 'Convex APY', 'track my Convex position', or 'how does Convex work'."
---

# Convex Finance

Use this skill when the user is asking about the **Convex protocol itself**, not just the `convex-mcp` implementation.

## Scope

Use this skill for:
- Convex protocol mechanics
- boosted Curve LP staking
- CVX and cvxCRV reward flows
- Convex pool / position analysis
- contract references from official Convex docs
- deciding when to use Convex MCP vs protocol reasoning

Do **not** use this skill as the primary skill when the user is asking to:
- execute a transaction
- build or debug the MCP server itself
- deploy or audit Solidity code
- get guaranteed or current yield without a live data source

## What models commonly get wrong

- They confuse the Convex protocol with the `convex-mcp` analytics layer.
- They hallucinate current APY, current pool status, or current claimable rewards.
- They blur together the main Curve-centric Convex system with the Frax and f(x) surfaces.
- They present reward composition as fixed instead of variable.
- They guess contract addresses from memory instead of using official docs or verified sources.

Correct behavior:
- Use protocol reasoning for architecture, concepts, and docs-backed references.
- Use MCP or direct live reads for current wallet state, pool state, or moving yields.
- Keep Curve/main Convex, Frax/cvxFXS, and f(x)/cvxFXN clearly separated.
- Treat APY and rewards as moving estimates, not guarantees.
- Prefer official Convex docs for contract identity.

## Core mental model

Simple framing:
1. Users deposit supported LP tokens into Convex.
2. Convex handles the boosting path around those positions.
3. Users can earn boosted CRV, CVX, and sometimes extra incentive tokens.
4. Users do not need to directly manage veCRV to access that boosted exposure.

Related routes:
- deposit CRV -> receive `cvxCRV`
- stake `cvxCRV` -> earn platform fee share / rewards
- stake `CVX` -> earn platform fee exposure through `cvxCRV`

Start here unless the user asks for deeper contract-level mechanics.

## Surface distinctions

Keep these surfaces separate:
- **Curve / main Convex path:** boosted LP staking, CVX, cvxCRV, lockers, reward contracts
- **Frax path:** separate booster / voter / staking contracts around cvxFXS
- **f(x) path:** separate booster / voter / staking contracts around cvxFXN
- **MCP layer:** read-only analytics and workflow support, not execution

Default to the Curve-centric surface when the user says "Convex" with no extra detail.
If they mention FXS, cvxFXS, FXN, or cvxFXN, switch surfaces explicitly and load `references/contract-addresses.md`.

## Convex MCP vs direct protocol reasoning

Use Convex MCP when the user needs:
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
- strategy comparison without pretending to have live reads

If both are needed, explain the protocol first, then use MCP for current data.

## Verified facts to anchor on

- Convex is a reward-boosting layer around Curve-related liquidity systems.
- Users can deposit supported LP tokens to get boosted CRV exposure without directly managing veCRV.
- Reward composition is variable and may include CRV, CVX, and extra incentive tokens.
- `convex-mcp` is for live reads and analytics, not execution.
- Official Convex docs are the source of truth for contract identity.
- Pool and APY data are time-sensitive.

## Canonical mainnet references

Use these as the most common Ethereum mainnet references:
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

For wider tables and surface-specific addresses, read `references/contract-addresses.md`.
For operating guidance, read:
- `references/workflows.md`
- `references/failure-modes.md`
- `references/answer-patterns.md`

## Response rules

- Lead with the conclusion.
- Use plain English before raw JSON.
- Do not claim fixed yields.
- Do not imply this skill can execute transactions.
- Do not guess current APY, live rewards, or live pool status without a live data source.
- If the user asks what they should do, reframe into factual tradeoffs rather than financial advice.

## Sources

Primary references:
- `https://docs.convexfinance.com/convexfinance`
- `https://docs.convexfinance.com/convexfinance/faq/contract-addresses`
- `https://github.com/convex-eth/platform`
- `https://github.com/BAiSEDagent/convex-mcp`
