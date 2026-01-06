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

**These are workflows you do dozens of times per day:**

| Command | What It Does |
|---------|--------------|
| `/commit-push-pr` | Commit changes, push, and create a PR |
| `/test-and-commit` | Run tests, then commit if passing |
| `/validate` | Run linting, type checks, formatting |

> "I use slash commands for every 'inner loop' workflow that I end up doing many times a day. This saves me from repeated prompting."
> — Boris Cherny, creator of Claude Code

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

**Why this matters:**
- Provides Claude with real-time information
- Avoids back-and-forth with the model
- Makes commands run faster

---

# Subagents: What They Are

**Pre-configured AI personalities with specific expertise**

- Operate with separate context windows
- Prevent "knowledge pollution" in main conversation
- Control their own tool access
- Defined in `.claude/agents/`

**Think of them as specialized team members:**
- Each has a focused domain
- Called in when their expertise is needed
- Work independently then report back

---

# Subagents: Use Cases

**Examples from the Claude Code team:**

| Agent | Purpose |
|-------|---------|
| `code-simplifier` | Simplifies code after Claude finishes working |
| `verify-app` | Has detailed instructions for testing end-to-end |

> "Similar to slash commands, I think of subagents as automating the most common workflows for most PRs."
> — Boris Cherny

**Other ideas:**
- `security-reviewer` - Check for vulnerabilities
- `docs-writer` - Generate documentation
- `test-generator` - Create comprehensive tests

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

# Key Takeaway: The Verification Loop

> "Probably the most important thing to get great results out of Claude Code — give Claude a way to verify its work."

**Verification can 2-3x the quality of results**

Both slash commands and subagents enable this:

```
┌──────────┐    ┌──────────┐    ┌──────────┐
│  Write   │───▶│  Verify  │───▶│  Refine  │
│  Code    │    │  Output  │    │  Result  │
└──────────┘    └──────────┘    └──────────┘
      ▲                               │
      └───────────────────────────────┘
```

---

# Getting Started

**1. Create the commands directory:**
```bash
mkdir -p .claude/commands
```

**2. Start with your most repeated prompt**
- What do you type to Claude multiple times a day?
- Turn that into a slash command

**3. Iterate and check into git**
- Share with your team
- Update when Claude does something wrong

**4. Graduate to subagents**
- When you need specialized expertise
- When context separation helps

---

# Resources

**Documentation:**
- [Claude Code Docs](https://docs.anthropic.com/en/docs/claude-code)

**Source for this presentation:**
- [Boris Cherny's Twitter Thread](https://x.com/bcherny/status/2007179832300581177)
- [DEV Community Breakdown](https://dev.to/sivarampg/how-the-creator-of-claude-code-uses-claude-code-a-complete-breakdown-4f07)

**Start automating your inner loop today.**
