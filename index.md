---
title: Documentation
description: How to connect any AI client to UseMyContext over MCP, what the thirteen tools do, folder mapping with .umc, the session-starter CLI, the security model, and plans and limits.
sidebar:
  label: Overview
---

## Your context, your control

One place holds the working picture of you - who you are, what you are working on, how you like things done - and any AI client reads it over MCP ([the Model Context Protocol](https://modelcontextprotocol.io/)). You write and approve it once; every connected client starts each conversation already knowing it.

The public surface holds no data of its own. The four internet-facing doors declare zero storage bindings - no database, no file store, no search index - so there is nothing in them to browse or breach. They can only relay a signed request inward to the one service that holds your data, and only ever for the account whose token signed it. Everything below follows from that.

### What changes, in one exchange

Same question, same person, one connection apart.

**Without context**

> **You:** Draft my investor update.
>
> **Assistant:** Happy to help! What company is this for, what stage are you at, and what happened this month?

**Connected**

> **You:** Draft my investor update.
>
> **Assistant:** On it. Leading with the July metrics from your files - the MRR line, both hires, and the roadmap note you saved last week.

### Three steps, once

1. **Sign in.** Email and a one-time code. No password, no API key.
2. **Add context.** Write or upload what your AI should know, and approve it.
3. **Connect.** One click in [Claude's directory](https://claude.ai/directory/connectors/usemycontext) or [ChatGPT's plugin directory](https://chatgpt.com/plugins/plugin_asdk_app_6a62cbc0ff488191890ba6370456e73e). One paste anywhere else.

The whole service is one remote MCP server over Streamable HTTP (the transport also described as [Server-Sent Events](https://html.spec.whatwg.org/multipage/server-sent-events.html), or SSE, and HTTP POST):

```
https://mcp.usemycontext.ai/mcp
```

**Using Claude on the web or Claude Desktop?** The quickest connect is one click from the [Claude Connectors Directory](https://claude.ai/directory/connectors/usemycontext) - our Community-tier listing. Open the listing, click Connect, and approve the OAuth screen. No URL to paste.

Any MCP client that speaks Streamable HTTP can use this universal configuration (also the manual path for Claude). Authentication is browser-based OAuth 2.1 with PKCE, so there is no API key to paste:

```json
{
  "mcpServers": {
    "usemycontext": {
      "type": "http",
      "url": "https://mcp.usemycontext.ai/mcp"
    }
  }
}
```

Claude Desktop reads the same block from its config file at `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows).

> **Building with AI?** Read the raw-text documentation directly at [/llms.txt](https://usemycontext.ai/llms.txt) (the index) or [/llms-full.txt](https://usemycontext.ai/llms-full.txt) (the full corpus), served as clean Markdown for retrieval pipelines, following the [llms.txt standard](https://llmstxt.org/).

## Client compatibility and transport

Every client below reaches the same remote MCP server over Streamable HTTP, the same account, and the same profile. Most sign in over OAuth 2.1 with PKCE (no API key); a few use an access token in an `Authorization: Bearer` header instead.

| Client | Category | Auth |
| --- | --- | --- |
| Claude (web and desktop) | Chat app | OAuth 2.1 (PKCE) |
| ChatGPT (plugin directory) | Chat app | OAuth 2.1 (PKCE) |
| Gemini | Chat app | OAuth 2.1 (PKCE), token-header fallback |
| Perplexity | Chat app | Custom MCP connectors disabled by Perplexity for now |
| Claude Code | Coding tool | OAuth 2.1 (PKCE) |
| Cursor | Coding tool | OAuth 2.1 (PKCE) |
| VS Code | Coding tool | OAuth 2.1 (PKCE) |
| Codex CLI | Coding tool | OAuth 2.1 (PKCE), token-header fallback |
| Cline | Coding tool | Bearer token header |
| Gemini CLI | Coding tool | OAuth 2.1 (PKCE), token-header fallback |
| Goose | Coding tool | Bearer token header |
| OpenCode | Coding tool | OAuth 2.1 (PKCE), token-header fallback |
| Zed | Coding tool | OAuth 2.1 (PKCE), token-header fallback |
| Orca | Coding tool | Registered in Orca's MCP settings; Orca documents no config shape |
| Antigravity | Coding tool | OAuth 2.1 (PKCE), token-header fallback |
| Any MCP client | Anything else | OAuth 2.1 (PKCE) or Bearer token header |
| Apple Shortcuts | Anything else | Bearer token header |
| Linear | Anything else | Bearer token header |

Per-client setup steps are in [Connect your client](https://usemycontext.ai/docs/connect).

## The thirteen tools at a glance

A connected AI sees exactly thirteen MCP tools. Twelve are reads (including `search` and `fetch`, thin aliases of `search_files` and `get_file` added for ChatGPT deep-research compatibility); the single write tool only files a pending suggestion for you to review. Full reference: [The thirteen tools](https://usemycontext.ai/docs/tools).

| Tool | What it does | Access | Scope |
| --- | --- | --- | --- |
| `profile` | Reads your compiled profile, built only from facts you accepted. | Read | `profile:read` |
| `list_profiles` | Lists your own profiles (projects) with each one's name, @handle, and privacy status, and marks which one a connection reads. Metadata only. | Read | `profile:read` |
| `info` | Explains what UseMyContext is, what a connection can and cannot do, and where to manage your account. Static public information only. | Read | `profile:read` |
| `account` | Reports your current plan, projects and storage used against your limits, and where to upgrade. Metadata only. | Read | `profile:read` |
| `list_files` | Lists your uploaded files (names and metadata only). | Read | `files:read` |
| `search_files` | Finds your documents by filename or metadata. | Read | `files:read` |
| `search` | The deep-research alias of `search_files` (ChatGPT's search result shape). | Read | `files:read` |
| `get_file` | Returns one file's full extracted text, size-guarded. | Read | `files:read` |
| `fetch` | The deep-research alias of `get_file` (ChatGPT's fetch result shape). | Read | `files:read` |
| `ask_docs` | Answers from your documents with cited passages. | Read | `docs:read` |
| `query_table` | Runs exact counts, sums, filters, and grouped totals over one tabular file. | Read | `docs:read` |
| `suggest_update` | Files a pending suggestion for you to review. Pending only: it never edits your data. | Write | `updates:write` |
| `shared_context` | Reads context others deliberately shared with you. | Read | `shared:read` |

## Integration guides and common workflows

- **Create an account and make my first connection**: [Getting started](https://usemycontext.ai/docs/getting-started) - the account comes free with your first OAuth approval, and a read-only demo account lets you look around first.
- **Connect a specific client**: [Connect your client](https://usemycontext.ai/docs/connect) - exact steps for Claude (web and desktop), Claude Code, Cursor, ChatGPT (one click from its plugin directory), and any other MCP client.
- **See what a connected AI can actually do**: [The thirteen tools](https://usemycontext.ai/docs/tools) - every tool, what it does, and the scope it requires.
- **Point a repo at the right profile**: [Folder mapping (.umc)](https://usemycontext.ai/docs/folder-mapping) - bind a folder to one of your projects in Claude Code or Cursor.
- **Feed a tool that reads files, not MCP**: [Session starter (usemycontext pull)](https://usemycontext.ai/docs/cli-pull) - one command writes your context to a local file any AI tool can read at startup.
- **Evaluate the security model**: [Security](https://usemycontext.ai/docs/security) - OAuth 2.1 with PKCE, per-tool scopes, audited reads, server-enforced revocation, and the structurally blind public surface, written for IT admins.
- **Understand plans and limits**: [Plans and limits](https://usemycontext.ai/docs/plans) - what Free and Premium include, and where Teams fits.
- **Put your public card on a site**: [Embed](https://usemycontext.ai/docs/embed) - a two-line snippet to embed your public context, plus the signup widget, with no tracking.

## Frequently asked questions

### Does UseMyContext require a local API key?

No. UseMyContext authenticates with browser-based OAuth 2.1 using PKCE, so there is no API key to generate, paste, or rotate.

### Which transport protocol does UseMyContext use?

UseMyContext runs as a remote Model Context Protocol (MCP) server over Streamable HTTP, the transport also described as Server-Sent Events (SSE) and HTTP POST, at `https://mcp.usemycontext.ai/mcp`.

### Which AI clients can connect to UseMyContext?

Claude on the web and desktop, Claude Code, Cursor, ChatGPT (one click from its plugin directory), and any other MCP client that speaks Streamable HTTP. Every client reads the same account and the same profile.

### Do I need a browser extension to use UseMyContext?

No. A connected assistant reads your context natively over MCP, so there is nothing to install beyond adding the server in your client's connector settings.

## More

- [Support](https://usemycontext.ai/support): how to reach us, and the common set-up guides.
- [Privacy policy](https://usemycontext.ai/privacy): what UseMyContext holds, what it cannot read, and your rights.
- [GitHub](https://github.com/usemycontext): plugin sources and per-client configuration examples.
- [usemycontext on npm](https://www.npmjs.com/package/usemycontext): a typed client and React hook for building your own app over MCP.
