# Introduction to Git

![Git Branching](/images/Git_logo.png "What is Git?")

## Table of Contents

1. [What is Git?](#what-is-git)
2. [How Git Works](#how-git-works)
   1. [Staging & Committing: The basic workflow](#staging--committing-the-basic-workflow)
   2. [Branching and Merging](#branching--merging)
   3. [Checkout: traveling along and between branches](#checkout-traveling-along-and-between-branches)
   4. [Interacting with remote repositories](#interacting-with-remote-repositories)
3. [How to get and run Git](#how-to-get-and-run-git)
4. [The anatomy of Git](#the-anatomy-of-git)
5. [Git operations and commands](#git-operations-and-commands)
   1. [Initializing Git](#initializing-git)
   2. [Checking the status of the working tree](#checking-the-status-of-the-working-tree)
   3. [Staging a file](#staging-a-file)
   4. [Committing changes to the repository](#committing-changes-to-the-repository)
   5. [Checking the history of commits](#checking-the-history-of-commits)
   6. [Creating, deleting and moving between branches](#creating-deleting-and-moving-between-branches)
   7. [Working on new branches](#working-on-new-branches)
   8. [Merging branches - Updating with new files](#merging-branches---updating-with-new-files)
   9. [Merging branches - Updating with existing files](#merging-branches---updating-with-existing-files)
   10. [Managing merge conflicts](#merge-conflicts)
   11. [Renaming tracked files using Git](#renaming-tracked-files-using-git)

## What is Git?

![VCS](/images/VCS_diagram.jpg)

[Git](https://git-scm.com/) is a popular open source and distributed (i.e. non-centralized) [Version Control Software](https://www.softwaretestinghelp.com/version-control-software/) (VCS) that enables tracking different versions of files during content development for digital projects (mostly, programming/coding projects). Git keeps a record of the different versions a file has had and allows users to rollback to previous instances of a project.

The ability to run back the clock to access files as they were at an earlier point in time is a key feature of Git (and other VCSs) as it allows to easily implement changes when anything needs to be corrected and instead of starting from scratch.

In addition, Git supports non-linear development. That is to say that Git allows projects to be slipt into branches, and for each branch to to be dedicated to the development of a particular feature that may be merged with the main project branch once the feature is ready to be deployed.

Finally, Git is not only a VCS, but it is also a collaboration tool. It enables people to share files via the use of centralized servers for which Git has the required communications protocols, and cryptographic tools for fast and safe collaboration. This allows for large projects involving many people to be organized, tasks to be coordinated, and the history of development to be tracked across large teams.

## How Git works

![Git simple diagram](/images/Git_Simple_Diagram.png)

Git helps to manage changes in a collection of files called a _**repository**_ which represents the sum of all files in a project which are being tracked and their associated history (i.e. previous versions). A "_local repository_" refers to that collection when the files are available in a person's computer, while a "_remote repository_" is housed in a server and helps to centralize the contribution of multiple people.

### Staging & Committing: The basic workflow

The most basic workflow of Git comprises a two step process, whereby changed files are first _**staged**_ and subsequently _**committed**_ to the local repository.

In the first step (_staging_), one of more files are placed in the staging area (also called _Git Index_). Single files or entire directories containing many files can be staged. The staging area can be seen as launching pad, an area where one of more files await before they are committed. Staging a file (or directory) is a way of a user signalling to Git which files he/she plans to add to the repository at the next commit.

The second step (to make a _"commit"_, or _"committing"_) is then to consolidate the changes made to the staged files into the local repository. Typically a file is committed only once some aspect of it, such as a small task, has been concluded. However small a task may be, it has to be concluded. This will help to create boundaries of execution, where at each commit we know which tasks have been implemented. In this fashion the repository can be temporally segmented into moments where different tasks were completed. Making a _"commit"_ is more than just updating the repository with new files, or new versions of older files. With each _"commit"_ a landmark is placed across the entire repository, which can be uniquely identified via an alphanumeric sequence with 40 characters known as an SHA-1 hash sequence.

### Branching & Merging

Branching refers to the ability of Git to split and manage parallel instances of the same project. Each instance is called a _**branch**_ and each carries with it not only the entire collection of files in the original branch, but also the history of that original branch up to the moment of creation of the new one. This allows for projects to bifurcate along multiple directions, and testing of different development paths can be undertaken without compromising the work developed on the so-called _"master"_ or _"main"_ branch.

Work developed along a side branch can evolve to the point where its contents can be  incorporated into the master branch through a processes known as _**merging**_. Once two branches merge, the contents of one branch are transferred to the other but both branches continue to exist. Merging alone does not extinguishes any of the branches involved in the "merger".

### Checkout: traveling along and between branches

The operation through which branches or commits are visited is called _**checkout**_. The exact point of the repository being visited is indicated by a Git element called "HEAD". The HEAD is said to be "_attached_" whenever it points to the latest _commit_ along a branch, otherwise, if the HEAD indicates an earlier commit, it is said to be "_detached_".

Using the _branch name_ different development paths of the repository can be checked out. Likewise, using the _commit identifier_ sequence, the project can be visited at an earlier time point. As a result of the checkout operation, the files in the associated working directory will change to reflect the specific _branch_ and _commit_ being checked out. The further back along the timeline you checkout a commit, the more embryonic the whole project will appear in the working directory. For this reason, it is popular to refer to a "time capsule" metaphor when discussing the "checkout" operation.

### Interacting with remote repositories

Oftentimes, we might begin working on a project for which some groundwork has already been done, and which we can access on a centralized server. To be able to work on that project, it is first required to _**clone**_ the remote repository in question, thereby creating a _local copy_ which becomes the _local repository_. Cloning ensures capture of the entire history of commits, and not just the files themselves.

Upon working on the files and committing changes to the local repository, we can then _**push**_ those changes from the local repository up to the remote repository. The administrator of the remote repository may or may not accept the changes being pushed.

Subsequent attempts to update our local repository can be made via a _**pull**_ or a _**fetch**_ mechanism. While doing a "_pull_" will update your local repository with all the new changes made centrally, a "_fetch_" will only download the changes allowing a case-by-case evaluation of which changes to commit to the local repository.

## How to get and run Git

![Git terminal](/images/terminal-git-prompt.png)

Git runs on Linux as a command-line application. So, if you do not have a Linux machine, you must run it in a Linux emulator. Git is available out of the box through the command line application Terminal in both Linux and Apple operating systems. For the Windows operating system, Git can be accessed installing _Git for Windows_ (downloadable [here](https://gitforwindows.org/)). For a quick and easy guide to install Git on your local machine check out [this handy guide](https://github.com/git-guides/install-git) produced by GitHub.

>Because Git runs on Linux, it is recommended that you get acquainted with basics of Linux shell scripting language known as _**BASH**_ (aka, Bourne Again SHell).
>
>Bash is the default shell command language currently used by most modern Linux distros. A shell is an interface layer that exposes the services of an operating system to the user, i.e. it is on the shell that we communicate to the computer which tasks we want it to perform. In modern operating systems, this interaction often occurs through a Graphical User Interface (GUI), with icons, windows and a surface point & select method (e.g. mouse). However, in the IT industry it is also common to use a Command Line Interface (CLI) which is essentially a text window where commands are typed and the operating system respond to those commands (no clicks allowed). Thus, Bash is simply a collection of specific commands with an inbuilt syntax which we can use to instruct a computer to run different tasks, such as renaming a file, moving it between directories, visualizing contents of a folder, etc. To know more about _bash_ scripting you can look up the [Bash reference manual](https://www.gnu.org/software/bash/manual/bash.html) or for a more soft approach you can check out [this "Geeks for geeks" page](https://www.geeksforgeeks.org/basic-linux-commands/).

## The anatomy of Git

_**The Git Directory.**_ Upon initializing Git on the folder which will contain the files relevant to our project, Git creates a **.git** folder, called **Git directory**. This .git folder is hidden by default, and will collect all metadata which enables Git to track the different stages of development of the repository. From the moment it is initialized, Git will investigate any file present within the set directory (including subfolders) and evaluate if those files are being tracked.

_**The Working Tree.**_ All files within the project folder that reside outside the Git directory are said to belong to the "**working tree**". These files include not only those which are part of the repository, but it includes also versions of those files which have changes that have not been committed, as well as files which are not being tracked. A working tree is said to be "cleaned", when it no longer has non-tracked files pending to be staged, nor staged files pending to be committed.

_**The Staging Area (or Git index).**_ To be committed to the repository, a file (or collection of files) must first be placed in what is known as the "**staging area**". This is a temporary area through which any file being placed on the repository needs to traverse. Different files can be placed in the staging area before being added to the repository. Once a file is committed, it is assigned to the repository and therefore exits the staging area.

**The HEAD**. HEAD is an element of Git operation that identifies or points to the a commit which was selected (or "checked-out"). A HEAD typically points to the most recent commit along a branch - in this case the head is said to be attached. However, HEAD may become detached if it points to an earlier commit along a branch.

**Branches.** Git allows work to be divided along paths called "**branches**". A project will start on a branch typically called "Master" or "Main". From the Master branch, new branches can be created, and from these more sub-branches can be formed too. When a branch is created, it inherits all contents present in the original branch up to the moment of branching. Yet, modifications made on the new branch (such as adding newly created files, or making modifications) will not be automatically passed back onto the original branch. For this to happen, a merge operation needs to be initiated manually. The file structure in the OS will always reflect the branch or commit which is set active.

_**The Repository.**_ The Git _**repository**_ is the collection of all the files that make up the most recent state of a project together with its different branches and their history in the different "commits" made.

## Git operations and commands

### Initializing Git

>**TLDR:** In your selected folder initialize Git with the **```git init```** command.
> Configure Git with your name: **```git config --global user.name "<your name>"```** and your e-mail address: **```git config --global user.mail "<your_e-mail_address>"```**

![Git init](/images/git_init.png "Using git init to start a repository")

Once you have navigated inside the folder which will contain all the files for your project, using the command **```git init```** will initialize Git and deploy to necessary tools to establish a Git repository and begin tracking its files along a "master" branch.

In the example above we created a folder called _"project_folder"_ and inside this folder Git was initialized resulting in a branch called "master" being created together with a **.git** directory. Because the Git directory is hidden, it can only be visualized using the bash **```ls -la```** command.

### Checking the status of the working tree

>**TLDR:** Use the **```git status```** command to evaluate the status of the working tree.

As an example, we create a python script file called **script.py** inside _"project_folder"_  directory.

Here we use _"nano"_ the Linux command line text-editor by entering in the shell prompt: **```nano script.py```** and insert the following lines of code:

```python
def main():
  pass
```

The script above simply contains an empty function called _main_ and that will do for now. After saving and returning to the shell prompt, we can then visualize the files in the directory and check what the status of the working tree using **```git status```**.

![Git status](/images/git_status.png "Using git status to check the working tree")

We can see that only **script.py** is present in the _"project_folder"_ directory, and the output of **```git status```** tells us three things:

1. The we are evaluating the status of the working tree in the MASTER branch.
2. That there are no commits at this moment,and
3. That it identifies **script.py** as an untracked file

### Staging a File

>**TLDR:** To stage a file use the **```git add <filename.ext>```** command.

![Git add](/images/git_add.png "Using git add to stage a file")

After staging the file, the last message of the output of **```git status```** changes and it now tells us that there is a new file ready to be committed.

>NOTE:
>
> If you have several files and you wish to add them all to the staging area in a single command, you can do it with **```git add *```**

### Committing changes to the repository

>**TLDR:** To update the repository with staged files, use **```git commit -m "<your message here>"```**

![Git commit](/images/git_commit.png "Using git commit to update the repository")

Staged files are finally committed to the repository using the **```git commit -m "<your message here>"```** where the **-m** flag is obligatory followed by a commenting message that reflects what the commit is about - i.e. which changes were made in the files relative the the previous versions.

In the example case after committing the **script.py** file, Git tells us a few things:

1. that has recorded a commit on the root of the master-branch with the ID number ea174cf (this code is actually only the first 7 characters of the 40 character-long hexadecimal SHA-1 commit identifier)
2. It indicates that this commit involved changing only one file, and resulted in the insertion of 16 lines of text (blank lines count too).
3. The line saying **create mode 100664** reflect the file permissions (read/write/execute) for the file owner (6, or read & write), group owner (6, or read & write) and other users (4, or read). For more details check out this material on "[understanding Linux file permissions](https://linuxize.com/post/understanding-linux-file-permissions/)".

After the commit is made, **```git status```** says that the work tree is clean, i.e. that there are no additional pending tasks involving any of the files associated with the tree - the tree is therefore, clean :).

> NOTE:
>
> If the file is already being tracked, Git will be aware that a modification has been made even if you do not stage the file.

### Checking the history of commits

>**TLDR:** To visualize the history of commits to the repository we use **```git log```** and if you want to check the patch of code that changed, you add the **-p** flag .

![Git log](/images/git_log.png "Using git-log to visualize history of commits")

The output og **```git log```** provides us with information regarding the commits, namely:

1. The full commit SHA-1 ID number (notice how the first 7 digits are the same as those returned by **```git commit```**)
2. It indicates that the HEAD is on the MASTER branch
3. It shows the author and date of the commit, along with its accompanying message.

By passing the **```-p```** parameter to **```git log```** we get more details about the _patch_ of code added to out repository. To the information above, it also adds the **diff file** which includes among other details, the exact lines of code which differed in the repository at the instance of that commit.

But we can continue on modifying **script.py**, by simply replacing "pass" with a print statement so that the script reads:

```python
def main():
  print("Hello, world")
```

![modification of script.py](/images/git_commit2.png)

As a result of this latest commit, the repository changes as evidenced by the output of the **```git log```** command.

![git log 2](/images/git_log2.png)

We now see that the repository contains two different commits, the latest of which appears on the top with a different commit identifier string.

The output of **```git log```** also indicates that in the latest commit we had one line deleted (-)which was replaced by an insertion (+) and clearly specifies the content of those lines.

### Creating, deleting and moving between branches

>**TLDR:** The **```git branch```** command alone simply lists all available branches.  To create a branch you need to specify the name of the branch as in **```git branch <new-branch-name>```**. You can then use  **```git checkout <new-branch-name>```** to hop on to the new branch and continue working there. If you want to delete a branch, you need to first checkout some other branch and then delete it by passing the command **```git branch -d <branch-to-delete>```**. For Git to inform you on which branch you are on, run  **```git branch --current-branch```**.

![Git_branch](/images/git_branch.png)

Creating branches is useful to test ideas, and unlike file directories where you can find subdirectories, in Git branches there are no subbranches. All branches are hierarchically similar.  In the example above, we started only with a single branch: the MASTER branch. We then created a new branch which we called "_dev_feature1_" followed by listing all available branches again where we noticed two things:

1. the "_dev-feature1_" branch was created, and
2. we remain in the MASTER branch, as indicated by the asterisk marking.

To move to the new branch we used the **```git checkout```** command, followed by the name of the new branch ("_dev_feature1_"), resulting in the branch "_dev-feature1_" being highlighted after running **```git branch```**

However, if we wish to delete a branch we cannot be on the branch we want to delete. Instead we need to checkout another branch and from there delete the branch by passing the command: **```git branch -d <branch-to-delete>```**.
> NOTE:
>
> An alternative way to create a new branch and immediately switching to the newly created branch is to run **```git checkout -b <new-branch-name>```**.
>
>To check in which branch you are working on, run  **```git branch --current-branch```**.

### Working on new branches

> **TLDR:** Once you checkout a branch, you can create new files in that branch. However, for them to be associated with that branch those files need to be committed. Files committed in one branch, will not be displayed on another. Untracked files appear in all branches.

We can use new branches to develop new content, such as creating new files. Here we are going to create a new branch called **"new-feature"** and in this branch we will create a new file called **"script2.py"** containing only an empty function called _new_function( )_. Something like this:

```python
def new_function():
  pass
```

![Git_script_on_new_branch](/images/git_script2_new_branch.png "Creating a new file in a side branch")

In our example above we created a new branch called "new-feature", checked-out the new branch and on it we created the _script2.py_ file. After committing the new file to the repository, we confirmed that it was present in the "new-feature" branch while absent from the "master" branch.

> Creating or modifying files on a given branch will only change the repository on that branch. The OS file structure will always reflect the branch which we set to be active.

At this point we can look at how the history of our repository has changed.

![Git log branches](/images/git_branch_log.png)

We begin at the _master_ branch and see the only two commits we have made to "script.py". However, when we change to _new-features_ branch, we see that those commits are mentioned also together with the latest third commit associated with the creation of the _scrip2.py_ file.

We now have two branches:

* the "master" branch, with 2 commits, and
* the "new-branch" branch with 3 commits.

We can take the opportunity to travel to earlier commits and check how this affects how the operating system sees the files. Our last stop was the "new-branch" branch, so we can go to the very first commit in the log of that branch which occurred before the creation of the branch to place.

![Git commit checkout](/images/git_commit_checkout.png)

As we checkout a commit Git warns us that we have a **"detached HEAD"**. This happens every time we checkout a commit instead of a branch, and it is a way of Git alerting that we are not working in the most updated version of a branch, but instead with the HEAD buried under one of the commits.

Because the commit we checked out was one very first commit we made, the _script2.py_ file disappeared and _script.py_ is available. By visualizing the contents of _script.py_ using the command **```cat script.py```** we see that indeed we no longer see the "print" statement we introduced to replace the "pass" statement. We have indeed reached an earlier version of the project.

### Merging branches - Updating with new files

>**TLDR:** To merge branches, we can follow a safe two step process:
>
>1. use **```git checkout <main-branch-name>```** to have HEAD pointing to the branch receiving the update.
>2. use **```git merge <side-branch-name>```** to bring the contents from a "_side branch_" into a "_main branch_".

Work on parallel branches can develop to the point where they should be merged back into the "master" branch.

![Git_merge](/images/git_merge.png "merging branches")

In our example, we leave the checked out commit and checkout back into the master branch and from there we gave the **```git merge```** command for the "master" branch to merge with the "new-branch" branch. This resulted in the update of the repository with a single file and 3 new lines of code which were inserted.

Within the "master" branch, listing the files in the _project_folder_ now reveals the presence of both _script.py_ and _script2.py_ files.

Importantly, merging does not involve merging the branches themselves, only their contents. Consequently, after a branch merger, the branches continue to exist but the history of the branch receiving the update is populated with the history of the updating branch.

>NOTE:
>
>A merger is signalled in the output of **```git log```** by the fact that two branches share the same commit.

### Merging branches - updating with existing files

When merging two branches which share the same files there is a chance of conflict. However, as long as the new version of the file is a direct successor of the old file, the old file simply gets updated.

Here we simulate this by changing in the "new-branch" branch and change the _new_function( )_ in the _script2.py_ so that now instead of a "pass" statement it features a print statement, like so:

```python
def new_function():
  print("Goodbye, Luna")
```

![Git_merge2](/images/git_merge2.png "Merge two branches sharing one changed file")

From the _master_ branch we switched to the _new-feature_ branch. There, we edited the _script2.py_ using the  _nano_ text editor, and committed the changes to the repository. We then checked out the _master_ branch once again, and confirmed that in that branch, the contents of the _script2.py_ file contained only the "pass" statement, indicative that that version of the file is the older one. We then proceeded with the merge with the _new-feature_ branch, and the changes implemented in that branch served to update the _master_ branch.

With the **```git merge```** command, git returned that it is updating the latest commit in the _master_ branch (a462ad0...cd81279) Git indicates that the merger resulted in the change of 2 lines in "_script2.py_" file, and a total of 1 file, 1 insertion and 1 deletion.

![Git log after merge - 2](/images/git_log_after_merge2.png)

Inspecting the Git log allows us to see that the latest commit was the result of a merger event, and the diff file highlights the differences between the two versions of the file.

### Merge Conflicts

Conflicts arise when, for example, two files who were changed in their independent branches are brought together within the same branch.

To simulate this problem, we will create two files with the same name ("_system_check.py_"), one in the MASTER branch, and another in the "_dev-feature1_" branch. The two files will differ in two lines.

![Git_conflict1](/images/git_conflict1.png "Conflict warning")

We are warned by Git which tell us that:

1. That there was a CONFLICT while merging "_system_check.py_" and so the merger failed.
2. It also tells us to fix the conflicts and only after that try to commit.

![Git_conflict2](/images/git_conflict2.png "Git status after conflict")

We can look at the current situation using **```git status```** which is a bit more verbose, but essentially highlights the same problem and tell us a few more things:

1. That after resolving the conflict, we need to stage the conflicting file using **```git add <conflicting_filename.ext>```**, and
2. That the merger can be cancelled by running **```git merge --abort```**:

To fix this conflict we need to open "_system_check.py_" using a code/text editor such as _Nano_ or _Vim_ - here I use Nano typing **```nano conflict_file.py```** in the shell prompt.

![Git_conflict3](/images/git_conflict3.png "text editor highlighting code differences between the two branches")

We see that when attempting to merge, noticing the conflict, Git edited the "_system_check.py_" file, and placed the code contained in both versions in the same file. It shows two sections were conflicts were found. These conflicts need to be resolved, that is, we must delete the parts that are not relevant (separators: "<<<<< HEAD", "======", ">>>>> dev-features1") and are incorrect (wrong code).

![Git_conflict4](/images/git_conflict4.png "Resolving a merger conflict")

After editing the script in Nano, we staged the file and verified that the situation of the conflicting file changed. Entering **```git status```** we are told that the all conflicts are fixed, but merger has not been completed. Using **```git merge```** is irrelevant as is only returns a fatal error given that a merge is ongoing. To advance further, we commit the changes to the conflicting file, and in that moment the merger is resolved. We confirm this by entering again the merge command which returns that everything is up to date.

### Renaming tracked files using Git

Sometimes you might want to rename a file that is being tracked. This can cause problems and it needs to be addressed clearly. 

There are two ways to handle renaming of files in git:

- Using the **git mv** command, which takes the old file name and the new file name as arguments. This command will automatically stage the rename for commit and preserve the file history¹³⁴. For example:

```bash
git mv old_file.txt new_file.txt
git commit -m "Rename old_file.txt to new_file.txt"
```

- Using the normal **rename** command of your operating system, and then using **git add** and **git rm** to stage the changes. This method requires you to manually tell git that you have renamed a file, but it will also detect the rename and preserve the file history²⁵. For example:

```bash
rename old_file.txt new_file.txt
git rm old_file.txt
git add new_file.txt
git commit -m "Rename old_file.txt to new_file.txt"
```

