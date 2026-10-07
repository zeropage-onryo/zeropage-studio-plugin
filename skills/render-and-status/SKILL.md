---
name: render-and-status
description: Start, price, approve and follow work that spends credits in Zero Page Studio: writing a scene from a direction, drawing keyframes, rendering a clip, and checking a background job. Use when someone says render, generate, make it, draw the stills, how much will it cost, or asks whether a job is done. ALWAYS shows the price and waits for the person's explicit yes before anything is spent. NOT for choosing ideas (concept-board), NOT for references (look-matching), and NOT for explaining plans or balances in general (credits-and-limits).
---

# Render and status

Three things here cost something, and every one of them is approved by the
person in this conversation before it happens:

| step | tool | what it spends |
|---|---|---|
| write a scene from a direction | `generate` (when offered) | model credit; a background job |
| draw the keyframes / render the clip | `quote` then `approve` (see "Today" below) | credits from the person's balance |
| render one reference still | `imagine_reference` | credits from the person's balance |

Reading is free: `board`, `idea`, `job`, `stats`.

## The approval rule

1. **Show the price first.** Before any spending call, state in one line what
   will be made, how many items (shots, stills), and the cost in credits,
   taken from a tool reply in this conversation (the `keyframes` block of a
   `pick`, a `quote` reply, the `credits` line of a tool description). Never
   estimate a price yourself.
2. **Ask, and wait.** "Draw 3 keyframes for 30 credits?" Then stop. A yes is a
   clear sentence from the person in this turn. "Go ahead" from an earlier
   turn, or an approval for a different item or price, does not count.
3. **One approval, one spend.** Do not call the spending tool twice for one yes.
   If a call is refused (balance, cap, or a stale quote), report the refusal's
   own words and ask what they want to do; do not retry.
4. **Say what happened.** After the call, report what was charged and the job
   or card id. If nothing was charged (a refusal, a note), say that.

## Writing a scene (`generate`)

Only offered when the connector has it switched on. It takes a direction: a
`finding_id` from `sparks` / `tonight`, or the spark text, and an optional
`goal`. It writes the scene, grounds it on the references banked behind the
direction, scores it and parks it on the board for a decision. It **never
renders**. It returns a job id; poll with `job` every 20 to 30 seconds and
report the parked card id when the job finishes. Treat it as a spend: say it
uses model credit and get a yes.

## Today: keyframes and the clip are approved in the studio

Until the `quote` and `approve` tools below ship, the priced approve for
keyframes and the clip lives on the Queue card in the studio. After a `pick`,
tell the person the `keyframes` count and credits from the reply and send them
to https://zeropage.studio/studio/queue to press "Draw keyframes" and the
render approve, where the same price is shown. Do not try to render another
way.

<!-- PLANNED: quote-then-approve in chat.
     Decided 2026-10-07; the tools are not yet on the server. When they are,
     this block replaces the "Today" section above:

## Keyframes and the clip (`quote` → `approve`)

1. `quote` with the picked card's id returns the stills to draw and the clip
   to render, each priced in credits, the person's balance, and a signed
   token that is valid for one hour.
2. Show the price exactly as returned and ask for a yes (the approval rule).
3. `approve` with the token. It re-checks the token, holds the credits
   before anything is submitted, refuses above the quoted price, and starts
   a background job. Claude will also ask for confirmation on this call; that
   prompt is part of the approval, not a substitute for the person's yes.
4. Poll `job` and report the clip or stills when finished. A failed job
   releases the hold; say so.
-->

## A reference still (`imagine_reference`)

Only when the person asked for a rendered reference frame for a direction that
has no real photograph. Write the hook frame (what is on screen in frame one
and its light) with them, show the credit cost from the tool's description,
get the yes, call it once. The reply says what was charged, or a note when the
balance or the daily cap refused it; never retry a refusal.

## Checking on work (`job`)

`job` with a job id returns status, label, progress detail and the result or
error. Jobs live in memory on the server: after a restart the id is unknown
and the tool says so. Then look at the board (`board`, `idea`) for the card the
job was producing before starting anything again.

## What not to do

- Never spend without a price shown and a yes in this turn.
- Never pass or print an image URL.
- Never call `approve`, `imagine_reference` or `generate` to "see what
  happens".
