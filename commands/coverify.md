---
description: Verify commitment conservation between two texts. Extracts commitment kernels, scores similarity, detects ghost tokens. Tests whether meaning survived transformation — or names what leaked.
argument-hint: "[original text] → [transformed text]"
---

# /coverify

Test the Commitment Conservation Law: C(T(S)) = C(S).

Commitment — the irreducible meaning in a signal — is conserved under transformation when enforcement is active. It leaks when enforcement is absent. CoVerify tests whether it held.

## Behavior

When invoked with two texts separated by `→`:

1. **Extract** commitment kernel from each: tokens carrying `must`, `shall`, `never`, `always`, `require`, `guarantee`, `ensure`, and the sentences that carry them.

2. **Score** Jaccard similarity between the two kernels.

3. **Detect ghost tokens** — commitment tokens present in the original, absent in the transformed version.

4. **Classify cascade risk:**
   - `HIGH` — modal/enforcement anchor lost (`must` → `should`, `shall never` → `can`)
   - `MEDIUM` — peripheral tokens leaked, anchors intact
   - `NONE` — no leakage

## Output Format

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MO§ES™ COVERIFY — COMMITMENT CHECK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ORIGINAL KERNEL    [extracted tokens]
TRANSFORMED KERNEL [extracted tokens]
JACCARD            [0.0 – 1.0]
VERDICT            CONSERVED / VARIANCE / DIVERGED
GHOST TOKENS       [leaked tokens or "none"]
CASCADE RISK       NONE / MEDIUM / HIGH
CASCADE NOTE       [explanation if risk present]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Verdicts:**
- `CONSERVED` — Jaccard ≥ 0.8, commitment kernel survived
- `VARIANCE` — same input, Jaccard < 0.8 — model extraction differs, not a leak
- `DIVERGED` — Jaccard < 0.8 — commitment leaked or inputs genuinely different

If no `→` separator is found, respond: "Usage: /coverify [original text] → [transformed text]"

Note: For automated cross-model structural classification, install `coverify` via ClawHub.
