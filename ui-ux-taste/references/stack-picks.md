# Stack picks per direction

Starting points, not fixed answers — adapt to the app type and constraints from Stage 1. Each
entry follows the five parts from `SKILL.md` Stage 3: framework, styling, components, motion,
icons/type.

**Clean SaaS** — Next.js (App Router) · Tailwind · shadcn/ui as the baseline, extend sparingly ·
motion: Framer Motion, used only for state transitions, not decoration · Hugeicons, one weight ·
type: Inter or Geist for both display and body, size does the differentiating work, not the face.

**Dark tech / cyber** — Next.js or Vite+React if no SSR need · Tailwind with a dark-first token
set · Radix primitives skinned custom, shadcn's default look reads too "SaaS-clean" for this ·
motion: subtle glow/pulse via CSS, Framer Motion for panel transitions · Hugeicons stroke variant ·
type: a geometric sans for display (Space Grotesk, Sora) + a mono face (JetBrains Mono, Berkeley
Mono) for data/code.

**Industrial brutalist** — plain React+Vite, this direction rarely needs SSR · CSS Modules or
vanilla-extract over Tailwind, since the whole point is deliberate rawness Tailwind's defaults
fight against · Radix primitives, fully custom-skinned, no shadcn · motion: minimal, hard cuts not
eases, if any · custom or Hugeicons stroke-only, thin weight · type: a grotesque/mono pairing
(Suisse/Neue Haas + a mono), tight tracking.

**Soft neumorphic / glass** — Next.js · Tailwind with custom shadow/blur utilities layered in ·
shadcn/ui works but needs the shadow tokens swapped for the soft-shadow set · motion: Framer
Motion, gentle spring easing throughout · Hugeicons duotone or rounded variant · type: a rounded
sans (Nunito, Quicksand for display; a plainer face for body so it stays legible).

**Playful maximalist** — Next.js or Remix · Tailwind · component baseline light-touch (Headless UI
for behavior, fully custom visuals) · motion: Framer Motion or GSAP if there's a hero sequence ·
custom illustrated icon set over Hugeicons if budget allows, otherwise Hugeicons bold/solid variant
· type: a characterful display face (Clash Display, Cabinet Grotesk) + a plain, legible body face —
don't let two loud faces fight.

**Editorial minimal** — Next.js (SSG-heavy, content-driven) · Tailwind, sparse custom utility set ·
minimal component library, mostly custom typographic components · motion: none, or a single fade-in
on scroll · Hugeicons thin stroke, used sparingly · type: a serif or high-contrast display face
(Fraunces, Canela) + a quiet body sans.

**Retro / nostalgic** — Next.js or Astro if content-heavy · Tailwind with a custom warm palette ·
fully custom components, off-the-shelf libraries read too clean for this direction · motion: CSS
only, deliberately a little imperfect · custom icon set matching the period, Hugeicons as fallback
· type: a period-accurate display face (VT323, Space Mono for 80s/90s-computer; a slab serif for
70s warmth) + a plain body face for actual readability.

**Native-feeling mobile** — React Native or Flutter if truly native-target; Next.js + PWA patterns
if web-based but must feel native · platform's own styling conventions over a CSS framework ·
platform component kits (iOS: SwiftUI-adjacent patterns; Android: Material 3) over shadcn · motion:
platform-standard transitions, nothing custom · platform-native icon sets (SF Symbols / Material
Symbols) over Hugeicons here specifically · type: platform system fonts (SF Pro / Roboto).

**Luxury minimal** — Next.js · Tailwind, very sparse utility use, most impact from spacing and type
scale, not components · little to no component library, mostly bespoke layout · motion: slow,
deliberate, Framer Motion with long durations · Hugeicons thin stroke, used rarely, or none · type:
a high-end serif or display sans (Canela, Söhne) at large sizes, huge whitespace budget.

**High-energy DTC** — Next.js · Tailwind · shadcn/ui for utility screens (checkout, account),
fully custom for marketing sections · motion: GSAP for scroll-triggered sequences, Framer Motion for
UI-level micro-interactions · Hugeicons solid/bold · type: a bold condensed or variable display face
+ a plain, fast-reading body face — conversion copy needs to scan quickly.

**Warm craft / artisan** — Astro or Next.js SSG · Tailwind with an earth-tone custom palette ·
mostly custom, light Headless UI for behavior · motion: minimal, texture and photography carry the
feel instead · Hugeicons duotone or a hand-drawn custom set if budget allows · type: a warm serif or
humanist sans for display + a plain body face.

**Experimental / art-directed** — Vite+React or Next.js depending on route complexity · CSS-in-JS
or vanilla-extract for per-project bespoke styling, Tailwind usually fights this direction · no
shared component library, this direction is deliberately one-off · motion: GSAP or Three.js if
there's a signature interactive/3D element, this is the direction where a real motion investment
pays off · custom icons or none · type: whatever the concept calls for, chosen last after the
visual concept is set, not first.

**Terminal / CLI-inspired** — plain React+Vite · Tailwind with a mono-first token set · fully
custom, minimal chrome · motion: typewriter/blink effects via CSS, nothing else · Hugeicons stroke,
sparse · type: a mono face for nearly everything (JetBrains Mono, IBM Plex Mono), maybe one sans for
long-form body text if there's prose content.

**Docs-clean** — Next.js with a docs framework (Nextra, Fumadocs) over hand-rolling this · Tailwind
· the docs framework's own component set, don't fight it with shadcn on top · motion: none · Hugeicons
thin stroke for nav/section icons only · type: system sans or Inter for body, a mono face for code
blocks — legibility and search speed matter more than personality here.
