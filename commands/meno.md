---
description: "Updates the project's 'Lessons Learned' knowledge base to prevent repeating mistakes."
argument-hint: "[The lesson or insight]"
---

# /memo

> **Goal:** Institutional Memory.
> **File:** `/llmdoc/reference/lessons-learned.md`

## Actions

1.  **Step 1: Ingest**
    * Analyze the user's insight.
    * *Example:* "Next.js App Router doesn't support generic Context providers."

2.  **Step 2: Archive**
    * Call `Task(agent="tracker")`.
    * **Prompt:** "Append this insight to `/llmdoc/reference/lessons-learned.md`. Format: `- **[Date] [Topic]:** [Insight]`."

3.  **Step 3: Index**
    * Ensure `finder` and `planner` check this file in future missions.