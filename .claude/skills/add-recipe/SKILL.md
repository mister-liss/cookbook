---
name: add-recipe
description: Add a recipe to the cookbook from pasted text, a URL, a photo, or a rough verbal description. Use when the user wants to save, capture, add, or file a new recipe, or dumps recipe text with no instructions. Do NOT use for edits to a recipe that already exists.
---

# Add a recipe

Goal: get the recipe into `recipes/<slug>.md` with correct frontmatter, committed and
pushed, in as few questions as possible.

## Steps

1. **Get the content.** Pasted text and photos are used as-is. For a URL, fetch it and
   pull out the recipe — ignore the blog preamble.

2. **Check for duplicates first.** Grep `recipes/` for the slug and for the main
   ingredient plus a distinguishing word from the title. If a plausible match exists,
   stop and ask whether this is a new recipe or an update to that one. Do not create a
   near-duplicate file on your own judgment.

3. **Write the file** at `recipes/<kebab-case-slug>.md` following `recipes/_TEMPLATE.md`.
   - Transcribe faithfully. Do not correct, streamline, or restate the method in your
     own words. Keep the original's units and phrasing.
   - Set `added` to today's date. Leave `last_made` and `rating` empty.
   - Set `source` to the URL, book, or person. If it came from the user's head, use
     `source: Steven`.
   - Tags: reuse tags already in `INDEX.md` where they fit before inventing new ones.
     Aim for 2–4.

4. **Fill gaps by asking, not guessing.** If servings or a cook time genuinely isn't
   stated, leave the field empty rather than estimating. Ask at most one batched
   question about anything actually unclear in the method.

5. **Reindex and commit.** Run `python3 bin/reindex.py`, then commit the recipe and
   `INDEX.md` together as `Add <title>`. Push.

6. **Report back short**: the title, the tags you assigned, and anything you left empty
   so the user can fill it in later.
