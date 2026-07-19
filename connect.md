---
title: Connect your client
description: Exact setup steps for Claude on the web and desktop, Claude Code, Cursor, ChatGPT Developer Mode, and any other MCP client - all doors into the same one server.
sidebar:
  order: 2
---

Every client below connects to the same server, the same account, and the same profile:

```
https://mcp.usemycontext.ai/mcp
```

## Claude (web and desktop)

Open Settings, then Connectors, choose "Add custom connector", and enter `https://mcp.usemycontext.ai/mcp`. Approve the OAuth screen that opens in your browser; the connection syncs across your Claude account. Full walkthrough: [How do I connect Claude to UseMyContext?](https://usemycontext.ai/blog/connect-claude)

## Claude Code

Install the plugin (it adds the server, a `/umc` skill, and automatic folder mapping) with two commands:

```
/plugin marketplace add usemycontext/claude-code-plugin
/plugin install usemycontext@usemycontext
```

Then run `/mcp`, select `usemycontext`, and complete the browser sign-in. Prefer the raw server without the plugin? Run `claude mcp add --transport http usemycontext https://mcp.usemycontext.ai/mcp`. Details: [claude-code-plugin](https://github.com/usemycontext/claude-code-plugin).

## Cursor

Add the server to your `mcp.json`, then connect under Cursor Settings, Tools and MCP Servers:

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

## ChatGPT

On paid ChatGPT plans, enable Developer Mode under Settings, then Apps, then Developer mode, and add a connector by URL with `https://mcp.usemycontext.ai/mcp`. The same OAuth approval and the same profile apply. Every other door (registries, plugins, SDK) is mapped in [Where can you connect UseMyContext from?](https://usemycontext.ai/blog/where-to-connect-usemycontext)

## Any MCP client

Use the universal JSON from the [overview](https://usemycontext.ai/docs). Some clients name the fields differently: `type` may be called `transport`, and some clients (Cursor among them) need only `url`. Whatever the client, the server address is always `https://mcp.usemycontext.ai/mcp` - if a listing points anywhere else, it is not us.
