# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

The source of my public "Leaders README" - a personal document about how I lead and how to work with me. Everything here is prose, not code: there is nothing to build or test. Markdown is linted with markdownlint-cli2 (rules in .markdownlint.jsonc; a PostToolUse hook lints every edited .md file except NOTES.md and feeds findings back for fixing).

- `README.md` - the document. The only publishable artifact.
- `NOTES.md` - working scratch. Raw material and reminders, not settled positions; never lift its contents verbatim into README.md.
- `AGENTS.md` - a symlink to this file; edit CLAUDE.md only.

## Working mode

Andru dictates; the session drafts into README.md and refines to his direction. Do not draft empty sections unprompted. Two repo skills support the work: `/council` stress-tests a section, decision, or draft passage against independent external models; `/publish-check` is the pre-publication gate - run it before any push that touches README.md.

## Voice and writing rules

- First person throughout; addressing the reader as "you" is correct.
- Sentence case for headings.
- Answer first: open each section with the position, then the reasoning.
- Facts over intensifiers; no promotional language, no filler.
- Prose for reasoning; lists only for enumerable facts.
- Keep the table of contents in sync with the sections, and heading levels consistent (one `#` title, `##` for sections).
- Mark unfinished sections with a `<!-- TODO: ... -->` comment. A bare or empty heading reads as a truncated file; the marker says stub, not cut-off.
- Never hard-wrap prose. One line per paragraph or bullet; let the editor soft-wrap. Mid-sentence line breaks read as cut-off lines (MD013 is disabled for this reason).

## Red line: third-party content

This document was researched against other leaders' public readmes. That material is copyrighted third-party work and lives outside this repo. Never copy it in, quote it at length, or commit files derived from it. The .gitignore and a local pre-commit hook block common research-file patterns (`sources/`, `council-*.md`, `*.pdf`, `*.html`, `*-raw.*`), but they are backstops, not the rule.

## Git

- Never commit or push to main. Branch first (`docs/<name>` for document work), then PR. Conventional Commits, e.g. `docs(readme): draft feedback section`.
- `origin` is github.com/codeninja55/leaders-readme (public).
- main is live: GitHub Pages serves the repo at <https://codeninja55.github.io/leaders-readme/> with README.md as the index (NOTES.md, CLAUDE.md, LICENSE excluded via _config.yml). Merging to main publishes - run publish-check first.
