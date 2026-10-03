---
name: tuaha-guidelines
description: >
  Initialize a new software project with AI-Native SDLC documentation files:
  intent.md, spec.md, and CLAUDE.md following the Claude Academy AI-Native SDLC Playbook.
  Activate when the user starts a new project, mentions creating project documentation,
  asks for intent.md / spec.md / CLAUDE.md files, or says they want to set up a project
  before coding begins. Also trigger on phrases like "create project docs",
  "setup my project", "initialize project structure", or when the user wants approval
  before starting development work.
when_to_use: >
  Use this skill when:
  (a) the user starts a new project or repository,
  (b) the user explicitly asks for intent.md, spec.md, or CLAUDE.md,
  (c) the user wants to follow the AI-Native SDLC Playbook workflow,
  (d) the user says they want to review/approve before coding starts,
  (e) the user mentions "project setup", "project initialization", or "create docs",
  (f) the user references Claude Academy, AI-Native SDLC, or intent/spec/CLAUDE.md pattern.
  Do NOT use if the user is already mid-development and only wants code changes.
effort: high
---

# Tuaha Guidelines: AI-Native SDLC Project Initializer

This skill initializes any new software project with the three core documentation files from the Claude Academy AI-Native SDLC Playbook:

1. **intent.md** — Captures what is wanted, why, and under what constraints.
2. **spec.md** — Requirements and design spec derived from intent.md.
3. **CLAUDE.md** — Project-specific conventions, commands, architecture, and common mistakes.

## Workflow

When this skill activates, follow these steps in order. Do NOT skip ahead to coding until the user explicitly approves.

### Step 1: Interview the User

Before creating any files, interview the user to understand the project. Ask about:

- **Project name and one-line description**
- **Problem being solved** — What can't be done today? Who is affected?
- **Proposed outcome** — What does "better" look like?
- **Affected users and systems** — Who will use this? What systems integrate?
- **Constraints** — Technical, security, compliance, budget, timeline.
- **Open questions** — Anything still unresolved.
- **Tech stack** — Languages, frameworks, tools (for CLAUDE.md).
- **Build/test/lint commands** — How is the project built and tested?
- **Architecture overview** — Key directories, patterns, boundaries.
- **Team conventions** — Coding standards, naming, patterns to follow or avoid.
- **Common mistakes** — Things Claude or new team members often get wrong.

If the user already has some of this written down, ask them to share it rather than re-asking.

### Step 2: Create intent.md

Write `intent.md` at the project root using this template:

```markdown
# Intent: <project-name>
Author: <user-name>. Status: draft.

## Problem
<Describe the problem in the user's own words.>

## Proposed outcome
<What success looks like. Concrete and measurable if possible.>

## Affected users and systems
<Who will use this? What systems does it touch?>

## Constraints
<Technical, security, compliance, budget, timeline constraints.>

## Open questions
<Anything unresolved that needs decision before design.>
```

Guidelines for intent.md:
- Use the user's own language; do not over-formalize.
- Keep it under one page.
- Focus on "what" and "why", not "how".
- Flag anything that seems ambiguous so the user can clarify.

### Step 3: Create spec.md

Write `spec.md` at the project root derived from intent.md. Use this structure:

```markdown
# Spec: <project-name>
Derived from: intent.md. Status: draft.

## Requirements
<Functional and non-functional requirements.>

## Design
<High-level design, component breakdown, data flow.>

## Interface
<APIs, UI, CLI, or whatever the external surface is.>

## Data model
<Key entities, schemas, storage.>

## Areas of concern
<Flagged risks, contradictions, or things needing escalation.>

## Open questions carried forward
<From intent.md, anything still unresolved.>
```

Guidelines for spec.md:
- The product owner (user) reviews this, not writes it.
- Flag areas of concern explicitly; do not hide uncertainty.
- Make it detailed enough that an engineer can plan against it.
- Keep it under two pages if possible.

### Step 4: Create CLAUDE.md

Write `CLAUDE.md` at the project root using this template:

```markdown
# <project-name>

## Commands
- Build: <command>
- Test: <command> (unit), <command> (integration)
- Lint: <command>
- Run: <command>
- Deploy: <command>

## Conventions
- <Language/framework version and key conventions>
- <Naming patterns>
- <Code style rules>

## Architecture
- <Directory structure and what goes where>
- <Key abstractions and boundaries>
- <External integrations>

## Things Claude gets wrong
- <Mistake 1 and how to avoid it>
- <Mistake 2 and how to avoid it>
```

Guidelines for CLAUDE.md:
- Keep it under one page. Claude reads all of it at the start of every session.
- Only include what a new joiner would need on day one.
- Update rule: when Claude makes a mistake twice, the correction goes here.
- Include build, test, lint commands explicitly.

### Step 5: Present and Wait for Approval

Present all three files to the user clearly. Use this exact message format:

> I have created the following AI-Native SDLC project documentation files:
>
> 1. **intent.md** — Captures the problem, proposed outcome, constraints, and open questions.
> 2. **spec.md** — Requirements and design spec derived from intent.md.
> 3. **CLAUDE.md** — Project conventions, commands, architecture, and common mistakes.
>
> Please review all three files. Let me know any changes you'd like, or approve them so we can proceed to the coding phase.
>
> **Do not start coding until you explicitly approve.**

Do NOT proceed to coding, file generation, or implementation until the user explicitly says they approve or gives a clear go-ahead like "looks good", "approved", "let's start coding", "proceed", etc.

### Step 6: Post-Approval Handoff

Once approved, the skill's job is done. Normal development proceeds. The three files now live in the repo root and should be:
- Checked into version control.
- Maintained by the team.
- Updated whenever intent changes or Claude repeats a mistake.

## Important Rules

- **Never skip the approval gate.** This skill exists to enforce human review before coding begins.
- **Do not generate code during this skill's execution** unless the user explicitly overrides and asks for it.
- **Keep files concise.** Long docs waste context window and go stale.
- **Use the user's own words** in intent.md; do not translate into corporate jargon.
- **Flag concerns early** in spec.md rather than hiding uncertainty.
- **CLAUDE.md is a living document.** It should be updated as the project evolves.

## Example Output Layout

After running this skill, the project root should contain:

```
<project-root>/
├── intent.md
├── spec.md
├── CLAUDE.md
└── <existing or future code files>
```

All three files are Markdown, human-readable, version-controlled, and immediately consumable by the next stage of the AI-Native SDLC.
