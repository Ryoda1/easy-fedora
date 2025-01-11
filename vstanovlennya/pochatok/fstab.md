---
description: Для власників твердотільних накопичувачів SSD.
---

# Fstab

{% hint style="warning" %}
Окрім стандартних параметрів монтування, я додаю ще ці три через кому після `compress=zstd:1`.
{% endhint %}

Відкриваємо файл `fstab` за допомогою команди в терміналі.

<pre class="language-bash"><code class="lang-bash"><strong>sudo gnome-text-editor /etc/fstab
</strong></code></pre>

І додаємо ці параметри після `compress=zstd:1`.

```bash
,defaults,noatime,discard=async
```

Для розділів: /, /home, /var/log.

<figure><img src="../../.gitbook/assets/obraz (23).png" alt=""><figcaption><p>Редагування файлу <code>fstab</code> у GNU/Linux.</p></figcaption></figure>
