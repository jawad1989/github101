# GIT
Git is the open source distributed version control system that facilitates GitHub activities on
your laptop or desktop. This cheat sheet summarizes commonly used Git command line
instructions for quick reference

[GIT Official BOOK](https://book.git-scm.com/book/en/v2/Getting-Started-About-Version-Control#ch01-getting-started)

![GIT](https://github.com/jawad1989/github101/blob/master/images/centralized-1.png)

# Subversion VS GIT 

![SCMvsVCS](https://github.com/jawad1989/github101/blob/master/images/centralized-vs-distributed.png)

# GIT BASIC COMMANDS

## Install

GitHub for Windows `https://windows.github.com`
GitHub for Mac `https://mac.github.com`
Git for All Platforms `http://git-scm.com`
Git distributions for Linux and POSIX systems are available on
the official Git SCM web site.

## Configuring Tooling

Configure User Information for all local repos
```
git config --global user.name "[name]"
Sets the name you want attached to your commit transactions
```
```
git config --global user.email "[email address]"
Sets the email you want attached to your commit transactions
```
```
git config --global color.ui auto
Enables helpful colorization of command line output
```

## Creating Repositories
When starting out with a new repository, you only need to do it
once; either locally, then push to GitHub, or by cloning an
existing repository.
```
git init
Turn an existing directory into a git repository
```
```
git clone [url]
Clone (download) a repository that already exists on
GitHub, including all of the files, branches, and commits
```

## Branches
Branches are an important part of working with Git. Any
commits you make will be made on the branch you're currently
“checked out” to. Use git status to see which branch that is.
```
git branch [branch-name]
Creates a new branch
```
```
git checkout [branch-name]
Switches to the specified branch and updates the
working directory
```
```
git merge [branch]
Combines the specified branch’s history into the
current branch. This is usually done in pull requests,
but is an important Git operation.
```
```
git branch -d [branch-name]
Deletes the specified branch
```

## Synchronize Changes
Synchronize your local repository with the remote repository
on GitHub.com
```
git fetch
Downloads all history from the remote tracking branches
```
```
git merge
Combines remote tracking branch into current local branch
```
```
git push
Uploads all local branch commits to GitHub
```
```
git pull
Updates your current local working branch with all new
commits from the corresponding remote branch on GitHub.
 git pull is a combination of git fetch and git merge 
```
## Make Changes

Browse and inspect the evolution of project files
```
git log
Lists version history for the current branch
```
```
git log --follow [file]
Lists version history for a file, including renames
```
```
git diff [first-branch]...[second-branch]
Shows content differences between two branches
```
```
git show [commit]
Outputs metadata and content changes of the specified commit
```
```
git add [file]
Snapshots the file in preparation for versioning
```
```
git commit -m "[descriptive message]"
Records file snapshots permanently in version history
```

## Redo Commits
Erase Miskates and craft replacement history
```
git reset [commit]
Undoes all commits after [commit], preserving changes locally
```
```
git reset --hard [commit]
Discards all history and changes back to the specified commit
```

## Stashing 
Think of the Stash as a clipboard on steroids: it takes all the changes in your working copy and saves them for you on a new clipboard. You're left with a clean working copy, i.e. you have no more local changes.

Later, at any time, you can restore the changes from that clipboard in your working copy - and continue working where you left off.

You can create as many Stashes as you want - you're not limited to storing only one set of changes. Also, a Stash is not bound to the branch where you created it: when you restore it, the changes will be applied to your current HEAD branch, whichever this may be.

``` 
after add .
git stash
```

you will see, once you try to commit it wont show anything to commit. to bring it back 
```
git stash list
git stash pop
or
git stash apply <stashname>
```

## Glossary
__git:__ an open source, distributed version-control system.<br/>
__GitHub:__ a platform for hosting and collaborating on Git repositories<br/>
__commit:__ a Git object, a snapshot of your entire repository compressed into a SHA<br/>
__branch:__ a lightweight movable pointer to a commit<br/>
__clone:__ a local version of a repository, including all commits and branches<br/>
__remote:__ a common repository on GitHub that all team member use to exchange their changes<br/>
__fork:__ a copy of a repository on GitHub owned by a different user<br/>
__pull request:__ a place to compare and discuss the differences introduced on a branch with reviews, comments, integrated
tests, and more<br/>
__HEAD:__ representing your current working directory, the HEAD pointer can be moved to different branches, tags, or commits
when using git checkout



## Git Workflows

### Git Flow

The Git Flow is the most known workflow on this list. It was created by Vincent Driessen in 2010 and it is based in two main branches with infinite lifetime:
![GITFLOW](https://github.com/jawad1989/github101/blob/master/images/356-3561396_gitflow-workflow-git-flow-hd-png-download.png)

* master — this branch contains production code. All development code is merged into master in sometime.
* develop — this branch contains pre-production code. When the features are finished then they are merged into develop.
During the development cycle, a variety of supporting branches are used:
* feature-* — feature branches are used to develop new features for the upcoming releases. May branch off from develop and must merge into develop.
* hotfix-* — hotfix branches are necessary to act immediately upon an undesired status of master. May branch off from master and must merge into master anddevelop.
* release-* — release branches support preparation of a new production release. They allow many minor bug to be fixed and preparation of meta-data for a release. May branch off from develop and must merge into master anddevelop.

### GitHub Flow
[More Details](https://guides.github.com/introduction/flow/)



The GitHub Flow is a lightweight workflow. It was created by GitHub in 2011 and respects the following 6 principles:
Anything in the master branch is deployable

![GITHUBFLOW](https://github.com/jawad1989/github101/blob/master/images/github-flow-2.png)

To work on something new, create a branch off frommaster and given a descriptively name(ie: new-oauth2-scopes)
Commit to that branch locally and regularly push your work to the same named branch on the server
When you need feedback or help, or you think the branch is ready for merging, open a pull request
After someone else has reviewed and signed off on the feature, you can merge it into master
Once it is merged and pushed to master, you can and should deploy immediately


### Git Lab Flow

The GitLab Flow is a workflow created by GitLab in 2014. It combine feature-driven development and feature branches with issue tracking. The most difference between GitLab Flow and GitHub Flow are the environment branches having in GitLab Flow (e.g. staging and production) because there will be a project that isn’t able to deploy to production every time you merge a feature branch (e.g. SaaS applications and Mobile Apps)

![More Details](https://github.com/jawad1989/github101/blob/master/images/environment_branches_gitLab.png)

The GitLab Flow is based on 11 rules:
* Use feature branches, no direct commits on master
* Test all commits, not only ones on master
* Run all the tests on all commits (if your tests run longer than 5 minutes have them run in parallel).
* Perform code reviews before merges into master, not afterwards.
* Deployments are automatic, based on branches or tags.
* Tags are set by the user, not by CI.
* Releases are based on tags.
* Pushed commits are never rebased.
* Everyone starts from master, and targets master.
* Fix bugs in master first and release branches second.
* Commit messages reflect intent.

[More Details](https://about.gitlab.com/blog/2014/09/29/gitlab-flow/)
