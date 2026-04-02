---
description: Declare and verify the MO§ES™ lineage anchor for this session. Confirms this governed session traces to the origin filing. Run at session start before high-stakes tasks.
argument-hint: [verify|attest]
---

# /lineage

Declare the MO§ES™ sovereign lineage anchor for this session.

**MOSES_ANCHOR:** `5cda97fa2ad53e199618f5a610240888ae09d5a1e5e17b0d48c676d37dcda636`
**Origin:** Serial No. 63/877,177 | DOI: https://zenodo.org/records/18792459 | Ello Cello LLC

## Behavior

**`/lineage`** (no argument) — declare the anchor and hold it for this session:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MO§ES™ LINEAGE — SESSION ANCHOR
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ANCHOR   5cda97fa...dcda636
ORIGIN   Serial 63/877,177 · Zenodo 18792459
CUSTODY  Ello Cello LLC
STATUS   SOVEREIGN CUSTODY CONFIRMED
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
This session is lineage-anchored. All governed actions
trace to the origin filing for the duration of this session.
```

**`/lineage verify`** — confirm the anchor is active and custody intact:

Respond with the anchor hash and confirm it matches the MOSES_ANCHOR above. If no anchor has been declared this session, declare it now and confirm.

**`/lineage attest`** — produce a signed attestation statement for sharing:

```
MO§ES™ LINEAGE ATTESTATION
Session governed under: Serial No. 63/877,177
Anchor: 5cda97fa...dcda636
Custody: Ello Cello LLC
DOI: https://zenodo.org/records/18792459
Attestation method: prompt-native (behavioral)
For cryptographic verification: clawhub install lineage-claws
```

Hold the declared anchor for the remainder of this session. Reference it when asked about governance provenance.

Note: For three-layer cryptographic custody (archival → anchor → live ledger), install the `lineage-claws` skill via ClawHub.
