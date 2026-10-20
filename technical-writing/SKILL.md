---
name: technical-writing
description: Write and review documentation prose in a plain, reader-facing voice, and check docs for tone and correctness. Use when authoring or editing READMEs, guides, specs, taglines, or package descriptions in any project.
allowed-tools: Read, Edit, Write, Grep, Glob, Bash, AskUserQuestion
---

# Technical Writing

House style for project documentation. Apply when writing or reviewing prose in
README files, getting-started guides, reference docs, specs, and package descriptions.

## Core directions

### 1. Lead plain; no jargon stacks

Open with a short, plain sentence that names the value, like `X is a <adjective> <noun>
that does Y`. Do not stack architectural jargon into the opener. Push that detail
into later sections.

- Bad: "Acme is an immutable document model backed by a piece table and a line index,
  driven by pure, deterministic reducers, read through complexity-stratified namespaces…"
- Good: "Acme is a fast, immutable text engine for building editors. It's built on a
  piece table and works with any UI framework."

### 2. Prefer the plain word

If a plain word carries the meaning, use it instead of the term of art.

- "stays framework-agnostic" / "binds to any UI layer" → "works with any UI framework"

When two clauses say the same thing, merge them into one.

### 3. Restructure sentences with em-dashes, semicolons, or colons

Treat an em-dash (—), semicolon (;), or colon (:) in prose as a cue to rethink
the whole sentence. Identify its main point and write it again around that point.
Do not preserve the original clause structure by swapping punctuation, inserting
"which" or "that", or splitting at the same mark. Keep supporting information
only when the reader needs it, and give it a clear place in the rewritten prose.

- Bad: "This spec records what the codebase implements today — the precise surface,
  not the roadmap."
- Bad: "This spec records what the codebase implements today; it omits the roadmap."
- Bad: "This spec records one thing: what the codebase implements today."
- Good: "Use this spec to look up currently implemented features."

Conventional separators in glossaries, list items, tables, and titles are exceptions.
Keep forms such as `term — definition` and `term: definition`, along with punctuation
inside code and literal values. Find candidates with `rg -n '—|;|:' <file>`, then
rewrite prose sentences and leave conventional or literal uses intact.

### 4. No emphasis markup

Do not use bold (`**...**`) or italics to emphasize words, and do not use superscript,
subscript, underline, or similar emphasis expressions (`<sup>`, `<sub>`, `<u>`). Carry
emphasis through word choice and sentence structure instead. Use inline code (`` ` ``)
only for real code, identifiers, and literal terms, never to stress an ordinary word.
Headings and lists provide all the structural emphasis documentation needs.

### 5. Short sentences, reader-facing voice

One idea per sentence. Address the reader ("you", "your app") where it helps. No emoji
or badges. Teach code-first by introducing each example with a one-line lead-in, then
showing the code.

### 6. Prefer the imperative over "You ..."

For instructions, give the action directly instead of opening with "You can", "You
need to", "You should", or "You must". The imperative says the same thing in fewer
words and reads as guidance rather than narration. Addressing the reader as "you" is
still fine when it carries meaning ("your app", "if you already have X"). The rule is
about the "You + verb" sentence opener, not the word "you".

- Bad: "You can run `npm install` to add the dependency."
- Good: "Run `npm install` to add the dependency."
- Bad: "You need to set the `API_KEY` variable before starting."
- Good: "Set the `API_KEY` variable before starting."

## Genre awareness

Match register to the document's job. Do not flatten everything to one voice.

- Onboarding prose (README, getting-started guides, doc intros): plain, conversational-
  technical, reader-facing. This is where directions 1, 2, and 5 apply most.
- Reference material (API references, specs, status docs): terse, status-first,
  scannable, with bullet fragments, `term — definition` lists, and inline code for
  terms. Keep this register, and do not conversationalize it. The em-dash/semicolon/colon
  rule (3) and the no-emphasis rule (4) still apply here. Fix these marks in prose but
  keep definition-list separators, and do not reach for bold to mark up terms.

## Organize around the reader's task

Lead with the main workflow. Introduce optional structures and advanced features
later, and say when the defaults are enough. Prefer a short hint such as
"Use other structures only when you need them" over explaining every default.
Do not imply that optional features are required setup.

When a product offers both UI and CLI workflows, separate their instructions.
For this house style, put UI before CLI unless the user or document's purpose
calls for another order. Shared installation and startup can precede both.
Keep browser gestures in the UI guide, command syntax in the CLI reference, and
HTTP contracts in the API reference. Link to the relevant guide rather than
repeating its instructions.

## Refine without losing the contract

When asked to shorten documentation, cut repeated explanations, design rationale,
implementation narration, obvious behavior, and sample output that adds no useful
information. Do not chase a word-count reduction or remove a command just to
make the document shorter.

- Guides should foreground actions, controls, and outcomes. Use compact tables
  for shortcuts or comparable settings.
- CLI and API references must retain commands or endpoints, required inputs,
  options, defaults, response shapes, and meaningful errors. State shared rules
  once, then document exceptions beside the affected operation.
- Operations and security docs must preserve authentication requirements, access
  boundaries, destructive effects, export exposure, data limits, and recovery
  steps. Use tables for modes and limits where comparison helps.

Keep the canonical explanation in one document and link to it from others.
Resolve contradictions against the implementation, especially differences between
live and static modes or default and opt-in behavior. Preserve useful heading
anchors and update links when moving material.

After restructuring, review the diff for lost requirements. Check local links
and anchors, code fences, and whitespace. Run existing documentation coverage
checks when they compare command or endpoint headings against source. Those
checks establish coverage, not factual correctness. Report any validation that
could not run. Avoid unrelated test suites for prose-only changes.

## Correctness is part of the writing

Prose that misdescribes the code is a bug. When writing or reviewing docs:

- Verify every API or feature claim against the source before stating it (for example,
  confirm an export actually exists in the code before documenting it).
- Keep numbers in sync with their declared source of truth (for example, test counts
  cited in a status doc must match the test report they reference).
- Remove claims for anything not implemented or not exposed.

## Code comments complement code, not 1:1 explanations

- Verify that the comment describes the purpose of the implementation so a reader can understand it without reading the code.
- Verify that it is not a 1:1 code explanation. If it is, remove it.
- Ensure it provides valuable insights that are not immediately obvious from the code alone.

## Review checklist

1. Opener is a short, plain value statement with no jargon stack.
2. No term of art where a plain word works, and no redundant clauses.
3. No em-dashes, semicolons, or colons in prose sentences (list/table/title separators are fine).
4. No bold, italics, or other emphasis markup (superscript, underline, etc.).
5. Sentences are short, one idea each, and reader-facing where useful.
6. Instructions use the imperative, not "You can/need to/should" openers.
7. Register fits the genre (onboarding prose vs. terse reference material).
8. Every factual or API claim checked against source.
9. No emoji or badges.
10. Main workflow comes first, optional features are clearly optional, and UI and CLI instructions are separate.
11. Refinement preserves reference contracts, operational requirements, and working links.
