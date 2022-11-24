# Hello world javascript action

This action checks PR title includes a given regex. Typically this will be set in main.yaml to match a JIRA ticket 

## Inputs

### `pattern`

**Required** The regex that must be matched as part of the PR title`.

## Outputs

### A status check on the PR

The time we greeted you.

## Example usage

```yaml
on:
  pull_request:
    types:
      # Check title when opened.
      - opened
      # Check title when new commits are pushed.
      - synchronize

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: Latermedia/gh-action-pr-naming@v1.2
        with:
          # Match pull request titles with JIRA Key format.
          pattern: '((?<!([A-Za-z]{1,10})-?)[A-Z]+-\d+)'
```