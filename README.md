<div align="center">
<img style="width: 100px;height: 100px;margin: auto;" src="https://avatars2.githubusercontent.com/u/62488287?s=200&amp;v=4">

# 🐱‍💻Git-Tips
## 🚧🚧🚧 UNDER CONSTRUCTION 🚧🚧🚧


</div>

## Tips

- [Merge a feature branch](#merge-a-feature-branch)
- [Ignore changes in a tracked file](#Ignore-changes-in-a-tracked-file)
- [Undo the last commit](#Undo-the-last-commit)
- [Delete the last commit](#Delete-the-last-commit)
- [Stash untracked files](#Stash-untracked-files)
- [Merge a remote branch](#Merge-a-remote-branch)
- [Delete a remote branch](#Delete-a-remote-branch)
- [Apply a commit to multiple branches with cherry-pick](#Apply-a-commit-to-multiple-branches-with-cherry-pick)
- [Commit Messages](#Commit-Messages)
- [This page is a collection of useful git tips.](#This-page-is-a-collection-of-useful-git-tips.)

## Merge a feature branch
In this example we assume that your feature branch, myfeature, is based off develop and that you are currently in your feature branch.

*1. Squash/reword/edit any commits if need be*

    git rebase -i develop
*2. Rebase your feature branch on top of current develop*

    git rebase develop
*3. Change to develop*

    git checkout develop
*4. Fast-forward merge your feature branch into develop*

    git merge myfeature
*5. Delete your local feature branch (see above tip for remote deletion)*

    git branch -d myfeature

## Ignore changes in a tracked file 
*1. To ignore:*

    git update-index --assume-unchanged <tracked-file>

*2. To stop ignoring:*

    git update-index --no-assume-unchanged <ignored-tracked-file>

## Undo the last commit
*Changes are put back into staged*

    git reset --soft HEAD~1

## Delete the last commit
*All changes are lost!*

    git reset --hard HEAD~1

## Stash un-tracked files
At times you will be working on a branch with un-tracked files (new files) and you'll need to checkout master to apply a bug fix.

First, add the un-tracked files to the index:

    git add <un-tracked-files>

Now do a regular stash:

    git stash

At this point you can checkout whatever branch you want and do what you need to do. When you're done, checkout your original working branch again and pop the changes from your stash:

    git stash pop

You can remove the files you indexed from the index if you want, as to not pollute your next commit:

    git rm --cached <files>


## Merge a remote branc
First, add the repo:

    git remote add <reponame> <location>

Now fetch in the changes:

    git fetch <reponame>

You'll want to do a diff against your branch to see what will be merged:

    git diff master <reponame>/<branch>

If you're happy with the changes, go ahead and merge it:

    git merge <reponame>/<branch>

## Delete a remote branch

    git push <repo> :<branch>

or

    git push --delete <repo> <branch>

## Apply a commit to multiple branches with cherry-pick
This technique uses cherry-pick to apply commits to branches that differ too much to use merge.

Checkout master branch

    git checkout master

Make commit

    git commit -m "Fixed the bug that caused issue xyz"

Checkout stable branch

    git checkout stable

Apply the last commit from master to this branch

    git cherry-pick master

## Commit Messages
Based on ​git commit guidelines and ​[How to Write a Git Commit Message](./how-to-write-commit.md).

The short answer on the golden rule for git commit subject lines is to you ask yourself:

**If applied, this commit will.**.. `<your commit subject line here>`

e.g. If applied, this commit will `Enable editing of torrent names in Add Dialog`

A general guideline on writing a good commit message is to provide information that is not already provided from the commit diff, which in essence is "the why, not the how".

* Explain why the change is necessary
    *  After reading the commit message it should should be apparent why the changes were made.
* Explain how the issue is addressed in broad terms
    *  It is not necessary to explain how the changes are made in detail as that can be seen from the commit diff.
Example commit message:
```
    Short summary of changes (preferably 50 characters or less)

    More detailed explanatory text, if necessary.  Wrap it to about 72
    characters or so. The first line can be considered as the subject of an
    email and the rest of the text as the body. The blank line separating
    the summary from the body is critical, unless you omit the body entirely.

    Further paragraphs come after blank lines.

    - Bullet points are okay, too

    - Typically a hyphen or asterisk is used for the bullet, preceded by a
        single space, with blank lines in between, but conventions vary here
```