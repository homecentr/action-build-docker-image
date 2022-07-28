# Build Docker Image composite action

## Usage
```yaml
name: CI/CD on master
on:
  push:

jobs:
  build:
    runs-on: ubuntu-latest
    permissions:
      contents: write # To add version tags
      packages: write # To push docker image
      issues: write   # Semantic release to link issues
    steps:
      - uses: actions/checkout@master

      - uses: homecentr/action-build-docker-image
        with:
          imageName: "homecentr/some-image" # name of the image
          runTests: true # set to false if the repo does not have "yarn test" command
          gitHubToken: ${{ secrets.GITHUB_TOKEN }}
          dockerHubUserName: ${{ secrets.DOCKERHUB_USERNAME }}
          dockerHubPassword: ${{ secrets.DOCKERHUB_PASSWORD }}
```