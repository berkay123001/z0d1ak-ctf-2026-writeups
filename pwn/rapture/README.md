# rapture · Pwn

**Core idea:** a “redundancy snapshot” copied a heap pointer without creating a new owner. Freeing one slot left its aliases usable as read/write handles to freed memory.

## Primitive and constraints

The snapshot menu stored the source chunk pointer in a second manifest slot. Freeing the source cleared only that slot; an alias still pointed to the chunk. Inspecting or recalibrating the alias therefore operated on a dangling pointer. Each manifest slot had a limited read and write ticket, so the chain required fresh aliases for each stage. A spent-ticket message is not a memory leak.

## Exploit outline

1. Exhaust the relevant tcache bin, free an aliased chunk into the unsorted bin, and read its `main_arena` pointer through the alias to determine the libc base.
2. Leak a freed chunk's safe-linked `fd` pointer. Reverse the `x ^ (x >> 12)`-style address masking to locate the heap.
3. Use an alias to overwrite a tcache `fd`, then allocate through the poisoned list to reach `environ` and learn the stack location. Two chunks must remain in the bin; otherwise a zero tcache count makes the allocator skip it.
4. Place a return-oriented chain on the stack and call `system("/bin/sh")` via libc gadgets. The return-address offset from `environ` varied between local and remote runs, so the exploit could not safely hard-code one universal offset.

## Evidence and limits

The private source audit records the live flag and the working exploit. The heap offsets, libc offsets, menu ticket accounting, and final stack distance are specific to the challenge's allocator and run. The writeup explains the chain; it does not claim a portable glibc technique.

**Flag:** `zdk{FR33d_ln_thE_d3EP_buT_nEver_Forg0T7en}`
