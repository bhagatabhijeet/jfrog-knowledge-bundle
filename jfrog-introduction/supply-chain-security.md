---
type: Concept
title: "Software supply chain security: Xray, build metadata and the SBOM"
description: How Artifactory and JFrog Xray turn build metadata into a software bill of materials and traceability.
tags: [artifactory, xray, introduction, security, sbom, compliance]
status: draft
generated:
  by: claude-code/opus-5.5
  at: 2026-10-11T00:00:00+00:00
stale_after: 2027-04-10T00:00:00+00:00
---

> [!TIP]
> **In one line:** Because every build goes through Artifactory, Xray can record what is in it, and that record is your SBOM and audit trail.

Artifactory lays the foundation for a company's software supply chain security. JFrog Xray builds on it by capturing the metadata from every build.

![A package passing a scanner with a green check](/assets/images/jfrog-introduction/xray-scan-pass.png)

```mermaid
flowchart LR
    B["Every build"] --> AF[("Artifactory")]
    AF --> X["Xray captures<br/>build metadata"]
    X --> S["Software bill<br/>of materials"]
    S --> T["Traceability for<br/>security and compliance"]
```

# What Xray does with build metadata

| Step | Result |
|---|---|
| Captures metadata from every build | A record of what went into each build |
| Forms a software bill of materials (SBOM) | An inventory of the build's contents |
| Provides traceability | Evidence for security and compliance purposes |

![A package failing the scanner, flagged in red](/assets/images/jfrog-introduction/xray-scan-fail.png)

# Related

- [What JFrog Artifactory is](/jfrog-introduction/what-is-artifactory.md) - traceability starts with every build being stored.
- [Access management](/jfrog-introduction/access-management.md) - the other half of securing the repository.

---

⬅️ [Deployment options and federation](/jfrog-introduction/deployment-and-federation.md) · 📚 [Topic index](/jfrog-introduction/index.md) · [Access management in Artifactory](/jfrog-introduction/access-management.md) ➡️
