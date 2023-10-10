# Changelog

## 3.2.0

### Minor Changes

- [#166](https://github.com/cloudflare/wrangler-action/pull/166) [`7d7b988`](https://github.com/cloudflare/wrangler-action/commit/7d7b98826e14e9ad422870a7263b7074b40bf16f) Thanks [@nix6839](https://github.com/nix6839)! - Support for package managers other than npm, such as pnpm and yarn.

  fixes #156

## 3.1.1

### Patch Changes

- [#161](https://github.com/cloudflare/wrangler-action/pull/161) [`e5251df`](https://github.com/cloudflare/wrangler-action/commit/e5251df52154e9ebc98edb02ee0598c7210dcf0f) Thanks [@1000hz](https://github.com/1000hz)! - Refactored error handling to stop execution when action fails. Previously, the action would continue executing to completion if one of the steps encountered an error. Fixes #160.

## 3.1.0

### Minor Changes

- [#154](https://github.com/cloudflare/wrangler-action/pull/154) [`3f40637`](https://github.com/cloudflare/wrangler-action/commit/3f40637a1c48016d2101e412a7a06f1eb4b9c2fd) Thanks [@JacobMGEvans](https://github.com/JacobMGEvans)! - feat: Quiet mode
  Some of the stderr, stdout, info & groupings can be a little noisy for some users and use cases.
  This feature allows for a option to be passed 'quiet: true' this would significantly reduce the noise.

  There will still be output that lets the user know Wrangler Installed and Wrangler Action completed successfully.
  Any failure status will still be output to the user as well, to prevent silent failures.

  resolves #142

## 3.0.2

### Patch Changes

- [#147](https://github.com/cloudflare/wrangler-action/pull/147) [`58f274b`](https://github.com/cloudflare/wrangler-action/commit/58f274b9f70867447519c6fa983c813e2b167b85) Thanks [@JacobMGEvans](https://github.com/JacobMGEvans)! - Added more error logging when a command fails to execute
  Previously, we prevented any error logs from propagating too far to prevent leaking of any potentially sensitive information. However, this made it difficult for developers to debug their code.

  In this release, we have updated our error handling to allow for more error messaging from pre/post and custom commands. We still discourage the use of these commands for secrets or other sensitive information, but we believe this change will make it easier for developers to debug their code.

  Relates to #137

- [#147](https://github.com/cloudflare/wrangler-action/pull/147) [`58f274b`](https://github.com/cloudflare/wrangler-action/commit/58f274b9f70867447519c6fa983c813e2b167b85) Thanks [@JacobMGEvans](https://github.com/JacobMGEvans)! - Adding Changesets

- [Version 3.0.0](#version-300)
- [Version 2.0.0](#version-200)

## Version 3.0.0 (Breaking update)

### Additions

- **Rewritten Wrangler Action in TypeScript.**
- Bulk secrets API utilization from Wrangler.
- Added testing for improved reliability.
- Implemented multiline support for the `command` input to allow running multiple Wrangler commands.
- Now using Node for the Action engine/runner.
- Open discussions with the community on all changes through GitHub Discussions and monitored Issues.

### Removals

- Removed Docker as a dependency.
- Dropped support for Wrangler v1.

### Changes

- Fixed CI/CD issues.

### Breaking changes

- Wrangler v1 is no longer supported.
  - Please update to the latest version of Wrangler.
- Updated default version of Wrangler to v3.4.0

### Additional Notes

- Major Version Default: [DEVX-632](https://jira.cfdata.org/browse/DEVX-632)
- Rewrite Project Tickets: [DEVX-804](https://jira.cfdata.org/browse/DEVX-804), [DEVX-802](https://jira.cfdata.org/browse/DEVX-802), [DEVX-800](https://jira.cfdata.org/browse/DEVX-800), [DEVX-632](https://jira.cfdata.org/browse/DEVX-632)

---

## Version 2.0.0 (Breaking update)

### Additions

- New `command` input
  - This allows you to specify the Wrangler command you would like to run.
    For example, if you want to publish the production version of your Worker you may run `publish --env=production`.
  - This opens up other possibilities too like publishing a Pages project: `pages publish <directory> --project-name=<name>`.
- New `accountId` input
  - This allows you to specify your account ID.

### Removals

- Removed `publish` input (refer to [Breaking changes](#breaking-changes)).

### Changes

-- no changes --

### Breaking changes

- `publish` has been removed.
  - You should instead do `command: