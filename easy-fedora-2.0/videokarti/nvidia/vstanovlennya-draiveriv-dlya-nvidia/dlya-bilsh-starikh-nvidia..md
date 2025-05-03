---
description: Встановлення драйверів для відеокарт Nvidia версій 340 та 390.
---

# Для більш "старих" Nvidia.

{% hint style="danger" %}
Після встановлення цих драйверів сесія Wayland буде недоступна!
{% endhint %}

{% hint style="warning" %}
Про 3D-ускорення графіки в таких проектах, як Wine, Proton та Bottles, на жаль, можна забути.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-01-19 at 21-36-51 Для более старых Nvidia Fedora Zero (1).png" alt=""><figcaption></figcaption></figure>

## Підключаємо репозиторій RPM Fusion

```bash
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
```

```bash
sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

## Встановлення драйвера версії 390

{% hint style="info" %}
Для відеокарт GeForce серії 400/500 та частково 600 серії
{% endhint %}

```bash
sudo dnf install xorg-x11-drv-nvidia-390xx akmod-nvidia-390xx
```

{% hint style="success" %}
Перезавантажуємо ПК
{% endhint %}

## Встановлення драйвера версії 340

{% hint style="info" %}
Для відеокарт GeForce серій 8/9/200/300
{% endhint %}

```bash
sudo dnf install xorg-x11-drv-nvidia-340xx akmod-nvidia-340xx
```

{% hint style="success" %}
Перезавантажуємо ПК
{% endhint %}
