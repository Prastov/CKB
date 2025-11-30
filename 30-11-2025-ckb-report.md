# Weekly Report --- CKB VM, Type-ID, Spawn, IPC, Debugging

**Author:** Tarek\
**Period:** 24 Nov 2025 → 30 Nov 2025

------------------------------------------------------------------------

## Monday --- 24 Nov 2025

I focused on understanding the full evolution of the CKB virtual
machines: VM0, VM1, and VM2.\
I reviewed how script execution depends on the selected VM version and
the impact of hash_type on version selection, especially for long-term
contract maintenance.\
I studied VM0 in detail: its instruction set, the initial cost model,
and the role of syscalls in memory-bound and I/O-bound operations.\
I also analyzed VM1 and VM2 changes, particularly the introduction of
the B-extension and the new MOP instructions that improve memory
performance.\
Finally, I reviewed the practical impact of deprecated syscalls and why
legacy syscalls such as exec are unsafe for modern deployments.

------------------------------------------------------------------------

## Tuesday --- 25 Nov 2025

I deepened my work on VM instruction costs and transaction execution
performance.\
I reviewed how CKB rounds fractional costs, how load cost multipliers
are applied, and why some instructions (like bitwise and multiplication)
become cheaper in VM2.\
I studied syscall pricing for data loading, witness reading, script
hashing, and signature verification.\
I also analyzed VM1's limitations: the issues around **spawn** vs
**exec**, the cost model inconsistencies, and how VM2 fixes these
problems with clearer rules, deterministic execution, and improved
safety around memory isolation.

------------------------------------------------------------------------

## Wednesday --- 26 Nov 2025

I spent the day studying **Type-ID**, which is central to secure
upgradable smart contracts on CKB.\
I learned the exact hash computation process for Type-ID generation
during minting, transfer, and burning cases.\
I reviewed the uniqueness guarantees:\
- how input 0 is used\
- how output index participates\
- why only one live cell may exist with the same Type-ID\
I also explored threat scenarios such as dependency injection attacks,
code hash collisions, and forged cell-deps, and confirmed how Type-ID
prevents all of these by binding script identity to a deterministic
hash.

------------------------------------------------------------------------

## Thursday --- 27 Nov 2025

I focused on the practical implementation of Type-ID.\
I reviewed the Rust implementation of the validation function, including
verifying group input/output constraints and comparing calculated IDs
with the stored ID in script args.\
I also studied how Type-ID was integrated at genesis level using a
predefined hash, and why the hash must remain stable forever.\
I explored how developers typically integrate Type-ID checks inside
custom lock and type scripts, especially when supporting migrations or
adding new behaviors over time.

------------------------------------------------------------------------

## Friday --- 28 Nov 2025

I worked on understanding the **Spawn** syscall introduced in the Meepo
hard fork.\
I compared Spawn to exec and noted the improvements:\
- child process isolation\
- explicit passing of argv\
- ability to wait for a child and retrieve its exit status\
- no ABI reuse problems\
- safer context handling\
I studied the full execution model: parent VM, child VM creation,
available file descriptors, memory isolation rules, and constraints such
as max number of VMs.\
I also reviewed the internal scheduling model and how child processes
affect total cycle consumption.

------------------------------------------------------------------------

## Saturday --- 29 Nov 2025

I dedicated the day to learning **inter-process communication** on CKB
via Spawn and pipes.\
I reviewed how a parent script creates a pipe, spawns a child, and
transfers one end of the pipe to the child.\
I studied serialization formats, including typical ArrayBuffer-based
encoding and the importance of reading data in loops to avoid partial
reads.\
I examined common errors such as:\
- OtherEndClosed\
- MaxVmsSpawned\
- unexpected EOF during read\
I also understood how to use wait to synchronize execution and ensure
both the child exit code and its output are handled correctly.\
Finally, I reviewed examples demonstrating on-chain modularization using
Spawn to load additional behaviors into child processes.

------------------------------------------------------------------------

## Sunday --- 30 Nov 2025

I completed the week studying **ckb-script-ipc**, the library built on
top of Spawn for higher-level communication.\
I reviewed the packet format: size prefix, method ID, payload, and error
codes.\
I analyzed how IPC supports a client/server pattern inside the CKB VM,
enabling reusable libraries, multi-function scripts, and structured
request/response communication.\
I also reviewed serialization choices, including JSON for readability
and simple binary formats for gas efficiency.\
Finally, I studied advanced debugging tools:\
- using CKB-Debugger to inspect execution steps\
- integrating GDB for native debugging\
- profiling cycles using flamegraphs\
- using the Native Simulator for fast local tests\
This gave me a complete view of the low-level debugging workflow for CKB
smart contracts.

------------------------------------------------------------------------

## End of Weekly Log

This week provided a deeper technical understanding of CKB's virtual
machines, contract versioning, Type-ID validation, Spawn-based process
creation, IPC frameworks, and professional debugging techniques
essential for advanced script development.
