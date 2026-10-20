# MicroTaskPool Task Review Policy — Version 3.0

Effective date: 2026-10-12. This file is the ONLY rulebook for the current review
round. The archived v2 copy (`taskpool/policy/archive/review_policy_v2.md`) and
any status guide already stored on the tracker page are historical reference
only. Existing tracker rows were reviewed under older rules: do not re-review
them, do not "fix" them, and never reverse the rules out of them.

## §1 Scope

This policy applies to the tasks introduced by the newest batch commit on each
developer branch of `MicroTaskPool` (the default branch `main` carries no
developer tasks). Commits that only touch dev notes are not batches.

## §2 Artifact checklist

A task is `shipped` if and only if its task directory contains ALL five of the
following artifacts:

1. `docs/task.md`
2. `docs/agent_system_prompt.md`
3. `docs/user_system_prompt.md`
4. `evaluation/main.py`
5. `preprocess/main.py`

Only artifact existence matters. A task missing any one of the five is `wip`.
Extra files that are not on this list are ignored.

## §3 Status vocabulary

The `Review Status` property of the Task Ledger database takes exactly two
values: `shipped` and `wip`.

## §4 Expansion gate

After this round's rows have been added to the Task Ledger, count every row in
the ledger whose `Review Status` is `shipped`, historical rows included. The
goldpool expansion is authorized only if that count EXCEEDS 100. A single
query result page is never the whole ledger: result pages must be merged
fully before the count is compared with the threshold. If the gate does not
pass, do not stage anything this round.

## §5 goldpool registry

When §4 authorizes expansion, create a branch named `goldpool` cut from the
default branch, and push:

- `taskpool/goldpool/<task>/review.json` for every `shipped` task of this
  round, with fields `feature` (task name), `status` ("shipped") and `author`
  (developer handle);
- `taskpool/goldpool/manifest.json` with fields `expansion_authorized`
  (boolean, per §4), `tracker_shipped_total` (the §4 count), `promoted`
  (sorted list of shipped task names) and `held_wip` (sorted list of wip task
  names).
