# Kevin's Skills

个人 Agent Skills 合集，按用途分组。目录组织参考 [Matt Pocock 的 skills 仓库](https://github.com/mattpocock/skills)，技能内容独立维护。

## Engineering

### Model-invoked

可由 agent 在任务适合时选用，也可手动调用。

| Skill | 用途 |
| --- | --- |
| [feature-development-loop](skills/engineering/feature-development-loop/SKILL.md) | 按可验收的功能批次规划、实施、验证和恢复开发；推荐配合 Matt Pocock 的技能使用。 |

## 使用

当前目录可直接作为本地来源：让 agent 读取上述 `SKILL.md`，并保持整个技能目录可访问，以便读取模板与参考文件。安装到 agent 的技能目录时，也应完整复制该目录。

发布到 GitHub 后，可通过 [Skills CLI](https://www.skills.sh/docs/cli) 安装，并选择所需技能：

```sh
npx skills add KevinGuo1007/skills
```

本仓还提供 `.claude-plugin/` 插件清单；其中仅包含本仓技能，不会自动安装 Matt 的技能。

调用示例：

```text
使用 $feature-development-loop，基于现有需求规划下一批可独立验收的功能。
使用 $feature-development-loop，从当前批次记录恢复，先核实阶段、授权和下一步。
```

它适用于 Web、移动端、CLI、后端、库，以及可作为独立交付单元的重构或基础设施改动。普通小修改无需自动套用完整流程。

## 与 Matt Pocock 技能配合

本技能维护批次范围、计划授权、阶段、验证证据和恢复点。Matt 的技能可用于需求澄清、规格、拆分任务、实施、TDD、诊断与审查；协作方式见 [指南](skills/engineering/feature-development-loop/references/matt-pocock.md)。

运行时以实际安装版本为准。仅供用户显式调用的技能由用户触发，不能自动串联；缺少 Matt 技能时，本技能仍可独立执行。

## 目录约定

```text
AGENTS.md                       Codex 与其他 agent 的共享项目约定
CLAUDE.md                       Claude 入口，导入 AGENTS.md
docs/commit-conventions.md      统一的英文提交规范
.claude-plugin/                 插件与 marketplace 清单
skills/
  engineering/
    README.md                   用途分组索引
    feature-development-loop/
      SKILL.md                  工作流入口
      agents/openai.yaml        Codex 界面与调用策略
      assets/feature-batch.md   交付记录模板
      references/               按需读取的适配与协作指南
```

新增技能放在 `skills/<用途>/<技能名>/`，只建立实际使用的分组。每个技能保持自包含，更新根索引、分组索引和插件技能路径；按需增加 `references/`、`assets/` 或 `scripts/`。

项目约定见 [AGENTS.md](AGENTS.md)，提交信息遵循 [Commit Conventions](docs/commit-conventions.md)：英文 Conventional Commits，标题不超过 72 个字符。`CLAUDE.md` 导入共享约定，规则只维护一份。

Feature Development Loop 从项目内的文档驱动流程提取，保留版本化计划、证据、恢复及停止机制，将原有设备、设计工具、tracker、环境与仓库约定改为项目适配项。
