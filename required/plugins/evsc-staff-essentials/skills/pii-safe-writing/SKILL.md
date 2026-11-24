---
name: "pii-safe-writing"
description: "Use when writing or editing anything that will be saved, committed, pushed, published or shared — changelogs, READMEs, TODOs, code, comments, commit messages, docs — to keep personal information out."
---

# Keep personal information out of anything that persists

Conversation is a working space: it's fine to discuss specific people, emails, and accounts there when the user has shared them. The moment text is headed somewhere that **persists or can be shared** — a file that gets committed or pushed (GitHub, GitLab), a changelog, README, TODO, handoff, code comment, commit message, issue, PR description, wiki, published page or shared document — it must not identify individuals.

This applies even if the repository is private. Private repos get shared, forked, made public, and copied into other tools, and git history keeps every version forever.

## What counts as personal information

Never write these into a persistent or shareable file:

- **Names** of real people (staff, students, customers, colleagues), including first names alone when the context makes them identifiable.
- **Personal email addresses**, and their local parts or usernames on their own (`first.last`, `jsmith2`) — the local part is usually the name.
- **Phone numbers, home addresses, photo URLs, employee or student ID numbers.**
- **Combinations that single someone out**: job title + building, "the only nurse at X", a rename from one surname to another, dates of a specific person's hire, departure, leave, or name change.
- **Anything about a person's employment, health, discipline, family, or legal status** (e.g. "left the district", "on leave", a surname change after marriage).
- **Student information** of any kind — treat as strictly confidential (FERPA and similar rules).
- **IP addresses or device identifiers** tied to a person.

## What is fine

- Counts, totals, aggregates, percentages ("15 pairs", "4,158 users").
- Role, group, and service addresses that don't belong to one person (`teacher@`, `allstaff@`, a support mailbox, a shared org account) — but describe a shared account generically if naming it adds nothing.
- Domain names, product names, plugin names, group names.
- Internal numeric record IDs (e.g. a database user ID) **only when needed for traceability**, and **never** next to a name, email, username, or detail that identifies the person.
- The author's own name where the author has chosen to put it (attribution, "Author:" lines).
- Fictional placeholders: `first.last@example.org`, "User A / User B".

## How to write about people instead

Describe by role or situation, not identity:

- "a renamed teacher", "one staff member whose address changed", "the audit's oldest pair", "a student-teacher account", "a departed editor".
- "User A's old account was created 13 hours after User B's..." when two parties must be distinguished.
- Keep the technical facts (timestamps, error codes, counts, sequence of events) — those are what make a changelog useful. Drop only what identifies the person.

## Two tiers: public files vs. private notes

Sometimes a later debugging step genuinely needs to know *who*. Then:

1. Put the identifying detail only in a **private** working place the user controls (a private project doc, a private handoff note) — the minimum needed.
2. In the public/shared file, refer to it generically: "which user: see the private handoff."

Never copy identifying details from a private note into a public file.

## Before delivering any persistent text

Scan the output — including every find/replace block, commit message, and code comment — for:

- `@` followed by a personal-looking address, or `word.word` local parts
- Capitalized first/last name pairs, or a single first name in a person context
- Record IDs sitting next to any of the above
- Before/after surname changes, job-title + location pairs

Rewrite anything that matches. In a FIND block, PII is acceptable only when it is the text being **removed**.

## When personal information is already in a file

If a file being edited already contains PII:

- Point it out briefly and offer to remove it in the same change.
- Explain that removing it from the current file doesn't remove it from git history; scrubbing history requires a history rewrite (e.g. `git filter-repo`) and a force-push, and anyone who already cloned keeps a copy. For a public repo, that may be worth doing; for a private one, removing it going forward is usually enough. Let the user decide.

## Code and configuration

- Don't hard-code real people's emails or names in source, tests, fixtures, or sample data. Use placeholders.
- If a config file that gets committed contains real people's accounts (exclusion lists, admin lists), flag it and suggest keeping that list outside version control (environment/script properties, an untracked config file).
- Log messages written to shared logs are a judgment call — operational logs may need emails to be useful — but never copy those log lines into docs or commits.

## Secrets are a separate, stricter rule

Passwords, API keys, tokens, and application passwords must never appear in any tracked file or in output at all. If one is found in a tracked file, say so immediately, recommend rotating it, and suggest moving it to a secret store (environment variables, script properties, a secrets manager).