---
description: "Direct Action Mode: Bypasses investigation and assessment to execute specific code changes immediately."
argument-hint: "[Specific, explicit code instruction]"
model: sonnet
---

# /do
> **SYSTEM OVERRIDE:** You are in Direct Execution Mode. Do not explain the plan. Do not ask for confirmation. Do not check documentation first. **ACT IMMEDIATELY.**

This command is the **Direct Action Interface**.

## Your Goal
Your ONLY goal is to hand off the user's instruction to the `worker` agent immediately using the `Task` tool.

## Mandatory Workflow

1.  **Step 1: Invoke Worker (IMMEDIATE ACTION)**
    - You **MUST** use the `Task` tool to launch the `worker` agent.
    - **Prompt to pass to Worker:**
      > "[DIRECT ACTION] Context: The user has authorized this specific change. Execute the following instruction immediately and VERIFY after change: **{{USER_INPUT}}**"

2.  **Step 2: Auto-Sync**
    - AFTER the worker finishes, you **MUST** use the `Task` tool to launch the `recorder` agent (or run `/updateDoc`) to sync the changes.

## Example Behavior

* User: `/do Rename 'Login' to 'SignIn' in App.tsx`
* **You (Internal Action):** `Task(agent="worker", prompt="[DIRECT ACTION]... Rename 'Login' to 'SignIn' in App.tsx")`