---
description: Запускаємо додатки та ігри Windows через Wine/Proton
---

# PortProton

**PortProton** — це проєкт, розроблений для спрощення запуску ігор Windows на Linux як для новачків, так і для досвідчених користувачів. Його мета — зробити процес запуску ігор (та іншого програмного забезпечення) максимально простим, одночасно надаючи гнучкі налаштування для просунутих користувачів.

PortProton базується на версії WINE від Valve (Proton) та її модифікаціях (Proton GE). У нього входять набір скриптів у поєднанні з самим WINE-Proton, контейнер Steam Runtime Sniper, а також портовані версії MANGOHUD (виведення корисної інформації у вікні гри: FPS, FrameTime, завантаження CPU, GPU тощо) і vkBasalt (покращення графіки в іграх, особливо ефективне у поєднанні з FSR, DLSS). Крім того, у проєкті передбачено багато готових оптимізацій для досягнення максимальної продуктивності.

Реалізовано функцію автоматичної установки в один клік (на вкладці **Автоустановка**) популярних ігрових лаунчерів, таких як WGC, Epic Games, Battle.net, Origin, EVE Online, Rockstar, Ubisoft Connect, League of Legends та багато інших.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Встановлення **PortProton** на Fedora Linux.

### Fedora-corp

```bash
sudo dnf copr enable boria138/portproton

sudo dnf install portproton
```

### Flatpak

```bash
flatpak install flathub ru.linux_gaming.PortProton
```
