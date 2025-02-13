# RPM Fusion

{% hint style="info" %}
RPM Fusion — це репозиторій, який поширює програмне забезпечення, яке Red Hat та Fedora Project не хочуть робити доступним у своїх власних репозиторіях, в основному з ліцензійних причин, оскільки Red Hat надає тільки програмне забезпечення з відкритим вихідним кодом.
{% endhint %}

Все програмне забезпечення, що є в RPM Fusion, вже попередньо скомпільовано у форматі RPM, потрібно лише виконати пошук у системному сховищі або ввести одну команду в терміналі.

```bash
sudo dnf search НАЗВА_ПАКЕТА
```

RPM Fusion був створений як комбінація з трьох інших репозиторіїв: Dribble, Freshrpms і Livna, з метою поширення якомога більшої кількості програмного забезпечення в одному місці.

## Як увімкнути RPM Fusion?

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

_Free_ repository

```bash
sudo dnf install \
  https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
```

_Nonfree_ repository

```bash
sudo dnf install \
  https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

{% hint style="success" %}
Рекомендується перезавантажити сесію або сам ПК.
{% endhint %}
