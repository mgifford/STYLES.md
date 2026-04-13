---
title: Tech-minimal example — STYLES.md
---

# STYLES.md — Axiom CLI

> This is a worked example of STYLES.md for an open-source command-line tool.
> It shows what a complete, filled-in style file looks like for a speed-focused,
> documentation-heavy developer project.

---

## Scope

| Surface | Files | Applies? |
| :--- | :--- | :--- |
| **Repository documentation** | README, AGENTS.md, CONTRIBUTING.md, `docs/*.md` | ✅ |
| **Published docs site** | `docs/index.md`, `_layouts/`, `assets/` | ✅ |

---

## 1. Core philosophy

1. **Precision first.** Every word must earn its place. Remove anything a developer would skip.
2. **Consistency is the default.** Match the pattern already in the repo before introducing a new one.
3. **Docs are code.** Apply the same review bar to documentation as to source.

---

## 2. Voice and tone

### Target reading level

- Assume the reader is a software developer familiar with CLI tooling.
- Avoid jargon from adjacent domains (legal, marketing, HR).
- Keep sentences under 20 words.

### Plain language rules

| Avoid | Use instead |
| :--- | :--- |
| Leverage | Use |
| Utilize | Use |
| Going forward | From now on |
| It is worth noting that | Note: |
| Best-in-class | [Specific measurable claim] |

### Grammar defaults

- **Voice:** Active. "The flag sets the output format" — not "The output format is set by the flag."
- **Headings:** Sentence case.
- **Oxford comma:** Yes.
- **Spelling:** American English.
- **Code references:** Always wrap in backticks: `--output`, `axiom run`, `config.yaml`.
- **Commands:** Show exact input and expected output in fenced code blocks with language tag:

  ````markdown
  ```bash
  axiom run --output json > results.json
  ```
  ````

---

## 3. Design tokens (docs site)

| Token | Light value | Dark value | Notes |
| :--- | :--- | :--- | :--- |
| `--bg` | `#ffffff` | `#0d1117` | GitHub-adjacent dark |
| `--text` | `#1f2328` | `#e6edf3` | 4.5:1 verified |
| `--code` | `#f6f8fa` | `#161b22` | Code blocks |
| `--button` | `#1f883d` | `#2ea043` | GitHub green |
| `--font-stack` | `-apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif` | — | `rem` only |
| `--mono` | `ui-monospace, "Cascadia Code", "Fira Code", monospace` | — | Code blocks |

### 3.1 Code formatting and naming

**Formatting defaults**

| Setting | Value |
| :--- | :--- |
| Indentation | 2 spaces |
| Trailing whitespace | Trim on save |
| Final newline | Required |

**Quote style by file type**

| File type | Quote style |
| :--- | :--- |
| `.html` | `"double"` |
| `.css` | `'single'` |
| `.js` | `'single'` |
| `.json` | `"double"` |
| `.yml` | None in general; `'single'` when forcing a string |

**Naming cases**

| What you're naming | Case |
| :--- | :--- |
| HTML attributes and values | `dash-case` |
| CSS custom property | `--dash-case` |
| CSS class | `dash-case` with category prefix (see below) |
| JavaScript variable / function | `camelCase` |
| JavaScript class | `PascalCase` |
| File names | `dash-case.extension` |

**CSS class prefixes**

| Category | Prefix | Rule |
| :--- | :--- | :--- |
| Component | `c-` | Encapsulated UI component |
| Utility | `u-` | Single-purpose helper (alignment, spacing, visibility) |
| JavaScript hook | `js-` | Selector for JavaScript behavior only — never styled |

**CSS property order**

Group properties within each rule in this order: display → position → size → space → typography → border → background → transitions and animation. This makes rules easier to scan and diff without requiring memorization of the full property list.

---

## 4. Accessibility constraints

- Heading levels sequential: `h1` → `h2` → `h3`. No skipping.
- All links have descriptive text. Never "click here" or "read more."
- Code examples must have explanatory prose — never let code stand alone without context.
- Minimum contrast: 4.5:1 body text, 3:1 large text and UI controls.
- See [ACCESSIBILITY.md](../../ACCESSIBILITY.md) for full commitment.

---

## 5. AI agent rules

- Read `AGENTS.md` before making any change.
- Prefer the simplest solution — do not add abstraction layers without an explicit reason.
- Never add boilerplate, placeholder comments, or TODO stubs unless asked.
- If you change behavior, update the relevant documentation in the same commit.
- Never override accessibility or sustainability constraints.
- Keep all changes scoped to the minimum needed.

---

## 6. References

- [AGENTS.md](../../AGENTS.md)
- [ACCESSIBILITY.md](../../ACCESSIBILITY.md)
- [SUSTAINABILITY.md](../../SUSTAINABILITY.md)
- [Plain Language Guidelines — Digital.gov](https://www.plainlanguage.gov/guidelines/)
- [WCAG 2.2](https://www.w3.org/TR/WCAG22/)
- [frontend-conventions skill — mikemai2awesome/agent-skills](https://github.com/mikemai2awesome/agent-skills/blob/main/skills/frontend-conventions/SKILL.md)
