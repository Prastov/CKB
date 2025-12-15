# Daily Report – CKB Study Progress
**Author:** Tarek  
**Period:** 08/12/2025 – 15/12/2025  

---

## 08/12/2025
- Reviewed the overall lifecycle of a CKB transaction from creation to confirmation.
- Studied the different transaction states (Pending, Confirming, Confirmed, Conflicting, Reverted, Abandoned).
- Focused on best practices for handling pending transactions and avoiding unsafe chaining.

## 09/12/2025
- Studied the full structure of a CKB transaction in detail.
- Analyzed each field including version, inputs, outputs, witnesses, and outputs_data.
- Reviewed real transaction examples to better understand how data is serialized and stored.

## 10/12/2025
- Learned how `cell_deps` work and why they are required for script execution.
- Compared `code` and `dep_group` dependency types and their use cases.
- Understood how CKB loads dependency cells into CKB-VM during execution.

## 11/12/2025
- Focused on transaction inputs and how Cells are consumed.
- Studied the `since` field and how it enables time-locked transactions.
- Reviewed block number, epoch-based, and timestamp-based constraints.

## 12/12/2025
- Deep dive into witnesses and their role in script validation.
- Studied the WitnessArgs convention and its structure.
- Understood how lock, input_type, and output_type fields are used by different scripts.

## 13/12/2025
- Learned how script grouping works in CKB transactions.
- Analyzed how witnesses are indexed and shared between script groups.
- Reviewed a complex example involving multiple lock and type scripts.

## 14/12/2025
- Studied block structure and how transactions are included in blocks.
- Learned about confirmation depth and chain reorganizations.
- Reviewed uncle blocks, their conditions, and how they affect consensus.

## 15/12/2025
- Studied the Fee Estimator feature introduced in recent CKB versions.
- Compared Confirmation Fraction and Weight-Units Flow algorithms.
- Reviewed limitations, fallback mechanisms, and best practices for fee estimation.

---

**Summary:**  
This week focused on building a solid understanding of CKB core transaction mechanics, preparing for more advanced on-chain script development.
