# GitHub Code Pusher Skill v1.5 - File Writes to GitHub
**Hermes Agent skill by Black Rain Labs**

## Workflow (exact, no escapes)
```
cd /home/null/bl4ckra1n-repo
mkdir -p DIR
cp SOURCE DIR/NAME.ps1
sed -i 's/^\\s*\\d+\\|//g' DIR/NAME.ps1
git add DIR/NAME.ps1  # EXACT filename
git ls-files DIR/NAME.ps1  # Verify
wc -l DIR/NAME.ps1
git commit -m 'Deploy NAME.ps1 (N lines)'
git push origin main
curl https://raw.githubusercontent.com/BlackRainLabs/Bl4ckRa1n-AI/main/DIR/NAME.ps1 | wc -l
```

## Quote Escapes FIXED
**AVOID:** `echo \"content\"` → literal `\\n` (hex 5c6e)
**USE:** 
```
cat > FILE << 'EOF'
Multi
line
content
EOF
```
**OR:** `printf 'content\\nline2' > FILE`

## Examples
/skills/finaltest.txt → **live** (v1.4 test)

**Pitfalls:** `echo` escapes newlines. **printf/cat EOF**. Dir wildcards fail pathspec.