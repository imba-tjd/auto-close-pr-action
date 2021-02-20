# Auto close PR Action

Many newcomers don't know how to use PR and create many invalid ones.

This action closes PRs whose body text DOESN'T match with given pattern.

The pattern is used by GNU grep.

NOTE: This action is not widely tested. Similar project: https://github.com/roots/issue-closer-action.

## Typical usage

```yml
# .github/PULL_REQUEST_TEMPLATE.md
<!-- If you are clear about what you are doing, type "confirm" without quotation marks after this colon: -->

# .github/workflows/auto_close_pr.yml
name: Auto Close PR
on:
  pull_request_target:
    types: [opened]  # so that not trigger when reopened

jobs:
  auto_close_pr:
    runs-on: ubuntu-latest
    if: github.repository == '<user>/<repo>'
    steps:
    - uses: imba-tjd/auto-close-pr-action@master
      with:
        pattern: ':\s*confirm\s*-->'
        # message: <optional>
```
