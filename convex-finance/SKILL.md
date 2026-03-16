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

## Known stale beliefs to correct

- Convex is not just a generic "Curve booster"; it has multiple protocol surfaces and token routes.
- MCP is not the protocol. MCP is only a live-data / analytics path.
- Current APY and current claimable rewards are not static facts.
- Reward composition must be decomposed, not flattened into one headline number.
- Addresses should come from official docs or verified explorers, not memory.
- Prisma should not be treated as an active default surface; governance confirmed shutdown and transition to Resupply, so it is legacy context.

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

Curve Wars context:
- Convex became strategically important because pooled vote power can influence Curve emissions.
- That made `vlCVX`, gauge voting, and external bribe markets core to the protocol’s power-user loop.
- When explaining why Convex matters beyond simple yield boosting, this governance layer is the answer.

Start here unless the user asks for deeper contract-level mechanics.

## Surface distinctions

Keep these surfaces separate:
- **Curve / main Convex path:** boosted LP staking, CVX, cvxCRV, lockers, reward contracts
- **Frax path:** separate booster / voter / staking contracts around cvxFXS
- **f(x) path:** separate booster / voter / staking contracts around cvxFXN
- **Prisma path (historical / inactive):** separate booster / depositor / staking and fee receiver contracts around `cvxPrisma`, but treat this surface as legacy context after the Prisma shutdown
- **MCP layer:** read-only analytics and workflow support, not execution

Default to the Curve-centric surface when the user says "Convex" with no extra detail.
If they mention FXS, cvxFXS, FXN, or cvxFXN, switch surfaces explicitly and load `references/contract-addresses.md`.
If they mention Prisma or cvxPrisma, frame it as historical / inactive context unless they explicitly ask about legacy contracts or post-mortem details.

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

## Task routing table

| Task | Primary path |
|---|---|
| Explain what Convex is | `SKILL.md` core mental model |
| Current APY / rewards / pool state | Convex MCP or direct live reads |
| Contract lookup | `references/contract-addresses.md` |
| Convex vs Curve comparison | `references/workflows.md` + `references/answer-patterns.md` |
| Ambiguous / stale live-data case | `references/failure-modes.md` |
| Frax / f(x) / cvxFXS / cvxFXN question | `references/contract-addresses.md` surface split |

## Verified facts to anchor on

- Convex is a reward-boosting layer around Curve-related liquidity systems.
- Users can deposit supported LP tokens to get boosted CRV exposure without directly managing veCRV.
- Reward composition is variable and may include CRV, CVX, and extra incentive tokens.
- `convex-mcp` is for live reads and analytics, not execution.
- Official Convex docs are the source of truth for contract identity.
- Pool and APY data are time-sensitive.

## Fee structure facts that matter

Use these for protocol comparisons and yield explanations.

### Curve fee split
Official docs currently describe a **17% fee on CRV revenue** from Curve LPs on Convex:
- 10% to `cvxCRV` stakers, paid as CRV
- 4.5% to `CVX` stakers, paid as cvxCRV
- 2% to treasury, paid as CRV
- 0.5% to the harvest caller, paid as CRV

Important: these fees are taken from **CRV revenue**, not all incentive tokens.

### Frax fee split
Official docs currently describe a **20% fee on FXS revenue**:
- 10% to `cvxFXS` LPs / stakers as FXS
- 5% to `vlCVX` holders as FXS
- 5% to treasury

### f(x) fee split
Official docs currently describe:
- 75% of veFXN revenue to `cvxFXN` stakers
- 25% of veFXN revenue to treasury
- plus a 17% fee on boosted LP revenue split 8.5% / 8.5% between `cvxFXN` stakers and treasury

If the user asks for exact current economics, say these parameters can change within protocol limits and should be checked against current docs.

## EthSkills dependencies worth loading

This skill composes well with:
- `https://ethskills.com/building-blocks/SKILL.md` for DeFi context and Curve-adjacent primitives
- `https://ethskills.com/addresses/SKILL.md` for broader address verification patterns
- `https://ethskills.com/concepts/SKILL.md` for mechanism and incentive framing

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

## Never say this

- Never present a live APY as fact without a live data source.
- Never say the skill itself can deposit, claim, or withdraw.
- Never answer a Frax or f(x) question using the default Curve-centric surface.
- Never give an execution-critical address without a verification caveat.
- Never flatten reward composition into one guaranteed number.

## Sources

Primary references:
- `https://docs.convexfinance.com/convexfinance`
- `https://docs.convexfinance.com/convexfinance/faq/contract-addresses`
- `https://github.com/convex-eth/platform`
