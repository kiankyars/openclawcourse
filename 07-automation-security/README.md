# Module 7: Automation & Security (~20 min)

**Learning objectives:** Learners know how to add cron jobs and heartbeats, what webhooks and Gmail PubSub are for, and core security posture: prompt injection risks, sandbox practices, tool deny lists, and browser control risks.

---

## Key Concepts

1. **Cron jobs**
   - Gateway scheduler: run tasks on a schedule (e.g. daily summary). Config under `cron`.
   - [Cron Jobs](https://docs.openclaw.ai/automation/cron-jobs)
   - [Cron vs Heartbeat](https://docs.openclaw.ai/automation/cron-vs-heartbeat)

2. **Heartbeats**
   - Periodic agent runs (e.g. read HEARTBEAT.md, act, reply HEARTBEAT_OK). Config: `agents.defaults.heartbeat` or per-agent `agents.list[].heartbeat`.
   - [Gateway Heartbeat](https://docs.openclaw.ai/gateway/heartbeat)

3. **Webhooks + Gmail PubSub**
   - Inbound triggers for automation (e.g. webhook URL, Gmail PubSub for email-driven flows).
   - [Webhooks](https://docs.openclaw.ai/automation/webhook), [Gmail PubSub](https://docs.openclaw.ai/automation/gmail-pubsub)

4. **Hooks**
   - e.g. voice transcription (SOUL Evil Hook). [Hooks](https://docs.openclaw.ai/hooks)

5. **Security posture**
   - **Prompt injection:** smaller models more susceptible; use sandbox + tool policy for untrusted or high-risk channels.
   - **Sandbox:** default non-main or all; scope session/agent; limit workspaceAccess.
   - **Tool policy:** deny lists for untrusted agents; avoid granting elevated exec to unknown senders.
   - **Browser control:** high risk; gate by channel/sender; prefer sandboxed browser when possible.
   - [Security](https://docs.openclaw.ai/gateway/security)
   - [Formal Verification (Security Models)](https://docs.openclaw.ai/security/formal-verification) (optional read)

---

## Lesson Plan

| Segment | Duration | Activity |
|---------|----------|----------|
| Cron + heartbeat | 6 min | Show cron config example; show heartbeat config and HEARTBEAT.md. |
| Webhooks / Gmail | 3 min | One slide or paragraph: what they’re for; link to docs. |
| Security posture | 8 min | Prompt injection; sandbox as default; tool deny lists; elevated and browser risks. |
| Checklist | 3 min | “Before going to production”: allowlist, sandbox, deny list, no secrets in workspace. |

---

## Doc References

- [Cron Jobs](https://docs.openclaw.ai/automation/cron-jobs)
- [Cron vs Heartbeat](https://docs.openclaw.ai/automation/cron-vs-heartbeat)
- [Webhooks](https://docs.openclaw.ai/automation/webhook)
- [Gmail PubSub](https://docs.openclaw.ai/automation/gmail-pubsub)
- [Security](https://docs.openclaw.ai/gateway/security)
- [Hooks](https://docs.openclaw.ai/hooks)

---

## Checklist (Instructor)

- [ ] Emphasize: security is non-negotiable for multi-user or high-trust scenarios; sandbox + tool policy are the main levers.
- [ ] Mention `openclaw doctor`, `openclaw status --all` for health before/after changes (bridge to Module 8).
