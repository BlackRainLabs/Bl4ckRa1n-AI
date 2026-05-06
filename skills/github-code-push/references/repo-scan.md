# Repo Scan Techniques
## Commands
- `tree -I .git -a -L 3`: Visual dir tree
- `git ls-tree -r --name-only HEAD | sort`: Tracked files
- `find . -type f | sort`: All files (excl .git)
- `du -sh */ | sort -hr`: Dir sizes
- `git ls-tree -r --name-only HEAD | wc -l`: Tracked file count
- `find . -name '*.md'`: MD files

## Dynamic README Gen Workflow (2026-05-06)
1. `read_file /path/README.md` → current content
2. Scan: `search_files path=repo_root pattern=.* target=files limit=50` + `find . -name '*.md' | head -20`
3. `git ls-tree` + `du -sh */` for structure/sizes
4. Update sections: Structure tree, Highlights, Stats (files, sizes, SHA, URLs)
5. `write_file` new content → `git add/commit/push` → verify SHA

**Pitfall:** search_files on subdirs may miss (e.g. no SecOps hits); use broad root scan + manual find/git ls-tree.

## read_file Fix
read_file adds `1| ` prefixes. Strip:
```bash
sed 's/^[0-9]*|//'
```

## Working Dir
`/home/null/git-work/Bl4ckRa1n-AI` (stable clone dir)