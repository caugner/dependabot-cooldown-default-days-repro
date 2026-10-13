# Dependabot cooldown default-days reproduction

This repository reproduces a possible side effect in Dependabot's parsed configuration when an npm update entry uses a cooldown exclusion.

## Setup

The npm manifest and lockfile pin `mdn-data` to an outdated version so Dependabot has a version update to inspect. The Dependabot configuration excludes scoped packages matching `@mdn/*` from cooldown.

## Reproduce

1. Enable Dependabot version updates for this repository.
2. Wait for the daily npm update check, or trigger a version update check.
3. Inspect the Dependabot run logs for the parsed configuration, especially the effective `cooldown.default-days` value.

The question is whether setting `cooldown.exclude` to `@mdn/*` changes the effective default cooldown days as a side effect. No `default-days` value is explicitly configured here.
