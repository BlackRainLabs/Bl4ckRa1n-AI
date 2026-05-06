--- 
name: github-code-push
description: GitHub file deploy skill v3.1. Main-first workflow (PR optional).
version: 3.1.0
author: Black Rain Labs / Claire V2 / Drew
license: MIT
metadata:
  hermes:
    tags: [GitHub, Deploy, PR, Code-Push, Multi-Repo, Safety]
    related_skills: [github-auth]

# github-code-push
**Version:** 3.1.0

## Core Rules

- Default to direct push to main. Use `mode: pr` only when explicitly requested.
- Always verify the new commit SHA after every commit or push.
- Never proceed if `git status` shows no changes.
- Never force-push to protected branches unless `force: true` is set **and** the user has confirmed.
- Log every action: timestamp, repo, files, mode, and result.

## Handling User Requests

Users often speak casually. Translate these natural requests into proper actions:

- \"Create a PowerShell script about X and upload it\" → Create file + direct push to main
- \"Check this script and improve it\" → Review → changes + direct push
- \"Just push this\" / \"Commit it directly\" → direct push to main
- \"Fix the bug and deploy it\" → Fix + direct push
- \"Build a module and put it in HermesDev\" → Create + direct push
- \"Make a PR\" → `mode: pr`

Always use clear, professional commit messages even when the user is casual. Confirm before risky actions.

## Parameters

- `target_repo` (required)
- `files` (required) — array of paths
- `commit_message` (required)
- `mode` — `pr` (only for PRs) or omit/default: direct push
- `base_branch` — default `main`
- `pr_title` (recommended for PRs)
- `dry_run` — `true` for testing
- `force` — only when user explicitly allows

## Workflows

**Direct Push (Default):** 
1. Checkout/switch to main
2. Make changes
3. Commit with clear message
4. Push to main
5. Verify new SHA and report

**PR Mode (when mode: pr):** 
1. Create feature branch (`agent/<AGENT_NAME>`)
2. Make changes
3. Commit + push branch
4. Create PR via `gh pr create`
5. Verify + report

**Large Files:**
Use `cp` + `sed` cleanup when needed, then follow chosen workflow.

## Pitfalls to Avoid

- Do **not** create branches/PRs unless `mode: pr`.
- Do **not** skip SHA verification.
- Do **not** push to protected branches without confirmation + `force: true`.
- Do **not** proceed with empty commits.
- Do **not** ignore branch protection rules.
- **\n Escapes:** read_file outputs `\n`. Always `sed -i 's/\\\n/\n/g'` before git add.
- **Bash Quotes:** Parens `()` → single quotes `'msg (safe)'` [refs/bash-commit-fix.md]

If any rule would be violated, stop and ask for user confirmation.

## Decision Process

1. Understand the request and required changes
2. Default to direct push (fast for solo edits)
3. Use `mode: pr` only if requested
4. Select clear `commit_message`
5. Execute workflow
6. Verify result (new SHA + success)
7. Report outcome clearly

## Best Practices

- Direct push for most cases
- PRs only for reviews/collabs
- Use `dry_run: true` when unsure
- Descriptive commits
- Log deploys
- GitHub App auth when possible

**Workdir:** `/home/null/git-work/Bl4ckRa1n-AI`. Strip prefixes: `sed -i 's/^[0-9]*|//g'`. Full clean: `sed -i 's/^[0-9]*|//g; s/\\\n/\n/g'`.

**Strictly follow.**

---