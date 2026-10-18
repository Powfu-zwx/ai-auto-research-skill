# Adapter for Karpathy autoresearch

Read the checked-out repository's `README.md` and `program.md` first. Its current instructions are authoritative for that run's editable files, metrics, dependencies, rollback rules, and launch commands. This adapter adds research reasoning; it does not grant permission to alter protected files or replace repository instructions.

The upstream design uses a small LLM training setup, bounded training runs, a protected evaluator, and a keep-or-discard loop. Verify the current checkout rather than assuming upstream details have remained unchanged.

## Add a campaign around the existing loop

Use the repository's runner and result tracking. Store additional research notes outside its rollback targets, following [research-record.md](research-record.md). Preserve the upstream results format if another tool consumes it.

Before starting, establish total campaign limits with the user. A per-training-run time limit is not a total budget. Reuse an existing finite limit if one is already supplied. If repository instructions require indefinite execution and the user has not established a compatible finite campaign, resolve that conflict before launching; inspection and planning can proceed.

Keep fixed evaluation and data handling intact. If the checkout permits edits only to `train.py`, put implementation changes there and keep notes outside tracked implementation files. Do not edit `prepare.py`, the evaluator, or package dependencies to make a proposed experiment pass.

If the repository's automatic rule keeps every development-score improvement, treat that saved revision as a screening candidate in the research record. Track the confirmed incumbent separately. Do not silently change the repository's keep/discard machinery or claim that an automatically kept revision has passed independent confirmation.

## Example research question

Question: Under this repository's fixed training budget and hardware, does throughput or learning efficiency currently limit the development metric?

Start with the unchanged baseline and record development score, useful training work completed, elapsed-time accounting, and peak memory where instrumentation is available and permitted. Check what the repository actually measures before interpreting these values.

One hypothesis could be: a permitted optimization to the training implementation increases useful training work under the same time budget without changing the objective or data distribution, producing a reproducible score improvement.

Choose a small implementation change, predict the throughput and score effects, and state what would contradict that explanation. Compare under matched hardware and seeds where practical. A faster step without an improved score is evidence about throughput, not proof of a better model. A worse short run does not rule out benefits at longer budgets.

If the score improves, repeat the comparison within the confirmation reserve. For a multi-part change, separate the parts before claiming which mechanism caused the gain. Do not alter the evaluator to add an easier metric.

At review time, ask whether prior experiments support a throughput limitation, a learning-efficiency limitation, or neither. Choose the next experiment to distinguish those explanations instead of trying another unrelated parameter change.

## Bound the conclusion

A gain on this development metric under this hardware and short budget establishes only that scoped observation. Test longer training, additional datasets, or different hardware only through separately authorized comparisons. If a protected final test is unavailable, report development evidence and the limitation.

Upstream source: [karpathy/autoresearch](https://github.com/karpathy/autoresearch).
