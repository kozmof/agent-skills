---
name: kozane
description: Use the Kozane CLI for modeling thoughts.
---

# Kozane

Kozane provides data structures for organizing text and modeling thinking processes. The names of these structures do not imply fixed intentions; different use cases may use them in different ways.

## Structures

- Namespace: A top-level container. It holds partitions, which group text units called cards. Most operations take place within a namespace.
- Partition: A sub-container that each card belongs to. Every namespace has a default partition named "General."
- Card: A unit of text with a 2D position.
- Glue: A bundle of cards.
- Layer: A stacking level that cards can be arranged on.
- Scope: A link between cards and taskspaces. Taskspaces correspond to directories and files on the filesystem.
- Warp: A saved point to jump to. Warps are not related to cards.

## Entrypoint

Use the installed `kozane` command, or `pnpm exec kozane` for a project dependency. Check `kozane --help` and the relevant subcommand's `--help`.

## Instructions

1. Examine the current Kozane data.
2. If it is empty or unrelated to the task, design a new structure: decide which namespace, partitions, and layers the task needs, then create them.
3. Otherwise, decide how to model the current task with the existing structures.
4. Use Kozane to work through the task.

## Card positioning

A card's `x`/`y` (`card add --x/--y`, `card move --x/--y`) is a pixel position on a real canvas, not a small arbitrary integer.

- Before placing cards, read `<workspace>/.kozane/config.json` and note `ui.canvasWidth`, `ui.canvasHeight`, and `ui.defaultCardWidth` to know the whole scale. 
- `x`/`y` cannot go negative: passing a negative value silently clamps to `0` instead of erroring.
- Start from the canvas center (`canvasWidth/2, canvasHeight/2`) as the origin of the layout if the canvas is empty.
- Space cards at least one `defaultCardWidth` (plus margin) apart center-to-center, or they overlap. When laying out a cluster of related cards, use a local grid (rows/columns spaced `defaultCardWidth + ~50px`) rather than packing them along a tight arc.
- To make position mean a measuarable concept, encode actual relations in it: e.g. distance from a card for depth/confidence, and angle or grouping for topical adjacency (related partitions/cards placed near each other).
- After moving cards, verify with `card list --namespace <ns>` and check the reported positions are spread across a meaningful fraction of the canvas, with no two unrelated cards landing on the same point.
- Verify pairwise for rebalance, not just by eyeballing the coordinate spread: run `card nearest <cardId>` for a card (its second line is the closest *other* card, with distance) 
