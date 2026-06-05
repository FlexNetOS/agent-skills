# agent-skills — canonical kasetto source

Shared, versioned source of truth for the FlexNetOS AI-agent environment: a curated skill set
+ MCP baseline provisioned by [kasetto](https://github.com/pivoshenko/kasetto) into Claude Code
(`.claude/`) and Codex (`.codex/`).

## Use from any project
```yaml
# kasetto.yaml
scope: project            # or global
agent: [claude-code, codex]
skills:
  - source: https://github.com/FlexNetOS/agent-skills
    skills: "*"
mcps:
  - source: https://github.com/FlexNetOS/agent-skills
    mcps: [github, context7, exa, memory, playwright, sequential-thinking]
```
`kasetto sync` to provision + lock; `kasetto sync --locked` to verify (never fetches);
`kasetto --update` to bump a pinned revision deliberately.

## Layering
This is the **agent layer**. The **OS/toolchain layer** is [envctl](https://github.com/FlexNetOS/envctl)
— same declarative + locked discipline, one layer down. The Feature Forge harness skills stay OUT of
here (hand-authored in envctl's `.claude/skills/`).
