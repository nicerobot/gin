- Generalize more to provide host, port, and path in the symlink.
  - Maybe using raw.github.com[-port]/gist/[gist]/[file].[typ] as the entire symlink
  - Still default to using gist

- Download the file to tmpfil, chmod +x and execute directly. It provides more versatility.

- Providing a general link in .gin can allow testing of various versions of a script:

  e.g. 
>     # Create a generic .gin
>     ln -s git-test.py ${HOME}/.gin/
>
>     # Run several versions of the file.
>     for gist in 1623040 1623041 1623042; do
>         GINHUB="https://raw.github.com/gist/${gist}" ${HOME}/bin/gin-test.sh
>     done
