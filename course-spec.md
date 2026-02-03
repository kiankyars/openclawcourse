# Course Specification

Formal learning outcomes, timing, and success criteria for the 3-hour OpenClaw course. Use this for alignment with Free Code Camp–style expectations and for QA.

---

## Overall Learning Outcomes

By the end of the course, learners will be able to:

1. **Explain** what OpenClaw is and how the Gateway fits into the network (channels → Gateway → Pi/tools).
2. **Install** OpenClaw, run the onboarding wizard, pair at least one channel, and send a message that receives an agent reply.
3. **Edit** `~/.openclaw/openclaw.json` to restrict channels (allowFrom, groups, requireMention) and understand session scope.
4. **Describe** the workspace layout (bootstrap files, memory, session files) and back up the workspace with a private git repo.
5. **Create** a minimal custom skill (SKILL.md with frontmatter and instructions) and install a skill from ClawHub.
6. **Configure** multi-agent routing (agents.list + bindings) and sandbox (mode, scope, workspaceAccess) and tool policy.
7. **Describe** automation (cron, heartbeat, webhooks) and security posture (prompt injection, sandbox, tool deny lists, browser risks).
8. **Build** a small personal-assistant setup (two channels, one skill, optional sandboxed agent, one cron/heartbeat) and verify with `openclaw doctor` and `openclaw status --all`.

---

## Lesson-Level Success Criteria

| Lesson | Success criterion (learner can …) |
|--------|-----------------------------------|
| 01 | State in one sentence what OpenClaw is and that the Gateway is a single process owning channels + WS. |
| 02 | Run `openclaw onboard --install-daemon`, pair one channel, open Control UI at 18789, and receive one agent reply. |
| 03 | Add or change one channel allowlist or group rule in openclaw.json and explain what mainKey / session scope means. |
| 04 | List AGENTS.md, SOUL.md, USER.md, memory/, and memory.md; init git in workspace and push to a private remote. |
| 05 | Write a SKILL.md with name, description, and short instructions; install one skill from ClawHub. |
| 06 | Add a second agent and a binding; set sandbox mode/scope once; name one tool policy (allow/deny). |
| 07 | Name cron, heartbeat, and webhooks; list three security practices (sandbox, tool deny, prompt injection). |
| 08 | Produce a working config with two channels, one skill, and one cron or heartbeat; run doctor and status. |

---

## Timing (Strict)

| Lesson | Planned | Buffer | Total |
|--------|---------|--------|-------|
| 01 | 18 | 2 | 20 |
| 02 | 23 | 2 | 25 |
| 03 | 28 | 2 | 30 |
| 04 | 23 | 2 | 25 |
| 05 | 23 | 2 | 25 |
| 06 | 28 | 2 | 30 |
| 07 | 18 | 2 | 20 |
| 08 | 23 | 2 | 25 |
| **Total** | **184** | **16** | **180** |

Instructor should keep each lesson within its Total; use Buffer for Q&A or catch-up.

---

## Prerequisites (Verified)

- Node ≥22.
- Docker (optional but recommended for Lesson 6).
- One of: WhatsApp, Telegram, or Discord account.
- Terminal and basic JSON/editing.

---

## Canonical Doc Set

All claims and examples must align with:

- https://docs.openclaw.ai
- https://docs.openclaw.ai/start/hubs (full doc index)
- https://docs.openclaw.ai/help (troubleshooting)

Lesson files link to specific doc pages; this spec does not duplicate them.
