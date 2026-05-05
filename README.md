# mdd-tui

A terminal dashboard for [MDD (Manual-Driven Development)](https://github.com/TheDecipherist/claude-code-mastery-project-starter-kit) projects created by the starter kit.

Reads your `.mdd/` directory and renders a live, navigable TUI showing doc health, drift status, audit reports, and full markdown content — without leaving the terminal.

![MDD Dashboard](./mdd_dashboard.png)

---

## Install

```bash
npm install -g mdd-tui
```

## Usage

Run from any project directory that has a `.mdd/` folder:

```bash
mdd dashboard
```

---

## Navigation

| Key | Action |
|-----|--------|
| `↑` / `k` | Move up in left panel / scroll up in right panel |
| `↓` / `j` | Move down in left panel / scroll down in right panel |
| `→` / `l` / `Enter` | Focus right panel (or expand initiative) |
| `←` / `h` / `Esc` | Focus left panel |
| `i` | Jump to first initiative in the list |
| `Page Up` | Scroll right panel up one page |
| `Page Down` | Scroll right panel down one page |
| `Home` | Jump to top of right panel |
| `End` | Jump to bottom of right panel |
| `r` | Refresh workspace |
| `q` / `Ctrl+C` | Quit |

**Initiative expand/collapse** — pressing `Enter` or `→` on an initiative row toggles its waves open or closed. When expanded, each wave appears as an indented sub-row showing status icon and feature progress (e.g. `2/3`).

---

## What it shows

**Left panel** — scrollable list with three sections (shown in order):

1. **INITIATIVES** *(shown only if `.mdd/initiatives/` exists)* — collapsible tree of initiatives and their waves:
   - `▸ Initiative Title  active` — collapsed; press Enter to expand
   - `▾ Initiative Title  active` — expanded; child waves shown below with progress
   - Wave rows: `● Wave Title 1/3` (active), `✓ Wave Title 3/3` (complete), `○ Wave Title 0/2` (planned)

2. **FEATURE DOCS** — all feature docs with drift status icons:

   | Icon | Meaning |
   |------|---------|
   | `✓` | In sync with source files |
   | `!` | Drifted — commits since last sync |
   | `✗` | Broken — source files missing |
   | `?` | Untracked — no source files defined |

3. **AUDIT REPORTS** *(shown only if audits exist)*

4. **DEP GRAPH** — click to view the dependency graph

**Right panel** — full detail view for the selected item:
- **Initiative**: status, overview, open product questions (unchecked ones highlighted), wave list with progress
- **Wave**: demo state, feature table with status and dependencies, open research items, next-action hint
- **Feature doc**: status chips, source files, dependencies, known issues, drift commits, full markdown body
- **Audit report**: full markdown content

**Status bar** — live counts: DOCS · IN SYNC · DRIFTED · BROKEN · UNTRACKED · ISSUES · AUDITS · INITIATIVES · WAVES (active)

---

## What is MDD?

MDD (Manual-Driven Development) is a documentation-driven workflow for building features with AI coding assistants. The manual isn't just a starting point — it drives the entire development lifecycle. Every feature, change, and decision is anchored to a `.mdd/docs/*.md` file that defines architecture, API, data model, and business rules. That document stays authoritative from first design through final implementation: code must match the manual, not the other way around.

`mdd-tui` is the companion dashboard — run it alongside your editor to track doc health across the project.

---

## Requirements

- Node.js 18+
- A project with a `.mdd/` directory

---

## License

MIT
