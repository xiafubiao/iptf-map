---
title: "Vendor: Primus FHE"
status: draft
---

# Primus FHE - A Modular Privacy-Preserving Computation Framework

## What it is

Primus FHE computation framework (so-called "FHEtransform") is designed as a modular, layered architecture that enables privacy-preserving computations on blockchain networks. The system combines on-chain smart contracts with off-chain processing capabilities to deliver secure, efficient fully homomorphic encryption operations.


## Fits with patterns (names only)

- [Private Stablecoin Shielded Payments](../patterns/pattern-private-stablecoin-shielded-payments.md): FHE allows encrypted balances/amounts for confidential transactions.
- [Private Intent-Based Vaults](../patterns/pattern-private-vaults.md): FHE enables confidential strategy execution without sacrificing asset transparency and auditability.
- [Shielded ERC-20 Transfers](../patterns/pattern-shielding.md): confidential ERC-20 token transfers with FHE computation service.
- [ZK Shielded Balances](../patterns/pattern-zk-shielded-balances.md): FHE can work alongside ZK techniques to enable confidential balances while preserving verifiability.

## Not a substitute for

- zkVM prover networks (e.g., Brevis, Succinct, Boundless, Nexus)
- off-chain compute networks without encrypted compute


## Architecture

FHETransform primarily consists of the following key components.

- **FHE Solidity library:** Also known as FHE system contracts, it allows developers to write confidential contracts in standard Solidity using encrypted data types and operations.

- **SpaceBridge:** SpaceBridge is a specialized blockchain component that serves as the core coordinator in FHETransform. SpaceBridge is responsible for coordinating interactions among users, the host chain, and Alphatrion, ensuring that encrypted data flows securely and correctly throughout the system.

- **AlphaTrion:** Decentralized services that verify encrypted inputs, run FHE computations, and commit results.

- **Preprocessor:** An off-chain component that transforms general EVM-based smart contracts into FHE-enabled contracts. enabling confidential transactions and privacy-preserving computation.

- **Key Management Service (KMS):** A threshold MPC network that generates and rotates FHE keys, and handles secure, verifiable decryption. At the current stage, the stores private keys in TEEs, with future plans to extend storage to the KMS. 

## Privacy domains (if applicable)

- **End-to-End Data Confidentiality**: Data remains encrypted from the moment it is created to the final output, ensuring that neither on-chain nor off-chain compute parties ever access sensitive plaintext.

- **Encrypted Operator Support**: All homomorphic operators (`+`, `−`, `*`, `/`, comparisons, boolean logic, etc.) are supported in encrypted form, enabling expressive confidential logic equivalent to plaintext computation. 

## Enterprise demand and use cases

- **Confidential Digital Asset Platforms**: Issue, trade, and manage tokens or assets where balances, holdings, and transaction logic remain confidential while the network can still enforce validity constraints. 

- **Secure Health and Finance Apps**: Perform analytics, scoring, or risk computations over encrypted personal or corporate data without exposing underlying plaintext, enabling regulatory compliance and user privacy.

- **Privacy-Preserving AI & Analytics**: Execute model inference or analytics tasks on encrypted datasets, such that service providers never see raw inputs or outputs, aligning with privacy regulations while deriving insights. 

- **Confidential Voting & Auctions**: Run on-chain auctions or voting systems where bids or votes remain encrypted, yet correct tallying and outcome determination are delivered.

## Technical details

- **Fully Homomorphic Encryption**: FHE allows computations to be performed directly on encrypted data without ever decrypting it. Smart contracts and compute services operate on ciphertexts, and only authorized users can decrypt final results. 

- **Modular, Layered Computation Stack**: FHETransform decouples encrypted computation from contract semantics, using modular components (Preprocessor, Alphatrion, KMS) to orchestrate secure encrypted workflows. 
  
- **Compiler-Like Integration for Developers**: Conventional Solidity contracts can be automatically transformed with FHE support, minimizing developer friction and enabling privacy-preserving logic in existing frameworks. 

- **Threshold Key Management for Security**: FHE keys are managed via threshold MPC, ensuring that no single party can derive decryption keys while maintaining verifiable decryption services for authorized consumers of computation outcomes.

## Strengths

- **Encrypted computation**: Data confidentiality is maintained at all times. 
  
- **Developer-friendly integration**: Solidity-based smart contracts and automated preprocessing enable easy adoption. 
  
- **Symbolic Execution**: All FHE operations are executed symbolically on the main chain. The actual computation over encrypted data is offloaded to Alphatrion, enabling more efficient, and highly scalable processing. 

## Risks and open questions

- **Performance and Cost**: FHE remains computationally intensive, and efficient execution at scale may require continued optimization. 
- **Key Management Complexity**: Threshold key rotation and secure MPC key services introduce operational complexity and trust assumptions, and are still under development. 
- **Ecosystem Adoption**: Integration with existing DeFi and enterprise stacks may require standardization and developer education.

## Links

- [FHETransform Docs](https://fhetransform.primuslabs.xyz/docs/intro/)  
- [Primus Labs Website](https://primuslabs.xyz)  

