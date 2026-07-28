---
name: shopping-list
description: Build a consolidated shopping list from one or more recipes in the cookbook, optionally scaled to different serving counts. Use when the user asks for a shopping list, grocery list, what to buy, or wants to plan meals for a week from the cookbook.
---

# Shopping list

## Steps

1. **Resolve the recipes.** Match what the user named against `INDEX.md`. If a name is
   ambiguous between two recipes, ask which one — do not pick.

2. **Read each recipe file** and take the ingredient lines verbatim.

3. **Scale** if the user asked for a different serving count: multiply against the
   recipe's `servings`. Keep fractions readable (1½ not 1.5). Do not scale a "pinch",
   "to taste", or "a glug" — carry those through unchanged.

4. **Consolidate.** Combine the same ingredient across recipes when the units match
   (2 onions + 1 onion = 3 onions). When units differ or the prep differs meaningfully
   (diced vs whole), keep them as separate lines rather than forcing a conversion.

5. **Group by store section**: Produce, Meat & Fish, Dairy, Pantry, Frozen, Other.

6. **Output to chat as a markdown checklist** — do not commit it. A shopping list is
   throwaway; the repo is for recipes.

   End with a short "Probably have already" section for staples (salt, pepper, oil,
   common spices) so they're visible but not cluttering the main list.
