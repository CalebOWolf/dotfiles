# ⚙️ Dotfiles

[![OS](https://img.shields.io/badge/Arch%20Linux-202020?style=flat&logo=archlinux&logoColor=646464&label=OS&labelColor=202020)](https://archlinux.org)
[![Terminal](https://img.shields.io/badge/Ghostty-202020?style=flat&logo=gnometerminal&logoColor=646464&label=Terminal&labelColor=202020)](https://ghostty.org)
[![Commits](https://img.shields.io/github/commit-activity/t/calebowolf/dotfiles?logo=github&logoColor=646464&label=GitHub%20Commits&labelColor=202020&color=000000)](https://github.com/CalebOWolf/dotfiles/commits/main)
[![Discord](https://img.shields.io/badge/calebowolf-discord?style=flat&logo=discord&label=Discord&labelColor=000000&color=00ff7f)](https://discord.com/users/202196441593020416)

> *My personal configuration files for Arch Linux* 🐧

## 📖 Overview

This repository holds the configs I use day to day on my Arch Linux setup.
It's version-controlled so I can rebuild my environment quickly on a new
machine and keep my settings in sync across devices.

## 🧰 What's Included

| Tool | Description | Config Location |
| ---- | ----------- | --------------- |
| [Ghostty](https://ghostty.org) | GPU-accelerated terminal emulator | `~/.config/ghostty/` |
| [btop](https://github.com/aristocratos/btop) | Resource monitor | `~/.config/btop/` |
| *More coming soon* | — | — |

## 📂 Structure

Each tool lives in its own folder that mirrors where its files go in `$HOME`:

```text
dotfiles/
├── ghostty/
│   └── .config/ghostty/config
├── btop/
│   └── .config/btop/btop.conf
└── README.md
```

## 🚀 Installation

> [!WARNING]
> These are my personal settings. Read through them before applying, and back
> up your existing configs first.

### Prerequisites

- [Arch Linux](https://archlinux.org) (or an Arch-based distro)
- [`git`](https://git-scm.com) and [GNU Stow](https://www.gnu.org/software/stow/)

```bash
sudo pacman -S git stow
```

### Setup

1. Clone the repository into your home directory:

   ```bash
   git clone https://github.com/CalebOWolf/dotfiles.git ~/dotfiles
   ```

2. Move into it:

   ```bash
   cd ~/dotfiles
   ```

3. Symlink the configs you want with Stow:

   ```bash
   stow ghostty btop
   ```

To remove a config's symlinks later, run `stow -D <name>`.

## 🛠️ Customization

Feel free to fork this repo and adapt it to your own setup. Changes to the
files in `~/dotfiles` apply immediately, since the configs are symlinked
into place.

## 📜 License

Free to use and modify. Take whatever is useful to you.

---

<div align="center">

Made with ☕ on Arch, btw.

</div>
