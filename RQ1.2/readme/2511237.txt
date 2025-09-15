# supervision

supervision lets you install and switch between multiple versions of SiteVision.

## What can supervision do for you?

```
supervision 0.6.0
usage: supervision <command> [<args>]

What supervision can do for you:
   use           Set the SiteVision version
   version       Show the current SiteVision version
   versions      List all SiteVision available to supervision
   install       Download and install a SiteVision version
   console       Start the current SiteVision version in console mode
```

## Install using Homebrew

On macOS with the `brew` command it's easy:

```
$ brew install svendahlstrand/tap/supervision
```

## Install the "hard" way

Just download the file [supervision][1], make it executable and place it somewhere in your path. Like this:

```bash
$ curl -O https://raw.github.com/svendahlstrand/supervision/master/bin/supervision && chmod +x supervision
```

### Prerequisites

On Linux you may have to install [davfs2][2].

And of course it helps to have a copy and license for SiteVision. ;)

## Install a SiteVision version manually

The easiest way to install a new SiteVision version is by running `supervision install`. All versions are located in the directory `~/.supervision/versions`, so it's not hard to install manually. Just download and unpack.

When you `ls` the `versions` directory it should look something like this:

```bash
$ ls -1 ~/.supervision/versions/
3.6.7-49
4.0.1-26
4.0.2-40
4.0.3-41
4.1-beta
```

[1]:https://raw.githubusercontent.com/svendahlstrand/supervision/master/bin/supervision
[2]:http://savannah.nongnu.org/projects/davfs2
