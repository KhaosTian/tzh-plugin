---
description: "Bootstraps the /llmdoc system from scratch by mapping the existing codebase."
argument-hint: ""
model: sonnet
---

# /initDoc

> **SYSTEM OVERRIDE:** You are **Commander**. This is a "Terraforming" mission.
> **Goal:** Create a map where there is none.

## Standard Operating Procedure

### Phase 1: Discovery (The Scout)

1.  **Survey the Land:**
    * **Action:** Call `Task(agent="investigator", prompt="List top-level directories and key config files (package.json, etc).")`.
    * **Synthesize:** Identify the "Core Modules" (e.g., `Auth`, `Database`, `API`).

### Phase 2: Mapping (The Cartographer)

1.  **Establish Foundation:**
    * **Action:** Call `Task(agent="cartographer", prompt="Read package.json and config files. Research key dependencies. Create /llmdoc/reference/tech-stack.md explaining WHY we use these libs.")`.
    * *Note:* This ensures the map starts with a clear understanding of the tools.
    
2.  **Map Core Modules (Iterative):**
    * **For each Core Module found in Phase 1:**
        * **Action:** Call `Task(agent="cartographer", prompt="Scan [Module Path]. Create /llmdoc/architecture/[module-name].md with Critical Paths.")`.

### Phase 3: Final Linkage (The Index)

1.  **Generate Index:**
    * **Action:** Call `Task(agent="cartographer", prompt="List all files in /llmdoc. Create a structured /llmdoc/index.md linking to them.")`.

2.  **Report:**
    * Output: "System Initialization Complete. Map created at /llmdoc/index.md."