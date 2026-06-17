# Summarize Me Examples

## Small Day

**Today In One Paragraph**
You set up the first version of a repo-local `summarize-me` skill so daily AI-assisted work can be reconstructed from actual evidence instead of becoming a black box of prompts and tool calls. The work focused on defining the command's purpose, output contract, and evidence-gathering behavior.

**What Changed**
- Added `.agents/skills/summarize-me/SKILL.md`.
- Added `.agents/skills/summarize-me/EXAMPLES.md`.

**Why It Changed**
The user wanted a daily work-memory summarizer that remembers process and reasoning, not just completed tasks.

**Decisions Made**
- Keep the skill instruction-first instead of script-first.
- Require evidence gathering before writing the summary.
- Use fixed sections so repeated daily summaries are easy to compare.

**What Failed Or Got Messy**
- No implementation failures were visible in the evidence.

**Evidence Trail**
- User request for `summarize-me today`.
- New skill files in `.agents/skills/summarize-me/`.

**Continue Tomorrow**
- Try the command after a real workday and tune the sections if the recap feels too verbose or too sparse.

## Larger Day

**Today In One Paragraph**
You spent the day tightening a feature from vague product intent into a usable implementation. The work moved through exploration, several AI-assisted edits, a failed test run caused by missing dependencies, and a final pass that clarified what was actually changed versus what still needs follow-up.

**What Changed**
- Updated the user-facing workflow in the relevant feature files.
- Adjusted supporting configuration.
- Captured follow-up questions for the next implementation pass.

**Why It Changed**
The original behavior made it hard to understand what the system had done and why. The changes were aimed at making the user's work easier to resume after multiple prompts, commits, and tool runs.

**Decisions Made**
- Keep the first version narrow enough to verify locally.
- Defer broader automation until the manual summary shape proves useful.

**What Failed Or Got Messy**
- One validation command failed because dependencies were unavailable.
- Some intent had to be inferred from conversation context rather than commits.

**Evidence Trail**
- Git diff and commit log from today.
- Terminal output from validation attempts.
- Conversation context and project notes.

**Continue Tomorrow**
- Re-run validation after installing dependencies.
- Decide whether the next version should write summaries to a dated file automatically.
