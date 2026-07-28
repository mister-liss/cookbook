# Cookbook

Recipes as plain markdown files, one per recipe, in `recipes/`. Browse [INDEX.md](INDEX.md).

The point of this repo: the files are the source of truth. Any Claude session — phone,
desktop, web — starts by reading them, so nothing depends on a model remembering
anything between conversations. Every change is a commit you can read or revert.

## Adding and editing

Open a Claude Code session on this repo and say what you want:

- *"add this"* + paste/photo/URL → files it as a new recipe (`add-recipe` skill)
- *"made the lemon chicken tonight, needed 10 more minutes"* → appends a dated note
- *"shopping list for lemon chicken and the chili, doubled"* → prints a list, commits nothing
- *"what can I make with what's in the fridge: X, Y, Z"* → searches the repo

Conventions and the rules Claude follows are in [CLAUDE.md](CLAUDE.md). If Claude keeps
getting something wrong, fix it there rather than repeating yourself each session — that
file is read at the start of every session.

## Cooking from it

Read recipes straight from GitHub in a browser or the GitHub mobile app. No AI session,
no waiting, works with wet hands and one bar of signal. Starting a Claude session just to
read a recipe you already have is the slow path.

## Maintenance

`INDEX.md` is generated. After any change to `recipes/`:

```sh
python3 bin/reindex.py
```
