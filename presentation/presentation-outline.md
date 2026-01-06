# Automating Your Development Workflow with Claude Code
## Slash Commands & Agents

---

# The Problem

**Developers repeat the same workflows many times daily**

- Commit, test, create PR
- Run validations before pushing
- Simplify code after implementation
- Verify changes end-to-end

**Manual repetition creates friction and inconsistency**

> We need automation at two levels: simple tasks & complex workflows

---

# Two-Tier Automation Approach

```
┌─────────────────────────────────────────────────┐
│                                                 │
│   Slash Commands          Subagents             │
│   ─────────────          ─────────              │
│   Inner Loop             Outer Loop             │
│   Frequent, simple       Specialized, complex   │
│   /commit-push-pr        code-simplifier        │
│   /validate              verify-app             │
│                                                 │
└─────────────────────────────────────────────────┘
```

Both save you from repeated prompting and let Claude use these workflows too.

---

# Slash Commands: What They Are

**Custom commands that automate your most frequent workflows**

- Stored in `.claude/commands/`
- Invoked with `/command-name`
- Checked into git for team sharing
- Written in markdown with embedded instructions

```
.claude/
└── commands/
    ├── commit-push-pr.md
    ├── validate.md
    └── test-and-commit.md
```

---

# Slash Commands: Inner Loop Use Cases

**Workflows you do dozens of times per day:**

| Command | What It Does |
|---------|--------------|
| `/commit-push-pr` | Commit, push, and create a PR |
| `/test-and-commit` | Run tests, commit if passing |
| `/validate` | Lint, type check, format |

> "I use slash commands for every 'inner loop' workflow. This saves me from repeated prompting."
> — Boris Cherny

---

# Slash Commands: Power Features

**Inline bash with `!` prefix pre-computes context**

```markdown
# /commit-push-pr

Current git status:
!git status --short

Recent commits for style reference:
!git log --oneline -5

Create a commit, push to remote, and open a PR.
```

**Why this matters:** Real-time context, less back-and-forth, faster execution.

---

# Slash Commands: Three Ways to Invoke

| Method | Example |
|--------|---------|
| **Direct** | Type `/validate` |
| **Conversational** | "Can you validate the code?" |
| **Autonomous** | Claude runs it as part of a larger task |

**Key insight:** Slash commands are exposed as "skills" — enabling conversational and autonomous invocation.

> "Make this change and prepare it for PR"
> → Claude autonomously runs `/validate` → `/commit` → `/pr`

---

# Subagents: What They Are

**Specialized AI "team members" with focused expertise**

- Separate context windows (prevents knowledge pollution)
- Work independently, then report back
- Defined in `.claude/agents/`

---

# Subagents: Use Cases

**From Boris Cherny's setup:**

| Agent | Purpose |
|-------|---------|
| `code-simplifier` | Refactor for clarity |
| `verify-app` | End-to-end testing |
| `build-validator` | Compilation checks |
| `code-architect` | Design review |

> "I think of subagents as automating the most common workflows for most PRs."
> — Boris Cherny

**Other ideas:** `security-reviewer`, `docs-writer`, `test-generator`

---

# Demo: Our Agents in Action

**Three agents for WienerMatch:**

```
.claude/agents/
├── verify-app.md
├── code-simplifier.md
└── component-reviewer.md
```

| Agent | Output |
|-------|--------|
| `verify-app` | "All 8 tests passed: add, toggle, delete, filters..." |
| `component-reviewer` | "2 critical, 5 warnings: missing aria-label..." |
| `code-simplifier` | "Extract filter buttons to map, saves ~15 lines..." |

**How it works:** Agent reads `.md` file → follows instructions → reports back

---

# When to Use Which

| Use Slash Commands When... | Use Subagents When... |
|---------------------------|----------------------|
| Task is structured/repeatable | Domain expertise is needed |
| You do it multiple times daily | Complex verification required |
| Steps are well-defined | Separate context helps |
| Quick automation needed | Specialized tool access needed |

**Rule of thumb:**
- Slash commands = **what** to do (process)
- Subagents = **how** to think (expertise)

---

# Two Philosophies, Both Valid

| | Boris Cherny | Peter Steinberger |
|--|--------------|-------------------|
| **Style** | Specialized subagents | Parallel visible agents |
| **Why** | Context separation | Full visibility |
| **Coordination** | Agents report back | Watch all agents work |

**Both work.** Choose based on:
- Specialized roles vs. direct observation
- Context isolation vs. visibility
- Delegate vs. steer

> No single "correct" setup — customize to your workflow.

---

# Key Takeaway: The Verification Loop

> "Give Claude a way to verify its work." — Boris Cherny

**Verification can 2-3x result quality.**

```
┌──────────┐    ┌──────────┐    ┌──────────┐
│  Write   │───▶│  Verify  │───▶│  Refine  │
└──────────┘    └──────────┘    └──────────┘
      ▲                               │
      └───────────────────────────────┘
```

Both slash commands and agents enable this loop.

---

# Getting Started

```bash
mkdir -p .claude/commands .claude/agents
```

1. **Start with your most repeated prompt** → slash command
2. **Add specialized reviews** → agent instruction files
3. **Check into git** → share with team, iterate over time

---

# Resources

**Documentation:**
- [Claude Code Docs](https://docs.anthropic.com/en/docs/claude-code)

**Source for this presentation:**
- [Boris Cherny's Twitter Thread](https://x.com/bcherny/status/2007179832300581177)
- [How Boris Uses Claude Code (paddo.dev)](https://paddo.dev/blog/how-boris-uses-claude-code/)
- [Just Talk To It (Peter Steinberger)](https://steipete.me/posts/just-talk-to-it)

**Start automating your inner loop today.**
