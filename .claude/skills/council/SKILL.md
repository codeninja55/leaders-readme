---
name: council
description: Stress-test a Leaders README section, decision, or draft passage against independent external models (Codex and AGY/Gemini). Use when Andru says "run the council", "council this", "pressure-test this section", or wants a second opinion on a position or draft before adopting it.
---

# Council review

Run the same brief past two independent models and report where they converge, where they split, and the strongest challenge to the current position. Never average the answers into a consensus - disagreement is the useful output.

## Input

`$ARGUMENTS` names the target: a README.md section, a NOTES.md idea, a file path, or a free-text question. If ambiguous, confirm the target before running.

## Procedure

1. **Write a brief** to the session scratchpad (never into the repo): the question, the current draft text of the target section, and the writing constraints from CLAUDE.md (first person, sentence-case headings, answer first, facts over intensifiers, no promotional language). Never include third-party readme content in the brief - the research corpus is copyrighted and stays out of prompts and out of this repo.

2. **Codex pass**:

   ```sh
   cat <brief> | codex exec --skip-git-repo-check -c sandbox_mode="read-only" "<prompt>"
   ```

   `--skip-git-repo-check` avoids the trusted-directory refusal.

3. **AGY pass**:

   ```sh
   agy --new-project --model "Gemini 3.5 Flash (High)" --print-timeout 3m -p "<prompt>"
   ```

   Always `--new-project` - plain `agy -p` can hang on a stale conversation. Never use `--dangerously-skip-permissions`.

4. **Synthesize**: report convergence, divergence, and the single strongest challenge to the current draft position. Hold any prose adopted from either model to the writing rules in CLAUDE.md - external model output tends toward intensifiers and promotional filler; strip it.

## Failure handling

If either CLI fails or times out, report which voice is missing and proceed with the other. A one-model council is still useful, but say so explicitly.
