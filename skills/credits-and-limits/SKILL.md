---
name: credits-and-limits
description: Explain what is free and what costs credits in Zero Page Studio, show the balance where a tool reports one, warn before anything expensive, and explain the connector's rate limit and what a 429 means. Use when someone asks how much something costs, what credits are, why a call was refused, why they got "rate limited", or whether an action will charge them. NOT for performing a render or an approval (render-and-status) and NOT for choosing ideas (concept-board).
---

# Credits and limits

## What is free

Reading and deciding never charges: `board`, `idea`, `search`, `stats`,
`sparks`, `tonight`, `images`, `images_for`, `job`. Writing a decision never
charges either: `capture`, `pick`, `archive`, `shoot`, `add_spark`,
`reference` (banking a found image stores it; it does not render anything).

## What costs credits

- **Keyframes** (one still per shot of a scene) and **the clip** are charged
  from the person's credit balance, at a price shown before the approve.
  Today that approve is on the Queue card in the studio; `pick` tells you how
  many stills and how many credits they would be.
- **A rendered reference still** (`imagine_reference`) is charged on the call
  at the price of one still.
- **Writing a scene** (`generate`, when offered) and **a research pass**
  (`research`, when offered) use model credit. They are included with an
  active plan or a credit balance; an account with neither is refused with a
  "subscribe or top up" note.

Credits are bought in the studio under Settings → Billing, where a new
workspace also gets a one-time trial grant. Prices are in credits, never
dollars, in every tool reply; repeat them as returned and do not convert.

## The balance

No connector tool reports the balance by itself yet. Where a tool reply
carries a balance or a "top up" refusal, report that. Otherwise point the
person to https://zeropage.studio/studio/settings, where the balance and the
plan are shown. Never guess a balance.

## Warn before anything expensive

Before any call that charges, say what it is and the credits, and get a yes
(render-and-status has the full rule). "Expensive" means anything above a
single still: a multi-shot keyframe strip, a clip, a research pass. If the
person's balance is unknown, say that too.

## Refusals you will see, and what they mean

- `subscribe_or_top_up` / "top up": the balance or plan does not cover it.
  Nothing was charged. Offer the billing page.
- "daily cap reached": a per-day limit on that kind of render was hit.
  Nothing was charged. Try tomorrow, or a different action.
- "no idea N" / "no finding N" / "no job N": the id is not one this person
  can see. Re-read the board rather than retrying the id.
- `rate_limited` (HTTP 429): too many calls in one minute from this account.
  The response carries `Retry-After` in seconds and the detail names the
  window. Wait that long, then continue; do not loop on it. The default limit
  is generous for a conversation (over a hundred calls a minute) and is only
  reached by polling in a tight loop. Poll `job` every 20 to 30 seconds, not
  continuously.

## What is never charged through this connector

Nothing is posted anywhere, nothing is deleted (archiving hides a card and
can be undone), and no payment method is touched. Buying credits or changing
a plan happens in the studio, never here.
