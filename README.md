# openfl/libpixman

This fork of [Pixman](https://gitlab.freedesktop.org/pixman/pixman) has been modified to work with [Lime](https://github.com/openfl/lime). (Specifically, files.xml was added and config.h was modified.) This isn't necessarily the latest version of Pixman, but it is the version that has been tested with Lime.

## Installing Lime and Pixman

1. [Fork Lime](https://github.com/openfl/lime/fork). (If you already did, skip to step 3.)
2. Install your fork as a Haxelib.

   ```bash
   $ haxelib git lime git@github.com:[username]/lime.git
   Installing lime from https://github.com/[username]/lime.git
   Library lime current version is now git
   ```

3. Navigate to [Haxelib folder]/lime/git/project/lib/pixman.

   This folder contains the Pixman project, which is treated as a separate Git repo even though it's inside the Lime folder.

4. Make a new branch to keep track of your upcoming changes.

   ```bash
   $ git checkout -b [new branch name]
   ```

## Updating Pixman

If you're running into an error in Pixman, first try pulling the latest version.

1. Add the [official Pixman repo](https://gitlab.freedesktop.org/pixman/pixman) as a remote:

   ```bash
   $ git remote add upstream https://gitlab.freedesktop.org/pixman/pixman.git
   ```

2. Pull the latest changes, and merge if necessary.

   ```bash
   $ git pull upstream master
   ```

3. Test the update.

   ```bash
   $ lime rebuild cpp -clean
   $ lime rebuild android -clean
   ```

   If on Mac, also test `lime rebuild ios -clean`.

If the update doesn't work, here are potential solutions:

- Add missing files near the bottom of files.xml. When Pixman adds new C++ source files, the compiler will initially fail to find them.
- Add missing compiler flags near the top of files.xml.
- If you suspect a `#define` is missing, see the top of config.h for instructions.
- [Open an issue](https://github.com/openfl/libpixman/issues) for errors without an obvious solution.

## Contributing to openfl/libpixman

To submit your changes, you'll need to make a second GitHub fork.

1. [Fork openfl/libpixman](https://github.com/openfl/libpixman/fork).
2. Add your new remote:

   ```bash
   $ cd [Haxelib folder]/lime/git/project/lib/pixman
   $ git remote add origin git@github.com:[username]/libpixman.git
   ```

3. Now you have somewhere to push to:

   ```bash
   $ git add .
   $ git commit
   $ git push -u origin [new branch name]
   ```

4. [Open a pull request](https://github.com/openfl/libpixman/pulls).

Making changes to Pixman will also apply a change to Lime. This change must be submitted separately.

1. Navigate to [Haxelib folder]/lime/git.
2. Push your changes.

   ```bash
   git checkout -b updatepixman
   git add .
   git commit -m "Update Pixman"
   git push -u origin updatepixman
   ```

3. [Open a pull request](https://github.com/openfl/lime/pulls).
