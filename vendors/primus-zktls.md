---
title: "Vendor: Primus zkTLS Network"
status: draft
maturity: testnet
---

# Primus zkTLS Network - Off-chain Data Verification

## What it is

Primus zkTLS Network is a decentralized data verification network based on zkTLS technology. It provides privacy-preserving off-chain data verification for any applications that require authentic web data including users private data. 

## Fits with patterns (names only)

- [Pattern: zk-TLS](../patterns/pattern-zk-tls.md): Primus network supports zkTLS-based data verification for decentralized applications.
- [Pattern: Attestation verifiable on-chain](../patterns/pattern-attestation-verifiable-on-chain.md): Primus network supports on-chain smart contract verification towards created attestations.
- [attern: zk-KYC/ML + ONCHAINID (ERC-734-735)](../patterns/pattern-zk-kyc-ml-onchainid-erc-734-735.md): Primus network supports privacy-preserving KYC/AML data verification, based on reusable KYC data from web2 identity providers. 

## Not a substitute for

- zkVM prover network (e.g., Brevis, Succinct, Boundless, Nexus)
- Attestation registry (e.g., EAS, verax)

## Architecture

- Client application: a client application integrates with Primus zkTLS SDK to request off-chain data verification from the network. A typical zkTLS protocol is executed between the client application, a selected network attestor and the web data source server. Eventually, the attestor should issue a signature on the proved data source within a TLS session, which is represented as a zkTLS attestation.

- Network contracts: contracts are deployed on EVM-compatible blockchains, to manage the attestors and tasks, and further verify the created zkTLS attestations.

- Network attestor: an network attestor is a computing node which forms a secure computation layer for executing zkTLS protocol. The 
attestor node is designated to run zkTLS tasks requested by client applications, and shall report the result to the network contracts. The attestor nodes run in TEEs, and form a decentralized working group to ensure the trustless computation.

## Privacy domains (if applicable)

- Attestor invisibility: the execution of a zkTLS protocol ensures the attestor is unaware of the attested data details.

- Privacy-preserving data verification: the created zkTLS attestation can be encoded in a privacy-preserving manner, where the client proves to the attestor that the attested data satisfies predefined conditions without revealing any sensitive information.
In that case, zkTLS operations like hashing and comparisons can be performed during the protocol execution.


## Enterprise demand and use cases

- Proof of reserve (PoR) solutions with off-chain asset accountability and privacy-friendly verification.
- zkKYC/AML for permissioned financial services.
- Authentic personal data sharing. 
- Programmable social payment and peer-to-peer on/off-rampings.

## Technical details

- Decentralized network architecture: Primus network is a decentralized network with system contracts to manage the off-chain attestors. To eliminate the trust of attestors, attestor nodes are deployed within TEEs by using Phala's DStack technology.
- zkTLS protocol: Primus network uses both proxy-TLS and MPC-TLS algorithms as configurable zkTLS variants. 
- Quicksilver protocol: the underlying VOLE-based interactive ZK system to support zkTLS protocols.
- Privacy-preserving computation: zkTLS attestation can be an input to a private zkVM program, to further enable privacy-preserving computation on the attested data, where the output proof can be verified publicly.
- Developer-friendly tools: multiple SDKs, developer hub, and Primus extension.

## Strengths

- Configurable privacy is supported by enabling zkTLS operations or exported zkVM computation.
- Trustless verification model with both zkTLS algorithm security and run-time envrionment security.
- Flexible performance and security tradeoff enabled by configurable zkTLS algorithms.
- Supports fetching data from any Web2 service, as long as it’s accessible through a TLS-based web API.

## Risks and open questions

- Performance: MPC-TLS algorithm execution may be latency-sensitive.
- Cross-network interoperability for zkTLS applications is still developing, as currently Primus network contracts are deployed on Base.

## Links
[Primus Website](https://primuslabs.xyz)
[Understand Primus Network](https://docs.primuslabs.xyz/primus-network/understand-primus-network)
[Build on Primus Network](https://docs.primuslabs.xyz/build/overview)
[Primus zkTLS protocol (MPC mode)](https://eprint.iacr.org/2023/964)