# Git Flow Presentation Outline

## Introduction

* Webteam background
    * WordPress
    * Python / Django
* How we use VCS
    * Started with CVS, migrated to SVN, in the process of migrating to Git
    * Majority of our codebase is under version control
    * Build / deploy tool that pulls from VCS and pushes to different environments (dev, test, prod)
* Why We Love Git
    * Fast!
    * Distributed!  No longer need an internet connection to commit
    * Branches are cheap!  Use them for everything!
    * Commit often locally, can always amend / squash / rebase before push

## Git Flow
http://nvie.com/posts/a-successful-git-branching-model/

Branching workflow for development.  Utilizes the following branches:

* `master`
* `develop`
* `feature/*`
* `hotfix/*`
* `release/*` (which we won’t discuss today, but should mention)

### Key points

* The `master` branch should be stable releases
* Each commit to `master` gets a dedicated tag (e.g. `1.1`)
* The `develop` branch should be integration branch for features / bug fixes, staging area for next release
* All feature development takes place in `feature` branches (e.g. `feature/private-posts`)
* Feature branches are branched off of and merged back into `develop`
* All hot fixes take place in dedicated `hotfix` branches
* Hotfixes branch of `master`, merge back in to `master` (with tag!) and `develop`
* All releases are staged in dedicated `release/` branches (e.g. `release/1.1`)
* Release branches are branched off of `develop` and merged back into `develop` as well as `master`

## Demo - BU Navigation Plugin
https://github.com/bu-ist/bu-navigation

**Instructions**: https://github.com/mgburns/tech-talk-gitflow

### Background

* WordPress and large page hierarchies
* Quick Tour
* WordPress without it
* Install plugin from WP.org
* Remove and install from Github
* Show them the key features it adds in the admin interface:
    * Edit Order screen
    * Move Post interface
    * External links

### Demonstrate a `hotfix` branch

* Disappearing navigation labels, fixed in https://github.com/bu-ist/bu-navigation/commit/aa2dfde653c0b60dddae8874b0b8e7dd6fb22b69
* Use `git bisect` to find the introductory commit
* Use a `hotfix` branch to fix it
* Merge back to `master` and tag
* Merge back to `develop`
* Delete the `hotfix` branch

### Demonstrate a `feature` branch

* Private post type support, merged in https://github.com/bu-ist/bu-navigation/commit/6652da60db72768a15888a8c3f047f0bd3d9ef3d
* Use a `feature` branch to add
* Demonstrate use of `no-ff` flag for merge
* __Optional__: Create the `feature` branch from an earlier commit that will result in a merge conflict on `develop` reintegration
* Merge back to `develop`
* Delete the `feature` branch

### Show them a community contributed pull request
https://github.com/bu-ist/bu-navigation/pull/4

### Show them how Github commenting + Git Flow provides a good workflow for code reviews
https://github.com/bu-ist/bu-slideshow/pull/2
