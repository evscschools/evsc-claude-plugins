---
name: "copy-ready-text"
description: "Deliver any text the user will paste somewhere else inside fenced code blocks so it gets a one-click copy button. Use this whenever the user asks for a description, bio, blurb, summary, tagline, email, Slack/Teams message, post, form-field answer, commit message, README section, prompt, or project instructions that will end up in another app or field, even if they never mention copying, code blocks, or formatting. Also use it when they ask for \"a couple of versions\" or \"something I can paste\"."
---

# Copy-ready text
 
When the user asks for text they will paste into another app, put it in a fenced code block. Most chat interfaces show a copy button on code blocks, so the user gets the exact text in one click. They don't have to drag-select or worry about stray bold markers, bullets, or your commentary coming along with it.
 
## When this applies
 
It applies when the text is going somewhere else: a GitHub or project description, a profile bio, an email or chat message, a form field, a social post, a commit message, a README section, a prompt or set of instructions for another tool, a spreadsheet formula, or a search string.
 
It does not apply to normal conversational answers, explanations, or advice the user only needs to read. If the user asked for a document or file, create the file instead of putting the content in a code block.
 
## Format
 
Put one block on each option. Above each block, add a short bold label saying what the version is for or how long it is, such as **Short (fits the GitHub About field)** or **Longer (for a README intro)**. When length matters, two or three versions are usually more helpful than one. Pick sensible defaults instead of asking clarifying questions first.
 
Keep explanations outside the blocks. Anything inside a block gets copied, so it should hold only the text the user will paste. If you need to explain a choice, do it in a sentence before or after the blocks.
 
Match the inside of the block to where the text is going:
 
- **Plain-text places** (description fields, form inputs, chat messages, email bodies): no Markdown syntax at all. No `**bold**`, `#` headings, or `-` bullets, because they would show up as literal characters once pasted.
- **Places that render Markdown** (README files, GitHub issues and comments, some wikis): Markdown is fine inside the block, since the raw Markdown is what the user wants to paste.
 
Don't hard-wrap paragraphs inside a block. Write each paragraph as one long line, with a blank line between paragraphs. Line breaks inside the block get pasted too, and they break up text in fields that reflow on their own.
 
Use a bare fence (three backticks with no language) for prose, so the interface doesn't add syntax colors. Use the right language tag for code or formulas. If the content itself contains triple backticks, fence it with four.
 
If the text has placeholders the user must fill in, use `[square brackets]` and point them out outside the block, so nothing goes out with a placeholder still in it.
 
## Mind the destination
 
If the destination has a known character limit, stay under it and say so in the label. For example, the GitHub repository "About" description allows 350 characters. If the text is going somewhere public (a public repo, a website, a social post), leave out personal names, email addresses, internal IDs, and similar details unless the user clearly wants them there.
 
## Example
 
The user asks: "Can you write me a description for this project?"
 
A good response says in one line what it assumed, then gives:
 
**Short** (fits a GitHub About field):
 
```
Two e-ink door signs that show who is in the office, at another site, or out, driven by one shared Google Sheet.
```
 
**Longer** (for a README intro):
 
```
This repo holds the markup, spreadsheet formulas, and scripts for two e-ink door signs. Each sign reads its own tab of a shared Google Sheet and shows each person's current status. A shared privacy policy shows sensitive absence reasons as a generic "Out of Office."
```
 
It ends with a short offer to adjust the length or tone, outside the blocks.
 