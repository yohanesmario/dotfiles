# Terminal

## Dependencies
I'm using xterm and tmux because they support dotfiles and can be easily replicated across devices. For ubuntu, they are available in the ubuntu repository.
```sh
sudo apt install xterm x11-xserver-utils tmux
```

The font being used is  `Roboto Mono Regular` font.

The `apply` script should have handled this for you.

## Custom Key Binding
You can setup custom keybinding for `Ctrl+Alt+T` to `xterm tmux`. The `apply` script will ask you if you want to apply this. Here's the steps if you want to apply it on your own.

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
