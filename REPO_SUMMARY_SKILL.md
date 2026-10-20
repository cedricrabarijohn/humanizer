---
name: humanizer-repo-guide
description: |
  Summarize the Humanizer repository so an AI agent can work in it safely and consistently.
  Use when planning or editing SKILL.md, README.md, manifests, or release metadata.
license: MIT
metadata:
  version: "1.0.0"
---

# Humanizer repository skill (summary)

Use this as a quick working guide for agents in this repository.

## What this repository is

- Humanizer is a Markdown-based AI skill.
- The product is the prompt in `/home/runner/work/humanizer/humanizer/SKILL.md`.
- There is no build system for product code.

## Main purpose

Humanizer rewrites AI-sounding prose so it reads like a person wrote it, without changing facts.

## Core files and roles

- `/home/runner/work/humanizer/humanizer/SKILL.md`: source of truth skill prompt with YAML metadata and 26 numbered patterns.
- `/home/runner/work/humanizer/humanizer/README.md`: user docs for install, usage, and pattern reference.
- `/home/runner/work/humanizer/humanizer/CHANGELOG.md`: release history, newest version first.
- `/home/runner/work/humanizer/humanizer/.claude-plugin/plugin.json`: Claude plugin manifest; points skills loader at repo root.
- `/home/runner/work/humanizer/humanizer/.claude-plugin/marketplace.json`: Claude marketplace manifest.
- `/home/runner/work/humanizer/humanizer/.cursor-plugin/plugin.json`: Cursor plugin manifest.
- `/home/runner/work/humanizer/humanizer/agents/openai.yaml`: OpenAI-compatible agent display metadata.
- `/home/runner/work/humanizer/humanizer/scripts/validate-package.py`: package consistency validator.
- `/home/runner/work/humanizer/humanizer/AGENTS.md`: contributor rules for safe updates.

## Repository invariants (must keep true)

- Keep only one skill file for packaging: root `SKILL.md` is canonical.
- Keep SKILL and README pattern lists aligned by number and name.
- Keep pattern numbering contiguous from 1 with no gaps.
- Keep ordering by strength/frequency (strongest first).
- Keep one shared version across:
  - `SKILL.md` (`metadata.version`)
  - first heading in `CHANGELOG.md`
  - `.claude-plugin/plugin.json`
  - `.cursor-plugin/plugin.json`
- Plugin manifest descriptions must match the first sentence of SKILL description.
- Keep `SKILL.md` at or under 5,500 words.
- Keep install/use language agent-neutral and portable.

## Writing standards

- Use Plain Language.
- Lead with the main point.
- Use short sentences and active voice.
- Keep exact identifiers, commands, paths, schema fields, and behavior-bearing phrases intact.

## Change policy

- Make small, targeted changes.
- Update `README.md` when skill behavior or pattern wording changes.
- Add a concise `CHANGELOG.md` entry for behavior changes and non-obvious fixes.
- Prefer folding new tells into existing patterns instead of adding new ones.

## Validation workflow

Run existing checks before finalizing changes:

1. `python3 /home/runner/work/humanizer/humanizer/scripts/validate-package.py`
2. `npx skills add . --list`
3. `claude plugin validate .`

If external CLIs are unavailable, run at least the local validator and report what could not be run.

## Scope boundaries for edits

- Preserve technical meaning and factual claims.
- Do not invent names, numbers, dates, quotes, or citations.
- Do not add tool-specific lock-in instructions.
- Avoid unnecessary growth in `SKILL.md`; every added word must earn its place.

## Quick task playbook for agents

1. Read `SKILL.md`, `README.md`, `CHANGELOG.md`, and `AGENTS.md`.
2. Identify whether changes affect patterns, docs, metadata, or packaging.
3. Apply minimal edits while preserving invariants.
4. Run validation checks.
5. Summarize changes and any unresolved constraints.
