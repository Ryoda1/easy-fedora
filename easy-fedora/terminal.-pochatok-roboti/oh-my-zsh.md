---
description: Оболонка для терміналу
---

# Oh-My-Zsh

### Що таке Oh My Zsh?

**Oh My Zsh** — це популярний фреймворк для керування конфігурацією оболонки Zsh. Він спрощує роботу з терміналом, додаючи підтримку тем, плагінів та зручних команд.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## Встановлення ZSH

```bash
sudo dnf install zsh
```

## Змінюємо оболонку (shell)

```bash
chsh -s /usr/bin/zsh
```

## Встановлення Oh My Zsh&#x20;

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Де знаходиться Config?

Конфігураційний файл для Zsh знаходиться в домашньому каталозі користувача і називається `.zshrc`

```bash
sudo nano ~/.zshrc
```

Ця команда відкриє файл у текстовому редакторі Nano.
