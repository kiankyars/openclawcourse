# Module 5: Skills System (~25 min)

**Learning objectives:** Learners understand the AgentSkills format (SKILL.md + YAML frontmatter), skill resolution (workspace → ~/.openclaw/skills → bundled), how to write a minimal custom skill, and how eligibility (os, requiredBinaries, env) and token cost work.

---

## Key Concepts

1. **What skills are**
   - AgentSkills-compatible folders: each skill is a directory with **SKILL.md** (YAML frontmatter + instructions). They teach the agent how to use tools.
   - [Skills](https://docs.openclaw.ai/tools/skills)

2. **Locations and precedence**
   - **Bundled** (ship with install) → **Managed** (`~/.openclaw/skills`) → **Workspace** (`<workspace>/skills`). Highest wins on name conflict.
   - Optional: `skills.load.extraDirs` in config.
   - [Locations and precedence](https://docs.openclaw.ai/tools/skills#locations-and-precedence)

3. **Format**
   - Required frontmatter: `name`, `description`. Optional: `homepage`, `user-invocable`, `disable-model-invocation`, `command-dispatch`, `command-tool`, `command-arg-mode`.
   - Use `{baseDir}` in instructions for the skill folder path.
   - [Format (AgentSkills + Pi-compatible)](https://docs.openclaw.ai/tools/skills#format-agentskills--pi-compatible)

4. **Gating (load-time filters)**
   - `metadata.openclaw`: `os`, `requires.bins`, `requires.anyBins`, `requires.env`, `requires.config`, `primaryEnv`, `install`.
   - Skills are filtered at load time; sandboxed agents need binaries inside the container too.
   - [Gating](https://docs.openclaw.ai/tools/skills#gating-load-time-filters)

5. **Config overrides**
   - `skills.entries.<name>.enabled`, `apiKey`, `env`, `config` in `~/.openclaw/openclaw.json`.
   - [Config overrides](https://docs.openclaw.ai/tools/skills#config-overrides--openclawopenclawjson)

6. **Token impact**
   - Base overhead when ≥1 skill; per-skill cost (~97 chars + name/description/location). Roughly ~24 tokens per skill.
   - [Token impact](https://docs.openclaw.ai/tools/skills#token-impact-skills-list)

7. **ClawHub**
   - Public skills registry: https://clawhub.com. Install: `clawhub install <slug>`; update: `clawhub update --all`.
   - [ClawHub](https://docs.openclaw.ai/tools/clawhub)

---

## Lesson Plan

| Segment | Duration | Activity |
|---------|----------|----------|
| What skills are | 3 min | Definition; precedence (workspace > managed > bundled). |
| SKILL.md format | 7 min | Show one bundled skill; frontmatter + body; gating metadata. |
| Write a minimal skill | 10 min | Create `workspace/skills/my-skill/SKILL.md` with name, description, short instructions; reload and confirm it appears. |
| ClawHub + token cost | 5 min | Browse clawhub.com; install one skill; mention token formula. |

---

## Doc References

- [Skills](https://docs.openclaw.ai/tools/skills)
- [Skills Config](https://docs.openclaw.ai/tools/skills-config)
- [ClawHub](https://docs.openclaw.ai/tools/clawhub)

---

## Checklist (Instructor)

- [ ] Treat third-party skills as untrusted; read before enabling. [Security notes](https://docs.openclaw.ai/tools/skills#security-notes).
- [ ] Session snapshot: skill list is fixed when session starts; changes apply on next session (or when skills watcher triggers).
- [ ] Optional: show `skills.load.watch` for auto-refresh during development.
