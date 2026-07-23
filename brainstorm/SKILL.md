---
name: brainstorm
description: Superpowers methodology for agentic software development. Includes brainstorming, planning, TDD, debugging, code review, and subagent workflows.
license: MIT (see LICENSE file)
metadata:
  author: Prime Radiant (original) | Agent Skills Collection
  source: https://github.com/obra/superpowers
  keywords:
  - brainstorming
  - planning
  - TDD
  - debugging
  - code review
  - subagent
  - development workflow
  - software methodology
---

# Superpowers - Agentic Development Methodology

A complete software development methodology for coding agents, built on composable skills that activate automatically throughout the development process.

## Skills Overview

### Core Development Workflow

| Skill | Description |
|-------|-------------|
| **brainstorming** | Activates before writing code. Refines rough ideas through questions, explores alternatives, presents design in sections for validation. Saves design document. |
| **writing-plans** | Activates with approved design. Breaks work into bite-sized tasks (2-5 minutes each). Every task has exact file paths, complete code, verification steps. |

### Implementation

| Skill | Description |
|-------|-------------|
| **subagent-driven-development** | Fast iteration with two-stage review (spec compliance, then code quality) |
| **executing-plans** | Batch execution with checkpoints for review |
| **dispatching-parallel-agents** | Concurrent subagent workflows |
| **test-driven-development** | RED-GREEN-REFACTOR cycle enforcement |

### Quality & Review

| Skill | Description |
|-------|-------------|
| **requesting-code-review** | Pre-review checklist, reports issues by severity |
| **receiving-code-review** | Responding to feedback |
| **systematic-debugging** | 4-phase root cause process |
| **verification-before-completion** | Ensure fixes are actually fixed |

### Collaboration & Git

| Skill | Description |
|-------|-------------|
| **using-git-worktrees** | Parallel development branches with isolated workspaces |
| **finishing-a-development-branch** | Merge/PR decision workflow |

### Meta

| Skill | Description |
|-------|-------------|
| **using-superpowers** | Introduction to the skills system |
| **writing-skills** | Create new skills following best practices |

## The Basic Workflow

```
brainstorming ──────► writing-plans ──────► executing-plans ──────► code review ──────► finish
     │                    │                      │
     │                    ▼                      ▼
     │              subagent-driven        test-driven
     │              development             development
     ▼
using-git-worktrees
```

### Phase 1: Brainstorming (HARD-GATE)
- Explore project context
- Ask clarifying questions (one at a time)
- Propose 2-3 approaches with trade-offs
- Present design in sections for validation
- Write and commit design document
- **NO implementation until design is approved**

### Phase 2: Planning
- Create detailed implementation plan
- Break into bite-sized tasks (2-5 minutes each)
- Each task has exact file paths, complete code, verification steps
- TDD emphasis: RED → GREEN → REFACTOR

### Phase 3: Execution
- **Subagent-Driven (recommended):** Fresh subagent per task + two-stage review
- **Inline Execution:** Batch execution with checkpoints

### Phase 4: Review
- Request code review before moving to next task
- Respond to feedback constructively
- Systematic debugging when issues arise

### Phase 5: Finish
- Verify all tests pass
- Choose: merge, PR, keep working, or discard
- Clean up worktree if needed

## Core Principles

- **Test-Driven Development** - Write tests first, always
- **Systematic over ad-hoc** - Process over guessing
- **Complexity reduction** - Simplicity as primary goal
- **Evidence over claims** - Verify before declaring success
- **YAGNI** - You Aren't Gonna Need It
- **DRY** - Don't Repeat Yourself

## Key Anti-Patterns

- ❌ "This is too simple to need a design" — Every project goes through brainstorming
- ❌ Writing code before tests (TDD)
- ❌ Large, monolithic tasks — Break into 2-5 minute pieces
- ❌ Placeholders in plans — "TBD", "implement later", "similar to X"
- ❌ Skipping code review

## Quick Reference

### Brainstorming Checklist
1. Explore project context
2. Offer visual companion just-in-time (not upfront)
3. Ask clarifying questions (one at a time)
4. Propose 2-3 approaches with trade-offs
5. Present design in sections
6. Write design doc to `docs/superpowers/specs/`
7. Spec self-review
8. User reviews written spec
9. Invoke writing-plans

### Plan Structure
```markdown
# Feature Implementation Plan

> **REQUIRED SUB-SKILL:** superpowers:subagent-driven-development

**Goal:** [One sentence]

**Architecture:** [2-3 sentences]

## Global Constraints

[Version floors, naming rules, etc.]

---

### Task 1: [Component Name]

**Files:**
- Create: `path/to/file.py`
- Modify: `path/existing.py:123-145`
- Test: `tests/path/test.py`

**Interfaces:**
- Consumes: [from earlier tasks]
- Produces: [for later tasks]

- [ ] **Step 1: Write failing test**
- [ ] **Step 2: Run to verify it fails**
- [ ] **Step 3: Write minimal code**
- [ ] **Step 4: Run to verify it passes**
- [ ] **Step 5: Commit**
```

## Resources

- [Official Documentation](https://github.com/obra/superpowers)
- [Discord Community](https://discord.gg/superpowers)
- [Release Announcements](https://github.com/obra/superpowers/releases)

## License

MIT License - see LICENSE file for details. Originally from [obra/superpowers](https://github.com/obra/superpowers) by Prime Radiant.
