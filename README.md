<div align="center">

# z0d1ak CTF Qualifiers 2026 · Writeups

**Seventeen recorded solutions, with the method and the evidence kept together.**

</div>

This is a curated English edition of my z0d1ak CTF Qualifiers 2026 work. It is not a mirror of the private working repository. Only the 17 challenges recorded as solved in its final audit are listed here; partial exploits, rejected flag candidates, downloaded-only challenges, credentials, and raw working directories are absent. Some results can be checked against local artifacts, while others rely on archived live-session records. Each page says which.

| Category | Challenge | Key idea | Evidence |
|:--|:--|:--|:--|
| Crypto | [THESEUS](crypto/theseus/README.md) | Rebuild historical EVM commitments | Solved setup state and recovered flag |
| Crypto | [siren](crypto/siren/README.md) | ECDSA nonce leakage → HNP lattice | Live flag and accepted submission |
| Crypto | [You Have Not Seen My Colors](crypto/unseen-colors/README.md) | Blue-channel mask → Elian script | Live endpoint returned flag |
| Pwn | [Salvage Protocol](pwn/salvage-protocol/README.md) | VM-to-vault request smuggling | Live flag |
| Pwn | [rapture](pwn/rapture/README.md) | Snapshot alias → UAF → stack ROP | Archived live flag |
| Pwn | [House XIII](pwn/house-xiii/README.md) | Stale object → protected call target | Archived live flag |
| Web | [captcha](web/captcha/README.md) | Proof not bound to check identity | Live unlock response |
| Misc | [genie](misc/genie/README.md) | Game Boy frame timing and echo search | Live win response |
| OSINT | [Uncharted Tides](osint/uncharted-tides/README.md) | Landmark identification from crops | Archived result; no transcript retained |
| Forensics | [Black Box](forensics/black-box/README.md) | Packet reorder and XOR | Local artifact decode |
| Forensics | [Ghost in the GPU](forensics/ghost-in-the-gpu/README.md) | Restore an NCHW float16 image | Flag legible in recovered image |
| Forensics | [Unrotated](forensics/unrotated/README.md) | Reconstruct seven incident fields | Archived live flag |
| Forensics | [Dead Current](forensics/dead-current/README.md) | CRIU memory + SHA-256 counter stream | Local decrypted payload |
| Forensics | [Layer Eight](forensics/layer-eight/README.md) | Recover a whiteouted OCI secret | AES-GCM tag verified |
| Forensics | [Hydra FC](forensics/hydra-fc/README.md) | Read a version-2 QR payload | Exact QR decode |
| Reverse | [husk](rev/husk/README.md) | Invert RC4 target and six rounds | Local binary-derived flag |
| Reverse | [rival-battle](rev/rival-battle/README.md) | Deterministic simulator and DFS | Original local binary returned flag |

## How to read these

Start with the failure or observation that made the challenge tractable, then follow the chain to the flag. The **Evidence and limits** section is as important as the exploit: a local decode is not a scoreboard acceptance, and an archived live result is not a promise that a retired service is still available. Flags are spoiler material and appear near the end of each page.

The [provenance ledger](docs/PROVENANCE.md) records which private source files support each writeup without publishing those files. [Independent reading](docs/EXTERNAL-READING.md) links other authors' solutions, including cryptography challenges I did **not** solve, in a separate section. No third-party writeup or solver was copied into this repository. These are historical CTF examples, not tests of current public services.
