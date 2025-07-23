---
title: Week in Ethereum News
description: This is a post on My Blog about agile frameworks.
date: 2025-07-11
---
* The [All Core Devs - Consensus (ACDC) #160 call](https://github.com/ethereum/pm/issues/1598) on July 10 focused on Fusaka upgrade progress, with discussions on the launch of fusaka-devnet-3 and preparations for the Glamsterdam upgrade. Key decisions included finalizing BPO (Blob Parameter Override) strategies and selecting a CL headliner for Glamsterdam.

## Eth R&D Protocol Call(s)

* [All Core Devs - Consensus (ACDC) #160, July 10 2025](https://ethereum-magicians.org/t/24771):
  * Fusaka upgrade:
    * fusaka-devnet-2 status was reviewed, with most clients showing stable performance
    * fusaka-devnet-3 specifications were finalized, targeting a July 7 launch date
    * The devnet will test all validator custody features, including data column sidecars by root and distributed blob building
    * Developers agreed to move forward with engine_getBlobsV2 changes, rolling back to V2 behavior that prohibits partial responses
  * Glamsterdam upgrade:
    * Mark from Lighthouse proposed [EIP-7732 (Enshrined Proposer Builder Separation)](https://blog.sigmaprime.io/glamsterdam-headliner.html) as the CL headliner
    * Discussion focused on selecting one CL headliner, with EIP-7732 gaining support for its slot restructuring approach
    * Developers discussed the tradeoffs between EIP-7732 and competing proposals like EIP-7782 (reducing block latency)
  * Client updates:
    * CL clients are being updated with new gas limit values
    * Several clients have implemented validator custody features, with Teku supporting backfill while Lighthouse, Prysm, and Grandine support without backfill

## Fusaka (Osaka + Fulu) upgrade

* [Fusaka-devnet-3 specifications](https://notes.ethereum.org/@ethpandaops/fusaka-devnet-3) were finalized, with the devnet launching on July 7, 2025. This devnet will test all validator custody features and represents the final testing environment before spec freeze.
* The EIP list for fusaka-devnet-3 includes several important updates:
  * [EIP-7594: PeerDAS - Peer Data Availability Sampling](https://github.com/ethereum/EIPs/blob/ed447a1105230659fdce084710ae36bc309ff99f/EIPS/eip-7594.md) with validator custody testing
  * [EIP-7825: Transaction Gas Limit Cap](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-7825.md) to prevent excessive gas usage in single transactions
  * [EIP-7939: Count leading zeros (CLZ) opcode](https://eips.ethereum.org/EIPS/eip-7939) with updated gas cost from 3 to 5
  * [EIP-7907: Meter Contract Code Size And Increase Limit](https://eips.ethereum.org/EIPS/eip-7907) with formula fixes and adjustments for large contracts
* Developers agreed on a BPO (Blob Parameter Override) strategy for the mainnet rollout, starting with conservative blob limits and gradually increasing based on real-world performance data.

## Glamsterdam (Amsterdam–G-Star) Upgrade

* Mark Mackey from Lighthouse published a [detailed proposal](https://blog.sigmaprime.io/glamsterdam-headliner.html) advocating for [EIP-7732: Enshrined Proposer Builder Separation](https://eips.ethereum.org/EIPS/eip-7732) as the Glamsterdam headliner.
* The proposal compares EIP-7732 against competing proposals:
  * EIP-7732 (Enshrined Proposer Builder Separation) offers slot restructuring with payload-block separation
  * EIP-7886 (Delayed Execution) provides an alternative slot restructuring approach
  * EIP-7782 (Reduce Block Latency) would shorten slots from 12 to 6 seconds
  * EIP-7805 (Fork-choice Enforced Inclusion Lists) focuses on censorship resistance
* The analysis argues that EIP-7732 better supports Ethereum's strategic initiatives for scaling L1, scaling L2, and improving UX, while also providing a cleaner separation between consensus and execution layers.
* A decision on the CL headliner is expected at the July 24 ACDC meeting, with developers emphasizing that only one headliner per layer will be selected.

## Layer 1

* [Partial History Expiry (PHE)](https://etherworld.co/2025/07/08/ethereum-clients-roll-out-partial-history-expiry/) has been rolled out across major Ethereum clients including Geth, Besu, and Nethermind, allowing nodes to prune historical state data while maintaining recent history.
* The [engine_getBlobsV2 API](https://github.com/ethereum/execution-apis/pull/671) behavior is being modified to prohibit partial responses, with a new [engine_getBlobsV3](https://github.com/ethereum/execution-apis/pull/674) proposed to support partial returns in the future.
* A new [eth/v2/builder/blinded_blocks API](https://github.com/ethereum/builder-specs/pull/123) has been proposed that would not return the execution payload and blobs, supporting more efficient block propagation.
* Developers are working on optimizing bandwidth usage for blob propagation, with significant differences observed between clients: Lighthouse and Grandine use ~20 Mbps while Prysm, Teku, and Lodestar average over 80-100 Mbps.

## Research

* [Privacy-Preserving Sybil Resistance](https://ethresear.ch/t/privacy-preserving-sybil-resistance-via-mpc-tls-and-semaphore-proofs/22722): A new approach combining MPC-TLS and Semaphore proofs was proposed to enable privacy-preserving Sybil resistance mechanisms, allowing users to prove uniqueness without revealing personal information.
* [Faster Block/Blob Propagation](https://ethresear.ch/t/faster-block-blob-propagation-in-ethereum/21370): Ongoing research into optimizing network propagation for blocks and blobs has seen new contributions, with researchers exploring techniques to reduce bandwidth requirements and improve propagation times.
* [Blob Notaries](https://ethresear.ch/t/blob-notaries-a-distributed-blob-publishing-design-to-scale-da/22709): A distributed blob publishing design was proposed to scale data availability by introducing specialized notaries that help coordinate and validate blob data.
* [Multidimensional Gas Metering](https://ethresear.ch/t/a-practical-proposal-for-multidimensional-gas-metering/22668): Discussions continue on practical approaches to implementing multidimensional gas metering, which would allow for more granular resource pricing in the EVM.

## Layer 2

* [Base achieves Stage 1 Decentralization](https://base.mirror.xyz/tWDMlGp48fF0MeADcLQruUBq1Qxkou4O5x3ax8Rm3jA) with the launch of permissionless fault proofs and an improved contract upgrade process featuring a security council, marking a significant milestone in their journey toward a more decentralized network.

* [Starknet introduces Asset Runes](https://www.starknet.io/blog/dont-stop-hodling-introducing-asset-runes/), a new Bitcoin-native asset system that gives users 1:1 exposure to Ethereum tokens while remaining on the Bitcoin network, bridging the gap between Bitcoin's security and Ethereum's DeFi ecosystem.

* [Optimism client teams prepare for gas limit increase](https://etherworld.co/2025/07/10/highlights-from-the-all-core-developers-consensus-acdc-call-160/) to 45 million, with Prysm, Nimbus, Lodestar, and Lighthouse all implementing updates to support the higher throughput without compromising node stability.

* [Fusaka Devnet 3 launch date confirmed](https://etherworld.co/2025/07/10/highlights-from-the-all-core-developers-consensus-acdc-call-160/) for July 21-22, following the identification and resolution of critical interoperability issues in Devnet 2, which will serve as a "happy-path" stress test for the upcoming upgrade.

## Stuff for Developers

* [Ethereum clients roll out Partial History Expiry](https://etherworld.co/2025/07/08/ethereum-clients-roll-out-partial-history-expiry/) (PHE), allowing node operators to prune old historical data and significantly reduce storage requirements. Geth, Besu, and Nethermind have all implemented this feature with various configuration options.

* [Engine API v3 blob semantics approved](https://etherworld.co/2025/07/10/highlights-from-the-all-core-developers-consensus-acdc-call-160/) with the merging of PR #674, introducing a new `engine_getBlobsV3` endpoint that requires execution layer clients to emit partial blobs, improving reliability for consensus layer implementations.

* [Builder API's GetPayload endpoint simplified](https://etherworld.co/2025/07/10/highlights-from-the-all-core-developers-consensus-acdc-call-160/) to no longer return execution payloads or blobs, with relays taking full responsibility for blob delivery. This change, tracked in PR #123, aims to optimize proposer workflows and prevent performance bottlenecks as BPOs expand.

* [Standardized eth_config JSON-RPC method adopted](https://etherworld.co/2025/07/05/fusaka-devnet-2-recast-as-bug-hunt-devnet-3-as-happy-path/) following EIP-7910, providing a single authoritative source for genesis parameters such as gas schedules, blob limits, and network forks to prevent client discrepancies.

## Ecosystem

* [Ethereum Foundation announces Partial History Expiry](https://etherworld.co/2025/07/08/ethereum-clients-roll-out-partial-history-expiry/) as a significant step toward a stateless, sustainable, and globally scalable protocol, allowing clients to discard older block data after a certain period while maintaining consensus.

* [Glamsterdam upgrade timeline extended](https://etherworld.co/2025/07/04/glamsterdam-timeline-extended-for-in-depth-eip-review/) to allow for more thorough review of proposed EIPs, with a target decision date of July 24, 2025 for selecting the consensus layer headliner.

* [PeerDAS mainnet fork planned for mid-October 2025](https://etherworld.co/2025/07/10/highlights-from-the-all-core-developers-consensus-acdc-call-160/), with large-scale testnets of at least 1,000 nodes to be deployed in August and September to collect meaningful data on propagation delays and network health.

* [Two-phase BPO rollout strategy agreed upon](https://etherworld.co/2025/07/10/highlights-from-the-all-core-developers-consensus-acdc-call-160/) to introduce higher blob throughput without destabilizing the network, with BPO 1 scheduled for approximately one week after Fusaka and BPO 2 following one to two months later.

## Centralization watch: threatening the value of your ETH

* 🚨 [Lido at 25.84%](https://dune.com/hildobby/eth2-staking), still too close to the [33.3% threshold](https://notes.ethereum.org/@djrtwo/risks-of-lsd).
* Client diversity (via clientdiversity.org):
  * Execution layer: Geth ~41% & Nethermind ~38%
  * Consensus layer: Lighthouse ~42.71% & Prysm ~30.91%
  * Any client bug over 33.3% could mean loss of finality.
* Better [geographic diversity](https://nodewatch.io/) is optimal, particularly outside of North America & Europe.

## Client Releases

* Execution layer:
  * [Geth v1.16.1](https://github.com/ethereum/go-ethereum/releases/tag/v1.16.1): Patch release fixing regressions from v1.16.0, including issues with `eth_getLogs`, `eth_getTransactionReceipt`, and `geth --vmtrace`.
  * [Erigon v3.0.14](https://github.com/erigontech/erigon/releases/tag/v3.0.14): "Otterly Odyssey" patch fixing bor patch to defer sync events.
  * [Reth v1.5.1](https://github.com/paradigmxyz/reth/releases/tag/v1.5.1): Maintenance release with stability improvements, fixes for historical sync on Base mainnet, and support for Flashbots v5 relay block validation API.

## EIPs/Standards

* EIPs (Ethereum improvement proposals):
  * [EIP-7907](https://github.com/ethereum/EIPs/commit/5376a712188b6c85a4b6940db9df177f403b536d): Reduce code limit, increase cost per word, fix `EXTCODESIZE` issue 
  * [EIP-7928](https://github.com/ethereum/EIPs/commit/46f29129db955fb56dddfed72efbdd41b030f5ac): Modify CodeChanges List to allow a max of 1 
  * [EIP-7910](https://github.com/ethereum/EIPs/commit/59c5b1739bc30ae056517d5c1bc1cfd6ebf0a30f): Add Fork Id to response, spec BPOs, add "last" 
  * [EIP-7939](https://github.com/ethereum/EIPs/commit/a794de3fcf71bb8c71e8bafdba11f63133ce4516): Change gas cost from 3 to 5 
* ERCs (application layer):
  * [EIP-7612](https://github.com/ethereum/EIPs/commit/e240176c57a7992c6cca80bfd59cfc1ba807c181): Remove redundant word
  * [EIPS-7742](https://github.com/ethereum/EIPs/commit/18ee7c33e53469fcff70b1186a1d7459d6389aac): Moved to stagnant  

## Onchain Stats

* Fees (via [ultrasound.money](https://ultrasound.money)):
    * Gas: 0.2 to 9.5 gwei, 1.0 gwei average; zero net issuance at 20.5 gwei
    * 2.7k ETH net issuance this week
* [ETHUSD](https://www.coingecko.com/en/coins/ethereum): $2507 – $2598, currently $2,582, all time high $4,878
* [ETHBTC](https://ratiogang.com/): currently 0.0236 (Flippening at ~0.165)

## Upcoming Dates of Note

* Jul 17 - [ETHGlobal Istanbul](https://ethglobal.com/events/istanbul) hackathon
* Aug 23-25 - [ETHWaterloo](https://ethglobal.com/events/waterloo2025) hackathon
* Sep 12-14 - [ETHSafari](https://ethsafari.xyz/) (Kenya)
* Oct 8-10 - [Devcon 7](https://devcon.org/) (Bangkok)
* Nov 15-17 - [ETHGlobal San Francisco](https://ethglobal.com/events/sanfrancisco2025)