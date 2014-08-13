# README #

A great article, [Let's Compile Like its 1992](http://fabiensanglard.net/Compile_Like_Its_1992/), provides some real nostalgia in its detailed description of setting up a build environment to compile classic Wolf3D. I've attempted to make it easy to *"jump start"* the process by providing a pre-configured environment. 

*To fully appreciate the process one **really should** read the article in full and go through all the steps!* 

But... if you want a bit of a bootstrap...

### What will you find? ###

* Commit Log of incremental setup and configuration
* All Zip archives used for setup
* Full build environment with path corrections noted by Fabien
* A full build branch containing the build process in the commit log and the end result, a running version of Wolf3D compiled in the environment.

### How do I get set up? ###

#### Install DOSBox ####

Make sure you have [DOSBox](http://www.dosbox.com/) installed and setup. In my case (using **crouton** to run *trusty* on my Chromebox)

```
sudo apt-get install dosbox
```

Pretty well did the trick. Your mileage may vary and DOSBox configuration is on you.

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

Remember to set your PATH environment variable in your DOSBox to `path=c:\borlandc\bin` per Fabien's write-up, else Borland C will bork about not finding the tools to perform the build (eg TASM.EXE).

### Anything else? ###

That's about it.

Hopefully this will help get things bootstrapped for a few people.

cheers! -morgan