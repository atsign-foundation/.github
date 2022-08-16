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

NB a public version of the archetype template can be found in the
[atsign-company](https://github.com/atsign-company/archetype) org.

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

## GitHub Actions

GitHub Actions are used extensively across org repos to undertake:

### Continuous Integration

Continuous Integration (CI) tests are in place to ensure that PRs are tested
before being merged. These will usually consist of some combination os:

* Unit tests - tests that can be run standalone (NB it's expected that unit
tests will be run before committing code).
* Functional tests - tests that require extra resources, such as an atPlatform
Virtual Environment.
* End to End tests - tests that require multiple additional resources, such
as secondary servers running different versions of code to ensure that new
code still works with existing production code.

### Continuous Delivery

Some repos are configured so that merges to trunk create a new release that
is automatically deployed to the staging environment.

Repos may also have automation such that release tags create releases that
are deployed to canary and production environments.

### Project automation

Workflows will pick up new issues and place them in Triage on the
[Dev Eng Sprint Planning Board](https://github.com/orgs/atsign-foundation/projects/8)

## GitHub Projects

We make use of a number of project boards to organise work.

The process starts with an issue being raised, making use of the templates
for bug, enhancement etc.

Automation is used to place issues in Triage, where they should be prioritised
and where possible assigned to somebody knowledgeable about the work involved
to resolve the issue.

Sufficiently high priority issues will be scheduled into two week sprints,
other issues will be placed in the backlog.

Where it's not obvious how much effort is expected we make use of
[Planning Poker](https://www.planningpoker.com/) to get the wisdom of the
team to determine an estimate. Issues are exported from GitHub Projects
using the [Dump Cards](https://github.com/atsign-company/dump_cards) scripts.

## Labels

The [labels](https://github.com/atsign-company/labels) repo is used to
manage a consistent set of labels across org repos.

## Changing things across the org

There are often times when a change needs to be made to multiple repos, and
these generally fall into two types: content changes and config changes.

### Content changes

When the same change is needed to content across multiple repos these can be
accomplished with [git-xargs](https://github.com/gruntwork-io/git-xargs) and
accompanying scripts.

For examples see (private repo)
[atsign-company/git-xargs_scripts](https://github.com/atsign-company/git-xargs_scripts)

### Config changes

We use the
[Terraform GitHub Provider](https://registry.terraform.io/providers/integrations/github/latest/docs)
to orchestrate changes across multiple repos. Different parts of the
underlying API(s) are supported by different resources within the provider,
so usage will be very context dependent.

[This Gist](https://gist.github.com/cpswan/76f70da05b4f8929b84db4f51a76b672)
provides an example of applying branch protection rules (in order to pass
Allstar compliance checks).

## Your account

### Profile

A complete profile helps to show the human side of our organisation, and
gives you a chance to highlight your interests and contributions.

### Multi Factor Authentication (MFA)

Please have MFA enabled, as it is safer for you, and this org.

### Signing commits

Signing commits with GPG keys (or SSH keys once feasible) is encouraged, as
it provides a stronger chain of custody for code.
