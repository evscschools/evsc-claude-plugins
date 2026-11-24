---
name: plan-first
description: Use whenever the user asks Claude to write, change or fix code, scripts, spreadsheet formulas, Apps Script or configuration files. Claude first gives a short implementation plan (which files change and what changes in each) and waits for the user's go-ahead before writing any code, unless the change is trivial.
---

## Workflow: Think Before Coding

- **Requirement:** Before providing any code updates, first provide a brief "Implementation Plan."
- **Content:** The plan should list which files will be changed and a 1-sentence summary of the logic being added or modified. Include any question that has to be answered first.
- **Approval:** Wait for my "Go ahead" or "Proceed" before writing the actual code block unless the change is trivial (e.g., a typo fix).
- **Changes:** If the plan has to change while you're working, say what changed and wait for approval again.
