# GitHub Code Pusher Skill v1.4 - File Writes to GitHub
**Hermes Agent skill by Black Rain Labs** - Handles large file deploys (500+ lines)

## Workflow
```
cd /home/null/bl4ckra1n-repo
mkdir -p DIR
cp SOURCE DIR/NAME.ps1
sed -i 's/^\\s*\\d+\\|//g' DIR/NAME.ps1
git add DIR/NAME.ps1  # EXACT filename - NO wildcards!
git ls-files DIR/NAME.ps1  # Verify staged
wc -l DIR/NAME.ps1
git commit -m \"Deploy NAME.ps1 (N lines)\"
git push origin main
curl https://raw.githubusercontent.com/BlackRainLabs/Bl4ckRa1n-AI/main/DIR/NAME.ps1 | wc -l
```

## Key Fix
- **git add EXACT_PATH** (pathspec fails on `git add DIR/`)
- `git ls-files` confirms staged
- GitHub auto-makes dirs

## Examples
- HATUI-v2.ps1 (442 lines): /HATUI/HATUI-v2.ps1
- Skills: /skills/NAME/SKILL.md

**Pitfalls:** Dir adds fail quoting. Always exact filename + ls-files verify.
**Proven:** thetest.txt → live raw URL instant.