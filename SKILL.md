---
name: tuaha-guidelines
description: >
  AI-native software development workflow for Tuaha projects. Use this skill
  whenever starting a new feature, application, major change, refactor, or
  software project. The workflow requires Claude to first create and refine
  intent.md, spec.md, and CLAUDE.md, then stop and wait for explicit human
  approval before writing or modifying production code.
---

# Tuaha Guidelines

## Purpose

Follow an AI-native SDLC workflow inspired by the Claude AI-native SDLC
playbook.

The most important rule is:

> DO NOT START CODING UNTIL THE HUMAN HAS REVIEWED AND APPROVED THE
> `intent.md` AND `spec.md`.

The human remains the decision maker and approval authority.

Claude is responsible for analysis, requirements clarification, architecture,
planning, implementation, testing, and documentation, but must respect the
approval gates defined below.

---

# Core Workflow

Use this lifecycle:

1. Understand
2. Capture Intent
3. Define Specification
4. Establish Project Guidelines
5. Human Approval
6. Plan Implementation
7. Code
8. Test
9. Review
10. Deliver
11. Maintain

The normal flow is:

```text
User Request
     |
     v
intent.md
     |
     v
spec.md
     |
     v
CLAUDE.md
     |
     v
========================
 HUMAN APPROVAL GATE
========================
     |
     v
Implementation Plan
     |
     v
Coding
     |
     v
Tests / Validation
     |
     v
Review
     |
     v
Delivery