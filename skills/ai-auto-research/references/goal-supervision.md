# Supervise unfinished research

Read this protocol for campaigns that span long jobs, interruptions, or authorized worker handoffs. Use it with the existing runner and [research record](research-record.md). It describes decisions for the current execution session, not a background service or a guarantee that an agent remains active after its host session ends.

## Separate execution from acceptance

The executor proposes and runs experiments. The acceptance step checks the contracted criteria against actual artifacts and measurements. In one session, the same agent can perform both steps using an independent harness; describe that arrangement honestly. A second agent's agreement alone does not validate a result or make shared evidence independent.

When delegation is already authorized and useful, give a worker the campaign goal, a bounded subproblem, allowed changes, the applicable criteria, evidence requirements, budget share, and checkpoint location. A subproblem's success does not establish campaign success. The campaign owner reconciles results and accepts the integrated final artifacts. This protocol neither requires nor authorizes creating workers, messaging other chats, or assigning a fixed agent hierarchy.

## Inspect meaningful progress

Use the host's completion notifications and job state first. For a long job without notifications, choose a bounded inspection cadence from expected runtime and cost. Back off while status is unchanged. Do not impose a universal polling interval or repeatedly narrate the same state.

Observe work through attributable evidence: process or scheduler state, new logs, completed experiment IDs, saved artifacts, or an expected progress milestone. Distinguish a quiet but active experiment from an inactive agent. CPU idleness, lack of chat messages, or a worker's absence alone is insufficient evidence to restart a GPU or remote job.

At completion, failure, unexpected idleness, or a missed milestone:

1. Reconcile the executor state, its job identity, the ledger, artifacts, acceptance record, and remaining budget. Verify process ownership before acting on it. If the job's state cannot be established, preserve the uncertainty and investigate before launching a duplicate.
2. Validate newly available results using the contracted checks. Verify their candidate and input identities, including any integration changes. Do not rerun the protected final test as an iterative repair check or disclose its contents to a worker choosing experiments.
3. If work is unfinished and no stopping condition applies, record the unmet criteria and select the next discriminating experiment, targeted repair, or recovery step. Provide the executor with concrete evidence and the remaining question rather than merely repeating a demand to finish.
4. Before a replacement or retry starts, establish that the earlier executor cannot continue conflicting work, or isolate its outputs and resources so only the current owner can update the candidate. Prefer the existing executor when it remains viable. Preserve logs and resumable artifacts; charge recovery against the same campaign budget and attempt limit.

If state is ambiguous or safe recovery requires a new permission or unavailable resource, checkpoint the campaign and identify the specific blocker. Do not manufacture a successful result or silently drop a criterion to make progress appear complete.

## Continue toward evidence, not endless activity

A failed acceptance check should change the next action. Repeating an identical attempt is justified only by a specific transient failure or the predeclared replication plan. Repeated substantive failures trigger the strategy review and contracted stopping rules.

Treat a completion claim as an input to acceptance. A passing intermediate experiment remains provisional until the campaign's confirmation requirements are met. An unavailable check prevents declaring the corresponding criterion satisfied, even if the worker reports success.

When the confirmed target is met or any campaign stopping condition applies, stop issuing new work. Reconcile owned active jobs through supported cancellation or bounded completion consistent with the contract. Do not terminate unrelated processes. Record canceled, unfinished, and unconfirmed work along with final resource use and a resumable checkpoint. Never report a budget stop as scientific success.

Conceptual source: [lidangzzz/goal-driven](https://github.com/lidangzzz/goal-driven/tree/c8e54ba3e9a4cf65df8fd9d92d0f9b231cab7f45). This protocol is original research-specific guidance; the source project's prompt template is not copied or installed.
