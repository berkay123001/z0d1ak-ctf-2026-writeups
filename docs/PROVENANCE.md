# Publication and evidence ledger

Source: the private local `Siber/SiberHackaton` working repository, reviewed against its `README.md` snapshot and selected challenge files on 30 September 2026. That source remains private and unchanged. Paths below are provenance identifiers, **not** published files or public links. This ledger explains the **included pages**; it does not claim to inventory every challenge I solved or every historical writeup.

| Writeup | Private source evidence | Basis of result |
|:--|:--|:--|
| THESEUS | `NOTES.md`, `challenges/crypto/crypto_theseus/solve.py` | `Theseus.opened()` and `Setup.isSolved()` true; setup calldata yielded flag |
| siren | `challenges/crypto/siren/SOLVED.md`, `solve.py` | Live service flag; recorded platform acceptance |
| You Have Not Seen My Colors | `challenges/crypto/unseen-colors/SOLVED.md`, challenge image | Private endpoint returned flag for decoded phrase |
| Salvage Protocol | `NOTES.md`, `challenges/pwn/exploit_salvage.py` | Live flag via VM/vault path |
| rapture | `README.md`, `NOTES.md`, `challenges/pwn/exploit_rapture_working.py` | Archived live flag and exploit record |
| House XIII | `README.md`, `NOTES.md`, `challenges/pwn/exploit_house13.py` | Archived live flag and exploit record |
| captcha | `challenges/webex/captcha/SOLVED.md`, `live-solve.mjs` | Successful unlock response with flag |
| genie | `challenges/misc/genie/SOLVED.md`, `genie_solver.py` | Remote `WIN` and flag response |
| Uncharted Tides | `README.md`, `NOTES.md`, `challenges/osint/uncharted-tides/` | Archived solved result and image crops; accepted submission transcript not retained |
| Black Box | `challenges/Forensics/black-box/solve.py`, `blackbox.bin` | Local packet decode |
| Ghost in the GPU | `challenges/Forensics/ghost-in-the-gpu/solve.py`, `recovered_image.png` | Flag visually present in reconstructed tensor image |
| Unrotated | `README.md`, `challenges/Forensics/forensics_unrotated/solve.py` | Archived live flag; seven-field answer script |
| Dead Current | `challenges/Forensics/forensics_dead-current/SOLVED.md`, `solve.py` | Decrypted incident payload from checkpoint |
| Layer Eight | `README.md`, `challenges/Forensics/forensics_layer_eight/app-image/` | Corrected flag via authenticated AES-GCM envelope |
| Hydra FC | `README.md`, `challenges/Forensics/forensics_hydra_fc/qr.png` | Version-2 QR payload with valid format/data structure |
| husk | `README.md`, `challenges/rev/rev_husk/solve.py` | Binary-derived reverse transformation |
| rival-battle | `README.md`, `NOTES.md`, `challenges/rev/rev_rival_battle/{sim.py,battle,trainer.sav}` | Archived route replayed on original local binary; it returned flag |

## Exclusions that matter

The reviewed source contains files named `SOLVED.md` that are **not** solved-result evidence. `rev_pekpek_stadium_64` has a rejected compressed-stream artifact; `forensics_dead-letter-wake` has an unverified hard-coded candidate; `forensics_17600-leagues`, `webex/both-cups`, and `crypto_sealed-cascade` are marked incomplete there. `Cyclotomic Echo` is marked downloaded-only in that snapshot. The separate ASIS 2025 RandomJS copies contain a bundled local test flag, not a verified live competition flag. None of these were promoted into this writeup collection. These labels describe the reviewed files, not work that may exist elsewhere.

This edition publishes explanatory writeups only. It does not copy challenge binaries, captured traffic, recovered credentials, personal tokens, third-party code, or the full private notebook. A command shown in a writeup is explanatory and may require historical challenge files or a retired instance.
