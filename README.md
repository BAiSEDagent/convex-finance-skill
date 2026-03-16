# Convex Finance Skill

Anthropic-style agent skill for **Convex Finance**.

This repo is a standalone skill package for agents that need to understand and work with the Convex protocol: boosted Curve LP staking, cvxCRV, CVX rewards, pool discovery, position tracking, APY comparison, and protocol contract references.

## Repo layout

```text
convex-finance-skill/
├── README.md
└── convex-finance/
    ├── SKILL.md
    └── references/
        ├── contract-addresses.md
        └── workflows.md
```

## What the skill covers

- What Convex is and how it fits around Curve / Frax / f(x)
- When an agent should route to this skill
- Core protocol mental model
- Read-only analytical workflows
- Canonical contract references from official Convex docs
- Guidance for agents using a Convex MCP server or direct onchain reads

## Install

Use the `convex-finance/` folder as the skill folder.

## Sources

- Convex docs: https://docs.convexfinance.com/convexfinance
- Contract addresses: https://docs.convexfinance.com/convexfinance/faq/contract-addresses
- Protocol repo: https://github.com/convex-eth/platform
- Convex MCP repo: https://github.com/BAiSEDagent/convex-mcp
