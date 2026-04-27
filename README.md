# VirgilBB — Security Portfolio

Independent security researcher specializing in systemic infrastructure security, logic errors, and economic exploits. Active across **Cantina**, **Code4rena**, **Immunefi**, **HackerOne**, **HackenProof**, **Bugcrowd**, **Remedy**, and **Sherlock**.

---

## Stats

| Metric | Value |
|--------|-------|
| Total Findings Submitted | 100 |
| Duplicate Findings | 40 |
| Accepted (Pending Disclosure) | 2 |
| Under Review | 21 |
| Platforms | Cantina · Code4rena · Immunefi · HackerOne · HackenProof · Bugcrowd · Remedy · Sherlock |
| Specialties | Systemic Infrastructure Security · Logic Errors · Economic Exploits |
| Primary Languages | Solidity · Rust (CosmWasm) · Python |

---

## Accepted — Pending Disclosure

| Protocol | Platform | Severity | Status |
|----------|----------|----------|--------|
| Pending Disclosure | Cantina | High (×2) | 2 findings accepted. Cantina releases details once contest closes and patches are applied. |

---

## Selected Public Findings

### Duplicates

| Protocol | Severity | Finding |
|----------|----------|---------|
| LiFi Executor (×6) | High | Executor approval drain, arbitrary calldata, permissionless swap paths |
| Symbiotic (×5) | Critical/Med | Vault ACL front-run, BurnerRouter zero-address lock, onSlash access control, setResolver bypass, hook role enforcement |
| Kuru DEX | Critical | ETH permanently locked in ERC20/ERC20 `depositSingleSide` |
| Doppler | Medium | `tickAccumulator` corruption in slot0 rebalance (N-epoch amplified) |
| Kiln | High | Withdrawer revert deadlock |
| Revert Finance | Medium | `V3Oracle` `twapSeconds=0` allows instant TWAP manipulation |
| Berachain | High | Honey oracle staleness in basket mode |
| Midas (×2) | Medium | `redeemInstant` allowance overcounting; `RedemptionVaultWithBUIDL`/`USTB` replicate same overcounting bug |
| Pendle Boros | Medium | `agentExpiry` timestamp bug |
| USDai | Medium | `DepositTimelock.refundWithdrawAmount` misdirected to wrong recipient |
| Concrete | High | `cancelRequest` uses `msg.sender` instead of request owner, permanently locking shares |
| Reserve Protocol | High | `ImmutableTokenJar` permissionless drain of non-target tokens in permissionless mode |
| Redstone | Critical | `getUniqueSignersThreshold()==0` silently disables all signature verification (triager upgraded High→Critical before dup close) |
| OKX DEX (×2) | Critical | `DagRouter._MODE_BY_INVEST` drains router balance; `PMMAdaptor` unauthenticated calldata-tail payer drains adapter ERC-20 |
| PancakeSwap (×2) | High | `CL_INCREASE_FROM_DELTAS` fee theft; `CL_MINT_FROM_DELTAS` principal theft |
| BitGo eth-multisig-v2 | Critical | `tryInsertSequenceId` integer overflow permanently locks wallet |
| BitGo eth-multisig-v4 | High | Cross-function reentrancy in WalletSimple drains ETH and ERC-20 tokens simultaneously |
| Kinetiq (×2) | High | Withdrawer revert deadlock permanently locks ETH in FeeRecipient; `executeEmergencyWithdrawal` omits accounting updates, inflating exchange ratio |
| LiNEAR Protocol (×2) | Critical/High | `drain_withdraw` missing manager access control allows permissionless validator drain; unchecked subtraction in `validator_get_balance_callback` panics on validator slashing |
| Modular Account V2 | Critical | `AllowlistModule` hook passes native selectors, enabling session key to replace proxy implementation |
| OKG | High | EIP-712 Calls struct `wallet` field bound to implementation address instead of wallet address |

### Active / Under Review

| Protocol | Platform | Severity | Summary |
|----------|----------|----------|---------|
| Dynamic.xyz | HackerOne | Critical | OAuth CSRF via missing state parameter enables Google/GitHub account linking without user consent |
| Dynamic.xyz | HackerOne | Critical | Unauthenticated endpoint exposes OAuth client IDs, masked secrets, and third-party API keys |
| NetScaler | HackerOne | Medium | RelayState reflected without HTML-encoding in `/cgi/logout` enables session cookie theft via XSS |
| Sablier | Cantina | Critical | Merkle multichain replay: cross-chain replay after TTL expiry reactivates expired proofs |
| OKX DEX | Cantina | Medium | ETH commission referrer reentrancy via untrusted delegatecall in fee distribution path |
| OKX DEX | Cantina | Medium | Partial fork weight causes input token permanent lock when rebalance is incomplete |
| LayerZero Stellar | C4 | High | DVN `UsedHash` TTL persistent storage replay after 30-day expiry |
| LayerZero Stellar | C4 | High | Endpoint `freeze_ttl_configs(None)` silently disables TTL with no recovery path |
| Renegade | C4 | High | `u128` underflow in `match_orders` corrupts order book state |
| Chainlink PA V2 | C4 | High | `performUpkeep` accepts caller-supplied amount with no cap, allowing `AUCTION_WORKER_ROLE` to drain entire FeeAggregator balance |
| Chainlink PA V2 | C4 | High | `auctionCallback` executes unrestricted `Call[]` array, enabling approval injection to drain `assetIn` from AuctionBidder |

---

## Cerebro AI

Multi-chain infrastructure operator.

| Project | Description | Links |
|---------|-------------|-------|
| Cerebro AI | Platform source | [GitHub](https://github.com/VirgilBB/cerebro-host) |
| AGDP.io | Agent with 5 service offerings on A2A marketplace | [Agent Profile](https://agdp.io/agent/9386) |
| Moltbook | A2A social platform for agent-to-agent content sharing | [Profile](https://www.moltbook.com/u/cerebro-ai) |

---

## Production Systems

| Project | Role | Links |
|---------|------|-------|
| XPR Network | Block producer | [Mainnet](https://explorer.xprnetwork.org/account/cerebroai) · [Testnet](https://testnet.explorer.xprnetwork.org/account/cerebro) |
| Metal Blockchain | Validator | [Explorer](https://explorer.metalblockchain.org/validators/NodeID-HDdohvYFYmiQYN44aX9KC1pdg5hQTEeaU) |
| Akash Network | Validator | [Stats](https://stats.akash.network/validators/akashvaloper163zp6lyavlg7r2cru8djmv6d8qnpvlm0nsnr6s?network=mainnet) |
| Decred Network | VSP | [Live](https://dcr.cerebro.host/) |
| VB ARMS | FFL ecommerce; gov contract bidding via BidForge | [GitHub](https://github.com/VirgilBB/vb-arms/tree/main) |

---

## Akash Deployment Templates

Reproducible infrastructure templates deployed on Akash decentralized cloud.

| Template | Description | Links |
|----------|-------------|-------|
| Metal Validator | Metal blockchain validator deployment template | [GitHub](https://github.com/VirgilBB/Metal-Validator) |
| DCRPulse | Decred VSP deployment template | [GitHub](https://github.com/VirgilBB/dcrpulse) |

---

## Methodology

- 36-class vulnerability taxonomy covering DeFi, bridges, ZK circuits, governance, Web2 infrastructure, and emerging verticals
- Mandatory program intake gate — scope, prior audits, and eligibility verified before analysis begins
- Every finding validated with Foundry fork tests against live chain state (or platform-appropriate runnable PoC for non-EVM targets)
- Protocol-type routing to prioritize highest-impact bug classes per target
- Positive-exemplar anchoring — every report cross-referenced against a corpus of judge-selected $10K+ findings before submission
- 13-block pre-validation gate covering program status, duplicates, audit history, PoC gas/body validation, on-chain TVL, source reachability, governance preconditions, structural integrity (USD impact, fix recommendation, line refs, code blocks), and hidden-content scans (invisible Unicode + credential leaks)

---

## Contact

- **GitHub**: [VirgilBB](https://github.com/VirgilBB)
- **X**: [@VirgilBellini](https://x.com/VirgilBellini) · [@Cerebro_Agent](https://x.com/Cerebro_Agent)

---

*Last updated: 2026-04-27*
