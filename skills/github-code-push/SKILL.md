---
name: github-code-push
description: v3.2 Clean main-push skill
version: 3.2.0
author: Bl4ckRa1n-AI

# github-code-push

Default: main push. PR only if mode: pr.

**NEVER \\n in write_file—literal only.**

sed 's/^[0-9]*|//g; s/\\\\n/\\n/g' before git.

