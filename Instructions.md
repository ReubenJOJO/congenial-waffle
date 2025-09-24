# Copilot Instructions for congenial-waffle

This repository demonstrates automation using GitHub Actions to fetch and update trending GitHub repositories daily. Follow these guidelines to be productive as an AI coding agent in this codebase:

## Big Picture Architecture
- **Purpose:** Automate daily updates of trending repositories using GitHub Actions.
- **Key Files:**
  - `.github/workflows/daily_updates.yml`: Main workflow for automation.
  - `trending.md`: Stores the latest trending repositories (updated daily).
  - `daily_updates.yaml`: Duplicate of the workflow file (for reference or alternate use).
  - `README.md`: Project overview.

## Workflow Details
- **Automation:**
  - Workflow runs daily at 05:00 UTC and can be triggered manually.
  - Uses `curl` and `jq` to fetch trending repositories from GitHub API (created in the last 7 days, sorted by stars).
  - Updates `trending.md` and creates a `trending.json` (not committed by default).
  - Commits changes to `trending.md` with a timestamped message.
  - Pushes changes using `ad-m/github-push-action@v0.8.0`.

## Developer Conventions
- **Commit Bot:** Commits are made using `github-actions[bot]` identity.
- **No build/test scripts:** The project is workflow-driven; no local build or test commands are required.
- **Manual Edits:** You may manually edit `trending.md` or workflow files, but automation will overwrite `trending.md` daily.
- **Secrets:** Requires `GITHUB_TOKEN` for API access (provided by GitHub Actions).

## Patterns & Integration Points
- **Data Flow:**
  - Workflow fetches data → writes to markdown → commits/pushes.
- **External Dependencies:**
  - Relies on GitHub API, `curl`, `jq`, and GitHub Actions runners.
- **Customization:**
  - To change the number of repos or query, edit the workflow's API call.
  - To change commit behavior, modify the commit/push steps.

## Example: Adding a New Automation
- Place new workflow files in `.github/workflows/`.
- Use similar patterns for API calls, file updates, and commits.
- Reference `daily_updates.yml` for structure and conventions.

## Key References
- `.github/workflows/daily_updates.yml` — main automation logic
- `trending.md` — output file, overwritten daily
- `README.md` — project intent

---
**For AI agents:**
- Prioritize automation and workflow logic.
- Avoid adding local build/test scripts unless new features require them.
- Document any new workflow or integration in the README.
