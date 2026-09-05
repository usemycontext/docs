---
title: Connect your client
description: Setup steps for every supported client - Claude, ChatGPT, Gemini, Perplexity, Claude Code, Cursor, VS Code, Codex CLI, Cline, Gemini CLI, Goose, OpenCode, Zed, Orca, Antigravity, Apple Shortcuts, Linear, and any other MCP client - all doors into the same one server.
sidebar:
  order: 3
---

You are on step 3 of three: **sign in**, **add context**, **connect**. If you have not done the first two, start at [Getting started](https://usemycontext.ai/docs/getting-started).

**In Claude, ChatGPT or Cursor, this is one click** - UseMyContext.ai is listed in [Claude's connector directory](https://claude.ai/directory/connectors/usemycontext) and [ChatGPT's plugin directory](https://chatgpt.com/plugins/plugin_asdk_app_6a62cbc0ff488191890ba6370456e73e), and Cursor has an **Add to Cursor** button on the Connect page inside the app, so there is no URL to paste. Everywhere else, you paste one address, once.

Every client below reaches the same remote MCP server over Streamable HTTP, the same account, and the same profile:

```
https://mcp.usemycontext.ai/mcp
```

Most clients connect the same way: add a custom or remote MCP server, paste the URL, and sign in with your email and a one-time code over OAuth. A few clients cannot do the browser sign-in yet and use an access token in an `Authorization: Bearer` header instead; you generate that token on the Connect page inside the app, under "Advanced - manual setup". Each client below notes which path it takes.

## Chat apps

### Claude (web and desktop)

<div class="cc-box cc-compact" style="background:#F6F0E2;border-radius:12px;padding:12px 14px;display:flex;align-items:center;justify-content:space-between;gap:14px;flex-wrap:wrap;margin:0 0 18px">
  <span style="font-size:14px;color:#1B1B17;line-height:1.4">One click to add from the Claude Directory.</span>
  <a href="https://claude.ai/directory/connectors/usemycontext?via=docs" target="_blank" rel="noopener" style="flex:none;background:#1F3D2B;color:#FAF6EC;font-weight:600;font-size:13px;text-decoration:none;padding:8px 15px;border-radius:999px">Connect to Claude</a>
</div>

The fastest path is the Claude Directory - one click, no URL to paste.

1. Open the UseMyContext.ai listing in the Claude Directory at [claude.ai/directory/connectors/usemycontext](https://claude.ai/directory/connectors/usemycontext) - our Community-tier listing - and click Connect.
<!-- SCREENSHOT: the Claude Directory "Connect" button on the UseMyContext.ai listing goes here (added later - do not insert a placeholder image). -->
2. Approve the OAuth screen that opens in your browser, then sign in with your email and the code we send. That is the whole setup.

In a chat, open the tools menu and make sure UseMyContext is enabled. Full walkthrough: [How do I connect Claude to UseMyContext?](https://usemycontext.ai/blog/connect-claude)

Prefer to add it manually? Open Settings, then Connectors, choose "Add custom connector", enter `https://mcp.usemycontext.ai/mcp`, and approve the OAuth screen. It reaches the same server and the same account.

### ChatGPT

<div class="cc-box cc-compact" style="background:#F6F0E2;border-radius:12px;padding:12px 14px;display:flex;align-items:center;justify-content:space-between;gap:14px;flex-wrap:wrap;margin:0 0 18px">
  <span style="font-size:14px;color:#1B1B17;line-height:1.4">Official ChatGPT plugin. Nothing to paste.</span>
  <a href="https://chatgpt.com/plugins/plugin_asdk_app_6a62cbc0ff488191890ba6370456e73e" target="_blank" rel="noopener" style="flex:none;background:#1F3D2B;color:#FAF6EC;font-weight:600;font-size:13px;text-decoration:none;padding:8px 15px;border-radius:999px">Install in ChatGPT</a>
</div>

UseMyContext.ai is published in the [ChatGPT plugin directory](https://chatgpt.com/plugins/plugin_asdk_app_6a62cbc0ff488191890ba6370456e73e), so there is nothing to paste. Open that link and click "Install plugin", or find it from inside ChatGPT: Settings, then Plugins, then "Browse plugins", search for `usemycontext`, open the UseMyContext.ai result and click "Install plugin". Sign in with your email and code when ChatGPT asks, then pull it into any chat with `@UseMyContext`.

Prefer to add it by hand, or on an older ChatGPT? On paid plans, open Settings, then Apps, open Advanced settings and turn on Developer mode. Back in Apps click "Create app", name it UseMyContext, paste `https://mcp.usemycontext.ai/mcp` as the Connection, and click Create to sign in. On older versions this lives under Settings, then Connectors. It reaches the same server and the same account.

Two ChatGPT habits keep answers accurate. Tag the app in each message that should use your context - type `@UseMyContext` or pick it from the plus menu; untagged replies answer from ChatGPT's own memory, not your profile. And a connection reads one profile at a time - your active one by default - so facts on your other profiles stay out of scope until you ask for a profile by its @handle or switch profiles at [usemycontext.ai](https://usemycontext.ai).

### Gemini

Read this first: consumer Gemini only accepts a custom MCP server through Gemini Spark's custom apps, and Google gates that. You must be 18 or over and in the US, signed in with a personal Google Account (work and school accounts are excluded), on a paid Spark tier, with Keep Activity on, and you can only add it from a desktop browser. If that is not you, there is no consumer Gemini route today - use Gemini CLI instead (its section is under Coding tools below), which has none of these conditions.

If it is you: on a computer, open gemini.google.com, then Settings & help, then Connected Apps. Under "Custom apps for Spark" choose "Add a custom app link to get started", enter `https://mcp.usemycontext.ai/mcp`, and click Next. UseMyContext opens its sign-in; sign in with your email and the code we send. Once connected from the web, Google says the connection also works in the Gemini mobile app.

What does not work: the Gemini app's own Settings, then Connectors (or Extensions), has no place to add a custom MCP server. This page said otherwise until 2 August 2026 and it was wrong. The steps above are Google's own, from its help page for custom apps for Spark, read 28 July 2026; we have not been able to walk them ourselves because they need a US personal account on a paid Spark tier. If Gemini asks you for a client ID and secret, it did not pick up our automatic registration - tell us and we will fix it.

### Perplexity

Perplexity does take custom remote MCP connectors. Its help centre documents adding one from Account settings, and its changelog puts the feature on the Pro, Max and Enterprise plans, not on Free. On Enterprise an admin decides whether members may add their own remote connectors, and that is off by default.

What we cannot tell you is whether UseMyContext.ai connects there, because we have not tried it. We publish steps for a client only once one of us has walked them end to end on a real account, and nobody here has a paid Perplexity plan yet. So this section carries no steps rather than a guess. If you are on Pro or Max and you try it, tell us and we will write it up.

## Coding tools

### Claude Code

The fastest path is the open-source plugin, installed with two commands:

```
/plugin marketplace add usemycontext/claude-code-plugin
/plugin install usemycontext@usemycontext
```

Then run `/mcp`, pick `usemycontext`, and choose Authenticate to sign in. Prefer the raw server without the plugin? Run `claude mcp add --transport http usemycontext https://mcp.usemycontext.ai/mcp` (add `--scope user` to use it in every project). On a headless box, `claude mcp login usemycontext` does the sign-in from the shell. Details: [claude-code-plugin](https://github.com/usemycontext/claude-code-plugin).

### Cursor

The fastest path is the **Add to Cursor** button, which you will find on the Connect page inside the app and on the last step of setup. It opens Cursor with UseMyContext already filled in: click Install, then sign in with your email and the code we send. Nothing to paste.

Prefer to add it by hand? Add the server to your `mcp.json` (a remote server needs only `url`, no `type`), then connect under Cursor Settings, Tools and MCP Servers, and sign in when Cursor opens the browser:

```json
{
  "mcpServers": {
    "usemycontext": {
      "url": "https://mcp.usemycontext.ai/mcp"
    }
  }
}
```

The [cursor-plugin](https://github.com/usemycontext/cursor-plugin) packages the same server with folder mapping for Cursor's plugin marketplace.

### VS Code

Open the Command Palette (`Cmd+Shift+P` or `Ctrl+Shift+P`) and run "MCP: Add Server". Choose HTTP, paste `https://mcp.usemycontext.ai/mcp`, name it UseMyContext, and pick Global (or Workspace), then sign in in-editor. Editing `.vscode/mcp.json` by hand uses a `servers` block:

```json
{
  "servers": {
    "usemycontext": {
      "type": "http",
      "url": "https://mcp.usemycontext.ai/mcp"
    }
  }
}
```

### Codex CLI

Open `~/.codex/config.toml` and add a server block:

```toml
[mcp_servers.usemycontext]
url = "https://mcp.usemycontext.ai/mcp"
```

Sign in over OAuth with `codex mcp login usemycontext`. No OAuth? Add `bearer_token_env_var = "UMC_TOKEN"` to the block and export `UMC_TOKEN` with an access token from the app's Connect page.

### Cline

In Cline, open the MCP Servers icon, then Remote Servers, then Edit Configuration. Add UseMyContext as a `streamableHttp` server. Cline's OAuth over Streamable HTTP is still patchy, so it uses an access token in an `Authorization: Bearer` header:

```json
{
  "type": "streamableHttp",
  "url": "https://mcp.usemycontext.ai/mcp",
  "headers": { "Authorization": "Bearer YOUR_TOKEN" }
}
```

### Gemini CLI

Open `~/.gemini/settings.json` and add UseMyContext under `mcpServers`, using `httpUrl` for a remote Streamable HTTP server:

```json
{
  "mcpServers": {
    "usemycontext": { "httpUrl": "https://mcp.usemycontext.ai/mcp" }
  }
}
```

Start `gemini` and it opens the browser sign-in. If it cannot sign in over OAuth, add `"headers": { "Authorization": "Bearer YOUR_TOKEN" }` with a token from the app's Connect page.

### Goose

In Goose, open Settings, then Extensions, then "Add custom extension". Set Type to Streamable HTTP, name it UseMyContext, and set the endpoint to `https://mcp.usemycontext.ai/mcp`. Goose's OAuth discovery cannot reach us yet, so add one Request Header: name `Authorization`, value `Bearer YOUR_TOKEN` (the word Bearer, a space, then an access token from the app's Connect page).

### OpenCode

Open `opencode.json` (or `opencode.jsonc`) and add UseMyContext under the `mcp` block as a `remote` server:

```json
{
  "mcp": {
    "usemycontext": {
      "type": "remote",
      "url": "https://mcp.usemycontext.ai/mcp",
      "oauth": {}
    }
  }
}
```

No client ID to paste: OpenCode sees our 401, finds our authorization server and registers itself over RFC 7591 dynamic client registration. The empty `oauth` block only makes that explicit, since OAuth auto-detection is already on by default (set `"oauth": false` to turn it off and use a header instead). Start OpenCode and it opens the browser sign-in; if it does not, run `opencode mcp auth usemycontext` to force it.

### Zed

Zed calls MCP servers context servers. The quickest path is Settings, then AI, then MCP Servers: click "Add Server", choose "Add Remote Server", and give it `https://mcp.usemycontext.ai/mcp`. That writes an entry into your settings file, which you can also open with the `zed: open settings file` action and edit by hand:

```json
{
  "context_servers": {
    "usemycontext": {
      "url": "https://mcp.usemycontext.ai/mcp"
    }
  }
}
```

A remote server needs only the `url` - no `type`, no `command`. When no `Authorization` header is set, Zed prompts you through the standard MCP OAuth flow, so sign in with your email and the code we send. Back in Settings, AI, MCP Servers, the indicator dot beside the server name turns green when it is connected.

### Orca

Orca is an agent development environment: it runs several coding agents side by side, each in its own git worktree, with its own skills registry, MCP registration and hooks.

Register the server under Settings, then Integrations, then MCP, with the address `https://mcp.usemycontext.ai/mcp`. That is the path Orca's own docs give for MCP endpoints, and they say the tools then "appear inside agent CLIs that support MCP".

Where we have to stop being specific: Orca does not publish a config-file shape for a remote MCP server the way every other client on this page does, so there is no JSON block here to paste, and we have not walked the sign-in ourselves. What helps is that the agents Orca runs are ones this page already covers - Claude Code, Codex CLI and OpenCode. If the Orca registration does not carry the OAuth sign-in through, connect the underlying agent directly with its section above; Orca runs that agent as-is and it reads its own MCP config. If you get it working either way, tell us and we will make this section exact.

### Antigravity

Antigravity is Google's agent IDE. Add UseMyContext from Settings, then Customizations, then Installed MCP Servers, and click "Add MCP". To edit the config by hand, open `mcp_config.json`:

```json
{
  "mcpServers": {
    "usemycontext": {
      "serverUrl": "https://mcp.usemycontext.ai/mcp"
    }
  }
}
```

Mind the key name. A remote server must use `serverUrl`; Antigravity's docs say the legacy `url` and `httpUrl` fields are not supported, so a block copied from the Cursor or Gemini CLI sections above will not connect here. Antigravity handles OAuth automatically for servers that support dynamic client registration, which ours does, so sign in with your email and the code we send. If it does not prompt, open Agent Settings, then Customizations, and click Authenticate beside UseMyContext.

## Anything else

### Any MCP client

In any MCP-capable client, add a remote or custom MCP server (Streamable HTTP) and paste `https://mcp.usemycontext.ai/mcp`. If the client speaks OAuth over MCP, UseMyContext opens its sign-in (your email and a one-time code). If it does not, send an `Authorization: Bearer YOUR_TOKEN` header with an access token from the app's Connect page. Some clients name the fields differently: `type` may be called `transport`, and some need only `url`. Whatever the client, the server address is always `https://mcp.usemycontext.ai/mcp` - if a listing points anywhere else, it is not us.

### Apple Shortcuts

Add to your context, or hear what your AI knows, by voice or text from iPhone, iPad, or Mac, without opening the app. Build a Shortcut with a "Get Contents of URL" action pointed at `https://mcp.usemycontext.ai/mcp`, method POST, an `Authorization: Bearer YOUR_TOKEN` header (token from the app's Connect page), and a JSON body calling one MCP tool. To add a note, call `suggest_update` (it files a pending suggestion you approve in the app); to read your profile aloud, call `profile`. Full recipe: the in-app Connect page, Apple Shortcuts.

### Linear

Linear's custom MCP dialog signs in with a header, not the email OAuth flow. Generate an access token on the app's Connect page (the Linear card), then in Linear open Workspace settings, Security, and enable MCP servers (needs an admin). Add a custom server URL of `https://mcp.usemycontext.ai/mcp`, then under your own Settings, Agent personalization, MCP servers, pick it and add the Authorization header with your token.
