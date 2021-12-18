<!-- start title -->

# GitHub Action: Generate Readme and Release Action

<!-- end title -->
<!-- start description -->

Builds an image, pushes to artifact registry, and caches to gha as well as the `cache` tag

<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->

```yaml
- uses: swarm-io/action-release-action@undefined
  with:
    # git token to use for the run
    token: ""
```

<!-- end usage -->
<!-- start inputs -->

| **Input**   | **Description**              | **Default** | **Required** |
| :---------- | :--------------------------- | :---------: | :----------: |
| **`token`** | git token to use for the run |             |   **true**   |

<!-- end inputs -->
<!-- start outputs -->
<!-- end outputs -->
<!-- start examples -->
### Example usage to release on PR merge to main
```yaml
name: Semantic Release
on:
  pull_request:
    types:
      - closed
    branches:
      - main
    paths:
      - action.yaml
jobs:
  semantic-release:
    if: github.event.pull_request.merged == true
    runs-on: ubuntu-latest
    steps:
      - uses: swarm-io/action-release-action@v1
        with:
          token: ${{ secrets.GIT_RUNNER_TOKEN }}
```
<!-- end examples -->
<!-- start [.github/ghdocs/examples/] -->
<!-- end [.github/ghdocs/examples/] -->
