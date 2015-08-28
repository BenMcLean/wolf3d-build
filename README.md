# README #

A great article, [Let's Compile Like its 1992][original-post], provides some real nostalgia in its detailed description of setting up a build environment to compile classic [Wolfenstein 3D][wolf3d-wiki]. I've attempted to make it easy to *"jump start"* the process by providing a pre-configured environment. 

*To fully appreciate the process one **really should** [read the article][original-post] in full and go through all the steps!* 

But... if you want a bit of a bootstrap...

### What will you find? ###

* Commit Log of incremental setup and configuration
* All Zip archives used for setup
* Full build environment with path corrections noted by Fabien
* A full build branch containing the build process in the commit log and the end result, a running version of Wolf3D compiled in the environment.

### How do I get set up? ###

#### Install DOSBox ####

Make sure you have [DOSBox][dosbox] installed and setup. In my case (using **[crouton][crouton]** to run *trusty* on my Chromebox)

```
sudo apt-get install dosbox
```

Pretty well did the trick. Your mileage may vary and [DOSBox][dosbox] configuration is on you.

#### Check it out and go...(almost) ####

Get the configured build environment with:

```
git clone https://Corra@bitbucket.org/Corra/wolf3d-build.git

```

Optionally rewind a bit and start with decompressing the *vgafiles.zip*:

```
git checkout vanilla-wolf3d
```

Or *fast-forward* because you just want the end result:

```
git checkout full-build
```
Alternatively
```
git clone https://Corra@bitbucket.org/Corra/wolf3d-build.git -b full-build
```

### What next? ###

Follow Fabien's article. Seriously.

Assuming you've detached to `vanilla-wolf3d` you should have something like this:
```
(trusty)corra@localhost:~/wolf3d-build$ ls -l c
total 1584
-rw-rw-r--  1 corra corra 856401 Aug 13 02:09 1wolf14.zip
drwxrwxr-x 13 corra corra   4096 Aug 13 02:09 BORLANDC
-rw-rw-r--  1 corra corra 170521 Aug 13 02:09 vgafiles.zip
drwxrwxr-x  2 corra corra   4096 Aug 13 02:09 WOLF3D
drwxrwxr-x  4 corra corra   4096 Aug 13 02:09 WOLFSRC
-rw-rw-r--  1 corra corra 576902 Aug 13 02:09 wolfsrc.zip
```
Which constitutes:

* fetched assets
* Shareware Wolf3D installed at `c/WOLF3D`
* Borland C Compiler installed
* Wolf3D Source code in `c/WOLFSRC`
* Project paths fixed for `GAMEPAL.OBJ` and `SIGNON.OBJ`

### Tips ###

#### Set your PATH ####
Remember to set your PATH environment variable in your [DOSBox][dosbox] to `path=c:\borlandc\bin` per Fabien's write-up, else Borland C will bork about not finding the tools to perform the build (eg TASM.EXE).

#### Error: Tried to load a sparse page! ####
This was [reported as a issue][sparse-page-issue] where I [comment][sparse-page-issue-comment] about a [comment thread][sparse-page-post-comment] that addresses this on [Fabian's original post][original-post].

The upshot is this is apparently a edge case issue with [DOSBox][dosbox] and digitized sound and the solution provided is `Set "Digitised Sound" to "None"`.

### Anything else? ###

Aside from that I decide to do things like this on copious amounts of sleep deprivation?

That's about it.

Hopefully this will help get things bootstrapped for a few people.

cheers! -morgan

[original-post]: http://fabiensanglard.net/Compile_Like_Its_1992/ "Let's Compile Like its 1992"
[sparse-page-post-comment]: https://disqus.com/home/discussion/fabiensanglardswebsite/compile_like_its_1992/#comment-1538345406
[sparse-page-issue]: https://bitbucket.org/Corra/wolf3d-build/issues/1/tried-to-load-a-sparse-page "Tried to load a sparse page!"
[sparse-page-issue-comment]: https://bitbucket.org/Corra/wolf3d-build/issues/1/tried-to-load-a-sparse-page#comment-21321588
[dosbox]: http://www.dosbox.com/ "DOSBox"
[wolf3d-wiki]: https://en.wikipedia.org/wiki/Wolfenstein_3D "Wikipedia entry: Wolfenstein 3D"
[crouton]: https://github.com/dnschneid/crouton

