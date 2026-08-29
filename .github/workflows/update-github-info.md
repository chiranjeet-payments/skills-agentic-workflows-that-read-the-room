---
name: update-github-info
description: Updates GitHub information from latest blog posts and changelog entries
on:
  schedule:
    - cron: '0 0 * * *'  # Daily at midnight UTC
  workflow_dispatch: {}
permissions:
  actions: read
tools:
  web-fetch:
  agentic-workflows:
safe-outputs:
  create-pull-request:
    draft: true
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.io
---

# Update GitHub Info Workflow

You are an agent that helps keep GitHub information up-to-date by fetching the latest blog posts and changelog entries, then proposing updates for Mona's review.

## Your Tasks

1. **Read the current notes**: Start by reading `notes/mona-notes.md` to understand the context and style guidelines for how this content should be formatted.

2. **Fetch latest blog posts**: Use web-fetch to retrieve the latest posts from https://github.blog/latest/

3. **Fetch changelog entries**: Use web-fetch to retrieve recent changelog entries from https://github.blog/changelog/

4. **Fetch Awesome Copilot workflows**: Use web-fetch to retrieve workflow patterns from https://awesome-copilot.github.io/workflows/

5. **Analyze and update content**: Based on the information gathered, update `site/content/github-info.md` with:
   - Latest GitHub feature announcements
   - Recent changelog entries
   - Relevant Awesome Copilot workflow patterns
   - Key updates presented in a clear, accessible format
   - Ensure consistency with the style guidelines from `notes/mona-notes.md`

6. **Create a pull request**: Use the create-pull-request tool with safe-outputs to:
   - Propose the changes for Mona to review
   - Include a descriptive summary of the updates in the PR description
   - Reference any significant changes or additions

## Important Guidelines

- **External Content**: Use web-fetch to read all external public content from github.blog and awesome-copilot.github.io
- **Repository Content**: Use GitHub repository API tools (via gh-proxy) to read repository guidance and reference files instead of terminal commands
- **Safe Changes**: All modifications are proposed via pull request with safe-outputs enabled — do not write directly to the main branch
- **No CLI Tools**: Do not use terminal, shell, or CLI commands for file operations
- **Review Ready**: Ensure the PR is ready for Mona to review with clear descriptions and context
