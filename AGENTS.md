# Repository Guidelines

## Project Structure & Module Organization
This repository is documentation-first and currently contains prompt/config assets plus compiled Markdown outputs.

- `agent-prompt-v1.md`: primary conversion prompt used by the agent.
- `agent-prompt-v2r.md`: system-level conversion rules and output schema.
- `output/`: generated component docs (for example `标题栏-Navigation-Bar.md`).

Keep new source instructions in the repository root as `.md` files. Keep generated deliverables in `output/`.

## Build, Test, and Development Commands
There is no build pipeline or automated test runner in this folder yet. Use lightweight checks before submitting changes:

- `rg --files`  
  List repository files quickly.
- `Get-Content -Raw -Encoding UTF8 .\agent-prompt.md`  
  Verify UTF-8 readability and avoid mojibake.
- `Get-ChildItem .\output`  
  Confirm generated files are present.

If automation is added later, document new commands here and in PR descriptions.

## Coding Style & Naming Conventions
- Use UTF-8 encoded Markdown with clear heading hierarchy (`#` to `####`).
- Prefer concise, structured sections over long prose.
- Keep terminology consistent with source specs (component names, token names, states, units).
- Output file naming pattern: `<组件名>-<EnglishName>.md` (example: `标题栏-Navigation-Bar.md`).
- Use lowercase kebab-case for any future scripts/config files (example: `pdf-parse.ps1`).

## Testing Guidelines
No formal framework is configured. Validate by review:

1. Check Markdown renders correctly.
2. Verify tables/lists are complete and not truncated.
3. Confirm uncertain OCR or image-derived details are captured under a `待确认问题` section.

For future automated tests, place them in a top-level `tests/` directory and name files `test-*.md` or `*.spec.*` by toolchain.

## Commit & Pull Request Guidelines
No local Git history is available in this directory, so no existing commit convention can be inferred. Recommended standard:

- Use Conventional Commits (for example `docs: add navigation bar conversion guide`).
- Keep commits focused on one logical change.
- PRs should include: purpose, changed files, sample output paths (for example `output/...`), and screenshots only when visual diff matters.
