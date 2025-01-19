# Встановлення драйверів для Nvidia

##

## Встановлення драйверів NVIDIA на Fedora 41

**1. Встановлення через RPM Fusion**

Щоб встановити драйвери NVIDIA за допомогою RPM Fusion, виконайте наступні кроки:

**Крок 1: Додайте репозиторії RPM Fusion**

Відкрийте термінал і виконайте наступні команди для додавання безкоштовного та небезкоштовного репозиторіїв RPM Fusion:

```bash
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

**Крок 2: Оновіть пакунки системи**

Оновіть пакунки вашої системи, щоб забезпечити сумісність із найновішими драйверами NVIDIA:

```bash
sudo dnf update
```

**Крок 3: Встановіть драйвери NVIDIA**

Встановіть драйвери NVIDIA та підтримку CUDA, виконавши наступну команду:

```bash
sudo dnf install akmod-nvidia
```

**Крок 4: Перезавантажте систему та перевірте встановлення**

Перезавантажте систему, щоб застосувати зміни:

```bash
sudo reboot
```

Після перезавантаження відкрийте термінал і виконайте наступну команду для перевірки встановлення:

```bash
nvidia-smi
```

Якщо команда відображає інформацію про ваш GPU NVIDIA, встановлення пройшло успішно.

## **2. Ручний метод встановлення**

Для досвідчених користувачів, які надають перевагу ручному встановленню, дотримуйтесь цих кроків:

**Крок 1: Підготуйте систему**

Встановіть необхідні пакети:

```bash
sudo dnf install kernel-devel kernel-headers gcc make dkms acpid libglvnd-glx libglvnd-opengl libglvnd-devel pkgconfig
```

**Крок 2: Завантажте драйвер NVIDIA**

Відвідайте [вебсайт NVIDIA](https://www.nvidia.com/Download/index.aspx) і завантажте відповідний драйвер для вашого GPU та версії Fedora. Збережіть файл у вашій домашній директорії.

**Крок 3: Вимкніть драйвер Nouveau**

Створіть файл із назвою blacklist-nouveau.conf у каталозі /etc/modprobe.d/ із таким вмістом:

```bash
blacklist nouveau
options nouveau modeset=0
```

Перегенеруйте initramfs ядра:

```bash
sudo dracut --force
```

**Крок 4: Встановіть драйвер NVIDIA**

Зробіть завантажений файл `.run` виконуваним і запустіть інсталятор:

```bash
chmod +x NVIDIA-Linux-x86_64-xxx.xx.run
sudo ./NVIDIA-Linux-x86_64-xxx.xx.run
```

Дотримуйтесь інструкцій на екрані, щоб завершити процес встановлення.

**Крок 5: Перезавантажте систему та перевірте встановлення**

Перезавантажте систему та перевірте встановлення за допомогою команди `nvidia-smi`, як зазначено у методі RPM Fusion.
