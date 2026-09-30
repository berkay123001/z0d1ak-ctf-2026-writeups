# You Have Not Seen My Colors · Crypto / visual encoding

**Core idea:** the useful signal was not a visible color; it was an exact channel predicate.

## Extracting the message

The supplied 100×100 RGB image looked noisy. Checking the blue component separately revealed a clean mask: a pixel belonged to the hidden drawing exactly when `B == 0`. Rendering those pixels black and all others white, then enlarging tenfold with nearest-neighbor interpolation, exposed geometric glyphs. Smooth scaling would blur the small strokes and make the script harder to identify.

The glyphs were written in Elian Script. They decode to the words `ZDK`, `MASTER`, `OF`, `CTF`. `ZDK` is the competition prefix, not part of the requested answer. The challenge wanted the remaining words in lowercase with underscores, so the submitted phrase was `master_of_ctf`.

## Why the format matters

The superficially plausible `zdk_master_of_ctf` was rejected by the private endpoint. The unprefixed phrase returned HTTP 200 with the flag. This distinction prevents a common writeup error: treating a decoded message and the final answer syntax as interchangeable.

**Flag:** `zdk{MaST3r_OF_COlORS_aND_CtF}`

**Lesson:** inspect exact per-channel predicates before trying arbitrary enhancement filters, and verify the answer format against the actual challenge oracle.
