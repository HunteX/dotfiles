# HunteX's Dotfiles

Personal dotfiles managed with [chezmoi](https://www.chezmoi.io/) for Arch Linux with Hyprland.

## What's Inside

- **Hyprland** - Wayland compositor configuration
- **Ax-Shell** - Custom configuration only (main app installed separately)
- **Matugen** - Material color generation
- **Zsh** - Shell configuration with Oh My Zsh and Starship
- **Oh My Zsh** - Custom plugins and themes
- **Kitty** - Terminal emulator configuration
- **Warp terminal** - Modern terminal with custom theme
- **Environment.d** - System environment variables (Wayland support)
- **Shell profiles** - .bash_profile, .profile for session setup
- **Wallpapers** - Arch Linux 4K wallpaper
- **Dunst** - Notification daemon configuration

## Prerequisites

Just install chezmoi - everything else will be installed automatically!

```bash
# Install chezmoi
sudo pacman -S git chezmoi
```

## Installation

### First Time Setup

```bash
# Initialize and apply dotfiles (will auto-install packages)
chezmoi init --apply https://github.com/HunteX/dotfiles.git

# Or step by step
chezmoi init https://github.com/HunteX/dotfiles.git
chezmoi apply  # This will run package installation script

# Install Ax-Shell
curl -fsSL get.axeni.de/ax-shell | bash
```

The first `chezmoi apply` will automatically:
- Install all required packages (Hyprland, kitty, fish, etc.)
- Install AUR packages (matugen, fabric-cli-git)
- Set up yay if not already installed

### Update Existing Installation

```bash
# Pull latest changes
chezmoi update

# Or manually
chezmoi git pull
chezmoi apply
```