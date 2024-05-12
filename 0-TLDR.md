# define and use aliases
```sh
$ git config --global alias.p 'push'
$ git p
```

# To see all your aliases
```sh
$ git config --global -l
user.name=ricardo
user.email=ricardo@example.com
alias.p=push
```

# useful Git aliases :
# 1. Git status
```sh
$ git config --global alias.st 'status -sb'
```
example 
```sh
$  git st
## master
```

# 2. Git log --oneline
```sh
$ git config --global alias.ll 'log --oneline'
```
example 
```sh
$ git ll
33559c5 (HEAD -> master) Another commit
17646c1 test1
```
# 3. Git last commit
```sh
$ git config --global alias.last 'log -1 HEAD --stat'
```
example 
```sh
$ git last
commit f3dddcbaabb928f84f45131ea5be88dcf0692783 (HEAD -> branch1)
Author: ricardo <ricardo@example.com>
Date:   Tue Nov 3 00:19:52 2020 +0000

    Commit to branch1

 test2 | 1 +
 test3 | 0
 2 files changed, 1 insertion(+)
```

# 4. Git commit
```ts
$ git config --global alias.cm 'commit -m'
```
example

```ts
$ git cm "A nice commit message"
[branch1 0baa729] A nice commit message
 1 file changed, 2 insertions(+)
```

# 5. Git remote
```ts
$ git config --global alias.rv 'remote -v'
```

# 6. Git diff
```ts
$ git config --global alias.dv 'difftool -t vimdiff -y'
```
example
```ts
$ git dv 33559c5 ca1494d file1
````
# 7. Git config list

```ts
$ git config --global alias.gl 'config --global -l'
```
example 

```ts
$ git gl
user.name=ricardo
user.email=ricardo@example.com
alias.p=push
alias.st=status -sb
alias.ll=log --oneline
alias.last=log -1 HEAD --stat
alias.cm=commit -m
alias.rv=remote -v
alias.d=diff
alias.dv=difftool -t vimdiff -y
alias.gl=config --global -l
alias.se=!git rev-list --all | xargs git grep -F
```

# 8. Git search commit
```ts
$ git config --global alias.se '!git rev-list --all | xargs git grep -F'
```
example 
```ts
$ git se test2
0baa729c1d683201d0500b0e2f9c408df8f9a366:file1:test2
ca1494dd06633f08519ec43b57e25c30b1c78b32:file1:test2
```

# to try

```ts
# branch delete: This checks out your local master branch and deletes all local branches
#                that have already been merged to master
brd = !sh -c \"git checkout master && git branch --merged | grep -v '\\*' | xargs -n 1 git branch -d\"

# branch delete here: Deletes all local branches that have already been merged to the branch
#                     that you're currently on
brdhere = !sh -c \"git branch --merged | grep -v '\\*' | xargs -n 1 git branch -d\"

# diff status: A git diff, but with only the filenames (which reminds me of git status)
diffst = diff --name-only

# forced pull: You have a local branch (e.g. for reviewing), but someone else did a forced push
#              update on the remote branch. A regular git pull will fail, but this will just set
#              the local branch to match the remote branch. BEWARE: this will overwrite any local
#              commits you have made on this branch that haven't been pushed.
pullf = !sh -c \"git reset --hard origin/$(git rev-parse --abbrev-ref HEAD)\"

# quick amend: Amend my staged changes to the last commit, keeping the same commit message
amend = commit --amend -C HEAD

# history: This is pretty much the only way I look at my log. Aside from providing one-line logs,
#          it also shows the branching in/out
hist = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
```


# Some submodule related aliases

```ts
git config --global alias.sup 'submodule update --init --recursive'
git config --global alias.coz '!f(){ git checkout "$@" && git submodule update --init --recursive; }; f'
git config --global alias.colz '!git checkout @{-1} && git submodule update --init --recursive'
git config --global alias.comz '!git checkout master && git submodule update --init --recursive'
git config --global alias.plz '!git pull && git submodule update --init --recursive'
git config --global alias.clz 'clone --recursive'
```
