---
description: Керування Flatpak-додатками
---

# Flatpak

<figure><img src="../../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### Оновити всі Flatpak-додатки:

```bash
flatpak update
```

Переглянути список встановлених Flatpak-додатків:

```bash
flatpak list
```

#### Видалити Flatpak-додаток:

```bash
flatpak remove org.назва.додатка
```

#### Видалити невикористовувані бібліотеки:

```bash
flatpak remove --unused
```

#### Видалити папку та конфіги з каталогу `/var`:

```bash
flatpak remove --delete-data
```
