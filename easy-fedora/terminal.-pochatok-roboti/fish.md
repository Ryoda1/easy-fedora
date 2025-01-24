---
description: Оболонка для терміналу
---

# Fish

<div align="left"><figure><img src="../../.gitbook/assets/image (48).png" alt="" width="300"><figcaption></figcaption></figure></div>

## Встановлення Fish shell

```bash
sudo dnf install fish
```

## Змінюємо оболонку термінала за замовчуванням.

```bash
chsh -s /usr/bin/fish
```

## Налаштування Fish

```
fish_config 
```

<figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

## Прибираємо або змінюємо напис

<div align="left"><figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure></div>

```bash
set -U fish_greeting ""
```

Якщо хочете додати свій текст то в лапках пишіть те, що хочете.

```bash
set -U fish_greeting "Hello World"
```

