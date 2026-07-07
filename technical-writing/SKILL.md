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

### 3. Avoid em-dashes, semicolons, and colons in prose

In a sentence, an em-dash (—), a semicolon (;), and a colon (:) are all the same
signal to reconstruct. The clause each introduces is usually additional or decorative
rather than essential. Treat the three the same way. Fold the content into the sentence
(commas, an "is"/"that" clause, or a second sentence), or cut it. Swapping one of these
marks for another does not solve the problem, so restructure the sentence instead.

- Bad: "This spec records what the codebase implements today — the precise surface,
  not the roadmap."
- Bad: "This spec records what the codebase implements today; it omits the roadmap."
- Bad: "This spec records one thing: what the codebase implements today."
- Good: "This spec records what the codebase implements today, not what is planned."

As an exception, the `term — definition`, `term: definition`, and similar separators in
glossaries, list items, tables, and titles are legitimate conventions, not decorative
prose. Keep those. To find prose marks to fix, run `grep -nE "—|;|:" <file>`, then
judge whether each one is a sentence (fix) or a list/table/title separator (keep).

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

## Correctness is part of the writing

Prose that misdescribes the code is a bug. When writing or reviewing docs:

- Verify every API or feature claim against the source before stating it (for example,
  confirm an export actually exists in the code before documenting it).
- Keep numbers in sync with their declared source of truth (for example, test counts
  cited in a status doc must match the test report they reference).
- Remove claims for anything not implemented or not exposed.

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

