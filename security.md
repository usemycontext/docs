---
title: Security
description: The security model for IT admins - OAuth 2.1 with PKCE and dynamic client registration, per-tool scopes with audience binding, audited reads, proposal-only writes, server-enforced revocation, structural blindness, EU residency, and self-serve account deletion.
sidebar:
  order: 7
---

For IT admins evaluating a connection:

- Authentication is [OAuth 2.1](https://datatracker.ietf.org/doc/draft-ietf-oauth-v2-1/) with [PKCE](https://datatracker.ietf.org/doc/html/rfc7636) and [dynamic client registration](https://datatracker.ietf.org/doc/html/rfc7591). Approval happens in the user's browser; no API key or token is pasted or written to a file.
- Tokens carry per-tool scopes (`profile:read`, `files:read`, `docs:read`, `updates:write`, `shared:read`) and support audience binding ([RFC 8707](https://datatracker.ietf.org/doc/html/rfc8707) resource indicators).
- Every access an AI makes leaves a record in the user's audit trail.
- The single write tool is proposal-only: it files a pending suggestion the user reviews in the app. Nothing an AI does edits the user's profile or files directly.
- Access is revocable per client, or for all clients at once, from the Connect page. Revocation is enforced on the server: the token dies immediately, everywhere.
- The public-facing surface is structurally blind: it holds no data bindings and physically cannot read user content, which lives on an isolated per-user data plane behind it.
- EU users' data is pinned to EU-jurisdiction storage.
- A user can delete their whole account themselves, from Settings, with no support ticket and no waiting period. Profile, facts, files, projects, share grants, connections and audit trail are hard-deleted from primary systems, deleted data leaves every backup within 3 days, and the account's @handle is released. Deletion starts immediately; the run's duration scales with how much the account holds, and the response is a metadata-only receipt of what was removed, which cannot be re-fetched because the session dies with the account. An active paid plan must be cancelled first, and a user who is the sole admin of a team must disband it first - the server refuses in both cases rather than half-deleting. Deletion is a browser-only action: a token minted for a connected AI client is refused, so nothing an assistant does can erase an account. The named list of what survives is in the [privacy policy](https://usemycontext.ai/privacy#deleting-your-account).
- The only thing the MCP server serves without authentication is static tool metadata (names, descriptions, schemas) for public discovery; every tool call requires a valid token.

The tool-by-tool scope mapping is in [The thirteen tools](https://usemycontext.ai/docs/tools). More detail is in the [privacy policy](https://usemycontext.ai/privacy).
