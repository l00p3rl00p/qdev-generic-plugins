<div align="center">

# QDev Generic Plugins

**Reusable plugin packaging and repository conventions.**

A starting point for independently developed plugins, with a standard README presentation and a strict, reusable source-to-artifact verification workflow.

[![Platform](https://img.shields.io/badge/Platform-Plugin_Development-FF1744?style=flat-square)](https://github.com/l00p3rl00p/qdev-generic-plugins) [![Code](https://img.shields.io/badge/Code-Verified_Artifacts-00D6C2?style=flat-square)](.github/workflows/strict-plugin-package.yml) [![Workflow](https://img.shields.io/badge/Packaging-GitHub_Actions-8B5CF6?style=flat-square&logo=githubactions&logoColor=white)](.github/workflows/strict-plugin-package.yml)

**Explore the project**

[![Getting started](https://img.shields.io/badge/Getting_Started-EAF2EF?style=for-the-badge&labelColor=EAF2EF)](#getting-started)
[![README template](https://img.shields.io/badge/README_Template-233C40?style=for-the-badge)](README.template.md)
[![Packaging](https://img.shields.io/badge/Packaging-233C40?style=for-the-badge)](#strict-packaging)
[![Contributing](https://img.shields.io/badge/Contributing-233C40?style=for-the-badge)](CONTRIBUTING.md)
[![Attribution](https://img.shields.io/badge/Attribution-233C40?style=for-the-badge)](ATTRIBUTION.md)

</div>

---

## What this repository provides

- **[README.template.md](README.template.md):** a copy of the official shared presentation template, with static bright Platform and Code badges, optional topic accents and subdued navigation.
- **[Strict plugin packaging](.github/workflows/strict-plugin-package.yml):** a generic reusable GitHub Actions gate for a native DSH Web plugin. It validates a committed package and frozen lockfile, runs its verification, checks its Host/browser entrypoints, packs, checks SHA-256 and commit provenance, installs the exact archive into a clean official DSH profile, and uploads all three release artifacts.
- **[Contributor guidance](CONTRIBUTING.md):** how to adopt the template and require package checks without interfering with running plugins.

This is a **template/catalog repository**, not an installable DSH plugin. No plugin source or default release artifact is claimed.

## Getting started

Copy the README template into a real plugin repository and replace its placeholders with verified project information. Keep the existing project-specific documentation and select only real navigation links.

To adopt the strict packaging workflow, copy `.github/workflows/strict-plugin-package.yml` to the plugin repository, then invoke it using its declared `workflow_call` inputs, including the plugin path and exact package name. Alternatively trigger it manually after source and lockfile are committed. It intentionally has **no automatic push job in this empty template repository**: without a real plugin it must not report package validation as passing.

## Strict packaging

For native DSH Web plugins, the release gate is:

**Test → Commit → Package → Verify SHA-256 → Clean-profile install → Publish provenance.**

The workflow uses Node.js 24, pnpm 10, frozen lockfiles, a real package `verify` script, Host/client loader checks, checksum verification before and after clean-profile installation and versioned artifact publication. It rejects missing manifests, lockfiles, browser entrypoints and package files. DSH version is an explicit workflow input, not an assumed universal compatibility guarantee.

Installed Web UI behavior, clickable controls, saved settings and real session outcomes require **separate live acceptance**; clean-profile registration alone cannot prove them.

## Project reference

| Question | Source |
| --- | --- |
| Where is the design template? | [README template](README.template.md) |
| What validates installable packages? | [Strict packaging workflow](.github/workflows/strict-plugin-package.yml) |
| How should projects adopt this? | [Contributing](CONTRIBUTING.md) |
| Whose conventions are these? | [Attribution](ATTRIBUTION.md) |
| Where is the reusable ACC-specific pipeline? | [Git Shared Workflows](https://github.com/l00p3rl00p/git-shared-workflows) |

<div align="center"><sub>Quatrus: Trust Intelligence · Govern Intelligently · Preserve Intent</sub></div>
