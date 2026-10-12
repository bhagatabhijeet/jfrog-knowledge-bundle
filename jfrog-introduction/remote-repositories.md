---
type: Concept
title: "Remote repositories: proxying and caching open source dependencies"
description: How Artifactory remote repositories proxy and cache external OSS dependencies, and what that gains a team.
tags: [artifactory, introduction, remote-repositories, oss, caching]
status: draft
generated:
  by: claude-code/opus-5.5
  at: 2026-10-11T00:00:00+00:00
stale_after: 2027-04-10T00:00:00+00:00
---

> [!TIP]
> **In one line:** A remote repository keeps a local copy of the open source packages you use, so builds are faster and keep working when the public source is down.

A remote repository in Artifactory proxies and caches external open source (OSS) dependencies. Builds ask Artifactory for a dependency, and Artifactory serves it from its cache.

![Artifactory in the center, with remote repositories caching external OSS dependencies](/assets/images/jfrog-introduction/remote-repository-cache.png)

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#B9F6CA','primaryBorderColor':'#00C853','primaryTextColor':'#06210F','lineColor':'#00B8D4','secondaryColor':'#B3E5FC','tertiaryColor':'#E8F5E9','noteBkgColor':'#FFE57F','noteTextColor':'#2B1B00','noteBorderColor':'#FFAB00'}}}%%
sequenceDiagram
    participant B as Build
    participant A as Artifactory remote repository
    participant P as Public OSS registry
    B->>A: Request a dependency
    A->>P: Fetch it (first time only)
    P-->>A: Package
    Note over A: Stored in the cache
    A-->>B: Package
    B->>A: Request it again
    A-->>B: Served from the cache
```

# Benefits

| Benefit | Why |
|---|---|
| Faster builds | Dependencies come from the cache, which dramatically improves build speed. |
| Lower network latency | Fewer round trips to external sources. |
| Reliable access | A cached package stays available even when the public OSS package becomes unavailable. |

# Related

- [Universal package support](/jfrog-introduction/universal-package-support.md) - the single source of truth these cached packages feed.
- [What JFrog Artifactory is](/jfrog-introduction/what-is-artifactory.md)

---

⬅️ [Universal package support and the single source of truth](/jfrog-introduction/universal-package-support.md) · 📚 [Topic index](/jfrog-introduction/index.md) · [Deployment options and federation](/jfrog-introduction/deployment-and-federation.md) ➡️
