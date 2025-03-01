2025-03-01 16:14

Tags: [[Git]] 

---

> [!i] You want to rebase branch-a to main

- 1. Check out the `branch-a`: 
```
git switch branch-a
```
- 2. Fetch latest:
```
git fetch
```
- 3. Start rebase:
```
git rebase origin/main
```
- 4. Resolve the conflicts
- 5. Stage the files after resolved:
```
git add .
```
- 6. Commit the code:
```
git commit -m"resolve conflict"
```
- 7. Continue rebase
```
git rebase --continue
```
- Repeat 4,5,6,7 (the number of rebase times depend on how much commits needed to be rebased)
- Push the code:
```
git push origin my-feature-branch --force-with-lease
```
---
# References