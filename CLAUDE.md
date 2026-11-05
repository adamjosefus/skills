# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

Adam's personal library of agent skills. The repo is a package installable with the [`skills` CLI](https://skills.sh):

```bash
npx skills@latest add adamjosefus/skills
```

That is the only distribution channel: no npm package, no Claude Code plugin manifest. There is no build, test or lint step: the content is Markdown.

## Consequences of installing via `npx skills`

- **Every skill must be self-contained.** Users can install a single skill (`--skill <name>`), and each one is copied or linked as its own folder. Never reference files outside the skill's directory, and never rely on another skill being installed. Mentioning a sibling skill by name in a description ("for X use `other-skill`") is fine.
- **Skills install into many agents** (Claude Code, Cursor, Codex, …), not only Claude Code. Claude-specific frontmatter such as `disable-model-invocation` may be ignored elsewhere, so a command's instructions must still make sense if another agent triggers it on its own.
- **Names share one folder with skills from other repos.** Use specific names (`typography-css`, `typography-czech`), not generic ones (`typography`, `reset`).
- The CLI discovers skills by their `SKILL.md` files. That's why the template is named `SKILL.template.md`: so it doesn't get installed as a skill.

## Layout

- `skills/<name>/SKILL.md`: one directory per skill. The CLI discovers these. Supporting files (e.g. `RECIPES.md`, `CATALOG.md`, `STANDARDS.md`) sit next to `SKILL.md` and are linked from it, so they load only when needed.
- `templates/SKILL.template.md`: the starting point for a new skill. It is deliberately not named `SKILL.md`, so the CLI doesn't install it.
- `README.md`: install instructions and the **Reference** list. Every skill must have an entry there, in the right section.

## Three kinds, one format

The `skills` CLI only installs skills, so commands and rules are skills too. The difference is in the frontmatter and in how the description is written:

| Kind    | Frontmatter                                  | Description says                                         |
|---------|----------------------------------------------|----------------------------------------------------------|
| Skill   | `name`, `description`                        | what it does + "Use when …" triggers                     |
| Command | adds `disable-model-invocation: true`        | what running `/<name>` does; user-invoked only           |
| Rule    | `name`, `description`                        | broad triggers ("Use whenever writing/editing …") so it loads every time the area is touched |

## Conventions

- `name` in the frontmatter equals the directory name (kebab-case).
- The description decides triggering. Name neighbouring skills ("for X use `other-skill`") so skills don't compete.
- Keep `SKILL.md` focused: hard rules and steps first, long catalogues in sibling files.
- When adding, renaming or removing a skill, update the README Reference list in the same change.

## Commits

Use [Conventional Commits](https://www.conventionalcommits.org/): `<type>(<scope>): <summary>`. The scope is the skill name. Leave it out for repo-wide changes.

- `feat`: new skill, or new rules/behaviour in an existing one: `feat(typography-czech): add rules for ellipsis`
- `fix`: wrong or contradictory rule, broken example: `fix(typography-css-reset): guard :heading selector`
- `refactor`: restructure without changing behaviour (split into sibling files, reword)
- `docs`: README, CLAUDE.md, template
- `chore`: repo config (`.gitignore`, `.gitattributes`)

Renaming or removing a skill breaks existing installs: mark it with `!` (`feat(typography-css)!: rename from typography`) and say what replaces it in the body.

## Checking a skill installs

```bash
npx skills@latest add . --list
```
