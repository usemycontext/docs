---
title: Security
description: The security model for IT admins - OAuth 2.1 with PKCE and dynamic client registration, per-tool scopes with audience binding, audited reads, proposal-only writes, server-enforced revocation, structural blindness, and EU residency.
sidebar:
  order: 5
---

For IT admins evaluating a connection:

- Authentication is OAuth 2.1 with PKCE and dynamic client registration. Approval happens in the user's browser; no API key or token is pasted or written to a file.
- Tokens carry per-tool scopes (`profile:read`, `files:read`, `docs:read`, `updates:write`, `shared:read`) and support audience binding (RFC 8707 resource indicators).
- Every read an AI makes is logged to the user's audit trail.
- The single write tool is proposal-only: it files a pending suggestion the user reviews in the app. Nothing an AI does edits the user's profile or files directly.
- Access is revocable per client, or for all clients at once, from the Connect page. Revocation is enforced on the server: the token dies immediately, everywhere.
- The public-facing surface is structurally blind: it holds no data bindings and physically cannot read user content, which lives on an isolated per-user data plane behind it.
- EU users' data is pinned to EU-jurisdiction storage.
- The only thing the MCP server serves without authentication is static tool metadata (names, descriptions, schemas) for public discovery; every tool call requires a valid token.

The tool-by-tool scope mapping is in [The eight tools](https://usemycontext.ai/docs/tools). More detail is in the [privacy policy](https://usemycontext.ai/privacy).
