---
description: Месенджер
---

# Telegram

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

```bash
flatpak install flathub org.telegram.desktop
```

## У версії Flatpak курсор більший, ніж системний

```bash
sudo flatpak override --env=XCURSOR_SIZE=12 org.telegram.desktop
```

## Якщо Flatpak Telegram не використовує встановлену тему для курсора миші.

```bash
flatpak --user override --filesystem=/home/$USER/.icons/:ro org.telegram.desktop
flatpak --user override --filesystem=/usr/share/icons/:ro org.telegram.desktop
```
