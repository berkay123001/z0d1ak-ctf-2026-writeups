# rival-battle · Reverse engineering

**Core idea:** a seemingly open-ended battle was deterministic. Reproduce its state transitions, then search for a short action sequence that reaches the exact final-state hash.

## Modeling the game

The battle binary mixed party HP, rival HP, active creature, turn counter, status effects, and a small RNG into its state. Every player command advanced those values in a fixed order. A Python model reproduced that order, including 16/32-bit integer wraparound; a C search version made the 14-turn exploration practical. The target state hash was `0x9218A78C`.

The successful commands, one per turn, were:

```text
2 3 4 6 4 2 7 2 1 6 4 2 4 2
```

Do not send the fourteen digits as one line: the binary reads one menu command at each prompt. The route's success is about the complete sequence and resulting state hash, not merely defeating all rival creatures.

## Evidence and limits

During this publication audit I fed those fourteen commands, one per line, to the original local `battle` binary with its `trainer.sav`. It printed that the route was perfect and returned the flag. The historical notebook also records the same route.

**Flag:** `zdk{59uLr71e_ls_tH3_b3ST_stAR7ER}`

**Lesson:** exact simulation plus bounded search is often stronger than guessing an intended strategy from the game's theme.
