# MCVS-PR-validation-action

Mission Critical Vulnerability Scanner (MCVS) Pull Request (PR) Validation
Action is a custom [GitHub Action](https://github.com/features/actions) that
consists of the following steps:

- Nonempty PR description.
- PR description contains issue URL.(optional)

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
    runs-on: ubuntu-22.04
    steps:
      # required as action performs some git actions under the hood. Without
      # a checkout, a: 'failed to run git: fatal: not a git repository' issue
      # will appear.
      - uses: actions/checkout@v4.1.7
      - uses: schubergphilis/mcvs-pr-validation-action@v0.1.2
```
