---
name: concept-board
description: Turn a brief into a few story ideas on the person's Zero Page Studio board and get their yes before anything is written or rendered. Use when someone describes a video, ad, short or scene they want made, asks what is on their board, or wants to decide between ideas. NOT for rendering, pricing or credits (see render-and-status and credits-and-limits), and NOT for choosing a visual look (see look-matching).
---

# Concept board

The board is the person's list of ideas, each a card with a title, a one-line
summary and a status (open, picked, archived, parked, shot). Nothing on this
skill's path spends money: reading, capturing, picking and archiving are free.

## Before you start

Call `board` with no arguments first. The person's open ideas are what is
waiting on them, and adding four new ideas to eleven unreviewed ones buries the
decision that was already the bottleneck. If the board has open cards, offer to
go through those before writing new ones.

If `board` errors with "no account" or a sign-in message, the person has not
created their workspace yet: ask them to sign in once at https://zeropage.studio
(the workspace is created on the first sign-in) and reconnect.

## Turning a brief into ideas

1. Read the brief. Ask at most **three** short questions, and only when the
   answer changes the idea: who it is for, how long (seconds), and what must be
   in frame (a product, a place, a person they will attach photos of). Offer
   choices as short chips, not open questions. Do not ask about budget, tools
   or style here.
2. Propose **two to four** ideas in the chat, each as: a working title, one
   sentence of what we see, one sentence of why it holds attention. Keep them
   different from each other.
3. Wait for the person to choose. Then call `capture` once per chosen idea with
   `title`, `hook` (what we see first) and `logline` (the one-sentence story).
   Put the brief's own words into `spark` so the idea remembers where it came
   from. Do not capture ideas they did not choose.
4. Reply with the new card ids and say that the scene itself is written in the
   studio (or with `generate` where that tool is offered), not here.

## Deciding on existing ideas

- `idea` with a card's id returns it in full, including any written scene
  prompt and its reference images. Read it before advising.
- `pick` marks an idea worth making. It spends nothing; the reply carries
  `keyframes` (how many stills a rendered version would need and their credit
  cost) which you should repeat to the person as information, not as a step
  you take.
- `archive` takes an idea off the board with a `reason`. Use one of the words
  the tool lists (weak concept, no turn, no stake, off-brand, unshootable, seen
  it); the reason is what the studio learns from. Archiving is reversible
  (`archived: false`).
- `shoot` records that an idea was actually made, by any means. Only call it
  when the person says the piece exists.
- `search` finds cards by a phrase when the person refers to an idea by
  description rather than id.

## What to say and not say

- Summaries, not dumps: a board read returns up to 25 cards and says
  `truncated: true` when more matched. Report the count and the few that fit
  what was asked; offer `status` filters rather than paging everything.
- Never invent a card id. Every id you use comes from a `board`, `search`,
  `capture` or `idea` reply in this conversation.
- Never say an idea is rendering, drawn or scheduled. This skill ends at a
  picked card.
