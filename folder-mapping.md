---
title: Folder mapping (.umc)
description: Bind a repo to one of your projects with a .umc file, so a work folder reads your work profile and a side project reads your personal one.
sidebar:
  label: Folder mapping
  order: 4
---

In Claude Code and Cursor, a `.umc` file in a repo root binds that folder to one of your projects, so a work repo reads your work profile and a side project reads your personal one:

```
projectId=p2
handle=@work
```

`projectId` scopes the reads; `handle` is an optional readable label. Both values are shown on the project's page in the web app, and the `/umc` skill can create or change the file for you. With no `.umc` file, the folder reads your account's active profile.
