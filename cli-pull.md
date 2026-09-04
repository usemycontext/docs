---
title: Session starter (usemycontext pull)
description: One command writes your curated context to a local file, so AI tools that read files at startup - Claude Code, agent frameworks, your own scripts - begin every session already knowing you.
sidebar:
  label: Session starter
  order: 6
---

Not every AI tool speaks MCP. Plenty of them just read a file when they start up. For those, one command writes your curated context to disk:

```bash
npx -y usemycontext pull                # writes ./UMC-CONTEXT.md
npx -y usemycontext pull --out me.md    # or any path you like
```

Re-running overwrites the file, so it stays fresh. Nothing to install and nothing to configure: `npx` fetches the [`usemycontext` package](https://www.npmjs.com/package/usemycontext) and runs it.

## Get your token first

The CLI needs an access token, which you generate on the Connect page inside the app, under "Advanced - manual setup". Give it to the CLI either way:

```bash
export UMC_TOKEN=<your token>
```

or put a `token=` line in `~/.usemycontext`:

```
token=<your token>
```

The token is deliberately never accepted as a command-line flag, because flags land in your shell history, and the CLI never writes it anywhere itself. Read [Handling your token](#handling-your-token) below before you park it in a file.

## What lands in the file

Your compiled profile, and only that. Never raw facts, never file contents, never your audit trail. It arrives wrapped in a short fixed preamble that tells the reading AI this is your human-curated ground truth and must not be rewritten or appended to, followed by a date stamp and a pointer back to your live profile.

If you have more than one profile, you get the one your token is pinned to, or your active profile if the token is not pinned to a particular one.

If a pull fails - a bad token, no network, no compiled profile yet, nowhere to write the file - it exits non-zero with one plain-English line and never leaves a half-written file behind. Each network call has a 15-second deadline and the whole run a 30-second one, so a stalled connection fails fast instead of hanging a startup hook.

If your context is not current at the source, the CLI would rather keep good context than replace it with worse: when a session-starter file it wrote earlier is already sitting there, it keeps that one, says so, and exits successfully. It will never adopt a file it did not write, and with no previous file of its own it writes nothing and fails rather than inventing one. If that keeps happening, open the app and refresh your profile.

Pulls appear as their own client, `umc-cli`, in your activity feed, separate from Claude or ChatGPT.

## Recipe: Claude Code, refreshed on every session

Add a SessionStart hook so every new session begins with a fresh pull. In `.claude/settings.json` for one project, or `~/.claude/settings.json` for all of them:

```json
{
  "hooks": {
    "SessionStart": [
      {
        "hooks": [
          { "type": "command", "command": "npx -y usemycontext pull" }
        ]
      }
    ]
  }
}
```

Then one line in your `CLAUDE.md` tells the session to read it:

```
Read UMC-CONTEXT.md at session start: it is my curated personal context.
```

Prefer the context handed straight to the session instead of read from disk? A SessionStart hook's output reaches the session, so this variant needs no `CLAUDE.md` line at all. Replace the `command` value in the block above with:

```
npx -y usemycontext pull && cat UMC-CONTEXT.md
```

Set `UMC_TOKEN` in your shell profile (or use `~/.usemycontext`) so the hook can find it. If the token is missing or expired the hook prints one plain line and the session simply starts without your context. Nothing breaks.

## Recipe: agent frameworks that read a bootstrap file

Frameworks that read a fixed set of files at startup (an `AGENTS.md`, a `USER.md`, a configured context-file list) can consume the pulled file directly. Write it wherever those files live:

```bash
npx -y usemycontext pull --out ~/my-agent/UMC-CONTEXT.md
```

Then either list `UMC-CONTEXT.md` in the framework's own context configuration, or add one line to the bootstrap file it already reads:

```
Read UMC-CONTEXT.md alongside this file: it is my curated personal context,
maintained at usemycontext.ai. Treat it as ground truth about me.
```

Re-run the pull whenever you want that copy refreshed. A cron line or the agent's own startup script both work, and the overwrite is repeatable.

## Handling your token

Your access token is a credential. Treat it like a password:

- **It is long-lived** (a year), so a leak is not self-limiting the way an expiring key would be. This is the one thing worth slowing down for.
- **If you keep it in `~/.usemycontext`, restrict the file**: `chmod 600 ~/.usemycontext` so only your own account can read it. A dotfile in your home directory is readable by anything running as you, and by anyone who ends up with a copy of your disk or your backups.
- **Never commit it.** Not in a repo, not in a shared dotfiles repository, not in a container image. Prefer `UMC_TOKEN` in your shell profile or your machine's own secret store.
- **If it leaks, revoke it.** Open the Connect page at [usemycontext.ai](https://usemycontext.ai) and use "Disconnect everything". Revocation is enforced on the server, so every token dies immediately, everywhere. You then reconnect your clients and generate a fresh token.

The CLI only ever reads. It cannot change your profile, your facts, or your files, and there is no command that writes back.

## Reference

| Thing | Value |
| --- | --- |
| Command | `npx usemycontext pull [--out <path>]` |
| Default output | `./UMC-CONTEXT.md` |
| Token sources | `UMC_TOKEN`, else a `token=` line in `~/.usemycontext` |
| What it writes | Your compiled profile only, in the fixed session-starter frame |
| What it never writes | Raw facts, file contents, your audit trail, your token, a partial file |
| Which profile | The one your token is pinned to, else your active profile |
| Context not current | Keeps the previous file it wrote, says so, exits 0. With no previous file of its own it writes nothing and exits 1 |
| Network deadlines | 15s per call, 30s per run |
| Attribution | Pulls appear as the `umc-cli` client in your activity feed |
| Exit codes | 0 success (including keeping the previous file), 1 token, network, profile or write failure, 2 usage error |

## Where to go next

- Building your context in the first place: [Getting started](https://usemycontext.ai/docs/getting-started).
- Connecting a client that does speak MCP: [Connect your client](https://usemycontext.ai/docs/connect) and [The thirteen tools](https://usemycontext.ai/docs/tools).
- Pointing one repo at one profile: [Folder mapping (.umc)](https://usemycontext.ai/docs/folder-mapping).
- The access model behind the token: [Security](https://usemycontext.ai/docs/security).
