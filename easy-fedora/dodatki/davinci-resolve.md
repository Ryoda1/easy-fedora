---
description: Найкращий відеоредактор. (Для досвідчених користувачів)
---

# DaVinci Resolve

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

## Автоматичний Метод встановлення DaVinci

```bash
sudo dnf copr enable -y herzen/davinci-helper
sudo dnf install -y davinci-helper
```

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

## Ручний метод встановлення DaVinci

{% hint style="danger" %}
Цей метод може не працювати.
{% endhint %}

[Davinci Fix](davinci-resolve.md#fix-fedora-39-dlya-davinci-resolve-18.6-1) для Fedora 41

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

{% embed url="https://www.blackmagicdesign.com/products/davinciresolve" %}

Розпаковуємо скачаний архів

```bash
cd ~/Downloads
unzip DaVinci_Resolve_XX.Y.Z_Linux.zip
```

Встановлюємо DaVinci Resolve.

```bash
./DaVinci_Resolve_XX.Y.Z_Linux.zip
```

{% hint style="info" %}
Для хлопців з відеокартами від NVIDIA на цьому все. Приємного творчого процесу!
{% endhint %}

## ДЛЯ ВІДЕОКАРТ AMD RADEON

### Доінсталюємо цей пакет:

```bash
sudo dnf install rocm-opencl
```

{% hint style="info" %}
Тепер все і для табору 'червоних'! Приємного творчого процесу!
{% endhint %}

### Перевіряємо, чи все працює утилітою clinfo

```bash
sudo dnf install clinfo
```

```bash
Number of platforms                               1
  Platform Name                                   AMD Accelerated Parallel Processing
  Platform Vendor                                 Advanced Micro Devices, Inc.
  Platform Version                                OpenCL 2.1 AMD-APP (3452.0)
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_icd cl_amd_event_callback 
  Platform Extensions function suffix             AMD
  Platform Host timer resolution                  1ns

  Platform Name                                   AMD Accelerated Parallel Processing
Number of devices                                 1
  Device Name                                     gfx1010:xnack-
  Device Vendor                                   Advanced Micro Devices, Inc.
  Device Vendor ID                                0x1002
  Device Version                                  OpenCL 2.0 
  Driver Version                                  3452.0 (HSA1.1,LC)
  Device OpenCL C Version                         OpenCL C 2.0 
  Device Type                                     GPU
  Device Board Name (AMD)                         AMD Radeon RX 5700 XT
  Device PCI-e ID (AMD)                           0x731f
  Device Topology (AMD)                           PCI-E, 0000:0c:00.0
  Device Profile                                  FULL_PROFILE

................
```

## Fix Fedora 41 для Davinci Resolve <a href="#fix-fedora-39-dlya-davinci-resolve-18.6-1" id="fix-fedora-39-dlya-davinci-resolve-18.6-1"></a>

{% embed url="https://github.com/H3rz3n/Davinci-Resolve-Fedora-38-39-40-Fix" %}

Підготовка Fedora 41 перед установкою DaVinci

```bash
sudo dnf install libxcrypt-compat libcurl libcurl-devel mesa-libGLU
```

Далі робимо установку для [ВІДЕОКАРТ AMD](davinci-resolve.md#dlya-videokart-amd-radeon)

Виконуємо команди після завершення установки DaVinci Resolve

```bash
cd /opt/resolve/libs
sudo mkdir disabled-libraries
sudo mv libglib* disabled-libraries
sudo mv libgio* disabled-libraries
sudo mv libgmodule* disabled-libraries
```
