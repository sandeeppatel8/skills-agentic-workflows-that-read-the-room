---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[Mona review] "
    draft: true
    max: 1
---

# Update Mona's GitHub Info

Read `notes/mona-notes.md` and the current `site/content/github-info.md` before researching or editing. Follow Mona's notes for editorial tone and scope.

Use the `web-fetch` tool to read both official sources:

- https://github.blog/latest/
- https://github.blog/changelog/

Identify recent items that can give developers practical GitHub guidance or meaningfully update the website's existing themes. Verify each summary against its source page; do not infer details from a headline, invent announcements, or include unsourced claims. Keep summaries short and practical, and link each item to its official source. Preserve relevant existing content and avoid duplicate entries.

Edit only `site/content/github-info.md`. Do not change the notes, workflow, site code, or other files. If neither source supports a useful update, make no changes and do not open an empty pull request.

When the content changes, use the `create-pull-request` safe output to open one draft pull request against `main` for Mona to review. Use a clear summary that mentions the source pages and the practical updates; do not write directly to `main` or use any other write mechanism.