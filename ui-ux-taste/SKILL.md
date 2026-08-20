---
name: ui-ux-taste
description: Discover a user's visual taste for an app or website by showing them real reference moodboards to react to, then translate that taste into one opinionated frontend tech stack recommendation and an ASCII wireframe of the key screen(s). Use this whenever someone is starting a new app/site and doesn't know what it should look like or which frontend stack fits — phrases like "I don't know what style I want", "what should my app's UI look like", "help me pick a design direction", "what stack should I use for the frontend", "show me some UI directions to choose from", or a vague "make me an app" with no visual brief yet. This is a taste-discovery + stack-recommendation front end; it hands off to the universal-ui-ux skill for the full build (tokens, responsive layout, icons, anti-slop critique). Do not use this when the user already has a locked design system or explicit style brief — go straight to universal-ui-ux instead.
---

# UI/UX Taste

Most people cannot describe the UI they want in words. They can react to it instantly on sight.
This skill exploits that: show real reference screens across a spread of distinct directions,
let the user point at what they like, and turn that reaction into a concrete plan — a frontend
stack and a wireframe — instead of a vague adjective like "modern" or "clean".

This skill answers two questions: **what should it look like**, and **what should it be built
with**. It does not build the thing. Once taste and stack are locked, hand off to the
`universal-ui-ux` skill (or just start building) for tokens, responsive implementation, icons,
and the anti-slop pass — don't duplicate that work here.

## The flow

```
1. SCOPE      → what's the app, who's it for, web or mobile
2. MOODBOARDS → show 4-6 real reference directions, let them react
3. STACK      → one opinionated frontend stack, derived from the chosen direction
4. WIREFRAME  → ASCII wireframe of the key screen, in that direction's spirit
```

Compress stage 1 if the user already gave enough context. Never compress stage 2 — the reactions
are the entire point of this skill; skipping straight to a stack recommendation from a text
description is exactly the failure mode this skill exists to avoid.

## Stage 1 — Scope, quickly

Get three things, in one batch, only if not already known:

1. **What the app/site does** — one sentence, their words.
2. **Web, mobile, or both** — changes which reference images and stack options are relevant.
3. **Any hard constraints** — existing brand colors, a required framework, a deadline. Don't
   fish for these; only ask if there's reason to think they exist.

If the user is impatient, state your assumption in one line and move straight to Stage 2. A
wrong assumption here costs one correction later; blocking on questions costs the whole flow.

## Stage 2 — Moodboards (the core of this skill)

Pick 4–6 **visually distinct** directions relevant to the app type — not near-duplicates. Pulling
from the same handful of buckets every time defeats the purpose; let the app's domain steer which
directions you pick. `references/style-directions.md` has a working list of directions with tuned
image-search queries and a one-line description of each, organized by product type (SaaS/dashboard,
consumer/social, ecommerce, portfolio/creative, dev tool). Read it before picking.

For each direction, use `image_search` with the tuned query (3–4 images) so the user sees real
shipped design work, not a description of a style. Write one line of prose introducing each
direction before its images — what it commits to, what kind of product it suits — then let the
images speak. Interleave: text → images → text → images, never all images with no framing.

After all directions are shown, ask the user to react — which one(s) pull them, what they'd mix,
what they'd drop. Use `ask_user_input_v0` for this if the choice is a clean single pick; if you
expect them to want to mix elements from two directions, just ask in prose instead, since that
answer won't fit clean buttons.

Do not skip to a stack recommendation on a hunch. If the reaction is mixed or noncommittal, show
1–2 more directions closer to what they leaned toward rather than guessing.

## Stage 3 — Stack, one opinionated answer

Once a direction is chosen, recommend **one** frontend stack, not a menu. A menu of five viable
frameworks makes the user do the work this skill exists to save them from. State the alternative
in a single sentence if it's close, then commit.

The stack has five parts — cover all five:

1. **Framework** — Next.js, plain React+Vite, SvelteKit, whatever fits the app's actual needs
   (SEO/SSR need, interactivity level, team familiarity if known).
2. **Styling approach** — Tailwind, CSS Modules, vanilla-extract, styled-components. Tailwind is
   the safe default for speed; only deviate with a reason (e.g. a highly custom art-directed site
   where utility classes fight the design rather than help it).
3. **Component baseline** — shadcn/ui, Radix primitives, Headless UI, Material UI, or none/custom.
   This should match the chosen direction: a brutalist/industrial direction wants unstyled
   primitives (Radix) it can skin from scratch; a clean SaaS direction wants shadcn/ui's baseline.
4. **Motion** — Framer Motion, GSAP, CSS-only, or none. Only recommend a library if the direction
   actually calls for choreographed motion; a lot of good UI needs none.
5. **Icons and type** — default to Hugeicons per `universal-ui-ux` unless the direction specifically
   wants something else (e.g. a hand-drawn/illustrative direction). Suggest one display face + one
   body face pairing that matches the direction's spirit, not a generic "Inter everywhere" default.

`references/stack-picks.md` has worked stack recommendations per direction from
`style-directions.md` as a starting point — adapt, don't copy blindly, since app type and
constraints from Stage 1 still matter.

**If this is a portfolio project** (the user is building it to show employers/clients rather than
for its own sake), check the stack against whatever else they've already got in their portfolio.
Reusing Next.js/FastAPI/Supabase-style choices across projects reads as a coherent engineer with a
real stack; a different framework in every project reads as untested breadth instead of depth.
Only break consistency when the chosen direction genuinely can't be served by the existing stack
(e.g. a native-mobile direction when the rest of the portfolio is all web) — and say so explicitly
when you do, since that's the one case worth calling out rather than silently matching.

## Stage 4 — Wireframe

Draw the key screen (the one the user will spend the most time on) as an ASCII wireframe in the
chosen direction's spirit — information density, whitespace, and hierarchy should already look
different between a brutalist direction and a soft/minimal one, even in ASCII.

Use the wireframe notation from `universal-ui-ux`'s `references/ascii-wireframing.md` — read it
before drawing if you haven't already in this conversation. Draw at minimum a mobile (390) and
desktop (1440) frame if the app targets both; one frame is enough if the user said mobile-only or
desktop-only in Stage 1.

Annotate each block with its role and size behavior, not just its position. Then stop and ask for
approval or changes before suggesting any further build work.

## Handoff

Once the wireframe is approved, say plainly that the next step — tokens, responsive build,
component code, icon wiring, anti-slop critique — is `universal-ui-ux`'s job, and offer to
continue there. Don't silently start building; taste and stack were the deliverable here.

## Working style

- Show, don't describe. If you catch yourself writing "a clean modern aesthetic with subtle
  shadows" instead of calling `image_search`, stop and search instead.
- One opinionated stack beats three neutral options, same principle as `universal-ui-ux`.
- If the user pushes back on the direction or stack, follow their lead — this skill is discovery,
  not persuasion.

## Reference files

| File | Read when |
|---|---|
| `references/style-directions.md` | Stage 2 — direction list, tuned image-search queries, organized by product type |
| `references/stack-picks.md` | Stage 3 — worked stack recommendations per direction, as a starting point |
