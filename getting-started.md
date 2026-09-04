---
title: Getting started
description: Create your account inside the first OAuth approval, make your first connection, and try the read-only demo account before creating your own profile.
sidebar:
  order: 2
---

## Three steps, once

1. **Sign in.** Email and a one-time code. No password, no API key.
2. **Add context.** Write or upload what your AI should know, and approve it.
3. **Connect.** One click in [Claude's directory](https://claude.ai/directory/connectors/usemycontext) or [ChatGPT's plugin directory](https://chatgpt.com/plugins/plugin_asdk_app_6a62cbc0ff488191890ba6370456e73e). One paste anywhere else.

The rest of this page is step 1 and step 3 in detail.

## Create your account

Start right here - enter your email, type the one-time code we send you, and your account is created. You can also do this on the web or inside the OAuth approval when you connect a client (all three end in the same account).

<div class="umc-signup" data-source="docs-getting-started"></div>

<script src="/embed.js" defer></script>

## Your account is created in the connect flow

You do not need to sign up before connecting a client. When a client first reaches the server, an OAuth approval page opens in your browser: enter your email, type the one-time code we send you, and approve the client. If the email is new to us, that first sign-in creates your account - there is no separate registration step, and no API key or password anywhere in the flow.

You can also sign in first at [usemycontext.ai](https://usemycontext.ai) with the same email and one-time code; either order ends in the same account.

## First connect

<div class="cc-box cc-compact" style="background:#F6F0E2;border-radius:12px;padding:12px 14px;display:flex;align-items:center;justify-content:space-between;gap:14px;flex-wrap:wrap;margin:0 0 18px">
  <span style="font-size:14px;color:#1B1B17;line-height:1.4">One click to add from the Claude Directory.</span>
  <a href="https://claude.ai/directory/connectors/usemycontext?via=docs" target="_blank" rel="noopener" style="flex:none;background:#1F3D2B;color:#FAF6EC;font-weight:600;font-size:13px;text-decoration:none;padding:8px 15px;border-radius:999px">Connect to Claude</a>
</div>

Using Claude on the web or desktop? That listing is our Community-tier Claude Directory listing - open it, click Connect, and approve the OAuth screen. No URL to paste. For every other client:

1. Pick your client on [Connect your client](https://usemycontext.ai/docs/connect) and add the server address `https://mcp.usemycontext.ai/mcp` (the universal JSON is on the [overview](https://usemycontext.ai/docs)).
2. Approve the OAuth screen that opens in your browser.
3. Your profile starts empty, and your AI onboards you right there in the chat: it asks three short questions (who you are and what you do, what every AI should always know about you, what you are working on right now) and files each answer as a pending suggestion you review and approve - nothing goes in without your say-so. Not in the mood? Say no and build it later at [usemycontext.ai](https://usemycontext.ai) instead: answer a short personalized interview, upload your documents, or connect your web presence - you review and approve what goes in either way. Files, uploads and settings always live at [usemycontext.ai](https://usemycontext.ai).
4. From then on, every conversation in that client starts with your context. Ask it what it knows about you to see the profile in action.

Each connection appears on your Connect page, where you can revoke it (or all clients at once) at any time.

## Try the demo account

Want to see a working profile before creating your own? Sign in with the demo account two ways: on the web at [usemycontext.ai](https://usemycontext.ai) (the "Try the live demo" button), or at the OAuth sign-in when you connect an MCP client to `https://mcp.usemycontext.ai/mcp`. Use `demo@usemycontext.ai` with code `424242`. It is a shared, read-only demo account.
