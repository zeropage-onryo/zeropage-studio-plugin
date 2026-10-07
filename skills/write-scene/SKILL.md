---
name: write-scene
description: Write the scene prompt for an idea on the person's Zero Page Studio board, in the shape the studio renders from, and save it with the `write_scene` tool against the photos they uploaded. Use when someone asks to write the scene, the prompt, the shots or the script for an idea, or says "make the scene" after choosing one. NOT for choosing between ideas (concept-board), NOT for pricing or rendering (render-and-status), and NOT for finding references (look-matching).
---

# Write the scene

A scene in Zero Page Studio is ONE paste-ready prompt a video model reads top
to bottom. The studio renders it one timed shot at a time, against the
photographs the person uploaded as elements. You write the prompt in the chat
(no model credit is spent for that), then save it with `write_scene`.

## Before writing

1. `idea` with the card's id: read the title, hook and logline. The logline is
   the idea; the prompt must carry it.
2. `elements`: the person's characters, props and places with their photo
   refs. Decide which photos the scene needs. If the scene needs a face, a
   product or a room and no element has photos of it, stop and tell the person
   to upload them in the studio first (Elements). The studio does not render a
   scene with no attached photos, and never from a name.
3. Settle the length in seconds (4 to 30; 10 is the default) and whether the
   idea wants cuts or one continuous take. Default to cuts: two or more shots.
   One continuous shot only when the person asked for one.

## The shape (five parts, in this order)

Write every look in cinematography and colour-grade terms. Never name a film,
a director, a brand or a real person.

1. **Opening line.** "Ultra-realistic grounded [tone] video in 9:16," then say
   which attached photo is the EXACT face, the EXACT outfit, the EXACT product
   or the EXACT place ("the attached photo of Sam is his exact face and
   clothing"). Name the photos; do not re-describe what they show. With no
   photos for a character, describe the person plainly.
2. **Style.** The look in two or three sentences: palette, light (source,
   direction, colour, hardness), lens and framing height, depth of field,
   finish and grade. Realism comes from practical light, believable physics
   and bodies, and restraint. Do not reach for "raw handheld, matte, muted"
   by habit.
3. **Beats, as timed shots.** Each shot opens with its window, written like
   `(0-4s)`. Windows start at 0s, are contiguous, never overlap, and end at the
   total length. Each window is rendered as its own clip by a model that sees
   only that window, so **each window is ONE shot**: one camera setup, one
   clear action that fits its length, 2 to 10 seconds. Cuts and location
   changes happen between windows, never inside one; say them ("hard cut to",
   "reverse on"). Open on an arresting image, turn or reveal, and end abruptly.
   Reactions are serious and physically believable, never cartoon. Use as many
   shots as the idea needs, not a habitual three.
4. **Sound.** Begin "No background music." then only the diegetic sound: what
   you would hear in that scene, nothing else.
5. **Avoid.** "Avoid: plastic AI sheen, CGI-looking skin or fabric, cartoon
   reactions, dramatic slow motion, named films, brands or actors."

A worked skeleton (replace everything in it):

```
Ultra-realistic grounded deadpan comedy in 9:16. The attached photo of Sam is
his exact face and clothing. Style: soft daylight from one window, true-to-life
colour with gentle contrast, a 35mm frame at chest height, shallow depth when
close, practical light only, a real lived-in kitchen.
(0-4s) Sam lifts the lid of a dented biscuit tin and freezes, both hands still
on it.
(4-10s) Hard cut to the hallway: Sam backs away from the open front door, the
tin held against his chest, and the door swings wider on its own. End abruptly.
No background music. Only diegetic sound: the tin lid's scrape, a floorboard,
the door's hinge.
Avoid: plastic AI sheen, CGI-looking skin or fabric, cartoon reactions,
dramatic slow motion, named films, brands or actors.
```

## Save it

Show the prompt to the person first and take their edits. Then call
`write_scene` with the idea's id, the prompt, `seconds`, and `refs`: the photo
refs from `elements`, exactly as listed, **the most important one first** (the
first ref is what the render anchors on: the face before the room). Pass at
least one ref; the tool refuses a scene with none, and refuses any ref
`elements` did not list.

The reply says how many shots were written and the seconds. It replaces any
scene the idea carried before. Nothing is spent.

## Then

Hand over to render-and-status: `pick` the idea, `quote` it, show the price,
and only on the person's yes `approve`.

## Do not

- Never invent a photo ref, and never pass a URL.
- Never leave a `{placeholder}` in the prompt; the tool refuses it.
- Never write a window longer than 10 seconds or shorter than 2.
- Never describe the look by naming a film, a brand or a person.
