# genie · Misc / Game Boy reversing

**Core idea:** the ROM accepted a large gold value only when three related memory words changed atomically on the right frame. That bypassed most gameplay and exposed a small state-search problem.

## Authenticated gold

The public gold word lived at `C100`; two check words at `C102` and `C104` authenticated it against a 16-bit session seed. Writing gold alone failed. The solver derived both companion words from the seed and selected `G = 0x1388` (5000 gold), then applied all three writes on frame 120. START on frame 121 reached floor 9 because the gold threshold was checked before the ordinary location/gate path.

This is a timing constraint as well as a value constraint: correct words on the wrong frame do not reproduce the state transition.

## Nine echoes

At floor 9, pressing A armed an echo action, and a neutral following frame allowed a write to `C300` to choose one of three operations. Reversing the ROM's state update and running breadth-first search found the nine-operation route:

```text
2, 0, 2, 1, 2, 2, 0, 2, 1
```

The writes occurred on alternating frames 124 through 140. The final state `C200=120E` hashed to `B14A`, the vault's target. The complete movie used the allowed twelve codes: three authenticated-gold writes and nine echo writes. Ten additional neutral frames let the win text finish rendering.

## Evidence and limits

The archived remote session printed `WIN` and the flag. The supplied local test suite checks the deterministic movie construction, but the public archive does not copy the ROM or solver.

**Flag:** `zdk{THrE3_worD5_ninE_eChOEs_On3_0p3N_s3al}`
