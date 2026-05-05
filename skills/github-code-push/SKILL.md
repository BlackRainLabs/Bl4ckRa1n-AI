# GitHub Code Pusher Skill v1.0

## Workflow (500+ lines guaranteed)

1. cd /home/null/claire-repo
2. mkdir -p DIR
3. cp SOURCE DIR/NAME.ps1
4. sed -i 's/^\\s*\\d+\\|//g' DIR/NAME.ps1
5. git add DIR/NAME.ps1
6. git commit -m \"Deploy NAME.ps1 (N lines)\"
7. git push origin main

## Verify
curl https://raw.githubusercontent.com/BlackRainLabs/Bl4ckRa1n-AI/main/DIR/NAME.ps1 | wc -l

## Examples
- HATUI-v2.ps1 (442 lines)
- Trading bots, bash/Python

**Pitfalls:** Always sed prefixes. GitHub auto-mkdirs path.
**Method:** Proven on HATUI deploy.