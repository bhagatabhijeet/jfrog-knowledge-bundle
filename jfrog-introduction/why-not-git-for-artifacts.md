---
type: Concept
title: "Why not Git for artifacts? Why Artifactory?"
description: Why a version control system is the wrong place to keep build artifacts, and what an artifact repository manager like Artifactory does that Git cannot.
tags: [artifactory, introduction, git, version-control, binary-repository, fundamentals]
status: draft
sources:
  - id: jfrog-git-lfs-blog
    resource: https://jfrog.com/blog/use-the-right-tool-for-the-job-git-lfs-with-artifactory/
    title: "JFrog Blog - Use the right tool for the job: Git LFS with Artifactory"
    author: team:jfrog
    last_modified: 2015-07-15T00:00:00+00:00
generated:
  by: claude-code/opus-5.5
  at: 2026-10-11T00:00:00+00:00
stale_after: 2027-04-11T00:00:00+00:00
---

> [!TIP]
> **In one line:** Git is a time machine for the code you write. Artifactory is a warehouse for the things you build. You need both.

"We already have Git. Why not just commit the [artifacts](/jfrog-introduction/what-is-an-artifact.md) there?" It is the most natural question a team asks, and the answer is that Git was built for a different job.

![Git versus Artifactory, side by side: Git is built for source code, Artifactory is built for artifacts](/assets/images/jfrog-introduction/git-and-artifactory.svg)

# Git is brilliant at source code

Git tracks text, line by line. It shows who changed what, lets many people edit at once, and merges their work. None of that helps with a compiled binary: nobody reads it, diffs it or merges it.

# Where Git falls short for artifacts

| # | The problem | Why it hurts |
|:-:|---|---|
| 1 | 🚫 **A version control system is not a repository.** | It cannot build server-side indexes or offer the dynamic APIs that package tools rely on, such as dependency resolution.[^jfrog-git-lfs-blog] Maven, npm, pip and Docker cannot pull packages from it the way they do from a registry. |
| 2 | 🔀 **It versions the wrong way.** | Source is tracked by content. Binaries are identified by name and version, so to Git each new build is just an unrelated new file.[^jfrog-git-lfs-blog] |
| 3 | 🔎 **It searches the wrong way.** | You look for a binary by its metadata, location, file name and what is inside the archive, not by lines of text.[^jfrog-git-lfs-blog] |
| 4 | 🐘 **The repository balloons.** | Git keeps every version of every file forever, and a clone brings the whole history with it. Commit binaries on every build and cloning gets slower for everyone. |
| 5 | 🕵️ **No release story.** | Git has no notion of promoting a build from one stage to the next, or of the metadata that proves what went into it. |

> [!WARNING]
> **What about Git LFS?** Git LFS keeps only a small text pointer in the repository and stores the large file somewhere else.[^jfrog-git-lfs-blog] That fixes the size problem, but the files still need a proper home, and Git still cannot serve packages to your build tools. Artifactory can be that home: it supports Git LFS repositories.[^jfrog-git-lfs-blog]

# Why Artifactory

Artifactory is built for exactly the job Git was not.

| What you need | How Artifactory answers it | Read more |
|---|---|---|
| 🏠 One home for every binary | A single organized store that every build uploads to | [What JFrog Artifactory is](/jfrog-introduction/what-is-artifactory.md) |
| 🧰 Works with your build tools | Handles over 40 package types in one system | [Universal package support](/jfrog-introduction/universal-package-support.md) |
| ⚡ Fast, dependable dependencies | Proxies and caches open source packages | [Remote repositories](/jfrog-introduction/remote-repositories.md) |
| 🚀 Safe releases | Promotes one immutable binary from stage to stage | [Build once, promote everywhere](/jfrog-introduction/build-once-promote-everywhere.md) |
| 🛡️ Security and audit trail | Build metadata, SBOM and traceability with Xray | [Supply chain security](/jfrog-introduction/supply-chain-security.md) |
| 🔐 Controlled access | Permissions and roles for users, groups and tokens | [Access management](/jfrog-introduction/access-management.md) |
| 🌍 Teams in many places | The same artifacts at every site | [Deployment options and federation](/jfrog-introduction/deployment-and-federation.md) |

# Use both, side by side

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#B9F6CA','primaryBorderColor':'#00C853','primaryTextColor':'#06210F','lineColor':'#00B8D4','secondaryColor':'#B3E5FC','tertiaryColor':'#E8F5E9','noteBkgColor':'#FFE57F','noteTextColor':'#2B1B00','noteBorderColor':'#FFAB00'}}}%%
flowchart LR
    D["👩‍💻 Developer"] -->|"commit source"| G[("Git<br/>source code")]
    G -->|"checkout"| B["⚙️ Build"]
    AF -->|"dependencies"| B
    B -->|"upload artifact"| AF[("Artifactory<br/>artifacts")]
    AF -->|"deploy"| P["🚀 Environments"]
```

| Keep in Git | Keep in Artifactory |
|---|---|
| Source code | Build outputs: `.jar`, `.whl`, `.dll`, `.tar.gz` |
| Build scripts and configuration as code | Container images and other packages |
| Documentation you edit by hand | Cached copies of third-party dependencies |

> [!NOTE]
> **The rule of thumb:** if a person wrote it, it goes in Git. If a build produced it, it goes in Artifactory.

# Related

- [What is an artifact repository?](/jfrog-introduction/what-is-an-artifact-repository.md)
- [Artifact sprawl: the problem Artifactory solves](/jfrog-introduction/artifact-sprawl.md) - the team in that story kept everything in Git and shared folders.

[^jfrog-git-lfs-blog]: JFrog Blog, "Use the right tool for the job: Git LFS with Artifactory".

---

⬅️ [Artifact sprawl: the problem Artifactory solves](/jfrog-introduction/artifact-sprawl.md) · 📚 [Chapter 01 index](/jfrog-introduction/index.md) · [What JFrog Artifactory is](/jfrog-introduction/what-is-artifactory.md) ➡️
