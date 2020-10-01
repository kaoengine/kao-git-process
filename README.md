<div align="center">
<img style="width: 100px;height: 100px;margin: auto;" src="https://avatars2.githubusercontent.com/u/62488287?s=200&amp;v=4">

# 🐱‍💻Git-Tips
## 🚧🚧🚧 UNDER CONSTRUCTION 🚧🚧🚧


</div>

## Tips

- Merge a feature branch
- Ignore changes in a tracked file
- Undo the last commit
- Delete the last commit
- Stash untracked files
- Merge a remote branch
- Delete a remote branch
- Apply a commit to multiple branches with cherry-pick
- Commit Messages
- This page is a collection of useful git tips.

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