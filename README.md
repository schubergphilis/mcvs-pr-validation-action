# MCVS-PR-validation-action

Mission Critical Vulnerability Scanner (MCVS) Pull Request (PR) Validation
Action is a custom [GitHub Action](https://github.com/features/actions) that
consists of the following steps:

- Nonempty PR description.

## Usage

Create a `.github/workflows/mcvs-pr-validation.yml` file with the following
content:

```bash
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
jobs:
  MCVS-PR-validation-action:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v4.1.1
      - uses: schubergphilis/mcvs-pr-validation-action@v0.1.0
```
