# .github

Shared GitHub setup for my repositories.

| Path | What it does |
| --- | --- |
| `.github/pull_request_template.md`, `.github/ISSUE_TEMPLATE/` | Default PR and issue templates. GitHub applies them to any of my repos that don't have their own. |
| `SECURITY.md`, `CONTRIBUTING.md` | Defaults, same rule. |
| `.github/workflows/bun-ci.yml` | Reusable workflow: Bun install, then a list of commands. Self-contained, so a caller's commit pin covers everything it runs. |
| `actions/setup-bun-install/` | Composite action: Bun plus a frozen-lockfile install. |
| `claude/` | My Claude Code files (see its README). |

Call the workflow from another repo, pinned to a commit:

```yaml
jobs:
  ci:
    uses: bhimrazy/.github/.github/workflows/bun-ci.yml@<commit-sha>
    with:
      commands: "bun run typecheck,bun run test"
```
