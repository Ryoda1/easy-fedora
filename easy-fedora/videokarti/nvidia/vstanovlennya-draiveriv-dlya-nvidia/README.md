# Встановлення драйверів для Nvidia

{% hint style="info" %}
У Fedora Linux 35 репозиторій із драйверами Nvidia тепер увімкнений за замовчуванням, якщо під час початкового налаштування системи поставити галочку на активацію стороннього репозиторію.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

## Встановлення Драйверів Invidia

```bash
sudo dnf install akmod-nvidia -y
```

## Альтеранативний метод встановлення

```bash
sudo dnf install gcc kernel-headers kernel-devel akmod-nvidia xorg-x11-drv-nvidia xorg-x11-drv-nvidia-libs xorg-x11-drv-nvidia-power nvidia-settings
```
