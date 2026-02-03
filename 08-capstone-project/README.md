# Module 8: Capstone Project (~25 min)

**Learning objectives:** Learners build a small “personal assistant” setup that uses at least two channels, a custom or ClawHub skill, optional sandboxed/family agent with restricted tools, and a cron or heartbeat. They can run `openclaw doctor` and `openclaw status --all` to verify state.

---

## Suggested Project (One Possible Path)

Build a **personal assistant** that:

1. **Channels:** WhatsApp + Telegram (or Discord) with allowlists and group mention rules.
2. **Custom skill:** e.g. calendar reminder, home automation (or install one from ClawHub: [Home Assistant](https://clawhub.com/skills/homeassistant), [CalDAV](https://clawhub.com/skills/caldav-calendar)).
3. **Multi-agent (optional):** “family” agent with sandbox mode `all`, scope `agent`, restricted tools (e.g. deny `exec`, `process`, `browser`); bind one channel or peer to it.
4. **Automation:** One cron job (e.g. daily summary) or heartbeat with HEARTBEAT.md.

---

## Lesson Plan

| Segment | Duration | Activity |
|---------|----------|----------|
| Project spec | 3 min | Share the suggested project; learners can simplify (e.g. one channel, one skill). |
| Build | 15 min | Config edits; add skill; optional second agent + binding; add cron or heartbeat. |
| Verify | 4 min | `openclaw doctor`; `openclaw status --all`; send test message on each channel. |
| Troubleshooting | 3 min | Common issues: config validation, pairing, gateway not running; point to [Troubleshooting](https://docs.openclaw.ai/help/troubleshooting). |

---

## Showcase (Steal Ideas)

Use [Showcase](https://docs.openclaw.ai/start/showcase) for concrete examples:

- 14+ agent orchestration (Kev’s Dream Team)
- Roborock vacuum, Home Assistant
- Cron/heartbeat, webhooks, skills from ClawHub

---

## Doc References

- [Showcase](https://docs.openclaw.ai/start/showcase)
- [Troubleshooting](https://docs.openclaw.ai/help/troubleshooting)
- [Configuration Examples](https://docs.openclaw.ai/gateway/configuration-examples)
- [Doctor](https://docs.openclaw.ai/gateway/doctor)
- [Gateway Runbook](https://docs.openclaw.ai/gateway)

---

## Checklist (Instructor)

- [ ] Provide a minimal `openclaw.json` starter (two channels, one agent, one skill) so learners don’t start from empty.
- [ ] If time: demo one showcase project (e.g. Home Assistant skill) so learners see a real deployment.
- [ ] End with “next steps”: Tailscale remote access, Nix/Docker deploy, formal verification doc.
