[Readme](../README.md) __|__ [Todo](../TODO.md) __|__ [Docs](../docs/README.md)

---

# Tmux plugins

> *added via tpm*

---

All files in this repo are ignored except rhe readme and gitignore

## Installing TPM

TPM is tmux's plugin manager.

Assuming that your tmux config is here: `~/.config/tmux` and it's the root of your git repository. The following will install TPM to the sub folder `plugins/tpm.`

### As a submodule

The advantange to installing as a sub module is that when installing these configs and git is set up properly it will pull all the files into place and you won't have to remember to clone it. Also git will not try to version the plugin.

```bash
git submodule add https://github.com/tmux-plugins/tpm plugins/tpm
```

### By cloning it

You can also clone it into the plugins folder. However each time you install this config you'll have to remember to clone it. Make sure to set up a .gitignore file for TPM and any plugins in the plugins folder.

```bash
git clone ~/.config/tmux/plugins/tpm ~/.config/tmux/plugins/tpm
```

#### Excluding contents of the plugins folder

Make a `.gitignore` in the `plugins` folder with the following:

```gitignore
# Ignore all files and sub directories
*
# Exclude (whitelist) the .gitignore.and the README.md from being ignore
!.gitignore
!tpm/
tpm/*
!README.md
```

## Plugins

You can find the largest collection of plugins on the [official tmux plugins page](https://github.com/tmux-plugins/list).

### These are the one's I'm using:

- [TPM](https://github.com/tmux-plugins/tpm) - Tmux Plugin Manager
- [dotbar](https://github.com/vaaleyard/tmux-dotbar) - Minimalist status bar theme

## Using TPM

At the bottom of your `tmux.conf` you can install plugins using the `set -g @plugin` notation.

```conf
# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'vaaleyard/tmux-dotbar'

# Other examples of installing plugin syntax:
# set -g @plugin 'github_username/plugin_name'
# set -g @plugin 'github_username/plugin_name#branch'
# set -g @plugin 'git@github.com:user/plugin'
# set -g @plugin 'git@bitbucket.com:user/plugin'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'
```

### Installing a plugin

After the plugin has been added to the `tmux.conf` you can fetch, install and refresh the tmux.conf from within tmux by pressing `prefix + I` (Note that's a capital I, like "Install").

### Updating Plugins

`prefix + U` (capital U, like "Update") will fetch and apply the updates then refresh the conf.

### Uninstalling plugins

Remove or comment the plugin line from `tmux.conf` and then press `prefix + alt + u` (Note that's a lowercase u. Like "uninstall"). This will unregister the plugin, trash the plugin files and refresh the tmux.conf

### Manage plugins from the command line

Within the `tpm` folder is the `bin` folder containing 3 scripts:

- `install_plugins` - using `github-user/plugin` format.
- `update_plugins` - specify a specific plugin or `all` to update all.
- `clean_plugins` - Removes all plugins not on plugin list

