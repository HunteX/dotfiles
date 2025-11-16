# HunteX's Dotfiles

Personal dotfiles managed with [chezmoi](https://www.chezmoi.io/) for Arch Linux with Hyprland.

## What's Inside

- **Hyprland** - Wayland compositor configuration
- **Ax-Shell** - Custom configuration only (main app installed separately)
- **Matugen** - Material color generation
- **Zsh** - Shell configuration with Oh My Zsh and Starship
- **Oh My Zsh** - Custom plugins and themes
- **Fish** - Alternative shell setup
- **Kitty** - Terminal emulator configuration
- **Warp** - Modern terminal with custom theme
- **Environment.d** - System environment variables (Wayland support)
- **Shell profiles** - .bash_profile, .profile for session setup
- **Wallpapers** - Arch Linux 4K wallpaper
- **Dunst** - Notification daemon configuration

## Prerequisites

Just install chezmoi - everything else will be installed automatically!

```bash
# Install chezmoi
sudo pacman -S chezmoi
```

Packages that will be auto-installed:
- **Hyprland ecosystem**: hyprland, hypridle, hyprlock, hyprpicker, hyprshot
- **Terminals**: kitty
- **Shell**: fish, starship, zsh
- **Utilities**: wofi, dunst, matugen-bin
- **Development**: python, python-gobject, gtk3, gtk4
- **Fonts**: ttf-hack-nerd
- **Ax-Shell deps**: fabric-cli-git, python-fabric-git

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

## Configuration Structure

```
~/.config/
├── hypr/               # Hyprland configuration
│   ├── hyprland.conf   # Main Hyprland config
│   ├── hypridle.conf   # Idle daemon config
│   └── hyprlock.conf   # Lock screen config
├── Ax-Shell/           # Ax-Shell custom config only
│   ├── README.md       # Installation instructions
│   └── config/
│       ├── config.json
│       ├── hypr/       # Ax-Shell Hyprland integration
│       └── matugen/    # Color templates
├── matugen/            # Material color generation
│   └── config.toml
├── environment.d/      # Environment variables
│   └── 10-custom.conf  # Wayland/Electron settings
├── fish/               # Fish shell config
├── kitty/              # Kitty terminal
├── warp/               # Warp terminal settings
└── warp-terminal/      # Warp terminal config
~/.oh-my-zsh/
└── custom/             # Oh My Zsh custom plugins/themes
~/.local/share/
└── warp-terminal/
    └── themes/         # Warp custom themes
~/
├── .zshrc              # Zsh configuration
├── .bashrc             # Bash configuration
├── .bash_profile       # Bash profile
├── .profile            # Shell profile
└── Images/             # Wallpapers and images
    └── arch-linux-wallpaper-4k.png
```

## Key Features

### Hyprland Setup
- Custom keybindings (SUPER as main modifier)
- Dual keyboard layout (US/RU with Alt+Space toggle)
- Smooth animations with custom bezier curves
- Media keys support
- Integration with Ax-Shell

### Ax-Shell
- Material Design based desktop environment
- Dynamic color theming with matugen
- Custom widgets and modules
- Wayland native

## Making Changes

```bash
# Edit files in your home directory normally
vim ~/.config/hypr/hyprland.conf

# Add changes to chezmoi
chezmoi add ~/.config/hypr/hyprland.conf

# Or use chezmoi edit
chezmoi edit ~/.config/hypr/hyprland.conf

# Commit and push changes
cd ~/.local/share/chezmoi
git add .
git commit -m "Update Hyprland config"
git push
```

## Customization

### Colors (Matugen)
Matugen automatically generates color schemes from wallpapers. Configuration is in `~/.config/matugen/config.toml`.

### Hyprland
Main configuration: `~/.config/hypr/hyprland.conf`
Ax-Shell integration: `~/.config/Ax-Shell/config/hypr/ax-shell.conf`

### Shell
- Zsh config: `~/.zshrc`
- Fish config: `~/.config/fish/config.fish`

## Troubleshooting

### Chezmoi not finding dotfiles
```bash
# Reinitialize with correct source
chezmoi init --source ~/p/github.com/HunteX/dotfiles
```

### Hyprland not loading Ax-Shell
Check the source line at the end of `~/.config/hypr/hyprland.conf`:
```conf
source = ~/.config/Ax-Shell/config/hypr/ax-shell.conf
```

## License

Personal dotfiles - feel free to use as inspiration for your own setup!

## Credits

- [Hyprland](https://hyprland.org/)
- [Ax-Shell](https://github.com/Axenide/Ax-Shell)
- [chezmoi](https://www.chezmoi.io/)
- [Matugen](https://github.com/InioX/matugen)
