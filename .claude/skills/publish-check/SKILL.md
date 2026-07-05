---
name: publish-check
description: Pre-publication gate for README.md. Run before pushing or publishing changes to the public Leaders README. Checks structure, links, voice, and copyright exposure. Use when Andru says "publish check", "is this ready to publish", or before any push of README.md changes.
---

# Publish check

Run every check below against README.md and report pass/fail per check with exact locations. Report findings first; do not fix anything without confirmation.

## Checks

1. **Structure**: one `#` title, `##` for all sections, sentence-case headings. Table of contents lists every section, and every reference-style link has a matching definition in the file.

2. **Links**: every external URL responds (`curl -sIL -o /dev/null -w "%{http_code}" <url>`). List dead or redirecting links with their status codes.

3. **Voice**: first person throughout, answer-first sections, no promotional language or intensifiers. Run the humanizer skill over changed prose to catch AI-slop patterns before publication.

4. **Copyright**: no long verbatim passages from other leaders' readmes, and every borrowed idea is attributed. Confirm `git status` shows no staged or untracked files matching research-corpus patterns (`sources/`, `council-*.md`, `*.pdf`, `*.html`, `*-raw.*`).

5. **Consistency**: README.md does not contradict itself section to section (cadences, availability, and commitments all agree).

## Output

A short report: each check, pass or fail, and for failures the line or link concerned. End with a single publish/hold recommendation.
