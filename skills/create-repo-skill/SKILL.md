---
name: create-repo-skill
description: Use when asked to create or improve a repo's README, docs, icon, badges, diagrams or evaluation report. Keeps code and layout; asks before publishing. Not for app code.
metadata:
  author: illescasDaniel
  tags: [readme, documentation, repository, visuals]
---

# Create or refresh a repository

## Purpose

Make a repository's public face (README, docs, visuals, evidence, tests) clear and honest without disturbing its code. Do NOT use for writing application code, release automation or licensing decisions.

## Prerequisites

Read/write access to the repo. Optional: an image tool or model the user names (for artwork), a skill evaluator (for scores), `gh` (only if the user approves publishing).

## Instructions

1. **Inspect first.** Read the existing README, docs, scripts, CI, repository guidance (`AGENTS.md`/`CLAUDE.md`), git status and the user's preferences. Preserve uncommitted work, public links and packaging conventions. A new project needs source, tests, docs, license and config; reorganize an existing one only where the benefit outweighs migration cost.
2. **Write the README as a concise entry point**, in this order: icon and truthful badges, title and one-paragraph purpose, how-it-works visual or table, quick start, requirements and limits, evaluation, tests, link to detailed docs, license.
3. **Add visuals.** Prefer accessible SVG with `<title>`/`<desc>` and meaningful `alt` text; keep a text alternative for each diagram. If the user asks for generated artwork, use the image or design tool or model they name; otherwise hand-write SVG. Artwork must match actual behavior.
4. **Place files by convention where it fits:** artwork in `assets/`, guides and evidence in `docs/`, tests in `tests/`, installable source in the project's established package directory. Don't change source paths, external links, install artifacts, build metadata or public APIs just for visual consistency; if files move, update references or provide a migration. Long examples go in `<details>` or `docs/`.
5. **Report evidence only if verified.** Name the artifact, exact revision, tool version, date and limits. Keep security findings separate from quality scores; show submetrics only when measured; a skill's score is not the score of the app around it. Put details in `docs/evaluation.md`; never invent ratings, badges, stars or coverage.
6. **Test what is executable.** Add offline tests for scripts when requested or warranted, using temporary fixtures; keep dev-only files out of installed packages and verify package contents when packaging changes. Keep CI and advertised platform/version support aligned. Agent-behavior and paid evaluations are separate from script tests: respect the user's budget.
7. **Finish.** Check local links, image alt text, structural validity and relevant tests. Report changes, evidence and what is untested.

## Examples

- "Give this repo a proper README with an icon and workflow diagram" → inspect, write `README.md`, add `assets/icon.svg` and `assets/workflow.svg`, link `docs/evaluation.md` only if an evaluation was actually run.
- "Add badges and a score" → add only badges backed by real CI or files; add a score only from a measured run with its date and revision.

## Rules

- Ask before any external action: creating a remote repo, pushing, publishing, installing globally or spending on paid evaluation, unless already authorized.
- Never claim popularity, compatibility, coverage or scores that were not verified.

## Limitations

- Does not write application code, choose a license for the user or judge whether a project is worth publishing.
- Visual quality depends on the image tool available; without one, SVG is hand-written and simpler.

## Troubleshooting

- **Image looks wrong or overflows:** validate the SVG as XML, shorten text, re-render and check it at the README display size.
- **Evaluator can't run (missing scanner):** record the check as not run in `docs/evaluation.md`; do not invent a score.
- **Links break after moving files:** search the repo for the old path and update or redirect it.
