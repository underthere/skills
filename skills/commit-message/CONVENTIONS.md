# Fallback convention: Conventional Commits

Used only when the repo's own history shows no clear style.

Format: `<type>(<scope>): <subject>`

| type | when |
| --- | --- |
| feat | new user-facing behavior |
| fix | bug fix |
| refactor | code change with no behavior change |
| perf | performance improvement |
| test | adding or fixing tests only |
| docs | documentation only |
| build | build system, dependencies |
| ci | CI configuration |
| chore | maintenance that fits nothing above |

- `scope` is optional; use the module or area name, not a file name.
- Subject in imperative mood, lowercase, no trailing period: `fix(auth): reject expired refresh tokens`.
- Breaking changes: add `!` after the type/scope and explain in the body.
