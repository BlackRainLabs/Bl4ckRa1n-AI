# GitHub Push Newline Fix (Drew pref)
write_file literal:
```
line1
line2
```
sed -i 's/^[0-9]*|//g; s/\\\\n/\\n/g' file
git add/commit/push
Verify raw.githubusercontent.com no /n render.