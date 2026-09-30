# captcha · Web

**Core idea:** the server validated a proof and a check assignment separately, but failed to bind the proof to the check that produced it.

## Why the intended race could not fit

An attempt lasted ten seconds and required receipts for `desktop-cleanup`, `cable-box`, `tile-scramble`, and `race-lap`. Each assignment had its own `check_id` and live WebSocket `channel_id`. The race's valid local replay took 956 ticks. The server's `PHYSICALLY_IMPLAUSIBLE` delay for that replay exceeded the attempt window, so doing every check honestly did not yield four receipts in time.

The `/api/checks/<check_id>/accept` endpoint checked the destination check and channel, but did not require that the supplied opaque proof was issued *for that same check*. This made an easy-check proof transferable to the difficult race assignment.

## Working flow

Start all four checks concurrently in one session with distinct client IDs. Keep one WebSocket alive per assignment; without it, verification fails with `CHANNEL_SCOPE`. Verify an easy check, then send its proof to the race's accept endpoint with the race's path and channel. Verify the donor again and the two remaining easy checks, accepting each promptly. Proof issuance was session-rate-limited, so requests were spaced about 1.02 seconds apart before calling `/api/unlock`.

## Evidence and limits

The archived run reported that the desktop proof was accepted for the race, all four receipts were accepted, and unlock returned the flag. This was an authorized CTF service; the old instance is not assumed to exist now.

**Flag:** `zdk{533ms_hUMAn_enOU6H_70_m3}`

**Lesson:** an opaque proof is only meaningful if the verifier binds it to its issuing challenge, session, and channel.
