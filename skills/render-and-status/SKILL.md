---
name: render-and-status
description: Price, approve and follow a render in Zero Page Studio: quote the keyframes and the clip for a picked idea, get the person's explicit yes, approve, and check the background job. Use when someone says render it, draw the stills, make the clip, how much will it cost, or asks whether a job is done. ALWAYS shows the price and waits for the person's yes before anything is spent. NOT for writing the scene (write-scene), NOT for choosing ideas (concept-board), and NOT for explaining plans or balances in general (credits-and-limits).
---

# Render and status

Two things here cost credits, and both are approved by the person in this
conversation before they happen:

| step | tool | what it spends |
|---|---|---|
| draw the keyframes (one still per shot) | `approve` with `what: "keyframes"` | credits, one still each |
| render the clip (one render per shot) | `approve` with `what: "clip"` | credits, priced per shot |

Reading is free: `quote`, `job`, `board`, `idea`, `stats`.

## The order

1. The idea has a scene (`idea` shows a prompt with reference photos). If not,
   write-scene first.
2. `pick` the idea if it is not picked. A render is approved only for a picked
   idea.
3. `quote` with the idea's id. The reply carries `keyframes` (stills still to
   draw, credits), `clip` (one render per timed shot, each with `seconds`,
   `credits` and a `token`), the `balance`, `credits_needed` and `affordable`.
   Optional `provider`, `model`, `duration` (whole-scene only) and `frame`
   pick the renderer; the defaults are the studio's. A quote is valid for one
   hour.
4. **Show the price and ask.** One line, from the quote, never your own
   arithmetic: "2 keyframes for 20 credits, then 2 shots of 5s on LTX for 87
   credits; balance 500. Draw the keyframes?" Then stop and wait.
5. On a clear yes in this turn, `approve` once:
   - keyframes: `approve` with `what: "keyframes"`.
   - clip: `approve` with `what: "clip"`, the `tokens` from the quote, and the
     same `provider` / `model` / `frame` you quoted. Credit is held before
     anything is submitted and released if the render fails.
   Claude will also ask for confirmation on the `approve` call; that prompt is
   part of the approval, not a substitute for the person's yes.
6. The reply carries a `job_id`. Poll `job` every 20 to 30 seconds and report
   when it finishes: the stills, or the clip on the idea. Then `idea` shows
   the result on the card.

Keyframes first, then the clip: a clip anchors on its shot's still. Two
separate approvals, two separate yeses.

## The approval rule

- Never spend without a price shown and a yes in this turn. "Go ahead" from an
  earlier turn, or a yes to a different item or price, does not count.
- One yes, one `approve`. Never call it twice for one yes.
- If `approve` is refused, report its own words and stop:
  - `missing_quote`, `expired`, `stale_content`, `wrong_render`: quote again
    and show the new price. The scene changed, or an hour passed, or the
    renderer choice differs from what was quoted.
  - `not_queued`: pick the idea first.
  - `no_reference`: the scene has no attached photos; back to write-scene.
  - `out_of_credits` / "top up": nothing was charged; point to the studio's
    billing page.
  - `nothing_to_draw`: every shot already has its still.
  - `renderer_unavailable`: the studio's renderer is not configured; tell the
    person and stop.
- Say what happened after every call: what was charged, the job id, or that
  nothing was charged.

## Checking on work (`job`)

`job` returns status, label, progress detail and the result or error. Jobs
live in memory on the server: after a restart the id is unknown and the tool
says so. Then read the idea (`idea`) to see what landed before approving
anything again. A failed render releases its hold; say so.

## What not to do

- Never call `approve` to "see what happens".
- Never pass or print an image URL.
- Never promise a delivery time; renders take a minute or more per shot.
