---
description: Якщо ти любиш ризикувати, можна піти далі...
---

# Оновлення до Beta.

{% hint style="info" %}
Ви берете на себе всі ризики! Але цікавість іноді бере своє...
{% endhint %}

## **Як оновитися вже зараз з Fedora 42 (в майбутньому просто заміняєте на 43/44 тощо):**

```bash
sudo dnf makecache --refresh && sudo dnf upgrade --refresh

sudo dnf autoremove && sudo dnf clean all

sudo dnf install dnf-plugin-system-upgrade -y

sudo dnf system-upgrade download --releasever=42 # Змінюємо тут

sudo dnf system-upgrade reboot
```

## **Якщо метод вище не працює або є помилки:**

```bash
sudo dnf system-upgrade download --releasever=42 --allowerasing --skip-broken

sudo dnf system-upgrade reboot

sudo dnf system-upgrade clean
```

## **Якщо ж і --allowerasing не працює, то пробуємо:**

```bash
sudo dnf distro-sync

sudo fixfiles -B onboot
```

_І пробуємо знову._

{% hint style="danger" %}
Пам'ятайте! Ви робите все на свій страх і ризик!

Немає гострої необхідності оновлюватися з версії на версію, краще, навпаки, почекати кілька днів після релізу і вже потім оновитися штатно через GNOME Software.
{% endhint %}
