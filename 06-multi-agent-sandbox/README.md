# Module 6: Multi-Agent Routing & Sandboxing (~30 min)

**Learning objectives:** Learners can define multiple agents in `agents.list`, route by channel/peer with `bindings`, and configure sandbox mode/scope/workspaceAccess and tool policies. They understand why sandboxing is the differentiator from “just run Claude Code.”

---

## Key Concepts

1. **Why multi-agent**
   - Isolation: different personas, permissions, workspaces (e.g. family vs work).
   - Per-agent: workspace, sessions, auth profiles, sandbox, tool policy.
   - [Multi-Agent Routing](https://docs.openclaw.ai/concepts/multi-agent)

2. **agents.list + bindings**
   - **agents.list[]:** id, default, name, workspace, agentDir, model, identity, groupChat, sandbox, tools, etc.
   - **bindings[]:** route inbound messages to agentId by `match.channel`, `match.accountId`, `match.peer`, `match.guildId`/`match.teamId`. Deterministic match order in docs.
   - [Multi-agent routing (config)](https://docs.openclaw.ai/gateway/configuration#multi-agent-routing-agents-list--bindings)

3. **Per-agent access profiles**
   - Full access (sandbox off), read-only tools + workspace, or messaging-only (no filesystem). Examples in config docs.
   - [Per-agent access profiles](https://docs.openclaw.ai/gateway/configuration#per-agent-access-profiles-multi-agent)

4. **Sandboxing**
   - Optional Docker-based isolation for tool execution; Gateway stays on host.
   - **Modes:** `off` | `non-main` | `all`.
   - **Scope:** `session` | `agent` | `shared` (containers).
   - **workspaceAccess:** `none` | `ro` | `rw` (sandbox workspace vs agent workspace).
   - Default image: `openclaw-sandbox:bookworm-slim`; build with `scripts/sandbox-setup.sh`.
   - [Sandboxing](https://docs.openclaw.ai/gateway/sandboxing)

5. **Tool policy**
   - `tools.allow` / `tools.deny`; per-agent `agents.list[].tools`; sandbox tool policy (`tools.sandbox.tools`). Deny wins.
   - Elevated exec runs on host and bypasses sandbox.
   - [Sandbox vs Tool Policy vs Elevated](https://docs.openclaw.ai/gateway/sandbox-vs-tool-policy-vs-elevated)

6. **Docker hardening**
   - Network isolation (default none); resource limits; optional custom image / setupCommand.
   - [Sandboxing](https://docs.openclaw.ai/gateway/sandboxing) (images + setup)

---

## Lesson Plan

| Segment | Duration | Activity |
|---------|----------|----------|
| Why multi-agent | 4 min | Use cases: family vs work; separate workspaces and tool sets. |
| agents.list + bindings | 10 min | Add a second agent; add binding by channel or accountId; send message and show routing. |
| Sandbox modes + scope | 8 min | Explain mode (off / non-main / all), scope (session / agent / shared), workspaceAccess. |
| Tool policy + elevated | 5 min | allow/deny example; mention elevated as host escape hatch. |
| Minimal sandbox enable | 3 min | Show minimal config snippet; `openclaw doctor`; optional build of default image. |

---

## Doc References

- [Multi-Agent Routing](https://docs.openclaw.ai/concepts/multi-agent)
- [Configuration: multi-agent](https://docs.openclaw.ai/gateway/configuration#multi-agent-routing-agents-list--bindings)
- [Sandboxing](https://docs.openclaw.ai/gateway/sandboxing)
- [Sandbox vs Tool Policy vs Elevated](https://docs.openclaw.ai/gateway/sandbox-vs-tool-policy-vs-elevated)
- [Multi-Agent Sandbox & Tools](https://docs.openclaw.ai/multi-agent-sandbox-tools)

---

## Checklist (Instructor)

- [ ] Don’t skip sandboxing: it’s the security differentiator; learners should know mode/scope/workspaceAccess.
- [ ] If Docker isn’t available, explain config and show docs; skip live sandbox run.
- [ ] Mention prompt-injection risks with smaller models and tool policy as mitigation (tease Module 7).
