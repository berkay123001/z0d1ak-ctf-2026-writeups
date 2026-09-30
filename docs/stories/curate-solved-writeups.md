# Story: Publish the solved z0d1ak 2026 archive

## Scope

Create an English, public, solution-only archive from the private z0d1ak working tree. Preserve precise evidence labels, avoid unsolved/decoy material, and do not mutate the source tree.

## Acceptance checklist

- [x] Review the final source audit rather than classifying by filenames alone.
- [x] Separate 17 recorded solutions from partial, unsolved, untouched, decoy, and local-test entries.
- [x] Give each selected challenge an English method, result, and evidence limit.
- [x] Keep raw private notes, credentials, binaries, and unreviewed scripts out of the publication tree.
- [x] Attribute independent writeups in a separate reading guide; do not count external-only cryptography solves as mine.
- [x] Validate local links, markdown hygiene, and source/result correspondence.
- [x] Run the inherited npm quality gates and record applicability.
- [x] Create a separate public GitHub repository and confirm the published tree.

## File list

- `README.md` — category index and verification legend.
- `docs/PROVENANCE.md` — source-to-writeup evidence ledger and exclusion rationale.
- `docs/EXTERNAL-READING.md` — attributed third-party reading, separate from the solved index.
- `docs/stories/curate-solved-writeups.md` — publication checklist and checks.
- `crypto/*/README.md`, `pwn/*/README.md`, `web/*/README.md`, `misc/*/README.md`, `osint/*/README.md`, `forensics/*/README.md`, `rev/*/README.md` — selected challenge explanations.

## Checks

- 17 challenge pages match the 17 flag entries in the final private-source audit.
- 25 relative Markdown links resolved; all nine external GitHub writeup links returned existing files.
- The original local `battle` binary returned the recorded rival-battle flag for the 14-command route; the Black Box and husk solvers independently printed their recorded flags. The recovered Ghost in the GPU image visibly contains its flag.
- Publication tree contains only Markdown; secret-pattern scan found no keys or credentials.
- `npm run lint`, `npm run typecheck`, and `npm test` were attempted. Each reported `Missing script`, because this documentation-only repository has no `package.json` or npm scripts. The inherited `.aios-core/constitution.md` file is absent in the home workspace.
