# Helium Browser — Arch Linux Pacman Repository

Automated Arch Linux binary repository for **Helium Browser** (`helium-browser-bin`), directly mirroring and building upstream [aur.archlinux.org/packages/helium-browser-bin](https://aur.archlinux.org/packages/helium-browser-bin).  
Maintained with automated GitHub Actions running official Arch Linux `makepkg`.

---

## How to Enable in Pacman

Add the following to your `/etc/pacman.conf`:

```ini
[custom-helium]
SigLevel = Optional TrustAll
Server = https://github.com/Aditya-233/helium/releases/download/repo
```

Then update pacman databases and install:

```bash
sudo pacman -Syu
sudo pacman -S helium-browser-bin
```

---

## Automated Updates

Whenever [aur.archlinux.org/packages/helium-browser-bin](https://aur.archlinux.org/packages/helium-browser-bin) updates:
1. GitHub Actions automatically syncs the exact AUR files (`PKGBUILD`, patches, `LICENSE`, `.SRCINFO`).
2. Builds the official package using `makepkg` inside an Arch Linux container (with PGP and checksum verification).
3. Updates the Pacman repository database (`custom-helium.db.tar.gz`) with `repo-add`.
4. Publishes it to the `repo` release.

Your system receives official AUR-identical binary updates automatically whenever you run `sudo pacman -Syu`.
