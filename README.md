# qBittorrent-nox static

This is a build script for qBittorrent-nox static. This script is just a modified version of  https://github.com/userdocs/qbittorrent-nox-static. The argument's explanation was rewritten. Parameter checks will be finished before dependencies installed. It also includes Git Action workflow to automatically build binaries.

## Available arguments

```
qBittorrent static build script

Usage: bash qbittorrent-static.sh [modules] [OPTS]

  available modules:

  all | install | bison | gawk | glibc | zlib | icu | openssl | boost
  libtorrent | qtbase | qttools | qbittorrent


Options:

  -b,--build-directory <path>      Setup build path for script
                                   Default build location: ./qb-build

  --boot-strap                     Creates dirs in this structure:
                                   ./qb-build/patches/APPNAME/TAG/patch

  -d,--debug                       Enables debug symbols for libtorrent and
                                   qBitorrent when building

  -n,--no-delete                   Skip all delete functions for selected
                                   modules to leave source code directories
                                   behind.

  -o,--optimize                    Warning, using this flag will mean your
                                   static build is limited to a matching CPU

  -p,--proxy <proxy>               Specify a proxy URL and PORT to use with
                                   curl and git

  -v,--verbose                     Enable verbose output

  -i,--icu                         Use ICU libraries when building qBittorrent.
                                   Final binary size will be around ~50Mb

  -m,--master                      Always use the master branch for
                                   libtorrent and qBittorrent

  --lm,--libtorrent-master         Always use the master branch for libtorrent

  --qm,--qbittorrent-master        Always use the master branch for qBittorrent

  --lt,--libtorrent-tag <tag>      Use a provided libtorrent tag when cloning
                                   from github.

  --qt,--qbittorrent-tag <tag>     Use a provided qBittorrent tag when cloning
                                   from github.

  --pr,--patch-repo <patch>        Specify a username and repo to use patches
                                   hosted on github

  --c-std <11/14/17>               Specify a C standard version for compiling

  --skip-<module>                  Skip rebuilding module if already exist

  -h, --help                       Display this help and exit

  --help-all,--full-help           Show more details about usage
```

## How to use Git Action

It requires 2 secrets: `QBIT_VERSION` and `LT_VERSION`. You can find the tag in [qBittorrent release](https://github.com/qbittorrent/qBittorrent/releases) and [Libtorrent release](https://github.com/arvidn/libtorrent/releases). First of all, fork this repo, and create your secrets. After secrets created, you can click "Run workflow" to build your binary.

It should take about half an hour to build amd64 binary. arm64 and armhf require defiantly a much longer time.

