---
description: Synchronize global agent workflows from the claude-code-quickstart repository.
---

# /sync-workflows

Use this workflow to pull the latest "Gold Standard" workflows from your central `claude-code-quickstart` repository.

## The Process

1.  **Execute Sync Script**:
    - Run `chmod +x scripts/sync-workflows.sh`
    - Run `./scripts/sync-workflows.sh`

2.  **Verify**:
    - Check `.agent/workflows/` to see that files are updated.

**Note**: This assumes `claude-code-quickstart` is located at `../claude-code-quickstart`.
// turbo-all
