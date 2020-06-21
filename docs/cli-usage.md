# CLI Usage

## Summary

General Syntax:

```sh
shelp COMMAND [arguments...] [options...]
shelp -h|--help          # Show general help
shelp COMMAND -h|--help  # Show help for COMMAND
shelp -v|--version       # Show CLI version
```

### Subcommands

```sh
shelp init       # Initialize shelp for shell environment
shelp install    # Install a package
shelp add        # Alias of "install"
shelp remove     # Uninstall a package
shelp uninstall  # Alias of "remove"
shelp list       # List installed packages
shelp upgrade    # Upgrade installed packages
shelp outdated   # Show outdated packages
shelp link       # Pseudo installation of local directory
shelp bundle     # Install packages at once with config file
shelp prune      # Remove packages not defined in config file
shelp destroy    # Delete all materials including packages
```

## init

Enable shelp in one's shell environment.

Usage:

```sh
shelp init - [SHELL]  # Print scripts (for specified SHELL)
```

It prints scripts for current shell unless user specify SHELL argument.

Options:

```sh
-c, --config string   # Configuration file
-h, --help            # Show help
```

## install (add)

Install a git repository as a shelp package and create symlinks for executable files in it.

Syntax:

```sh
# Handy syntax using HTTPS protocol
shelp COMMAND [<site>/]<account>/<repository>[@<ref>] [<package-name>]

# Specify complete git-url with any protocol
shelp COMMAND <git-url> [<package-name>]
```

If you ommit preceding `<site>/` specifier in former syntax, "github.com" is used by default.  
You can specify any branch or tag or commit hash for `@<ref>` parameter.

Options:

```sh
-c, --config string   # Configuration file
-h, --help            # Show help
-v, --verbose         # Verbose output
```

See [Tutorial](../tutorial/#install-packages) for more detailed instruction.

## remove (uninstall)

Uninstall a package clearing symlinks of executable files if they exist.

Syntax:

```sh
shelp COMMAND <package>
```

Examples:

```sh
shelp COMMAND bats-core
shelp COMMAND enhancd
```

Options:

```sh
-c, --config string   # Configuration file
-h, --help            # Show help
-v, --verbose         # Verbose output
```

## list

List installed packages.

Syntax:

```sh
shelp list
```

Options:

```sh
-c, --config string   # Configuration file
-h, --help            # Show help
-v, --verbose         # Verbose output
```

## upgrade

Upgrade installed packages.

Syntax:

```sh
# Upgrade all installed packages
shelp upgrade

# Upgrade a single package
shelp upgrade <package>
```

Options:

```sh
-c, --config string   # Configuration file
-h, --help            # Show help
-v, --verbose         # Verbose output
```

## outdated

Show installed packages which can be updated.

Syntax:

```sh
shelp outdated
```

Options:

```sh
-c, --config string   # Configuration file
-h, --help            # Show help
-v, --verbose         # Verbose output
```

## link

Pseudo installation of a package from local filesystem.  
Creates symbolic link of a directory into a package path.

Syntax:

```sh
shelp link path/to/dir [<package-name>]
```

If you ommit `<package-name>` argument, the basename of the directory is used as the package name.

Examples:

```sh
shelp link .                   # Link current directory
shelp link path/to/foo-sh foo  # Link as package "foo"
```

Options:

```sh
-c, --config string   # Configuration file
-h, --help            # Show help
-v, --verbose         # Verbose output
```

## bundle

Install packages at once which are defined in config file.

Syntax:

```sh
shelp bundle [-c|--config CONFIG]
```

Options:

```sh
-c, --config string   # Configuration file
-h, --help            # Show help
-v, --verbose         # Verbose output
```

Specification:

- If there are pseudo-installed packages created by `link` command whose names are the same as
configured packages, `bundle` operation removes the package at first, then re-install it according
to the configuration

## prune

Uninstall packages not defined in config file.

Syntax:

```sh
shelp prune [-c|--config CONFIG] [-y|--yes] [--link]
```

This doesn't remove symlinks created with `link` command by default.  
To remove them, specify `--link` option.

Options:

```sh
-c, --config string   # Configuration file
-h, --help            # Show help
    --link            # Prune symlinks at the same time
-v, --verbose         # Verbose output
-y, --yes             # Prune without confirmation
```

## destroy

Delete all contents in SHELP_ROOT including the root directory.

Syntax:

```sh
shelp destroy [-y|--yes]
```

Options:

```sh
-c, --config string   # Configuration file
-h, --help            # Show help
-y, --yes             # Destroy without confirmation
```
