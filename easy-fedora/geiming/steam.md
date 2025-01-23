---
description: Найкрутіша ігрова платформа для Linux.
---

# Steam

<figure><img src="../../.gitbook/assets/obraz (13).png" alt=""><figcaption></figcaption></figure>

## Встановлення:

### RPM Fusion

<pre class="language-bash"><code class="lang-bash">sudo dnf config-manager setopt fedora-cisco-openh264.enabled=1
<strong>sudo dnf install steam -y
</strong></code></pre>

## Flatpak

```bash
flatpak install flathub com.valvesoftware.Steam
```

## Увімкнення Proton (Steam Play) для запуску ігор на Linux:

<figure><img src="../../.gitbook/assets/obraz.png" alt=""><figcaption><p>Steam Play увімкне Proton.</p></figcaption></figure>

## Мій диск не видно у Steam із Flatpak

Додаємо шлях до нашого диска/каталогу в утиліті Flatseal:

```bash
flatpak install flathub com.github.tchx84.Flatseal
```

<figure><img src="../../.gitbook/assets/obraz (21).png" alt=""><figcaption></figcaption></figure>

