# Git Commands Cheatsheet

## Create and Switch Branches

```bash
git switch -c branch-name
```

Example:

```bash
git switch -c labs/react-foundations
```

---

## Switch Branches

```bash
git switch main
git switch dev
```

---

## Check Current Branch

```bash
git branch
```

Current branch is marked with `*`.

---

## Check Git Status

```bash
git status
```

---

## Add Files

```bash
git add .
```

Or specific files:

```bash
git add README.md
```

---

## Create Commit

```bash
git commit -m "feat: add navbar component"
```

---

## Push Branch

```bash
git push origin branch-name
```

Example:

```bash
git push origin dev
```

---

## Pull Latest Changes

```bash
git pull origin main
```

---

## Merge Branches

```bash
git switch main
git merge dev
```

---

## View Commit History

```bash
git log --oneline
```

---

## Delete Local Branch

```bash
git branch -d branch-name
```

---

## Delete Remote Branch

```bash
git push origin --delete branch-name
```

---

## Stash Changes

```bash
git stash
```

Restore:

```bash
git stash pop
```

---

## Fetch Remote Changes

```bash
git fetch
```

---

## Clone Repository

```bash
git clone <repo-url>
```
