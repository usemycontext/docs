---
title: Documentation
description: How to connect any AI client to UseMyContext over MCP, what the eight tools do, folder mapping with .umc, the security model, and plans and limits.
sidebar:
  label: Overview
---

## What UseMyContext is

UseMyContext is a personal context layer: one profile of who you are and what you are working on, kept in your own account, that any AI client can read over MCP (the Model Context Protocol). You write and approve the context once; every connected AI starts each conversation already knowing it.

The whole service is one remote MCP server (Streamable HTTP):

```
https://mcp.usemycontext.ai/mcp
```

Any MCP client that speaks Streamable HTTP can use this universal configuration. Authentication is OAuth in your browser, so there is no API key to paste:

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

## I want to...

- **Create an account and make my first connection**: [Getting started](https://usemycontext.ai/docs/getting-started) - the account comes free with your first OAuth approval, and a read-only demo account lets you look around first.
- **Connect a specific client**: [Connect your client](https://usemycontext.ai/docs/connect) - exact steps for Claude (web and desktop), Claude Code, Cursor, ChatGPT Developer Mode, and any other MCP client.
- **See what a connected AI can actually do**: [The eight tools](https://usemycontext.ai/docs/tools) - every tool, what it does, and the scope it requires.
- **Point a repo at the right profile**: [Folder mapping (.umc)](https://usemycontext.ai/docs/folder-mapping) - bind a folder to one of your projects in Claude Code or Cursor.
- **Evaluate the security model**: [Security](https://usemycontext.ai/docs/security) - OAuth 2.1 with PKCE, per-tool scopes, audited reads, server-enforced revocation, and the structurally blind public surface, written for IT admins.
- **Understand plans and limits**: [Plans and limits](https://usemycontext.ai/docs/plans) - what Free and Premium include, and where Teams fits.

## More

- [Support](https://usemycontext.ai/support): how to reach us, and the common set-up guides.
- [Privacy policy](https://usemycontext.ai/privacy): what we hold, what we cannot read, and your rights.
- [GitHub](https://github.com/usemycontext): plugin sources and per-client configuration examples.
- [usemycontext on npm](https://www.npmjs.com/package/usemycontext): a typed client and React hook for building your own app over MCP.
