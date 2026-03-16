# Convex Finance Skill

Standalone agent skill for **Convex Finance**.

This repo is for agents that need to understand and work with the Convex protocol: boosted Curve LP staking, cvxCRV, CVX rewards, pool discovery, position tracking, APY comparison, and protocol contract references.

## Repo layout

```text
convex-finance-skill/
├── README.md
├── convex-finance/
│   ├── SKILL.md
│   └── references/
│       ├── answer-patterns.md
│       ├── contract-addresses.md
│       ├── failure-modes.md
│       └── workflows.md
└── evals/
    └── convex-finance.yaml
```

## What the skill covers

- Convex protocol mental model
- protocol-vs-MCP boundary
- main Convex vs Frax vs f(x) surface distinctions
- curated contract references from official Convex docs
- operational answer patterns and failure modes
- evals for targeted factual uplift

## Install

Use the `convex-finance/` folder as the skill folder.

## Evals

The repo includes `evals/convex-finance.yaml` with prompt, expected facts, and fail conditions modeled after EthSkills-style evaluation.

## Sources

- Convex docs: https://docs.convexfinance.com/convexfinance
- Contract addresses: https://docs.convexfinance.com/convexfinance/faq/contract-addresses
- Protocol repo: https://github.com/convex-eth/platform
