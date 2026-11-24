# Oxo Operator Plugins

Public distribution repository for Oxo Operator's security plugin packages.

## Contents

- `plugins.json` — the release manifest: plugin version, package path, archive SHA-256/size, and the package tree SHA-256/size that Oxo verifies after extraction.
- `packages/<plugin>/<version>/package.zip` — the plugin package itself (manifest, skill, assets). No provider binaries are included; Trivy and Semgrep runtimes are installed by Oxo from their own pinned upstream distribution.

## Integrity

Oxo verifies both the downloaded archive SHA-256 and the extracted package tree digest before installing. A mirror (for example Gitee or an object-storage/CDN copy) can serve the same bytes because verification is independent of the host.

## Pro entitlement

This repository is public so plugin packages can be mirrored and inspected. **Downloading a package does not install it**: Oxo still enforces the Pro security entitlement in the application before a security plugin can be installed or enabled.

## Layout

The main branch carries the current package for each plugin listed in `plugins.json`. Git history preserves previous snapshots. GitHub Release assets remain available for clients that pin a version.

```text
plugins.json
packages/
  cvss-assistant/0.1.1-oxo.1/package.zip
  risk-scanner/0.9.8-oxo.1/package.zip
  semgrep/1.2.0/package.zip
  trivy/1.0.0/package.zip
```

## CVSS Assistant

Assess vulnerabilities with CVSS 4.0. AI proposes metric selections and explains the supporting facts or assumptions; the pinned FIRST reference implementation calculates the score. Change metrics in an interactive report to immediately update the score and vector, while preserving the original AI assessment. Supports Base, Threat, Environmental and Supplemental metrics. Reports follow your conversation language, with inline HTML first and standalone HTML fallback. No vulnerability exploitation, target execution or remote scoring service. Requires an existing trusted Node.js runtime; no npm runtime dependencies are installed.

[cvss-assistant 0.1.1-oxo.1 package](packages/cvss-assistant/0.1.1-oxo.1/package.zip).

## Risk Scanner

Review Skills, MCP tools, and plugins with traceable source evidence.

Separate declared capabilities, exposure, supply-chain controls, integrity concerns, and validated data/execution paths. Reports show the scope and supporting evidence without treating powerful legitimate features as proof of maliciousness.

Supports local Skill archives, captured MCP tool metadata, and plugin ZIP packages. Unsupported components remain explicit. Scanned code and hooks are never executed. Reports follow your conversation language.

[risk-scanner 0.9.8-oxo.1 package](packages/risk-scanner/0.9.8-oxo.1/package.zip).
