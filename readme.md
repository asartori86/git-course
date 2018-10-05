

# Version control with git

[Why git?](http://phdcomics.com/comics/archive.php?comicid=1531)

A version control system is a tool that keeps track of `changes` for
us and help us version and `merge` our files. Changes are stored in
`commit`s. The complete history of `commit`s for a particular project
and their metadata make up a **repository**. Repositories can be kept in
sync across different computers.

Git is a **distributed** version control system, meaning that they do
not need a centralized server to host the repository.

### Take home messages

- Nothing that is committed to version control is ever lost, unless
  you work really, really hard at it. Since all old versions of files
  are saved, it’s always possible to go back in time to see exactly
  who wrote what on a particular day, or what version of a program was
  used to generate a particular set of results.

- As we have this record of who made what changes when, we know who to
  ask if we have questions later on, and, if needed, revert to a
  previous version, much like the “undo” feature in an editor.

- When several people collaborate in the same project, it’s possible
  to accidentally overlook or overwrite someone’s changes. The version
  control system automatically notifies users whenever there’s a
  conflict between one person’s work and another’s.


## Setting up git

```bash
$ git config --global user.name "Alberto Sartori"
$ git config --global user.email "alberto.sartori86@gmail.com"
$ git config --global core.editor "emacs -nw -Q"
$ git config --global core.editor "vim"

$ git config --list

$ cat ~/.gitconfig
```

### RTFM

```bash
$ man git
$ git config -h
$ git config --help
$ man git-config
```

Or take a look at [software carpentry lecture](http://swcarpentry.github.io/git-novice/) and [pro git book](https://git-scm.com/book/en/v2) 

## First steps with git

```bash
$ mkdir planets
$ cd planets
$ git init
$ ls -a
```
```bash
$ git status
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)
```
Let's create a new a file and see what happens

```bash
$ echo 'Cold and dry' > mars.txt
```
```bash
$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	mars.txt

nothing added to commit but untracked files present (use "git add" to track)
```
```bash
$ git add mars.txt 
$ git status

On branch master

Initial commit

Changes to be committed:

  (use "git rm --cached <file>..." to unstage)

new file:   mars.txt

```

```bash
$ git commit

...

[master (root-commit) 2d88073] added mars.txt file

 1 file changed, 2 insertions(+)

 create mode 100644 mars.txt

```

```bash

$ echo 'another line' >> mars.txt
$ git status
$ git diff
$ git add mars.txt
$ git commit -m "another line"
$ git status
$ git log

```

## Branching

Create a new branch

```bash
$ git branch branch_name
```

Move the `HEAD` on branch `branch_name`

```bash
$ git checkout branch_name
```

The two above steps can be done

```bash
$ git checkout -b branch_name
```

Do the usual steps in this branch. Once satisfied, let's `merge` this branch into the `master` branch:

First of all, move the `HEAD` on the `master` branch

```bash
$ git checkout master
```

Now `merge` the other one

```bash
$ git merge branch_name
```

## Remotes

You can always add one or more remotes to your **local** repository

```bash
$ git remote add custom_label remote_git_repository_address
```

To retrieve, `fetch` updates from a `remote` named `custom_label`

```bash
$ git fetch custom_label
```

The above command downloads **in your `.git` folder** new commits and new branches

To apply these changes, you should `merge` the **remote** branch you want. For example, if I want to apply to my local `master` branch the changes made on the remote `master` branch, I have to do

```bash
$ git checkout master
$ git merge custom_label/master
```

When you `clone` a remote git repository, the remote as **by default** the label `origin`

If you have write access to a remote repository `custom_label`, you can `push` your branch `branch_name` as follows

```bash
$ git push custom_label branch_name
```







