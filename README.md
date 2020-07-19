kiss-hook manager
-----------------

A directory based kiss-hook manager. I prefer to use this structure now after
having a single script with tons of `case` statements. It was hard to read and
hard to manage.


Installation
------------

If you want to install this, copy (or symlink) the `kiss-hook` file to the
directory you will be using as the hook directory. You will then need to
set the `$KISS_HOOK` variable pointing to this script.

If you don't want to put this script to the hook directory, you can set the
environment variable `$KISS_HOOK_DIR` pointing to that directory.


Setting up hooks
----------------

For every hook, you can set up a directory or a single file with the name of the
hook. You can add a file named `lib` to the hook directory which will be sourced
for every hook. This is useful for using functions on multiple hook types.

For example with the `post-build` hook, if you have package specific
configuration you create a directory named `post-build/`. In it you will have
files for all packages that you want to hook into. If you are hooking `gcc`,
`sbase`, and `less` you will have `post-build/gcc` `post-build/sbase`, and
`post-build/less` files. If you also want a hook that will affect every package
you will need to add `post-build/post-build`.

If you don't have a package specific hook, but you want a hook that will deal
with every package (or a hook that doesn't even deal with packages), you can
simply create a file for the hook.

Here is an example structure:


    ├── kiss-hook
    ├── lib
    ├── post-build
    │   ├── gcc
    │   ├── less
    │   ├── post-build
    │   └── sbase
    ├── post-install
    │   └── linux
    ├── pre-build
    └── pre-fetch
