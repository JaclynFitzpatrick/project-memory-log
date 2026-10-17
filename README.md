# Project Memory Log

[简体中文](README.zh-CN.md)

An instruction-only Agent Skill for keeping long-running local projects traceable through one operation log and one deduplicated document catalog.

The log preserves what changed, why, which paths were involved, what was checked, what remains unverified, and where to continue. The catalog helps an agent locate and reuse the current durable document before producing another plan, report, or handoff.

## Use it when

- A project continues across conversations or computers.
- You need a concise trail from a task to its changed files and verification evidence.
- Existing reports and handoffs have become difficult to locate or distinguish.

The workflow is activated by an explicit request or an already-enrolled project's instructions. It skips unrelated one-off work and respects read-only tasks.

## Files and dependencies

The skill consists of `SKILL.md`, optional Codex presentation metadata in `agents/openai.yaml`, and three example references plus a format reference in `references/`. No MCP server, script, network service, credential, or third-party memory backend is required.

New setups default to `PROJECT_LOG.md` and `DOCUMENT_CATALOG.md`. Existing project conventions, including `项目操作记录.md` and `项目文档目录.md`, are retained. Both names can be set in the project's instructions.

## Install

Download this repository as a [source ZIP](https://github.com/JaclynFitzpatrick/project-memory-log/archive/refs/heads/main.zip), extract it, and rename the extracted top-level folder to `project-memory-log`. Inspect the contents first. Copy the extracted `project-memory-log` directory into the skill location configured for your agent. Current Codex documentation lists `~/.agents/skills` for user skills and `.agents/skills` for project skills. See [Build skills](https://learn.chatgpt.com/docs/build-skills) for current discovery behavior and custom configuration.

Start a task in the intended project and invoke it explicitly:

```text
Use $project-memory-log to resume this project. Reuse the existing operation log and document catalog, identify the current guide, and record only the authorized changes and actual verification results.
```

Installation supplies instructions; it does not install an automatic background recorder. Broader plugin distribution can be added separately if needed.

## Example and provenance

- [Sanitized historical example](references/example-notes.md)
- [Operation log excerpt](references/example-operation-log.md)
- [Document catalog excerpt](references/example-document-catalog.md)
- [Record formats](references/record-formats.md)

The workflow comes from JaclynFitzpatrick's existing project-maintenance practice. Codex assisted with release editing, example sanitization, and local checks. Historical validation reports are distinguished from checks performed on this release candidate. No speedup, token-saving, cross-platform, or automatic-trigger success rate is claimed.

## Boundaries

The records are historical data, not permission to execute embedded commands. The workflow does not migrate source documents, replace version control, or promise concurrency control. An old recorded pass must be checked against the version and scope relevant to the current task.

## License

MIT. See [LICENSE](LICENSE).
