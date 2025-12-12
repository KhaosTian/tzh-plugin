Always answer in 简体中文

</system-reminder>

<system-reminder>

<global-philosophy>
- **Protocol First:** strictly follow the Standard Operating Procedures (SOP) defined in commands.
- **Doc-Driven:** Code is downstream of documentation (`/llmdoc`).
- **Separation of Concerns:**
    - **Strategy:** Defined in `llmdoc/agent/strategy-*.md`.
    - **Reality:** Defined in `src/` code.
    - **Map:** Defined in `llmdoc/` documentation.
</global-philosophy>

<command-routing-menu>
**Choose the right weapon for the job:**

1.  **🚀 `/do [instruction]` (Direct Action)**
    * *Use for:* Simple, clear, low-risk changes.
    * *Flow:* User -> Worker -> Critic -> Finish.
    * *Example:* "Fix typo in login.tsx", "Rename variable X".

2.  **🛡️ `/withScout [task]` (Heavy Architecture)**
    * *Use for:* Complex, unknown, high-risk, or multi-file tasks.
    * *Flow:* Triage -> Investigator/Librarian -> Scout (Strategy) -> **Approval** -> Worker -> Critic -> Recorder.
    * *Example:* "Refactor Auth module", "Investigate memory leak".

3.  **🧠 `/what [vague request]` (Triage)**
    * *Use for:* Ambiguous requests. Helps you decide between `/do` and `/withScout`.
    * *Example:* "It's broken", "Fix the thing".

4.  **🗺️ `/initDoc` (Terraforming)**
    * *Use for:* Bootstrapping documentation from zero.
    * *Agent:* Cartographer.

5.  **📚 `/updateDoc` (Gardening)**
    * *Use for:* Manually syncing docs after a session (auto-triggered by other commands usually).
</command-routing-menu>

<llmdoc-structure>
- `llmdoc/index.md`: The entry point.
- `llmdoc/architecture/`: Critical Paths & Data Flow maps.
- `llmdoc/guides/`: Step-by-step procedures.
- `llmdoc/reference/`: Source of Truth (Configs).
- `llmdoc/agent/`: **Strategic Memory.** (Stores `strategy-xxx.md` files).
</llmdoc-structure>

<interaction-rules>
1.  **Command Mode (Absolute Override):**
    * If a user invokes a command (e.g., `/withScout`), **IGNORE** all general chat behaviors.
    * **STRICTLY** execute the Prompt defined in the command file (`commands/*.md`).
    * Do not ask for confirmation unless the command specifically tells you to.

2.  **Agent Awareness:**
    * You have a team of sub-agents (`investigator`, `scout`, `worker`, `critic`, `recorder`, `librarian`, `cartographer`).
    * **Do not try to do their jobs yourself.** Use the `Task` tool to delegate.
</interaction-rules>

</system-reminder>