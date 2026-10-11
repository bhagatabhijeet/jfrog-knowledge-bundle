---
type: Concept
title: "Build once, promote everywhere"
description: Releasing by promoting one immutable binary across repositories, not rebuilding it for each stage.
tags: [artifactory, introduction, promotion, release]
status: draft
generated:
  by: claude-code/opus-5.5
  at: 2026-10-11T00:00:00+00:00
stale_after: 2027-04-10T00:00:00+00:00
---

> [!TIP]
> **In one line:** Build the binary one time, then move that exact binary from repository to repository. Never rebuild it for a later stage.

Build once, promote everywhere is the release approach Artifactory is built around: a binary is built a single time, and that same immutable binary is then promoted from one repository to the next.

![Identical packages loaded onto trains at an export dock](/assets/images/jfrog-introduction/build-once-promote-everywhere.png)

```mermaid
flowchart LR
    B["Build once"] --> R1[("Repository 1<br/>e.g. dev")]
    R1 -->|"promote"| R2[("Repository 2<br/>e.g. qa")]
    R2 -->|"promote"| R3[("Repository 3<br/>e.g. prod")]
    R3 --> REL["Release"]
    N["Same immutable binary at every step"] -.- R2
```

# The idea

| Term | Meaning here |
|---|---|
| Build once | The binary is produced by one build, not rebuilt for each stage. |
| Immutable | The binary does not change after it is built. |
| Promote | The same binary moves across repositories as it advances towards release. |

# Why it matters

- It accelerates software delivery and releases.
- What gets released is the very binary that was built, which addresses the inconsistent builds described in [artifact sprawl](/jfrog-introduction/artifact-sprawl.md).

# Related

- [What JFrog Artifactory is](/jfrog-introduction/what-is-artifactory.md)

---

⬅️ [What JFrog Artifactory is](/jfrog-introduction/what-is-artifactory.md) · 📚 [Topic index](/jfrog-introduction/index.md) · [Universal package support and the single source of truth](/jfrog-introduction/universal-package-support.md) ➡️
