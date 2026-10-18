# AI Auto Research Skill

[English](README.md)

这个 skill 帮助 AI 自主研究：提出可被实验推翻的假设，运行实验，独立评估结果，并根据证据调整研究方向。

它把速度、高度、深度和广度落实到研究决策中。AI 需要识别瓶颈、使用专业方法、引入有用的其他领域方法，并选择能减少不确定性的实验。

它还把执行和验收分开。AI 声称完成后，需要用最终文件和实验结果逐项核对成功标准。长任务会先检查实际进度，再决定继续、修复或恢复执行，并保留原来的预算和任务记录。

## 安装

下载或克隆仓库，把完整的 `skills/ai-auto-research` 文件夹复制到所用工具支持的 skill 目录。

Codex 项目可以使用 `.agents/skills/ai-auto-research/`。安装方式见 [OpenAI 官方说明](https://learn.chatgpt.com/docs/build-skills)。其他支持 `SKILL.md` 的工具可以读取核心指令，但目录规则和界面配置支持程度不同，尚未逐一实测。

skill 本身没有运行依赖，也不需要 API Key。实际研究需要项目自己的数据、实验工具、评估程序和计算资源。安装不会启动实验或扩大权限。

## 使用

在研究项目中输入：

```text
使用 $ai-auto-research 改进这个项目的训练效率。
先检查现有实验工具和评估程序。
只使用当前本地 GPU 和已有依赖，总时间不超过 60 分钟。
预留 20 分钟验证候选结果，禁止使用付费外部服务。
保持评估程序和数据划分不变。
报告已确认的改进、有价值的失败和仍然不确定的地方。
```

也可以只让它检查现有 Auto Research 流程，暂不运行实验。没有研究预算时，它会先检查项目，再提出有明确上限的试验方案。

## 文件

核心流程在 [SKILL.md](skills/ai-auto-research/SKILL.md)。

研究记录规范在 [research-record.md](skills/ai-auto-research/references/research-record.md)。

Karpathy 项目的接入方法在 [karpathy-autoresearch.md](skills/ai-auto-research/references/karpathy-autoresearch.md)。

长任务、中断恢复和已获授权的分工协作按需读取 [goal-supervision.md](skills/ai-auto-research/references/goal-supervision.md)。这个协议不要求固定团队，也不授予额外权限。

[验收场景](evals/scenarios.md) 用于后续行为评估，场景本身不代表测试已经通过。

## 边界

skill 区分初筛候选和已确认改进。失败实验会保留记录。研究会在预算、目标或停止条件触发时结束。评估程序和最终测试数据受到保护。

验收和进度监督借鉴了 [goal-driven](https://github.com/lidangzzz/goal-driven/tree/c8e54ba3e9a4cf65df8fd9d92d0f9b231cab7f45) 的思想。项目使用自行编写的研究流程，没有复制原项目的提示词模板。监督规则由当前会话执行，不是后台守护程序。

当前版本未运行完整 GPU 研究实验，也没有研究质量基准成绩。它不保证发现新方法或取得正向结果。没有改进和证据不足都属于有效研究结论。

来源说明和贡献约定见 [English README](README.md)。本项目采用 [MIT 许可证](LICENSE)。
