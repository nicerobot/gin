# gin

Run commands directly from [github](https://gist.github.com/) gists.

## Installation:

Assuming you put scripts into `${HOME}/bin`:

>     curl -ks https://raw.github.com/nicerobot/gin/master/ginstall | sh

## Configure a command

Let's run the Gist: [`gin-shtest.sh`](https://gist.github.com/nicerobot/1623040/raw/gin-shtest.sh).

First, create a symlink to it.

>     SCRIPT=nicerobot/1623040/raw/gin-shtest.sh ${HOME}/bin/ginln

That didn't download the file. It only creates a symbolic link. The benefit (and danger) is that, now, with each execution of gin-shtest, the file will be pulled from github. e.g.

### Test the command

The symbolic link that was created above can be executed just link any other command line script.

>     ${HOME}/bin/gin-shtest gin

>>     Hello, gin!

- Note how script-links are created without extensions. The extension is important to `gin` but it isn't important to you so it's left off.

### What happened?

Look at the source for [`gin-shtest.sh`](https://gist.github.com/nicerobot/1623040/raw/gin-shtest.sh) on GitHub.

Basically, what just happened is:

>     curl -ks https://gist.github.com/nicerobot/1623040/raw/gin-shtest.sh | sh -s gin

1. Fetch the file from GitHub: `curl -ks https://gist.github.com/nicerobot/1623040/raw/gin-shtest.sh`
2. Pipe the script to `sh`
3. Pass in the parameter "gin": `-s gin`

That's it.

You can run `gin` scripts within other scripts. Even call other `gin` scripts from within `gin` scripts. It's simply a shell script (almost) like any other.

# Possible Uses

Imagine a GitHub-centralized configuration utility for your local computing environment. For example, i want to always share the same homebrew installation. I can write a Gist that lits all the packages to install. I can write a `gin` that reads it and runs the update. I can even write a `gin` that keeps all my `gin` symlinks consistent across machines.

### It works for python too

[`gin-pytest.py`](https://gist.github.com/nicerobot/1623040/raw/gin-pytest.py)

>     SCRIPT=nicerobot/1623040/gin-pytest.py ${HOME}/bin/ginln

### Test the command

>     ${HOME}/bin/gin-pytest

>>     Hello, gin!

# Security

## Link to specific versions of scripts which you know are safe.

### Configure commands

To be secure, it's a good idea to link to a specific commit to ensure that someone doesn't change the file out from under you. It's possible with `gin` like so:

[`gin-shtest.sh`](https://gist.github.com/nicerobot/1623040/raw/df8a3733e4c9226c5c83b30fe927e0c4cc3232e9/gin-shtest.sh)

>     curl -ks https://raw.github.com/nicerobot/gin/master/ginln \
>     | SCRIPT=nicerobot/1623040/raw/df8a3733e4c9226c5c83b30fe927e0c4cc3232e9/gin-shtest.sh sh
>     ${HOME}/bin/gin-shtest

>>     Hello, gin!

As seen, the SCRIPT= value is simply the link to the raw.github.com file. Include a specific commit and it's _locked_ to that file.

[`gin-pytest.py`](https://gist.github.com/nicerobot/1623040/raw/21c07ed06a5ba0160d0918beb4cd83b82021abf3/gin-pytest.py)

>     curl -ks https://raw.github.com/nicerobot/gin/master/ginln \
>     | SCRIPT=nicerobot/1623040/raw/21c07ed06a5ba0160d0918beb4cd83b82021abf3/gin-pytest.py sh
>     ${HOME}/bin/gin-pytest

>>     Hello, gin!
