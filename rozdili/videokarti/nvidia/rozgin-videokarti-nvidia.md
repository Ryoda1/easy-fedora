---
description: Включаємо розгін Nvidia на Linux
---

# Розгін відеокарти NVIDIA

{% hint style="danger" %}
Все в даному розділі ви робите на свій страх і ризик! Будьте уважні!
{% endhint %}

```bash
sudo mkdir /etc/X11/xorg.conf.d/

sudo gnome-text-editor /etc/X11/xorg.conf.d/20-nvidia.conf
```

Далі додаємо в файл:

```bash
Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "НАЗВА ВАШОЇ ВІДЕОКАРТИ"

#если у вас уже есть настройки в файле, достаточно добавить два пункта ниже.

Option "RegistryDwords" "PerfLevelSrc=0x2222"
Option "TripleBuffer" "True"
Option "Coolbits" "28"
EndSection
Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "Stereo" "0"
Option "nvidiaXineramaInfoOrder" "DFP-0"

#если у вас уже есть настройки в файле, достаточно добавить пункт ниже.

Option "metamodes" "nvidia-auto-select +0+0 { ForceFullCompositionPipeline = On }"
Option "SLI" "Off"
Option "MultiGPU" "Off"
Option "BaseMosaic" "off"
SubSection "Display"
Depth 24
EndSubSection
EndSection
```

{% hint style="info" %}
Редагуємо BoardName "НАЗВА ВАШОЇ ВІДЕОКАРТИ"
{% endhint %}

{% hint style="success" %}
Зберігаємо CTRL+O, ENTER, CTRL+X
{% endhint %}
