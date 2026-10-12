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
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#B9F6CA','primaryBorderColor':'#00C853','primaryTextColor':'#06210F','lineColor':'#00B8D4','secondaryColor':'#B3E5FC','tertiaryColor':'#E8F5E9','noteBkgColor':'#FFE57F','noteTextColor':'#2B1B00','noteBorderColor':'#FFAB00'}}}%%
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
| 🔨 **Build once** | The binary is produced by one build, not rebuilt for each stage. |
| 🔒 **Immutable** | The binary does not change after it is built. |
| 🚀 **Promote** | The same binary moves across repositories as it advances toward release. |

# Why it matters

- It accelerates software delivery and releases.
- What gets released is the very binary that was built, which addresses the inconsistent builds described in [artifact sprawl](/jfrog-introduction/artifact-sprawl.md).

# Rebuild or promote?

| | ❌ Rebuild for each stage | ✅ Build once, promote |
|---|---|---|
| What reaches production | A *new* binary, built later | The *same* binary that passed testing |
| Can stages differ? | Yes. A dependency may have changed in between | No. It is byte-for-byte identical |
| Speed | A full build every time | A move between repositories |
| "What did we ship?" | Hard to prove | The binary and its checksum answer it |

# What it looks like in practice

A team usually keeps one repository per stage, and a release walks through them.

| Stage | Repository (example) | Who can write |
|---|---|---|
| 🌱 Development | `payments-maven-dev-local` | Developers and CI |
| 🧪 Testing | `payments-maven-qa-local` | The promotion step only |
| 🏭 Production | `payments-maven-prod-local` | Release managers only |

The repository names follow the [naming conventions](/repository-management/repository-naming-conventions.md). The stages are a common pattern, not a rule.

> [!NOTE]
> **Promotion is cheap.** Artifactory stores each binary once and keeps paths in a database, so moving a binary between repositories does not copy the file. See [checksum-based storage](/jfrog-introduction/checksum-based-storage.md).

# Related

- [Builds: the logbook of your CI](/artifactory-views/builds.md) - promotion works on a published build.
- [Checksum-based storage](/jfrog-introduction/checksum-based-storage.md) - why promoting costs almost nothing.
- [Artifact sprawl](/jfrog-introduction/artifact-sprawl.md) - the inconsistent builds this approach removes.
- [What JFrog Artifactory is](/jfrog-introduction/what-is-artifactory.md)

---

⬅️ [Remote repositories: proxying and caching open source dependencies](/jfrog-introduction/remote-repositories.md) · 📚 [Chapter 01 index](/jfrog-introduction/index.md) · [Checksum-based storage: how Artifactory keeps binaries](/jfrog-introduction/checksum-based-storage.md) ➡️
