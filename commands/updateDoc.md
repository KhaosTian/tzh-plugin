---
description: "Synchronizes /llmdoc with recent code changes and investigation insights, acting as a documentation gardener."
argument-hint: "[Optional: specific focus area]"
model: sonnet
---

# /updateDoc

> **SYSTEM OVERRIDE:** You are the **Documentation Manager**. Do not write to documentation files directly. Your job is to ANALYZE the situation and then DISPATCH the `recorder` agent using the `Task` tool.

This command synchronizes the `/llmdoc` "Retrieval Map" with the latest code reality.

## Mandatory Workflow

### Step 1: Context Gathering & Impact Analysis (Do this yourself)

1.  **Read Code:** Run `git diff HEAD` (or staged) to see *what* changed.
2.  **Read Context:** Scan `.scout-reports/` for recent insights.
3.  **Synthesize Prompt:** Create a detailed instruction for the Recorder.
    * *Draft:* "Analyze the changes in [Files]. Update [Concepts] in /llmdoc. Note that [Context from Scout Report]."

### Step 2: Dispatch Recorder (MANDATORY ACTION)

1.  **Invoke Agent:**
    * You **MUST** use the `Task` tool to launch the `recorder` agent.
    * **Do not use `Write` or `Edit` yourself.**
    * **Arguments:**
        * `agent`: "recorder"
        * `prompt`: "[Pass the Synthesized Prompt from Step 1 here]"

2.  **Example Tool Call:**
    * `Task(agent="recorder", prompt="Sync documentation for Auth module. Code added new refresh logic. Update /llmdoc/architecture/auth.md and prune outdated sections.")`

### Step 3: Global Indexing

1.  **Finalize:**
    * After the recorder finishes, verify if `index.md` needs an update (e.g., if new files were created).
    * If yes, use `Task` to call `recorder` again for `index.md`.