---
description: Шрифти від Microsoft
---

# Microsoft Fonts

## Встановлюємо шрифти, які використовуються у Windows.

Перед встановленням шрифтів Microsoft, необхідно переконатися, що у вашій системі є всі необхідні інструменти. До них належать: curl для завантаження файлів, cabextract для розпакування файлів шрифтів Microsoft, а також fontconfig для керування та налаштування доступу до шрифтів. Більшість установок Fedora мають ці інструменти за замовчуванням, але буде доцільно перевірити та встановити відсутні.

Використовуйте цю команду для їх встановлення:

```bash
sudo dnf install curl cabextract xorg-x11-font-utils fontconfig
```

Після встановлення необхідних компонентів можна завантажити та встановити пакет **Microsoft Core Fonts**, використовуючи таку команду:

```bash
sudo rpm -i https://downloads.sourceforge.net/project/mscorefonts2/rpms/msttcore-fonts-installer-2.6-1.noarch.rpm
```
