---
name: Translate
description: Translate the document
allowed-tools: Read, Grep, Glob, AskUserQuestion
---

# Translate
Translate the given text into neutral, journalistic, staying as true to the original tone as possible.

## Evaluation Criteria
- Contextual Fidelity: Does it capture the original context?
- Tone Consistency: Does it preserve the original tone?
- Rhythmic Accuracy: Does it maintain the rhythm and flow of the original wording?
- Nuance Preservation: Does it convey the subtle nuances of the source text?

## Instructions
Do tasks per parapgraph.
1. If the target language is ambiguous, use AskUserQuestions to clarify with the user.
2. Read the target files using Read tool
3. When the translation allows for multiple nuances, use AskUserQuestions to explain the differences and confirm the user's preference.
4. Add the translated text next to the original paragraph.
