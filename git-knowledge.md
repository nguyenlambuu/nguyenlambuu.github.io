
# GIT Knowledge

##### By Phuong Binh Nguyen

List out all branches (includes remote): `git branch -a`

List out all branches (only local): `git branch -l`

List out all branches (only remote): `git branch -r`

List branch by latest push: `git for-each-ref --sort=committerdate refs/heads/ --format='%(HEAD) %(color:yellow)%(refname:short)%(color:reset) - %(color:red)%(objectname:short)%(color:reset) - %(contents:subject) - %(authorname) (%(color:green)%(committerdate:relative)%(color:reset))'`

view history of a person: `git --no-pager log --decorate=short --pretty=oneline --reverse --author=phuongbn --after="2019-03-10" --before="2019-03-14"`

Git view work of someone: `git rev-list --remotes --author="phuongbn" --date=iso --pretty --branches="*" --no-merges --after="2019-03-10" --before="2019-03-14"`

View history on a branch: `git --no-pager log --decorate=short --pretty=oneline --reverse branch-name` | [Link](https://www.atlassian.com/git/tutorials/git-log)

View history by GUI: `git log --graph --oneline --all --decorate`

To view diff in git log: `git log -p file-name`

View change in short: `git log --stat`

View details for one commit:`git show ee19baca53b7`

Git grep by message: `git log -i --grep="deployment"`

Blame for a person who change the code: `git blame ee19baca53b7 file-name`

Get all logs around a file: `git log -p -- deployment/cv_cfg.sh`

Create diff between two commits: `git diff ee19baca53b7  wrqqbaca53b7 > my.patch`

Diff between a commit to its parent: `git log -u -1 ee19baca53b7`

View all files in a commit: `git ls-tree --name-only -r ee19baca53b7`

Show all changes around a file: `git log --follow -- file-name`

View file content after a commit: `git show revision:path/to/file`

Revert the modify that was not commited: `git checkout -- file-name` | [Link](http://christoph.ruegg.name/blog/git-howto-revert-a-commit-already-pushed-to-a-remote-reposit.html)

Revert the commit that was not push:
```
git commit -m "Something terribly misguided"
git reset HEAD~
git add -a
git commit -c branch-name
```

Delete a second commit and keep all others (after push):
```
git rebase -i ee19baca53b7
git push branch-name -f
```

Revert commit that already push:
```
git reset HEAD^ --hard
git push origin +your-branch
```

Git merge: `git merge --no-commit --no-ff the/other/branch`

Git resolve conflict: `git merge tool`

Git delete branch local/remote: `git branch -D branch-name`

Git create a branch from current one: `git checkout -b branch-name`

View diff on two different branch: `git diff q...the/other/branch -- path/to/conflicting/file`

View log on two different branch: `git log -p the/other/branch..HEAD -- path/to/conflicting/file`

Git patch ignore errors: `git apply --reject --whitespace=fix mychanges.patch`

Git reset origin to revision:
```
git reset --hard cedc856
git push --force origin master
```

Git remember account: `git config credential.helper store`

Git remove remembered account: `git config --unset credential.helper`

Git show all settings: `git config --list`

Git show info on the repo: `git remote show origin`

Git update the local to same as remote:
```
git fetch origin**
git reset --hard origin/master
```

Git staged &  being asked: `git add --patch file-name`

Git unstage: `git reset -- file-name`

To view the git history: `git reflog` | [Link](https://www.atlassian.com/git/tutorials/rewriting-history)

Modify message of the last commit: `git commit --amend -m "an updated commit message"`

Add forgotten files to previous commit: `git commit -a --amend --no-edit`

Apply one commit from one branch to another: `git cherry-pick -x commit-hash` | [Link](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)

Delete local branches that does not exists on remote: `git fetch --prune`

Git tag add/delete:
```
git tag
git tag -d tag_name
```
