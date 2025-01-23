# Print Format Diff

`track-overrides` is a GitHub Action designed to track method overrides in Python projects.
It automatically detects the base branch from the pull request that triggers the action and compares the code changes in the pull request against the corresponding branch in the repository specified in the method annotations. 

This comparison is performed using the commit hash associated with each method. If the overridden method and the upstream method have different commit hashes, the action will indicate that the overridden method has changed. This seamless comparison capability enables efficient tracking of method overrides across different branches and repositories.


## Usage

To use the `diff-print-format` GitHub Action in your workflow, follow these steps:

### 1. Create a Workflow File

Create a new GitHub Actions workflow file in your repository, e.g., `.github/workflows/diff_print_format.yml`, and add the following content:

```yaml
name: Diff Print Formats

on:
  pull_request:

jobs:
  diff_print_format:
    runs-on: ubuntu-latest
    name: Diff Print Formats
    steps:
      - name: Checkout the code
        uses: actions/checkout@v3
        with:
          fetch-depth: 0

      - name: Diff Print Formats
        uses: diamorafaela/diff-print-format@main
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```