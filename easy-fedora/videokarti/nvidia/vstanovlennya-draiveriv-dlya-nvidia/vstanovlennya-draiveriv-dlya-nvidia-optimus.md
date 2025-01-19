---
description: Гібридна графіка на Fedora Linux.
---

# Встановлення драйверів для NVIDIA Optimus

{% hint style="info" %}
Починаючи з Fedora 31 та версії пропрієтарного драйвера 435.xx, технологія NVIDIA Optimus, що використовується в ноутбуках з гібридною графікою, повністю підтримується «з коробки». На жаль, старі покоління відеокарт (менше серії 700) не підтримуються, тому працювати не будуть.
{% endhint %}

**Підключимо репозиторії RPM Fusion.**

```bash
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

Встановимо стандартний драйвер NVIDIA для сучасних відеокарт.

```bash
sudo dnf install gcc kernel-headers kernel-devel akmod-nvidia xorg-x11-drv-nvidia xorg-x11-drv-nvidia-libs
```

Якщо використовується 64-бітна ОС, але потрібно запускати також Steam та 32-бітні версії ігор, то встановимо також 32-бітний драйвер (встановлювати відразу після попередніх).

```bash
sudo dnf install xorg-x11-drv-nvidia-libs.i686
```
