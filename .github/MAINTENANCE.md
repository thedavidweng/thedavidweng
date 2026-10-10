# Profile repository maintenance

The profile README is edited directly; there is no generated listing or build.
The one-time jactionlint 2.0.2 default audit replaces routine workflow linting.
No scheduled validation or Dependabot updater is needed for this static repository.

`mirror.yml` runs on branch/tag pushes and manual dispatch. It serializes mirror
writes without cancelling an in-progress sync. Checkout has read-only GitHub
contents permission and does not persist its token. `CODEBERG_TOKEN` must authorize
writes to `thedavidweng/thedavidweng` on Codeberg; no GitHub write scope is needed.
The pinned mirror action uses its own credentials and force-syncs branches/tags.

To sync manually: `gh workflow run mirror.yml --ref master`, then inspect the
result with `gh run list --workflow mirror.yml`. For a local audit, install
jactionlint 2.0.2 and run `jactionlint --version`,
`jactionlint --profile default --format summary`, and `jactionlint --diff`.
Review any proposed changes before applying them. GitHub branch protection has
no required status contexts referencing the retired Workflow lint job.
