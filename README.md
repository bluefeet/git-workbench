# Git Workbench

The `git workbench` commands provide a sandboxed replica of the user's
git repository.  This sandbox is meant to be used by automation and can
provide a safe place for automated developer tooling to do there git work.

Before the workbench is used all tools should first ensure that the
workbench is in a pristine state:

    git workbench pristine

This will ensure that everything is setup right and that the workbench
repository is in sync with the source repository.

From there any git command which is preceded by `workbench` will operate
in the workbench repository instead of the user's repository.  For example:

    git workbench checkout foo

Any changes to the workbench repo will not affect the source repo.

## Commands

### init

    git workbench init

Initializes the workbench repository by cloning from the source repository,
copying hte user name and email, copying any remotes, setting up the `owner`
remote, and copying any hooks.

### remove

    git workbench remove

Removes the workbench repository.

### pristine

    git workbench pristine

If the workbench repo exists this command makes sure that it is in good working
order and any garbage left over (random branches, working tree changes, etc) is
all cleaned up.  If the workbench repo does not exist then this will automatically
call `git workbench init`.

### dir

    git workbench dir

Prints the location of the workbench repo.

