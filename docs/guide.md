# Guide

This page illustrates typical workflows of `shelp` to manage packages.

See [CLI Usage](../cli-usage/) for available options of each command.

## Install Packages

Use `shelp install` to install a package.  
Detailed instruction is on [Tutorial](../tutorial/#install-packages) page.

If the package contains executable files in its `bin/` or root directory, symbolic links pointing
them will be created in `$SHELP_ROOT/bin/` directory on installation.  
`$SHELP_ROOT/bin` is added to `$PATH` by `shelp init -`, so you can use the executable files without
specifying their paths.

You can configure for which files symbolic links are to be created with the
[configuration file](../configuration/#configuration-file).

!!! hint
    `shelp add` command is the alias of `shelp install`.

## View Installed Packages

To see installed packages, run:

```sh
shelp list
```

## Load Scripts in Packages

Shell function `include` provided by `shelp init -` enables you to load a shell script in a package
in easier way:

```sh
include <package> <script-path>
```

Example is on [Tutorial](../tutorial/#include-function) page.

## Uninstall Packages

You can uninstall a package with `remove` or `uninstall` command:

```sh
shelp remove <package-name>
```

This command also clears symbolic links of executable files if any of them exists.

!!! hint
    `shelp uninstall` command is the alias of `shelp remove`.

## Upgrade Packages

You can check outdated packages by running this command:

```sh
shelp outdated
```

"A package is outdated" means it has updates which can be pulled from tracking remote.  
In such a case, you can use `shelp upgrade` command to keep packages up-to-date:

```sh
shelp upgrade [<package-name>]
```

If you ommit the package name, this upgrades all outdated packages.

## Pseudo Installation by `link` Command

`shelp link` command makes a symbolic link in the package directory pointing to an existing
directory in the file system.

For example, following command will create a symbolic link of current directory as if it is a `shelp` _package_:

```sh
shelp link .
```

The package name will be the name of the directory in this case.

This feature is useful to check what it will be like when the directory is installed as `shelp`
package.

This command does not require the source directory to be a git repository.

## Configure Packages to be Installed

With configuration file explained in [Configuration](../configuration/#configuration-file) page,
you can manage packages to be installed with some properties.

A recommended way is to use default `$SHELP_ROOT/config.yml` path for it so that you can run the
following command with no option:

```sh
shelp bundle
```

This installs all configured packages in the config file.

On the other hand, the following command removes packages not configured in the file:

```sh
shelp prune
```

It will be nice if you keep the configuration file in a VCS repository.
