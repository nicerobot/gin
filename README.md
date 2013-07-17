# gin

Run commands directly from [github](https://gist.github.com/) gists.

## Installation:

Assuming you put scripts into `${HOME}/bin`:

>     curl -ks https://raw.github.com/nicerobot/gin/master/ginstall | sh

## Configure a command

Let's run the Gist: [`gin-shtest.sh`](https://raw.github.com/gist/1623040/gin-shtest.sh).

First, create a symlink to it.

>     SCRIPT=1623040/gin-shtest.sh ${HOME}/bin/ginln

That didn't download the file. It only creates a symbolic link. The benefit (and danger) is that, now, with each execution of gin-shtest, the file will be pulled from github. e.g.

### Test the command

The symbolic link that was created above can be executed just link any other command line script.

>     ${HOME}/bin/gin-shtest gin

>>     Hello, gin!

- Note how script-links are created without extensions. The extension is important to `gin` but it isn't important to you so it's left off.

### What happened?

Look at the source for [`gin-shtest.sh`](https://raw.github.com/gist/1623040/gin-shtest.sh) on GitHub.

Basically, what just happened is:

>     curl -ks https://raw.github.com/gist/1623040/gin-shtest.sh | sh -s gin

1. Fetch the file from GitHub: `curl -ks https://raw.github.com/gist/1623040/gin-shtest.sh`
2. Pipe the script to `sh`
3. Pass in the parameter "gin": `-s gin`

That's it.

### It works for python too

[`gin-pytest.py`](https://raw.github.com/gist/1623040/gin-pytest.py)

>     SCRIPT=1623040/gin-pytest.py ${HOME}/bin/ginln

### Test the command

>     ${HOME}/bin/gin-pytest

>>     Hello, gin!

# Security

## Link to specific versions of scripts which you know are safe.

### Configure commands

To be secure, it's a good idea to link to a specific commit to ensure that someone doesn't change the file out from under you. It's possible with `gin` like so:

[`gin-shtest.sh`](https://raw.github.com/gist/1623040/3cafab50e9ecf35885a68e98c64d32900d306689/gin-shtest.sh)

>     curl -ks https://raw.github.com/nicerobot/gin/master/ginln \
>     | SCRIPT=1623040/3cafab50e9ecf35885a68e98c64d32900d306689/gin-shtest.sh sh
>     ${HOME}/bin/gin-shtest

>>     Hello, gin!

As seen, the SCRIPT= value is simply the link to the raw.github.com file. Include a specific commit and it's _locked_ to that file.

[`gin-pytest.py`](https://raw.github.com/gist/1623040/21c07ed06a5ba0160d0918beb4cd83b82021abf3/gin-pytest.py)

>     curl -ks https://raw.github.com/nicerobot/gin/master/ginln \
>     | SCRIPT=1623040/21c07ed06a5ba0160d0918beb4cd83b82021abf3/gin-pytest.py sh
>     ${HOME}/bin/gin-pytest

>>     Hello, gin!
