# Uncharted Tides · OSINT

**Core idea:** identify a specific building from visual geometry before trying to guess the requested place-name format.

## Search path

The challenge photograph contained more context than the target itself. The private work directory preserves a progression of crops: a broad scene, an isolated church facade, nearby village details, and enlarged views for visual search. Isolating the facade reduced the noise from landscape and fencing. The resulting landmark match was **Our Lady of Miracles Church** in **Badem**.

The final answer combined the building name and locality in the challenge's lowercase, underscore-and-hyphen format. That formatting step matters: an otherwise correct landmark can still fail an exact-string flag check.

## Evidence and limits

The final private audit and notebook record this as solved and preserve the derived flag plus image crops. A raw accepted-submission response or screenshot was not retained in the source material reviewed here, so this page reports an **archived result**, not a newly verified live oracle.

**Flag (archived record):** `zdk{our_lady_of_miracles_church-badem}`

**Lesson:** retain the image evidence and the exact answer format separately; a location hypothesis should not silently become a claim of live acceptance.
