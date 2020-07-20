# shelp

[![release](https://badgen.net/github/release/progrhyme/shelp)](https://github.com/progrhyme/shelp/releases)

`shelp` is a Git-based package manager written in Go, primarily for shell scripts.

## What is this for?

With `shelp`, you can do the followings:

- Install any git repositories reachable with `git` command and organize them under `$SHELP_ROOT` directory. `shelp` treat them as _packages_
- Add any executable files in a _package_ into `$PATH` when `shelp` installs it
- Load any shell script in a _package_ easily by `include` function bundled in `shelp`
- Manage what _packages_ to be installed and how by the configuration file; and install them at once
- Specify any git branch or tag or commit hash for a _package_ to install

## System Requirements

- OS: Linux or macOS
- `git` command

Supported Shells:

- Bash, Zsh and most POSIX compatible shells
- fish shell

## To Get Started

These guides will show you how to use `shelp` step by step:

- [Bootstrap](./bootstrap/) ... Install and activate `shelp` in your shell
- [Tutorial](./tutorial/) ... Basic usage of `shelp`
- [Configuration](./configuration/) ... Configure and customize `shelp` settings
- [Guide](./guide/) ... More usecases with `shelp` packages
- [CLI Usage](./cli-usage/) ... Command reference

## Versions

Latest v0.6.0 was released on 2020-06-20.

Refer to [CHANGELOG.md](https://github.com/progrhyme/shelp/blob/master/CHANGELOG.md) to see difference between versions.

## Alternatives

There are other tools to manage shell scripts in modular way like `shelp` does.  
Here are some examples:

 Software | Supported Shells
----------|------------------
 [basherpm/basher](https://github.com/basherpm/basher) | Bash, Zsh, fish shell
 [zplug](https://github.com/zplug/zplug) | Zsh
 [bpkg](https://www.bpkg.sh/) | Bash
 [jorgebucaran/fisher](https://github.com/jorgebucaran/fisher) | fish shell

## Special Thanks

**basher** inspired me to implement some features of this tool.

## License

The MIT License.

Copyright &copy; 2020 IKEDA Kiyoshi
