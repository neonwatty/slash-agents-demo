# Demo Walkthrough

A guide for trying out the slash commands and agents in this project.

## Setup

```bash
npm install
npm run dev
```

Open http://localhost:5173 to see WienerMatch.

## Try the Slash Commands

### /validate
Runs lint, unused code detection, and build checks.

```
/validate
```

**What you'll see:** Three checks run in sequence, each reporting pass/fail.

### /commit
Shows current changes and creates a commit with a clear message.

```
/commit
```

**What you'll see:** Git status, diff stats, then a commit with an auto-generated message.

### /pr
Pushes the branch and creates a pull request.

```
/pr
```

**What you'll see:** Branch info, commits to push, then a PR link.

## Try the Agents

Agents can be invoked conversationally. Try these prompts:

### verify-app
> "Use the verify-app agent to test the application"

**What you'll see:** End-to-end test of the wishlist feature — add, toggle, delete, filter.

### component-reviewer
> "Run the component-reviewer agent on App.tsx"

**What you'll see:** Accessibility issues, performance suggestions, best practice recommendations.

### code-simplifier
> "Have the code-simplifier agent review the codebase"

**What you'll see:** Opportunities to reduce duplication, extract components, improve clarity.

## Key Concepts

| Concept | Location | Purpose |
|---------|----------|---------|
| Slash commands | `.claude/commands/` | Automate frequent workflows |
| Agents | `.claude/agents/` | Specialized expertise |
| Project context | `.claude/CLAUDE.md` | Background for all agents |

## Three Ways to Invoke Slash Commands

1. **Direct:** Type `/validate` in Claude Code
2. **Conversational:** "Can you validate the code?"
3. **Autonomous:** Claude runs it as part of a larger task
