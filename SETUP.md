# Quick Setup Guide

## Что было сделано

Dotfiles репозиторий успешно настроен с помощью chezmoi для вашего Arch Linux с Hyprland.

## Структура репозитория

```
~/p/github.com/HunteX/dotfiles/
├── README.md              # Основная документация
├── .chezmoiignore         # Файлы для игнорирования
├── .gitignore             # Git ignore правила
├── dot_config/            # ~/.config/
│   ├── hypr/              # Конфигурация Hyprland
│   ├── Ax-Shell/          # Ax-Shell desktop environment
│   ├── matugen/           # Генерация цветовых схем
│   ├── fish/              # Fish shell
│   ├── kitty/             # Kitty terminal
│   └── warp/              # Warp terminal
├── dot_local/             # ~/.local/
│   └── share/warp-terminal/themes/
└── dot_zshrc              # ~/.zshrc
```

## Что добавлено

- ✅ Hyprland (hyprland.conf, hypridle.conf, hyprlock.conf)
- ✅ Ax-Shell (полная конфигурация)
- ✅ Matugen (генерация Material цветов)
- ✅ Zsh с Starship prompt
- ✅ Fish shell
- ✅ Kitty terminal
- ✅ Warp terminal с кастомной темой
- ✅ Dunst уведомления

## Следующие шаги

### 1. Настройка удаленного репозитория

```bash
cd ~/p/github.com/HunteX/dotfiles

# Добавить remote (если еще не добавлен)
git remote add origin https://github.com/HunteX/dotfiles.git

# Или через SSH
git remote add origin git@github.com:HunteX/dotfiles.git

# Отправить на GitHub
git push -u origin main
```

### 2. Глобальная настройка git (если нужно)

```bash
git config --global user.name "HunteX"
git config --global user.email "huntex@yandex.ru"
```

### 3. Проверка chezmoi

```bash
# Проверить статус
chezmoi status

# Посмотреть разницу
chezmoi diff

# Применить изменения (если нужно)
chezmoi apply
```

### 4. Внесение изменений в будущем

```bash
# Отредактировать файл
vim ~/.config/hypr/hyprland.conf

# Добавить в chezmoi
chezmoi add ~/.config/hypr/hyprland.conf

# Или использовать chezmoi edit
chezmoi edit ~/.config/hypr/hyprland.conf

# Закоммитить
cd ~/.local/share/chezmoi
git add .
git commit -m "Update hyprland config"
git push
```

### 5. Установка на новую систему

```bash
# 1. Установить chezmoi
sudo pacman -S chezmoi

# 2. Применить dotfiles (автоматически установит все пакеты!)
chezmoi init --apply https://github.com/HunteX/dotfiles.git

# 3. Установить Ax-Shell
curl -fsSL get.axeni.de/ax-shell | bash

# Готово! Все пакеты установлены, конфигурация применена
```

**Что происходит автоматически:**
- ✅ Устанавливается Hyprland и все компоненты
- ✅ Устанавливаются терминалы (kitty), shell (fish, starship)
- ✅ Устанавливаются AUR пакеты через yay (matugen, fabric)
- ✅ Применяются все конфигурационные файлы

## Важные замечания

1. **Symlink**: Репозиторий связан с `~/.local/share/chezmoi` через symlink
2. **Ax-Shell**: .git репозиторий Ax-Shell игнорируется в .chezmoiignore
3. **Python cache**: __pycache__ директории игнорируются
4. **Fish variables**: fish_variables игнорируется (генерируется автоматически)

## Файлы для исключения

Следующие файлы автоматически игнорируются (см. `.chezmoiignore`):
- Python cache (__pycache__, *.pyc)
- Backup файлы (*.bak, *.backup)
- Log файлы (*.log)
- Ax-Shell cache
- Fish shell generated files
- Oh My Zsh .git

## Полезные команды

```bash
# Обновить dotfiles из репозитория
chezmoi update

# Посмотреть, что изменится
chezmoi diff

# Применить изменения
chezmoi apply -v

# Re-init chezmoi
chezmoi init --source ~/p/github.com/HunteX/dotfiles

# Проверить управляемые файлы
chezmoi managed
```

## Troubleshooting

### Если chezmoi потерял связь с репозиторием

```bash
rm -rf ~/.local/share/chezmoi
ln -s ~/p/github.com/HunteX/dotfiles ~/.local/share/chezmoi
```

### Если нужно игнорировать дополнительные файлы

Отредактируйте `.chezmoiignore` в корне репозитория.
