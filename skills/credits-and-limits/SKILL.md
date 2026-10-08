---
name: credits-and-limits
description: Explain what is free and what costs credits in Zero Page Studio, read the balance off a quote, warn before anything expensive, and explain a refusal or the connector's rate limit (a 429). Use when someone asks how much something costs, what credits are, what their balance is, why a call was refused, why they got "rate limited", or whether an action will charge them. NOT for performing a render or an approval (render-and-status) and NOT for choosing ideas (concept-board).
---

# Credits and limits

## What is free

Reading and deciding never charges: `board`, `idea`, `search`, `stats`,
`projects`, `project`, `project_chat`, `elements`, `quote`, `job`. Writing a
decision, a scene or a project never charges either: `capture`, `pick`,
`archive`, `shoot`, `write_scene`, `create_project`, `save_chat`. Writing the scene
prompt happens in this chat, so it costs the studio nothing.

## What costs credits

- **Keyframes**: one still per shot of a scene, charged from the person's
  balance when `approve` with `what: "keyframes"` runs. `quote` says how many
  and the credits.
- **The clip**: one render per shot, priced by the renderer, the model, the
  length and the resolution. `quote` says each render's credits and the total.

Both are approved only after the price is shown and the person says yes
(render-and-status). Credit is held before anything is submitted and released
if the render fails.

Credits are bought in the studio under Settings → Billing, where a new
workspace also gets a one-time trial grant. Prices are in credits in every
tool reply; repeat them as returned and do not convert to money.

## The balance

`quote` returns `balance`, `credits_needed` and `affordable`. Report those
three plainly. `exempt: true` means this account is not charged (an operator
account). Without a quote in this conversation, point the person to
https://zeropage.studio/studio/settings rather than guessing.

## Warn before anything expensive

Before any `approve`, say what it is and the credits, and get a yes. Anything
above a single still counts as expensive: a strip of keyframes, any clip. If
`affordable` is false, say so before asking, and offer the billing page
instead of the approve.

## Refusals you will see, and what they mean

- `out_of_credits` / "top up": the balance does not cover it. Nothing was
  charged. Offer the billing page.
- `missing_quote`, `expired`, `stale_content`, `wrong_render`: the price shown
  no longer matches (an hour passed, the scene changed, or the renderer choice
  differs). Quote again. Nothing was charged.
- `not_queued`: pick the idea first. `no_reference`: the scene has no attached
  photos. `nothing_to_draw`: the stills already exist.
- "no idea N" / "no job N": the id is not one this person can see. Re-read the
  board rather than retrying the id.
- "no workspace yet": the person has not signed in at https://zeropage.studio.
  One web sign-in creates the workspace; then reconnect.
- `rate_limited` (HTTP 429): too many calls in one minute from this account.
  The response carries `Retry-After` in seconds. Wait that long, then
  continue; do not loop on it. The limit is generous for a conversation (over
  a hundred calls a minute) and is only reached by polling in a tight loop.
  Poll `job` every 20 to 30 seconds, not continuously.

## What is never charged or changed through this connector

Nothing is posted anywhere, nothing is deleted (archiving hides a card and
can be undone), and no payment method is touched. Buying credits or changing
a plan happens in the studio, never here.
