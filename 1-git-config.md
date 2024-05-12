# open ~/.gitconfig
```ts
code ~/.gitconfig
```

# Creating Git Aliases
```ts
[alias]
    s = status -s
    cnv = commit --no-verify
    cane = commit --amend --no-edit
    aa = add .
    p = push
    pf = push --force
    la = log --oneline --decorate --graph --all
    l = log --oneline --decorate --graph
    rl= ref log
    la = "!git config -l | grep alias | cut -c 7-"
```

```ts
[alias]
    # one-line log
    l = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=short

    a = add
    ap = add -p
    c = commit --verbose
    ca = commit -a --verbose
    cm = commit -m
    cam = commit -a -m
    m = commit --amend --verbose
    
    d = diff
    ds = diff --stat
    dc = diff --cached

    s = status -s
    co = checkout
    cob = checkout -b
    # list branches sorted by last modified
    b = "!git for-each-ref --sort='-authordate' --format='%(authordate)%09%(objectname:short)%09%(refname)' refs/heads | sed -e 's-refs/heads/--'"

    # list aliases
    la = "!git config -l | grep alias | cut -c 7-"
```


```ts
# Diff line-wise
d = diff

# Diff staged line-wise
ds = diff --staged

# Diff word-wise
dw = diff --color-words

# Diff staged word-wise
dws = diff --color-words --staged

# Diff character-wise
dt = diff --word-diff-regex=.

# Diff staged character-wise
dts = diff --word-diff-regex=. --staged
```
