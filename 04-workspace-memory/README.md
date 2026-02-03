# Module 4: Workspace & Memory (~25 min)

**Learning objectives:** Learners know the workspace folder layout, what each bootstrap file does, how memory (memory.md + daily logs) works, and how to back up the workspace with git (private).

---

## Key Concepts

1. **Workspace vs config/state**
   - Workspace = agent’s working directory and context (default `~/.openclaw/workspace`).
   - Config, credentials, sessions live under `~/.openclaw/` and are **not** part of the workspace repo.
   - [Agent Workspace](https://docs.openclaw.ai/concepts/agent-workspace)

2. **Bootstrap files (in workspace)**
   - **AGENTS.md** — How the agent should operate and use memory.
   - **SOUL.md** — Persona, tone, boundaries.
   - **USER.md** — Who the user is and how to address them.
   - **IDENTITY.md** — Agent name, vibe, emoji (bootstrap ritual).
   - **TOOLS.md** — Guidance on local tools (does not control tool availability).
   - **HEARTBEAT.md** — Optional short checklist for heartbeat runs.
   - **BOOT.md** — Optional startup checklist (on gateway restart).
   - **BOOTSTRAP.md** — One-time first-run ritual; delete after use.
   - [Workspace file map](https://docs.openclaw.ai/concepts/agent-workspace#workspace-file-map-what-each-file-means)

3. **Memory**
   - **memory/YYYY-MM-DD.md** — Daily memory log.
   - **memory.md** (optional) — Long-term memory; load only in main/private session.
   - Memory flush before compaction: agent writes durable memories to disk.
   - [Memory](https://docs.openclaw.ai/concepts/memory)

4. **Session files**
   - Session history: `.jsonl` under `~/.openclaw/agents/<agentId>/...`; compaction applies.
   - Don’t commit session dirs to the workspace repo.

5. **Git backup**
   - Treat workspace as **private** memory; init git, add private remote, `.gitignore` secrets.
   - [Git backup](https://docs.openclaw.ai/concepts/agent-workspace#git-backup-recommended-private)

---

## Lesson Plan

| Segment | Duration | Activity |
|---------|----------|----------|
| Workspace layout | 8 min | List workspace dir; open AGENTS.md, SOUL.md, USER.md; explain injection into context. |
| Bootstrap vs memory | 6 min | Bootstrap = every session; memory/ = daily; memory.md = curated long-term. |
| Session files | 3 min | Where .jsonl lives; compaction; don’t commit. |
| Git backup | 8 min | `git init`, private remote, push; show suggested .gitignore. |

---

## Doc References

- [Agent Workspace](https://docs.openclaw.ai/concepts/agent-workspace)
- [Memory](https://docs.openclaw.ai/concepts/memory)
- [Compaction](https://docs.openclaw.ai/concepts/compaction) (memory flush)
- [Reference templates](https://docs.openclaw.ai/reference/templates/AGENTS) (AGENTS, SOUL, USER, etc.)

---

## Checklist (Instructor)

- [ ] Clarify: workspace is default cwd for file tools but **not** a hard sandbox; sandbox is separate (Module 6).
- [ ] Do not commit `~/.openclaw/openclaw.json` or credentials to the workspace repo.
- [ ] Mention `agents.defaults.bootstrapMaxChars` (default 20000) if discussing large bootstrap files.
