<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-import-gpg/v7.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-import-gpg/v7.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references in the workflow files use mutable version tags instead of pinned 40-character SHA commit hashes, making the workflows vulnerable to supply-chain attacks if a tag is moved or a dependency is compromised.

.github/workflows/ci.yml: actions/checkout@v6 (×3), actions/github-script@v8 (×5)
.github/workflows/labels.yml: actions/checkout@v6, crazy-max/ghaction-github-labeler@v5
.github/workflows/test.yml: actions/checkout@v6, docker/bake-action@v6, codecov/codecov-action@v5
.github/workflows/validate.yml: actions/checkout@v6, docker/bake-action/subaction/list-targets@v6, docker/bake-action@v6

Locations:

- `.github/workflows/ci.yml:37`
- `.github/workflows/ci.yml:40`
- `.github/workflows/ci.yml:52`
- `.github/workflows/ci.yml:82`
- `.github/workflows/ci.yml:85`
- `.github/workflows/ci.yml:120`
- `.github/workflows/ci.yml:123`
- `.github/workflows/ci.yml:138`
- `.github/workflows/labels.yml:37`
- `.github/workflows/labels.yml:41`
- `.github/workflows/test.yml:22`
- `.github/workflows/test.yml:25`
- `.github/workflows/test.yml:29`
- `.github/workflows/validate.yml:27`
- `.github/workflows/validate.yml:31`
- `.github/workflows/validate.yml:49`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all 16 unpinned `uses:` references across 4 workflow files to full 40-character commit SHAs:
- actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803 (used in ci.yml ×3, labels.yml, test.yml, validate.yml)
- actions/github-script@v8 → @ed597411d8f924073f98dfc5c65a23a2325f34cd (used in ci.yml ×5)
- crazy-max/ghaction-github-labeler@v5 → @24d110aa46a59976b8a7f35518cb7f14f434c916 (labels.yml)
- docker/bake-action@v6 → @5be5f02ff8819ecd3092ea6b2e6261c31774f2b4 (test.yml, validate.yml ×2)
- docker/bake-action/subaction/list-targets@v6 → @5be5f02ff8819ecd3092ea6b2e6261c31774f2b4 (validate.yml)
- codecov/codecov-action@v5 → @0fb7174895f61a3b6b78fc075e0cd60383518dac (test.yml)
All original tags preserved as inline comments for readability.

