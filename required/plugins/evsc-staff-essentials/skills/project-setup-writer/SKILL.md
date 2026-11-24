---
name: "project-setup-writer"
description: "Writes the title, description and instructions for a new Claude Project. Use when someone is setting up a project, wants project instructions, or asks what to name or describe one."
---
 
# Project Setup Writer
 
Help the user fill in the three text fields of a new Claude Project: the **title**, the **description**, and the **instructions**. The user will paste each one into a separate field, so the output should be easy to copy and need no cleanup.
 
The three fields do different jobs, and keeping them apart is most of the craft:
 
- **Title**: what the project is called in the sidebar and project list. It's for finding the project again at a glance.
- **Description**: a short note for people (the user, or teammates if it's shared) saying what the project is for. It's not where behavior goes.
- **Instructions**: what Claude reads in every chat in the project. This is the part that changes how Claude behaves, so most of the effort goes here.
## Step 1: Understand the project
 
You need to know:
 
1. **Purpose**: what the user will keep coming back to this project for. Ask for the recurring tasks, not just the topic. "Marketing" is a topic; "drafting weekly newsletter copy and LinkedIn posts for our bakery" is a purpose.
2. **Who uses it**: just the user, or a team? Who is the end audience for what Claude produces?
3. **Context Claude needs every time**: who the user is, their role, the organization, the product, terms of art, and any standing facts.
4. **Files they'll upload** to the project's knowledge, if any (style guides, docs, data, past examples).
5. **Preferences**: tone, length, format, language, things to always or never do, and mistakes they're tired of correcting.
Pull as much as you can from what the user already said. That includes an earlier conversation they want to turn into a project, or an existing prompt they pasted. Only ask about gaps that would really change the instructions. Ask in one short batch, at most 3 or 4 questions, rather than an interview. If the request is already clear, skip the questions and draft. A draft gets better feedback than a questionnaire, and you can say which assumptions you made.
 
## Step 2: Write the title
 
- 2 to 5 words, specific enough to tell apart from the user's other projects ("Bakery Newsletter & Social" rather than "Marketing Help").
- Lead with the distinctive word, because sidebars truncate.
- Skip filler such as "Project", "Assistant", "AI" or "Claude", and skip emoji unless the user likes them.
- Give 2 or 3 options when there's no obvious best. They're cheap to offer and naming is taste.
## Step 3: Write the description
 
- 1 or 2 plain sentences: what the project is for and, if shared, who it's for.
- Write it for a person skimming a project list, not as instructions to Claude. Leave out "You are…" and rules.
- Example: "Drafts and edits our weekly email newsletter and social posts in the Rise & Crumb brand voice. Upload new menu items to Knowledge before asking for promo copy."
## Step 4: Write the instructions
 
Write in second person, addressed to Claude, as a clear brief to a capable colleague who knows nothing about the user yet. Keep it as short as the project allows. Every line is read in every chat, so lines that state what Claude already does ("be helpful", "be accurate") only dilute the ones that matter.
 
Use this structure. Drop any section that would be empty, and rename headings if it reads better:
 
```
## Context
Who the user is, their role and organization, and what this project is for. Include standing facts and terms Claude should know.
 
## What you'll usually be asked to do
The recurring tasks, each with a line on what a good result looks like.
 
## How to work
The approach: when to ask clarifying questions and when to just draft, how much to explain, and how to handle uncertainty.
 
## Style and format
Tone, length, structure, language, spelling variant, formatting defaults.
 
## Using the project files
What each uploaded file is and when to rely on it (for example, "Follow brand-voice.pdf for all customer-facing copy; it overrides general style advice").
 
## Avoid
The specific mistakes or habits the user doesn't want, with the reason when it isn't obvious.
```
 
Principles that make instructions work:
 
- **Explain the why.** "Keep posts under 150 words, because most readers see them on mobile" generalizes better than "MAX 150 WORDS". Avoid all-caps and stacks of ALWAYS/NEVER. Calm, reasoned guidance is followed more reliably and more sensibly.
- **Say what to do, not only what to avoid.** "Write in short paragraphs of 2 to 3 sentences" beats "Don't write walls of text".
- **Be concrete.** Name the audience, the reading level, the format and the length. Vague adjectives like "professional" or "engaging" mean different things to different readers, so pin them down with a short example or a description.
- **Include a short example** when the user's voice or format is particular. Show one, a few lines long, and label it as an example so Claude doesn't copy it word for word.
- **Only reference files the user said they'll upload**, and use their real names if given. Otherwise, write the section generically or leave it out and suggest what to upload.
- **Don't invent facts** about the user's business, product or audience. Where something important is unknown, leave a clearly marked placeholder like `[YOUR PRODUCT NAME]` and point it out.
- **Match length to need.** A personal writing helper might need 10 lines. A team project with a style guide, workflows and edge cases might need a page. Don't pad a simple one or truncate a complex one.
## Step 5: Deliver
 
Put each field in its own fenced code block so each one has a copy button, and keep all explanation outside the blocks. Use this order:
 
**Title** (one block per option if offering several)
 
```
Bakery Newsletter & Social
```
 
**Description**
 
```
Drafts and edits our weekly email newsletter and social posts in the Rise & Crumb brand voice.
```
 
**Instructions**
 
```
## Context
...
```
 
If the instructions contain their own code fences, wrap the instructions block in four backticks so the outer block doesn't break.
 
After the blocks, add a few short lines, only where useful:
 
- **Assumptions** you made and placeholders to fill in.
- **Suggested files to upload** to the project's knowledge, if that would help (a style guide, past examples they liked, a glossary).
- **Skills worth turning on**, if any fit the project (see below).
- **One or two starter prompts** that show how to use the project.
If the instructions run long or the user asks for a file, also offer them as a downloadable `.md` file. The code blocks stay the main delivery, since they're what the user pastes.
 
### Skills worth turning on
 
Skills give Claude specialized know-how, such as building Word, Excel, PowerPoint or PDF files. Once a skill is on, Claude uses it automatically whenever a task calls for it, including in this project. So the right skill can make the project noticeably better at its main job.
 
- **Match skills to the recurring tasks from Step 1.** Reports, proposals or letters call for the Word or PDF skills. Budgets, trackers or data analysis call for Excel. Decks call for PowerPoint. Brand-sensitive copy calls for a brand or style skill if the user's organization has one. Suggest at most 2 or 3, each with one line on what it adds to *this* project. If nothing fits, suggest nothing, because a list of loosely related skills is just noise.
- **Check what's already on.** Skills in your own list of available skills are already enabled, so don't tell the user to turn those on. At most, mention that they'll kick in automatically. If the session has a tool that lists or suggests skills the user can add, use it to find real candidates instead of guessing names.
- **Say where to turn them on:** Settings > Plugins > Discover. Menu names change over time, so if the user can't find something, they can contact EVSC Technology Support on the EVSC Connect website.
- **Mention that skills are account-wide, not per-project.** Turning one on affects all of the user's chats. That's usually what they want, but they should know.
There's usually no need to name skills inside the project instructions. Claude uses enabled skills on its own when a task calls for them, so naming them adds lines without changing behavior.
 
## Step 6: Refine
 
Invite one round of changes, and when the user asks for a change, resend only the field or fields that changed, each in its own block. If they later say Claude in the project is doing something they don't like, the fix usually belongs in the instructions: add a line to "Avoid" or "How to work" with the reason, rather than rewriting the whole thing.