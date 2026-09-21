---
name: update-github-info
description: Keep the GitHub Info page current with useful, sourced updates from the GitHub Blog, Changelog, and Awesome Copilot workflows.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine: copilot
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    draft: true
    max: 1
    reviewers: [mona]
    fallback-as-issue: false
---

# Update GitHub Info

Maintain the GitHub Info page for Mona's review.

## Instructions

1. Read `notes/mona-notes.md` before making any decisions.
2. Use the web-fetch tool to read:
   - https://github.blog/latest/
   - https://github.blog/changelog/
  - https://awesome-copilot.github.com/workflows/
3. Use the GitHub repository API tools for repository reads. Do not use terminal, CLI, or sandboxed commands to read repository guidance or reference files.
4. Identify a small number of recent updates that are useful for developers learning GitHub. Keep summaries short and practical.
5. Update `site/content/github-info.md` with the selected updates. Mention the source for every update from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows.
6. Review the resulting file for accuracy, clarity, and unnecessary duplication. Make only focused content changes.
7. Create a draft pull request with the changes for Mona to review. Include a concise title and explain which sources informed the update in the pull request body.
8. Do not write directly to the default branch, push changes manually, or create a pull request without first making and checking the intended file changes.
