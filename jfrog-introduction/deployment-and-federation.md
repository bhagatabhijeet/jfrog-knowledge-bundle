---
type: Concept
title: "Deployment options and federation"
description: How Artifactory is installed (hybrid, multi-cloud, self-hosted) and how it shares artifacts across sites.
tags: [artifactory, introduction, deployment, federation, multi-site]
status: draft
generated:
  by: claude-code/opus-5.5
  at: 2026-10-11T00:00:00+00:00
stale_after: 2027-04-10T00:00:00+00:00
---

> [!TIP]
> **In one line:** Install Artifactory where it suits you, and federate so every site works from the same artifacts.

Artifactory supports geographically distributed teams in two ways: a choice of installation models, and the ability to federate artifacts across multiple sites.

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#B9F6CA','primaryBorderColor':'#00C853','primaryTextColor':'#06210F','lineColor':'#00B8D4','secondaryColor':'#B3E5FC','tertiaryColor':'#E8F5E9','noteBkgColor':'#FFE57F','noteTextColor':'#2B1B00','noteBorderColor':'#FFAB00'}}}%%
flowchart LR
    S1[("Site A<br/>self-hosted")] <-->|"federated"| S2[("Site B<br/>cloud")]
    S2 <-->|"federated"| S3[("Site C<br/>another cloud")]
    S1 <-->|"federated"| S3
    T1["Team A"] --> S1
    T2["Team B"] --> S2
    T3["Team C"] --> S3
```

# Installation models

| Model | In plain words |
|---|---|
| 🖥️ **Self-hosted** | You run Artifactory on your own infrastructure |
| ☁️ **Multi-cloud** | Artifactory runs on more than one cloud provider |
| 🔀 **Hybrid** | A mix: some of it in the cloud, some of it on your own infrastructure |

The model names are JFrog's. The one-line descriptions are a plain-language guide.

![Teams at three sites labeled hybrid, multi-cloud and self-hosted](/assets/images/jfrog-introduction/deployment-options.png)

# Federation

Artifacts can be federated across multiple sites, so teams in different locations access the same artifacts without conflict.

![Three teams at different sites sharing the same set of artifacts](/assets/images/jfrog-introduction/federation.png)

# Why federate?

| Without federation | With federation |
|---|---|
| Each site has its own copy, and they drift apart | Every site sees the same artifacts |
| Teams wait for files to be sent across | The artifact is already there |
| "Which site has the right version?" | They all do |

> [!NOTE]
> On JFrog SaaS, each location is a **site**. See [subscriptions, sites and JPDs](/platform-navigation/subscriptions-sites-and-jpds.md) for how sites are organized, and [Artifactory editions](/jfrog-introduction/artifactory-editions.md) for who runs what.

# Related

- [Subscriptions, sites and JPDs](/platform-navigation/subscriptions-sites-and-jpds.md)
- [Artifactory editions: Open Source and SaaS](/jfrog-introduction/artifactory-editions.md)
- [Repository types in Artifactory](/repository-management/repository-types.md) - federated repositories are the fourth type.
- [Artifact sprawl](/jfrog-introduction/artifact-sprawl.md) - "more developers across multiple sites" is one of the causes this addresses.

---

⬅️ [Remote repositories: proxying and caching open source dependencies](/jfrog-introduction/remote-repositories.md) · 📚 [Topic index](/jfrog-introduction/index.md) · [Software supply chain security: Xray, build metadata and the SBOM](/jfrog-introduction/supply-chain-security.md) ➡️
