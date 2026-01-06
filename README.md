# Slash Commands Demo

A demo project illustrating Claude Code slash commands and agents for automating development workflows.

## What's Included

### Demo App
WienerMatch - a React + TypeScript + Vite SPA used as a working codebase for demonstrating slash commands.

### Slash Commands
Located in `.claude/commands/`:

| Command | Purpose |
|---------|---------|
| `/commit` | Stage and commit changes with a good message |
| `/pr` | Push branch and create a pull request |
| `/validate` | Run code quality checks before committing |

## Running Locally

```bash
npm install
npm run dev
```

Opens at http://localhost:5173/

## Learn More

See `presentation/presentation-outline.md` for a presentation on slash commands and agents.
