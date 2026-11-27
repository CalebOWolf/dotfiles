<div align="center">

# ⚙️ dotfiles

**My personal configuration files for Arch Linux.**

[![Arch Linux](https://img.shields.io/badge/Arch%20Linux-00ff7f?style=flat&logo=archlinux&logoColor=646464&label=OS&labelColor=000000)](https://archlinux.org)
[![Ghostty](https://img.shields.io/badge/Ghostty-202020?style=flat&logo=gnometerminal&logoColor=646464&label=Terminal&labelColor=000000)](https://ghostty.org)
[![btop](https://img.shields.io/badge/btop-202020?style=flat&logo=linux&logoColor=646464&label=Monitor&labelColor=000000)](https://github.com/aristocratos/btop)
[![Commits](https://img.shields.io/github/commit-activity/t/calebowolf/dotfiles?style=flat&logo=github&logoColor=646464&label=GitHub%20Commits&labelColor=202020&color=000000)](https://github.com/CalebOWolf/dotfiles/commits/main)

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
| Bell sound | Audio played by Ghostty's terminal bell | `~/Documents/Sounds/` |
| [btop](https://github.com/aristocratos/btop) | Resource monitor | `~/.config/btop/` |
| [fish](https://fishshell.com) | Default interactive shell | `~/.config/fish/` |
| [Bash](https://www.gnu.org/software/bash/) | Fallback shell | `~/.bashrc` |
| [Git](https://git-scm.com) | Git identity, LFS and credential helper | `~/.gitconfig` |
| [hyfetch](https://github.com/hykilpikonna/hyfetch) | Pride-flag system info (fastfetch backend) | `~/.config/hyfetch.json` |
| [pacman](https://wiki.archlinux.org/title/Pacman) | Package manager, extra repos, parallel downloads | `/etc/pacman.conf` |
| [makepkg](https://wiki.archlinux.org/title/Makepkg) | Package build settings | `/etc/makepkg.conf` |
| [mkinitcpio](https://wiki.archlinux.org/title/Mkinitcpio) | Initramfs hooks | `/etc/mkinitcpio.conf` |
| [KDE Plasma](https://kde.org/plasma-desktop/) | Aero theme, colors, fonts, panels, shortcuts, KWin effects | `~/.config/` (`kdeglobals`, `kwinrc`, …) |
| Wallpapers | Desktop and lock screen images used by Plasma | `~/Pictures/Wallpapers/` |
| Package lists | Explicitly installed repo and AUR packages | `packages/` |

## 📂 Structure

Each tool lives in its own folder that mirrors where its files go in `$HOME`.
System files live in `arch/`, and package lists in `packages/`:

```text
dotfiles/
├── ghostty/
│   └── .config/ghostty/config.ghostty
├── sounds/
│   └── Documents/Sounds/outlook.ogg
├── btop/
│   └── .config/btop/btop.conf
├── fish/
│   └── .config/fish/config.fish
├── bash/
│   └── .bashrc
├── git/
│   └── .gitconfig
├── hyfetch/
│   └── .config/hyfetch.json
├── kde/
│   └── .config/
│       ├── kdeglobals
│       ├── kwinrc
│       ├── kwinrulesrc
│       ├── kglobalshortcutsrc
│       ├── kscreenlockerrc
│       ├── plasmarc
│       ├── plasmashellrc
│       └── plasma-org.kde.plasma.desktop-appletsrc
├── wallpapers/
│   └── Pictures/Wallpapers/
├── arch/
│   └── etc/
│       ├── pacman.conf
│       ├── makepkg.conf
│       └── mkinitcpio.conf
├── packages/
│   ├── pkglist.txt
│   └── aurlist.txt
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
   stow ghostty sounds btop fish bash git hyfetch wallpapers
   ```

To remove a config's symlinks later, run `stow -D <name>`.

### KDE Plasma

Plasma rewrites its config files all the time, so copy these into place
instead of symlinking them (otherwise every tweak shows up as a change in the
repo). Log out of Plasma first, then run:

```bash
cp kde/.config/* ~/.config/
```

The Aero theme itself comes from the `aerothemeplasma-*` AUR packages in
`packages/aurlist.txt`; install those before copying. The desktop and lock
screen wallpapers come from the `wallpapers` package, so stow it first.

To save your current Plasma setup back into the repo:

```bash
cp ~/.config/{kdeglobals,kwinrc,kwinrulesrc,kglobalshortcutsrc,kscreenlockerrc,plasmarc,plasmashellrc,plasma-org.kde.plasma.desktop-appletsrc} kde/.config/
```

### System configs

The files in `arch/etc/` belong in `/etc` and are owned by root, so copy them
into place instead of symlinking. Compare them with your current files first:

```bash
diff /etc/pacman.conf arch/etc/pacman.conf
```

```bash
sudo cp arch/etc/pacman.conf arch/etc/makepkg.conf arch/etc/mkinitcpio.conf /etc/
```

After changing `mkinitcpio.conf`, rebuild the initramfs:

```bash
sudo mkinitcpio -P
```

### Packages

Reinstall the official repo packages:

```bash
sudo pacman -S --needed - < packages/pkglist.txt
```

Reinstall the AUR packages with [paru](https://github.com/Morganamilo/paru):

```bash
paru -S --needed - < packages/aurlist.txt
```

To refresh the lists after installing or removing packages:

```bash
pacman -Qqen > packages/pkglist.txt
```

```bash
pacman -Qqem > packages/aurlist.txt
```

## 🛠️ Customization

Feel free to fork this repo and adapt it to your own setup. Changes to the
files in `~/dotfiles` apply immediately, since the configs are symlinked
into place.

## 📜 License

Released under the [MIT License](LICENSE). Take whatever is useful to you.

---

<div align="center">

Made with ☕ on Arch, btw.

</div>
