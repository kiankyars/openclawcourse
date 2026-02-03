# Skills System

**Learning objectives:** Learners understand the AgentSkills format (SKILL.md + YAML frontmatter), skill resolution (workspace → ~/.openclaw/skills → bundled), how to write a minimal custom skill, and how eligibility (os, requiredBinaries, env) and token cost work.

---

## Key Concepts

### What skills are

- AgentSkills-compatible folders: each skill is a directory with **SKILL.md** (YAML frontmatter + instructions). They teach the agent how to use tools.

See: [Skills](https://docs.openclaw.ai/tools/skills)

### Token impact

- Base overhead when ≥1 skill; per-skill cost (~97 chars + name/description/location). Roughly ~24 tokens per skill.

See: [Token impact](https://docs.openclaw.ai/tools/skills#token-impact-skills-list)

### ClawHub

- Public skills registry: https://clawhub.com. Install: `clawhub install <slug>`; update: `clawhub update --all`.
- Treat third-party skills as untrusted; read before enabling.

[Security notes](https://docs.openclaw.ai/tools/skills#security-notes).
[ClawHub](https://docs.openclaw.ai/tools/clawhub)
