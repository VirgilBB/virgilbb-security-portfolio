# Security Research Portfolio — Virgil Bellini

Independent smart contract and web security researcher. Active across **Cantina**, **Code4rena**, **Immunefi**, and **HackerOne** since 2024.

---

## Stats

| Metric | Count |
|--------|-------|
| Total Submissions | 57+ |
| Findings Under Review | 7 |
| Independent Duplicate Discoveries | 19 (across 10 protocols) |
| Confirmed / Accepted | In progress |
| Platforms | Cantina · Code4rena · Immunefi · HackerOne |
| Primary Languages | Solidity · Rust (CosmWasm) · Python |
| Focus Areas | DeFi (LST, lending, DEX) · Cross-chain · Web2 auth on Web3 infra |

---

## Active / Under Review — Cantina

> Full reports pending official Cantina publication. Summaries reflect the submitted finding.

| Protocol | Severity | Summary | Status |
|----------|----------|---------|--------|
| Sablier | Critical | Merkle multichain replay — cross-chain replay after TTL expiry reactivates expired proofs | Under Review — pending official publication |
| OKX DEX | High | ETH commission referrer reentrancy via untrusted delegatecall in fee distribution path | Under Review — pending official publication |
| OKX DEX | High | Partial fork weight causes input token permanent lock when rebalance is incomplete | Under Review — pending official publication |
| InfiFi | Medium | Gateway pause DoS — operator cannot restore service after emergency pause sequence | Under Review — pending official publication |

---

## Ready to Submit

Findings that have cleared all internal quality gates (§16 gate pass) and are pending platform submission.

| Protocol | Platform | Severity | Summary |
|----------|----------|----------|---------|
| Kinetiq | Cantina | High | `closeRebalanceRequests` triggers L1 redelegation before undelegation confirms — double-delegation ordering race on Hyperliquid |
| Kinetiq | Cantina | High | `executeEmergencyWithdrawal` omits accounting update — exchange ratio permanently inflated |
| Kinetiq | Cantina | High | `cancelWithdrawal` over-counts `_cancelledWithdrawalAmount` by `bufferUsed` — L1 over-delegation on redelegate |
| Ventuals | Cantina | Medium | Permissionless `finalizeBatch` — any address can grief withdrawal queue with empty batches, resetting 24h timer indefinitely |
| Ventuals | Cantina | Medium | `applySlash(batchIndex, 0)` permanently bricks protocol via `totalHypeProcessed` underflow — no on-chain recovery |
| Citrix NetScaler | HackerOne | High | Session slot assigned before identity binding completes — cross-user session swap (CVE-2026-4368) |
| Rujira Ghost Credit | Code4rena | High | `BankMsg` commits collateral before `SubMsg` vault repay — collateral orphaned when preference step fails |

---

## Private Submissions (Anonymized — NDA / Pending Disclosure)

| Platform | Severity | Type |
|----------|----------|------|
| HackerOne | Critical | OAuth CSRF — missing `state` parameter allows session linking via Google/GitHub social login on Web3 auth platform |
| HackerOne | Critical | Unauthenticated endpoint exposes OAuth client secrets and third-party API keys in production |
| HackerOne | Medium | Reflected XSS via unencoded redirect parameter in enterprise VPN gateway logout flow |
| Immunefi | High | Collateral liquidation logic error in DeFi lending protocol — borrower collateral silently orphaned on failed repay |
| Cantina | High | Cancelled withdrawal accounting gap — attacker over-delegates validator funds on L1 (Hyperliquid LST) |
| Cantina | Critical | Merkle-based multichain airdrop replay via cross-chain TTL gap |
| Cantina | High | DEX reentrancy via untrusted delegatecall in referral commission distribution path |

---

## Duplicate / Contested (Learning Log)

**19 independent duplicate discoveries across 10 protocols.** Every finding here was valid and confirmed — co-discovered with other researchers. This is direct evidence of finding real bugs, not noise.

| Protocol | Severity | Finding | Notes |
|----------|----------|---------|-------|
| LiFi Executor (×6) | High | Executor approval drain, arbitrary calldata, permissionless swap paths | All 6 confirmed valid — co-discovered across live Cantina contest |
| Symbiotic (×5) | High/Med | Vault ACL front-run, BurnerRouter zero-address lock, onSlash access control, setResolver bypass, hook role enforcement | Co-discovered in Symbiotic vault/slasher system |
| Kuru DEX | Critical | ETH permanently locked in ERC20/ERC20 `depositSingleSide` | Critical severity, co-discovered |
| Doppler | Medium | `tickAccumulator` corruption in slot0 rebalance (N-epoch amplified) | Co-discovered, dup of #162 |
| Kiln | High | Withdrawer revert deadlock — 4 independent finders (dup of #50) | Co-discovered |
| Revert Finance | Medium | `V3Oracle` `twapSeconds=0` allows instant TWAP manipulation | Co-discovered |
| Berachain | High | Honey oracle staleness in basket mode — stale price accepted silently | Immunefi, co-discovered |
| Midas | Medium | `redeemInstant` allowance overcounting blocks legitimate user redemptions | Co-discovered |
| Boros | Medium | `agentExpiry` timestamp bug (originally submitted as High, downgraded) | Co-discovered |
| USDai | Medium | `DepositTimelock.refundWithdrawAmount` misdirected to wrong recipient | Co-discovered — dispute filed on severity |

---

## Methodology

**Smart Contracts (Solidity)**
- Manual review of state machines, accounting invariants, access control, and cross-function ordering
- Focus: ordering races in LST protocols, accounting gaps in lending/withdrawal flows, delegatecall attack surfaces, reentrancy via non-obvious callback paths

**Rust / CosmWasm**
- Message ordering analysis (BankMsg vs SubMsg execution model, `reply_always` error absorption)
- u128 overflow/underflow in fixed-point arithmetic
- Cross-contract reply handler silent failure patterns

**Web2 on Web3 Infrastructure**
- OAuth flow analysis: missing `state` param, session token binding races
- API endpoint enumeration on Web3 production infrastructure
- CVE-mapped findings against vendor-provided test instances

**Pre-Submission Process**
- 6-block pre-validation: duplicate check across Cantina/C4/Sherlock public disclosures, audit PDF grep (all known audit reports), reachability verification, TVL check
- §16 Final Gate: 10 grep-based passes before every submission — em-dash check, placeholder check, single-fix enforcement, TVL documentation, C4/H1/Cantina template compliance

---

## Contact

- **GitHub**: [VirgilBB](https://github.com/VirgilBB)
- **X**: [@VirgilBellini](https://x.com/VirgilBellini) · [@Cerebro_Agent](https://x.com/Cerebro_Agent)
- **Cantina**: cantina.xyz/u/virgilbb
- **Code4rena**: code4rena.com/@virgilbb

---

*Last updated: 2026-04-05*
