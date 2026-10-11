---
type: Concept
title: "Access management in Artifactory"
description: How Artifactory controls who can do what, using multi-level permissions and role-based access.
tags: [artifactory, introduction, security, permissions, rbac]
status: draft
generated:
  by: claude-code/opus-5.5
  at: 2026-10-11T00:00:00+00:00
stale_after: 2027-04-10T00:00:00+00:00
---

> [!TIP]
> **In one line:** Who can do what is decided by permissions and roles, attached to users, groups and tokens.

Artifactory makes access management and user control more secure by managing multi-level permissions and role-based access.

![Security gates labelled users, groups and tokens](/assets/images/jfrog-introduction/access-control.png)

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#B9F6CA','primaryBorderColor':'#00C853','primaryTextColor':'#06210F','lineColor':'#00B8D4','secondaryColor':'#B3E5FC','tertiaryColor':'#E8F5E9','noteBkgColor':'#FFE57F','noteTextColor':'#2B1B00','noteBorderColor':'#FFAB00'}}}%%
flowchart LR
    U["Users"] --> P{{"Multi-level permissions<br/>and role-based access"}}
    G["Groups"] --> P
    T["Tokens"] --> P
    P --> R[("Repositories<br/>and artifacts")]
```

# What access is tied to

Permissions and roles are tied to three kinds of identity:

- **Users**
- **Groups**
- **Tokens**

# Related

- [Software supply chain security](/jfrog-introduction/supply-chain-security.md)
- [What JFrog Artifactory is](/jfrog-introduction/what-is-artifactory.md)

---

⬅️ [Software supply chain security: Xray, build metadata and the SBOM](/jfrog-introduction/supply-chain-security.md) · 📚 [Topic index](/jfrog-introduction/index.md)
