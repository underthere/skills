# Working on this repo

This is a personal agent-skills repo, shipped as a Claude Code plugin.

## Layout

- Each skill lives in `skills/<skill-name>/` with a `SKILL.md` at its root. Supporting docs sit next to it and are linked from `SKILL.md` so they load only when needed.
- Each skill also carries `agents/openai.yaml` with interface metadata (`display_name`, `short_description`) for Codex and other non-Claude harnesses. Claude Code ignores it; keep it in sync with the frontmatter.
- `.claude-plugin/plugin.json` lists the published skills. Adding a skill directory is not enough — its path must also be added to the `skills` array there.

## Writing skills

- The frontmatter `description` is what triggers model invocation. It must say what the skill does AND when to use it, in one or two sentences.
- Keep `SKILL.md` short and imperative. Move reference material (tables, formats, long examples) into sibling `.md` files and link them.
- One skill = one job. If a skill grows a second job, split it.

## Checks

- `bash scripts/list-skills.sh` lists every skill; every listed skill should appear in `plugin.json`.
