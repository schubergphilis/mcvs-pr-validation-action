# MCVS-PR-validation-action

Mission Critical Vulnerability Scanner (MCVS) Pull Request (PR) Validation
Action is a custom [GitHub Action](https://github.com/features/actions) that
consists of the following steps:

- Nonempty PR description.

## Usage

Create a `.github/workflows/mcvs-pr-validation.yml` file with the following
content:

```yaml
---
name: MCVS-PR-validation-action
"on":
  pull_request:
    types:
      - edited
      - opened
      - reopened
      - synchronize
  workflow_call:
permissions:
  contents: read
  pull-requests: read
jobs:
  MCVS-PR-validation-action:
    runs-on: ubuntu-24.04
    steps:
      # required as action performs some git actions under the hood. Without
      # a checkout, a: 'failed to run git: fatal: not a git repository' issue
      # will appear.
      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6.0.2
      - uses: schubergphilis/mcvs-pr-validation-action@6f153c01301ab2f92336781173b7f3a796de5f3e # v0.2.2
```

Pin actions to a full commit SHA rather than a tag, as tags can be moved. Use
[Dependabot](https://docs.github.com/en/code-security/dependabot/working-with-dependabot/keeping-your-actions-up-to-date-with-dependabot)
to keep the pinned SHAs up to date.
