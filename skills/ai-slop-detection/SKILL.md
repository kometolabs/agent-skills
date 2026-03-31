---
name: ai-slop-detection
description: "Check the project for AI slop across language, code, UI, and configuration."
license: Apache-2.0
metadata:
  author: kometolabs
  source: https://github.com/kometolabs/agent-skills/tree/main/skills/ai-slop-detection
  version: "1.1.0"
---

Check the project for AI slop across language, code, UI, and configuration.

## Language slop (docs, strings, comments, README)

- Em dashes and ellipses: `—`, `…`
- Buzzwords: delve, leverage, utilize, robust, seamless, comprehensive, cutting-edge, revolutionize, game-changing, state-of-the-art, innovative, streamline, empower, unlock, harness, tapestry, landscape, realm, pivotal, nuanced, multifaceted
- Filler phrases: "it's worth noting", "it's important to note", "certainly", "absolutely", "of course", "needless to say", "as mentioned above", "in today's world", "in conclusion", "let's dive in", "without further ado", "navigate to", "navigate the complexities", "It should be noted", "One might argue", "In order to" (instead of just "to")
- Exclamation marks or emojis in technical docs ("This is a powerful feature!")
- Excessive use of emojis in READMEs
- Any mentions of Lovable, Bolt.new, Base44, v0 or other vibe-coding platforms

## Code slop

- Comments explaining obvious operations (`// increment i by 1`)
- TODO/FIXME/HACK/NOTE comments left in
- Overly generic names: `data`, `result`, `item`, `value`, `helper`, `utils`, `manager`, `handler`, `service` (when more specific names are possible)
- Single-use interfaces or wrapper classes that add no logic
- Unnecessary abstraction layers or indirection
- Unused imports or variables
- Empty catch blocks
- Copy-pasted error messages ("Something went wrong")
- Overly defensive null checks where types guarantee non-null
- Mixed camelCase and snake_case named files in the same codebase (especially in a freshly scaffolded project)
- AI-generated `robots.txt` that contradicts itself - allows all bots while also listing specific allow rules
- Any resources that belong to vibe-coding platforms, for example `https://bolt.new/static/og_default.png` or `https://lovable.dev/opengraph-image-p98pqg.png`
- `ignoreBuildErrors: true` or `unoptimized: true` in Next.js config
- The `generator` meta-tag that points to a vibe-coding platform, e.g. `<meta name="generator" content="v0.dev">`
- `any` type used liberally in TypeScript
- Dependencies installed but never imported anywhere in the codebase
- Any vibe-coding platform-specific dependencies, for example `lovable-tagger`, `@base44/vite-plugin` or `@base44/sdk`

## Test slop

- Excessive use of mocks, stubs, or fakes
- Test suites that don't test anything
- Tests that test the mock, not the code
- `expect(true).toBe(true)` or similarly vacuous assertions

## UI/style slop

- Purple and indigo as primary palette (Tailwind: `purple-*`, `indigo-*`, `violet-*`)
- Gradient hero sections with vague taglines ("Build faster. Ship smarter.")
- Animated gradient text on headings
- Everything is a rounded card with drop shadow
- Generic section names: "Features", "Testimonials", "Pricing", "How It Works", "Get Started Today"
- Decorative blobs or mesh gradients in backgrounds
- Rounded-full avatars with gradient borders
- "Trusted by 10,000+ teams" social proof with fake logos
- Excessive use of `backdrop-blur`

## Output format

- Findings grouped by category with file:line references
- A brief conclusion: likely AI-generated / mixed / likely human

## IMPORTANT

- Flag patterns, don't nitpick style. A single "utilize" is not a finding; a pattern is.
- Do not trust pre-existing reports.
