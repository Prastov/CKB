# Weekly Report (10 – 16 Nov 2025)

## Day-by-Day Progress

### Monday, Nov 10  
Started the week by reviewing the introduction to Lumos.  
Understood that Lumos is a dApp framework enabling both frontend and backend development on Nervos CKB.  
Reviewed the structure of a Lumos-based transaction, including creating a transaction skeleton, adding inputs and outputs, signing, and broadcasting to a local CKB Dev Chain.  
Executed an initial example using `node index.js` to observe the lifecycle of a transaction.

### Tuesday, Nov 11  
Focused on transaction structure, including inputs, outputs, dependencies, and witnesses.  
Explored how the `TransactionSkeleton` is built and updated with ImmutableJS and how `addDefaultCellDeps()` and `addDefaultWitnessPlaceholders()` simplify transaction preparation.  
Sent a test transaction and learned how to verify its confirmation via:  
`rpc get_transaction --hash <TX_HASH>`.

### Wednesday, Nov 12  
Encountered the recurring issue “Live cell not found” when re-running the same transaction.  
Learned that once a cell is consumed as an input, it becomes a dead cell and cannot be reused.  
Documented how to locate valid live cells using:  
`ckb-cli rpc get_live_cell`.

### Thursday, Nov 13  
Completed the lab on calculating capacity requirements.  
Manually gathered a live cell belonging to the account `ckt1...gwga`.  
Added logic to calculate transaction fees and output capacities, ensuring the change cell properly handled remaining CKBytes.  
Learned to work with fees denominated in Shannons, where 1 CKByte equals 100,000,000 Shannons.

### Friday, Nov 14  
Studied cell collection mechanisms and indexers in Nervos.  
Learned how indexers improve transaction assembly performance by organizing cell data.  
Configured the `ckb.toml` file to activate the Indexer module.  
Tested the configuration by running a small script using the Lumos Indexer class.

### Saturday, Nov 15  
Worked on the Automated Cell Collection Lab.  
Used the `collectCapacity()` function from Lumos’ shared library to automatically gather input cells based on required capacity.  
Configured a transaction involving multiple inputs and two outputs (recipient and change).  
Gained an understanding of how automated collection reduces errors and ensures correct capacity handling.

### Sunday, Nov 16  
Explored methods for storing data inside a cell.  
Used both `ckb-cli` and Lumos to create a cell containing file-based data (“Hello Nervos!”).  
Calculated the required capacity as 61 CKBytes (minimum) plus 13 CKBytes (data), totaling 74 CKBytes.  
Verified the stored data by decoding the hex output and validating its hash using:  
`ckb-cli util blake2b --binary-path "./files/HelloNervos.txt"`.

## Summary of the Week  
This week provided practical experience with Lumos transaction creation, cell management, and data storage on-chain.  
Khalil practiced both manual and automated transaction workflows and strengthened understanding of capacity as the defining factor in CKB storage.  
The introduction to indexing and data storage workflows clarified how smart contracts and dApps interact with the CKB state layer.

## Challenges and Notes  
Repeated “live cell not found” issues highlighted the importance of using fresh live cells.  
Troubleshot Indexer configuration through adjustments in `ckb.toml`.  
Initial difficulty working with Shannons, later resolved with consistent practice.  
Recognized that storage-heavy dApps require thoughtful CKByte planning.

## Goals for Next Week  
Begin development of a custom lock script using Rust.  
Study type scripts and how transaction validation logic is enforced.  
Investigate how Lumos handles script deployment and debugging.  
Practice retrieving on-chain data using Lumos indexer queries.

**Period:** 10 – 16 Nov 2025
