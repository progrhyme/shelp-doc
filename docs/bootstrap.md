# Bootstrap

You need to go through following steps to start using `shelp`:

1. Install `shelp` binary
1. Activate `shelp` in your shell

## Install shelp

There are several ways to install `shelp` :

- [Homebrew](https://brew.sh/) or [Linuxbrew](https://docs.brew.sh/Homebrew-on-Linux) (using Tap)
- Download from GitHub releases
- go get (go command is needed)

Choose one which is suitable for you.

### Homebrew (Linuxbrew)

```sh
brew tap progrhyme/taps
brew install shelp
```

### Download from GitHub releases

Download latest binary from GitHub [releases](https://github.com/progrhyme/shelp/releases)
and put it under one directory in `$PATH` entries.

Let's see typical commands to achieve this:

```sh
bin=/usr/local/bin  # Change to your favorite path
version=0.6.0       # Make sure this is the latest
os=darwin           # or "linux" is supported
curl -Lo $bin/shelp "https://github.com/progrhyme/shelp/releases/download/v${version}/shelp_${version}_${os}_x86_64"
chmod +x $bin/shelp
```

### go get

Run the following:

```sh
go get github.com/progrhyme/shelp
```

## Activate in Shell

To enable `shelp` automatically in your shell, append the following to your profile script
(such as `~/.bashrc` or `~/.zshrc`):

```sh
# For POSIX-compatible shells
eval "$(shelp init -)"
```

As for fish shell, append the following to `~/.config/fish/config.fish`:

```sh
# For fish shell
shelp init - | source
```

If you want to store `shelp` materials in a location different from the default `~/.shelp`, set
`SHELP_ROOT` environment variable beforehand.

See [Configuration](../configuration) page for details and other options.
