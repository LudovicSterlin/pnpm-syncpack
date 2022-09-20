# pnpm-syncpack

Minimalist example of [syncpack](https://github.com/JamieMason/syncpack) not working with `pnpm` [workspace protocol (`workspace:`)](https://pnpm.io/workspaces#workspace-protocol-workspace).

This repo was created in with the only purpose to submit an issue in [syncpack](https://github.com/JamieMason/syncpack) repo.

## Prerequisites

- [pnpm](https://pnpm.io/installation) (on MacOS we recommend `brew install pnpm`)
- [syncpack](https://www.npmjs.com/package/syncpack): `npm install --global syncpack`

## Error

To see the error when using `workspace:*` as the version for locally developed packages.

Run

```sh
syncpack list-mismatches
```

You should see the error below

```console
- @pnpm-syncpack/shared: 1.0.0 is developed in this repo at packages/shared/package.json
  workspace:* in dependencies of packages/api/package.json
  workspace:* in devDependencies of packages/app/package.json
  1.0.0 in version of packages/shared/package.json
```
