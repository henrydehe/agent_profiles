# Agent Profiles

Centralized repository for AI agent profiles that sync across multiple repositories.

## Structure

- `profiles/` - Individual profile files (.md format)
- `repo_mapping.yaml` - Maps repositories to their assigned profiles
- `templates/` - Templates for new repositories
- `.github/workflows/` - Automated sync workflows

## Usage

### Adding a New Profile

1. Create a new `.md` file in `profiles/` with your agent instructions
2. The same content will be distributed to all mapped repositories

### Adding a Repository

Add your repository to `repo_mapping.yaml`:

```yaml
repositories:
  "your-org/your-repo":
    profile: "profile_name"  # Must match filename in profiles/ (without .md)
    agent_files:
      claude: "CLAUDE.md"
      codex: "agents.md"
      positron: "llms.txt"
    path: "."  # Where to place files in target repo
```

### For New Repositories

1. Copy files from `templates/basic/` to your new repository
2. Add your repository to `repo_mapping.yaml`
3. Profiles will sync automatically on the next update

## Sync Behavior

- Triggered automatically when profiles or mapping changes
- Creates/updates agent files in target repositories
- Same profile content distributed to all configured agent files
- Can be triggered manually via GitHub Actions