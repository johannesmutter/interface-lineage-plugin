---
name: interface-lineage-link-types
description: The Interface Lineage typed-edge vocabulary and how to read edge direction. Use when interpreting the output of the get_lineage MCP tool, or whenever you need to reason about relationships between designs in the corpus (came_after, inspired_by, contrasts_with, extends, embodies, …).
---

# Interface Lineage edge vocabulary

`get_lineage` returns typed edges. **Direction is read from the SOURCE
document's perspective.** "A `came_after` B" means A is the later design. The
tool tells you each edge's `direction` (`out` = this doc → other, `in` = other →
this doc); combine that with the type to read it correctly.

## The types

**Time**
- `came_after` — the source is the later design (its target is the earlier one).
- `came_before` — the source is the earlier design.

**Influence** (asymmetric pair — pick by which side you're standing on)
- `inspired_by` — the source drew on the target.
- `influenced` — the source shaped the target.
- `originated` — the source is where an idea first appeared.

**Kinship & contrast**
- `similar_to` — hand-authored "these rhyme" (note: this counts as a *linked*
  relationship, so `find_related` deliberately excludes it — it surfaces the
  *unlinked* cousins instead).
- `contrasts_with` — solves the same problem the opposite way.

**Structure**
- `extends` / `refines` — builds on and sharpens the target.
- `replaces` — supersedes the target.
- `embodies` — the source (an interface) instantiates the target (a principle).
- `violates` / `complicates` — works against or muddies the target.
- `serves` — advances the target's goal.
- `groups` / `collects` — the source gathers the target as a member.
- `instance_of` / `completed_by` — typing and completion relations.

**Authorship**
- `created_by` — the source was made by the target (a `person`).

## Reading tips

- A pair like `came_after` + `inspired_by` on the same two docs is common and
  consistent: the later design both post-dates and drew on the earlier one.
- Don't invert direction silently. If you're describing the *target* of a
  `came_after` edge, it's the *earlier* design — say so.
- Untyped edges exist in older data; ignore blank types.
