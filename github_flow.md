# Github Flow

These are some suggestions that can be followed to implement a really useful Github Flow in daily development:

### Separate Branch for Each Deployment Environment

**Master** - Code in this branch should be fully tested and ready to be deployed to production. No code should be
directly pushed into master branch.

**Staging** - Staging branch should be used for testing by the QA engineers. Ideally this branch/environment should be
an exact replica of the production

**Develop** - This branch contains pre-production code. Code is merged in develop once a feature is completed by a
developer

### Development Branches Naming Conventions

There are different types of naming conventions that are used. Anyone of them can be used, that suits the team best. But
one thing has to be made sure that the whole always use the same naming convention.

Some naming conventions are:

_[Developer Initials]-[Issue Id in Management Board]-[Very Brief title]_

_[Developer Initials]-[Type of Work (feature, hotfix, bug)]-[Very Brief title]_

_[Developer Initials]-[Date]-[Very Brief title]_

There is no right or wrong in these conventions. However, consistency is the key, that there should not be any variation
in the naming conventions used by the team

### Workflow

There can be three types of workflows, depending upon the situation:

1. Feature/Bug Fix
2. Hot Fix

**Feature/Bug Fix**

- Create a new branch from develop
- Once the development is complete, create a PR against the develop branch.
- PR must be reviewed by developers and should have at least two thumbs up for it to be able to be merged
- Squash and Merge the branch into develop
- Delete the branch
- After testing, develop branch is merged into staging
- Staging branch is tested in staging environment
- Once passed by QA, staging branch should be merged into master

**Hot Fix**

- Create a new branch from master.
- Once the development is complete, create a PRs against Master and Develop branch.
- PR should have at least two thumbs up for it to be able to be merged
- After doing initial testing on the hotfix branch Squash and Merge the branch into Master and Develop
- Delete the branch
- Perform regression testing on the master branch

### Creating Release

Please make sure that all of the production releases are documented and tagged on github

[https://help.github.com/en/articles/creating-releases](https://help.github.com/en/articles/creating-releases)
