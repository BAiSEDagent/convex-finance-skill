# Contract Addresses

Use this file when the user needs exact protocol references, contract lookups, or ecosystem expansion beyond the basic Ethereum mainnet set in `SKILL.md`.

Primary source:
- https://docs.convexfinance.com/convexfinance/faq/contract-addresses

Last reviewed against official docs and source repos: 2026-03-16
Verification method standard: official Convex docs first, then verified block explorer page, then lightweight read checks where available.

## Rules

- Treat this file as a curated reference, not an exhaustive registry.
- For execution-critical answers, tell the agent to re-check official Convex docs and a verified block explorer page before acting.
- If there is any discrepancy between memory and docs, prefer official Convex docs for contract identity.

## Main Convex / Curve-centric Ethereum surface

- Booster: `0xF403C135812408BFbE8713b5A23a04b3D48AAE31`
- Booster Owner: `0x3cE6408F923326f81A7D7929952947748180f1E6`
- Voter Proxy: `0x989AEb4d175e16225E39E87d0D97A3360524AD80`
- Multisig: `0xa3C5A1e09150B75ff251c1a7815A07182c3de2FB`
- Deployer: `0x947B7742C403f20e5FaCcDAc5E092C943E7D0277`
- CVX: `0x4e3FBD56CD56c3e72c1403e103b45Db9da5B9D2B`
- cvxCRV: `0x62B9c7356A2Dc64a1969e19C23e4f579F9810Aa7`
- CRV Depositor: `0x8014595F2AB54cD7c604B00E9fb932176fDc86Ae`
- Reward Factory: `0xEdCCB35798fae4925718A43cc608aE136208aa8D`
- Token Factory: `0x3c995e43E6ddD551E226F4c5544C77BfeD147aB9`
- Stash Factory: `0x877288c4e6EbA4f635bA7428706447353B47De75`
- CVX Rewards: `0xCF50b810E57Ac33B91dCF525C6ddd9881B139332`
- cvxCRV Rewards: `0x3Fe65692bfCD0e6CF84cB1E7d24108E434A7587e`
- Pool Manager: `0x782BcE229a8b603c99161e867A49D5426da37f95`
- Claim Zap v3: `0x3f29cB4111CbdA8081642DA1f75B3c12DECf2516`
- CVX Locker (current vlCVX): `0x72a19342e8F1838460eBFCCEf09F6585e32db86E`
- CVX Locker (old vlCVX): `0xD18140b4B819b895A3dba5442F959fA44994AF50`
- Pool Utilities: `0x5Fba69a794F395184b5760DAf1134028608e5Cd1`

## Surface distinction rules

- If the user says "Convex" with no extra context, start with the Curve-centric surface.
- If the user mentions FXS, cvxFXS, FXN, or cvxFXN, explicitly switch to the Frax or f(x) surface.
- Never answer with an address from the wrong surface.

## Curve Arbitrum

- VoteProxy: `0x989AEb4d175e16225E39E87d0D97A3360524AD80`
- Booster: `0xF403C135812408BFbE8713b5A23a04b3D48AAE31`
- Reward Hook: `0xEdCCB35798fae4925718A43cc608aE136208aa8D`
- Reward Manager: `0x972794eBd4B3bbA8A185202f899F8F7664519Bd7`
- Reward Factory: `0x8014595F2AB54cD7c604B00E9fb932176fDc86Ae`
- Cvx Incentives: `0x665D4Bea98e3a1849526553453E8369B448C6AD4`
- Fee Deposit: `0xE7CdD5ed586A095e395f2007449721eA2a5B878a`
- Pool Utilities: `0xB20e684dE561C54021651050F4518dAa1976eB42`
- Pool Manager: `0x98ECe0d8aBd1f96672a497D3053999Df172FaA8b`

## Curve Polygon

- Vote Proxy: `0x989AEb4d175e16225E39E87d0D97A3360524AD80`
- Booster: `0xF403C135812408BFbE8713b5A23a04b3D48AAE31`
- Reward Hook: `0xEdCCB35798fae4925718A43cc608aE136208aa8D`
- Reward Manager: `0x3c995e43E6ddD551E226F4c5544C77BfeD147aB9`
- Reward Factory: `0xCF50b810E57Ac33B91dCF525C6ddd9881B139332`
- Cvx Incentives: `0xA46944D0845F786117D0e1034fC10585747C861b`
- Fee Deposit: `0x665D4Bea98e3a1849526553453E8369B448C6AD4`
- Pool Utilities: `0x25E12482a25CF36EC70fDA2A09C1ED077Fc21616`
- Pool Manager: `0xFC0A2FfDea23804494aA1707741E5A6Eaa2f8017`

## Frax surface

- Booster: `0xA2cF21b157b2f203e37b616b619f438B5aa86Ee5`
- Voter Proxy: `0x59CFCD384746ec3035299D90782Be065e466800B`
- cvxFXS: `0xFEEf77d3f69374f66429C91d732A244f074bdf74`
- fxsDepositor: `0x8f55d7c21bDFf1A51AFAa60f3De7590222A3181e`
- cvxFXS Staking: `0x49b4d1dF40442f0C31b1BbAEA3EDE7c38e37E31a`
- Pool Registry: `0x41a5881c17185383e19Df6FA4EC158a6F4851A69`
- Pool Utilities: `0xFCB28d032e422aE3710C1Ad74338cBB40B0749CF`
- Fee Deposit: `0x7A527d8bB09f7D70C148aB5DE919e9BF68a0d769`

## f(x) surface

- Voter Proxy: `0xd11a4Ee017cA0BECA8FA45fF2abFe9C6267b7881`
- Booster: `0xAffe966B27ba3E4Ebb8A0eC124C7b7019CC762f8`
- cvxFXN: `0x183395DbD0B5e93323a7286D1973150697FFFCB3`
- FxnDepositor: `0x56B3c8eF8A095f8637B6A84942aA898326B82b91`
- cvxFXN Staking: `0xEC60Cd4a5866fb3B0DD317A46d3B474a24e06beF`
- Burner: `0x0f6E12F0Be8487c35E063Ec0E03903367C421e94`
- Fee Deposit: `0x8133F7D5CD1A1E184228C373F5bEFa98Fa01395D`

## Prisma surface (historical / inactive)

Treat this section as legacy reference material. Prisma governance confirmed shutdown and transition to Resupply after the exploit period, so do not present this as an active default Convex surface.
Reference context: `Prisma Shutdown & Transition Plan` from Resupply / PIP-46 transition communications.

- VoteProxy: `0x8ad7a9e2B3Cd9214f36Cb871336d8ab34DdFdD5b`
- cvxPrisma: `0x34635280737b5BFe6c7DC2FC3065D60d66e78185`
- Depositor: `0x61404F7c2d8b1F3373eb3c6e8C4b8d8332c2D5B8`
- Burner: `0xCFC7B36fA3B59CA963a44c86c2C369bC311896E5`
- Booster: `0x79a50f83E7AFf970CeAB5152a15461A4f1c3799E`
- cvxPrisma Staking: `0x0c73f1cFd5C9dFc150C8707Aa47Acbd14F0BE108`
- Staking Fee Receiver Booster: `0xaF92400476cd81C7379bB54fD2646E8fa476Cf3F`
- Staking Fee Receiver Platform: `0x3C716E88AE0fcc5D78bd11810CA451941e2eFe6A`
- Fee Deposit Booster: `0x4B33E944E4Ae1Cb58ABfED5a16a4E25b041Fb5d5`
- Fee Deposit Platform: `0xe91861cB57C6C2AA55B7AB0E6853ae1D96b63EFA`
- Receiver Vault: `0xb20b384C2F958f2100E14C5048922613F937674A`
- Fee Claimer Booster: `0x394bfb7e6A6E7197BBA16C8dC5f581de8A1847b6`
- Fee Claimer Platform: `0x2F30ef614C4B10C32437864EfE57B6D8ED4b9Ba8`
- Boost Delegate: `0x806d47Df9141FdE4A77e1e54F0ca4184526ADe60`
- Utility: `0x3fc264C5154D16c0eB765F6dd12A55Bdc18F7951`
- Vesting Claim: `0x7e2Ca1134dC44B5D368575Da316d87ac9B9065E7`
- Drop Minter Vecrv: `0x8864187b257e0fB3BD74054b72D9c1834e76d712`
- Drop Minter Points: `0x9c4d60fA85088d40e3D8030dba283E9708EC9292`
- Treasury Manager: `0xBb48c21E9101A85EE6D00B4F1A7B946dF1B09EA7`
- Treasury Manager Prisma: `0xD60cd4AD7A2D6bF4eC9fccbCAeec769b52726dfd`

## Verification checklist

Before giving an address for anything important:
1. Match the contract name against official Convex docs.
2. Confirm the explorer page is verified if possible.
3. Optionally confirm a lightweight read such as `symbol()`, `owner()`, or `poolLength()`.
