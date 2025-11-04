# Git Workflow Strategy

## Branch Structure

- **`main`** -> Production (no direct changes allowed)
- **`development`** -> Integration branch
- **Feature branches** -> All new work

## Branch Naming Convention

```
<type>/<TICKET-CODE>-<description>
```

**Types:**
- `feat/` - New features
- `fix/` - Bug fixes
- `hotfix/` - Critical production fixes
- `chore/` - Maintenance, refactoring
- `style/` - Code formatting only
- `docs/` - Documentation
- `test/` - Tests

**Examples:**
```
feat/JIRA-123-Add-User-Auth
fix/JIRA-456-Cart-Bug
hotfix/JIRA-789-Payment-Issue
```

## Feature brancing steps

### 1. Create Branch
```bash
git checkout development
git pull origin development
git checkout -b feat/JIRA-123-Feature-Name -> your branch
```

### 2. Work & Stay Updated
- Make small, focused commits
- Merge `development` regularly to avoid conflicts:
  ```bash
  git merge development
  ```
### 2.1 Naming commits
- Follow convetional commit messages
```bash
feat(auth): add password reset functionality
fix(cart): resolve item duplication issue
docs(readme): update installation instructions
```


### 3. Before PR
Run locally:
```bash
npm run typecheck
npm run lint
npm run test
npm run build
```

### 4. Create Pull Request
- ```bash
  git push --set-upstream origin your-branch
  ```
- **PR title:** `[JIRA-123] Brief description`
- **Keep PRs small** (less than 400 lines)
- Link to ticket
- Describe your changes clearly

### 5. Code Review
- **Minimum 1 reviewer required**
- All reviewers must approve
- Provide constructive feedback (not just "LGTM")
- Author fixes all observations before merging
- Delete branch after merge

## General rules

**Do:**
- Keep PRs small and focused
- Sync with `development` frequently
- Write meaningful commit messages
- Respond to all review comments

**Don't:**
- Commit directly to `main` or `development`
- Merge without approval
- Create huge PRs
- Ignore CI/CD failures