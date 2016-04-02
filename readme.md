# sync files all over the place
**ssync** (**s**ystem **sync**) is a symlinking git wrapper for [config] files.

:warning: *Currently in early development. You might want to avoid productive use until this notice is removed...* :construction:

## Synopsis
It acts as a wrapper to put any file into its repository and puts a symlink in the original place. This allows to apply version control without having to store stuff in one place or litter your drive with separate repositories.

The idea is to synchronize multiple machines this way by synchronizing everything that is not created by packages but was placed or configured manually. If you only care about files in `/etc` you might want to have a look at [etckeeper](https://github.com/joeyh/etckeeper), if manually gitting `~/.config` is enough, fine... but if you like to unify all of this and would like to have full control over a selective set of files **ssync** might be just the right tool for you.

## Requirements
- Dependencies
  - `git` version 2.X
  - `rsync` (tested with version 3)
  - GNU's `coreutils`, `bash` version 4
- Permissions
  - needs to run as **root** to properly deal with file permissions
