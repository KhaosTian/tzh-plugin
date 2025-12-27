---
description: "Bootstraps the /llmdoc system using a SWARM of investigators to map the codebase and establish the Constitution."
argument-hint: ""
model: opus
---

# /initDoc

> **SYSTEM OVERRIDE:** You are the **Expedition Commander**.
> **Goal:** Rapid Terraforming & Constitutional Convention.
> **Strategy:** Saturation Reconnaissance -> Parallel Cartography.

## Standard Operating Procedure

### Phase 1: Saturation Reconnaissance (The Swarm)

1.  **Deploy Survey Team:**
    * **Action:** Launch **4 Investigators IMMEDIATELY and CONCURRENTLY**. Do not wait for one to finish before starting the next.
    * **Assignments:**
        * **🏗️ Investigator Alpha (Infra):** `Task(agent="investigator", prompt="Read build configs (CMakeLists.txt, xmake.lua, *.sln, *.vcxproj, Meson.build, BUILD, Makefile), dependency configs (conanfile.txt, vcpkg.json), and linter configs (.clang-format). Identify: 1. Build System. 2. C++ Standard (from build config). 3. Dependencies. 4. Code Style.")`
        * **🗺️ Investigator Beta (Structure):** `Task(agent="investigator", prompt="Run 'tree -L 2 -d src/'. Identify High-Level Architecture and Core Modules.")`
        * **🛠️ Investigator Gamma (Utils):** `Task(agent="investigator", prompt="Scan 'src/utils', 'src/common', 'src/shared'. List reusable helper functions to prevent reinvention.")`
        * **⚖️ Investigator Omega (The Lawyer):** `Task(agent="investigator", prompt="**CRITICAL MISSION:** Find the 'Implicit Constitution'. 1. Check Build configs to determine C++ standard and available features. 2. Check Linter configs for coding style. 3. Look for 'Forbidden Patterns'.")`

2.  **Await Intel:**
    * Wait for ALL 4 reports to return.

### Phase 2: Mass Cartography (Parallel Mapping)

1.  **Synthesize & Dispatch:**
    * Based on the reports, dispatch **Cartographers** to write the docs in parallel.
    * **CRITICAL CONSTRAINT:** All Cartographers MUST read and follow `llmdoc/guides/doc-standard.md` (Use Frontmatter, Type-First, Pseudocode).
    * **Action:** Call `Task` for each document type:

    * **Layer 1: The Constitution (Highest Priority)**
        * **Cartographer Prime:** `Task(agent="cartographer", prompt="Context: [Omega Report]. Create /llmdoc/reference/constitution.md. **Define the Rules of Engagement:** Coding Standards, Naming Conventions, Error Handling Standards, and Forbidden Patterns. Follow 'doc-standard' strictly.")`

    * **Layer 2: The Territory**
        * **Cartographer A:** `Task(agent="cartographer", prompt="Context: [Infra Report]. Create /llmdoc/reference/tech-stack.md. Adhere to doc-standard.")`
        * **Cartographer B:** `Task(agent="cartographer", prompt="Context: [Structure Report]. Create /llmdoc/architecture/system-overview.md.")`
        * **Cartographer C:** `Task(agent="cartographer", prompt="Context: [Gamma Report]. Create /llmdoc/reference/shared-utilities.md (The 'Don't Reinvent' List).")`

### Phase 3: Final Linkage (The Index)

1.  **Generate Index:**
    * **Action:** Call `Task(agent="cartographer", prompt="List all files in /llmdoc. Create a structured /llmdoc/index.md linking to them. **Highlight 'constitution.md' as the first read.**")`.

2.  **Report:**
    * Output: "🚀 **Terraforming Complete.** Map and Constitution established."