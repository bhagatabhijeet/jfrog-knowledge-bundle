# Start here

* [Repository types in Artifactory](repository-types.md) - The four repository types Artifactory hosts (local, remote, virtual, federated) and what each is for.

# The three core types

* [Local repositories](local-repositories.md) - What a local repository stores, how its artifacts are addressed, and the settings fixed at creation.
* [Remote repositories](remote-repositories.md) - How a remote repository proxies and caches an upstream registry on demand, and the rules that follow from that.
* [Virtual repositories](virtual-repositories.md) - How a virtual repository puts local and remote repositories behind one URL, and exactly when to use one, which is almost always.

# Going further

* [Smart Remote repositories](smart-remote-repositories.md) - A remote repository that proxies a repository in another Artifactory instance, and the four extras that brings.
* [Why the package type matters](why-package-type-matters.md) - Every repository has one package type, fixed at creation; pick the wrong one and Artifactory stores your files but does not understand them.
* [Repository naming conventions](repository-naming-conventions.md) - JFrog's recommended naming patterns for local, remote and virtual repositories, and how naming supports governance.

# Hands-on

* [Walkthrough: set up .NET repositories in JFrog SaaS](set-up-dotnet-repositories.md) - Step-by-step creation of a local, a remote and a virtual NuGet repository in JFrog SaaS, in that order, then connecting the dotnet client.
