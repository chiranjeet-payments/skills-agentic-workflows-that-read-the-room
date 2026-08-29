---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
    - awesome-copilot.github.com
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot Workflows: https://awesome-copilot.github.com/workflows/

Workflow instructions:
- Use `web-fetch` to read the public guidance from the GitHub Blog, GitHub Changelog, and Awesome Copilot Workflows.
- Use GitHub repository API tools to read repository guidance and reference files instead of terminal, CLI, or sandboxed commands.
- Update `site/content/github-info.md` with concise, practical updates for readers and include source context when content comes from the GitHub Blog, GitHub Changelog, or Awesome Copilot Workflows.
- Open a pull request for Mona to review before merging.
- Use a pull request title that mentions Mona or GitHub Info.
- Do not write directly to `main`; rely on `safe-outputs` with `create-pull-request` so the agent can propose changes without direct writes.
- When the workflow creates a pull request, keep it focused on the GitHub Info page and clearly note the source of the update.
