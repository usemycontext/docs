---
title: Embed
description: Put your public UseMyContext.ai card on any website, or drop the signup widget on your own site, with a two-line snippet and no tracking.
sidebar:
  order: 9
---

UseMyContext.ai gives you two things you can embed on a web page: your own public context card, and the signup widget. Both load from a single small script and need no build step, no account key, and no cookies on the reader's side.

## Embed your public context

Your public context is the curated card behind your @handle - the same card people see at your public page and can read over MCP. Embedding it drops that card straight onto any site you control, the way you would embed a video or a post: the page shows your live public context, and it stays in sync as you update it.

Add two lines where you want the card to appear:

```html
<script async src="https://usemycontext.ai/embed.js"></script>
<div class="umc-profile" data-handle="yourhandle"></div>
```

The script is loaded once per page; you can place as many `div.umc-profile` blocks as you like and each renders the card for its own handle.

### Attributes

| Attribute | Required | What it does |
| --- | --- | --- |
| `data-handle` | Yes | The @handle whose public card to show. Only a project set to public renders; anything else shows nothing. |
| `data-source` | No | A short label for where the embed lives (for example `data-source="my-blog"`). It travels with the read as attribution only. |

### It updates live

The card reads your public context at load time, so when you edit your UseMyContext profile and recompile, every page that embeds your handle shows the new version on its next load. There is nothing to re-paste or redeploy on the host site.

### How viewers can pull it over MCP

The embed is a view of the same public context any AI client can read by handle over MCP. A reader who connects a client to the server can ask for your card with the `shared_context` tool and a `handle` argument - so the card on your page and the context an assistant reads are the same public source, addressed by the same @handle.

## Embed the signup widget

The signup widget lets a visitor create their own UseMyContext account inline, without leaving your page. It is first-party for now: it creates accounts on UseMyContext.ai directly.

```html
<script async src="https://usemycontext.ai/embed.js"></script>
<div class="umc-signup" data-source="your-site"></div>
```

Set `data-source` to a short label for the placement. It is attribution only - it tells us which page a signup came from and carries no personal data.

## How it loads

One script (`embed.js`) handles every embed on the page. It mounts each card or widget in its own lazily-loaded iframe, so nothing below the fold requests anything until it scrolls into view and a slow embed never blocks the rest of your page. Profile embeds set no cookies, and the only thing that travels beyond the public card itself is the optional `data-source` slug - there is no visitor tracking.
