# gin

Run commands directly from [github](https://gist.github.com/) gists.

## Installation:

Assuming you put scripts into `${HOME}/bin`:

>     mkdir ${HOME}/.gin \
>     && curl -ks https://raw.github.com/nicerobot/gin/master/gin >${HOME}/bin/gin \
>     && chmod +x ${HOME}/bin/gin

## Configure commands

[`gin-test.sh`](https://raw.github.com/gist/1623040/gin-test.sh)

>     ln -s 1623040/gin-test.sh ${HOME}/.gin/
>     ln -s gin ${HOME}/bin/gin-test.sh
>     ${HOME}/bin/gin-test.sh

>>     Hello, gin!

### Works for python too

[`gin-test.py`](https://raw.github.com/gist/1623040/gin-test.py)

>     ln -s 1623040/git-test.py ${HOME}/.gin/
>     ln -s gin ${HOME}/bin/gin-test.py
>     ${HOME}/bin/gin-test.py

>>     Hello, gin!


# Security

## Link to specific versions of scripts which you know are safe.

### Configure commands

[`gin-test.sh`](https://raw.github.com/gist/1623040/3cafab50e9ecf35885a68e98c64d32900d306689/gin-test.sh)

>     ln -s 1623040/3cafab50e9ecf35885a68e98c64d32900d306689/gin-test.sh ${HOME}/.gin/
>     ln -s gin ${HOME}/bin/gin-test.sh
>     ${HOME}/bin/gin-test.sh

>>     Hello, gin!

[`gin-test.py`](https://raw.github.com/gist/1623040/21c07ed06a5ba0160d0918beb4cd83b82021abf3/git-test.py)

>     ln -s 1623040/21c07ed06a5ba0160d0918beb4cd83b82021abf3/git-test.py ${HOME}/.gin/
>     ln -s gin ${HOME}/bin/gin-test.py
>     ${HOME}/bin/gin-test.sh

>>     Hello, gin!
