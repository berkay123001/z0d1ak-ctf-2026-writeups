# husk · Reverse engineering

**Core idea:** the binary's anti-debug checks did not need to be defeated. In the normal, untraced environment, their failure values formed the key to the next decoding stage.

## Reversing the check

The program combined outcomes from `ptrace`, `TracerPid`, a timing probe, and an environment check into four little-endian words. Under the expected normal conditions, these words became the 16-byte RC4 key. A table near the usage string supplied a 41-byte shuffled buffer; RC4 KSA/PRGA turned it into the target state.

The input candidate itself passed through six rounds of byte transformations: rotations, XOR, additions, and permutations, followed by a linear-congruential-generator XOR stream. Instead of brute-forcing a 41-byte candidate, the solver inverted those rounds in reverse order, then undid the final LCG stream. Correctness depends on preserving byte truncation and 32-bit wraparound at each step.

## Evidence and limits

The local solver read the supplied `husk` binary and returned the full flag during this publication audit. That independently supports the private index entry; it is not an accepted-submission receipt.

**Flag:** `zdk{the_ANtld3BUG_wAs_the_deCRyPtLon_K3y}`

**Lesson:** anti-analysis branches can themselves encode the intended key schedule; model the normal execution path before patching them away.
