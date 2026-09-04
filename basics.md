---
title: The basics
description: New to this? A plain-language guide to MCP, what a context layer is, and why you do not need to be a developer to use UseMyContext.
sidebar:
  label: The basics
  order: 1
---

If you are not a developer, you are in the right place. UseMyContext.ai works with everyday AI assistants like Claude and ChatGPT, and connecting it is a few clicks, no coding. This page explains the handful of words you will meet in the rest of these docs.

## What is MCP?

MCP, [the Model Context Protocol](https://modelcontextprotocol.io/), is an open standard that lets an AI assistant read from a source you choose and approve. Think of it like a standard wall socket: once your assistant supports MCP, it can plug into UseMyContext the same way it plugs into anything else, with no custom wiring. Claude, ChatGPT, Gemini, and Perplexity all speak MCP, so you set your context up once and any of them can read it.

You do not install or build anything to use MCP. In your assistant you add a "connector" and paste one web address. That is the whole technical part.

## What is a context layer?

A context layer is one place that holds a working picture of you: who you are, what you are working on, and how you like things done. Instead of re-explaining yourself at the start of every chat, your assistant reads that picture from the layer. UseMyContext is that layer, and you own it. More on the idea: [What is a context layer?](https://usemycontext.ai/blog/what-is-a-context-layer)

## Do I need to be a developer?

No. Using UseMyContext is three everyday steps:

1. Sign in with your email and a one-time code (no password, no API key).
2. Write or upload the things you want your AI to know, and approve them.
3. Connect your assistant once by pasting a single web address.

The developer-flavored parts of these docs (config files, command lines) are optional shortcuts for people who want them. The main path is all clicks.

## What can a connected AI actually see?

Only what you put in and approved. Nothing is shared until you say so, access is granted tool by tool, and you can switch any connection off whenever you like. The full list of what an assistant can do is on [The thirteen tools](https://usemycontext.ai/docs/tools), and the safeguards are on [Security](https://usemycontext.ai/docs/security).

## How do I start?

Go to [Getting started](https://usemycontext.ai/docs/getting-started) to make your account and your first connection, then [Connect your client](https://usemycontext.ai/docs/connect) for the exact steps for your assistant.

## Frequently asked questions

### What does MCP stand for?

MCP stands for the Model Context Protocol, an open standard for connecting an AI assistant to sources of context you approve.

### Which AI assistants can read my UseMyContext profile?

Any assistant that [supports MCP](https://modelcontextprotocol.io/clients), including Claude, ChatGPT, Gemini, and Perplexity, plus coding tools like Cursor and VS Code. You connect once and each one reads the same profile.

### Do I need to know how to code to use UseMyContext?

No. You sign in with an email code, write or upload what you want your AI to know, and connect an assistant by pasting one web address. No coding or API keys are required.

### Is it safe to connect my AI to UseMyContext?

Yes. You approve everything that goes in, access is granted per tool, reads are audited, and you can revoke any connection in one click. UseMyContext is also built so its public surface cannot read your data.
