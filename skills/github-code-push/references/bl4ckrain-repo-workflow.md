# Bl4ckRa1n-AI Repo Workflow Notes (2026-05-06)
## User Expectations (Drew)
- SHA verify **every** push: `git rev-parse HEAD`
- Live links: https://github.com/BlackRainLabs/Bl4ckRa1n-AI/blob/main/PATH
- No drama, direct results

## Escapes Fixed (Live repro)
read_file → `1|line\\n\\n2|line`
```
sed -i 's/^\\s*\\d\\+\\|//g'  # Strip 1|
sed -i 's/\\\\n/\\n/g'        # Fix \\n → \n
```

## Pitfalls (Session 2026-05-06)
- write_file clean → cp/sed safer for git
- `git -C /path` prevents cwd loss
- User calls out formatting → IMMEDIATE fix + verify