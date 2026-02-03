# Module 3: Gateway & Channels (~30 min)

**Learning objectives:** Learners can read and edit `openclaw.json`, configure channel allowlists and group mention behavior, understand session scope (per-sender, mainKey), and use slash commands (`/new`, `/reset`).

---

## Key Concepts

1. **Config location and format**
   - `~/.openclaw/openclaw.json` (JSON5: comments and trailing commas allowed).
   - Strict validation: unknown keys or invalid values → Gateway refuses to start. Use `openclaw doctor` to see issues.
   - [Configuration](https://docs.openclaw.ai/gateway/configuration)

2. **Minimal config (recommended starting point)**
   - `agents.defaults.workspace`, `channels.whatsapp.allowFrom` (or equivalent for Telegram/Discord).
   - [Minimal config](https://docs.openclaw.ai/gateway/configuration#minimal-config-recommended-starting-point)

3. **Channel config**
   - **allowFrom:** allowlist of E.164 (WhatsApp) or tg/discord ids for who can trigger the bot (DMs).
   - **groups:** per-channel group policy; `requireMention`; `mentionPatterns` per agent.
   - **groupPolicy:** `allowlist` | `open` | `disabled`; group allowlists vary by channel (e.g. Discord guilds, Slack channels).
   - [channels.whatsapp](https://docs.openclaw.ai/gateway/configuration#channels-whatsapp-allowfrom), [Group chat mention gating](https://docs.openclaw.ai/gateway/configuration#group-chat-mention-gating-agents-list-groupchat--messages-groupchat)

4. **Session management**
   - Per-sender scope; `mainKey` (default `main`); DMs collapse to shared “main” session; groups get separate session keys.
   - [Session Management](https://docs.openclaw.ai/concepts/session), [Sessions](https://docs.openclaw.ai/concepts/sessions)

5. **Streaming and chunking**
   - Block streaming; channel-specific chunk limits and coalesce.
   - [Streaming and Chunking](https://docs.openclaw.ai/concepts/streaming)

6. **Slash commands**
   - `/new`, `/reset`, etc. Standalone message; leading `/`. [Slash Commands](https://docs.openclaw.ai/tools/slash-commands)

---

## Lesson Plan

| Segment | Duration | Activity |
|---------|----------|----------|
| Config structure | 8 min | Open `openclaw.json`; walk `agents.defaults.workspace`, `channels.*`. |
| allowFrom + groups | 10 min | Set allowlist for one channel; set `requireMention` for groups; show mentionPatterns. |
| Sessions | 5 min | Explain mainKey, DM vs group sessions; optional: show session key in UI or CLI. |
| Slash commands | 4 min | Demo `/new`, `/reset`; mention other commands from docs. |
| Apply + restart | 3 min | Change one key; `openclaw doctor`; restart Gateway if needed. |

---

## Doc References

- [Configuration](https://docs.openclaw.ai/gateway/configuration)
- [Configuration Examples](https://docs.openclaw.ai/gateway/configuration-examples)
- [Session Management](https://docs.openclaw.ai/concepts/session)
- [Streaming and Chunking](https://docs.openclaw.ai/concepts/streaming)
- [Slash Commands](https://docs.openclaw.ai/tools/slash-commands)

---

## Checklist (Instructor)

- [ ] Use a **copy** of config for edits so learners see structure without breaking a live gateway.
- [ ] Emphasize: config is the main “code” for OpenClaw; don’t rush the JSON.
- [ ] If time: show `config.patch` / `config.apply` from [Configuration](https://docs.openclaw.ai/gateway/configuration#partial-updates-rpc) (RPC) for safe updates.
