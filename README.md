# Helium Browser — Arch Linux Pacman Repository

Automated Arch Linux binary repository for **Helium Browser** (`helium-browser-bin`).  
Maintained with automated GitHub Actions tracking upstream releases from [imputnet/helium-linux](https://github.com/imputnet/helium-linux).

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

Whenever [imputnet/helium-linux](https://github.com/imputnet/helium-linux) releases a new stable version, a GitHub Actions workflow in this repository:
1. Downloads the official release binary.
2. Packages it into an Arch `.pkg.tar.zst` package.
3. Updates `custom-helium.db.tar.gz` and `custom-helium.files.tar.gz` using native `repo-add`.
4. Publishes it to the `repo` release.

Your system receives updates automatically whenever you run `sudo pacman -Syu`.
