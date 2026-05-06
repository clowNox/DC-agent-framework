# Folder Structure Guide

This document explains what every folder and file in this system does and where it lives on your machine.

---

## Repository Structure (This Repo)

```
claude-agent-framework/
├── README.md                        ← start here
├── agents/                          ← all 8 agent files
│   ├── orchestrator.md
│   ├── discovery-session.md
│   ├── code-reviewer.md
│   ├── test-writer.md
│   ├── architecture-reviewer.md
│   ├── compliance-reviewer.md
│   ├── doc-generator.md
│   └── pattern-recognition.md
├── docs/                            ← full architecture documentation
│   ├── agent-system-plan.docx
│   └── learning-layer-plan.docx
└── setup/
    └── folder-structure.md          ← this file
```

---

## Your Machine Structure (After Setup)

```
~/.claude/
├── agents/                          ← copy all agent .md files here
│   ├── orchestrator.md
│   ├── discovery-session.md
│   ├── code-reviewer.md
│   ├── test-writer.md
│   ├── architecture-reviewer.md
│   ├── compliance-reviewer.md
│   ├── doc-generator.md
│   └── pattern-recognition.md
│
├── project-memory/                  ← created per project at runtime
│   ├── INDEX.md                     ← orchestrator master ledger
│   ├── task-list.md                 ← locked project contract
│   ├── code-reviewer-report.md      ← code reviewer chapter file
│   ├── test-writer-report.md        ← test writer chapter file
│   ├── architecture-report.md       ← architecture reviewer chapter file
│   ├── compliance-report.md         ← compliance reviewer chapter file
│   ├── doc-generator-report.md      ← doc generator chapter file
│   └── [project-name]-suggestions.md ← per project learning suggestions
│
└── agent-learnings/                 ← grows across projects over time
    ├── code-reviewer-learnings.md
    ├── test-writer-learnings.md
    ├── architecture-learnings.md
    ├── compliance-learnings.md
    ├── doc-generator-learnings.md
    └── pattern-recognition-learnings.md
```

---

## Google Drive

```
Google Drive/
└── master-suggestions.md            ← institutional memory, all projects
```

Create this file manually before your first project closes.
The orchestrator will push to it automatically after each project, post your approval.

---

## Setup Commands

```bash
# Create folder structure
mkdir -p ~/.claude/agents
mkdir -p ~/.claude/project-memory
mkdir -p ~/.claude/agent-learnings

# Copy agents from this repo
cp agents/*.md ~/.claude/agents/

# Verify
ls ~/.claude/agents/
```
