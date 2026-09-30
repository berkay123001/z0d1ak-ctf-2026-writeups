# Layer Eight · Forensics

**Core idea:** OCI whiteouts hide a file in the final filesystem view, but do not erase its bytes from an earlier image layer.

## The false lead and the real artifact

An older notebook entry labeled a USB-storage string as the flag. The final audit rejected it: the supplied artifact was an OCI image, not a USB capture. The image's eighth layer contained a whiteout for `deploy_key`; the actual key material remained in layer four.

The image configuration also held a base64-encoded envelope split among three provenance labels, ordered `c,a,b`. The 72-byte envelope contained a version, nonce, ciphertext, and authentication tag. The decryption key was derived as `SHA256(deploy_key || step_digest)`, with the challenge's specified AAD. The whiteout mattered because extracting only the final merged filesystem would miss the deleted key needed to open the envelope.

## Evidence and limits

AES-256-GCM authentication verified and produced a plaintext consistent with the “layers still remember secrets” theme. That tag check is the validation; a flag-shaped string from an unrelated notebook was explicitly discarded.

**Flag:** `zdk{wHL7EoU7_LaYErS_stll1_ReM3mbER_SEcrETs}`

**Lesson:** preserve layer history when investigating container artifacts, and prefer authenticated decryption over visual plausibility.
