# Testing/learning jujutsu

## Basic commands

Creating a new repository:

```sh
$ jj git init .
Initialized repo in "."

$ jj log
@  unsmxwsn pm@mkz.me 2024-08-21 20:19:59 8f89d5bb
│  (no description set)
◆  zzzzzzzz root() 00000000
```

Note: Modifying the file will "prepare" a new git commit, changing the git commit id but not the working copy id:

```sh
$ jj log
@  unsmxwsn pm@mkz.me 2024-08-21 20:23:45 d91b14ec
│  (no description set)
◆  zzzzzzzz root() 00000000
```

Setting a description to current working copy:

```sh
$ jj describe -m "creating a basic README"
Working copy now at: unsmxwsn 552a06d1 creating a basic README
Parent commit      : zzzzzzzz 00000000 (empty) (no description set)
```

Sharing the working copy on github:

```sh
$ jj git remote add origin git@github.com:mycroft/test-jj.git
$ jj branch set trunk --allow-backwards
Created 1 branches pointing to unsmxwsn 75d5fa62 trunk | creating a basic README
Hint: Consider using `jj branch move` if your intention was to move existing branches.
$ jj git push
Branch changes to push to origin:
  Add branch trunk to 75d5fa62e3cf
Warning: The working-copy commit in workspace 'default' became immutable, so a new commit has been created on top of it.
Working copy now at: vnwzwwsn f2a1594d (empty) (no description set)
Parent commit      : unsmxwsn 75d5fa62 trunk | creating a basic README
```

As work was shared/pushed to github, a new working copy is created.


## Squash workflow

The workflow works like this:

* set a description about what's to be done
  - `jj describe -m "README: describing squash workflow"`
* create a new working copy
  - `jj new`
  - At this moment, the parent commit will be empty (ie: no diff)
* once work is complete, squash the working commit into the parent commit.
  - `jj squash`

As squash will merge current changes into the parent commit, it is possible to do that multiple time! The parent commit will not change (unlike the git's commit id obviously). `jj squash` works as `git commit --amend`.

