# Ax-Shell Configuration

This directory contains only the custom configuration for [Ax-Shell](https://github.com/Axenide/Ax-Shell).

The main Ax-Shell application should be installed separately.

## Structure

Only the `config/` directory is tracked in dotfiles:
- `config/` - Custom Ax-Shell configuration
  - `hypr/` - Hyprland integration configs (ax-shell.conf, colors.conf, hypridle, hyprlock)
  - `matugen/` - Color generation templates
  - `config.json` - Main Ax-Shell settings
  - `cavalcade/` - Cava visualizer config

## Installation

### Quick Install (Recommended)

```bash
# Install Ax-Shell with all dependencies
curl -fsSL get.axeni.de/ax-shell | bash
```

### Manual Installation

```bash
# Install dependencies
sudo pacman -S python python-gobject gtk3 gtk4

# Install Fabric (Ax-Shell framework)
yay -S fabric-cli-git python-fabric-git

# Clone Ax-Shell
git clone https://github.com/Axenide/Ax-Shell.git ~/.config/Ax-Shell

# Apply your custom config via dotfiles
chezmoi apply
```

The `config/` directory from dotfiles will overlay the Ax-Shell installation, applying your customizations.

## What's Customized

- **Hyprland Integration**: Custom keybindings, colors, idle/lock configs
- **Matugen Templates**: Material Design color generation
- **Personal Settings**: Your config.json preferences

## Updating

When updating Ax-Shell:
```bash
cd ~/.config/Ax-Shell
git pull
# Your config/ will be preserved by chezmoi
```
