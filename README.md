# Stacy Action

# Full example to integrate in GitHub Actions

```yml 
on:
  pull_request:
    branches: [ main ]

jobs:
  Comment Stacy output in PR:
    runs-on: ubuntu-latest
    permissions:
      pull-requests: write
      contents: write
      repository-projects: write
    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Run Stacy Analyzer
        uses: ./
        with:
          target: 'tests/'
      - uses: mshick/add-pr-comment@v2.8.2
        with:
          message-path:  ${{ github.workspace }}/report.out
```

This example, if put in `.github/workflows/`, will run Stacy in the `target:` folder (in this case, the test folder) and comment the output in the PR.
