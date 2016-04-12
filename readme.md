# sync files all over the place
**ssync** (**s**ystem **sync**) is a symlinking git wrapper for [config] files.

:construction: *Still under development but apparently stable. Keep backups though, just in case.*

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

## Setup & Usage
As root user these are the first steps to get started:
```
# ssync
```
ssync will tell you to edit the config template created at `/etc/ssync.conf`.
Afterwards execute the setup:
```
# ssync setup new
```
On subsequent installations you would call `ssync setup` but for now the `new` parameter is required to create a new ssync-compatible repository and push it upstream.
Look at the initial commit:
```
# ssync log
```
For the moment the repo is clean:
```
# ssync status
```
Add some files or folders to keep in sync:
```
# ssync add /etc/bash.bashrc
# ssync add foo_file
# ssync add /root/bar_directory
```
This moves the specified paths to the repository and puts symlinks in their original places.
Now `ssync status` will show these recent changes.
To remove repository contents and restore them try:
```
# ssync rm /root/bar_directory
```
To synchronize your files to other machines package the changes with
```
# ssync commit "added some files"
```
and publish them:
```
# ssync publish
```
After installing ssync on another machine you can would use
```
# ssync update
```
to fetch the latest changes.


**For a full command overview use: `ssync help`**
