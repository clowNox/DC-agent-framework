# Claude Agent Framework

A production-grade multi-agent system built for Claude Code. Designed to make you a better developer by automating code review, test writing, architecture analysis, compliance checking, documentation, and continuous learning — all while keeping you in full control of every decision.

---

## What This Is

This framework is a system of 8 intelligent agents that work together inside Claude Code. Each agent has a specific job. They communicate through a structured file system. An orchestrator manages everything. You stay in the loop on every decision that matters.

The system gets smarter with every project. Mistakes become lessons. Lessons get applied. Patterns get surfaced. Nothing is repeated twice.

---

## The 8 Agents

| Agent | File | What It Does |
|---|---|---|
| Discovery Agent | `agents/discovery-session.md` | Runs at project start. Asks questions until it fully understands what you want to build. Creates a locked task list |
| Orchestrator | `agents/orchestrator.md` | Brain of the system. Maintains the master index, verifies grades, manages failures, handles the learning flow |
| Code Reviewer | `agents/code-reviewer.md` | Reviews code changes for bugs, security issues, and quality problems. Assigns preliminary grades |
| Test Writer | `agents/test-writer.md` | Identifies untested code, writes meaningful tests, runs them, reports results |
| Architecture Reviewer | `agents/architecture-reviewer.md` | Evaluates system structure, module boundaries, dependencies, and scalability |
| Compliance Reviewer | `agents/compliance-reviewer.md` | Checks code against SOC2, HIPAA, GDPR, App Store, and Play Store requirements |
| Doc Generator | `agents/doc-generator.md` | Writes and maintains accurate project documentation automatically |
| Pattern Recognition | `agents/pattern-recognition.md` | Reads accumulated project history, finds repeating patterns, surfaces insights with suggested fixes and estimated impact |

---

## How It Works

### Starting a Project
Say **"new project"** to Claude Code. The discovery session activates automatically. Claude asks you questions one at a time until it fully understands what you want to build. A task list is created collaboratively and locked. Nothing starts until you confirm it.

### During Development
Every time you complete a subsection of your task list, you are prompted:

```
Subsection [X.X.X] complete. Run code reviewer and test writer? Yes / No
```

You stay in control. Nothing runs without your approval.

### Agent Communication
Every agent owns a chapter file. They write only to their own file. The orchestrator reads all chapter files and maintains the master INDEX.md — the single source of truth for everything happening in the project.

### Grading System
Every problem found by any agent is graded 1-10:

| Grade | Meaning | Who Handles It |
|---|---|---|
| 1 — 2 | Trivial | Agent fixes autonomously |
| 3 — 5 | Low to medium | Agent fixes autonomously |
| 6 — 7 | Significant | Flagged to you |
| 8 — 9 | Serious | Flagged to you immediately |
| 10 | Critical | Flagged to you this second |

Agents assign preliminary grades. The orchestrator verifies and finalises every grade with full system context. The orchestrator's grade is always final.

### Failure Handling
No agent is ever silent. Every agent always submits a report — complete or incomplete. When an agent fails, the orchestrator investigates the root cause, documents it, and presents you with a path forward. If one clear solution exists, it presents that. If a genuine fork exists, it presents Option A and Option B. You decide.

### The Audit Trail
Every problem, every grade, every fix, every decision is documented. You are always the final verification layer. Every resolved issue generates a completion report that comes to you regardless of grade. You can interrogate the orchestrator at any time — "Why did you do this?" — and it must answer fully.

---

## The Learning Layer

The system learns from every mistake made across every project.

**How it works:**
1. A mistake occurs
2. Orchestrator identifies it as a lesson worth documenting
3. Orchestrator writes a suggestion to the per-project suggestion file
4. You review and approve or dismiss
5. If approved — orchestrator drafts the lesson wording, you refine it, you confirm
6. Orchestrator writes the final lesson to the relevant agent's learning file
7. That agent reads its learning file at the start of every future task

**The master suggestion document** lives on Google Drive. Every completed project's learnings are pushed there automatically after your approval. This is the institutional memory of the entire system.

**The Pattern Recognition Agent** reads the master document when you ask it to. It finds correlating patterns across projects and surfaces them with three components: pattern found, suggested fix, and estimated impact. It runs manually only — on your command.

---

## Folder Structure

### On Your Machine
```
~/.claude/
├── agents/                          ← drop all agent files here
│   ├── orchestrator.md
│   ├── code-reviewer.md
│   ├── test-writer.md
│   ├── architecture-reviewer.md
│   ├── compliance-reviewer.md
│   ├── doc-generator.md
│   ├── pattern-recognition.md
│   └── discovery-session.md
│
├── project-memory/                  ← created automatically per project
│   ├── INDEX.md
│   ├── task-list.md
│   ├── code-reviewer-report.md
│   ├── test-writer-report.md
│   ├── architecture-report.md
│   ├── compliance-report.md
│   ├── doc-generator-report.md
│   └── [project-name]-suggestions.md
│
└── agent-learnings/                 ← grows over time
    ├── code-reviewer-learnings.md
    ├── test-writer-learnings.md
    ├── architecture-learnings.md
    ├── compliance-learnings.md
    ├── doc-generator-learnings.md
    └── pattern-recognition-learnings.md
```

### On Google Drive
```
Google Drive/
└── master-suggestions.md            ← institutional memory across all projects
```

---

## Setup

### Step 1 — Install Claude Code
If you do not have Claude Code installed:
```bash
npm install -g @anthropic-ai/claude-code
```

### Step 2 — Create the folder structure
```bash
mkdir -p ~/.claude/agents
mkdir -p ~/.claude/project-memory
mkdir -p ~/.claude/agent-learnings
```

### Step 3 — Copy agent files
Copy all `.md` files from the `agents/` folder in this repository into `~/.claude/agents/`

```bash
cp agents/*.md ~/.claude/agents/
```

### Step 4 — Create the master suggestion document
Create a new Google Doc or Google Drive document named `master-suggestions.md`. This is where project learnings will be pushed after each project closes.

### Step 5 — Restart Claude Code
```bash
claude
```

Or run `/agents` inside Claude Code to load agents immediately.

### Step 6 — Start your first project
Type: **"new project"**

The discovery session will activate automatically.

---

## Core Design Principles

- **Silence is never allowed** — every agent always submits a report, complete or incomplete
- **You are always the final verification layer** — no fix is invisible, regardless of grade
- **Options only exist when a real fork exists** — never manufactured for appearances
- **The task list is the project contract** — nothing moves without it, nothing changes without your approval
- **The orchestrator is an analyst, not just a librarian** — it diagnoses, it does not just record
- **The index is an audit trail** — every action, grade, fix, and decision is documented and answerable
- **The system gets smarter over time** — but only as fast as you allow it to

---

## Documentation

Full architecture and design decisions are documented in the `docs/` folder:

- `docs/agent-system-plan.docx` — complete system architecture, all three improvements, full flow
- `docs/learning-layer-plan.docx` — the learning layer, pattern recognition system, folder structure

---

## What This Is Not

- Not a fully autonomous system — you approve every significant decision
- Not a guarantee of zero mistakes — the goal is fewer repeated mistakes
- Not plug and play for non-Claude Code environments — built specifically for Claude Code
- Not a black box — everything is documented, traceable, and answerable

---

## Built With

- Claude Code — multi-agent framework
- Claude Opus 4 — orchestrator and pattern recognition
- Claude Sonnet 4 — code reviewer, test writer, architecture reviewer, compliance reviewer
- Claude Haiku — doc generator
- Markdown + YAML frontmatter — agent configuration
- Google Drive — institutional memory

---

*This framework was designed and built through a structured discovery and planning process. Every design decision has a documented reason. Read the docs folder to understand why things work the way they do.*
