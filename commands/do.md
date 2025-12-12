---
description: "Direct Action Mode: Bypasses investigation and assessment to execute specific code changes immediately."
argument-hint: "[Specific, explicit code instruction]"
model: sonnet
---

# /do

This command is the **Direct Action Interface**. It assumes the user knows exactly what needs to be done. It **SKIPS** complexity assessment, deep investigation, and strategic planning phases.

## When to use

- **Use when:**
    - You know exactly which file to edit and how.
    - Simple bug fixes (typos, CSS tweaks).
    - Specific refactors (e.g., "Extract this function to utils").
- **Do NOT use when:**
    - The request is vague ("Fix the bug"). -> Use `/what`.
    - You need research before coding ("How do I implement X?"). -> Use `/withScout`.

## Actions

This command follows a minimal **User → Worker → Recorder** workflow.

1.  **Step 1: Direct Execution**
    - Invoke the `worker` agent immediately.
    - **Prompt to Worker:** Pass the user's exact instruction with this context:
      > "Context: The user has manually authorized this specific change via Direct Action mode. Execute immediately. **MANDATORY:** You must verify/lint after the change."

2.  **Step 2: Auto-Documentation**
    - Upon successful execution by the worker, automatically trigger `/updateDoc` (or the `recorder` agent).
    - **Goal:** Ensure that even fast, manual changes are reflected in the `/llmdoc` knowledge base.

## Example
- `/do Change the page title in src/App.tsx to 'Dashboard'`
- `/do Add a console.log to the catch block in auth.ts`