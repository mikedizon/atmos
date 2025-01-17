---
title: atmos describe stacks
sidebar_label: stacks
sidebar_class_name: command
id: stacks
description: Use this command to show the fully deep-merged configuration for all stacks and the components in the stacks.
---

:::note Purpose
Use this command to show the fully deep-merged configuration for all stacks and the components in the stacks.
:::

## Usage

Execute the `describe stacks` command like this:

```shell
atmos describe stacks [options]
```

This command shows configuration for stacks and components in the stacks.

:::tip
Run `atmos describe stacks --help` to see all the available options
:::

## Examples

```shell
atmos describe stacks
atmos describe stacks -s tenant1-ue2-dev
atmos describe stacks --file=stacks.yaml
atmos describe stacks --file=stacks.json --format=json
atmos describe stacks --components=infra/vpc
atmos describe stacks --components=echo-server,infra/vpc
atmos describe stacks --components=echo-server,infra/vpc --sections=none
atmos describe stacks --components=echo-server,infra/vpc --sections=none
atmos describe stacks --components=none --sections=metadata
atmos describe stacks --components=echo-server,infra/vpc --sections=vars,settings,metadata
atmos describe stacks --components=test/test-component-override-3 --sections=vars,settings,component,deps,inheritance --file=stacks.yaml
atmos describe stacks --components=test/test-component-override-3 --sections=vars,settings --format=json --file=stacks.json
atmos describe stacks --components=test/test-component-override-3 --sections=deps,vars -s=tenant2-ue2-staging
```

:::tip
Use `jq` to filter the output.
:::

## Flags

| Flag                | Description                                                                                                                                                                                                                          | Alias | Required |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------|:---------|
| `--stack`           | Filter by a specific stack.<br/>Supports names of the top-level stack config files (including subfolder paths),<br/>and Atmos stack names (derived from the context vars)                                                            | `-s`  | no       |
| `--file`            | If specified, write the result to the file                                                                                                                                                                                           |       | no       |
| `--format`          | Specify the output format: `yaml` or `json` (`yaml` is default)                                                                                                                                                                      |       | no       |
| `--components`      | Filter by specific Atmos components<br/>(comma-separated string of component names)                                                                                                                                                  |       | no       |
| `--component-types` | Filter by specific component types: `terraform` or `helmfile`                                                                                                                                                                        |       | no       |
| `--sections`        | Output only the specified component sections.<br/>Available component sections: `backend`, `backend_type`, `deps`, `env`,<br/>`inheritance`, `metadata`, `remote_state_backend`,<br/>`remote_state_backend_type`, `settings`, `vars` |       | no       |
