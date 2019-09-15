# Application Development and Versioning

Every promotion in production server, jenkins will auto generate semantic version in every release.

### Flow for development

1. Always make sure you are updated from master
   `git pull origin master`

2. Create a task branch
   `git checkout -b INITIAL_NAME-GEN-TICKET`

3. Micro commit in every changes. So we can easy to track what changes have done in branch
   example:

```
 git commit -am "TICKET: INITIAL_NAME-GEN-TICKET AFFECTED: Todo list CHANGES: created a types for todo"
 git commit -am "TICKET: INITIAL_NAME-GEN-TICKET AFFECTED: Todo list CHANGES: created an epicx for getTodoList"
 git commit -am "TICKET: INITIAL_NAME-GEN-TICKET AFFECTED: Todo list CHANGES: created an action for todo"
```

4. Before pushing to master always make sure you are updated if ever there's a new changes in the master origin
   `git pull origin master`

5. push your branch local in origin
   `git push origin BRANCH_NAME`

## Assume that we have an issue in production.

### Flow for hotfix

Strictly need to follow:

1.  `git-fetch` - to download branch from origin repository.

```
    git fetch origin VERSION_BRANCH_TO_HOTFIX
```

2.  git checkout TAGS example: `git checkout v.0.1.0`

3.  Create a hotfix branch. NOTE: make sure you are in fetched branch before to create a hotfix branch

```
    git checkout hotfix-whatToHotfix-version

    example: git checkout hotfix-whatToHotfix-v.0.1.0
```

4.  Please don't ever pull in master branch, because we are hot fixing a certain issue in a production version.
5.  Micro commit in every changes. So we can easy to track what changes have done in branch
6.  push your branch local in origin
7.  Pull request to version branch to hot-fix
