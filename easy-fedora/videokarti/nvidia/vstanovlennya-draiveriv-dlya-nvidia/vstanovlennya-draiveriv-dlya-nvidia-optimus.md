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

## Дії по закінченні встановлення:

По закінченні встановлення необхідно переконатися, що модулі ядра були успішно зібрані та встановлені коректно.

```bash
sudo akmods --force
```

{% hint style="warning" %}
Якщо виникла помилка, то детальний журнал можна знайти в каталозі /var/cache/akmods/nvidia/
{% endhint %}

Тепер виріжемо з образу initrd драйвер nouveau та додамо NVIDIA:

```bash
sudo dracut --force
```

## При виникненні чорного екрану:

{% hint style="warning" %}
Якщо по закінченні встановлення та перезавантаження замість вікна входу в систему з'являється чорний екран, то в завантажувачі додамо через пробіл наступні параметри ядра:
{% endhint %}

```bash
rd.drivers.blacklist=nouveau nouveau.modeset=0
```

{% hint style="info" %}
Також необхідно обов'язково зайти в модуль налаштування UEFI комп'ютера або ноутбука і відключити UEFI Secure Boot (сама Fedora підтримує роботу з Secure Boot, однак модулі ядра пропрієтарного драйвера не мають цифрового підпису, тому не можуть бути завантажені в цьому режимі і, як наслідок, користувач побачить чорний екран), а також перевести його з режиму Windows Only в Other OS.
{% endhint %}

## Робота з NVIDIA Optimus

За замовчуванням буде використовуватися інтегроване рішення, але для запуску додатку з використанням дискретної відеокарти необхідно передавати особливі змінні середовища:

```bash
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia application [параметри запуску додатку]
```

Приклад запуску панелі управління NVIDIA для конфігурацій з Optimus:

```bash
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia nvidia-settings -c :8
```

Приклад запуску додатку app.exe через Wine на Optimus:

```bash
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia wine app.exe
```

## Видалення драйверів:

Якщо виникли якісь проблеми, або драйвери NVIDIA більше не потрібні, їх завжди можна видалити стандартним способом:

```bash
sudo dnf remove \*nvidia\*
```

По закінченні видалення необхідно обов'язково пересобрати образ initrd, щоб повернути в нього видалений при установці вільний драйвер nouveau:

```bash
sudo dracut --force
```
