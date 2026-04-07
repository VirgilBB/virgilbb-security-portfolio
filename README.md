# Security Research Portfolio — Virgil Bellini

Independent smart contract and web security researcher. Active across **Cantina**, **Code4rena**, **Immunefi**, and **HackerOne** since 2024.

---

## Stats

| Metric | Count |
|--------|-------|
| Total Submissions | 65+ |
| Findings Under Review | 11 |
| Platforms | Cantina · Code4rena · Immunefi · HackerOne |
| Primary Languages | Solidity · Rust (CosmWasm) · Python |
| Focus Areas | DeFi (LST, lending, DEX) · Cross-chain · Web2 auth on Web3 infra |

---

## Duplicates

| Protocol | Severity | Finding |
|----------|----------|---------|
| LiFi Executor (×6) | High | Executor approval drain, arbitrary calldata, permissionless swap paths |
| Symbiotic (×5) | High/Med | Vault ACL front-run, BurnerRouter zero-address lock, onSlash access control, setResolver bypass, hook role enforcement |
| Kuru DEX | Critical | ETH permanently locked in ERC20/ERC20 `depositSingleSide` |
| Doppler | Medium | `tickAccumulator` corruption in slot0 rebalance (N-epoch amplified) |
| Kiln | High | Withdrawer revert deadlock |
| Revert Finance | Medium | `V3Oracle` `twapSeconds=0` allows instant TWAP manipulation |
| Berachain | High | Honey oracle staleness in basket mode — stale price accepted silently |
| Midas (×2) | Medium | `redeemInstant` allowance overcounting; `RedemptionVaultWithBUIDL`/`RedemptionVaultWithUSTB` replicate same overcounting bug |
| Boros | Medium | `agentExpiry` timestamp bug |
| USDai | Medium | `DepositTimelock.refundWithdrawAmount` misdirected to wrong recipient |
| Concrete | High | `cancelRequest` uses `msg.sender` instead of request owner, permanently locking shares |
| Reserve Protocol | High | `ImmutableTokenJar` permissionless drain of non-target tokens in permissionless mode |
| Redstone (×2) | Critical/High | `getUniqueSignersThreshold()==0` disables all signature verification; `pickMedian()` integer overflow enables permanent oracle DoS |
| OKX DEX (×2) | Critical | `DagRouter._MODE_BY_INVEST` drains router balance; `PMMAdaptor` unauthenticated calldata-tail payer drains adapter ERC-20 |
| Pendle | High | `PYLpOracle` zero-duration TWAP manipulation |
| PancakeSwap (×2) | High | `CL_INCREASE_FROM_DELTAS` fee theft; `CL_MINT_FROM_DELTAS` principal theft |

---

## Active / Under Review

| Protocol | Platform | Severity | Summary |
|----------|----------|----------|---------|
| Dynamic.xyz | HackerOne | Critical | OAuth CSRF via missing state parameter enables Google/GitHub account linking without user consent |
| Dynamic.xyz | HackerOne | Critical | Unauthenticated endpoint exposes OAuth client IDs, masked secrets, and third-party API keys |
| NetScaler | HackerOne | High | Cross-user session swap via race condition in Gateway/AAA session binding |
| NetScaler | HackerOne | Medium | RelayState reflected without HTML-encoding in `/cgi/logout` enables session cookie theft via XSS |
| Sablier | Cantina | Critical | Merkle multichain replay: cross-chain replay after TTL expiry reactivates expired proofs |
| OKX DEX | Cantina | Medium | ETH commission referrer reentrancy via untrusted delegatecall in fee distribution path |
| OKX DEX | Cantina | Medium | Partial fork weight causes input token permanent lock when rebalance is incomplete |

| Injective Peggy | C4 | High | `submitBatch` fee reverts brick the bridge when fee token transfer fails |
| Injective Peggy | C4 | High | `updateValset` reward revert permanently locks validator set updates |
| LayerZero Stellar | C4 | High | DVN `UsedHash` TTL persistent storage replay after 30-day expiry |
| LayerZero Stellar | C4 | High | Endpoint `freeze_ttl_configs(None)` silently disables TTL with no recovery path |
| Renegade | C4 | High | `u128` underflow in `match_orders` corrupts order book state |

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

---

## Contact

- **GitHub**: [VirgilBB](https://github.com/VirgilBB)
- **X**: [@VirgilBellini](https://x.com/VirgilBellini) · [@Cerebro_Agent](https://x.com/Cerebro_Agent)

---

*Last updated: 2026-04-07*
