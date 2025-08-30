# Contributing

This project uses Conventional Commits and UPM-friendly practices for Unity.

## Commit Messages
- Format: `type(scope): subject`
- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `perf`, `build`, `ci`, `chore`, `revert`
- Scopes: `modules`, `manifest`, `docs`, `navigation`, `popup`, `tutorial`
- Subject: imperative, <= 50 chars, no period
- Body: explain Why first, then What (bullets if helpful)
- Footer: `BREAKING CHANGE:` or refs as needed

Examples
- `chore(modules): scaffold UPM packages (navigation/popup/tutorial)`
- `build(manifest): link local UPM packages via file:`
- `docs: add root Quickstart`

## Branches
- `feature/<scope>-<desc>`
- `fix/<scope>-<desc>`
- `chore/<scope>-<desc>`

## Unity Specific
- Keep `.meta` files in sync and committed.
- Do not commit generated folders: `Library/`, `Temp/`, `Build*`, `.vs/`, etc.
- Place reusable code in UPM packages (outside `Assets/`) and reference via `Packages/manifest.json`.

