--- 
name: github-code-push
description: GitHub code push/deploy skill v3.2. Main default, PR optional, clean newlines.
version: 3.2.0
author: Bl4ckRa1n-AI / Drew
license: MIT
tags: [github, deploy, code-push]

# github-code-push v3.2

**Default: direct main push.** Branch/PR only if `mode: pr`.

## Parameters
- target_repo (required)
- files (required)
- commit_message (required)
- mode: pr (optional)
- base_branch: main

## Workflow Default
1. cd workdir
2. Edit files (write_file + sed clean)
3. git add
4. git commit
5. git push main
6. git log --oneline -1 SHA

## PR Mode
1. git checkout -b agent/Bl4ckRa1n-AI
2. Edit/push
3. gh pr create

## Clean Rules
**LITERAL newlines in write_file:**
line1
line2

**NOT:** "line1\\nline2"

**Pre-git:** sed -i 's/^[0-9]*|//g; s/\\\\n/\\n/g' file

Workdir: /home/null/git-work/repo
