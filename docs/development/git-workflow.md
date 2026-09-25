# Git Workflow

Use focused feature branches and commits.

Recommended flow:

```text
Create feature branch
→ Implement
→ Build
→ Test
→ Review diff
→ Commit
```

Examples:

```text
feat: add police unit system
feat: add emergency lighting controller
feat: add pursuit lighting groups
fix: prevent busy units from receiving calls
refactor: separate vehicle definition from entity logic
docs: update lighting architecture
```

Avoid mixing unrelated changes in one commit.

Review the diff before committing.
