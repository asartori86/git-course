# Version control with git

A version control system is a tool that keeps track of `changes` for
us and help us version and `merge` our files. Changes are stored in a
`commit`. The complete history of commits for a particular projects
and their metadata make up a `repository`. Repositories can be kept in
sync across different computers.

Git is a `distributed` version control system, meaning that they do
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

	git config --global user.name "Alberto Sartori"
	git config --global user.email "alberto.sartori86@gmail.com"
	git config --global core.editor "emacs -nw -Q"
	git config --global core.editor "vim"
	
	git config --list

	cat ~/.gitconfig

### RTFM

	man git
	git config -h
	git config --help
	man git-config


## First steps with git

	mkdir planets
	cd planets
	git init
	ls -a
```
git status
```
```
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)
```
