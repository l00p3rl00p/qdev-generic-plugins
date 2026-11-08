# Contributing and template adoption

This repository holds **templates**, not a runnable native DSH plugin.

## README presentation

Copy [README.template.md](README.template.md) from this repository into a plugin's README and fill in only verified repository facts. Preserve the existing project body, actual operating instructions and links. Apply fixed vivid red (`FF1744`) to Platform/Harness and bright teal (`00D6C2`) to Code/Technology, choose other accent colors based on actual project importance, and retain subdued light Getting Started / dark teal Explore navigation.

## Strict packaging

Copy or invoke [the strict native DSH workflow](.github/workflows/strict-plugin-package.yml). It accepts `plugin_path`, `package_name` and `dsh_version` as **required inputs** and intentionally has no runnable default package. This pipeline only applies to native DSH Web plugins with a valid `package.json`, `pnpm-lock.yaml`, `cordis.patch.yml`, built Host and browser entrypoints, and `pnpm run verify`.

The package must pass **Test → Commit → Package → Verify SHA-256 → Clean-profile install → Publish provenance**, using the same committed source revision, verified release archive and official clean DSH profile. Do not skip failures, silently resolve lockfiles in release jobs, treat an artifact upload as successful installation, or claim that clean-profile registration proves the live Web UI works.

A consuming plugin repository can add a short trigger workflow:

```yaml
name: Verify plugin release
on: [push, pull_request, workflow_dispatch]
permissions:
  contents: read
jobs:
  strict:
    uses: ./.github/workflows/strict-plugin-package.yml
    with:
      plugin_path: "."
      package_name: "REPLACE-WITH-REAL-PACKAGE-NAME"
      dsh_version: "REPLACE-WITH-SUPPORTED-DSH-VERSION"
```

Only use the trigger after replacing values based on that package's actual manifest and tested DSH compatibility. Verify real browser mounting, control activation, session outcomes and saved configuration separately in the running target environment.

## Scope

A plugin that is not native DSH Web needs its **own appropriate packaging adapter** while retaining the same general strictness. Do not falsely run DSH profile installation against an unrelated generic plugin. Other workflows and the README color conventions are maintained at [Git Shared Workflows](https://github.com/l00p3rl00p/git-shared-workflows).
