# Weekly Progress Report
**Week:** 3 November 2025 – 10 November 2025

## Summary of Activities

### Monday, 3 November 2025
Completed advanced exercises on smart contract memory management in Rust:
- Practiced pointer safety and ownership in no_std environments.
- Reviewed stack vs. heap allocation under CKB VM constraints.
- Documented best practices for optimizing small data structures.

### Tuesday, 4 November 2025
Explored Capsule framework setup for local CKB development:
- Installed Capsule CLI and initialized a test project.
- Built and deployed a sample contract locally.
- Compared Capsule deployment flow with CCC Playground workflow.

### Wednesday, 5 November 2025
Learned about transaction scripts and on-chain validation logic:
- Studied structure of lock and type scripts.
- Reviewed transaction lifecycle within the CKB blockchain.
- Simulated a basic validation flow with debug logging enabled.

### Thursday, 6 November 2025
Developed first integration test for a simple smart contract:
- Created unit tests using Capsule testing utilities.
- Implemented mock transaction inputs and outputs.
- Verified behavior of contract functions under different scenarios.

### Friday, 7 November 2025
Improved contract error handling and debugging capabilities:
- Integrated custom error enums with descriptive messages.
- Practiced propagating Result<T, E> through contract logic.
- Tested panic safety in runtime execution.

### Saturday, 8 November 2025
Focused on performance and gas optimization:
- Measured execution cost using profiling tools.
- Refactored code for reduced memory footprint.
- Benchmarked improved build against original implementation.

### Sunday, 9 November 2025
Consolidated weekly learning outcomes:
- Documented differences between CCC and Capsule workflows.
- Updated notes on no_std limitations and workarounds.
- Planned topics for next week’s deep dive on serialization and deserialization in CKB.

## Challenges & Notes
- Setting up Capsule required several environment dependencies not present in the Playground.
- Debugging transaction scripts locally took longer due to limited documentation.
- Continued progress in handling memory safety under no_std was essential for stable builds.

## Goals for Next Week
- Study serialization and deserialization for on-chain data structures.
- Build and deploy a multi-script transaction for end-to-end testing.
- Implement event logging and advanced error handling patterns.
