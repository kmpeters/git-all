# git all

Execute a git command on multiple repositories

## Installation

Add ``git-all`` to your ``PATH``

## Usage

When ``git-all`` is on your ``PATH``, it can be called without the hyphen:

```
$ git all -h
usage: git-all [-h] [-d DEPTH] [-s] [-l] [-x] ...

positional arguments:
  args        git command to execute in each repo

optional arguments:
  -h, --help  show this help message and exit
  -d DEPTH    max search depth (used by the find command)
  -s          include submodules
  -l          list repos
  -x          allow pushing to repos (expert mode)
```

## Notes

* The default search depth is 6

* The ``-x`` flag is required to use the ``push`` command

## Examples

### Check status of all development projects

```
[hostname ~/devel]$ git all -d 2 status
```

### Change all submodules of a project from detached heads to master branches

```
[hostname ~/motor/modules]$ git all -s status
[hostname ~/motor/modules]$ git all -s fetch
[hostname ~/motor/modules]$ git all -s checkout master
[hostname ~/motor/modules]$ git all -s status
```

### Convert a shallow synApps clone to a full synApps clone

```
[hostname ~/synApps]$ git all fetch --unshallow
[hostname ~/synApps]$ git all config remote.origin.fetch "+refs/heads/*:refs/remotes/origin/*"
[hostname ~/synApps]$ git all fetch origin

```

Note: [assemble_synApps.sh](https://github.com/EPICS-synApps/support/blob/master/assemble_synApps.sh) creates a shallow clone by default.
