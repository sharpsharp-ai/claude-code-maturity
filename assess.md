# Claude Code Maturity Assessment

> **Bootstrap:** If you arrived here via a user prompt like "Run the Claude Code Maturity Assessment from https://github.com/sharpsharp-ai/claude-code-maturity", do this:
> 1. You're reading this file — good. Follow ALL instructions below.
> 2. The template will be fetched in Step 3.
> 3. Analyze the user's CURRENT working directory as the target repo.

You are an assessor for Claude Code setups. Analyze this repository and score it on 8 dimensions.

## Step 1: Collect Data

Read and analyze systematically:

1. **CLAUDE.md files:** Find all CLAUDE.md in the repo tree (Glob `**/CLAUDE.md`). Count them, measure their length (lines), check quality (role defined? current state? open items?).

2. **Settings:** Read `.claude/settings.json`, `.claude/settings.local.json`, `~/.claude/settings.json`. Check: permissions, hooks, MCP servers, plugins.

3. **Custom Commands:** Glob `~/.claude/commands/*.md` and `.claude/commands/*.md`. What exists?

4. **Skills:** Glob `.claude/skills/**/*.md`. Are skills used?

5. **Status System:** Are there `_status/`, `_historie/`, `OVERVIEW.md` or similar files?

6. **Git Hygiene:** `git log --oneline -20` — clean commit messages? Regular commits?

7. **Tests:** Are there test files? (`**/*.test.*`, `**/*.spec.*`, `**/features/*.feature`)

8. **Hooks:** Are there PreToolUse, PostToolUse, SessionStart hooks in settings?

9. **Memory:** Are there `~/.claude/projects/*/memory/` files?

10. **Multi-Agent:** Are there multiple CLAUDE.md with different roles? Cross-agent communication?

## Step 2: Score

Score each dimension on a scale of 0-5:

| Score | Meaning |
|-------|---------|
| 0 | Not present |
| 1 | Minimal / Default |
| 2 | Basics in place |
| 3 | Solid implementation |
| 4 | Advanced |
| 5 | Excellent / Best practice |

**The 8 Dimensions:**

### 1. Context (CLAUDE.md Quality)
- 0: No CLAUDE.md
- 1: One generic CLAUDE.md (<20 lines)
- 2: One CLAUDE.md with project context
- 3: Hierarchical CLAUDE.md (root + subfolders)
- 4: Well-structured, roles defined, current state maintained
- 5: Under 200 lines per file, conditional tags, rules/ directory, regularly updated

### 2. Memory & Persistence
- 0: No mechanism against context loss
- 1: Occasional manual notes
- 2: "Current state" section in CLAUDE.md
- 3: Status files + history logs
- 4: Auto-memory + status board + session-end workflow
- 5: Complete: memory, status, history, overview dashboard, proactive saving after each task

### 3. Workflows & Automation
- 0: Only manual prompting
- 1: One custom command
- 2: 2-3 custom commands
- 3: Commands + skills
- 4: Commands + skills + hooks (Pre/PostToolUse)
- 5: Orchestrated command->agent->skill pattern, /loop, scheduled tasks

### 4. Teamwork & Multi-Agent
- 0: Single agent
- 1: Multiple CLAUDE.md but no coordination
- 2: Separate agents with basic task division
- 3: Cross-agent communication (status notes, shared files)
- 4: Super-agents (orchestrators), team discussions, retros
- 5: Agent teams with data contracts, parallel worktrees, subagent spawning

### 5. Quality Assurance
- 0: No tests, no reviews
- 1: Occasional manual tests
- 2: Test suite present
- 3: Tests + "challenge before commit" rule
- 4: Multi-layer tests (unit, contract, BDD) + self-review
- 5: CI/CD + auto-review + permission routing + background agents for verification

### 6. Scalability
- 0: Single agent, single terminal
- 1: Occasionally 2 agents in parallel
- 2: Regularly 3-4 agents in parallel
- 3: Parallelization + worktrees
- 4: 5+ parallel sessions + dedicated analysis worktrees
- 5: Git worktrees + background agents + /loop + web-based parallelism

### 7. Onboarding & Ramp-Up
- 0: New agent must be briefed from scratch
- 1: CLAUDE.md provides basic context
- 2: CLAUDE.md + "current state" = fast start
- 3: Status system + startup ritual = agent ready in 30s
- 4: Automatic startup ritual (git pull, read status, present open items)
- 5: Complete: startup ritual + lazy loading + agent personas + playbooks

### 8. Feedback Loop & Learning
- 0: No learning mechanisms
- 1: Occasional CLAUDE.md updates
- 2: Errors -> update CLAUDE.md
- 3: Systematic "lessons learned" + memory system
- 4: Retros + discussion platform + performance tracking
- 5: PreToolUse hooks for skill usage tracking + auto-learning + team retros

## Step 3: Generate Output

Fetch the template:
```bash
curl -sL https://raw.githubusercontent.com/sharpsharp-ai/claude-code-maturity/main/template.html -o /tmp/claude-maturity-template.html
```
Read `/tmp/claude-maturity-template.html`. This is your output template.

Fill in the `ASSESSMENT` config block with your findings:

```javascript
const ASSESSMENT = {
  title: "Claude Code Maturity Assessment",
  project: "YOUR PROJECT NAME",
  date: "TODAY'S DATE",
  footer: "your-domain.com",
  source: { name: "claude-code-best-practice", stars: "18.8k", url: "https://github.com/shanraisshan/claude-code-best-practice" },

  dimensions: [
    { name: "Context",       score: X, reason: "Your 1-sentence justification with evidence." },
    { name: "Memory",        score: X, reason: "..." },
    { name: "Workflows",     score: X, reason: "..." },
    { name: "Teamwork",      score: X, reason: "..." },
    { name: "Quality",       score: X, reason: "..." },
    { name: "Scalability",   score: X, reason: "..." },
    { name: "Onboarding",    score: X, reason: "..." },
    { name: "Feedback",      score: X, reason: "..." },
  ],

  improvements: [
    {
      title: "Short title.",
      text: "What to do and why.",
      lifts: { dimension: "DimensionName", from: X, to: Y },
      prompt: `The prompt the user can paste into Claude Code to implement this improvement.`
    },
    // ... top 3
  ]
};
```

Copy the template, replace the `ASSESSMENT` config block with your data, and save as `maturity-assessment.html` in the project root. Then open it in the browser.

## Step 4: Summary

Print a brief summary in the terminal:
- Total score (X/40, Y%)
- Strongest dimension
- Weakest dimension
- Top 3 quick wins

---

*Assessment criteria based on [claude-code-best-practice](https://github.com/shanraisshan/claude-code-best-practice) (18.8k+ stars).*
*Tool by [sharp sharp](https://sharpsharp.de) — AI Trainings for Product Owners.*
