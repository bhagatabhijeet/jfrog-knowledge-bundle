<div align="center">

<img src="assets/readme/cover.svg" alt="JFrog Knowledge Bundle. Read it in minutes. Hand it to your AI agents." width="100%"/>

<br/><br/>

[![In this issue](https://img.shields.io/badge/📰_In_this_issue-00C853?style=for-the-badge)](#-in-this-issue)
[![Why read it](https://img.shields.io/badge/✨_Why_read_it-00B8D4?style=for-the-badge)](#-why-you-will-keep-reading)
[![Learning path](https://img.shields.io/badge/📍_Learning_path-7C4DFF?style=for-the-badge)](#-the-learning-path)
[![Under the hood](https://img.shields.io/badge/🧭_Under_the_hood-F50057?style=for-the-badge)](#-under-the-hood)
[![Use it](https://img.shields.io/badge/🚀_Use_it-FF8A00?style=for-the-badge)](#-use-it)
[![Contribute](https://img.shields.io/badge/🤝_Contribute-FFAB00?style=for-the-badge)](#-contribute)

[![OKF v0.2](https://img.shields.io/badge/OKF-v0.2-4285F4?style=flat-square)](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)
[![License CC0](https://img.shields.io/badge/License-CC0_1.0-40BE46?style=flat-square)](LICENSE)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-8A2BE2?style=flat-square)](#-contribute)

</div>

> **JFrog training, one concept at a time.** Each idea gets one short page with a one-line takeaway, a diagram and a worked example. People can read it in minutes. AI agents can read the same files and know how far to trust them.

<img src="assets/readme/divider.svg" alt="" width="100%"/>

## 📰 In this issue

<table>
<tr>
<td width="50%" valign="top">

<a href="jfrog-introduction/index.md"><img src="assets/readme/chapter-01.svg" alt="Chapter 01: JFrog Introduction. From artifact chaos to one source of truth." width="100%"/></a>

| | Concept |
|:-:|---|
| **01** | [What is an artifact?](jfrog-introduction/what-is-an-artifact.md) |
| **02** | [Artifact sprawl: the problem](jfrog-introduction/artifact-sprawl.md) |
| **03** | [What JFrog Artifactory is](jfrog-introduction/what-is-artifactory.md) |
| **04** | [Build once, promote everywhere](jfrog-introduction/build-once-promote-everywhere.md) |
| **05** | [Universal package support](jfrog-introduction/universal-package-support.md) |
| **06** | [Remote repositories: proxy and cache](jfrog-introduction/remote-repositories.md) |
| **07** | [Deployment options and federation](jfrog-introduction/deployment-and-federation.md) |
| **08** | [Supply chain security: Xray and the SBOM](jfrog-introduction/supply-chain-security.md) |
| **09** | [Access management](jfrog-introduction/access-management.md) |

</td>
<td width="50%" valign="top">

<a href="repository-management/index.md"><img src="assets/readme/chapter-02.svg" alt="Chapter 02: Repository Management. Local, remote, virtual: decoded." width="100%"/></a>

| | Concept |
|:-:|---|
| **10** | [Repository types in Artifactory](repository-management/repository-types.md) |
| **11** | [Local repositories](repository-management/local-repositories.md) |
| **12** | [Remote repositories](repository-management/remote-repositories.md) |
| **13** | [Smart Remote repositories](repository-management/smart-remote-repositories.md) |
| **14** | [Virtual repositories](repository-management/virtual-repositories.md) |
| **15** | [Repository naming conventions](repository-management/repository-naming-conventions.md) |

🟢 **New here?** Start at **01** and follow the *next* link at the foot of each page.

🟣 **Know the basics?** Jump straight to **10**.

</td>
</tr>
</table>

<img src="assets/readme/divider.svg" alt="" width="100%"/>

## ✨ Why you will keep reading

<table>
<tr>
<td width="25%" valign="top" align="center">

### 🎯

**One page, one idea**

Short enough for a coffee break, complete enough to stand alone.

</td>
<td width="25%" valign="top" align="center">

### 🎨

**A picture on every page**

Each concept opens with a one-line takeaway and a diagram.

</td>
<td width="25%" valign="top" align="center">

### 🔗

**Linked, not stacked**

Follow *previous* and *next*, or wander through the cross-links.

</td>
<td width="25%" valign="top" align="center">

### 🔒

**Trust you can see**

Every page says who wrote it, who checked it and when it expires.

</td>
</tr>
</table>

<div align="center">

<a href="jfrog-introduction/artifact-sprawl.md"><img src="assets/images/jfrog-introduction/different-kinds-of-artifacts.png" alt="Different kinds of artifacts" width="32%"/></a>
<a href="jfrog-introduction/universal-package-support.md"><img src="assets/images/jfrog-introduction/single-source-of-truth.png" alt="A single source of truth for all packages" width="32%"/></a>
<a href="jfrog-introduction/build-once-promote-everywhere.md"><img src="assets/images/jfrog-introduction/build-once-promote-everywhere.png" alt="Build once, promote everywhere" width="32%"/></a>

<sub>A taste of the illustrations inside chapter 01. Click one to open its page.</sub>

</div>

<img src="assets/readme/divider.svg" alt="" width="100%"/>

## 📍 The learning path

```mermaid
flowchart LR
    subgraph T1["Chapter 01 · JFrog Introduction"]
        direction LR
        A["The problem:<br/>artifact sprawl"]:::green --> B["What<br/>Artifactory is"]:::teal --> C["What it<br/>makes possible"]:::blue
    end
    subgraph T2["Chapter 02 · Repository Management"]
        direction LR
        D["Repository<br/>types"]:::orange --> E["Local, remote,<br/>Smart Remote, virtual"]:::pink --> F["Naming and<br/>governance"]:::purple
    end
    C ==> D
    classDef green fill:#00C853,stroke:#00963F,color:#06210F
    classDef teal fill:#00B8D4,stroke:#008BA3,color:#00222A
    classDef blue fill:#2979FF,stroke:#004ECB,color:#FFFFFF
    classDef orange fill:#FF8A00,stroke:#C25E00,color:#2B1B00
    classDef pink fill:#F50057,stroke:#BB002F,color:#FFFFFF
    classDef purple fill:#7C4DFF,stroke:#3F1DCB,color:#FFFFFF
```

And the one picture worth remembering from chapter 02:

```mermaid
flowchart LR
    DEV["Developers and CI"]:::grey --> V{{"Virtual repository<br/>one URL"}}:::purple
    V -->|"1. first"| L[("Local<br/>what you build")]:::green
    V -->|"2. then"| R[("Remote<br/>cached dependencies")]:::orange
    R -->|"on demand"| P["Public registry"]:::grey
    classDef green fill:#00C853,stroke:#00963F,color:#06210F
    classDef orange fill:#FF8A00,stroke:#C25E00,color:#2B1B00
    classDef purple fill:#7C4DFF,stroke:#3F1DCB,color:#FFFFFF
    classDef grey fill:#ECEFF1,stroke:#90A4AE,color:#263238
```

<img src="assets/readme/divider.svg" alt="" width="100%"/>

## 🧭 Under the hood

The bundle follows the [**Open Knowledge Format (OKF) v0.2**](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md), Google Cloud's open, vendor-neutral way to package knowledge as linked Markdown files with YAML metadata. There is no database and no special tooling: if you can read Markdown, you can read this bundle.

### 🚦 Read the trust signals

| Signal in the page header | What it tells you |
|---|---|
| 🔴 No `verified` entry | **Unverified.** Treat it as a draft. |
| 🟡 `verified` by a tool or agent only | **Machine-confirmed.** Checked automatically, not yet by a person. |
| 🟢 `verified` by a `human:` actor | **Human-reviewed.** A person has confirmed it. |
| 🔖 `status: draft` / `stable` / `deprecated` | Where the page is in its life. |
| ⏰ `stale_after` in the past | Due for review. The product may have moved on. |

<details>
<summary><b>📁 How the repository is laid out</b></summary>

<br/>

```text
jfrog-knowledge-bundle/        ← the OKF bundle root
├── index.md                   ← table of contents, declares okf_version: "0.2"
├── log.md                     ← what changed and when, newest first
├── README.md                  ← you are here (repo front page, not a concept)
├── assets/images/<topic>/     ← illustrations used by the concepts
├── assets/readme/             ← cover artwork for this page
└── <topic>/
    ├── index.md               ← what's in this topic
    └── <concept>.md
```

In OKF, the **file path is the concept's identity**. `index.md` and `log.md` are reserved names; every other `.md` file in the bundle is a concept.

</details>

<details>
<summary><b>🔬 Anatomy of a concept page</b></summary>

<br/>

Each concept file opens with a short YAML header, followed by the page itself:

```markdown
---
type: Concept
title: A short, human-friendly title
description: One sentence that says what you will learn here.
tags: [artifactory, repositories]
status: stable
sources:
  - id: jfrog-docs
    resource: https://docs.jfrog.com/artifactory/docs/repository-management
    title: JFrog Artifactory documentation
generated:
  by: human:bhagatabhijeet
  at: 2026-10-10T00:00:00+00:00
verified:
  - by: human:bhagatabhijeet
    at: 2026-10-10T00:00:00+00:00
stale_after: 2027-04-10T00:00:00+00:00
---

The explanation, with claims tied to their source.[^jfrog-docs]

# Examples

Commands and configuration you can copy and run.
```

Only `type` is required by the spec. The other fields are where the trust comes from.

</details>

<img src="assets/readme/divider.svg" alt="" width="100%"/>

## 🚀 Use it

<table>
<tr>
<td width="50%" valign="top">

### 📖 If you are learning

1. Pick a chapter from [In this issue](#-in-this-issue).
2. Read a page. Follow the links that interest you.
3. Check the header when you need to know how far to trust a page.

</td>
<td width="50%" valign="top">

### 🤖 If you are building with AI agents

Point your agent, retrieval pipeline or knowledge catalog at the repository root.

```bash
git clone https://github.com/bhagatabhijeet/jfrog-knowledge-bundle.git
```

</td>
</tr>
</table>

What an agent gets from the format:

- 🆔 **Stable identity.** Every concept is addressed by its path and carries typed metadata, so retrieval can be precise.
- 📎 **Citable answers.** `sources`, `generated` and `verified` let an agent cite a page and weigh how reliable it is.
- ⏳ **Freshness.** `status` and `stale_after` let an agent skip or flag content that is out of date.
- 🔌 **No custom code.** Any OKF v0.2 consumer can read the bundle as it is.

<img src="assets/readme/divider.svg" alt="" width="100%"/>

## 📅 Roadmap

| Chapter | Status |
|---|---|
| 📗 [JFrog Introduction](jfrog-introduction/index.md) | 🚧 Draft, awaiting human review |
| 📙 [Repository Management](repository-management/index.md) | 🚧 Draft, awaiting human review |
| 📘 More topics | ⏳ Coming, one chapter at a time |

Watch or star the repository to catch each new chapter.

## 🤝 Contribute

Corrections, new concepts and better examples are all welcome.

1. 🎯 **One concept per file.** If a page explains two ideas, split it.
2. 🔖 **Always set `type`**, and add `title`, `description` and `tags`.
3. 📎 **Cite your sources** in `sources`, and tie claims to them with footnotes.
4. 📝 **Sign your work.** Set `generated.by` to `human:<your-github-id>` for content you wrote yourself.
5. 🔗 **Link generously** to related concepts, using bundle-relative paths that start with `/`.
6. 📒 **Record the change** in `log.md`.

A bundle is conformant when every concept file has parseable frontmatter with a non-empty `type`, and the reserved files keep their structure. Please check that before opening a pull request.

## 📄 License

Released under [CC0 1.0 Universal](LICENSE). Use it, adapt it and teach from it, with no permission needed.

**Credit is welcome, never required.** If this work helps you, a mention is appreciated:

> JFrog Knowledge Bundle by [bhagatabhijeet](https://github.com/bhagatabhijeet/jfrog-knowledge-bundle)

GitHub's **Cite this repository** button gives the same details in citation formats.

The images in `assets/images/` are not covered by the CC0 licence. They remain the property of JFrog Ltd.

<br/>

<div align="center">

<img src="assets/readme/back-cover.svg" alt="Star it. Fork it. Teach with it. More topics on the way, same format." width="100%"/>

<sub>This is an independent community project. It is not affiliated with or endorsed by JFrog Ltd.<br/>
JFrog and Artifactory are trademarks of JFrog Ltd.</sub>

</div>
