
---
layout: default
---

## Open source

The Media-Cloud AI source code is hosted on the [https://gitlab.com/media-cloud-ai](https://gitlab.com/media-cloud-ai) Gitlab group.

The project is organised arround the following subgroups :
  - _Backbone_: some MCAI-related tools configuration
  - _Backend_: the MCAI Web platform sources
  - _Command Line Tools_: some CLI applications to interact with the MCAI environment
  - _Continuous Integration_: CI pipelines and runners definitions
  - _Documentation_: for the MCAI Web Site
  - _Libraries_: common libraries sources
  - _SDKs_: Rust and Python SDKs for MCAI workers
  - _Startup_: MCAI deployment utilities
  - _Workers_: MCAI workers

### Bug reports

_To be defined_

### Code contribution

Feel free to propose your fix, improvement or feature in the code of any of the projects of Media-Cloud AI.

See the [Developer contribution rules](#developer-contribution-rules) section to find out how to proceed.

## Developer contribution rules

This document aims to define some rules that <ins>must be followed as strictly as possible</ins> by anyone wishing to contribute to the Media-Cloud AI project.

### Git

As the main tool for sharing Media-Cloud AI code, the use of Git must be given special attention.

The organization of the different Git projects of Media-Cloud AI is based on the [git-flow](https://git-flow.readthedocs.io/en/latest/presentation.html) philosophy. This mainly involves that each contribution (feature, fix, hotfix or release) has its own branch, based on a main branch (`main` (formerly `master`) or `develop`, or both).

#### Branch naming rule:

Git branches should be named following this pattern:

    `<topic>/<issue_title_or_description>`

   with `fix`, `feature`, `hotfix`, `release`, `ci`... as possible `<topic>` values.

#### Commit policy:

Here are some good practices to apply:

 - Use English for all contributions
 - __Write descriptive and meaningful commit messages__. No, "change" "wip" or "update" don't belong to this category!
 - __Commit only related work__: the least amount of lines that make sense together, and related to the branch purpose.
 - Don't commit changes that break the code: projects should be compiling at any commit level.
 - The author of a commit is responsible for it and should try to fix issues it may cause.

#### Push consideration:

 - Rebase your working branch as frequently as you can before publishing it on the remote repository.
 - Don't push directly on main branches (master, main, develop...)
 - __Never `push --force` onto a main branch__ (master, main, develop), other developers are basing there work on it!
 - You may rewrite the history (`push --force`) in specific cases:
     - After you rebased your branch
     - To amend the last commit of your branch

    __Always make sure to explicit the target branch when using `push --force`!__


Overall, __avoid changing a published history__! If you want to change your branch history:
 1. Create a new branch
 2. Re-commit your changes properly on the new branch (`git cherry-pick` can be helpful)
 3. Then remove the former branch


### Gitlab environment

The Gitlab platform is used to centralize the code, and to manage to development of Media-Cloud AI.

Before starting your contribution, please ensure your Gitlab profile shares the email address you configured in your local Git.

#### Issues:

__Each contribution must be linked to an Issue__ on the related Gitlab repository.

This means that, as an example, if you found a bug:

 1. Check whether an Issue already exists regarding this bug
 2. If necessary, create a new Issue to report the bug
    a. Choose an explicit title
    b. Explicit the Issue into the description
    c. Don't hesitate to split the Issue into multiple unit tasks
    d. Apply the appropiate [labels](https://gitlab.com/groups/media-cloud-ai/-/labels)
 3. Create a new branch with a name based on the title of the Issue (see the [Branch naming rule](#branch-naming-rule) section)
 4. Start commiting patches to fix this bug

#### Merge Requests:

__Each contribution must result in a Merge Request__ on the related Gitlab repository. __Each Merge Request must be related to an existing Issue__.

When your development is complete, push your branch on the remote Gitlab repository, and create a Merge Request targeting a main branch (`develop` or `main`).

You must __assign yourself as an Assignee__: meaning that you are responsible for the changes proposed, and you will be in charge of merging the branch into the target branch.

You can mark the Merge Request as _Draft_, if you consider it is not ready for a review.

You can also use labels to improve the Merge Request understanding and indexation.

When the Merge Request is ready, you have to request a review by __assigning the issuer or a relevant* developer as a Reviewer__: this person has to review your code, may request some changes, and is responsible for the final approval.

You should also check the Continuous Integration (CI) pipeline results: __all CI jobs must have succeeded__ before your branch can be merged.

Please be sure to have your branch rebased on the target branch in order to have the correct commit history. In addition, you should rebase your own commits so the commit history keeps clean and clear (eg. remove the `wip` or `fix` commits).

Once the Merge Request is approved (and the CI pipeline succeeded), you can merge your branch into the target branch.

Finally, you can close the related issue.

\* _someone that will be able to understand the purpose of your Merge Request, or at least a member of the Q&A team (if any)_

#### Roadmap, Milestones and release management

Upstream of any new release, a roadmap will be determined by project owners with the content of this new release.

When all the features contained in the milestone are ready, a release branch is created from the `develop` branch and a release candidate version is tagged from it. Possibly, fixes are pushed in this release branch followed by another release candidate version.

When the release candidate is compliant to what is expected, the release branch is merged in both `main` and `develop` branches.

---

### To sum up:

 1. Find or create an Issue
 2. Create a related branch
 3. Commit properly: <ins>explicit labels</ins>, project still compiling
 4. Push your branch
 5. Create a Merge Request (MR), and ask for a review
 6. Follow/discuss the comments of the reviewer, commit & push corrections
 7. Once the MR is approved, merge your branch into the target branch
 8. Congrats! You (or the issuer) may now close the related issue.

---
