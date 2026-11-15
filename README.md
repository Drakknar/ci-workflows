# ci-workflows

<img src="assets/icon.svg" alt="" width="96" align="right">

Shared GitHub Actions workflows for Drakknar's repos.

- `image.yml`: secret scan, tests, build and smoke test; publishes to GHCR from `main` only.
- `foundry-module.yml`: checks for a Foundry VTT module.

Callers pin an exact commit, so a change here reaches a repo only through that repo's own pull request:

```yaml
jobs:
  build:
    uses: Drakknar/ci-workflows/.github/workflows/image.yml@<full commit sha> # main
    permissions:
      contents: read
      packages: write
    with:
      test_command: npm ci --no-audit --no-fund && npm test
```

A caller's required checks are named after its job, for example `build / test`.
