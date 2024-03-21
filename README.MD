# Tmux Sessionizer

This script facilitates the management of tmux sessions by allowing users to quickly select a project directory and either create a new tmux session or switch to an existing one associated with that directory.

## Overview

This script is based on [ThePrimeagen's](https://github.com/ThePrimeagen/.dotfiles/blob/master/bin/.local/scripts/tmux-sessionizer) *blazingly fast* `tmux-sessionizer` script but instead of reliyng on a static list of directories I choose to setup an ENVAR `TMS_PJ_DIRS` to define the list of directories to choose from.

If `TMS_PJ_DIRS` is not defined, tmux-sessionizer will use the current directory.

## Requirements

- `tmux` installed on the system ([install instructions](https://github.com/tmux/tmux/wiki/Installing))
- `fzf` (fuzzy finder) for directory selection ([install instructions](https://github.com/junegunn/fzf?tab=readme-ov-file#installation))

## Blazingly Fast Installation
```sh
$ git clone github.com/pxlctzn/tmux-sessionizer && chmod +x ./tmux-sessionizer && mv ~/.local/bin/scripts/tmux-sessionizer && echo "export PATH=$PATH:~/.local/bin/scripts" >> ~/.bashrc
```

1. Download the script using git clone: `$ git clone github.com/pxlctzn/tmux-sessionizer`;
2. Make it executable: `$ chmod +x tmux_sessionizer`;
3. Move the `tmux_sessionizer` file (not the directory) into `~/.local/bin/scripts/`;
4. Add the `~/.local/bin/scripts/` directory to your PATH.

See, **blazingly fast**!

Don't forget to reload your terminal or `source ~/.bashrc` to use tmux-sessionizer.

## Setup
Create an ENVAR named `TMS_PJ_DIRS` listing your projects top directory. The expected format is : "/path/to/directory1 /path/to/directory2 /path/to/directory3"

## Usage
```bash
$ tmux_sessionizer [directory]
```

* If a directory is provided as an argument, the script will use that directory for selection.
* If no argument is provided, the script will use the directories specified in the `TMS_PJ_DIRS` ENVAR for selection.
    * If `TMS_PJ_DIRS` is not defined, the script will default to using the current directory for selection.
* If a directory is selected (either through `TMS_PJ_DIRS` or as an argument), the script checks if a tmux session with the same name exists. If not, it creates a new session with that name and sets the working directory to the selected directory.
* If a tmux session with the selected name already exists, the script switches to that session.

## Acknowledgments
The script is based on ThePrimeagen's original [tmux-sessionizer](https://github.com/ThePrimeagen/.dotfiles/blob/master/bin/.local/scripts/tmux-sessionizer). Watch out though, it is **blazingly fast**.
Uses `fzf` for fuzzy directory selection.
