<div align="center">

# ⚙️ dotfiles

**My personal configuration files for Arch Linux.**

[![Arch Linux](https://img.shields.io/badge/Arch%20Linux-1793D1?style=for-the-badge&logo=archlinux&logoColor=white)](https://archlinux.org)
[![Ghostty](https://img.shields.io/badge/Ghostty-2D2D2D?style=for-the-badge&logo=gnometerminal&logoColor=white)](https://ghostty.org)
[![btop](https://img.shields.io/badge/btop-4C4C4C?style=for-the-badge&logo=linux&logoColor=white)](https://github.com/aristocratos/btop)

</div>

---

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
