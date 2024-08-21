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
