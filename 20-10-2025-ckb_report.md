# CKB Learning Journey: Week of 20-27 October 2025

## Daily Learning Log

### 20/10/2025 | CKB Fundamentals
**Core Concepts Explored:**
- Discovered CKB (Common Knowledge Base) as Nervos Network's foundational layer
- Learned about Proof of Work consensus mechanism implementation
- Understood the decentralized, immutable ledger architecture
- Explored key components: Cell Model, Scripts, Transactions, and CKB-VM

### 21/10/2025 | Transaction Mechanics
**Transaction Flow Analysis:**
- Cells as containers for value and data storage
- Minimum storage requirement: 61 CKBytes (62 recommended for fees)
- Live Cells concept: unspent transaction outputs
- Transaction lifecycle example (200 CKB → 100 CKB transfer):
  - Input selection and output creation
  - Digital signature application
  - Network propagation through nodes
  - Mining confirmation and state transition

### 22/10/2025 | Script Architecture
**Script System Deep Dive:**
- Scripts as binary programs executed on CKB-VM (RISC-V)
- Three-component structure:
  - Code hash for script identification
  - Hash type for location method
  - Args for script differentiation
- Script categories:
  - Lock Scripts (mandatory ownership control)
  - Type Scripts (optional usage rules)
- Practical example: secp256k1_blake160_sighash_all verification process

### 23/10/2025 | Virtual Machine Operations
**CKB-VM Execution Model:**
- RISC-V based script execution environment
- Four-phase execution workflow:
  1. Script loading via hash references
  2. Data retrieval from cells and witnesses
  3. Logic execution and validation
  4. Success/failure status return
- Resource management through cycle counting
- Block-level computational limits (3.5B cycles mainnet)

### 24/10/2025 | Development Environment
**OffCKB Toolchain Setup:**
```bash
# Environment initialization
npm install -g @offckb/cli
offckb node          # Start local devnet
offckb clean         # Reset chain state

# Project development workflow
offckb create my-project -c my-contract
offckb deploy --network devnet --target ./build --output ./deployments
offckb debug <tx-hash>
```

### 25/10/2025 | Debugging & Optimization
**Transaction Analysis:**
- Detailed script execution tracing
- Cycle consumption metrics (example: 3.8M cycles total)
- Single-cell debugging techniques:
```bash
offckb debug <tx-hash> --single-script input[0].lock
offckb debug <tx-hash> --bin ./custom-script.bin
```

### 26/10/2025 | Network Infrastructure
**Multi-Environment Strategy:**
- Mainnet: Production environment (ckb address prefix)
- Testnet (PUDGE): Protocol testing (ckt address prefix)
- Devnet: Local development sandbox

**Environment switching:**
```bash
offckb system-scripts --network testnet
```

### 27/10/2025 | API Integration
**RPC & Real-time Communication:**
- JSON-RPC 2.0 interface for blockchain interaction
- Essential methods:
  - Chain state queries (`get_tip_block_number`)
  - Transaction management (`send_transaction`, `get_transaction`)
- Real-time monitoring:
  - TCP subscriptions (port 18114)
  - WebSocket connections (port 18115)
- Data formatting standards: hex encoding with 0x prefix

## Weekly Insights

### Key Technical Understanding
- **Cell Model:** Grasped the fundamental storage unit and transaction lifecycle
- **Script Execution:** Understood how lock/type scripts control asset behavior
- **VM Architecture:** Learned about RISC-V implementation and cycle-based resource management
- **Tooling Proficiency:** Gained hands-on experience with OffCKB development stack

### Development Challenges
- Transaction cycle optimization requires careful planning
- Network stability considerations for different environments
- Strict data formatting requirements in RPC communications
- Debugging complexity with multi-script transactions

### Forward Planning

**Immediate Objectives (Next Week):**
- Smart Contract Development: Build and deploy TypeScript contract on Devnet
- API Integration: Implement JSON-RPC and WebSocket communication
- Scenario Testing: Multi-cell transaction patterns and edge cases
- Performance Tuning: Cycle optimization strategies for custom scripts

**Skill Development Focus:**
- Advanced script debugging techniques
- Multi-network deployment strategies
- Resource consumption optimization
- Real-time monitoring implementation
