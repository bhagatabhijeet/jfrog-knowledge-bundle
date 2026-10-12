---
type: Concept
title: "Packages, Builds, Artifacts: which is which?"
description: "The three Artifactory views compared - Packages is a catalog, Builds is a logbook, Artifacts is a file explorer - and how to choose between them."
tags: [artifactory, packages, builds, artifacts, fundamentals]
status: draft
sources:
  - id: docs-objects
    resource: https://docs.jfrog.com/artifactory/docs/understanding-artifacts-and-packages
    title: "JFrog documentation - Understand Artifacts and Packages"
    author: team:jfrog-docs
  - id: docs-packages
    resource: https://docs.jfrog.com/artifactory/docs/viewing-packages
    title: "JFrog documentation - Viewing Packages"
    author: team:jfrog-docs
generated:
  by: claude-code/opus-5.5
  at: 2026-10-11T00:00:00+00:00
stale_after: 2027-04-11T00:00:00+00:00
---

> [!TIP]
> **In one line:** Packages tells you *what you have*, Builds tells you *who made it*, Artifacts shows you *where the file is*.

Under **Artifactory** in the left menu sit three entries that newcomers constantly mix up. They are not three different stores. They are three windows onto the same software.

![Packages, Builds and Artifacts compared: a catalog, a logbook and a file explorer](/assets/images/artifactory-views/three-windows.svg)

# The four things Artifactory keeps

Artifactory manages a handful of object types. Three of them have their own menu entry.[^docs-objects]

| Object | JFrog's definition | Menu entry |
|---|---|---|
| 📄 **Artifact** | Any stand-alone file in Artifactory, identified by a unique checksum | [Artifacts](/artifactory-views/artifacts.md) |
| 📦 **Package** | The name as defined in package metadata, such as `package.json` for npm or `manifest.json` for Docker | [Packages](/artifactory-views/packages.md) |
| 🏗️ **Build** | An output that represents the build step of CI, with details of the method and dependencies involved | [Builds](/artifactory-views/builds.md) |
| 🎁 **Release Bundle** | An immutable set of content that represents a release candidate | Release Lifecycle |

# How they relate

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#B2EBF2','primaryBorderColor':'#00B8D4','primaryTextColor':'#00222A','lineColor':'#FF8A00','secondaryColor':'#C8E6C9','tertiaryColor':'#E0F7FA','noteBkgColor':'#FFE57F','noteTextColor':'#2B1B00','noteBorderColor':'#FFAB00'}}}%%
flowchart LR
    B["🏗️ Build<br/>payments-api #142"] -->|"produced"| A1["📄 payments-api-2.3.0.jar"]
    B -->|"produced"| A2["📄 payments-api-2.3.0.pom"]
    A1 --> P["📦 Package<br/>payments-api 2.3.0"]
    A2 --> P
    B -.->|"consumed"| D["📦 spring-core 6.1.4"]
```

| Relationship | In plain words |
|---|---|
| 📦 → 📄 **A package is made of artifacts** | A package can contain a single artifact, or several.[^docs-objects] |
| 🏗️ → 📄 **A build produces artifacts** | The build record lists exactly which files a run created. |
| 🏗️ → 📦 **A build consumes packages** | The same record lists the dependencies the run pulled in. |

# One example, three views

Say your CI builds version 2.3.0 of a service called `payments-api`.

| Open | You see | You can answer |
|---|---|---|
| 📦 **Packages** | `payments-api`, with version `2.3.0` at the top | "Is 2.3.0 out? How do I install it?" |
| 🏗️ **Builds** | `payments-api`, last build ID `142` | "Which run made 2.3.0, and from what?" |
| 📄 **Artifacts** | `pay-maven-dev-local/com/acme/payments-api/2.3.0/payments-api-2.3.0.jar` | "Where exactly is the file, and what is its checksum?" |

# Which one do I open?

| Your question starts with... | Open |
|---|---|
| "Do we have...", "which version of...", "how do I install..." | 📦 [Packages](/artifactory-views/packages.md) |
| "Which build...", "what went into...", "what changed between..." | 🏗️ [Builds](/artifactory-views/builds.md) |
| "Where is the file...", "what is in this repository...", "let me upload..." | 📄 [Artifacts](/artifactory-views/artifacts.md) |

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#B2EBF2','primaryBorderColor':'#00B8D4','primaryTextColor':'#00222A','lineColor':'#FF8A00','secondaryColor':'#C8E6C9','tertiaryColor':'#E0F7FA','noteBkgColor':'#FFE57F','noteTextColor':'#2B1B00','noteBorderColor':'#FFAB00'}}}%%
flowchart TD
    Q{"What do you know?"}
    Q -->|"A package name"| P["📦 Packages"]
    Q -->|"A build name or number"| B["🏗️ Builds"]
    Q -->|"A repository or a path"| A["📄 Artifacts"]
    P -.->|"Show in Artifacts Tree"| A
    P -.->|"Builds tab"| B
```

> [!NOTE]
> You are never stuck in one view. A package's details link to the builds that made it and to its place in the Artifacts tree.[^docs-packages]

# Who lives where

| Role | Spends most time in |
|---|---|
| 👩‍💻 **Developer** | Packages |
| 🚀 **Release or DevOps engineer** | Builds |
| 🛠️ **Administrator** | Artifacts |

This is a typical pattern, not a rule. Everyone uses all three sooner or later.

# Related

- [A tour of the left menu](/platform-navigation/the-left-menu.md)
- [What is an artifact?](/jfrog-introduction/what-is-an-artifact.md)

[^docs-objects]: JFrog documentation, "Understand Artifacts and Packages".
[^docs-packages]: JFrog documentation, "Viewing Packages".

---

⏮️ [Previous chapter: Projects](/projects/index.md) · 📚 [Chapter 05 index](/artifactory-views/index.md) · [Packages: the catalog of everything you hold](/artifactory-views/packages.md) ➡️
