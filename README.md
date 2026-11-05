# Skills

[![skills.sh](https://skills.sh/b/adamjosefus/skills)](https://skills.sh/adamjosefus/skills)

Agent skills, commands and rules I use in every project.

Agents are fast, but they don't know the small rules that decide whether a result looks right. They write `"quotes"` in Czech text, leave a one-letter preposition hanging at the end of a line, and let light text in dark mode look heavier than the same text in light mode.

These skills write those rules down, so the agent gets them right the first time and I don't have to repeat them in every prompt.

## Install

```bash
npx skills@latest add adamjosefus/skills
```

Install a single skill:

```bash
npx skills@latest add adamjosefus/skills --skill typography-czech
```

List what's available without installing:

```bash
npx skills@latest add adamjosefus/skills --list
```

## Why use it?

Small mistakes compound. Straight quotes instead of „české“, a hyphen where a dash belongs, `30%` where it should be `30 %`, a text reset that breaks your buttons because hyphenation was applied globally. Each one is minor; together they make the result feel careless.

Each skill lists the mistakes agents typically make in its area and how to fix them.

## Reference

- **[typography-css](./skills/typography-css/SKILL.md)**: How text should render: wrapping, hyphenation, vertical trim, underlines, numerals, variable fonts and optical weight in dark mode, scoped so it never breaks your UI.
- **[typography-css-reset](./skills/typography-css-reset/SKILL.md)**: Run `/typography-css-reset` to add a modern CSS text reset to your project, adapted to its fonts, tokens and dark-mode switch, instead of pasting a generic one.
- **[typography-czech](./skills/typography-czech/SKILL.md)**: Writes Czech text by Czech typographic rules (ČSN 01 6910), and checks and fixes existing texts: quotes, dashes, non-breaking spaces, numbers, units and dates.
