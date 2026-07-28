# Cookbook — rules for Claude

This is Steven's personal cookbook. It is a **record**, not a draft. Most of what is
here is already correct and already tested. Your default posture is: change the one
thing that was asked for and touch nothing else.

## Layout

- `recipes/<slug>.md` — one recipe per file, kebab-case slug, no subfolders.
- `recipes/_TEMPLATE.md` — the shape every recipe follows. Not a recipe; never index it.
- `INDEX.md` — generated. Do not hand-edit; run `python3 bin/reindex.py`.
- `bin/reindex.py` — regenerates `INDEX.md` from frontmatter.

## Hard rules

1. **Read the file before editing it.** Never regenerate a recipe from memory, and never
   write a recipe file with `Write` if it already exists — use `Edit`.
2. **No unrequested rewrites.** Do not reformat, reorder steps, retitle, "clean up"
   wording, normalize units, or round quantities. If a step reads oddly, it is probably
   deliberate. Leave it.
3. **No unrequested substitutions or improvements.** Do not suggest swaps, healthier
   versions, or technique corrections unless asked.
4. **Preserve voice and units exactly.** If it says "a big glug of oil", it stays a big
   glug of oil. Do not convert cups to grams (or back) unless asked.
5. **`## Notes` is append-only.** Add dated bullets at the end. Never edit or delete an
   existing note — a note that contradicts an older one still gets appended, both stay.
6. **Never delete or rename a recipe file** unless asked for by name.
7. **Check for duplicates before adding.** Search `recipes/` for the slug and for likely
   near-matches (main ingredient, key words in the title). If something close exists,
   ask before creating a second file.
8. **One commit per change**, with a message naming the recipe. Run `bin/reindex.py` and
   include `INDEX.md` in the same commit whenever a recipe is added, renamed, or removed.

## Frontmatter

Required: `title`, `tags`, `servings`. Everything else optional, and an empty field is
fine — leave it empty rather than guessing.

```yaml
---
title: Skillet Lemon Chicken
tags: [chicken, weeknight, one-pan]
servings: 4
active_time: 20m
total_time: 40m
source: adapted from NYT Cooking
added: 2026-07-28
last_made:
rating:
---
```

`tags` are freeform and lowercase. Reuse an existing tag from `INDEX.md` before inventing
a new one.

## When something is ambiguous

Ask. A wrong guess written into a file is worse than a question, because the file is the
source of truth from then on.
