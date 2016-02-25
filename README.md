[![Docker Stars](https://img.shields.io/docker/stars/neoeinstein/mono-alpine.svg?style=flat-square)](https://hub.docker.com/r/neoeinstein/mono-alpine/)
[![Docker Pulls](https://img.shields.io/docker/pulls/neoeinstein/mono-alpine.svg?style=flat-square)](https://hub.docker.com/r/neoeinstein/mono-alpine/)

Mono (C#) Docker image
======================

This image is based on Alpine Linux image, which is only a 5MB image, and contains
[Mono](http://www.mono-project.com/).

WARNING: That Mono image was compiled for Arch Linux and is ported to Alpine via
[glibc hack](https://github.com/gliderlabs/docker-alpine/issues/11)! It is being used
because the current Mono package for Alpine Linux (based on musl instead of glibc)
generates a segfault when bootstrapping the F# compiler.

Total size of this image is only:
[![](https://badge.imagelayers.io/neoeinstein/mono-alpine:latest.svg)](https://imagelayers.io/?images=neoeinstein/mono-alpine:latest 'Get your own badge on imagelayers.io')

Usage Example
-------------

```bash
$ echo 'using System; class MainClass { public static void Main (string[] args) { Console.WriteLine ("Hello World"); } }' > qq.mono
$ docker run --rm -v "$(pwd)":/mnt neoeinstein/mono-alpine sh -c "mcs -out:/mnt/qq.exe /mnt/qq.mono && mono /mnt/qq.exe"
```

Once you have run these commands you will have `qq.exe` mono-executable in your
current directory, and you will get printed 'Hello World' from Mono!

Acknowledgements
----------------

This image is based on the Alpine Linux Mono image developed by [frolvad](https://hub.docker.com/r/frolvlad/alpine-mono/).
