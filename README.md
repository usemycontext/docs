# UseMyContext documentation

This repository mirrors the documentation for [UseMyContext](https://usemycontext.ai): own your context,
for every AI app. The rendered, canonical docs live at
**[usemycontext.ai/docs](https://usemycontext.ai/docs)** - read them there for the best
experience (sidebar navigation, working cross-links, search engines and AI crawlers are
pointed there too).

**Try it in 30 seconds - no signup.** Sign in as `demo@usemycontext.ai` with code `424242`
(fixed - no email access needed). A shared, read-only demo account with a full profile,
files, and a shared context. Docs: https://usemycontext.ai/docs

## Pages

| Page | What it covers |
|---|---|
| [index.md](./index.md) | Overview: what UseMyContext is, the universal MCP configuration, where to go next |
| [basics.md](./basics.md) | New to this? MCP, context layers, and why you do not need to be a developer |
| [getting-started.md](./getting-started.md) | Create an account and make your first connection |
| [add-context.md](./add-context.md) | What you can add (facts, files, calendars, copied-in storage), projects and @handles, who can see each project |
| [connect.md](./connect.md) | Exact connect steps for Claude, Claude Code, Cursor, ChatGPT, and any MCP client |
| [tools.md](./tools.md) | The thirteen MCP tools, what each does, and the scope it requires |
| [folder-mapping.md](./folder-mapping.md) | Bind a folder to one of your projects with a `.umc` marker (needs our plugin for your coding tool) |
| [cli-pull.md](./cli-pull.md) | `npx usemycontext pull`: write your context to a local file any AI tool can read at startup |
| [security.md](./security.md) | OAuth 2.1 with PKCE, per-tool scopes, audited reads, revocation, the blind surface |
| [plans.md](./plans.md) | What Free, Premium and Team include |
| [embed.md](./embed.md) | Put your public context card, or the signup widget, on any web page |

## About this mirror

The markdown source of truth lives in the UseMyContext monorepo and is rendered to
`usemycontext.ai/docs` at build time. In these mirror copies, the site's root-relative
cross-page links have been rewritten to full `https://usemycontext.ai/docs/...` URLs so
they resolve when read on GitHub. The frontmatter at the top of each file drives the
rendered site's sidebar and can be ignored here. The sign-up form on
`getting-started.md` only renders on the site, so on GitHub use
[usemycontext.ai/docs/getting-started](https://usemycontext.ai/docs/getting-started) to create an account.

## License

[MIT](./LICENSE)
