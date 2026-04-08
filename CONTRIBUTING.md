# Contributing

Thanks for contributing.

## Commit convention (Conventional Commits)

This repository uses Conventional Commits so release notes and versioning can be automated with release-please.

Format:

```text
<type>(optional-scope): <short summary>
```

Examples:

- `feat(display): add compact euro icon spacing`
- `fix(ci): adjust yamllint rules for ESPHome`
- `docs(readme): clarify Home Assistant sensor mapping`
- `chore(repo): add editor and git defaults`

Supported types:

- `feat` (new feature)
- `fix` (bug fix)
- `docs` (documentation)
- `refactor` (code restructure without behavior change)
- `perf` (performance improvement)
- `test` (tests)
- `build` (build tooling/dependencies)
- `ci` (CI/CD workflow)
- `chore` (maintenance)
- `style` (format/style-only)
- `revert` (revert commit)

## Pull requests

- Keep PRs focused and small when possible.
- Make sure GitHub Actions checks pass.
- Use clear PR titles and descriptions.
