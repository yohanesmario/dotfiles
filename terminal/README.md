# Terminal

## Dependencies
I'm using xterm and tmux because they support dotfiles and can be easily replicated across devices.
- XTerm >= 353
- Tmux >= 3.2

The font being used is  `Roboto Mono Regular` font.

## Custom Key Binding
You can setup custom keybinding for `Ctrl+Alt+T` to `xterm tmux`.

To get existing custom key bindings, run this on your terminal:
```sh
gsettings get org.gnome.settings-daemon.plugins.media-keys custom-keybindings
```
It should return something like this:
```sh
['/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/']
```

Add one more to the list:
```sh
gsettings set org.gnome.settings-daemon.plugins.media-keys custom-keybindings ['/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/xterm-tmux/']
```

In this case, `xterm-tmux` is our target. Then you can set the properties for `xterm-tmux`:
```sh
# Name:
gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/xterm-tmux/ name 'Terminal Emulator'

# Command:
gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/xterm-tmux/ command 'xterm tmux'

# Key Combination:
gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/xterm-tmux/ binding '<Primary><Alt>t'
```

## How to Apply
Run `apply` script.
