---
name: explore-lineage
description: Explore a design through the Interface Lineage corpus — pull its acknowledged lineage AND its unlinked cousins, then synthesize the tension and pose generative design questions. Use when the user is designing something and wants grounded precedent, asks "what came before / what's related to X", "how have others solved this", or wants to think through a design move against real examples instead of averaged-out training data. Requires the Interface Lineage MCP (search / fetch / get_lineage / find_related).
---

# Explore a design's lineage

The point of this skill is the move the user found more productive than asking a
model cold: take one design, gather both its **acknowledged influences** and its
**unlinked cousins**, then *synthesize* — surface the underlying tension and turn
the contrast into questions for the design in front of them. Ground every claim
in fetched corpus text; never fill a gap from memory.

## Steps

1. **Locate.** `search` for the design (or `list_catalog` to browse a type).
   `fetch` the best match and read it — this is the anchor.
2. **Acknowledged lineage.** `get_lineage` on the anchor. These are the
   hand-authored, typed edges: what it `came_after`, what `inspired` it, what it
   `contrasts_with`, what it `extends` or `embodies`. Read the edge types, not
   just the titles — a `contrasts_with` is a different signal than a `came_after`.
3. **Unlinked cousins.** `find_related` on the anchor. These are designs that
   feel similar but that *no edge connects* — the "you should also look at this"
   set. This is where the corpus beats a plain read: it surfaces precedent the
   author never explicitly linked.
4. **Read the best of each.** `fetch` the 2–4 most interesting results across
   both sets. Don't rank by score alone; pick the ones that resolve the same
   problem *differently*.

## Then synthesize — don't list

Write, grounded only in what you fetched:

- **The tension.** What underlying problem is the anchor design resolving? State
  it as a real trade-off (e.g. "discoverability vs. accidental activation"), not
  a summary.
- **Two resolutions.** How do the acknowledged ancestors resolve that tension,
  and how do the unlinked cousins resolve it differently? The gap between "what
  it descends from" and "what it merely resembles" is usually the insight.
- **Generative questions.** 3–5 pointed questions for someone designing in this
  space now. Each must be a real fork the corpus illuminates — "X chose an
  explicit gesture and Y chose an implicit one; which cost can your context
  absorb?" — not a generic prompt.

## Calibration

- A single relevant precedent read closely beats ten titles listed. Depth over
  breadth.
- If `find_related` and `get_lineage` return the *same* design, that's a strong
  signal — note it. If they diverge sharply, the divergence is the story.
- Attribute makers and link dossiers by their canonical URL (see the
  `cite-interface-lineage` skill). Interpret edge directions with the
  `interface-lineage-link-types` skill — direction is read from the source doc's
  perspective.
- If the MCP tools aren't available, say so plainly and stop — do not fabricate
  lineage from training data. That's the exact failure mode this corpus exists
  to prevent.
