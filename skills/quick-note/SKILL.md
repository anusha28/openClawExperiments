---
name: quick-note
slug: quick-note
description: Captures short notes from messages starting with `note:` and stores them in memory.
version: 1.0.0
author: Ms. Claw
tags: ["notes", "memory", "capture", "journal"]
metadata: {"clawdbot":{"emoji":"🦞"}}
---

# Quick Note 🦞

## Description
Captures a quick note when a message starts with `note:`.

## Invocation
This skill activates when the user message begins with:
- `note:`

## Inputs
- note_text (string, required)
  The text after `note:`.

## Behavior
When invoked:
1. Capture the text after `note:`.
2. Classify it as one of: `idea`, `task`, `follow-up`, or `reminder`.
3. Rewrite it into one short, clean entry without changing the meaning.
4. Append it to `memory/YYYY-MM-DD.md` using the current date, with a timestamp and label in this format:
   - `- HH:MM — [label] clean entry`
5. If it clearly implies future action, add a short item to the open-loops section in `MEMORY.md`.
   - If no `## Open Loops` section exists, create one at the end.
   - Keep open-loop items short and action-oriented.
   - Do not add duplicates.
6. Reply with a short confirmation that says how it was categorized.

## Output Format
Return a short plain-text confirmation in this style:
- `Got it — logged as [label].`
- `Noted — categorized as [label].`

Keep the confirmation brief.