# Start here

* [What is an artifact?](what-is-an-artifact.md) - An artifact is the ready-to-deploy file a build produces; here is what it contains and what it looks like in each ecosystem.
* [What is an artifact repository?](what-is-an-artifact-repository.md) - An artifact repository is a server that keeps multiple versions of your artifacts; here is what it does and why teams rely on one.
* [Artifact sprawl: the problem Artifactory solves](artifact-sprawl.md) - How a growing software team loses track of its binaries, and what that costs.
* [Why not Git for artifacts? Why Artifactory?](why-not-git-for-artifacts.md) - Why a version control system is the wrong place to keep build artifacts, and what an artifact repository manager like Artifactory does that Git cannot.
* [What JFrog Artifactory is](what-is-artifactory.md) - Artifactory as the one organized place where a team stores, manages and traces every artifact it builds.
* [Artifactory editions: Open Source and SaaS](artifactory-editions.md) - The two ways to get JFrog Artifactory, a free open source edition you host yourself and a SaaS edition JFrog runs for you, and how to choose.
* [Checksum-based storage: how Artifactory keeps binaries](checksum-based-storage.md) - Artifactory stores every binary once, named by its checksum, and keeps paths in a database; this is what makes it fast, lean and trustworthy.

# Capabilities

* [Build once, promote everywhere](build-once-promote-everywhere.md) - Releasing by promoting one immutable binary across repositories, not rebuilding it for each stage.
* [Universal package support and the single source of truth](universal-package-support.md) - Why one repository manager that handles over 40 package types replaces a separate tool per technology.
* [Remote repositories: proxying and caching open source dependencies](remote-repositories.md) - How Artifactory remote repositories proxy and cache external OSS dependencies, and what that gains a team.
* [Deployment options and federation](deployment-and-federation.md) - How Artifactory is installed (hybrid, multi-cloud, self-hosted) and how it shares artifacts across sites.

# Security

* [Software supply chain security: Xray, build metadata and the SBOM](supply-chain-security.md) - How Artifactory and JFrog Xray turn build metadata into a software bill of materials and traceability.
* [Access management in Artifactory](access-management.md) - How Artifactory controls who can do what, using multi-level permissions and role-based access.
