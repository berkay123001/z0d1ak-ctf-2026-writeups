# THESEUS · Crypto / EVM

**Core idea:** an address is only a location. Its current bytecode is not the whole history of the contract that lived there.

## The puzzle

The target `Theseus` address had five successive implementations. Four earlier hulls were destroyed, so inspecting only the final deployed code lost the values needed by `unlock`. The chain's transaction and log history remained available. The useful question was therefore not “what does the current contract contain?” but “which historical commitments can be reconstructed from its earlier transactions?”

## Reconstruction

1. Recover `firstMark` from block 3 and `secondMark` from block 8.
2. At block 13, read the eight canonical records. Each record is the one-byte index followed by its log data, not just the log data alone.
3. Apply the historical chart decoder to obtain the selected leaf, three Merkle siblings, `harbourRoot`, and `proofSalt`. Keep the leaf order exactly as the contract expects.
4. Form `stateProofMark = keccak256(firstMark || secondMark || harbourRoot || proofSalt)`.
5. Obtain the execution witness for the trace digest, then submit the assembled proof to `Theseus.unlock` from the player account.

The original solver used the chain's RPC history and the provided interfaces; the intermediate logs are part of the proof, not decorative clues. Replacing one byte, changing record order, or hashing textual hex instead of bytes changes the commitment.

## Evidence and limits

The archived transaction left `Theseus.opened() == true` and `Setup.isSolved() == true`. The flag was then recovered from setup initialization calldata. This is a historical chain result, not an offline proof that an arbitrary current deployment is vulnerable.

**Flag:** `zdk{An_aDDRe5S_lS_A_10CATLOn_No7_an_LD3NTl7y}`

**Lesson:** code disappearance does not erase the authenticated transaction history that committed to earlier state.
