## Git Scenarios - How Do I Fix That?

*Rob Richardson*

```
git init

echo "file1" > file1.txt
git add file1.txt
git commit -m "initial commit"

echo "file2" > file2.txt
git add file2.txt
git commit -m "add file 2"
```

`git log --oneline`

`git log --oneline --graph --decorate --all`

`--all` adds previous history on branches that are irrelevant

*Branches are maliable, commit hashes are whats important*

`HEAD` is the current latest working directory

Prints out commits with short SHA1 Ids. 

#### Time moves up in Git

```
echo "file3" > file3.txt
git add file3.txt
git commit -m "add file 3"
```

#### Checkout branch from a commit

```
git checkout -b asdf3asdf // Enter detatched head state. HEAD doesn't point to branch
git checkout -b mynewbranch // Point HEAD to a branch
```

`git reset --hard` Go back to the previous actual commit

`git update-ref refs/heads/mybranch HEAD` Put my HEAD onto that branch directly. Does not change git's history at all. Just where things currently point

`git reflog` Shows everywhere that HEAD has been. You can use this to find states that weren't attatched to a branch. Good for finding previous detatched HEADs

`git cherry-pick dfa4sdfasd` -> merge conflicts -> `git mergetool` -> resolve conflicts -> `git commit`

Specify a merge tool in your git config

`git rebase branchname` place all changes on top of that branch

#### Do not rewrite history that anyone else is touching

`git rebase -i asdfsd42` Interactively rearrange commits.

`pick` sets order
`squash` Mix a bunch of commits in order

When you rebase make a seperate branch before the interactive rebase so that you can always go back to it.

`git bisect` Keep splitting halfway point between commits to find where something went wrong.