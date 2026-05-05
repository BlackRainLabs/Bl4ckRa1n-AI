---
name: github-code-push
description: GitHub file deploy skill v2.2. cp+sed+write_file. Multi-repo support.
version: 2.2.0
author: Black Rain Labs / Claire V2
license: MIT
metadata:
  hermes:
    tags: [GitHub, Deploy, Large-Files, Code-Push, Multi-Repo]
    related_skills: [github-auth]

# GitHub Code Pusher v2.2

**Commit SHA REQUIRED** - no change unless `git commit` returns hash.

## Workdirs
```
temp-repo          # Current (Bl4ckRa1n-AI)
bl4ckra1n-repo     # Legacy
/home/null/repo/   # Future
```

## Workflows

### 1. Large Files (cp+sed)
```
cd /home/null/temp-repo
cp SOURCE skills/NAME.ps1
sed -i 's/^[0-9]*|//' skills/NAME.ps1  # Strip read_file prefixes
git add skills/NAME.ps1
git commit -m "Deploy NAME vX"
git push origin main
```

### 2. Small Files (write_file → git)
```
write_file(path="/home/null/temp-repo/README.md", content="# Updated")
cd /home/null/temp-repo
git add README.md
git commit -m "Update README"
git push
```

## Rules
**NO SHA = NO CHANGE:**
```
git log --oneline -1  # Must see new hash
```

## Escapes
```
cat > FILE << 'EOF'
Multi-line literal
