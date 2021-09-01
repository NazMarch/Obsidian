#GitBash 

```ad-warning
title: Preconditions
collapse: open
It can happen if you force checkout to other branch
If you drop your stash
If you just detect missing of your stashes someday

BEFORE: 
- Don't delete your local branches
- Don't delete your repository folder
- Don't clear .git folder of your local repository 
  and anything else there
- Clear or save all changes before restoring
```

```ad-info
title: 1. Go to git bash
collapse: open
```bash
# run  
git stash list
# if list is empty or have missing stashes run below cmd

# showing the list of all stashes, commits
# run the long command
git fsck --unreachable | grep commit | cut -d ' ' -f3 | xargs 
git log --merges --no-walk
```

Then search your stash and copy hash of `commit`

```ad-info
title: Go to git bash
collapse: open
```bash
# applying stash
# warn: no changes before run command
# warn: look at the branch where commmit was created
# it be better to stay at the same branch
git stash apply 42946e5130c11592beda8d20f93d60e23323b65a
```

Can check here more info, if you could not resolve the problems
https://dev.to/meduzen/recover-a-lost-git-stash-in-two-steps-569

```
git update-ref refs/stash 4b3fc45c94caadcc87d783064624585c194f4be8 -m "My recovered stash"

git update-ref refs/stash 4b3fc45c94caadcc87d783064624585c194f4be8 --create-reflog -m "My recovered stash"

```

https://gist.github.com/joseluisq/7f0f1402f05c45bac10814a9e38f81bf

```
git log --graph --oneline --decorate $( git fsck --no-reflog | awk '/dangling commit/ {print $3}' )

git stash apply YOUR_WIP_COMMIT_HASH_HERE
```

```ad-warning
title: Clean up stashes
collapse: open
```bash
rm .git/refs/stash .git/logs/refs/stash
```
