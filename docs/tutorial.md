# Tutorial

This page explains basic features of `shelp` with instruction.

## Install Packages

`shelp` installs any git repositories as _packages_.  
The typical way to do it is to run `shelp install` command.

SYNOPSIS:

```sh
# Handy syntax using HTTPS protocol
shelp install [<site>/]<account>/<repository>[@<ref>] [<package>]

# Specify complete git-url with any protocol
shelp install <git-url> [<package>]
```

You can specify any branch or tag or commit hash for `@<ref>` parameter.

For example, the following command installs https://github.com/bats-core/bats-core
into `$SHELP_ROOT/packages/bats` directory.

```sh
shelp install bats-core/bats-core bats
```

Then, you can run `bats` command in the package.

!!! note
    To specify commit hash as `@<ref>` param, you must provide first 7 digits of it at least.

Other Examples:

```sh
# Handy syntax
shelp install b4b4r07/enhancd           # Install "enhancd" from github.com
shelp install b4b4r07/enhancd@v2.2.4    # Install specified tag or branch
shelp install gitlab.com/dwt1/dotfiles  # Install from gitlab.com

# Specify git-url
shelp install git@github.com:b4b4r07/enhancd.git  # Install via SSH protocol
shelp install file:///path/to/repository          # Install via Local protocol
shelp install git://server/gitproject.git         # Install via Git protocol
```

!!! note "Limitation"
    1. Unless commit hash is specified with `@<ref>` param, `shelp install` clones repository as
    shallow one, with `--depth=1` option
    1. You can't specify `--branch` option in the latter command syntax, nor others

You can install packages more configurable way by `shelp bundle` command and the configuration file.  
See [Configuration](../configuration) page for more details.

## `include` Function

The bootstrapping command `shelp init -` loads a shell function `include`.

Function Usage:

```sh
include <package> <script-path>
```

This will load `<script-path>` in `<package>` by `.` shell built-in function.

!!! example
    Suppose you have installed [https://github.com/ohmyzsh/ohmyzsh](https://github.com/ohmyzsh/ohmyzsh) by shelp.  
    Then, the following command load oh-my-zsh.sh on your current shell:

    ```sh
    include ohmyzsh oh-my-zsh.sh
    ```

!!! info
    - In fish shell, _source(1)_ command is used instead of `.` to load scripts
