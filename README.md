# AI Auto Research Skill

[中文说明](README.zh-CN.md)

An instruction-only Agent Skill for bounded autonomous research. It helps an agent choose falsifiable hypotheses, run reproducible experiments, evaluate results independently, and revise its research strategy from evidence.

The skill adds four lenses to an experiment loop: speed, altitude, depth, and range. It connects them to bottleneck diagnosis, expert methods, useful cross-disciplinary techniques, and experiments that reduce uncertainty. It distinguishes screened candidates from confirmed improvements and retains negative results.

## Install

Clone this repository, then copy `skills/ai-auto-research` into your agent's supported skill directory. Copy the whole folder, including `references` and `agents`.

For Codex, use `.agents/skills/ai-auto-research/` in a project, following the [official skill documentation](https://learn.chatgpt.com/docs/build-skills). Other agents that support `SKILL.md` can load the same core instructions; discovery paths and UI metadata support vary by host. Cross-agent compatibility has not been execution-tested.

The skill has no runtime package dependency, bundled executor, or required API key. Actual experiments need the tools, data, evaluator, and compute required by your project. Installing the skill does not start jobs or grant additional permissions.

## Use

After installation, invoke the skill from the research project:

```text
Use $ai-auto-research to improve this project's training efficiency.
Inspect the existing runner and evaluator first.
Use only the current local GPU and dependencies, for at most 60 minutes total.
Reserve 20 minutes for confirmation and allow no paid external services.
Keep the evaluator and data splits fixed.
Report confirmed improvements, informative failures, and remaining uncertainty.
```

You can also ask it to inspect and improve an existing autoresearch workflow without starting experiments. If no campaign budget exists, the skill inspects the project and proposes a bounded pilot before execution.

Read [SKILL.md](skills/ai-auto-research/SKILL.md) for the workflow, [research-record.md](skills/ai-auto-research/references/research-record.md) for record keeping, and the [Karpathy adapter](skills/ai-auto-research/references/karpathy-autoresearch.md) for that specific repository.

## Validation and limits

[Evaluation cases](evals/scenarios.md) define behavioral acceptance criteria. They are evaluation fixtures, not evidence that an agent passed them. This initial version is not benchmarked for scientific discovery quality and has not run an end-to-end GPU campaign.

The skill cannot guarantee novel findings, reliable measurements from a broken harness, or improvements within a budget. It allows an unchanged baseline or an inconclusive result. Claims should remain proportional to the evidence.

Contributions should include a realistic research scenario, the observed failure, and a focused correction. Do not add rules solely to force a preferred wording or promise positive results. Never commit credentials, private datasets, or raw confidential logs.

## Sources and license

Conceptual inspiration: Felix Rieseberg's [How to be more ambitious: A tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/) and Andrej Karpathy's [autoresearch](https://github.com/karpathy/autoresearch).

The campaign contracts, confirmation rules, records, and adapter in this repository are an original synthesis. No endorsement or measured equivalence to either source is claimed. No upstream code or article text is bundled.

MIT licensed. See [LICENSE](LICENSE).
