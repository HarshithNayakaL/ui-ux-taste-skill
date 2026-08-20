# ui-ux-taste

**A skill that figures out what your app should look like — by showing you, not asking you.**

Most people can't describe the UI they want. Ask someone "what style are you going for?" and
you'll get *modern*, *clean*, *minimal but not boring* — adjectives that mean nothing and lead
to a generic build. But show them six real interfaces and they'll point at one in two seconds.

`ui-ux-taste` exploits that gap. It shows you real shipped design work across distinct
directions, reads your reaction, and turns it into two concrete deliverables: **one opinionated
frontend stack** and an **ASCII wireframe** of your key screen.

It doesn't build the thing. It decides what the thing should be.

---

## The flow

```
1. SCOPE      → what's the app, who's it for, web or mobile
2. MOODBOARDS → 4–6 real reference directions, you react
3. STACK      → one opinionated frontend stack, derived from what you picked
4. WIREFRAME  → ASCII wireframe of the key screen, in that direction's spirit
```

Stage 2 is the whole point and never gets skipped. Recommending a stack from a text description
is exactly the failure mode this skill exists to prevent.

---

## What you get

**A stack, not a menu.** Five parts, all covered: framework, styling approach, component
baseline, motion, and icons/type. A menu of five viable frameworks makes you do the work the
skill was supposed to save you.

**A stack that matches the look.** A brutalist direction gets unstyled Radix primitives to skin
from scratch and CSS Modules over Tailwind — because Tailwind's defaults fight deliberate
rawness. A clean SaaS direction gets shadcn/ui and Framer Motion for state transitions only.
The visual direction drives the technical choice, not the other way around.

**Portfolio-aware picks.** If you're building to show employers, the skill checks the stack
against what's already in your portfolio. Next.js across four projects reads as a coherent
engineer with a real stack; a different framework in every project reads as untested breadth.
It only breaks consistency when the direction genuinely demands it — and says so when it does.

**A wireframe before code.** Mobile (390) and desktop (1440) frames, each block annotated with
its role and resize behavior. Approve it before anyone writes a component.

---

## Installation

**Claude Code / Claude Desktop**

```bash
git clone https://github.com/harshithnayakal/ui-ux-taste-skill.git
cp -r ui-ux-taste-skill/ui-ux-taste ~/.claude/skills/
```

Or scope it to a single project by copying into `.claude/skills/` in that repo instead.

**Other agents (Codex, OpenCode, Cursor, Cline, and friends)**

This is written as a Claude skill, but it's plain Markdown with no Claude-specific runtime —
`SKILL.md` is the instruction set and the two files in `references/` are lookup tables it reads
on demand. Any agent that can follow a Markdown playbook can run it:

- **Codex** — drop `SKILL.md` into `AGENTS.md`, or reference it from there by path.
- **OpenCode** — add it as a custom instruction file or a command in your config.
- **Cursor / Cline / Windsurf** — paste `SKILL.md` into a rule file
  (`.cursorrules`, `.clinerules`) or attach it as project context.
- **Anything else** — feed `SKILL.md` as a system prompt and keep `references/` reachable.

Two tool names in the file assume a Claude-ish environment: `image_search` (Stage 2) and
`ask_user_input_v0` (Stage 2's reaction prompt). Swap them for your agent's equivalents —
any web-image search and any user-prompt mechanism work. If your agent has no image search at
all, the skill loses most of its value, since showing real work *is* the method.

---

## Triggering it

The skill fires on the moment before a project has a look:

> "I don't know what style I want."
> "What should my app's UI look like?"
> "Help me pick a design direction."
> "What stack should I use for the frontend?"
> "Show me some UI directions to choose from."

Or just a vague "make me an app" with no visual brief attached.

**When not to use it:** you already have a locked design system or an explicit style brief.
There's no taste to discover — go straight to building.

---

## What's inside

| File | Purpose |
|---|---|
| `SKILL.md` | The four-stage flow and the rules for each stage |
| `references/style-directions.md` | Direction catalog with tuned image-search queries, organized by product type — SaaS/dashboard, consumer/social, ecommerce, portfolio/creative, dev tool |
| `references/stack-picks.md` | Worked stack recommendations per direction, as adaptable starting points |

The reference files are loaded on demand rather than inlined, so the skill stays cheap to keep
in context until it's actually running.

---

## Handoff

`ui-ux-taste` deliberately stops at the wireframe. Tokens, responsive implementation, component
code, icon wiring, and the anti-AI-slop critique pass are `universal-ui-ux`'s job — this skill
hands off rather than duplicating that work.

Taste and stack are the deliverable. The build is a separate conversation.

---

## Author

**Harshith Nayaka L** — [harshith-nayaka-l-portfolio.vercel.app](https://harshith-nayaka-l-portfolio.vercel.app/)

## License

MIT — see [LICENSE](LICENSE).
