# at_mono

The atsign-foundation GitHub organisation has a unique answer to the poly
vs. mono repo debate. While most organisations typically fall into one of
the two categories, this organisation's Dart repositories follow a hybrid
approach.

## The Hybrid Poly-monorepo Approach

Our Dart repos follow a hybrid poly-monorepo approach, wherein we use a series
of several monorepos. Packages amongst the monorepos are sorted based on the
type of product, for example, all Flutter widgets live in the at_widgets
repository.

### Benefits of the Approach

With over 40 packages to maintain, using a hybrid poly-monorepo structure
is a must for maintaining the atPlatform efficiently. If we used a pure
multirepo approach, then we would be forced into maintaining over 40
repositories. This is why we've opted for the hybrid approach, allowing us
to work closely with things that are related, and autonomously from things
that aren't.

### The Major Weakness of the Approach

The hybrid multi-monorepo approach tends to fall short when it comes to
testing cross-repository package dependencies. This makes it difficult to
detect issues contained in lower-level packages early on. On occasion, an
issue floats all the way up through the dependency tree, ultimately affecting
end-developers.

## The Poly-as-Mono Repo (at_mono)

As is the nature of the atPlatform, we've flipped the "Mono-as-Poly" approach
which involves using a monorepo for development and distributing each package
to its own polyrepos.

Since we distribute from the poly-monorepos to
[pub](https://pub.dev/publishers/atsign.org/packages) and
[docker hub](https://hub.docker.com/u/atsigncompany), we don't need to
worry about distributing to pure polyrepos. However, we do need to join the
poly-monorepos into a single monorepo for the purposes of testing. To simplify
the concept, we've coined it as the "Poly-as-Mono" approach, since in practice
the process is same when using pure polyrepos (although the process is more
accurately described as a polymono-as-mono approach).

The [at_mono repo](https://github.com/atsign-foundation/at_mono) is the home for
our Poly-as-Mono repo.

## Clarifying Terms

- `monorepo` - When a repository contains all the packages/libraries for a given
  project/system.
- `polyrepo` - When a repository contains only one package/library for a given
  project/system and several repositories are created for a project.
- `poly-monorepo` - An individual monorepo that is part of a series of monorepos.
  Each poly monorepo contains a subset of the total packages.
- `Mono-as-poly repo` - When a monorepo is used for development and testing, and
  packages are distributed to individual polyrepos.
- `Poly-as-mono repo` - When polyrepos (or in this case "poly-monorepos") are
  used for development, joined together into a monorepo to form a single testing
  environment, and distributed as individual packages.

## Dart Poly-monorepo Structure

To make it easier to work with the various poly-monorepos in at_mono, we've
adopted the following structure for repositories:

- `.github/` - The GitHub configuration directory.
	- `composite/` - Reusable "composite" workflows for GitHub Actions.
	- `workflows/` - Typical GitHub Actions workflows.
	- `...` and all other typical `.github` things.
- `docs/` - Additional documentation that is scoped to the repository level.
- `packages/` - The (public facing) Dart and Flutter packages in the repo.
- `tests/` - The repo-level (i.e. non-package-specific) tests/testing suites in the repo.
- `tools/` - All tools and automation (except the workflows in `.github`).
- `melos.yaml` - Configuration for our monorepo management tool
[melos](https://melos.invertase.dev/).
  - Allows us to define the locations of all packages in the repo so we can link
  them locally (via pubspec.lock modification).
  - Allows us to define a standard set of scripts for the repository.
- Standard [atGithub](./atGitHub.md) documentation:
  - `README.md`
  - `LICENSE`
  - `code_of_conduct.md`
  - `CONTRIBUTING.md`
  - `SECURITY.md`

## The at_mono Repository

> To be completed by @XavierChanth at a later date.  
> This section will dive into the specifics of at_mono.
