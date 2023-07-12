# Git and Remote Repositories

![Remote_Repositories](/images/git_remote_repositories.png)

## Hot to setup a remote repository

A remote repository can in principle be hosted on any server, and so long as you have the right permissions to access such a server, you can use any server to house your remote repository. Companies often manage their own set of servers to have more tight control over their data, or may hire specialized companies for that.

GitHub is a platform dedicated to host Git repositories, and over the years it has added a considerable amount of functionality that helps making the creation and management of repositories, not only easier but also safer.

There are multiple guides on how to create repositories on Github but [this one from GitHub](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository) is particularly useful.

It is important to note that while it is possible to use HTTPS protocol to specify the repository's remote URL, in some cases you may need to use a Secure SHell, or SSH, protocol to do so.

SSH is a cryptographic network protocol that enables exchange of data over unsecure networks. It requires the user to issue a private/public key pair.

## Some Nomenclature

**Fork**: a remote repository that is a copy of another repository. In GitHub (and in other VCSs) forks are used so that individuals and teams can independently work on projects after which they submit their changes to the original repository by issuing a "pull request".

**Pull Request**: Is the mechanism by which someone working on a copy of a remote repository (a fork) can request the owner of the original remote repository to evaluate a set of new changes to be included in the original remote repository.

**Origin**: An _alias_ on the local machine to refer to the remote repository associated with a git directory. It harbors the URL to a remote repository to which a project is connected to. Typically we speak of a single repository from which to _fetch_ data from and _push_ data to, but they can also be specified to be different.

## How to locally configure a remote repo

To configure the remotes that you want to fetch from, you can use the `git remote` command to add, remove, rename, or modify the remote repositories that you have configured¹. For example, to add a new remote named `upstream` with the URL `https://github.com/user/repo.git`, you can use:

```bash
git remote add upstream https://github.com/user/repo.git
```

To remove a remote named `upstream`, you can use:

```bash
git remote remove upstream
```

To rename a remote named `origin` to `main`, you can use:

```bash
git remote rename origin main
```

To change the URL of a remote named `origin` to `https://github.com/user/new-repo.git`, you can use:

```bash
git remote set-url origin https://github.com/user/new-repo.git
```

You can also use the `-v` flag with the `git remote` command to see the URLs that Git has stored for each remote¹. For example, to see the URLs of all your remotes, you can use:

```bash
git remote -v
```

By default, Git uses the remote named `origin` as the default remote to fetch from, unless there is an upstream branch configured for the current branch². You can change the upstream branch for a local branch by using the `git branch --set-upstream-to` or `git branch -u` command². For example, to make the local branch `master` track the remote branch `master` from the remote `upstream`, you can use:

```bash
git branch -u upstream/master master
```

## Get info from your remote repository

To know the exact URL of the _origin_ enter **```git remote -v```** in the command line or for a more verbose option type **```git remote show origin```** .

To get to know which remote branches on the remote repository are being tracked, type:
**```git branch -r```**

To get the history of commits on the origin type **```git log origin/<master-branch-name> [-p]```**

**```git status```** will say if your local repository is fully updated with respect to the remote one.

To fully update your local repository with new changes in the remote repository use **```git pull```**. This is an express way of implementing in your local repository all remote changes. However, if you want to have more control over which changes you want to update your local repo with, then use **```git fetch```** and use **```git merge```** to select which changes you want to commit locally. However, this will apply only to the branch you are on. If you have a project with multiple branches, locally and remotely, and you want to fetch all the changes in all branches, use **```git fetch --all```**, or **```git remote update```**  

## How to locally set a branch to track a remote one?

To set a branch to track a remote one, you can use the git branch --set-upstream-to or git branch -u command. This command sets up the tracking information for the local branch, which can be the current branch or a specified one. For example, to make the local branch foo track the remote branch foo from the remote origin, you can use:

**```git branch -u origin/foo foo```**

Alternatively, you can use the --track flag with the git checkout command to create a new local branch with the same name as the remote one and directly establish a tracking connection between the two. For example, to create and track the remote branch bar from the remote origin, you can use:

**```git checkout --track origin/bar```**

To change the remote a branch is tracking, you can use the same git branch --set-upstream-to command with a different remote name and branch name. For example, to make the local branch foo track the remote branch baz from the remote upstream, you can use:

**```git branch -u upstream/baz foo```**

## How to implement selective changes in a local repo

There are different ways to decide which changes to accept locally and which to reject, depending on the situation and the tools you use. Here are some common methods:

- If you want to merge selective changes from one branch to another, you can use the **`git checkout`** command with the `--track` or `-p` flags to create a new branch or pick hunks from another branch. You can also use the **`git cherry-pick`** command to apply specific commits from another branch.
- If you encounter merge conflicts while merging two branches, you can use a tool like GitHub or VS Code to resolve them visually². You can also use a 3-way merge editor to compare the changes from both branches and the common ancestor². You will need to edit the conflicting lines manually and remove the annotations added by Git.
- If you want to discard your local changes and accept the remote changes, you can use the **`git reset --hard`** command to reset your working tree and then use the `git pull` command to update your branch³. You can also use the **`git clean -f`** command to remove any untracked files.

## The "Three-Way" Merge

A **three-way merge** in Git is a process of combining the changes from two branches that have diverged from a common base commit. Git performs a three-way merge when you run git merge with a branch that is not a direct ancestor of your current branch. In this case, Git will find the most recent common ancestor of the two branches, and compare it with the tips of the two branches to determine what changes to apply.

A three-way merge can result in: (a) a _fast-forward merge_, (b) a _non-conflicting merge_, or (c) a _conflicting merge_.

A **fast-forward merge** occurs when the common ancestor is the same as the current branch, and Git simply moves the branch pointer to the target branch.

A **non-conflicting merge** occurs when the changes in the two branches do not overlap, and Git can automatically create a new merge commit that combines both changes.

A **conflicting merge** occurs when the changes in the two branches affect the same lines or files, and Git cannot decide which version to keep. In this case, Git will mark the conflicts in the affected files and ask you to resolve them manually.

In the case of conflicting merge, to troubleshoot these situations, it is helpful to visualize what is at stake. We can make use of **```git log --graph --oneline --all```** to obtain a sketch of the history of commits and identify divergence in the branches. To get more details about specific commits we can use **```git log -p origin/<name-of-local-branch>```**. Eventually, a conflicting merge has to be implemented manually, and the conflicting code edited out.

## How to push a new branch to the remote repo

To create a remote branch in Git, you need to have a local branch that you want to publish on the remote repository. You can create a local branch using the `git checkout -b <branch-name>` command, or check out an existing one using the `git checkout <branch-name>` command.

Once you have a local branch ready, you can push it to the remote repository using the `git push <remote-name> <branch-name>` command, where `<remote-name>` is usually `origin`, the default name for the remote you cloned from. This will create a new branch on the remote repository with the same name as your local branch, and upload your local commits to it.

You can also use the `-u` option with `git push` to set up a tracking relationship between your local and remote branches. This will make it easier to sync your changes in the future, as you can simply use `git push` or `git pull` without specifying the remote or branch names. For example:

`git push -u origin <branch-name>`

## Merging versus Rebasing - What is the difference?

Both `git merge` and `git rebase` are commands that integrate changes from one branch into another. However, they do it in different ways.

`git merge` creates a new commit that combines the changes from the current branch and the target branch. This preserves the history of both branches as it happened, but it also introduces a merge commit that may not be very informative. `git merge` is a non-destructive operation that does not change the existing branches.

`git rebase` rewrites the history of the current branch by replaying its commits on top of the target branch. This results in a linear and clean history, but it also modifies the original commits and erases any divergence between the branches. `git rebase` is a destructive operation that changes the existing branches.

The choice between `git merge` and `git rebase` depends on your preferences and workflow. Some advantages of `git merge` are:

- It is easier and safer to use, especially for beginners.
- It preserves the complete history and context of your project.
- It does not require you to resolve conflicts more than once.

Some advantages of `git rebase` are:

- It avoids creating unnecessary merge commits.
- It creates a more readable and logical history.
- It makes it easier to use commands like `git log`, `git bisect`, and `git blame`.

> Note: When a project has multiple branches with several collaborators, having a linear history can help identify a bug. Having a log structure with many branches as a result of `git merge` can make debugging difficult and in those instances `git rebase` can be helpful.

For more information, you can check out these resources:

- [Merging vs. Rebasing | Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/merging-vs-rebasing) ¹
- [What's the difference between 'git merge' and 'git rebase'? - Stack Overflow](https://stackoverflow.com/questions/16666089/whats-the-difference-between-git-merge-and-git-rebase) ²
- [Differences Between Git Merge and Rebase — and Why You Should Care](https://blog.git-init.com/differences-between-git-merge-and-rebase-and-why-you-should-care/) ³
- [What is the Difference Between Git Merge vs Git Rebase?](https://dev.to/firstfingerin/what-is-the-difference-between-git-merge-vs-git-rebase-4m78) ⁴
- [Git Merge vs Rebase | Which Is Better? | Perforce](https://www.perforce.com/blog/vcs/git-rebase-vs-merge-which-better) ⁵

## How to perform a Rebase

To perform rebasing in Git, you need to follow these steps:

1. Check out the branch that you want to rebase onto another branch. For example, if you want to rebase your `feature` branch onto the `main` branch, you would run:

`git checkout feature`

2. Run the `git rebase` command with the name of the branch that you want to rebase onto. For example, if you want to rebase onto the `origin/main` branch, you would run:

`git rebase origin/main feature`

This will move all the commits from your `feature` branch on top of the latest commit from the `main` branch, and replay them one by one. If there are any conflicts, you will need to resolve them manually and then continue the rebase with `git rebase --continue`.

3. Once the rebase is done, you can push your rebased branch to the remote repository. If you have already pushed your original branch before, you will need to use the `--force` option to overwrite it. For example:

`git push --force origin feature`

However, be careful when using `--force`, as it can cause problems for other collaborators who have based their work on your original branch. You should only use it if you are sure that no one else is working on or depending on your branch.

For more information, you can check out these resources:

- [Git Rebase - How Tow Use Git Rebase | W3Docs Online Git Tutorial](https://www.w3docs.com/learn-git/git-rebase.html)
- [Git - Rebasing](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)
- [git rebase | Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase)
- [Git Rebase - javatpoint](https://www.javatpoint.com/git-rebase)

## Resolving Conflicts in Rebasing

When rebasing, in the event of a conflict, Git gives 3 options:

- To abort rebasing
- To skip the conflicting file(s)
- To resolve the conflict manually

In the case of manual resolution of the conflict, during the rebasing process (as during with mergers), the manually intervened files need to be staged, and then rebasing should be resumed. In other words:

1. **`git add <conflict-file-name.ext>`**
2. **`git rebase --continue`**


## Setting locally a new URL for the remote repository

Sometimes you make a typo in naming a file, and it needs to be changes. Other times, you make a type in naming a remote repository and it needs to change.

It can also happen, that the server configurations where your remote repo is located are changed, so that to access it, you need to change the URL locally so that your machine can continue on Pulling and Pushing.

If that happens:

You can change the URL of a remote repository in Git using the `git remote set-url` command. This command takes two arguments: the remote name and the new repository URL. For example, if you want to change the URL of the remote repository named `origin`, you can use the following command:

```
git remote set-url origin NEW_REPOSITORY_URL
```

Make sure to replace `NEW_REPOSITORY_URL` with the actual URL of the new repository.

