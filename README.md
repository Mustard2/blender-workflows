# GitHub CI Workflows for Blender Extensions

Collection of Reusable Workflows that can be used on Blender Extensions repositories.


## Workflows available

The workflows available are the following, with their path to add to your workflow file.

- [**Build the Extension**](.github/workflows/blender-build.yml) with Blender and generate the file that can be directly uploaded to the Blender Extension website or shared with users.

```
.github/workflows/blender-build.yml
```


## How to Use

- Create a new file in your repository to run the workflow in the workflows folder. For instance:

```
.github/workflows/blender-build.yml
```

- Modify the file adding

```yml
name: Build & Test Blender Extension

on:
  pull_request:
  push:
    branches:
      - main

jobs:
  blender:
    uses: Mustard2/blender-workflows/.github/workflows/blender-build.yml@v1
    with:
      timeout-seconds: 180
      # Uncomment to specify a Blender version different from the latest
      #blender-version: "5.1.0"
```

- If the Extension builds correctly, an artifacts is uploaded which can be reviewed and downloaded in the Workflow Summary.


## Testing multiple versions

To test more Blender versions at the same time, `strategy: matrix` can be used. For instance

```yml
jobs:
  blender:
    strategy:
      matrix:
        blender: [ "5.1.0", "4.2.0" ]

    name: Blender ${{ matrix.blender }}
    needs: lint
    uses: Mustard2/blender-workflows/.github/workflows/blender-build.yml@v2
    with:
      timeout-seconds: 180
      blender-version: ${{ matrix.blender }}
```


## Update the Workflow version

When an updated version of the workflow is available, update the tag `v1` with the appropriate version.
