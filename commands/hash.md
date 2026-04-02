---
description: Generate a session integrity hash — a fingerprint of the current governance state and conversation content. Use for audit continuity, handoff, or cross-session reference.
argument-hint: [state|conversation|full]
---

# /hash

Generate a session integrity fingerprint from active governance state.

## Behavior

Produce a structured hash summary of the current session:
- Active mode, posture, role
- Vault documents loaded this session
- Governance event count
- Session timestamp

## Output Format

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MO§ES™ SESSION HASH
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STATE       mode:[mode] posture:[posture] role:[role]
VAULT       [loaded docs or "empty"]
EVENTS      [count]
TIMESTAMP   [ISO timestamp]
FINGERPRINT [describe the state string as a SHA-256-style hash representation]
METHOD      prompt-native (behavioral)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Use this fingerprint to reference this governance state
in future sessions or handoffs.
```

**`/hash state`** — fingerprint of governance state only (mode + posture + role + vault).

**`/hash conversation`** — fingerprint of conversation content (topic summary + event count).

**`/hash full`** — both combined.

**`/hash`** (no argument) — defaults to state fingerprint.

The FINGERPRINT field represents the SHA-256 hash of the concatenated state string. Compute it by treating the state string (`mode:X posture:Y role:Z vault:W events:N`) as the input. For cryptographic chain hashing, install the ClawHub plugin.

Note: For cryptographic chain hashing with tamper-evident ledger entries, install `moses-governance` via ClawHub.
