# Zero Page Studio

Run your [Zero Page Studio](https://zeropage.studio) idea board from a
conversation with Claude: turn a brief into a few story ideas you approve
before anything is written or rendered, set the look from reference images you
attach, start and follow renders with the price shown and your approval
first, and keep each piece of work in a project you can come back to.

Zero Page Studio is an AI pre-production studio for creators and filmmakers.
You give it an idea and reference images; it writes one paste-ready scene
prompt, draws the keyframes, and renders the clip, one shot at a time, with a
price in front of every spend.

## What the plugin contains

- **A connector**: the studio's remote MCP server at
  `https://zeropage-studio.fly.dev/mcp`. You sign in with your Zero Page Studio
  account; the tools read and write your own board and projects and nobody
  else's.
- **Five skills** that teach Claude the studio workflow:
  - `concept-board` — a brief becomes two to four ideas you choose between, then
    cards on your board. Reads and decisions only.
  - `write-scene` — Claude writes the scene prompt in the studio's shape (an
    opening line naming your photos, a style block, timed shots, diegetic
    sound, an avoid list) and saves it against the photos you uploaded.
  - `look-matching` — the visual look, from your own element photos and from a
    frame you describe. The studio renders against photographs you uploaded,
    never a name and never an image off the web.
  - `render-and-status` — quoting the keyframes and the clip, approving on your
    yes, following the job.
  - `credits-and-limits` — what is free, what costs credits, what a refusal or
    a 429 means.

The connector offers these tools: `board`, `idea`, `search`, `capture`, `pick`,
`shoot`, `archive`, `stats`, `projects`, `project`, `project_chat`,
`create_project`, `save_chat`, `elements`, `write_scene`, `quote`, `approve`,
`job`. Only `approve` spends, and only after `quote` has shown the price.

**Projects** are the same ones on your projects board in the studio. `projects`
lists them; `project` reopens one, whether you made it here or in the studio,
with its brief, its look, its scenes, the reference images those scenes used,
its renders and the latest turns of its chat; `project_chat` pages back
through that chat. `create_project` starts a new one, and `save_chat` keeps
this conversation with it, so the next time the project is opened, here or in
the studio, the conversation is there.

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
3. "Write the scene." → Claude reads your elements (the bottle you
   photographed, the gym floor), writes the scene as timed shots in the chat,
   takes your edits, and saves it onto the card with your photos attached.
4. "What would it cost?" → Claude picks the card and quotes it: the keyframes,
   the clip per shot, your balance.
5. "Draw the keyframes." → Claude repeats the price and waits for your yes,
   then approves; it polls the job and shows the stills. The clip is the same
   again: a quote, your yes, the render.
6. "Keep this with my bottle-ad project." → Claude saves the conversation into
   the project. Next week, "open the bottle ad" brings back its brief, its
   scenes, the references they used and this chat.

## Data

The connector sends the text you type for an idea (title, hook, logline), the
scene prompts Claude writes with you, the ids of cards and of your own
element photos, a project's name, brief and look when you create one, and --
only when you ask Claude to keep a conversation with a project -- the text of
that conversation's turns, to your Zero Page Studio account at
`zeropage-studio.fly.dev`, over HTTPS, with the OAuth sign-in you approve. The
studio stores what you capture, pick, archive and write on your board, and
the projects and saved conversations, under your account; a saved
conversation is kept until you delete its project in the studio. Keyframes
and renders run on the studio's AI providers and are charged in credits from
your balance after a price is shown and you approve; see the studio's
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
