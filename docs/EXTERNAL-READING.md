# Independent solutions and further reading

This is a reading list, **not** an expansion of my solved-challenge count. The links lead to other players' original publications; none of their text, scripts, or flags has been copied here. Checked on 30 September 2026. Some writeups use different challenge instances and show different flag strings, so compare the method and its evidence rather than assuming byte-for-byte identity with my local artifacts.

## Compare methods on challenges in this archive

| Challenge | My account | Independent author | Interesting comparison |
|:--|:--|:--|:--|
| siren | [Nonce-prefix HNP](../crypto/siren/README.md) | [hax1ng](https://github.com/hax1ng/z0d1ak-ctf-qualifiers-2026/blob/main/crypto/siren/README.md) | Lattice construction and how candidate keys are checked. |
| THESEUS | [Historical commitments](../crypto/theseus/README.md) | [hax1ng](https://github.com/hax1ng/z0d1ak-ctf-qualifiers-2026/blob/main/crypto/theseus/README.md) | Dynamic discovery of addresses and event data rather than fixed instance values. |
| You Have Not Seen My Colors | [Blue-channel mask](../crypto/unseen-colors/README.md) | [Abdelkad3r](https://github.com/Abdelkad3r/z0d1akCTF-2026-Qualifiers/blob/master/Crypto/you-have-not-seen-my-colors/README.md) | PNG parsing and mask extraction without relying on an image editor. |
| Salvage Protocol | [VM-to-vault frame crossing](../pwn/salvage-protocol/README.md) | [hax1ng](https://github.com/hax1ng/z0d1ak-ctf-qualifiers-2026/blob/main/pwn/salvage-protocol/README.md) | Declared-length desynchronization and clearance timing. |
| House XIII | [Overlap and protected callback](../pwn/house-xiii/README.md) | [hax1ng](https://github.com/hax1ng/z0d1ak-ctf-qualifiers-2026/blob/main/pwn/house-xiii/README.md) | Signed cursor semantics, object aliasing, and the secret oracle. |
| Dead Current | [Checkpoint decryption](../forensics/dead-current/README.md) | [Abdelkad3r](https://github.com/Abdelkad3r/z0d1akCTF-2026-Qualifiers/blob/master/Forensics/dead-current/README.md) | How to locate the deleted record and master state in CRIU images. |

## Solved by others, not by this archive

These challenges are deliberately **not** in the main solution table. Finding another player's writeup does not turn an incomplete or untouched local investigation into my solve.

| Challenge | Independent writeup | Local status at publication |
|:--|:--|:--|
| Rewind | [Abdelkad3r](https://github.com/Abdelkad3r/z0d1akCTF-2026-Qualifiers/blob/master/Crypto/rewind/README.md) | No local solved record in the reviewed source. |
| Rewind Revenge | [Abdelkad3r](https://github.com/Abdelkad3r/z0d1akCTF-2026-Qualifiers/blob/master/Crypto/rewind-revenge/README.md) | No local solved record in the reviewed source. |
| Cyclotomic Echo | [hax1ng](https://github.com/hax1ng/z0d1ak-ctf-qualifiers-2026/blob/main/crypto/cyclotomic-echo/README.md) | Handout downloaded; marked untouched in my source audit. |

Read the evidence/limits section of my page first, then the linked author account. In particular, do not replace a local artifact-derived flag with a different player's instance output.
