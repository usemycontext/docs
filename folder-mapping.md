---
title: Folder mapping (.umc)
description: Bind a repo to one of your projects with a .umc file, so a work folder reads your work profile and a side project reads your personal one. It works where our plugin for your coding tool is installed.
sidebar:
  label: Folder mapping
  order: 6
---

A `.umc` file in a repo root binds that folder to one of your projects, so a work repo reads your work profile and a side project reads your personal one:

```
projectId=p2
handle=@work
```

`projectId` scopes the reads; `handle` is an optional readable label. Both values are shown on the project's page in the web app. With no `.umc` file, the folder reads your account's active profile.

## It needs our plugin

The `.umc` file only takes effect where our plugin for your coding tool is installed. The plain MCP server ignores it: if you connected by adding just the server address, the file does nothing.

| Tool | What reads the `.umc` file |
| --- | --- |
| Claude Code | Our [Claude Code plugin](https://github.com/usemycontext/claude-code-plugin). Its session-start hook reads the file, and its `/umc` skill can create or change it for you. |
| OpenCode | Our [OpenCode plugin](https://github.com/usemycontext/opencode-plugin): its instructions file tells OpenCode to use the mapping, and its optional plugin file reads the `.umc` file for you. |
| Gemini CLI | Our [Gemini CLI extension](https://github.com/usemycontext/gemini-cli-extension). It tells Gemini to read the file and use the mapping; Gemini CLI has no hook we can use, so this rests on Gemini following that instruction. |
| Cursor | Our Cursor plugin, where it is installed (it also has the `/umc` skill). It is not listed in Cursor's marketplace yet, and the Add to Cursor button on the Connect page connects the plain server without it, so for now most Cursor setups ignore the file: use one of the options below. |

Install steps for Claude Code, OpenCode and Gemini CLI are on [Connect your client](https://usemycontext.ai/docs/connect).

## Without the plugin

You can still point a connection at one project:

- **Name it in the chat.** Ask for the project by its @handle, for example "read my profile @work". This works on a connection to all your projects. See [The thirteen tools](https://usemycontext.ai/docs/tools).
- **Connect to one project only.** When you connect, choose a single project instead of all of them. Every read on that connection then uses that project.
