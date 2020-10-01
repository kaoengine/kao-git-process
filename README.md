# kao-git-process

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

1. Squash/reword/edit any commits if need be
    > git rebase -i develop
2. Rebase your feature branch on top of current develop
    > git rebase develop
3. Change to develop
    > git checkout develop
4. Fast-forward merge your feature branch into develop
    > git merge myfeature
5. Delete your local feature branch (see above tip for remote deletion)
    > git branch -d myfeature

## Ignore changes in a tracked file ¶
1. To ignore:
    > git update-index --assume-unchanged <tracked-file>
2. To stop ignoring:
    > git update-index --no-assume-unchanged <ignored-tracked-file>