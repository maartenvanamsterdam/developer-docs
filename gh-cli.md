# GitHub CLI (`gh`) Cheatsheet

## Authentication

```bash id="o3l1n2"
gh auth login
```

Check authentication status:

```bash id="n8f4qe"
gh auth status
```

---

# Clone Repository

```bash id="p6h3xk"
gh repo clone username/repository
```

Example:

```bash id="m2w7df"
gh repo clone maartenvanamsterdam/react-fundamentals
```

---

# Create Repository

```bash id="d9u5rj"
gh repo create
```

Create and push current folder:

```bash id="g5a1lc"
gh repo create my-project --public --source=. --push
```

---

# View Repository

```bash id="r1k9vb"
gh repo view
```

Open in browser:

```bash id="f3x2nm"
gh repo view --web
```

---

# Pull Requests

Create PR:

```bash id="j7t4cy"
gh pr create
```

Create PR with base branch:

```bash id="k4m8qw"
gh pr create --base main --head dev
```

List PRs:

```bash id="v6n2ze"
gh pr list
```

View PR:

```bash id="c8h5up"
gh pr view
```

Checkout PR locally:

```bash id="s1q9xr"
gh pr checkout 12
```

Merge PR:

```bash id="e4d7lm"
gh pr merge
```

---

# Issues

List issues:

```bash id="u2v8gc"
gh issue list
```

Create issue:

```bash id="w5k3na"
gh issue create
```

View issue:

```bash id="t9m6pj"
gh issue view 1
```

---

# Releases

Create release:

```bash id="y7b4dq"
gh release create v1.0.0
```

List releases:

```bash id="a3n8vf"
gh release list
```

---

# Workflow / GitHub Actions

List workflows:

```bash id="h6u1zr"
gh workflow list
```

View workflow runs:

```bash id="q8c5ly"
gh run list
```

Watch workflow live:

```bash id="z2d7mk"
gh run watch
```

View workflow logs:

```bash id="x4v9nb"
gh run view
```

Rerun failed workflow:

```bash id="b1q6te"
gh run rerun
```

---

# Open GitHub in Browser

Open current repo:

```bash id="m5w2rk"
gh browse
```

Open PR page:

```bash id="p9z4lc"
gh pr view --web
```

---

# Helpful Combination with Git

```bash id="n3y7uf"
git switch -c feature/navbar
git add .
git commit -m "feat: add navbar"
git push origin feature/navbar
gh pr create
```

