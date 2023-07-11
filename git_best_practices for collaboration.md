# Best practices for collaboration

![Collab Image](https://pulaskicounty.net/wp-content/uploads/2017/06/ThinkstockPhotos-508408868.jpg)

## Rule #1

### _Always synchronize your branches before starting any work on your own_

Starting with the most up-to-date material helps to minimize conflicts once your work gets merged with that of other people.

Over the period of development, frequently _pull_ and _push_ code from remote branches, so that differences between branches are minimized to manageable sizes.

## Rule #2

### _Avoid having very large changes that modify a lot of different things_

For example, if you want to change the name of a variable and you want to add a new function, don't do it under the same commit but instead split the changes into small chunks that can be easily described in a single commit line.

## Rule #3

### _When working on a big change, it makes sense to have a separate "feature" branch_

This allows development of new feature that may require a long cycle, while keeping the "master/main" branch to be able to work on smaller maintenance tasks (like debugging, etc).

## Rule #4

### _Regularly merge changes made on the master branch back into the "feature" branch_

Once the work in the feature branch is completed, it will be merged with the master branch, however the "master/main" branch will be updated in the course of the development of the new feature. To avoid possible errors once the feature is ready to be deployed, it is important to keep developing the "feature" in the context of a developing "master/main" branch.

## Rule #5

### _Have the latest version of the project in the master branch, and the stable version of the project in a separate branch_

If you need to maintain more than one version of a project at the same time, it's common practice to have the latest version of the project in the master branch and a stable version of the project on a separate branch.

You'll merge your changes into the separate branch whenever you declare a stable release.

When using these two branches, some bug fixes for the stable version may be done directly on the stable branch if they aren't relevant to the latest version anymore.

## Rule #6

### _Don't rebase changes that have been pushed to remote repos_

Rebasing can help a lot with identifying bugs, but use it with caution. Whenever we do a rebase, we're rewriting the history of our branch. The old commits get replaced with new commits, so they'll be based on different snapshots than the ones we had before and they'll have completely different hash sums. **Rebasing  works fine for local changes, but can cause a lot of trouble for changes that have been published and downloaded by other collaborators.**

The Git server will automatically reject pushes that attempt to rewrite the history of the branch. It's possible to force Git to accept the change, but it's not a great idea unless you really know what the implications will be.

As a possible workflow, consider instead:

1. Make your development in the "feature" branch.
2. When ready rebase the master branch.
3. Delete the old "feature" branch.

## Rule #7

### _Always strive to write good, short and clear "commit" messages_

It's already important when you're working alone since good commit messages help the future you understand what's going on, but it's even more important when you're collaborating with others since it gives your collaborators more context on why you made the change and can help them understand how to solve conflicts when necessary. So commit to being a good collaborator and remember to add those commit messages.

