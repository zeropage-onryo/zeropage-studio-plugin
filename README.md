# Zero Page Studio

Run your [Zero Page Studio](https://zeropage.studio) idea board from a
conversation with Claude: turn a brief into a few story ideas you approve
before anything is written or rendered, set the look from reference images you
attach, and start and follow renders with the price shown and your approval
first.

Zero Page Studio is an AI pre-production studio for creators and filmmakers.
You give it an idea and reference images; it writes one paste-ready scene
prompt, draws the keyframes, and renders the clip, one shot at a time, with a
price in front of every spend.

## What the plugin contains

- **A connector**: the studio's remote MCP server at
  `https://zeropage-studio.fly.dev/mcp`. You sign in with your Zero Page Studio
  account; the tools read and write your own board and nobody else's.
- **Four skills** that teach Claude the studio workflow:
  - `concept-board` — a brief becomes two to four ideas you choose between, then
    cards on your board. Reads and decisions only.
  - `look-matching` — the visual look from reference images, by id, with the
    page each came from. The studio grounds on photographs you attach, never on
    a name.
  - `render-and-status` — writing a scene, drawing keyframes, rendering a clip
    and following a job, always with the price shown and your yes first.
  - `credits-and-limits` — what is free, what costs credits, what a refusal or
    a 429 means.

## Before you use it

1. Sign in once at https://zeropage.studio. Your workspace is created on the
   first sign-in and comes with a one-time trial grant of credits. The
   connector cannot create a workspace by itself; until you have one it
   answers "no account".
2. Add the plugin, then connect the Zero Page Studio connector on its
   Connectors tab and approve the sign-in.

## A 60-second demo

1. "What's on my board?" → Claude calls `board` and lists your open ideas.
2. "I want a 10-second product spot for a matte black water bottle on a wet
   gym floor, no people." → Claude asks at most three short questions, proposes
   three ideas, and captures the one you pick as a card.
3. "Find me references for that light." → Claude searches for frames by light
   and surface, shows what each candidate is, and banks the two you choose
   behind the idea's direction, with their source pages.
4. "Pick it." → Claude marks the card picked and tells you how many keyframes
   a render would need and what they cost in credits.
5. "Draw them." → Claude shows the price and waits for your yes. Today the
   priced approve is on the Queue card in the studio, where Claude sends you;
   when the connector's `quote` and `approve` tools ship, the same approval
   happens in the chat.

## Data

The connector sends the text you type for an idea (title, hook, logline, a
direction), reference-image search phrases, and the ids of cards and images to
your own Zero Page Studio account at `zeropage-studio.fly.dev`, over HTTPS, with
the OAuth sign-in you approve. The studio stores what you capture, pick and
archive on your board, and the reference images you bank, under your account.
Scene writing, keyframes and renders run on the studio's AI providers and are
charged in credits from your balance after a price is shown; see the studio's
[privacy policy](https://zeropage.studio/privacy) and
[terms](https://zeropage.studio/terms) for what is kept and for how long. The
plugin itself runs no code, stores nothing, and sends nothing anywhere else.

Nothing in the plugin can buy credits, change a plan, post anywhere, or delete
your work (archiving hides a card and can be undone).

## Rate limit

The connector allows a generous number of calls per minute per account (over a
hundred). A `429` carries `Retry-After` in seconds. Polling a job every 20 to
30 seconds never reaches it.

## Support

Open an issue at https://github.com/zeropage-onryo/zeropage-studio-plugin/issues.

## Validated

`claude plugin validate ./zeropage-studio-plugin` on 2026-10-07 (Claude Code 2.1.285):

```
Validating plugin manifest: ./zeropage-studio-plugin/.claude-plugin/plugin.json

✔ Validation passed
```
