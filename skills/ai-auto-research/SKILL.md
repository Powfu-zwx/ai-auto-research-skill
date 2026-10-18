---
name: ai-auto-research
description: Plan and run bounded autonomous research through falsifiable hypotheses, executable experiments, independent evaluation, and evidence-based strategy reviews. Use for iterative ML, algorithm, or systems experiments and for improving an existing autoresearch loop; not for literature-only summaries or ordinary one-off fixes.
---

# AI Auto Research

Turn an outcome into a reproducible research campaign. Optimize both the result and what the experiments establish. A negative or inconclusive result is a legitimate outcome.

## Establish the research contract

Inspect the project's instructions, existing experiment runner, raw data, evaluation code, available tools, and prior results before proposing infrastructure. Reuse the existing workflow when it can supply reliable evidence.

Write a short campaign contract using [references/research-record.md](references/research-record.md). Record:

- The desired outcome and the scientific or engineering question behind it.
- The primary metric, direction, baseline, minimum useful improvement, and constraints that must not regress.
- Allowed changes, protected evaluation and data boundaries, environment, and reproducibility requirements.
- Total time, compute and spending limits; per-experiment timeout; resources reserved for confirmation; stopping and strategy-review conditions.
- How the agent will measure results independently of its own written judgment.

Use already authorized resources and existing project limits. If no campaign budget is established, do read-only inspection and propose a bounded pilot before starting an experiment loop. Ask only for missing decisions that affect validity, scope, or spending. Do not repeatedly request permission for experiments inside an established contract.

If the desired outcome has no credible observable test, design a measurement pilot first. Do not disguise an unvalidated proxy score as the outcome.

Record hashes or immutable versions of the evaluator, data splits, starting code, and relevant dependencies. Separate development data from a protected final test. The agent must not use final-test examples or scores to guide candidate selection. An external evaluator may return the final result after selection; if only development evaluation is available, label the conclusion accordingly.

## Make ambition operational

Apply these lenses when forming or revising the research strategy, rather than mechanically expanding every experiment:

- **Speed:** Reduce avoidable experiment overhead while preserving comparable measurements. Count completed, valid experiments rather than launches.
- **Altitude:** Identify the bottleneck between the current task and the desired outcome. Choose experiments that distinguish competing explanations of that bottleneck. Keep the current evaluator fixed; a proposed objective change belongs in a new campaign.
- **Depth:** Start with raw observations and expert methods. State what evidence would refute each explanation. Distinguish an improved score, an explanation of its cause, and a claim that it generalizes.
- **Range:** Borrow a concrete method from another field when it could change the decision: statistical experimental design, compiler profiling, numerical analysis, causal inference, or another relevant method. Explain its expected contribution. Simulated professional personas are not independent expertise or evidence.

Use difficult goals as exploration targets. Never use confidence, persistence, or the instruction that something must be possible as evidence.

## Establish a credible baseline

Run the unmodified baseline with the intended command and environment. Save raw output and resource use. Check that evaluation executes the real workload, fails on invalid output, and measures the intended objective. Do not launch a search against a broken baseline.

Estimate variability at a cost appropriate to the claim. For stochastic or noisy workloads, use repeat runs or paired comparisons and record seeds or workload samples. Choose the replication plan before seeing candidate scores. A single inexpensive run can screen ideas, but it cannot establish a reliable improvement.

If the environment cannot execute the experiment, deliver the contract and executable plan with the limitation stated. Do not invent measurements.

## Run an evidence-producing loop

For each experiment:

1. **Choose a hypothesis.** Read the ledger and select an unresolved question. Record the mechanism, alternatives, expected observation, refutation condition, expected cost, and why this experiment is worth doing next. Prefer a small discriminating experiment. An explicitly exploratory combination is acceptable, but requires later ablation before causal claims.
2. **Save a reproducible candidate.** Use an isolated branch, directory, or the project's existing mechanism. Preserve unrelated user changes. Record the exact patch or revision, command, configuration, data identity, seed, environment, and parent candidate before execution.
3. **Execute within limits.** Enforce the timeout and resource bounds. Include failed runs and repair attempts in the campaign budget. Stop an invalid or runaway experiment. Do not install packages or use external services outside the established scope.
4. **Evaluate independently.** Use the protected harness and raw outputs, not the model's assessment of its own work. Verify comparable workload, elapsed-time definition, hardware, precision, data and resource accounting. Treat NaN, missing observations, changed evaluation, or violated constraints as invalid rather than a winning score.
5. **Classify the evidence.** Record supported, refuted, or inconclusive for the hypothesis; record invalid for an unusable run. Small or noisy score differences remain inconclusive. Preserve plausible alternative explanations.
6. **Decide and preserve.** Mark a promising screen as provisional. Promote to the incumbent only after the contracted confirmation and constraint checks pass. Revert or isolate losing code without deleting its logs, patch, or findings. Keep informative failures available for future decisions.

Track screening candidates separately from the confirmed incumbent. If budget ends before confirmation, report the candidate as unconfirmed. Never silently promote it to a proven improvement.

Read [references/research-record.md](references/research-record.md) when creating or resuming records. When working specifically in Karpathy's autoresearch, also read [references/karpathy-autoresearch.md](references/karpathy-autoresearch.md).

## Review the strategy

At the contracted review interval, after repeated invalid runs, or when progress stalls, leave the execution loop long enough to review the evidence:

- Which explanations gained or lost support? Which important uncertainty remains?
- Are we repeatedly testing the same idea, searching too narrowly, or optimizing a weak proxy?
- Which next experiment best balances useful improvement, uncertainty reduction, and remaining cost?
- Would an alternative method distinguish the explanations more cheaply?
- Are apparent gains explained by noise, changed workload, evaluation leakage, or resource differences?

Update the hypothesis queue and rationale. Preserve exploratory branches that answer different questions rather than discarding everything with a temporarily worse score. Do not automatically rerun failed ideas without a changed mechanism or new evidence.

The review may change search strategy inside the contract. It must not silently change the metric, data splits, allowed scope, or budget. If those need to change, record the reason and establish a new contract version before further experiments. Changing evaluation creates a new comparison series with a new baseline.

## Confirm and stop

Reserve enough budget to compare the selected candidate with the baseline or incumbent under the predeclared confirmation plan. Match precision of the claim to the number and independence of observations. Report effect size and uncertainty when meaningful; do not invent statistical significance.

Repeated development-set search can overfit. Use a protected final test only after selection, without feeding its results back into this campaign. If that test informs more tuning, treat it as development data and require a fresh protected test for a generalization claim.

Stop at the first applicable contract boundary: exhausted budget, confirmed target, explicit user stop, unresolved validity failure, unavailable required resource, or the agreed diminishing-return rule. Leave a resumable checkpoint. The skill does not create background jobs, schedules, or an indefinite execution entitlement.

## Report the evidence

Follow the user's requested format and language. State the changed files or artifacts, then validation run and not run. Report the baseline, confirmed result, remaining provisional candidates, resource use, and reason for stopping. Link the exact commands, raw results, revisions, and relevant external sources.

Separate observations from explanations and generalization claims. Make unresolved uncertainty explicit. Do not call a method novel without an appropriate literature check, or claim broad generalization from a single benchmark.

Keep research artifacts local unless sharing is authorized. Do not include credentials or private data in a public report. The skill does not authorize publishing, deploying, messaging other chats, or spawning additional agents; follow the user's scope and the host's permissions.
