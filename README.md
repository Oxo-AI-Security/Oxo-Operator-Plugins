# Oxo Operator Plugins

Public distribution repository for Oxo Operator's security plugin packages.

## Contents

- `plugins.json` — the release manifest: plugin version, package path, archive SHA-256/size, and the package tree SHA-256/size that Oxo verifies after extraction.
- `packages/<plugin>/<version>/package.zip` — the plugin package itself (manifest, skill, assets). No provider binaries are included; Trivy, Semgrep and Nuclei runtimes are installed by Oxo from their own pinned upstream distribution.

## Integrity

Oxo verifies both the downloaded archive SHA-256 and the extracted package tree digest before installing. A mirror (for example Gitee or an object-storage/CDN copy) can serve the same bytes because verification is independent of the host.

## Pro entitlement

This repository is public so plugin packages can be mirrored and inspected. **Downloading a package does not install it**: Oxo still enforces the Pro security entitlement in the application before a security plugin can be installed or enabled.

## Layout

```text
plugins.json
packages/
  nuclei/1.0.0/package.zip
  semgrep/1.2.0/package.zip
  trivy/1.0.0/package.zip
```
