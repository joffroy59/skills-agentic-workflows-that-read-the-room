---
name: update-github-info
description: Draft practical updates for Mona's GitHub Info website from official GitHub sources.
on:
  schedule:
    - cron: '17 9 * * *'
  workflow_dispatch:
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
    allowed-files:
      - "site/content/github-info.md"
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
engine:
  id: copilot
  copilot-sdk: true
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use web-fetch to review:

- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/

Identify recent, useful updates for developers that fit the website's focus.
Update `site/content/github-info.md` with concise, practical content. Preserve
the existing structure and include source context when information comes from
the GitHub Blog or GitHub Changelog. Do not invent details; if no relevant,
verifiable update is available, call `noop` with a brief reason and make no
changes.

If you make a meaningful update, open a draft pull request for Mona to review.
Use a title that mentions Mona or GitHub Info. Do not write directly to `main`;
route the change through the configured `safe-outputs` `create-pull-request`.
