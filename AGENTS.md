# Repository Guidelines

## Project Structure & Module Organization
Light Theme with Bars is a VS Code color theme; the core definitions live in `themes/light-theme.json`, formatted with two-space indentation. `samples/` hosts multi-language snippets used for screenshots and manual verification. `images/` holds icon and preview assets referenced by `README.md`. Release metadata and npm scripts sit in `package.json`, while version history stays in `CHANGELOG.md`. Keep new assets under the existing directories so marketplace packaging keeps working.

## Build, Test, and Development Commands
Run `npm install` once to pull the VSCE tooling captured in `package-lock.json`. Use `npm run packaging` to produce a `.vsix` bundle in the repository root, and `npm run publish` when shipping to the Marketplace; both commands delegate to `npx vsce`. For local previews, open this folder in VS Code and press `F5` to launch an Extension Development Host with the theme applied. You can also run `code --extensionDevelopmentPath=$(pwd)` from a second VS Code instance to inspect the theme in-place.

## Coding Style & Naming Conventions
Maintain two-space indentation in JSON and avoid trailing commas (VS Code's default formatting works). Scope names inside `tokenColors` stay lowercase and must match TextMate grammar identifiers; group related scopes together and reuse existing prefix patterns (for example, `support.variable`). Asset filenames use lowercase-with-hyphens (see `images/icon.png`), and new screenshots should land under `images/` with descriptive names.

## Testing Guidelines
There is no automated test suite yet; rely on manual verification. Before publishing, load the theme in the Extension Development Host and sweep through the files in `samples/` to catch regressions in language tokens, editor selections, and UI chrome. Capture any required screenshot updates with VS Code's command palette (`Developer: Reload Window`) after styling tweaks. Summarize notable visual checks in the pull request description so reviewers know what was exercised.

## Commit & Pull Request Guidelines
Commits in this repo are concise and task-oriented (for example, “색상 구성 업데이트”); continue using short, imperative summaries that name the scope or asset you touched. For pull requests, provide 1) a description of theme changes and affected scopes, 2) screenshots or GIFs when colors shift, and 3) references to related issues. Ensure `CHANGELOG.md` and the `version` in `package.json` advance together before tagging a release so published `.vsix` files align with the log.

## Release Notes
Package drops follow semantic version bumps (see existing `.vsix` archives). When preparing a release, update `CHANGELOG.md` with highlights (English and Korean welcome), rebuild the `.vsix`, and keep the artifact in the repository root for traceability.
