<a href="https://github.com/polyseam/mac-bin-build-demo/actions/workflows/bin-build.yaml">
    <img src="https://github.com/polyseam/mac-bin-build-demo/actions/workflows/main-latest.yaml/badge.svg" alt="main" style="max-width: 100%;">
</a>

# rate-limit issue repro

This repo reproduces an issue with the rate-limiting of the GitHub API.

The issue is centered around the program
[polyseam/cndi](https://github.com/polyseam/cndi). When any `cndi` command is
invoked, the CLI checks if there is a newer version available on GitHub
Releases.

This check always succeeds except specifically when ran within a GitHub runner
where it fails with a rate-limit error, most commonly on macOS runners.

My best guess is that this is a result of the macOS runners being shared and the
rate-limit being shared across all users of the runner, specifically limited by
IP Address.

## Table of Failures

| Timestamp                 | OS |
| ------------------------- | -- |
| 2024-06-05T21:14:11+00:00 | ?  |
