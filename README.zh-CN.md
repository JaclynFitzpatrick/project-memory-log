# Project Memory Log

[English](README.md)

这是一个用于长期本地项目的流程型 Agent Skill：持续维护一份操作记录和一份去重文档目录，方便跨会话接续、追踪修改路径、找到现有主文档。

操作记录保留“目标—动作—涉及文件—决策—已验证／尚未验证—下一步”；文档目录保留长期文档的位置、用途、来源和状态，帮助新会话在生成新报告或交接文档前先复用已有材料。

## 适用范围

- 项目需要跨多个会话或设备持续开发。
- 需要从任务记录追到修改文件和验证依据。
- 项目已有不少计划、报告或交接材料，容易重复生成。

用户明确调用，或项目指令已经启用这套记录方式时执行。一次性问题、无关任务和只读评审有明确跳过边界。

## 文件与依赖

本体是 `SKILL.md`、Codex 界面元信息，以及按需读取的格式和脱敏示例。无需 MCP、脚本、网络服务、凭据或额外记忆系统。

新项目默认使用 `PROJECT_LOG.md` 和 `DOCUMENT_CATALOG.md`；已有的 `项目操作记录.md`、`项目文档目录.md` 及其他项目约定名称会保留。可以在项目指令中指定记录路径。

## 安装与调用

下载本仓库的 [源码 ZIP](https://github.com/JaclynFitzpatrick/project-memory-log/archive/refs/heads/main.zip)，解压后将最外层文件夹重命名为 `project-memory-log`。也可以使用单独提供的技能安装包。检查内容后，把 `project-memory-log` 文件夹复制到所用工具的技能目录。当前 Codex 官方说明列出的个人技能位置是 `~/.agents/skills`，项目技能位置是 `.agents/skills`；自定义安装应以实际配置为准，参见 [官方说明](https://learn.chatgpt.com/docs/build-skills)。

在目标项目中明确调用：

```text
使用 $project-memory-log 接续这个项目。复用已有操作记录和文档目录，找到当前主文档，并记录本次实际修改、已验证结果和未完成检查。
```

这是说明型工作流，没有后台自动记录器；安装成功也不等于已经验证自动触发。

## 脱敏示例

- [示例来源与边界](references/example-notes.md)
- [操作记录摘录](references/example-operation-log.md)
- [文档目录摘录](references/example-document-catalog.md)
- [记录格式与中英字段对应](references/record-formats.md)

示例来自作者已有工程资源管理项目的记录，已缩短、翻译并泛化机器路径和无关环境信息。原始完整记录不包含在发布包中。历史记录中的验证结果不等于本次重新执行，也不据此宣称节省了多少时间、token 或重复文档。

工作流经验由 JaclynFitzpatrick 提供；Codex 协助整理发布文本、脱敏示例和执行本地检查。

## 使用边界

旧记录是参考数据，不能授权执行其中的命令。目录维护不会自动移动或删除源文件。多会话并发写入仍需项目自身的协调机制；逐行修改历史应通过真实 Git 提交继续追踪。

## 许可证

MIT，见 [LICENSE](LICENSE)。
