# Introduction to Github

## Learning Objectives

* Describe the differences between Git and Github
* Explain what is an Upstream Repo
* Fork, Clone, and Add WDI Curriculum as an Upstream Repo
* Describe Github Features including Issues, Branches, and Pull Requests
* Fork Github quiz repo, Create a solution_quiz_branch, and Create a Pull Request

## Framing (10 min)

<!--OPENING  -->
Review Git Basics
<!--Git is a touch concept, can I get a fist to five from everyone on how they are feeling about git ? -->

<!--Ideas:
1. Drawing diagrams on board, students filling them in?
2. 5 MIN Q & A for anything unclear about git?
3. Quick exercise making commits?
4. Asking Quiz Questions to students?
-->
1. What is the most common workflow for creating save points while working locally?
2. What commands are used to share changes (commits) between repos?
3. Describe the fork/clone model, and how it is used for HW submission.
4. What are the differences between git and github?

<!--Introduction To New Material-->

## Git versus Github (10 min)

* Git is the version control software we use locally on our computers in order to keep track of our files, directories, and our modifications to them in a central repository.
* GitHub is a public hosting site for storing repositories. It's a place where all of our repos are stored remotely on a server.
* It's literally a "hub" for storing Git repositories and a social platform for people to collaborate and work on open source projects
* Github is not only used for software development. It can be used for any collaboration projects. You can store text documents or other file types.
* Most of repos on Github are Public. Github is Open Source to encourage collaboration

### Why do we use Github? (5 min)

* Visual Interface to See and Navigate Through our Repositories
* Provides a Remote Backup/Copy of our files
* Allows for Collaboration and Sharing Work Easy
* Provides an issue tracking system
* Place to Show Work off to Employers

## Git Remote: Upstream, Fetch, and Pull (10 min)

<!--Does Anyone Remember How to Add a Remote Git Repo?-->

![Git Pull Upstream](git06.jpg)

After we have already forked and cloned someone else's repository onto our local machine - we need a way to be able to update our local copy with any changes being made to that master repository.

One of the ways we can do this is by establishing a link to this remote repository that points "upstream" to that repo on Github so that we can get all the changes anytime we want.

The convention is to add an `upstream` remote.

The upstream repo could be compared to the gatekeeper of the project or the original repo. Your forked copy is typically called the origin repo

```
$ git remote add upstream <original_github_repo_url>

```
This remote is where we can pull from at any time, but do not have permission to push our changes.

<!--SHOW TRYING TO PUSH UP TO MASTER, DON'T PUSH UP -->

## YOU-DO Fork and Clone the Curriculum Repo (5 min)

Fork the Curriculum Repo to your personal account. Clone your fork to your computer in your ~/wdi folder.

NOTE: If you already have a curriculum folder in your ~/wdi folder, delete or rename it before you clone.

## YOU-DO: Setup Upstream for Curriculum Repo (10 min)
1. Students should visit the [Curriculum](https://github.com/ga-dc/curriculum)'s page and copy the ssh clone url to the clipboard
2. In our terminal, change directories into our local curriculum directory
```
# in ~/wdi
$ cd curriculum
```
3. See all current remotes with:
`$ git remote -v`
4. Add a new remote named upstream to our repository
5. Pull down updates from the upstream remote

```
$ git pull origin upstream
```

## Break (10 min)

## Github Features: Issues, Branches, Pull-Requests, and Merging

### Creating Issues on Github (5 min)

An Issue is a note on a repo regarding some matter that needs attention. It could be a bug, a suggestion for a new feature, a question about the repo or code, etc! On GitHub you can also label, search and assign issues, which help with managing projects.

In this example, we have a github practice repository, but it's completely empty and there is no README [main information page you see on github repos]! It needs more information so students know what the heck this repo is about. Let's open an Issue!

### I-DO: Create a Github Issue

Now this issue has a permanent home (URL) that you can reference even after it is closed. Next, we need to work towards adding a README and closing this issue. Let's make a new branch....

### Think/Pair/Share-1/3/6: Why Branches?  (15 min)

We are going to start with reading [Git Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging/).  This is an introduction to branching.

Instructions: Take 5 minutes to read up to Basic Merge Conflicts and STOP THERE (5 min).

Take another minute to think about why branches/branching are important. Now, turn and talk with your neighbor and discuss your thoughts.

Now, turn and share with your neighbor your thoughts, and we'll share what we feel is important.

Q. Why is branching an important part of git?

---
> A. Branches are useful for many reasons, but some of the most common ones:

> 1. EXPERIEMENTATION -To allow experimentation. By switching to a new branch, we can experiment,
and if the experiment fails, we can delete it and easily switch back to master
(or another branch of our choice). If it succeeds, we can merge those changes
into master.
2. WORKFLOW/COLLABORATION-To allow work to proceed on multiple features (or by multiple people) without
interfering. When a feature is complete, it can be merged back into master.
3. EASILY FIX BUGS-To allow easy bug fixes on a stable version while features are being developed.

<!--NEED VISUAL TOOL LESSON BRANCHES-->

### What are Branches? (5 min)

A branch in git is just a label on a particular commit in a repository, along
with all of it's history (parent commits).

What makes a branch special in git (vs a tag), is that we're always *on* a
specific branch, and when we commit, the current branch label moves forward to
the new commit. Another way to say that is the branch label always stays at the
tip of the branch.

![Git Branch Diagram](https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/01.svg)
> The diagram above visualizes a repository with two isolated lines of development, one for a little feature, and one for a longer-running feature. By developing them in branches, it’s not only possible to work on both of them in parallel, but it also keeps the main master branch free from questionable code.

> From [Atlassian - Git Branching Tutorial](https://www.atlassian.com/git/tutorials/using-branches/git-branch)

### I-DO: Create a new branch (5 min)

Let's create a new branch called Add-Readme.

`git branch Add-Readme` - create a new branch called Add-Readme
`git checkout Add-Readme` - switch to this particular branch

We can combine these two steps into one by doing the following:
`git checkout -b <new_branch_name>`

Let's add a readme.md file, add a few sentences about this repo, then commit our changes.

`$ touch readme.md`
`$ git add readme.md`
`$ git commit -m "Inital Commit"`

Now, we need to push this branch to our Repo Remote. We want to make sure to push origin <branch_name>, not push origin master

`$ git push origin Add-Readme`

## Common Commands for Managing Branches

* `git branch <new_branch_name>` - create a new branch
* `git checkout <branch_name>` - switch to a specific branch (checks out tip commit and makes branch active)
* `git checkout -b <new_branch_name>` - create a new branch and check it out in one step
* `git branch` - list local branches (`-a` lists local and remote)
* `git branch -d <branch_to_delete>` - delete a branch
* will not let you delete if branch isn't merged into another branch (i.e. would cause data loss)
* `git branch -D <branch_to_delete>` - over-rides and deletes a non-merged branch
* `git merge <branch_name>` - merges `<branch_name>` into the current branch, creating a new merge commit in the process

### Pull Requests (10 min)

Pull Requests are an important part of collaborating on GitHub.

By making a PR, you’re requesting that someone pull in your changes and merge them into their branch. A PR allows you to compare the content on two branches, and all the changes or diffs(differences) are highlighted in green and red.

As soon as you make a change, you can open a Pull Request. People use Pull Requests to start a discussion about commits (code review) even before the code is finished. This way you can get feedback as you go or help when you’re stuck.

It's good practice to even make a Pull Request for branches in your own repository and merge it yourself to get more comfortable with PRs!

A Pull-Request is a way for us to incorporate our feature branch and work back into our master branch. You can merge any branch into your current branch with the git merge command locally. However, we are completing this process on our remote repo through a PR.

### I-DO: Create a Pull-Request and Merge Changes

Let's Review our Pull-Request, and Merge it back into the Master Branch. TADA! Now we have a readme.

## Break (10 min)

## OverView of GitHub Workflow(5 min)
> From [Github Guides](https://guides.github.com/introduction/flow/)

To Recap, In Software Development, Github is very useful in managing and tracking updates and changes to our code.

1. Discuss

Discuss an idea for a new feature on the project mailing list. Agree on what needs to be done.

2. Specify

Create a Github issue for the feature.
It's often useful to write the ticket as a brief functional spec, documenting the requirements as user stories. Github's support for checkboxes in markdown is useful here:

3. Create a Branch

Create a feature branch off the master to work on this issue:
```
$ git checkout -b [name of branch that solves issue]

```
Writing a name that has meaning to the issue we are working on

4. Work and commit onto your branch

Make changes/commits commits locally, then push your branch up to our remote repository

5. Open a Pull-Request or PR

6. Merge Branch into Master


## YOU-DO - Pushing and PRs from Branches (10 min)

Many OSS projects request that you create pull requests from a non-master branch.

1. Fork and Clone https://github.com/ga-dc/git-tricks.
2. Create and switch to a branch called `<your_name>_suggestion`.
3. Add your own "trick".
4. Commit, and push that change to your remote called 'origin' (your fork)
```
$ git push origin '<your_name>_suggestion'
```
5. Create a pull request from that branch to the upstream (ga-dc) master branch

## YOU-DO - Submit an Issue to this Repo (5 min)

Please Include Your LastName in the title of the Issue. Include in the content of the issue

1. On a Scale from 1-5 how you are feeling about Git and Github
2. What aspect of Git and Github are you still confused about


## Closing (5 mins)

Additional Exercises:

* Please go back into Github and make sure your profile has your accurate FULL NAME, and a relevant Photo of you. Your presence on github is important! Potential employers will visit your profile!
