# Weekly Report — 1 Dec 2025 → 8 Dec 2025  
**Author: Tarek**

This week I focused on deepening my understanding of CKB’s transaction model, block structure, and all the mechanisms that make the chain deterministic, secure, and flexible. Below is a detailed breakdown of what I learned and worked on each day.

---

##  Monday — 1 Dec 2025  
**Topic: Transaction Structure**

Today I began by studying the full structure of a CKB transaction and how it consumes existing Cells to create new ones.  

I reviewed each field in detail:

- **version** (used for protocol evolution)  
- **cell_deps** (dependency cells allowing scripts to run)  
- **header_deps** (block headers necessary for deterministic execution)  
- **inputs** (Cells being spent)  
- **witnesses** (signatures or proofs)  
- **outputs** (newly generated Cells)  
- **outputs_data** (data stored in each output)

I also examined a complete raw transaction example to understand how outputs and outputs_data are separated, and why CKB’s VM benefits from this design.

---

##  Tuesday — 2 Dec 2025  
**Topic: Transaction Lifecycle**

Today I learned about the different states a transaction can go through:

- Pending  
- Confirming  
- Confirmed  
- Conflicting  
- Conflictive  
- Reverted  
- Abandoned  

I understood when and why transactions change state, and how generators should behave:  
– avoid chaining pending transactions  
– never use outputs of confirming transactions  
– store reverted transactions  
– keep abandoned transactions for some time  

The distinction between **Conflicting** and **Conflictive** became clear: one depends on pending finality, the other on confirmed conflicting transactions.

---

##  Wednesday — 3 Dec 2025  
**Topic: cell_deps**

I dug deeper into how **cell_deps** work and why scripts need them.  
I reviewed the structure of a **CellDep**, especially:

- **out_point** (tx_hash + index)  
- **dep_type** (code or dep_group)

Today I fully understood the difference between **code** and **dep_group**, and why grouping dependencies can dramatically reduce transaction size and improve efficiency.

---

##  Thursday — 4 Dec 2025  
**Topic: header_deps**

Today I focused on **header_deps** and the determinism rules of CKB.  

I learned that:

- Only canonical chain headers can be referenced.  
- No uncle block can be included in header_deps.  
- Transactions must execute results identically across nodes.

This is essential to maintain consensus and avoid any inconsistent script execution.

---

##  Friday — 5 Dec 2025  
**Topic: Inputs & Time Locks (since)**

Today I looked at the structure of **CellInput**, especially:

- **previous_output**  
- **since** (time lock mechanism)

I learned how **since** can enforce:

- block height locks  
- epoch-based locks  
- timestamp-based locks  

The main rule I learned:  
️ If **one** input’s since condition is not satisfied, the **entire** transaction is invalid.

---

##  Saturday — 6 Dec 2025  
**Topic: Witnesses & Script Conventions**

Today I explored how **witnesses** are used for signatures and proofs.  
I learned the structure of **WitnessArgs**:

- lock  
- input_type  
- output_type  

I studied the grouping rules and understood how multiple scripts may reference the same witness but only read the part that concerns them.  

The concept of **script grouping** and witness ordering finally became clear thanks to the detailed example.

---

##  Sunday — 7 Dec 2025  
**Topic: Outputs & outputs_data**

Today I reviewed the role of **outputs** and **outputs_data**.  
I learned why CKB separates these two:

- outputs → state (capacity + lock + type)  
- outputs_data → raw data  

This helps maintain a state model that is easy to verify and allows future optimization.

---

##  Monday — 8 Dec 2025  
**Topic: Fee Estimator, Blocks & Uncles**

### Fee Estimator  
I learned about the new CKB Fee Estimator (v0.120.0) and explored:

- Confirmation Fraction algorithm  
- Weight-Units Flow algorithm  
- Fallback estimator  
- Priority modes  

I now understand how nodes estimate fee rates using pool flow and historical data.

### Blocks  
I reviewed block structure in detail:

- header  
- transactions  
- proposals  
- uncles  

I also studied an actual block JSON to see how all fields fit together.

### Uncle Blocks  
I learned the exact conditions for a block to be considered an uncle:

- Same epoch & difficulty  
- Not part of main chain  
- Parent relationship rules  
- First referencing block rules

The examples helped me understand how miners handle block races.

---

##  Weekly Summary

This week, I focused on mastering how CKB transactions and blocks work. I now understand:

- The full transaction format  
- Transaction state transitions and best practices  
- How cell_deps and header_deps function  
- Inputs, since locks, and time constraints  
- Witness structures and grouping conventions  
- Output cell structure and data model  
- Fee estimation models  
- Block structure and uncle block logic  

I feel much more confident analyzing and building CKB transactions after this week.

