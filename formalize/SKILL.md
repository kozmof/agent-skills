---
name: Formalize
description: Analyze the code and identify areas for formalization.
allowed-tools: Read, Grep, Glob
---

# Formalize

Balance is key; Excessive abstraction is NOT formalization.

## What is NOT formalization:

- Overusing utilities, factories, helpers, or builder functions is NOT formalization.
- Adding detailed documentation is NOT formalization.
- Simply converting code into classes is NOT formalization.

## Evaluation Criteria:

Evaluate the formalization based on the following:
- Does it improve overall code readability?
- Are context boundaries and responsibilities fine-grained?
- Does it improve testability?
- Does the structure bring regularity to complexity?
- Are the rules for extension clear?
- Are effects on values simple?
- Is there regularity in data manipulation?
- Does it maximize language-specific features? (e.g., TypeScript types, Rust pattern matching)
- Are there any pitfalls that might mislead someone reading the code for the first time?
- Which parts of the structure are most likely to become fragile or be bypassed in the future?

## Output rules:

- Focus on the code itself rather than the comments.
- Iteratively check both the fine details and the overall structure of the code.
- Skip positive feedback.
- Omit metrics such as priority or 5-star ratings.

## Code checklist

1. Data structures
2. Interfaces
3. Algorithms
4. Specific Implementations

## Instructions

1. Read the target files using Read tool
2. Search for patterns using Grep
3. Find related files using Glob
4. Provide detailed feedback on formalization
