# Hydra FC · Forensics

**Core idea:** a provided QR image was the decisive artifact; an older notebook flag belonged to a rejected interpretation.

## Decoding the symbol

The 330×330 image resolved to a 25×25 grid, which is a version-2 QR code. Its format bits formed a valid BCH(15,5) codeword at Hamming distance zero, selecting error-correction level M and mask pattern 7. After unmasking and zigzag traversal, the data used byte mode with length 21, followed by a normal terminator and canonical padding. The decoded 21-character payload was the flag.

This structural check matters because an earlier 42-character candidate from a different theory could not fit the decoded byte length. The QR's actual capacity and mode fields refute that older claim without needing to guess at typography.

## Evidence and limits

The flag is supported by a deterministic local decode of the provided QR image. The archived audit records the corrected value; it does not rely on the stale notebook string.

**Flag:** `zdk{M355L_oR_rONaLdO}`

**Lesson:** validate the encoding format and payload length before elevating a visible or guessed string to a result.
