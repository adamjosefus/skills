# Skills

My personal collection of agent skills: workflows, commands and rules I want in every project.

## Install

```bash
npx skills@latest add adamjosefus/skills
```

Install a single skill:

```bash
npx skills@latest add adamjosefus/skills --skill <name>
```

List what's available without installing:

```bash
npx skills@latest add adamjosefus/skills --list
```

## Reference

### Skills

Knowledge and workflows the agent loads on its own when the task matches.

- **[typography-czech](./skills/typography-czech/SKILL.md)**: Czech typographic rules (ČSN 01 6910). Writes Czech text correctly, and checks and fixes existing texts: quotes, dashes, non-breaking spaces, numbers, units and dates.

### Commands

Actions you run explicitly with `/<name>`. The agent never triggers them by itself.

- **[typography-css-reset](./skills/typography-css-reset/SKILL.md)**: Adds a modern CSS text reset to the project, adapted to its fonts, tokens, dark-mode switch and stylesheet setup.

### Rules

Conventions the agent follows whenever it works in the area they cover.

- **[typography-css](./skills/typography-css/SKILL.md)**: Wrapping, hyphenation, vertical trim, underlines, numerals, quotes, variable fonts and optical weight compensation in dark mode, scoped so they stay overridable.
