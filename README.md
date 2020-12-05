# Git Flow

## Table of Contents

**[Cloning a repo and changing the remote url](#Cloning-a-repo-and-changing-the-remote-url)**<br>
**[Basic Git Workflow](#Basic-git-work-flow)**

## Cloning a repo and changing the remote url

(These steps are only for when you initially clone a project repo. Not when you clone your partners repo to collaborate together. To do that, you only have to complete step 1!)

### 1. The first step is to clone the repo!

- Navigate to the repo you want to clone and hit the big green code button. Copy the link given.

![clone-repo](./clone-repo.png)

- Navigate in your terminal to the directory where you want this repo to live. I chose ~/Documents/appAcademy
- `git clone HTTPS://LINKTOURL/THATYOUCOPIED`

![git-clone](./git-clone.png)

### 2. Sweet, you have the cloned repo in your preferred directory. Now lets make your own repo. On github, create a new repository.

- Default settings are fine. Hit the big green button `Create Repository`

![create-repo](./create-repo.png)

### 3. Next, copy the .git link that is on the next page. Do not do any other steps on this page - That is for when you do not clone a repo.

![your-dotgit](./your-dotgit.png)

### 4. Whenver you clone a repo it already has a .git directory with certain configurations set up. To be able to push this repo to your newly created GitHub repo we have to change the remote origin.

- To do that, just run this command: (Make sure you are inside the repo you cloned)

  - `git remote set-url origin https://LINK/TO/YOUR/GIT/THAT/YOU/COPIED/FROM/PREVIOUS/STEP.git`

  ![set-url](./set-url.png)

### 5. Thats its! You can now run `git push` and it will push to your newly created repo. Try it out :)

---

## Basic Git work flow.

- After making changes to a file and you are ready to commit / push to your repo you can run the following commands:

  - `git add .` - stages modifed files to be committed.
  - `git status` - displays files that have been modified
  - `git commit -m 'A hopefully helpful commit message'` - commits the changes to your local repo. Get in the habit now of making helpfull commit messages
  - `git push` - pushes your local commits to your github repo!

- To pull down changes that your partner pushed to the repo you simply have to run:
  - `git pull` - this will fetch the most recent updates!





## **Gitting Started with Git**

- Version Control Systems help us keep track of changes over time.

  - VCS tools abstract the work of keeping projects and programmers in sync with one another.

- **`Git`** is the most popular VCS in use today.

* **`Repository`** : Comprises all the source code for a particular project.

* **`Commits`** : collection of changes grouped towards a shared purpose.

  ![msg and hash](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Module-JavaScript/git/assets/image-git-timeline.svg)

* **`Commit Messages & Commit Hashes`** :
  Git id's your commits with a specially generated series of letters and numbers called a Hash, and a detailed message describing the commit.

  - They are 40 characters long, but by default Git abbreivates hashes to 7 characters.

* **`References`** : Way to alias a commit in plain english.

  - **`HEAD`** : default reference that points to the most recent commit.

* Git maintains three lists of changes:
  - **`Working Directory`**
    - Keeps all of your in-progress changes.
  - **`Staging Area`**
    - Reserved for changes you're ready to commit.
  - **`Commit History`**
    - Made up of changes you've already committed.

**Tracking Changes in a Repository**

- **`Git Init`** : Allows you to start a repository in your current directory.

- **`Git Add`** : Adds content to your repository.

- **`Git Status`** : Used to check what has been staged in your repository.

- **`Git Commit -m`** : Used to commit your changes/additions into the commit history - flag is used to add a message to your commit.

- **`Git Log`** : Used to check your repo's commit history.

**Branches and Workflow**

- **`Branch`** : Basically a seperate timeline in Git, reserved for it's own changes - Master is the default branch.

- **`Git branch [name of branch]`** : Used to reate a new branch.
  ![img of branch](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Module-JavaScript/git/assets/image-git-branch.svg)

- **`Git Checkout`** : Used to switch to an existing branch.

**Bringing it Back Together**

- **`Git Merge`** : Used to integrate one branch into another.

**Connecting with the world via Github**

- **`DCVS`** : Distributed Version Control System - built in support for managing code both locally and from a distant source.

- We typically refer to the primary remote of a repo as the **`origin`**.

- We `clone` a distant repo once, use `pull` to update it and `push` our own code into it.

**Collaboration via Git and Github**

```js
> git branch add-my-new-file
> git add my-new-file.js
> git commit -m "Add new file"
> git push -u origin add-my-new-file
```

This is the typical push workflow.

- **`-u`** flag stands for **`--set-upstream`**.
- **`Git Pull`** : Used to update your files from remote repo - behind the scenes this is a combination of Git Fetch and Git Merge.
  ![git pull behind](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Module-JavaScript/git/assets/image-git-pull-parts.svg)

- **Pull Request** : Feature specific to Github, used as a safety net to prevent bugs and is a critical aspect of collaboration workflow.
  1. Push your code to GH on it's own branch.
  2. Open pull request via a base branch.
  3. GH creates a comparison page for your new code vs existing.
  4. Your teammates review for errors.
  5. Make changes based on feedback and push new commits upwards.
  6. PR automatically makes changes.
  7. If everyone is satisfied, a repo maintainer will merge your branch.
  8. Your code is now on the main branch - nice!

---

## **Managing your Github Repository**

- **`Git Diff`** : Used to visualize any tracked differences in our repository.
  ![img of diff](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Module-JavaScript/git/assets/image-git-diff-output.svg)

* **`---`** & **`+++`** : let's us know there are both additions & subtractions in our js file.
* **`@@`** : shows use where our chunk of changes are line-wise.

**Diff Options**

- By default git diff compares the cwd to the last commit.
  - If we append **--staged** we can compare the staging area instead of the cwd.
- There are many other ways to use git diff to compare as well!

```js
# See differences between the 'feature'
# branch and the 'master' branch.
> git diff master feature

# Compare two different commits
> git diff 1fc345a 2e3dff

# Compare a specific file across separate commits
> git diff 1fc345a 2e3dff my-file.js
```

**Time Travel**
![checkout](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Module-JavaScript/git/assets/image-git-checkout.svg)

- Using Git Checkout is entirely non-destructive.
- Git checkout has a few special characters and reserved references.

```js
# You can checkout a branch name.
# You'll be using this particular branch a lot!
> git checkout master

# You can also use commit hashes directly
> git checkout 7d3e2f1

# Using a hyphen instead of a hash will take
# you to the last branch you checked out
> git checkout -

# You can use "HEAD~N" to move N commits prior
# to the current HEAD
> git checkout HEAD~3
```

---

## **Git Do-over: Reset and Rebase**

- **Git Reset** : Can be used to travel back in time before a bug or error occured.
  - **--soft** : appended to reset to move our HEAD ref to the commit we specified - does not touch our code, only resets commit messages.(least dangerous!)
  - **--mixed** : Default state of Git reset, changes are preserved but they are removed from the commit history straight to the working directory.
  - **--hard** : Adjust head ref and totally destroy any interim code changes

**Rebase: An Alternative Form of Time Travel**

- **Git Rebase** : Involves changing your current branch's base branch.
  - Rebasing is a dangerous process that involves re-writing history.
    ![diagram of rebase](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Module-JavaScript/git/assets/image-git-rebase-before-and-after.svg)

**The Golden Rule of Git**

> Never change the history of a branch that's shared with others.

- This rule refers to git reset and git rebase.
- Just don't use these on any branch that is shared with others!!!

---

## **Git Merge Conflicts & You**

- **Merge Conflict** : Special state that Git presents to us when two branches have code changes that are incompatible with each other.
  ![conflict img](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Module-JavaScript/git/assets/image-git-merge-conflict.svg)

**Conflict Resolution**
![img of conflict](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Module-JavaScript/git/assets/image-git-merge-conflict-inline-operators.svg)

- The <<< === >>> signs are delimiters to indicate we are separating two pieces of conflicting code.
- The first piece is from our Base Branch.
- The second piece is from our incoming branch.

---
