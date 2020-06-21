# Configuration

There are some ways to configure `shelp` behavior:

- Environment variables
- Configuration file
- Command-line options

## Environment Variables

There are a few environment variables which `shelp` refers on running:

 Variable | Default | Description
----------|---------|-------------
 SHELP_CONFIG | `$SHELP_ROOT/config.yml` | Path of config file
 SHELP_ROOT | `$HOME/.shelp` | Directory where the contents are stored

## Configuration File

You do not necessarily need a configuration file to use `shelp`.  
But it will bring you a powerful functionality to manage packages with the file.

Here is an example configuration describing the most of available properties:

```YAML
path:
  # SHELP_ROOT directory
  # Default: "~/.shelp"
  # NOTE: "~" is not expanded on loading YAML
  root: "/usr/local/shelp"

# Package configs for installation
# Spec:
# - from: <remote-location>
#   as: <package-name>
#   at: <branch-or-tag-or-commitHash>
#   bin:
#     - <path-to-bin-file>
#     - :
packages:
- from: b4b4r07/enhancd@v2.2.4
- from: gitlab.com/dwt1/dotfiles
  as: dwt1-dotfiles
- from: bpkg/bpkg
  bin:
    - bpkg
- from: git@github.com:someone/gitproject.git
  at: feature/awesome
```

When you run `shelp bundle` with this configuration, the listed packages will be installed.

And when you run `shelp prune` with it, packages not configured will be uninstalled.

## Command-line Options

`-c|--config CONFIG` option is available for all commands.  
It specifies the path of configuration file and takes precedence over the environment variable
`SHELP_CONFIG`.
