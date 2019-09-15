# Manage Git

### Clone the project

```bash
$ git clone git@github.com:Ubidy/Ubidy_ReactStarterKit.git
```

### Develop a new feature in 'master' branch

##### 1. Create a feature branch based off of master.

```bash
$ git checkout master
$ git checkout -b INITIALNAME-TICKETNUMBER `eg. JSL-GEN-143`
$ git push —set-upstream INITIALNAME-TICKETNUMBER
```

##### 2. Develop the code for the new feature and commit as you go.

```bash
// make changes
$ git add -A
$ git commit -m `"GEN-143 : AFFECTED: PROFILE VIEWER : CHANGES: ENHANCE LOADING"`

// make more changes
$ git add -A ...to add all
$ git commit -m `"GEN-143 : AFFECTED: PROFILE VIEWER : CHANGES: ENHANCE LOADING"`
```

##### 3. Push your branch to remote.

```bash
// make sure that you commit all changes before git pull
$ git pull origin master

// if you have conflict you need to resolved it first
$ git push --set-upstream origin JSL-GEN-143
```

#### 4. Make a pull request using github website

Navigate to the project on Github and open a pull request with the following
branch settings or **[click here](https://github.com/juztinlazaro/developers-paperback/Ubidy_ReactStarterKit/pulls)**

- Step 1: Click **"New pull request"** button
- Step 2: Choose a base branch **"master"** and make sure the compare branch is **"your new branch"**
- Step 3: Select a user as reviewer
- Step 4: Add Comment or description **e.g. Please code review and merge**
- Step 5: Click **"Create pull request"** button
- Step 6: Contact the person you have selected to review your code and have a decision who will merge the pull request

## Branch name template

```bash
$ git checkout -b {JIRA TICKET NUMBER}
```

## How to undo (almost) anything with Git

**[click here](https://github.com/blog/2019-how-to-undo-almost-anything-with-git)**
