---
title: Add your context
description: What you can put into UseMyContext - facts, a short interview, your resume, links, files, calendars and copied-in files from Dropbox, Google Drive, kDrive and Notion - plus projects, @handles, who can see each project, and how your AI's suggestions reach you.
sidebar:
  label: Add your context
  order: 3
---

This is step 2 of three: **sign in**, **add context**, **connect**. Everything below happens at [usemycontext.ai](https://usemycontext.ai), on your Profile and Storage pages. Your AI reads what you add here as soon as it is connected.

Your AI gets two things: a short summary built from your facts, which it reads first, and your files, which it reads when a question needs them.

## Tell it about yourself

| Way | What happens |
| --- | --- |
| Type a fact | The box on your Profile page says "Add a fact, paste a link, or drop a file". Type one thing about you and press Add. Edit or delete any fact later. |
| Write a few sentences | On a new, empty profile, say what the profile is for and who you are. We turn it into short facts you can edit, using only what you said. |
| Answer a short interview | Let Your Bot interview you: it asks one easy question at a time and turns your answers into facts. |
| Add your resume or a personal statement | Pick the file, check the facts we pull out of it, edit them, then save. The file itself is kept with your files too. |
| Paste a link | Paste a web address (your site, a profile page) in the same box. We read the page and save a short summary of it as a fact. |
| Let your AI set it up | When you first connect, your AI can ask you one setup question in the chat. See [How your AI adds to it](#how-your-ai-adds-to-it). |

## Upload files

Drop a file on your Profile page, use Attach file, or upload on the Storage page. Your AI can then list, search and read it, and answer from it with the passage it used.

| File | Notes |
| --- | --- |
| PDF | Up to 10 MB each. |
| Word (.docx) | Up to 10 MB each. Old .doc files are not supported: save as .docx or PDF first. |
| Excel (.xlsx) | Up to 2 MB each. Your AI can count, add up and filter the rows of the first sheet exactly. |
| CSV | Like Excel, your AI can count, add up and filter the rows exactly. |
| Text (.txt) and Markdown (.md) | Read as they are. |
| Images (.png, .jpg, .webp) | The text in a picture, like a screenshot or a photo of a page, is read so your AI can search it (for pictures up to 10 MB). |
| Calendar (.ics) | An export from Google, Apple or Outlook Calendar. See [Calendars](#calendars). |

CSV, text, image and calendar files can be up to 20 MB each. Other file types are not accepted. Every file counts toward the storage of the project it is in (see [Projects](#projects)).

## Calendars

Two ways, both on every plan:

- **Upload a calendar file** (.ics). Your AI reads it as a list of events by date.
- **Link your calendar.** On the Storage page, paste your calendar's private link once (Google, Apple iCloud or Outlook all offer one). Your AI sees the past week and the next 60 days, refreshed daily. The link is kept secret: it is stored encrypted and never shown in full again.

Either way, your AI reads only each event's title, time, place and calendar name. It never reads who is invited, the event description, or meeting links, and email addresses and links are removed from what it does read.

## Copy in from other storage

On the Storage page you can pick files from other services. We copy the files you pick into your project; your AI reads the copies, never your account at that service.

| Service | Plans | How |
| --- | --- | --- |
| Dropbox | Every plan, Free included | Choose files in Dropbox's own picker. To update a file, choose it again. |
| Google Drive | Premium, or a member of a paid Team | Sign in with Google and pick files. Press Refresh to copy in newer versions. |
| kDrive | Premium, or a member of a paid Team | Paste a kDrive API token, then pick files. Refresh as above. |
| Notion | Premium, or a member of a paid Team | Paste a Notion integration token, then pick pages. Refresh as above. |

Copied files count toward your project's storage. To remove one, choose Disconnect in its menu on the Storage page: the copy leaves this project and your file at the service is not touched.

## Projects

A project is one profile: its own facts, its own files and its own summary. Keep work and personal apart, or make one per client.

| Plan | Projects | Storage |
| --- | --- | --- |
| Free | 2 | 20 MB per project (40 MB across 2 projects) |
| Premium | 10 | 100 MB per project (1 GB across 10 projects) |

Team details are on [Plans and limits](https://usemycontext.ai/docs/plans).

Every project has its own **@handle**, which you choose when you create it: 3 to 30 characters, and no one else can have it. It is how an AI points at that project, for example "read my profile @my-work". A handle never changes, even if you rename the project, and it stays yours even if you delete the project. Only deleting your whole account frees it.

A connected AI reads your active project unless it is pointed at another one, by its @handle in the chat or, in coding tools, with [folder mapping](https://usemycontext.ai/docs/folder-mapping). If you chose a single project when you connected, that connection always reads that project.

## Who can see a project

Every project starts private. Press Share on the project to choose who else can read it.

| Choice | Who can read it |
| --- | --- |
| Private | Only you and the AI apps you connect. |
| Specific people | People you invite by email. They read the summary only, never your facts or files, and nothing flows back. Stop sharing any time. |
| Public | Anyone with the link to your public page. It is also listed in the public directory, and other members can read it from their AI. They read the summary only. |
| Team | On a paid team, the teammates in your team. They read the summary only. |

People you share with read it from their own AI, through the `shared_context` tool (see [The thirteen tools](https://usemycontext.ai/docs/tools)).

## How your AI adds to it

A connected AI can suggest new facts with one tool, `suggest_update`. A suggestion does not change your profile: it waits on your Profile page, where you Accept or Ignore it, or Accept all when there are several.

The one exception is your first setup answers. On a new, private profile that you have not shared and that has no name, facts or waiting suggestions yet, the answers you give your AI to its setup question save straight to your profile, so you are set up in one chat. That is at most five short answers, within 30 minutes, from one AI app. Each shows in your activity under that app's name, and you can edit or delete it like any other fact. Everything after that waits for your approval.

Nothing an AI does ever touches your files.

## Where to go next

- Connect your AI: [Connect your client](https://usemycontext.ai/docs/connect).
- See every tool a connected AI can use: [The thirteen tools](https://usemycontext.ai/docs/tools).
- Plans, storage and teams: [Plans and limits](https://usemycontext.ai/docs/plans).
