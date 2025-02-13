---
description: 'Утиліта для бекапу вашої системи: (Для досвідчених користувачів.)'
---

# Timeshift

Timeshift — це утиліта, яка працює в двох режимах: RSYNC для створення повних знімків вашого диска та BTRFS, де використовуються особливості файлової системи BTRFS, що дозволяє створювати точки відновлення.

<figure><img src="../../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>

## Встановлення

```bash
sudo dnf install timeshift
```

{% hint style="warning" %}
Щоб режим Btrfs працював коректно, необхідно переналаштувати Btrfs subvolumes, оскільки утиліта Timeshift була створена для дистрибутивів, подібних до Debian, і тому не розуміє маркування subvolumes у Fedora Linux.
{% endhint %}
