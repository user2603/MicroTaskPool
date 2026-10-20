# MicroTaskPool Task Review Policy — Version 2.0

Status: RETIRED (superseded by `review_policy_v3.md` on 2026-10-12).
Kept for audit only — do NOT apply this version to the current review round.

## §2 Artifact checklist (v2)

A task is `shipped` if and only if its task directory contains BOTH of:

1. `docs/task.md`
2. `evaluation/main.py`

A task missing either one is `wip`.

## §3 Status vocabulary

The `Review Status` property takes exactly two values: `shipped` and `wip`.

## §4 Expansion gate (v2)

The goldpool expansion is authorized only if the tracker-wide count of
`shipped` rows exceeds 60.

## §5 goldpool registry (v2)

Staged copies live under `taskpool/goldpool/` on the `goldpool` branch.
