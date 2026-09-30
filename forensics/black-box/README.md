# Black Box · Forensics

**Core idea:** parse the recording as fixed-width telemetry packets, reorder one packet class, then undo a short XOR mask.

## Decoding

The binary file was a sequence of 16-byte records:

```text
"BX" (2 bytes) | type (1) | sequence (3, big-endian) | payload (10)
```

Only type-3 records contributed to the hidden text. After filtering, the three-byte sequence number—not file position—determined order. Each ten-byte payload was XORed with alternating bytes `de ad`, and trailing zero padding was removed before concatenation. Interpreting the complete file as one XOR stream, or sorting the sequence as little-endian, destroys the message.

## Evidence and limits

The local solver reads the original `blackbox.bin`, performs the record selection and decoding, and prints the recovered flag. This is an artifact-derived result; no live service is needed.

**Flag:** `zdk{31EMENtAry_BLn4Ry_pARsLN6_m4St3r}`

**Lesson:** establish record boundaries and ordering before applying a cipher transform.
