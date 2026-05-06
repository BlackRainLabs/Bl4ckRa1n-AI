---
name: github-code-push
version: 3.3.0
author: Bl4ckRa1n-AI / Drew

# github-code-push v3.3 - PR Default + Literal Newlines

## Core Rules
- Default `mode: pr`
- SHA verify always
- No empty commits
- No force-push without `force: true` + confirm
- Log all: timestamp/repo/files/mode/result

## User Request Translation
- "upload script" → create + pr
- "improve" → review + pr
- "push direct" → push mode
- "deploy" → pr

## Params
target_repo, files, commit_message, mode (pr default), base_branch (main), pr_title, dry_run, force

## Workflows
**PR (default):**
1. branch agent/Bl4ckRa1n-AI
2. changes
3. commit/push
4. gh pr create
5. SHA report

**Push (mode: push):**
1. main
2. changes
3. commit/push main

**Large Files:** cp + sed clean

## Pitfalls
- No direct push default
- sed 's/^[0-9]*|//g; s/\\\\n/\\n/g' ALWAYS pre-git
- **write_file LITERAL newlines only:**
content here
multi line

