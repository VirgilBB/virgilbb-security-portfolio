# Security Research Portfolio — Virgil Bellini

Independent smart contract and web security researcher. Active across **Cantina**, **Code4rena**, **Immunefi**, and **HackerOne** since 2024.

---

## Stats

| Metric | Count |
|--------|-------|
| Total Submissions | 57+ |
| Findings Under Review | 7 |
| Confirmed / Accepted | In progress |
| Platforms | Cantina · Code4rena · Immunefi · HackerOne |
| Primary Languages | Solidity · Rust (CosmWasm) · Python |
| Focus Areas | DeFi (LST, lending, DEX) · Cross-chain · Web2 auth on Web3 infra |

---

## Active / Under Review

| ID | Protocol | Platform | Severity | Type | Status |
|----|----------|----------|----------|------|--------|
| sablier-001 | Sablier | Cantina | Critical | Merkle multichain replay — cross-chain replay after TTL expiry | Under Review |
| okx-001 | OKX DEX | Cantina | High | ETH commission referrer reentrancy via untrusted delegatecall | Under Review |
| okx-002 | OKX DEX | Cantina | High | Partial fork weight input token permanent lock | Under Review |
| lzstellar-002 | LayerZero Stellar | Code4rena | High | DVN UsedHash TTL persistent storage replay after 30-day window | Under Review |
| lzstellar-003 | LayerZero Stellar | Code4rena | High | EndpointV2 persistent TTL silently disabled via freeze_ttl_configs(None) | Under Review |
| renegade-001 | Renegade | Code4rena | High | u128 underflow in match_orders (Rust/CosmWasm) | Under Review |
| infinifi-002 | InfiFi | Cantina | Medium | Gateway pause DoS — operator cannot restore service | Under Review |

---

## Ready to Submit (§16 Gate Pass)

Findings that have cleared all internal quality gates and are pending platform submission.

| ID | Protocol | Platform | Severity | Summary |
|----|----------|----------|----------|---------|
| kinetiq-001 | Kinetiq | Cantina | High | closeRebalanceRequests triggers L1 redelegation before undelegation confirms — double-delegation ordering race |
| kinetiq-002 | Kinetiq | Cantina | High | executeEmergencyWithdrawal omits accounting update — exchange ratio permanently inflated |
| kinetiq-003 | Kinetiq | Cantina | High | cancelWithdrawal over-counts _cancelledWithdrawalAmount by bufferUsed — L1 over-delegation on redelegate |
| ventuals-004 | Ventuals | Cantina | Medium | Permissionless finalizeBatch — anyone can grief withdrawal queue with empty batches (24h DoS) |
| ventuals-005 | Ventuals | Cantina | Medium | applySlash(batchIndex, 0) permanently bricks protocol via totalHypeProcessed underflow |
| netscaler-002 | Citrix NetScaler | HackerOne | High | Session slot assigned before identity binding — cross-user session swap (CVE-2026-4368) |
| rujira-002 | Rujira Ghost Credit | Code4rena | High | BankMsg commits collateral before SubMsg vault repay — collateral orphaned on preference failure |

---

## Private Submissions (Anonymized — NDA/Pending Disclosure)

| Platform | Severity | Type |
|----------|----------|------|
| HackerOne | Critical | OAuth CSRF — missing state parameter allows account linking via social login (Web3 wallet auth flow) |
| HackerOne | Critical | Unauthenticated endpoint exposes OAuth client secrets and third-party API keys |
| HackerOne | Medium | Reflected XSS via unencoded redirect parameter in enterprise VPN gateway logout flow |
| Immunefi | High | Collateral liquidation logic error in DeFi lending protocol — borrower collateral silently orphaned |
| Cantina | High | Cross-chain bridge — attacker over-delegates validator funds via cancelled withdrawal accounting gap |
| Cantina | Critical | Merkle-based multichain airdrop replay via cross-chain TTL gap |
| Cantina | High | DEX reentrancy via untrusted delegatecall in referral commission path |

---

## Duplicate / Contested (Learning Log)

Independent discoveries later confirmed as known or co-discovered — evidence of coverage depth.

| Protocol | Severity | Outcome | Notes |
|----------|----------|---------|-------|
| LiFi Executor (×6) | High | Duplicate | 6 independent findings in the LiFi executor; all confirmed valid, co-discovered |
| Symbiotic (×5) | High/Med | Duplicate | 5 findings in the Symbiotic vault/slasher system, co-discovered during live contest |
| Kuru DEX | Critical | Duplicate | ETH locked in ERC20/ERC20 depositSingleSide — Critical, co-discovered |
| Doppler | Medium | Duplicate | tickAccumulator corruption in slot0 rebalance, co-discovered |
| Kiln | High | Duplicate | Withdrawer deadlock — dup of #50 (4 independent finders total) |
| Reserve Protocol | High | Duplicate | V3Oracle twapSeconds=0, co-discovered |

---

## Methodology

**Smart Contracts (Solidity)**
- Manual line-by-line review of state machines, accounting invariants, access control
- Focus on: cross-function ordering races, accounting gaps in LST/lending protocols, delegatecall attack surfaces, reentrancy via non-obvious callback paths

**Rust / CosmWasm**
- Message ordering analysis (BankMsg vs SubMsg execution model)
- u128 overflow/underflow in fixed-point arithmetic
- Reply handler error absorption patterns

**Web2 on Web3 Infrastructure**
- Auth flow analysis: OAuth state param, session token binding races
- API endpoint enumeration on Web3 company production infrastructure

**Pre-Submission Process**
- 6-block pre-validation: duplicate check across Cantina/C4/Sherlock public disclosures, audit PDF grep, reachability verification, TVL check
- §16 Final Gate: 10 grep-based passes on every report before submission

---

## Contact

- **GitHub**: [VirgilBB](https://github.com/VirgilBB)
- **Cantina**: cantina.xyz/u/virgilbb
- **Code4rena**: code4rena.com/@virgilbb
- **X / Twitter**: _(add handle)_
- **Telegram / Signal**: Available on request

---

*Last updated: 2026-04-05*
