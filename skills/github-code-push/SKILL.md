# GitHub Code Pusher Skill v1.7
Hermes Agent skill by Black Rain Labs

## Workflow
cd /home/null/bl4ckra1n-repo
mkdir -p DIR
cp SOURCE DIR/NAME.ps1
sed -i 's/^\\s*\\d+\\|//g' DIR/NAME.ps1
git add DIR/NAME.ps1
git ls-files DIR/NAME.ps1
wc -l DIR/NAME.ps1
git commit -m 'Deploy NAME.ps1'
git push origin main

## Quote Fix
Use cat << 'EOF' for literal newlines
