---
title: The thirteen tools
description: The full reference for the thirteen MCP tools a connected AI can call - what each does, whether it reads or writes, and the OAuth scope it requires.
sidebar:
  label: Tools
  order: 4
---

A connected AI sees exactly thirteen tools. Twelve are reads; the single write tool only files a pending suggestion for you to review. Two of the reads, `search` and `fetch`, are thin aliases of `search_files` and `get_file`, added for ChatGPT deep-research compatibility - the same data and permissions, returned in the result shape that surface requires.

| Tool | What it does | When you would use it | Access | Scope |
| --- | --- | --- | --- | --- |
| `profile` | Reads your compiled profile: a curated summary built only from facts you accepted. | Open a fresh chat and it already knows your role, your stack, your tone. | Read | `profile:read` |
| `list_profiles` | Lists your own profiles (projects) with each one's name, @handle, and privacy status, and marks which one a connection reads by default (an account-wide connection can read any of them). Metadata only. | Ask which profile this chat is reading - work, personal, or a client. | Read | `profile:read` |
| `info` | Explains what UseMyContext is, what a connection can and cannot do, and where you go to manage your account. Static public information only, no user data. | "What can you actually do here?" - answered honestly, limits included. | Read | `profile:read` |
| `account` | Reports your current plan, how many projects and how much storage you are using against your limits, and where to upgrade. Metadata only. | Check how close you are to your storage limit before a big upload. | Read | `profile:read` |
| `list_files` | Lists your uploaded files (names and metadata only). | Ask what this profile already holds before you add more. | Read | `files:read` |
| `search_files` | Finds your documents by filename or metadata. | Ask your AI to find that one file you saved five months ago. | Read | `files:read` |
| `search` | The deep-research alias of `search_files`: the same search, returned in the id/title/url result shape ChatGPT deep research requires. | ChatGPT deep research finds your files the way Claude does. | Read | `files:read` |
| `get_file` | Returns a file's full extracted text, size-guarded. | Have it read the whole brief before it drafts a word. | Read | `files:read` |
| `fetch` | The deep-research alias of `get_file`: the same full-text read (same audit, same size guard), returned in the id/title/text shape ChatGPT deep research requires. | ChatGPT pulls a full document into a deep-research run. | Read | `files:read` |
| `ask_docs` | Answers from your documents with cited passages. | "What did we promise the client in March?" - answered with the exact passage. | Read | `docs:read` |
| `query_table` | Runs exact, deterministic counts, sums, filters, and grouped totals over one tabular file. | "How much did I invoice in Q2?" - counted from the rows, never estimated. | Read | `docs:read` |
| `suggest_update` | Files a pending suggestion for you to review in the app. Pending only: it never edits your profile or files directly. | Mention you changed roles once. Approve it once. Every AI knows. | Write | `updates:write` |
| `shared_context` | Reads context others deliberately shared with you: a share, a public or network @handle, or a teammate on an active team plan. | "Brief me on Ana before our call" - from what she chose to share. | Read | `shared:read` |

## When a connected AI reaches for a tool on its own

The server does not only tell a connected AI what each tool does, it tells it when to reach for one unprompted, and every client that reads the live tool list gets that guidance with no configuration from you. Two triggers close the loop around a conversation. At the start: when a question touches you personally - your background, work, history, projects, or documents - it is told to check `profile` and `ask_docs` before saying it does not know or guessing, so you should not have to name UseMyContext for your own context to be used. At the end: when a conversation has surfaced something new and durable about you and is wrapping up (you say thanks or goodbye, or the task completes), it is told to offer to save that with `suggest_update` before the context is lost. A save is a pending suggestion you review and accept on your Profile page, and nothing is ever written to your files.

This is guidance we give the client, not a promise about what it does with it: how closely an AI follows either trigger is up to that client, and some need a nudge. ChatGPT is the clearest case - an untagged message answers from ChatGPT's own memory, so tag `@UseMyContext` in each message that should use your context. The per-client habits are in [Connect your client](https://usemycontext.ai/docs/connect).

## Pointing a call at one profile

If you have more than one profile, an account-wide connection reads whichever one is active unless the call says otherwise. Every profile-scoped tool above (`profile`, `list_files`, `search_files`, `search`, `get_file`, `fetch`, `ask_docs`, `query_table`, `suggest_update`) takes an optional profile selector: either the internal `projectId` from `list_profiles`, or the profile's own public `@handle`, so you can just say "read my profile @my-work" and mean it.

The selector only ever addresses **your own** profiles. A handle belonging to someone else, and a handle nobody holds, are refused identically - so nobody can use this to test whether a private handle exists - and a handle we cannot match is refused outright rather than quietly serving a different profile. A connection you narrowed to one profile ignores the selector entirely: the token's own binding always wins. Reading a context somebody else shared with you or published is a different tool, `shared_context`.

Every tool call requires an OAuth token carrying the matching scope, so a connection can be narrowed to exactly what a client needs. The scopes and the rest of the access model are covered in [Security](https://usemycontext.ai/docs/security).
