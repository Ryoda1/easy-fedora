---
description: Перенесення subvolume btrfs (Для досвідчених користувачів.)
---

# Налаштовуємо підтоми BTRFS

Перш за все, перевіряємо, щоб у вашій системі нічого не було змонтовано в директорії **/mnt**.

```bash
ls -a /mnt
```

Якщо в директорії вже щось змонтовано, просто створіть нову директорію та змонтуйте туди.

Наприклад:

```bash
sudo mkdir /mnt/btrfs
```

{% hint style="warning" %}
У цьому посібнику всі команди будуть виконуватись з урахуванням того, що була створена директорія btrfs.
{% endhint %}

Далі потрібно визначити, на який пристрій встановлено систему:

```bash
df -h
```

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Тепер монтуємо файлову систему (з урахуванням ваших результатів):

<pre class="language-bash"><code class="lang-bash"><strong>sudo mount /dev/sda3 /mnt/btrfs
</strong></code></pre>

Якщо відкрити примонтовану директорію через файловий менеджер, то будуть видні примонтовані підрозділи (subvolume).

## перенос підтомів

Тепер приступаємо до переносу підтомів.

```bash
sudo mv /mnt/btrfs/root /mnt/btrfs/@

sudo mv /mnt/btrfs/home /mnt/btrfs/@home
```

Далі редагуємо fstab:

```bash
sudo vim /etc/fstab
```

{% hint style="success" %}
Змінюємо **root** на **@**, а **/home** на **@home** в **fstab**.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Зберігаємо зміни за допомогою **Ctrl+O**, виходимо з редактора за допомогою **Ctrl+X**.
{% endhint %}

Оновлюємо GRUB (обов'язково!):

```bash
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```

## Розмонтовуємо файлову систему

Скидаємо всі дані з кешу в файлову систему:

```bash
sync
```

Розмонтовуємо файлову систему:

```bash
sudo umount -r /mnt/btrfs
```

{% hint style="success" %}
&#x20;Тепер можна перезавантажити ПК.
{% endhint %}

Командою:

```bash
sudo btrfs sub list /
```

можна подивитися, які **subvolumes** у нас зараз є.

{% hint style="success" %}
Тепер, до речі, Timeshift працюватиме на повну.
{% endhint %}
