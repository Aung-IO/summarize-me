---
name: summarize-me
description: Create daily work-memory summaries for AI-assisted developers that reconstruct what happened, why it happened, decisions, failures, changes, and next steps. Use when the user says "summarize-me today", asks for a daily recap, work-memory summary, end-of-day developer summary, or wants to recover context from prompts, commits, tools, notes, and file changes.
---

# Summarize Me

## Quick Start

When the user runs:

```sh
summarize-me today
```

Produce a grounded end-of-day work-memory summary. The goal is to help the user remember the real process of the day, not merely list completed tasks.

## Workflow

1. Establish the date window.
   - Treat `today` as the user's local current date.
   - If timezone or workspace date is available, use it explicitly.
   - If the available evidence spans midnight, mention the exact date range used.

2. Gather evidence before summarizing.
   - Inspect recent git commits, staged and unstaged changes, and notable file diffs.
   - Review any available conversation context, prompts, notes, task files, terminal output, issue references, or docs.
   - Prefer local evidence over inference. If evidence is missing, say what could not be inspected.

3. Reconstruct the work process.
   - Identify what the user was trying to accomplish.
   - Explain why the work mattered or what problem it was addressing.
   - Capture decisions, tradeoffs, reversals, failed attempts, blockers, and tool/AI-assisted steps.
   - Distinguish shipped changes from explored ideas.

4. Write the summary in a human memory style.
   - Use concrete nouns, file names, commands, commits, and artifacts when available.
   - Avoid generic productivity language.
   - Do not overstate certainty. Mark inferred points as inferred.

## Output Format

Use these sections:

- **Today In One Paragraph**: A narrative overview of the day's work and intent.
- **What Changed**: Concrete repo, document, design, config, data, or decision changes.
- **Why It Changed**: The motivation, problem, or pressure behind the work.
- **Decisions Made**: Decisions, accepted constraints, tradeoffs, and abandoned paths.
- **What Failed Or Got Messy**: Failed commands, dead ends, confusing moments, regressions, or unresolved friction.
- **Evidence Trail**: Commits, files, commands, notes, conversations, or artifacts used to build the recap.
- **Continue Tomorrow**: Specific next actions, questions, and context the user should not have to rediscover.

Keep the recap concise but information-dense. If the day was large, group related workstreams instead of making a chronological log.

## Evidence Commands

Use commands like these when working in a git repository:

```sh
git status --short
git log --since="today 00:00" --oneline --decorate
git diff --stat
git diff --cached --stat
```

Use `rg` to search notes, task files, or project docs for today's date, TODOs, and terms from the conversation.

## Style Rules

- Write for the future version of the user who needs to reload the day's reasoning quickly.
- Preserve uncertainty and missing context.
- Focus on causality: "because", "so that", "after", "but", "then".
- Include AI/tool involvement when it changed the shape of the work.
- Do not invent commits, commands, results, or motivations that are not supported by evidence.

See [EXAMPLES.md](EXAMPLES.md) for compact output examples.
