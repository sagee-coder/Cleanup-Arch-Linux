# Pacman Cache Cleanup (Arch Linux)

This document explains how to safely clean disk space used by Pacman’s package cache on Arch Linux and Arch-based distributions.

Pacman stores downloaded packages in:

/var/cache/pacman/pkg

Over time, this directory can grow very large because Pacman does not automatically remove old package versions.

---

## Why the Cache Gets Large

Pacman keeps cached packages for:
- Reinstalling packages without re-downloading
- Downgrading packages if an update breaks something
- Faster local installs

This behavior is intentional, but manual cleanup is required.

---

## Commands Used for Cleanup

### 1. Remove Cached Packages That Are No Longer Installed

sudo pacman -Sc

This removes cached packages that are no longer installed while keeping current ones.

---

### 2. Install Cleanup Utilities

sudo pacman -S pacman-contrib

This installs paccache, the recommended tool for managing the Pacman cache.

---

### 3. Remove Old Versions of Installed Packages

sudo paccache -r

This keeps only the latest version of each installed package and removes older versions.

---

## Verify Disk Usage After Cleanup

du -sh /var/cache/pacman/pkg

Typical size after cleanup:
- 500MB–2GB is normal
- Larger sizes indicate frequent updates or large packages

---

## Notes

- Do not manually delete files in /var/cache/pacman/pkg
- Avoid pacman -Scc unless disk space is critically low
- Cache will grow again unless cleanup is automated

---

## Tested On

- Arch Linux
- Arch-based distributions (Manjaro, EndeavourOS)

---



output_path
