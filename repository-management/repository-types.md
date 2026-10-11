---
type: Concept
title: "Repository types in Artifactory"
description: The four repository types Artifactory hosts (local, remote, virtual, federated) and what each is for.
tags: [artifactory, repositories, repository-types]
status: draft
sources:
  - id: docs-repo-mgmt
    resource: https://docs.jfrog.com/artifactory/docs/repository-management
    title: "JFrog Artifactory documentation - Repository Management"
    author: team:jfrog-docs
generated:
  by: claude-code/opus-5.5
  at: 2026-10-11T00:00:00+00:00
stale_after: 2027-04-10T00:00:00+00:00
---

> [!TIP]
> **In one line:** Local holds what you build, remote caches what you depend on, virtual puts both behind one URL, and federated keeps sites in sync.

In Artifactory, a repository is a place to organize artifacts into a cohesive group by application and project. Artifactory hosts four repository types.[^docs-repo-mgmt]

```mermaid
flowchart LR
    DEV["Developers and CI"] --> V{{"Virtual repository<br/>one URL"}}
    V -->|"1. look here first"| L[("Local repository<br/>what you build")]
    V -->|"2. then here"| R[("Remote repository<br/>cache of dependencies")]
    R -->|"on demand"| PUB["Public registry"]
    L <-->|"federated sync"| L2[("Federated repository<br/>at another site")]
```

# The four types

| Type | What it holds | Typical use |
|---|---|---|
| [Local](/repository-management/local-repositories.md) | Artifacts your organization uploads or creates itself | Build outputs, binaries and other packages you generate |
| [Remote](/repository-management/remote-repositories.md) | A cache of artifacts proxied from a remote URL, such as a public registry | Your project's external dependencies |
| [Virtual](/repository-management/virtual-repositories.md) | Nothing of its own: it aggregates local and remote repositories | One controlled entry point for searching and resolving artifacts |
| Federated | Contents synchronized with other federated repositories at remote sites in the same Federation | Sharing the same artifacts across sites |

# How they fit together

- **Local** is where what you build goes in.
- **Remote** is where what you depend on comes in from outside.
- **Virtual** sits in front of both, so tools talk to a single URL.
- **Federated** keeps repositories at different sites in step with each other.

A [Smart Remote repository](/repository-management/smart-remote-repositories.md) is a remote repository whose upstream is another Artifactory instance.

# One more type, by subscription

With an Enterprise+ subscription and JFrog Distribution, there are also Release Bundle repositories. They collect a signed group of artifacts and protect them from changes, so distribution to targets is consistent.[^docs-repo-mgmt]

# Related

- [Repository naming conventions](/repository-management/repository-naming-conventions.md)
- [Deployment options and federation](/jfrog-introduction/deployment-and-federation.md) - the introduction-level view of federation.

[^docs-repo-mgmt]: JFrog Artifactory documentation - Repository Management.

---

📚 [Topic index](/repository-management/index.md) · [Local repositories](/repository-management/local-repositories.md) ➡️
