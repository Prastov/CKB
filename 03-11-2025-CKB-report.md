# CKB Learning Journey: Week of 20 October – 3 November 2025

## Daily Learning Log

### 28/10/2025 | Multi-Language SDK Overview
**Core Concepts Explored:**
- Overview of available SDKs for interacting with CKB (Rust, Go, Java, JavaScript/TypeScript)
- Compared architecture, maturity, and ecosystem support of each SDK
- Understood how language choice impacts performance, integration, and debugging
- Set up local environments for Rust, Go, and Node.js to test SDK operations

### 29/10/2025 | Rust SDK Deep Dive
**Development Focus:**
- Installed and configured `ckb-sdk-rust`
- Explored transaction creation via the Rust API
- Implemented simple cell creation and transfer scripts
- Learned error handling and dependency management using Cargo
- Experimented with serialization using `molecule-rust`
- Observed Rust’s strong type safety and low-level memory efficiency for CKB logic

### 30/10/2025 | Go SDK Implementation
**Hands-On Practice:**
- Installed `ckb-sdk-go` and configured a lightweight devnet environment
- Created scripts to query chain state (`GetTipBlockNumber`, `GetCellsByLockHash`)
- Built and sent basic transactions through RPC endpoints
- Explored Go’s concurrency patterns for monitoring live transactions
- Understood Go’s advantages in building CKB backend services due to goroutines and simplicity

### 31/10/2025 | Java SDK Exploration
**Object-Oriented Integration:**
- Set up `ckb-sdk-java` for enterprise-grade development
- Explored `CkbRpcClient` and `AddressUtils` classes
- Created Java-based transaction builder
- Integrated JSON-RPC communication for on-chain data retrieval
- Analyzed performance and JVM-level memory management tradeoffs
- Ideal use case: enterprise and multi-threaded CKB infrastructure apps

### 01/11/2025 | JavaScript & TypeScript SDK
**Frontend & Fullstack Development:**
- Installed `@nervosnetwork/ckb-sdk-core` and `@nervosnetwork/ckb-sdk-utils`
- Created a wallet instance and built mock transactions in TypeScript
- Connected to Devnet using WebSocket for real-time updates
- Implemented custom lock script execution
- Tested multi-cell transfers through async functions
- Observed how JS/TS SDK simplifies CKB dApp frontend integration

### 02/11/2025 | Cross-SDK Comparison
**Comparative Evaluation:**
- Benchmarked transaction build times across Rust, Go, Java, and TypeScript
- Compared API design patterns and data serialization formats
- Evaluated RPC interaction performance
- Documented SDK-specific pain points (Rust: setup complexity, Java: verbosity)
- Identified best-fit SDKs by use case:
  - **Rust** → Smart contract & low-level tooling
  - **Go** → Backend microservices & monitoring agents
  - **Java** → Enterprise integration & large system pipelines
  - **TypeScript** → Frontend and quick prototyping

### 03/11/2025 | Integration & Toolchain Automation
**System-Wide Experimentation:**
- Built multi-language toolchain for CKB interaction and testing
- Automated RPC calls across SDKs to compare real-time block responses
- Created unified test scripts for transaction simulation
- Analyzed performance (avg transaction broadcast latency: ~220ms Devnet)
- Improved debugging flow with unified logging and error capture

## Weekly Insights

### Key Technical Understanding
- **SDK Ecosystem Mastery:** Understood how different languages interact with CKB via JSON-RPC
- **Rust Proficiency:** Gained confidence in low-level transaction scripting and molecule serialization
- **Go & Java Strengths:** Identified their backend reliability for CKB services
- **TypeScript Advantage:** Learned how to integrate CKB features easily into web and fullstack environments

### Development Challenges
- Managing dependencies across SDKs with varying library maturity
- Consistency in transaction formats between Rust and TypeScript implementations
- RPC endpoint version differences between networks
- Debugging multi-language toolchains during parallel testing

### Forward Planning

**Immediate Objectives (Next Week):**
- Build a cross-language benchmarking suite for transaction validation
- Deploy smart contracts using Rust on Devnet
- Integrate Go-based backend with TypeScript frontend
- Begin real-world scenario testing with multi-cell transactions

**Skill Development Focus:**
- Advanced RPC integration patterns
- Unified SDK testing and automation scripting
- Smart contract optimization in Rust
- Continuous deployment setup for CKB services
