---
title: The eight tools
description: The full reference for the eight MCP tools a connected AI can call - what each does, whether it reads or writes, and the OAuth scope it requires.
sidebar:
  label: Tools
  order: 3
---

A connected AI sees exactly eight tools. Seven are reads; the single write tool only files a pending suggestion for you to review.

| Tool | Title | What it does | Access | Scope |
| --- | --- | --- | --- | --- |
| `profile` | Your profile | Reads your compiled profile: a curated summary built only from facts you accepted. | Read | `profile:read` |
| `list_files` | List your files | Lists your uploaded files (names and metadata only). | Read | `files:read` |
| `search_files` | Search your files | Finds your documents by filename or metadata. | Read | `files:read` |
| `get_file` | Open a file | Returns a file's full extracted text, size-guarded. | Read | `files:read` |
| `ask_docs` | Ask your documents | Answers from your documents with cited passages. | Read | `docs:read` |
| `query_table` | Query a table exactly | Runs exact, deterministic counts, sums, filters, and grouped totals over one tabular file. | Read | `docs:read` |
| `suggest_update` | Suggest a profile update | Files a pending suggestion for you to review in the app. Pending only: it never edits your profile or files directly. | Write | `updates:write` |
| `shared_context` | Read shared context | Reads context others deliberately shared with you: a share, a public or network @handle, or a teammate on an active team plan. | Read | `shared:read` |

Every tool call requires an OAuth token carrying the matching scope, so a connection can be narrowed to exactly what a client needs. The scopes and the rest of the access model are covered in [Security](https://usemycontext.ai/docs/security).
