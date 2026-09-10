---
name: update-github-info
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:

permissions: read-all

tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:

network:
  allowed:
    - defaults
    - github.blog
    - awesome-copilot.github.com
    - github.com

safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    reviewers: [alexandre-huet]
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Keep Mona's GitHub Info website current with useful, official GitHub updates.

## Instructions

1. Use the GitHub repository API tools to read `notes/mona-notes.md` and `site/content/github-info.md`. Do not use terminal commands, the GitHub CLI, or sandboxed commands to read repository guidance or reference files.
2. Use `web-fetch` to read https://github.blog/latest/, https://github.blog/changelog/, and https://awesome-copilot.github.com/workflows/.
3. Select a small set of recent, practical updates that help developers learn GitHub faster. Follow Mona's editorial notes, keep summaries concise, and cite each GitHub Blog, Changelog, or Awesome Copilot workflows source with its URL.
4. Update only `site/content/github-info.md`; preserve its existing Markdown structure and official-reference focus.
5. When an update is warranted, use the `create-pull-request` safe output to propose the change. Set a clear title and body that summarize the selected updates and open a pull request for Mona to review. Do not write directly to `main`.
6. Do not open a pull request when the existing content is already current or no suitable updates are found.