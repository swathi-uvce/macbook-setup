# 💻 MacBook Setup - Beautiful Terminal Experience

> Transform your boring MacBook terminal into a beautiful, powerful, and productive command-line interface using **iTerm2** + **Oh My Zsh**

![Final Result](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/14.png)

---

## 📋 Table of Contents

- [Prerequisites](#-prerequisites)
- [Installation Overview](#-installation-overview)
- [Step 1: Install iTerm2](#1️⃣-install-iterm2)
- [Step 2: Install Oh My Zsh](#2️⃣-install-oh-my-zsh)
- [Step 3: Install Powerline](#3️⃣-install-powerline)
- [Step 4: Install PowerFonts](#4️⃣-install-powerfonts)
- [Step 5: Install Color Scheme](#5️⃣-install-solarized-color-scheme)
- [Step 6: Install Theme](#6️⃣-install-agnoster-theme)
- [Step 7: Install Syntax Highlighting](#7️⃣-install-syntax-highlighting-plugin)
- [Step 8: Install Auto-suggestions](#8️⃣-install-auto-suggestions-plugin-optional)
- [Final Configuration](#-final-configuration)
- [Troubleshooting](#-troubleshooting)

---

## 🔧 Prerequisites

Before starting, ensure you have:

- **macOS** (tested on Monterey, Ventura, Sonoma, Sequoia)
- **Xcode Command Line Tools**
  ```bash
  xcode-select --install
  ```

- **Git**
  ```bash
  # Check if installed
  git --version
  
  # Or download from https://git-scm.com
  ```

---

## 🗺️ Installation Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                    🍎 MACBOOK SETUP FLOW                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   Prerequisites → iTerm2 → Oh My Zsh → Powerline → Fonts        │
│                                    ↓                            │
│                         Colors → Theme → Plugins → ✅ Done!      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

| Component | Purpose |
|-----------|---------|
| iTerm2 | Better terminal emulator for macOS |
| Oh My Zsh | Zsh configuration framework |
| Powerline | Status line dependency |
| PowerFonts | Special characters support |
| Solarized | Eye-friendly color scheme |
| Agnoster | Beautiful prompt theme |
| Plugins | Syntax highlighting & auto-complete |

---

## 1️⃣ Install iTerm2

1. Download from [https://www.iterm2.com/](https://www.iterm2.com/)
2. Drag to Applications folder
3. Open iTerm2
4. Set Zsh as default shell:

```bash
chsh -s /bin/zsh
```

> 💡 To revert to bash: `chsh -s /bin/bash`

---

## 2️⃣ Install Oh My Zsh

Choose one method:

```bash
# Using curl (recommended)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

```bash
# Using wget
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

---

## 3️⃣ Install Powerline

```bash
# Install pip if not available
sudo easy_install pip

# Install powerline
pip install powerline-status --user
```

---

## 4️⃣ Install PowerFonts

```bash
# Create a directory for open source projects
mkdir -p ~/OpenSource && cd ~/OpenSource

# Clone and install fonts
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts
./install.sh
```

### Configure Font in iTerm2:
```
iTerm2 → Preferences (⌘,) → Profiles → Text → Font → Change Font → Meslo LG M
```

---

## 5️⃣ Install Solarized Color Scheme

```bash
cd ~/OpenSource
git clone https://github.com/altercation/solarized
cd solarized/iterm2-colors-solarized/
open .
```

Double-click both `.itermcolors` files to install, then:
```
iTerm2 → Preferences (⌘,) → Profiles → Colors → Color Presets → Solarized Dark
```

---

## 6️⃣ Install Agnoster Theme

```bash
cd ~/OpenSource
git clone https://github.com/fcamblor/oh-my-zsh-agnoster-fcamblor.git
cd oh-my-zsh-agnoster-fcamblor/
./install
```

Edit `~/.zshrc`:
```bash
vi ~/.zshrc
```

Change the theme line to:
```bash
ZSH_THEME="agnoster"
```

Save and exit: Press `Esc`, type `:wq`, press `Enter`

---

## 7️⃣ Install Syntax Highlighting Plugin

```bash
cd ~/.oh-my-zsh/custom/plugins/
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
```

Edit `~/.zshrc` and update plugins:
```bash
plugins=(git zsh-syntax-highlighting)
```

Add at the **end** of `~/.zshrc`:
```bash
source ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

> ⚠️ **Important:** `zsh-syntax-highlighting` must be the LAST plugin!

---

## 8️⃣ Install Auto-suggestions Plugin (Optional)

```bash
cd ~/.oh-my-zsh/custom/plugins/
git clone https://github.com/zsh-users/zsh-autosuggestions
```

Update plugins in `~/.zshrc`:
```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

---

## 📝 Final Configuration

Your `~/.zshrc` should look like this:

```bash
# Path to Oh My Zsh installation
export ZSH="$HOME/.oh-my-zsh"

# Theme
ZSH_THEME="agnoster"

# Plugins (zsh-syntax-highlighting MUST be last)
plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
)

# Source Oh My Zsh
source $ZSH/oh-my-zsh.sh

# Source syntax highlighting
source ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

Apply changes:
```bash
source ~/.zshrc
```

---

## 🎨 Optional Customizations

### Custom Background Image
```
iTerm2 → Preferences (⌘,) → Profiles → Window → Background Image → Select Image
```

### Adjust Auto-suggestion Color
```
iTerm2 → Preferences (⌘,) → Profiles → Colors → ANSI Colors → Bright (first box)
```

### Hide Username in Prompt
Add to `~/.zshrc`:
```bash
DEFAULT_USER=$(whoami)
```

---

## 🔍 Troubleshooting

| Issue | Solution |
|-------|----------|
| Strange characters (□ or ?) | Install PowerFonts and set font to "Meslo LG" |
| `pip: command not found` | Run `sudo easy_install pip` or `brew install python` |
| `git: command not found` | Install Xcode CLI: `xcode-select --install` |
| Auto-suggestions too dim | Adjust in Preferences → Colors → ANSI Colors → Bright |
| Changes not applying | Run `source ~/.zshrc` or restart iTerm2 (⌘Q, reopen) |
| Permission denied | Run with `sudo` or check file permissions |

---

## ✅ What You Get

| Feature | Description |
|---------|-------------|
| ✨ Beautiful Prompt | Shows user, directory, git branch & status |
| 🎨 Syntax Highlighting | Commands colored for easy reading |
| 💡 Auto-suggestions | History-based command completion |
| 🌈 Solarized Colors | Eye-friendly color scheme |
| ⚡ Special Icons | Git status indicators, arrows, symbols |
| 🖼️ Custom Background | Optional wallpaper support |

---

## 🚀 Quick Install Script

For experienced users, here's a one-shot script:

```bash
#!/bin/bash
# macbook-setup.sh - Quick terminal beautification

# Install Oh My Zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" "" --unattended

# Install plugins
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# Install fonts
cd /tmp
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts && ./install.sh
cd .. && rm -rf fonts

echo "✅ Done! Now:"
echo "1. Set ZSH_THEME=\"agnoster\" in ~/.zshrc"
echo "2. Add plugins: plugins=(git zsh-autosuggestions zsh-syntax-highlighting)"
echo "3. Set iTerm2 font to 'Meslo LG M for Powerline'"
echo "4. Run: source ~/.zshrc"
```

---

## 📚 Credits & References

- Original guide: [sirius1024/iterm2-with-oh-my-zsh](https://github.com/sirius1024/iterm2-with-oh-my-zsh)
- [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh)
- [iTerm2](https://iterm2.com/)
- [Powerline Fonts](https://github.com/powerline/fonts)
- [Solarized](https://github.com/altercation/solarized)
- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)

---

## 📄 License

MIT License - Feel free to use and modify!

---

<p align="center">
  Made with ❤️ for MacBook users
</p>
