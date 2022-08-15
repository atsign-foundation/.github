# atGitHub

The atsign-foundation GitHub organisation has accumulated a whole bunch
of conventions and configuration, which until this document were being
carried around in the heads of the team. The purpose of this guide is
to make those conventions and configuration explicit.

## Our GitHub Apps (bots)

We have the following GitHub Apps installed:

### Allstar

[Allstar](https://github.com/ossf/allstar) is an app from the Open
Source Security Foundation ([OSSF](https://openssf.org/)) that monitors
the configuration of our GitHub repos.

We have an opt-in strategy that covers all the public repos, and make use of
the default policies covering:

* Branch Protection
* Binary Artifacts
* Outside Collaborators
* SECURITY.md
* Dangerous Workflow
* Generic Scorecard Check

### BackHub

> Backhub is a cloud to cloud backup solution for your GitHub repositories.
Backups include metadata such as issues and come with daily snapshots up to
30 days back in time. Restore to GitHub or clone directly from BackHub.
GitHub repository backups have never been easier.

### DigitalOcean

Vestigial from when Digital Ocean was a more important part of our cloud
infrastructure. (We still use it for DNS, but we don't use GitHub integration
for that).

### Semantic PRs

> A GitHub app to check that pull requests follow the Conventional Commits spec

This was implemented to ensure that we have high quality pull request (PR)
titles, which can then feed in to high quality change logs.

The process begins by using
[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
to ensure structured commit messages, which then become the basis for PR
titles.

At the moment we don't mandate passing checks for this bot, but that may
change.

## Our templates

New repos should be created from templates, as the templates take care of
the boilerplate needed to pass the GitHub recommended community standards
checks:

* README
* Code of conduct
* Contributing guide
* License

NB we implement issue templates and pull request template at an org
level, though they can be overridden at the repo level.

### archetype

The primary template is called
[archetype](https://github.com/atsign-foundation/archetype) and simply
takes care of the checklist above.

### archetype-pubdev

When a repo will be used to publish content to [pub.dev](https://pub.dev)
the [archetype-pubdev](https://github.com/atsign-foundation/archetype-pubdev)
can be used to provide some additional framework examples.

## Dependabot

We use Dependabot to keep an eye on dependencies for things like:

* GitHub Actions
* Dockerfiles
* Dart/Flutter pubspec.yaml

When Dependabot sees an update to a dependency it will raise a PR, which
can then be tested before we make the decision to merge.

### Dependabot vs Secrets

A malicious dependency might try to steal secrets, so Dependabot doesn't have
access to secrets when it's running GitHub Actions.

In some cases this means that we've crafted tests so that they won't run
when a PR originates from Dependabot, as otherwise they'd fail, and we
wouldn't be able to merge the Dependabot PR due to a failed check.

### Dependabot rollups

It's common for Dependabot to raise multiple PRs for the same dependency
changing in multiple places across a repo. This can be tedious, as once
one change is merged all the others need to be rebased. So to save time
we manually roll up a number of Dependabot PRs by merging their respective
bramches together. At least Dependabot is smart enough to close the
original PRs when the rollup is merged. Hopefully Dependabot will get the
ability to handle rollups for itself.

