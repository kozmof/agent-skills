---
name: Refine spec
description: Refine the specifications which a user pointed out
allowed-tools: Read, Grep, Glob, AskUserQuestion 
---

# Refine Specifications
Recursively perform the following tasks to refine the specifications:
- Read the specification file.
- Identify the primary goal and its sub-goals.
- Breakdown the steps required to achieve the goal.
- Identify any ambiguities or unclear points within those steps.
- Use AskUserQuestion to clarify any points of uncertainty.

# Testable Spec
Testability is key. Idempotency is the gold standard for testing.
- Categorize implementations by domain.
- Analyze critical paths, edge cases, error scenarios, and manual intervention points.
- Outline the test plans.

# Instructions
1. Read the target files using the Read tool.
2. Search for specific patterns using Grep.
3. Find related files using Glob
4. Ask any ambiguities using AskUserQuestion.
