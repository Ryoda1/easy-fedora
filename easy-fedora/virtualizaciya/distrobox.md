---
description: Контейнер
---

# DistroBox

Distrobox — це інструмент, який дозволяє використовувати різні дистрибутиви Linux у контейнерах з повною інтеграцією з основною системою. Дізнайтеся, як встановлювати, налаштовувати та використовувати Distrobox з різними менеджерами контейнерів, хост-системами та дистрибутивами.

<figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

## Встановлення Distrobox:

```bash
sudo dnf copr enable alciregi/distrobox
sudo dnf install distrobox
sudo dnf install podman
```

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

## Як користуватися distrobox?

### Основні команди Distrobox

* **`distrobox-assemble`** – створює та знищує контейнери на основі конфігураційного файлу.
* **`distrobox-create`** – створює контейнер.
* **`distrobox-enter`** – для входу в контейнер.
* **`distrobox-ephemeral`** – створює тимчасовий контейнер, який видаляється після виходу з оболонки.
* **`distrobox-list`** – для перегляду списку контейнерів, створених за допомогою Distrobox.
* **`distrobox-rm`** – для видалення контейнера, створеного за допомогою Distrobox.
* **`distrobox-stop`** – для зупинки запущеного контейнера, створеного за допомогою Distrobox.
* **`distrobox-upgrade`** – для оновлення одного або кількох запущених контейнерів одночасно.
* **`distrobox-generate-entry`** – створює запис контейнера у списку застосунків.
* **`distrobox-init`** – точка входу в контейнер (не призначена для ручного використання).
* **`distrobox-export`** – використовується всередині контейнера для експорту застосунків і сервісів з контейнера на хост.
* **`distrobox-host-exec`** – для запуску команд/програм із хоста, перебуваючи всередині контейнера.

**Ось приклад створення контейнера з операційною системою за допомогою Distrobox:**

```bash
distrobox-create --name arch-distrobox --image archlinux:latest
```

Ця команда створить контейнер на основі останньої версії образу Arch Linux.
