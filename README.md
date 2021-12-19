<!-- start title -->

# GitHub Action:Generate Readme and Release Action

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

    # If true, this action will disable the `include administrators` setting in branch
    # protection for this branch, and re-enable it after release. Re-enabling is run
    # using always()
    # Default: false
    toggle-admins: ""

    # The release configuration to use for the release. Set this to
    # `@swarm-io/release-config-javascript-actions` for javascript actions
    # Default: @swarm-io/release-config-actions
    release-config: ""
```

<!-- end usage -->
<!-- start inputs -->

| **Input**            | **Description**                                                                                                                                                                |            **Default**             | **Required** |
| :------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------: | :----------: |
| **`token`**          | git token to use for the run                                                                                                                                                   |                                    |   **true**   |
| **`toggle-admins`**  | If true, this action will disable the `include administrators` setting in branch protection for this branch, and re-enable it after release. Re-enabling is run using always() |                                    |  **false**   |
| **`release-config`** | The release configuration to use for the release. Set this to `@swarm-io/release-config-javascript-actions` for javascript actions                                             | `@swarm-io/release-config-actions` |  **false**   |

<!-- end inputs -->
<!-- start outputs -->
<!-- end outputs -->
<!-- start examples -->

### Example usage to release on PR merge to main with branch protection enabled

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
          toggle-admins: true
```

<!-- end examples -->
<!-- start [.github/ghdocs/examples/] -->
<!-- end [.github/ghdocs/examples/] -->
