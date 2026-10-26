# Agent guide: profile README

`readme.md` is edited by hand. Workflow and mirror maintenance live in `.github/MAINTENANCE.md`.

## Contributed To

- List only merged PRs (or direct commits) to other people's repos. Do not list open or draft PRs.
- Describe what the user contributed, not the project. Use sentence-case noun phrases (e.g. "Factory requests opened as Droid fix").
- Every item links its PR(s). Separate several items in one entry with `; `.
- For very large sets (Homebrew), link the main PRs, then end with `and [more](https://github.com/OWNER/REPO/pulls?q=is%3Apr+author%3Athedavidweng+is%3Amerged)`.
- Substantive = a real feature, bug fix, or meaningful code/build/CI/packaging work (a NEW Homebrew formula/cask for someone else's software counts). Not substantive: docs/README edits (check the diff, not just the title) and mechanical changes: pure version bumps, dependency/toolchain updates, upstream syncs, lockfile/manifest refreshes, lint/advisory ignores, behavior-neutral deprecation migrations, build-config moves, CI flake retries.
- A repo is listed only if it has at least one substantive merged PR. Never list a repo whose only contributions are docs or mechanical (e.g. sharp, beets, kimi-code, mieru, gpui-kit, deck-tailscale, openwrt/packages, cockpit-tools).
- Drop mechanical PRs entirely, even in listed repos; only docs PRs get the trailing `; docs updates (...)` item.
- In a listed repo, mention docs-only PRs (including trivial comment/style fixes) as one short trailing item: `; docs updates ([#1](pr-url), [#2](pr-url))`.
- Never list submissions of the user's own software (e.g. winget-pkgs manifests for OpenKara, Homebrew casks/formulae for the user's own apps). Packaging other people's software in Homebrew is fine.
- Entry format:
  `- [repo](https://github.com/OWNER/REPO) <badge> - Contribution ([#1](pr-url)); other contribution ([#2](pr-url))`

## Star badge

Use exactly this (replace OWNER/REPO):

```html
<img src="https://img.shields.io/github/stars/OWNER/REPO?style=flat-square&label=%E2%98%85&labelColor=555&color=555" align="absmiddle" height="18" alt="stars">
```

GitHub keeps `align="absmiddle"`, so the single-tone grey badge sits on the text's center line in both light and dark themes. The markdown image form `![stars](...)` sits on the baseline and the two-tone default looks noisy. Never write star counts as text.

## Sorting

- Contributed To: number of the user's substantive merged PRs in the repo (docs and mechanical PRs not counted), descending; then stars, descending.
- Own projects: the user's commit count on the default branch (GraphQL `history(author: {id})`), descending; then stars, descending. Sort within each section.

## Own projects

- Include the user's own repos with >=5 stars, except material/resource-sharing repos (datasets, awesome lists, skills collections).
- Include every project on https://app.blahaj.uk (Hajware; read `https://app.blahaj.uk/llms.txt`), with its site or docs link.

## Style and checks

- Keep the existing structure and English tone. Lists stay tight: no blank lines between items.
- Use live data from the GitHub API; never invent numbers.
- Before committing, check that every link and badge URL returns 200 (LinkedIn returns 999 to bots; that is expected).

## Git

- Author and committer: only `thedavidweng <95214375+thedavidweng@users.noreply.github.com>`. No `Co-authored-by` or other trailers.
- Conventional commit messages (e.g. `docs: ...`). No force-push.
- `master` has a PR-required rule; the owner bypasses it on direct pushes.
