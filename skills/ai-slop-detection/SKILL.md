---
name: ai-slop-detection
description: "Check the project for AI-generated slop: buzzwords, code smells, and generic UI patterns."
license: Apache-2.0
metadata:
  author: kometolabs
  source: https://github.com/kometolabs/agent-skills/tree/main/skills/ai-slop-detection
  version: "1.0.0"
---

Check the project for AI slop across language, code, and UI.

## Language slop (docs, strings, comments, README)

**Em dashes and ellipses:** `—` `…`

**Buzzwords:** delve, leverage, utilize, robust, seamless, comprehensive, cutting-edge, revolutionize, game-changing, state-of-the-art, innovative, streamline, empower, unlock, harness

**Filler phrases:** "it's worth noting", "it's important to note", "certainly", "absolutely", "of course", "needless to say", "as mentioned above", "in today's world", "in conclusion"

**AI tells:** "As an AI...", "I'd be happy to...", "Great question!", "I hope this helps"

## Code slop

- Comments explaining obvious operations (`// increment i by 1`)
- TODO/FIXME/HACK/NOTE comments left in
- Overly generic names: `data`, `result`, `item`, `value`, `helper`, `utils`, `manager`, `handler`, `service` (when more specific names are possible)
- Single-use interfaces or wrapper classes that add no logic
- Unnecessary abstraction layers or indirection

## UI/style slop

- Purple and indigo as primary palette (Tailwind: `purple-*`, `indigo-*`, `violet-*`)
- Gradient hero sections with vague taglines ("Build faster. Ship smarter.")
- Everything is a rounded card with drop shadow
- Generic section names: "Features", "Testimonials", "Pricing", "How It Works", "Get Started Today"
- Decorative blobs or mesh gradients in backgrounds

## Output format

- Findings grouped by category with file:line references
- A brief conclusion: likely AI-generated / mixed / likely human

## IMPORTANT

- Flag patterns, don't nitpick style. A single "utilize" is not a finding; a pattern is.
