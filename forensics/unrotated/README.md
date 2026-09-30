# Unrotated · Forensics

**Core idea:** a supposedly retired integration token still worked; its audit trail connected separate logs into one seven-field incident report.

## Reconstructing the incident

The challenge evidence contained collaboration audit events, changes, runner jobs, a service identity, and a console endpoint. The significant path passed through an accepted integration-token session into an operations runner event. The answer was not a single recovered secret: the remote reporter expected seven fields in order—archive, timestamp, operator, change reference, runner job, service endpoint, and console.

The recorded sequence was:

```text
depth-chart-archive
2026-06-11T09:26:41Z
mara.venn
CHG-2147
OR-7312
BLUEFIN@203.0.113.86:8448
console-cpt-03
```

Those values were submitted to successive `report[1]` through `report[7]` prompts. Preserving the exact timestamp and identifiers mattered; a vaguely correct narrative was not accepted by an exact-field checker.

## Evidence and limits

The private audit records the live flag and preserves a seven-answer TLS client. The service is retired, and this archive does not publish the underlying logs or token. The historical result is not evidence that any real-world service currently accepts that token.

**Flag:** `zdk{A_Hum4N_r34d5_7HE_WAke_no7_tHe_LabEL5}`
