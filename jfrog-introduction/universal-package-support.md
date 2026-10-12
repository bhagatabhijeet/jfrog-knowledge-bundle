---
type: Concept
title: "Universal package support and the single source of truth"
description: Why one repository manager that handles over 40 package types replaces a separate tool per technology.
tags: [artifactory, introduction, package-types, single-source-of-truth]
status: draft
generated:
  by: claude-code/opus-5.5
  at: 2026-10-11T00:00:00+00:00
stale_after: 2027-04-10T00:00:00+00:00
---

> [!TIP]
> **In one line:** One repository manager for every package type means one place to look, for every technology.

Artifactory handles over 40 types of packages. A team therefore does not need a different solution for each technology or tool: everything is managed in one system.

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#B9F6CA','primaryBorderColor':'#00C853','primaryTextColor':'#06210F','lineColor':'#00B8D4','secondaryColor':'#B3E5FC','tertiaryColor':'#E8F5E9','noteBkgColor':'#FFE57F','noteTextColor':'#2B1B00','noteBorderColor':'#FFAB00'}}}%%
flowchart LR
    T1["Docker"] --> AF
    T2["npm"] --> AF
    T3["Maven"] --> AF
    T4["PyPI"] --> AF
    T5["...and 40+ package types in all"] --> AF
    AF[("Artifactory:<br/>single source of truth")] --> TEAM["Every team, every tool"]
```

# Single source of truth

Because every package type lives in the same place, a company can rely on Artifactory as its single source of truth for all open source packages. Packages are kept organized and available for further use.

![Many package types arranged around a single source of truth badge](/assets/images/jfrog-introduction/single-source-of-truth.png)

# What changes for the team

| ❌ Without it | ✅ With it |
|---|---|
| A separate store or tool per technology | One system for all package types |
| Packages scattered and hard to find | Packages organized and ready for reuse |
| No agreed place to look | One source of truth |

# A few of the package types

| Ecosystem | Package type | What it looks like |
|---|---|---|
| ☕ Java | Maven, Gradle | `.jar`, `.war` |
| 🟩 JavaScript | npm | `.tgz` packages |
| 🐍 Python | PyPI | `.whl` wheels |
| 🟦 .NET | NuGet | `.nupkg` packages |
| 🐳 Containers | Docker | Images and tags |
| ⎈ Kubernetes | Helm | Charts |
| 📁 Anything else | Generic | Any file at all |

These are examples. The full list is much longer.

> [!IMPORTANT]
> **One system does not mean one repository.** Each repository holds a single package type, chosen when it is created. See [why the package type matters](/repository-management/why-package-type-matters.md).

# Related

- [Why the package type matters](/repository-management/why-package-type-matters.md)
- [Packages: the catalog of everything you hold](/artifactory-views/packages.md) - where you browse them all.
- [Remote repositories](/jfrog-introduction/remote-repositories.md) - how external open source packages get into that single source.
- [What JFrog Artifactory is](/jfrog-introduction/what-is-artifactory.md)

---

⬅️ [Build once, promote everywhere](/jfrog-introduction/build-once-promote-everywhere.md) · 📚 [Topic index](/jfrog-introduction/index.md) · [Remote repositories: proxying and caching open source dependencies](/jfrog-introduction/remote-repositories.md) ➡️
