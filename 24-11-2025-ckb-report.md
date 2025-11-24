# Weekly Report — 17 to 24 November 2025  
**Author:** Tarek  
---

## **Weekly Summary**

This week was fully focused on deepening my understanding of **CKB Scripts**, **VM execution**, **syscalls**, and **cycle regulation**.  
I explored how scripts execute inside the **CKB-VM**, how lock & type scripts differ, how execution cost is measured, and how different programming languages can be used to build on-chain logic on Nervos CKB.

The second half of the week covered lower-level aspects such as **syscall usage**, **VM version selection**, and **cycle limits**, which clarified how the CKB protocol guarantees determinism, security, and performance across dApps.

---

## **Day-by-Day Progress**

---

### **Monday — 17 Nov — Intro to Scripts & Execution Model**

* Started the week by reviewing **what a Script is** in CKB:  
  - A Turing-complete binary executed inside the CKB-VM  
  - Controls ownership (Lock Script)  
  - Defines validation logic (Type Script)
* Studied **how scripts are executed**, focusing on:  
  - Execution inside CKB-VM  
  - Script success/failure codes  
  - How CKB executes all scripts of a transaction to validate it

**Key Understanding:**  
Scripts behave like executable binaries, similar to Unix programs compiled for RISC-V, giving CKB unique flexibility compared to other blockchains.

---

### **Tuesday — 18 Nov — Script Types & Structure**

* Deep dive into **Lock Scripts vs Type Scripts**:
  - Lock Script: controls ownership & spending  
  - Type Script: controls state transitions
* Learned the **Script structure**:  
  - `code_hash`  
  - `hash_type` (data, type, data1, data2)  
  - `args`
* Understood how **hash_type influences VM version selection** and determinism.

**Key Insight:**  
The same script code can behave differently depending on its args. This makes scripts reusable and highly customizable.

---

### **Wednesday — 19 Nov — Programming Languages for Scripts**

* Explored languages available for CKB script development:
  - **Rust** (recommended — safety + performance)
  - **C** (used for sUDT, xUDT)  
  - **JavaScript** (via QuickJS interpreter — slower but flexible)  
  - **Lua**, **Ruby**, **Python**, **Golang**, etc. (via VM-on-VM deployment)
* Studied important Rust libraries:
  - `ckb-std`
  - `ckb-testtool`
  - `ckb-script-templates`

**Key Insight:**  
Any language can run on CKB if its VM/interpreter is deployed on-chain — extremely powerful architecture.

---

### **Thursday — 20 Nov — Syscalls & Interaction with CKB-VM**

Focused on learning the internal **CKB-VM syscalls** that scripts rely on to interact with the blockchain state.

Covered syscalls such as:
* `ckb_load_cell`
* `ckb_load_input`
* `ckb_load_header`
* `ckb_load_transaction`
* `ckb_load_witness`
* `ckb_spawn`, `ckb_wait`, `ckb_write`, `ckb_read`, etc.
* Low-level constants like:
  - `CKB_SOURCE_INPUT`, `CKB_CELL_FIELD_CAPACITY`, etc.

Explored the **spawn syscall example**, showing how scripts can:
* create processes,
* write/read between them,
* and validate string operations.

**Key Insight:**  
Syscalls are the backbone of script interaction with transaction data; understanding them is mandatory before writing serious on-chain logic.

---

### **Friday — 21 Nov — Regulating Scripts with Cycle Limits**

* Studied how CKB manages **resource limits** through cycles.
* Learned the rules for:
  - Instruction cycle cost (e.g., MUL, DIV, branches)
  - Syscall cycle cost (≥500 cycles + memory cost)
  - ELF loading cost (0.25 cycles/byte)
* Reviewed **max_block_cycles = 3.5B** (Mirana mainnet)
* Learned how cycle limits prevent:
  - infinite loops  
  - denial-of-service scripts  
  - oversized executables  

**Key Insight:**  
Cycle limits ensure predictable execution and fair use of VM resources without limiting the expressiveness of the VM.

---

### **Saturday — 22 Nov — VM Improvements & MOP Fusion**

* Reviewed **MOP Fusion** (Macro-op fusion) in VM v1 & v2.
* Learned how fused operations dramatically reduce cycle cost for:
  - multiplication  
  - division  
  - crypto-heavy functions  
  - far jumps  
  - 32-bit extensions

**Key Insight:**  
VM micro-optimizations matter a lot, especially for cryptographic scripts or repetitive logic.

---

### **Sunday — 23 Nov — VM Version Selection & Determinism**

* Studied how CKB selects **which VM version** to use for each script.
* Learned that this depends on the script’s `hash_type`:
  - `data` → VM0  
  - `data1` → VM1  
  - `data2` → VM2  
  - `type` → always latest VM  
* Reviewed cases where developers should pick:
  - **data hash** = deterministic execution  
  - **type hash** = access to latest VM features

**Key Insight:**  
CKB gives developers full control over determinism, compatibility, and feature updates.

---

### ** Monday — 24 Nov — Security & Defensive Measures**

* Reviewed how CKB handles **VM vulnerabilities**:
  - mempool-level protection (not consensus-breaking)
  - ability for users to bypass restrictions if needed
* Understood how the chain balances:
  - developer freedom  
  - protocol safety  
  - backward compatibility  

**Key Insight:**  
Even when issues occur, CKB prioritizes decentralization by keeping final control in the user’s hands.

---

## **Challenges**

* Some syscalls are complex and require a strong understanding of Molecule serialization.
* VM version differences can introduce subtle bugs if not handled properly.
* Cycle measurement rules are detailed and require careful attention when optimizing scripts.

---

## **Goals for Next Week**

* Begin hands-on testing using **ckb-testtool**.
* Write a basic Rust lock script.  
* Experiment with VM cycle profiling.  
* Implement a small example using `ckb_load_cell` and `ckb_load_witness`.
* Explore Type ID scripts and on-chain code deployment flow.

---

## **End of Report**
**Prepared by:** Tarek  
**Date:** 24 November 2025