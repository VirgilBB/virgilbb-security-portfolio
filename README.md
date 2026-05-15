# VirgilBB (Cerebro) — Security Portfolio

Independent researcher specializing in systemic infrastructure security, logic errors, and economic exploits. Active across **Cantina**, **Code4rena**, **HackerOne**, **HackenProof**, **Bugcrowd**, **Remedy**, **Sherlock**, and **Immunefi**.

---

## Stats

| Metric                        | Value                                                                                   |
| ----------------------------- | --------------------------------------------------------------------------------------- |
| Total Findings Submitted      | 107 |
| Duplicate Findings            | 45 |
| Critical Duplicates           | 8                                                                                       |
| High Duplicates               | 19                                                                                      |
| Accepted (Pending Disclosure) | 2                                                                                       |
| Under Review                  | 15 |
| Platforms                     | Cantina · Code4rena · HackerOne · HackenProof · Bugcrowd · Remedy · Sherlock · Immunefi |
| Specialties                   | Systemic Infrastructure Security · Logic Errors · Economic Exploits                     |
| Primary Languages             | Solidity · Rust (CosmWasm) · Python · Move · Cairo · Anchor · TS/JS                     |

---

## Accepted — Pending Disclosure

| Protocol           | Platform | Severity  | Status                                                 |
| ------------------ | -------- | --------- | ------------------------------------------------------ |
| Pending Disclosure | Cantina  | High (×2) | 2 accepted findings. Currently undisclosed on Cantina. |

---

## Selected Public Findings

### Duplicates

| #   | Protocol              | Severity | Finding                                                                                                                                           |
| --- | --------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Kuru DEX              | Critical | ETH permanently locked in ERC20/ERC20 `depositSingleSide`                                                                                         |
| 2   | Redstone              | Critical | `getUniqueSignersThreshold()==0` silently disables all signature verification (triager upgraded High→Critical before dup close)                   |
| 3   | OKX DEX (×2)          | Critical | `DagRouter._MODE_BY_INVEST` drains router balance; `PMMAdaptor` unauthenticated calldata-tail payer drains adapter ERC-20                         |
| 4   | BitGo eth-multisig-v2 | Critical | `tryInsertSequenceId` integer overflow permanently locks wallet                                                                                   |
| 5   | LiNEAR Protocol       | Critical | `drain_withdraw` missing manager access control allows permissionless validator drain                                                             |
| 6   | Modular Account V2    | Critical | `AllowlistModule` hook passes native selectors, enabling session key to replace proxy implementation                                              |
| 7   | Symbiotic             | Critical | Vault ACL front-run enables malicious delegator installation at initialization                                                                    |
| 8   | UFarm                 | Critical | `highWaterMark` unit mismatch — premature performance fee extraction                                                                              |
| 9   | Autopool              | Critical | `getFloorCeilingPrice` LP oracle dimensional error — 6,680× overvaluation on Curve V2 pool                                                        |
| 10  | LiFi Executor (×3)    | High     | No-ACL arbitrary calldata drain via `swapAndCompleteBridgeTokens`; missing `ReentrancyGuard`; `ReceiverOIF` stranded principal                    |
| 11  | PancakeSwap (×2)      | High     | `CL_INCREASE_FROM_DELTAS` fee theft; `CL_MINT_FROM_DELTAS` principal theft                                                                        |
| 12  | Berachain             | High     | Honey oracle staleness in basket mode                                                                                                             |
| 13  | Kinetiq (×2)          | High     | Withdrawer revert deadlock permanently locks ETH in FeeRecipient; `executeEmergencyWithdrawal` omits accounting updates, inflating exchange ratio |
| 14  | Reserve Protocol      | High     | `ImmutableTokenJar` permissionless drain of non-target tokens in permissionless mode                                                             |
| 15  | BitGo eth-multisig-v4 | High     | Cross-function reentrancy in WalletSimple drains ETH and ERC-20 tokens simultaneously                                                             |
| 16  | LiNEAR Protocol       | High     | Unchecked subtraction in `validator_get_balance_callback` panics on validator slashing                                                            |
| 17  | Midas                 | High     | `redeemInstant` allowance overcounting — double-spend via repeated partial redeems                                                                |
| 18  | Concrete              | High     | `cancelRequest` uses `msg.sender` instead of request owner, permanently locking shares                                                            |
| 19  | Blockdaemon ARC       | High     | `--arc.hide-pending-txs` does not sanitize `eth_getBlockByNumber("pending")` in JSON-RPC batch requests                                           |
| 20  | NEAR Intents Bridges  | High     | Replay guard removal in `fin_transfer_send_tokens_callback` enables EVM→NEAR proof reuse                                                          |

| autofinance-1 | Critical | Division-by-zero in AutopoolDebt.totalAssetsTimeChecked freezes Autopool after full destination exit + 24h stale |
| ventuals-4 | High | Permissionless finalizeBatch Enables Zero-Cost Griefing Attack That Delays All Withdrawals by One Full Cycle |

## Active / Under Review

| #  | Protocol               | Platform    | Severity |
| -- | ---------------------- | ----------- | -------- |
| 1  | SafeSwap               | HackenProof | Critical |
| 2  | Tokemak Autopilot / auto.finance | Remedy      | Critical |
| 3  | Magic Labs             | Bugcrowd    | Critical |
| 4  | Renegade               | C4          | High |
| 5  | Rujira                 | C4          | High |
| 6  | SafeSwap               | HackenProof | High |
| 7  | XRPL April 2026        | Sherlock    | High |
| 8  | K2                     | C4          | High |
| 9  | SafeSwap               | HackenProof | High |
| 10 | Asphere                | HackenProof | High |
| 11 | BOB                    | Remedy      | High |
| 12 | K2                     | C4          | Medium |
| 13 | reserve-governor       | Cantina     | Medium |
| 14 | Backblaze              | Bugcrowd    | Medium |
| 15 | Ventuals               | Cantina     | Medium |
| 16 | Ventuals               | Cantina     | Medium |
| 17 | Aztec Network Bug Bounty | Cantina     | Medium |
| 18 | BigONE                 | HackenProof | Low |

---

## Methodology

| Phase / Component          | Process & Validation Details                                                                                                                                                                                                                                                                                           |
| :------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Taxonomy & Scope**       | 36-class vulnerability taxonomy covering DeFi, bridges, ZK circuits, governance, Web2 infrastructure, and emerging verticals.                                                                                                                                                                                          |
| **Program Intake**         | Mandatory gate verifying scope, prior audits, and eligibility before analysis begins.                                                                                                                                                                                                                                  |
| **Proof of Concept**       | Every finding validated with Foundry fork tests or Tenderly live-state simulation against mainnet (platform-appropriate runnable PoC for non-EVM targets).                                                                                                                                                             |
| **Attack Surface Routing** | Protocol-type routing prioritizes highest-impact bug classes per target.                                                                                                                                                                                                                                               |
| **Quality Benchmarking**   | Positive-exemplar anchoring—every report cross-referenced against a corpus of judge-selected $10K+ findings before submission.                                                                                                                                                                                         |
| **Automated QA Gate**      | **Two-stage validation:**  <br>1. **Phase 2.6 Sweep:** 9-check structural analysis (placeholders, path purge, headers, duplicates, PoC completeness).  <br>2. **8-Block Preflight:** Program status, on-chain TVL, source reachability, governance preconditions, and hidden-content scans (Unicode/credential leaks). |
| **Adversarial Review**     | **G9 Process:** Critical and High findings evaluated by an isolated hostile-triager sub-agent (context-isolated) to prevent confirmation bias.                                                                                                                                                                         |

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

| Project          | Role                                             | Links                                                                                                                             |
| ---------------- | ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| XPR Network      | Block producer                                   | [Mainnet](https://explorer.xprnetwork.org/account/cerebroai) · [Testnet](https://testnet.explorer.xprnetwork.org/account/cerebro) |
| Metal Blockchain | Validator                                        | [Explorer](https://explorer.metalblockchain.org/validators/NodeID-HDdohvYFYmiQYN44aX9KC1pdg5hQTEeaU)                              |
| Akash Network    | Validator                                        | [Stats](https://stats.akash.network/validators/akashvaloper163zp6lyavlg7r2cru8djmv6d8qnpvlm0nsnr6s?network=mainnet)               |
| Decred Network   | VSP - Virtual Service Provider                   | [Live](https://dcr.cerebro.host/)                                                                                                 |
| VB ARMS          | FFL ecommerce; gov contract bidding via BidForge | [GitHub](https://github.com/VirgilBB/vb-arms/tree/main)                                                                           |

---

## Akash Deployment Templates

Reproducible infrastructure templates deployed on Akash decentralized cloud.

| Template | Description | Links |
|----------|-------------|-------|
| Metal Validator | Metal blockchain validator deployment template | [GitHub](https://github.com/VirgilBB/Metal-Validator) |
| DCRPulse | Decred VSP deployment template | [GitHub](https://github.com/VirgilBB/dcrpulse) |

---

## Contact

- **GitHub**: [VirgilBB](https://github.com/VirgilBB)
- **X**: [@VirgilBellini](https://x.com/VirgilBellini) · [@Cerebro_Agent](https://x.com/Cerebro_Agent)

---

*Last updated: 2026-05-15*

