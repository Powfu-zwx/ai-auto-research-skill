# Research record

Use the project's existing tracking system if it captures equivalent evidence. Otherwise create a campaign directory outside version-control rollback targets, such as `research/<campaign-id>/`. Keep sensitive or large data out of commits. Record stable references and hashes instead.

## Campaign contract

Record these fields in `contract.md` before the loop. Resolve execution-critical unknowns before launching experiments; a missing value is not permission to assume unlimited resources.

| Field | Meaning |
| --- | --- |
| Identity | Campaign ID, contract version, parent campaign if any |
| Question | Desired outcome, current bottleneck, competing explanations |
| Evaluation | Primary metric and direction, minimum useful effect, non-regression constraints, evaluator identity |
| Acceptance | Required success items, their verifier and evidence, artifact/input identity; distinguish research success from deliverable completeness |
| Data | Raw input provenance, immutable versions or hashes, development split, protected final-test arrangement |
| Scope | Allowed files and methods, protected files, allowed dependencies and services |
| Environment | Hardware, software versions, resource availability, accounting convention |
| Baseline | Starting revision, command, configuration, raw-output location, variability estimate |
| Budget | Total wall time, compute and money caps where applicable; per-run timeout; maximum attempts if useful |
| Validation | Screening rule, confirmation comparisons and replication plan, reserved confirmation budget |
| Reviews | Review cadence, invalid-run trigger, diminishing-return rule |
| Supervision | For long or delegated runs: responsible executor, job identity, expected progress signals, inspection cadence, recovery attempt limit |
| Stop | Target, budget boundary, validity failure handling, checkpoint location |

Record the effective limiting budget when the user gives only one cap. Count setup, evaluation, retries, confirmation, tool/API costs, and review overhead against the relevant total. Fixed training time alone is not total campaign time.

## Acceptance record

For each required criterion, record its ID, acceptance rule, verifier command or external check, candidate revision or artifact hash, relevant input and evaluator identities, evidence location, check time, status, and reason. Use `pending`, `passed`, `failed`, or `not-checkable`. Only `passed` satisfies an item. Missing evidence remains pending or not-checkable; it is never an assumed pass. This record is separate from an experiment's hypothesis evidence or promotion status.

Attach corrections and subsequent checks rather than overwriting the earlier result. Invalidate a pass when the artifact, evaluator, or relevant inputs change. At campaign close, record whether the research target was met, whether the requested deliverables were completed, and the stopping reason separately.

## Experiment ledger

Use an append-only JSONL file, database, or tracker. Keep original observations; attach corrections rather than silently replacing past results. Separate run validity, hypothesis evidence, and promotion decisions.

Each experiment needs:

- Experiment ID, timestamp with timezone, contract version, parent candidate ID.
- Hypothesis, competing explanation, expected observation, and refutation condition, written before execution.
- The decision this experiment could change and its estimated cost.
- Exact code revision or saved patch, configuration, command, seed or workload sample, environment and data identities.
- Evaluation identity, raw logs and outputs, primary score, constraint measurements, elapsed time, compute and money used where measurable.
- Run validity and reason; hypothesis evidence and reason; promotion decision and reason.
- Next implication, uncertainty, and whether confirmation is still required.

Allowed concepts, independent of serialization:

| Dimension | Values |
| --- | --- |
| Run validity | valid, invalid, failed, timed-out |
| Hypothesis evidence | supported, refuted, inconclusive; use inconclusive for unusable runs |
| Promotion | rejected, provisional, confirmed-incumbent, superseded |

A failed implementation does not refute the scientific hypothesis. A valid score improvement does not by itself establish the proposed mechanism.

## Strategy review

Record a review after the contracted trigger, not only at the end. Reference experiment IDs, update the competing explanations, and write the next experiment selection rationale. Track cumulative cost and the confirmation reserve. Distinguish a new idea from a previously tested idea with a new label.

## Resume checkpoint

Record the confirmed incumbent, provisional candidates, in-flight process or job IDs and ownership, completed attempt IDs, remaining budgets, protected data exposure, and next action. Include current acceptance evidence, unmet criteria, the last observed progress signal, and recovery attempts already spent. Before resuming, reconcile the ledger with actual processes and artifacts. Do not launch a duplicate job or reset the campaign's consumed budget. A missing result remains unknown until checked.

## Final evidence note

Include baseline and candidate measurements with comparable conditions, observations versus proposed explanation, validation performed and omitted, total resource use, stopping reason, and reproducible artifact references. If no candidate passes confirmation, retain the baseline and say so. Report a protected-test result as final evidence rather than an invitation to tune against that test.
