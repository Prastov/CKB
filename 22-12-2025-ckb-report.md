# Weekly Report – Nervos CKB Learning  
**Author:** Tarek  
**Period:** 15/12/2025 → 22/12/2025  

---

## Overview
During this week, I focused on understanding the **Block structure in CKB**, the concept of **Uncle Blocks**, detailed exploration of **Block Header & PoW validation**, how transactions are packaged, and finally how **nodes work**, including running Full Nodes & Testnet Nodes. This helped me better understand how CKB maintains decentralization, security, and performance.

---

### Monday – 15/12/2025  
Today I studied what a **Block** is in Nervos CKB. I learned that a block is a container of transactions and includes important consensus data.  
I explored the block structure fields:
- `header`
- `transactions`
- `uncles`
- `proposals`

I also reviewed real JSON examples to better visualize how a block is structured on-chain.

---

### Tuesday – 16/12/2025  
I continued working with **Block transactions** and how they are committed.  
Key learnings:
- Transactions inside a block are finalized and validated
- The first transaction is always a **cellbase transaction** (miner reward)
- Proposals exist before commitment

I also reviewed examples of transactions inside blocks to understand how inputs, outputs, locks, and witnesses appear structurally.

---

### Wednesday – 17/12/2025  
Today I learned deeply about **Uncle Blocks**.  

Main points:
- Uncle blocks occur when 2 miners produce blocks at nearly the same time
- Only one enters the canonical chain
- The other becomes an *uncle* block
- Studied the conditions that classify an uncle block:
  - Must not be on the main chain  
  - Same epoch and difficulty  
  - Referenced correctly by another block  

This helped me understand chain competition and fairness in PoW networks.

---

### Thursday – 18/12/2025  
Focused on the **Header** of a block and why it is critical.  

I studied:
- Header structure  
- RawHeader fields (version, epoch, timestamp, difficulty, parent hash)
- Relationship between:
  - `transactions_root`
  - `uncles_hash`
  - `proposals_hash`
  - `dao` data

Then I studied **Proof of Work header verification process** and how:
- Eaglesong hashing works
- Compact target difficulty comparison works
- Nonce validation determines PoW success

This gave me much clearer insight into security mechanisms on CKB.

---

### Friday – 19/12/2025  
Today I focused on how the header hash is derived and how CKB references blocks using it.
Also studied:
- UncleBlock structure formally
- Transactions commitment flow and proposal lifecycle
- Learned that proposals must be included before commitment
- Understood delay windows like `close` and `far` commitment windows

---

### Saturday – 20/12/2025  
Shifted learning from protocol theory to **node level understanding**.  

Studied:
- What a node is
- Why running your own node is important
- Trustless verification
- Privacy benefits
- Contribution to decentralization

Also reviewed trade‑offs such as storage cost, performance requirements, network usage.

---

### Sunday – 21/12/2025  
Studied **Full Nodes** and **Light Nodes**.

Key learnings:
- Full node stores full blockchain + validates blocks
- Light node stores headers only
- Full node = maximum trustless + decentralization
- Light node = lightweight but needs trust in other nodes
- Understood resource requirements (disk, CPU, RAM)

Also studied how CKB avoids state bloat using:
- Live cells only rule
- 1 CKB = 1 byte storage economy
- Spending cells to free state space

---

### Monday – 22/12/2025  
Finally I learned how to:
- Install CKB node
- Run Mainnet node
- Run Testnet node
- Check sync with `sync_state`
- Handle IBD state
- Make node connectable
- Ensure it contributes to P2P network stability

Reviewed real logs examples to understand syncing behavior.

---

## Summary of the Week
This week gave me a strong understanding of how CKB works at **block level + consensus level + node level**. Now I have a clear picture of:
- How blocks are structured
- How uncle blocks work
- How headers secure blockchain integrity
- How transactions move from proposal to commitment
- How nodes validate and secure the network

I am now much more confident in understanding internal blockchain mechanics of Nervos CKB.

---

**Tarek**
