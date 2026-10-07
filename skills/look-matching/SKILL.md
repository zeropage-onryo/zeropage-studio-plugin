---
name: look-matching
description: Set the visual look of a scene in Zero Page Studio from reference images, by id only, and explain what the studio can and cannot match. Use when someone says "make it look like this", attaches or describes a reference image or video frame, asks for a mood, light or texture, or wants to know which references sit behind an idea. NOT for writing the story (concept-board), NOT for rendering or prices (render-and-status), and NOT for finding or copying a real person's face.
---

# Look matching

Zero Page Studio grounds a scene on **photographs the person attached**, never
on a name. A character is a set of photos they uploaded; a product is a set of
photos they uploaded; a place is the same. A reference found on the web is a
mood, light and texture reference held beside those, always with the page it
came from. If no photo is attached, the scene is written from words alone and
the studio says so.

## The rule on people

Never search the web for a specific real person's face, and never bank a frame
because it shows one. If the person wants a face in the scene, it is theirs or
someone they have the right to use, and it goes in as photos they attach in the
studio (Elements). Say this plainly when asked for a celebrity, a public
figure or "someone who looks like X".

## Working with references

Everything here is by **id**. You never see, type or pass an image URL; the
tools refuse one.

- `images` with a direction's `finding_id` lists the reference images already
  banked behind it, each with the page it came from. Read this before
  proposing more: two or three good frames beat eight.
- `images_for` searches open image sources for frames. Describe the **light and
  the surfaces**, not the story: "cold fluorescent on wet tile, overhead" finds
  more than "a man regretting something". Name the world and the look together.
  It returns up to 6 candidates (max 12) as ids with what each shows and its
  credit.
- `reference` banks one candidate behind a direction by its `candidate_id`.
  Only ids from an `images_for` reply in this conversation; the tool refuses
  any other. Bank at most three per direction and tell the person which you
  chose and why, with the credit line.
- `sparks` / `tonight` list the banked directions and their ids when the
  person does not have one to hand.

## Reading an attached image or video frame

When the person shares an image or a frame from a video, describe it in the
terms the studio writes scenes in, and offer that description back for their
yes before searching: the light (source, direction, colour, hardness), the
surfaces and textures, the framing (how close, what height), the palette, the
grain or softness, what is moving. Then search `images_for` with that
description. Do not claim the studio will reproduce a specific film, brand
campaign or artist's work; it matches light and texture, not authorship.

## Generated references

`imagine_reference` renders ONE reference still for a direction from a hook
frame and **spends credits on the call**. Do not call it from this skill. If a
rendered reference is wanted, hand over to render-and-status, which shows the
price and waits for approval first.

## Reply shape

Report: which direction the references are banked behind (its id), the frames
kept (what each shows, source), and the one-line look description the scene
will be written against. Keep it short enough to read on a phone.
