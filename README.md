# Better Auth Agent Skills

Claude Code skills for building production-grade authentication with [Better Auth](https://better-auth.com).

**Fork:** https://github.com/ai-startup-learning/better-auth-skills

---

## Skills Included

| Skill | Trigger | Purpose |
|-------|---------|---------|
| `create-auth` | Adding auth to a project | Scaffold full auth layer: DB, routes, providers, UI |
| `best-practices` | Configuring `auth.ts` | Adapters, sessions, plugins, env vars, gotchas |
| `emailAndPassword` | Email/password auth | Verification, password reset, hashing |
| `organization` | Multi-tenant apps | Orgs, members, roles, invitations, teams |
| `twoFactor` | MFA/2FA | TOTP, OTP, backup codes, trusted devices |
| `security` | Hardening auth | Rate limiting, CSRF, cookies, secrets, auditing |

---

## Install in a New Project

### Option 1 — Per project (GitHub URL)

```bash
claude plugin add https://github.com/ai-startup-learning/better-auth-skills
```

### Option 2 — Global (all projects, one machine)

```bash
claude plugin add https://github.com/ai-startup-learning/better-auth-skills --global
```

### Option 3 — Local clone (recommended for active development)

```bash
# One-time setup
git clone https://github.com/ai-startup-learning/better-auth-skills ~/claude-skills/better-auth

# Install globally from local path
claude plugin add ~/claude-skills/better-auth --global
```

### Option 4 — Reference in CLAUDE.md (team projects)

Add to your project's `CLAUDE.md`:

```md
## Auth

This project uses Better Auth. When implementing or modifying auth:
- Use the `create-auth` skill to scaffold the auth layer
- Use the `best-practices` skill for config reference
- Use the `emailAndPassword`, `twoFactor`, `organization`, or `security` skills for specific features
- Always fetch https://better-auth.com/llms.txt to find the current doc page before writing code

Skills source: https://github.com/ai-startup-learning/better-auth-skills
```

---

## Update Skills

### If installed from GitHub URL

```bash
claude plugin update better-auth-agent-skills
```

### If installed from local clone (Option 3)

```bash
cd ~/claude-skills/better-auth && git pull
```

No reinstall needed — Claude reads from disk on every use.

---

## Improve Skills & Push

When you find gaps or make improvements to any skill file:

```bash
cd c:/Development/skills

# Edit the relevant SKILL.md file, then:
git add <file>
git commit -m "docs: describe the improvement"
git push fork main
```

If you installed via local clone, the update is available immediately after `git pull` on the consuming machine. No reinstall needed.

---

## Which Install Option to Use

| Scenario | Recommendation |
|----------|---------------|
| Solo dev, multiple projects | Option 2 — global install |
| Team project, shared standards | Option 4 — CLAUDE.md in repo |
| Actively improving skills | Option 3 — local clone |
| One-off project | Option 1 — per project URL |

---

## How the Skills Work

Each skill is a markdown file Claude reads when you trigger auth-related tasks. Skills instruct Claude to:

1. **Fetch `https://better-auth.com/llms.txt`** — machine-readable doc index
2. Find the relevant section for the current task
3. Fetch that specific doc page for current API signatures
4. Apply the patterns and gotchas documented in the skill

This means skills stay accurate even as Better Auth releases new versions.

---

## Repo Structure

```
.claude-plugin/
  marketplace.json          # Plugin manifest (registers all skills)
better-auth/
  create-auth/SKILL.md      # Auth scaffolding skill
  best-practices/SKILL.md   # Config & adapter reference
  emailAndPassword/SKILL.md # Email/password auth
  organization/SKILL.md     # Multi-tenant org management
  twoFactor/SKILL.md        # 2FA / MFA
  .claude-plugin/
    plugin.json
security/
  SKILL.MD                  # Security hardening
```
