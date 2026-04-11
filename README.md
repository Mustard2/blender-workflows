# GitHub CI Workflows for Blender Extensions

Collection of workflows that can be used on Blender Extensions repositories.


## Workflows available

- **Build the Extension** with Blender and generate the file that can be directly uploaded to the Blender Extension website or shared with users.

```
.github/workflows/blender-build.yml
```


## How to Use

- Create a new file in your repository called

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
    uses: Mustard2/blender-workflows/.github/workflows/blender-build.yml@main
    with:
      timeout-seconds: 180
      # Uncomment to specify a Blender version different from the latest
      #blender-version: "5.1.0"
```

- If the Extension builds correctly, an artifacts is uploaded which can be reviewed and downloaded in the Workflow Summary.
