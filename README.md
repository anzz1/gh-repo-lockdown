# GitHub Repo Lockdown 101

#### Add Lockdown action
https://github.com/USER/REPO/new/master?filename=.github%2Fworkflows%2Flockdown.yml&workflow_template=blank

lockdown.yml - Copy &amp; Paste
```yml
name: 'Repo Lockdown'

on:
  issues:
    types: opened
  pull_request_target:
    types: opened

permissions:
  issues: write
  pull-requests: write

jobs:
  action:
    runs-on: ubuntu-latest
    steps:
      - uses: dessant/repo-lockdown@v3
        with:
          issue-comment: >
            This repository does not accept bug reports,
            see the README for details.
          skip-closed-issue-comment: true
          pr-comment: >
            This repository does not accept pull requests,
            see the README for details.
          skip-closed-pr-comment: true
```


#### Main Page
https://github.com/USER/REPO/  

Click the gear icon on the right sidebar next to "About".

##### Include in the home page
Uncheck everything.

#### General
https://github.com/USER/REPO/settings

##### Features
Uncheck everything except _Preserve this repository_.

##### Pull requests
- [ ] Allow merge commits
- [X] Allow squash merging
  * Default to pull request title and commits details
- [X] Allow rebase merging
- [ ] Always suggest updating pull request branches
- [ ] Allow auto-merge
- [ ] Automatically delete head branches

#### Branches - Add branch protection rule
[https://github.com/USER/REPO/settings/branch_protection_rules/new?branch_name=*](https://github.com/USER/REPO/settings/branch_protection_rules/new?branch_name=*)

##### Branch name pattern
`*`

##### Protect matching branches
- [X] Lock branch

##### Rules applied to everyone including administrators
- [X] Allow force pushes
  * Everyone
- [X] Allow deletions

#### Actions
https://github.com/USER/REPO/settings/actions

##### Actions permissions
- [X] Allow all actions and reusable workflows

##### Fork pull request workflows
_This option will appear after you have added the lockdown.yml action above_

- [X] Run workflows from fork pull requests
- [ ] Require approval for fork pull request workflows.

##### Workflow permissions
- [X] Read and write permissions

---

### Unlocking the repo
#### Branches - Delete branch protection rule
https://github.com/USER/REPO/settings/branch_protection_rules/

#### Actions - Delete lockdown.yml
https://github.com/USER/REPO/delete/master/.github/workflows/lockdown.yml

