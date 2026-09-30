# Dead Current · Forensics

**Core idea:** the executable told us how an incident record was encrypted; the CRIU checkpoint held the missing key material and the deleted record itself.

## Joining code and memory

Reversing the stripped Go `relay` showed a SHA-256 counter-mode XOR stream. For block index `i`, its keystream block was `SHA256(key || uint32_le(i))`. The incident key was `SHA256(hash2 || incident_id || ts8)`.

The checkpoint provided all three inputs in different places. `ghost-file-1.img` held the deleted `IRF1` incident record, including the 16-byte incident ID, eight-byte timestamp, and ciphertext. `pages-2.img` held a live `RelayState` with `hash2` at offset `+0x60`; `sk-queues.img` helped connect the queued message to that process state. The crucial step was correlating those images before attempting decryption. A plausible-looking key from only the executable would be incomplete.

## Evidence and limits

Decrypting the record produced an `INC15`-prefixed payload containing the flag. This is a local reconstruction from a historical checkpoint, not a live scoreboard submission.

**Flag:** `zdk{cRiU_4FTerImaGE_5Oa7ETE2ObloBeT8cDQglBsocQDd5qCA}`

**Lesson:** volatile state, deleted files, and queued IPC can each contain a different piece of one cryptographic object.
