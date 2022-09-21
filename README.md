# pnpm-syncpack

Minimalist example of a `pnpm` monorepo using [workspace protocol (`workspace:`)](https://pnpm.io/workspaces#workspace-protocol-workspace) and [syncpack](https://github.com/JamieMason/syncpack) to verify the versions are matching.

UPDATE: issue is **NOW RESOLVED**.

This repo was created with the only purpose to submit [this](https://github.com/JamieMason/syncpack/issues/95) issue (see [JamieMason/syncpack/issues/95](https://github.com/JamieMason/syncpack/issues/95)) in [syncpack](https://github.com/JamieMason/syncpack) repo.

## Prerequisites

- [pnpm](https://pnpm.io/installation) (on MacOS we recommend `brew install pnpm`)
- [syncpack](https://www.npmjs.com/package/syncpack): `npm install --global syncpack`

## Error

The error was about using the pnpm workspace protocol (`workspace:`).

<details>
  <summary>How to reproduce the error</summary>

To see the error when using `workspace:*` as the version for locally developed packages.

1. Set workspace to true in [.syncpackrc.yaml](.syncpackrc.yaml)

```yaml
workspace: true
```

> This is actually the default configurations.

2. Run

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

</details>

<br/>

### Fixing the error

To use pnpm workspace protocol (`workspace:`) with syncpack (as of today 2022/09/21).

You just have to set the `workspace` option to `false`. This can be done in the config file, like the [.syncpackrc.yaml](.syncpackrc.yaml) of this repo (see other options for config file in the [doc](https://github.com/JamieMason/syncpack#-configuration-file)).

```yaml
workspace: false
```
