# Humanizer Skill

This repository now contains a single reusable AI skill for rewriting AI-sounding prose so it reads more naturally while preserving meaning.

## Purpose

Use this skill when you want an AI agent to:
- remove common AI-writing patterns
- keep facts and intent intact
- produce cleaner, more human-sounding text

## Contents

- `skill/SKILL.md` — the complete Humanizer skill prompt

## How to use

1. Copy `skill/SKILL.md` into your agent's skill directory, or import this repository in your skill manager.
2. Invoke the skill in your agent (for example with a command like `/humanizer`, depending on your tool).
3. Provide the text you want rewritten.

## Notes

- Keep the source text factual and complete.
- The skill rewrites style and structure; it should not invent facts.
