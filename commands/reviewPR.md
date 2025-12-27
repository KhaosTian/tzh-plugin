---
description: "Conducts an automated, multi-perspective review of a Pull Request with structured output."
argument-hint: "[PR number or URL]"
---

# /reviewPR

This command performs a "Virtual Tech Lead" review, checking for code quality, architectural integrity, and documentation completeness.

## When to use

- **Use when:** User asks to review a PR or a branch before merging.

## Actions

1.  **Step 1: Fetch & Prepare**
    - Get PR details (`gh pr diff`, `gh pr view`).
    - **Context:** Read `/llmdoc/architecture` to understand the intended design patterns.

2.  **Step 2: Parallel Structured Analysis**
    - Deploy `finder` agents with specific personas. **inspectorAL:** Each finder MUST output an `<Issues>` list and an `<Assessment>` score.

    - **finder A (Code & Safety):**
      - Check: Error handling, strict typing, security risks, leftover debug code.
    - **finder B (Architecture & Pattern):**
      - Check: Does this match the `/llmdoc` patterns? Separation of concerns?
    - **finder C (Completeness):**
      - Check: Is documentation updated? Are error cases handled?

3.  **Step 3: Synthesize Report**
    - Merge findings. Filter out duplicates.
    - **Classify:**
      - 🔴 **Blocking:** Security risks, major bugs, architectural violations.
      - 🟡 **Warning:** Missing documentation, confusing naming, edge cases.
      - 🟢 **Nitpick:** Formatting, typos.

4.  **Step 4: Interactive Submission**
    - Present the structured report to the user.
    - Options: "Post as Comment", "Request Changes", or "Approve".
    - Execute the `gh pr review` command based on choice.