---
name: github-code-push
description: GitHub file deploy skill. cp+sed for large files. Commit confirmation required.
version: 2.1.0
author: Black Rain Labs
license: MIT
metadata:
  hermes:
    tags: [GitHub, Deploy, Large-Files, Code-Push]
    related_skills: [github-auth]

# GitHub Code Pusher v2.1

Hermes Agent skill for GitHub file writes. **Commit confirmation REQUIRED** - no change unless `git commit` returns SHA.

## Workflow
```
cd /home/null/bl4ckra1n-repo
cp SOURCE skills/NAME.ps1
sed -i 's/^\\s*\\d+\\|//g' skills/NAME.ps1
git add skills/NAME.ps1
git ls-files skills/NAME.ps1  # Verify staged
git commit -m 'Deploy NAME.ps1'  # SHA confirms change
git push origin main
curl https://raw.githubusercontent.com/BlackRainLabs/Bl4ckRa1n-AI/main/skills/NAME.ps1 | wc -l
```

## Commit Rule
**NO COMMIT SHA = NO CHANGE.** Always check:
```
git log --oneline -1  # New SHA = success
```

## Escapes
**cat << 'EOF'** literal newlines:
```
cat > FILE << 'EOF'
Line 1
Line 2
EOF
```

## Pitfalls
- **Exact add:** `git add skills/NAME.ps1`
- **No dir add:** `git add skills/` fails pathspec
- **Auto-mkdir:** GitHub creates path on push

**Proven:** 600-line bigfinal.txt live.
