# gin

Run commands directly from [github](https://gist.github.com/) gists.

## Installation:

Assuming you put scripts into `${HOME}/bin`:

>     curl -ks https://raw.github.com/nicerobot/gin/master/ginstall | sh

## Configure commands

[`gin-shtest.sh`](https://raw.github.com/gist/1623040/gin-shtest.sh)

>     SCRIPT=1623040/gin-shtest.sh ${HOME}/bin/ginln
>     ${HOME}/bin/gin-shtest # Note how script-links are created without extensions.

>>     Hello, gin!

### Works for python too

[`gin-pytest.py`](https://raw.github.com/gist/1623040/gin-pytest.py)

>     SCRIPT=1623040/gin-pytest.py ${HOME}/bin/ginln
>     ${HOME}/bin/gin-pytest

>>     Hello, gin!

# Security

## Link to specific versions of scripts which you know are safe.

### Configure commands

[`gin-shtest.sh`](https://raw.github.com/gist/1623040/3cafab50e9ecf35885a68e98c64d32900d306689/gin-shtest.sh)

>     curl -ks https://raw.github.com/nicerobot/gin/master/ginln \
>     | SCRIPT=1623040/3cafab50e9ecf35885a68e98c64d32900d306689/gin-shtest.sh sh
>     ${HOME}/bin/gin-shtest

>>     Hello, gin!

[`gin-pytest.py`](https://raw.github.com/gist/1623040/21c07ed06a5ba0160d0918beb4cd83b82021abf3/gin-pytest.py)

>     curl -ks https://raw.github.com/nicerobot/gin/master/ginln \
>     | SCRIPT=1623040/21c07ed06a5ba0160d0918beb4cd83b82021abf3/gin-pytest.py sh
>     ${HOME}/bin/gin-pytest

>>     Hello, gin!
