# WienerMatch

A demo React app for showcasing Claude Code slash commands and agents.

## About the App

WienerMatch is a playful dachshund matchmaking landing page. The interactive feature is a **trait wishlist builder** where users can:
- Add traits they want in their ideal doxie
- Mark traits as "Must-Have" (unchecked) or "Nice-to-Have" (checked)
- Filter the list by trait priority
- Delete traits

## Tech Stack

- **React 19** with hooks-based state management
- **TypeScript** in strict mode
- **Vite** for dev server and builds
- **Single component** architecture (App.tsx, ~380 lines)

## NPM Scripts

| Script | Purpose |
|--------|---------|
| `npm run dev` | Start dev server (localhost:5173) |
| `npm run build` | TypeScript compile + Vite build |
| `npm run lint` | ESLint checks |
| `npm run knip` | Unused code detection |

## Code Patterns

- All state managed with `useState` hooks
- `Todo` interface for wishlist items: `{ id, text, completed }`
- Filter state: `'all' | 'active' | 'completed'`
- Derived state for `filteredTodos` and `stats`

## Slash Commands

Located in `.claude/commands/`:
- `/validate` — Run lint, knip, and build
- `/commit` — Stage and commit with good message
- `/pr` — Push branch and create PR

## Agents

Located in `.claude/agents/`:
- `verify-app` — End-to-end testing
- `code-simplifier` — Post-implementation cleanup
- `component-reviewer` — React best practices audit
