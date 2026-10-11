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

![How the three repository types work together: developers and pipelines use one virtual URL, which checks the local repository first and then the remote, which fetches from the internet](/assets/images/repository-management/repositories-big-picture.svg)

![The three types of Artifactory repositories: local, remote and virtual, with what each one does and what goes in it](/assets/images/repository-management/three-repository-types.svg)

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#FFE0B2','primaryBorderColor':'#FF8A00','primaryTextColor':'#2B1B00','lineColor':'#7C4DFF','secondaryColor':'#E1BEE7','tertiaryColor':'#FFF3E0','noteBkgColor':'#E1BEE7','noteTextColor':'#2A0A3A','noteBorderColor':'#7C4DFF'}}}%%
flowchart LR
    DEV["Developers and CI"] --> V{{"Virtual repository<br/>one URL"}}
    V -->|"1. look here first"| L[("Local repository<br/>what you build")]
    V -->|"2. then here"| R[("Remote repository<br/>cache of dependencies")]
    R -->|"on demand"| PUB["Public registry"]
    L <-->|"federated sync"| L2[("Federated repository<br/>at another site")]
```

# The three you will use every day

Almost everything you do in Artifactory touches one of three repository types. Learn these three and the rest follows.

| | 🟢 Local | 🟠 Remote | 🟣 Virtual |
|---|---|---|---|
| **In one phrase** | Upload = local repository | Proxy + cache for external dependencies | One URL in front of both |
| **Direction** | You push artifacts **in** | It pulls artifacts **in from outside** | It **routes** requests to the others |
| **Holds** | What your organization builds | Cached copies of what you depend on | Nothing of its own |
| **Typical contents** | Your organizational artifacts, internal packages, microservice artifacts, client-specific builds | Packages from Maven Central, the npm registry, PyPI, or another Artifactory instance | A list of local and remote repositories |
| **Can you upload to it?** | ✅ Yes | ❌ No | ↪️ Yes, it forwards to a default local |
| **Who uses it** | CI pipelines publishing builds | Builds resolving third-party dependencies | Every developer and pipeline, as their single address |
| **Deep dive** | [Local repositories](/repository-management/local-repositories.md) | [Remote repositories](/repository-management/remote-repositories.md) | [Virtual repositories](/repository-management/virtual-repositories.md) |

## A picture for each

**🟢 Local: your own shelf.** If your organization made it, it lives here.

![A local repository: builds and manual uploads deploy into it; developers, pipelines and environments download from it](/assets/images/repository-management/local-repository.svg)

**🟠 Remote: fetch once, keep a copy.** The first request goes out to the internet; every later one is answered from the cache.

![A remote repository: fetches a dependency once from an outside registry, caches it and serves later requests from the cache](/assets/images/repository-management/remote-repository.svg)

**🟣 Virtual: the front desk.** One address for everyone, whatever sits behind it.

![A virtual repository: one URL for developers and pipelines, checking the local repository first and then the remote](/assets/images/repository-management/virtual-repository.svg)

## An everyday analogy

| Repository | Think of it as | Because |
|---|---|---|
| 🟢 Local | Your own bookshelf | It holds the books you wrote yourself. |
| 🟠 Remote | A photocopy of a library book | You fetched it once from elsewhere and kept a copy, so you never need to go back. |
| 🟣 Virtual | The front desk | You ask one person; they know which shelf to check, and in what order. |

> [!NOTE]
> **Who sets these up?** Administrators. Creating a repository needs Admin or Project Admin permission and is done from the **Administration** area. Developers and pipelines then use what was created. The [.NET walkthrough](/repository-management/set-up-dotnet-repositories.md) shows who can do what.

## Which one do I need?

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#FFE0B2','primaryBorderColor':'#FF8A00','primaryTextColor':'#2B1B00','lineColor':'#7C4DFF','secondaryColor':'#E1BEE7','tertiaryColor':'#FFF3E0','noteBkgColor':'#E1BEE7','noteTextColor':'#2A0A3A','noteBorderColor':'#7C4DFF'}}}%%
flowchart TD
    Q1{"What are you doing?"}
    Q1 -->|"Publishing something<br/>we built"| L["🟢 Local repository"]
    Q1 -->|"Using a library<br/>from the internet"| R["🟠 Remote repository"]
    Q1 -->|"Configuring a build tool<br/>or developer machine"| V["🟣 Virtual repository"]
    V -.->|"which contains"| L
    V -.->|"and"| R
```

> [!IMPORTANT]
> **The golden rule:** people and pipelines talk to the **virtual** repository. Locals and remotes do the work behind it.
>
> This is the one to get right. Read [when to use a virtual repository](/repository-management/virtual-repositories.md) before you configure a single tool.

# The full list: four types

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
