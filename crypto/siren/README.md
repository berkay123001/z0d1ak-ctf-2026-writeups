# siren · Crypto

**Core idea:** a few known bits of each ECDSA nonce turn many signatures into a Hidden Number Problem.

## Where the entropy went

The service signed chosen messages with secp256k1 ECDSA. Its nonce had a public, message-derived 10-bit prefix and a random 246-bit suffix. The prefix did not reveal a full nonce, and one signature was not enough. Across 48 signatures, however, the same private key had to satisfy a family of modular relations.

For each signature `(r, s)` on message hash `z`, ECDSA gives `s·k ≡ z + r·d (mod n)`. Write the nonce as `k = prefix·2^246 + low`, where `0 ≤ low < 2^246`. Substitution gives `s·low − r·d ≡ z − s·prefix·2^246 (mod n)`. The right-hand side is known for each sample, while every `low` is bounded. Rewriting those constraints for many samples produces an HNP lattice. LLL reduction, followed by a closest-vector step, yielded the private key candidate.

## From candidate to unlock

1. Request 48 signatures on chosen messages and retain each message, signature, and public prefix.
2. Build the modular lattice with the correct curve order and nonce-bit alignment; a one-bit shift changes the problem.
3. Check the recovered private scalar against the service's advertised public point. This is a much stronger check than seeing a plausible hex number.
4. Sign the forbidden message `unlock:release-the-tide` locally and send the valid signature to the challenge service.

## Evidence and limits

The private-key recovery was checked locally in five of five probabilistic self-tests at 48 samples. The archived live TLS service returned the flag, and the platform submission was recorded as accepted. The old endpoint should not be expected to remain available.

**Flag:** `zdk{4_few_BlTS_PeR_Slgn4tURe_sLnKs_TH3_kEy}`

**Lesson:** partially predictable nonces leak the long-term signing key even when no complete nonce is reused.
