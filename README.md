# VirgilBB (Cerebro) — Security Portfolio

Independent researcher specializing in systemic infrastructure security, logic errors, and economic exploits. Active across **Cantina**, **Code4rena**, **HackerOne**, **HackenProof**, **Bugcrowd**, **Remedy**, **Sherlock**, and **Immunefi**.

---

## Stats

| Metric                        | Value                                                                                   |
| ----------------------------- | --------------------------------------------------------------------------------------- |
| Total Findings Submitted      | 104                                                                                     |
| Duplicate Findings            | 41                                                                                      |
| Critical Duplicates           | 8                                                                                       |
| High Duplicates               | 18                                                                                      |
| Accepted (Pending Disclosure) | 2                                                                                       |
| Under Review                  | 22                                                                                      |
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

| Protocol | Severity | Finding |
|----------|----------|---------|
| Kuru DEX | Critical | ETH permanently locked in ERC20/ERC20 `depositSingleSide` |
| Redstone | Critical | `getUniqueSignersThreshold()==0` silently disables all signature verification (triager upgraded High→Critical before dup close) |
| OKX DEX (×2) | Critical | `DagRouter._MODE_BY_INVEST` drains router balance; `PMMAdaptor` unauthenticated calldata-tail payer drains adapter ERC-20 |
| BitGo eth-multisig-v2 | Critical | `tryInsertSequenceId` integer overflow permanently locks wallet |
| LiNEAR Protocol | Critical | `drain_withdraw` missing manager access control allows permissionless validator drain |
| Modular Account V2 | Critical | `AllowlistModule` hook passes native selectors, enabling session key to replace proxy implementation |
| Symbiotic | Critical | Vault ACL front-run enables malicious delegator installation at initialization |
| UFarm | Critical | `highWaterMark` unit mismatch — premature performance fee extraction |
| Autopool | Critical | `getFloorCeilingPrice` LP oracle dimensional error — 6,680× overvaluation on Curve V2 pool |
| LiFi Executor (×3) | High | No-ACL arbitrary calldata drain via `swapAndCompleteBridgeTokens`; missing `ReentrancyGuard`; `ReceiverOIF` stranded principal |
| PancakeSwap (×2) | High | `CL_INCREASE_FROM_DELTAS` fee theft; `CL_MINT_FROM_DELTAS` principal theft |
| Berachain | High | Honey oracle staleness in basket mode |
| Kinetiq (×2) | High | Withdrawer revert deadlock permanently locks ETH in FeeRecipient; `executeEmergencyWithdrawal` omits accounting updates, inflating exchange ratio |
| Reserve Protocol | High | `ImmutableTokenJar` permissionless drain of non-target tokens in permissionless mode |
| BitGo eth-multisig-v4 | High | Cross-function reentrancy in WalletSimple drains ETH and ERC-20 tokens simultaneously |
| LiNEAR Protocol | High | Unchecked subtraction in `validator_get_balance_callback` panics on validator slashing |
| Midas | High | `redeemInstant` allowance overcounting — double-spend via repeated partial redeems |
| Concrete | High | `cancelRequest` uses `msg.sender` instead of request owner, permanently locking shares |
| Blockdaemon ARC | High | `--arc.hide-pending-txs` does not sanitize `eth_getBlockByNumber("pending")` in JSON-RPC batch requests |
| NEAR Intents Bridges | High | Replay guard removal in `fin_transfer_send_tokens_callback` enables EVM→NEAR proof reuse |
| Boba Network | High | `failedNativeDisbursements` keyed by `depositId` only — cross-chain collision permanently freezes failed native disbursements |
| OKG | High | EIP-712 `Calls` struct `wallet` field bound to implementation address instead of wallet address |
| NetScaler | High | Session slot race — cross-user session swap (CVE-2026-4368) |

## Active / Under Review

| Protocol              | Platform    | Severity |
| --------------------- | ----------- | -------- |
| SafeSwap              | HackenProof | Critical |
| Tokemak / auto.finance| Remedy      | Critical |
| Magic Labs            | Bugcrowd    | Critical |
| Renegade              | C4          | High     |
| Rujira                | C4          | High     |
| SafeSwap              | HackenProof | High     |
| SafeSwap              | HackenProof | High     |
| XRPL                  | Sherlock    | High     |
| K2 Finance            | C4          | High     |
| Asphere               | HackenProof | High     |
| BOB                   | Remedy      | High     |
| OKX DEX               | Cantina     | Medium   |
| OKX DEX               | Cantina     | Medium   |
| K2 Finance            | C4          | Medium   |
| Reserve Governor      | Cantina     | Medium   |
| Backblaze             | Bugcrowd    | Medium   |
| Immutable             | Bugcrowd    | Medium   |
| Ventuals              | Cantina     | Medium   |
| Ventuals              | Cantina     | Medium   |
| Reserve               | Cantina     | Low      |
| Reserve               | Cantina     | Low      |
| BigONE                | HackenProof | Low      |

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

*Last updated: 2026-05-03*

