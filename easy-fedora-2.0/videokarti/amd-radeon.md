---
cover: >-
  https://www.thefpsreview.com/wp-content/uploads/2020/10/amd-radeon-rx-6000-series-where-gaming-begins-tease-1-scaled.jpg
coverY: 0
---

# AMD RADEON

{% hint style="info" %}
Сучасні пріоритети при виборі відеокарти для Linux радикально змінилися. Якщо кілька років тому очевидним вибором були карти від “зелених” (Nvidia), то зараз, завдяки розвитку відкритого драйвера **Mesa**, карти "червоних" від **AMD** стали більш вигідним рішенням для користувачів Linux.

Компанія **AMD** зробила стратегічно важливий крок, відкривши вихідний код свого драйвера для відеокарт. Це дозволило спільноті Linux швидко інтегрувати цей код у свої проєкти, результатом чого стало стрімке вдосконалення драйвера **Mesa**. На сьогодні цей драйвер забезпечує відмінну продуктивність і стабільність для користувачів, які обирають відеокарти AMD.
{% endhint %}

## **Утиліта CoreCtrl**

CoreCtrl — це утиліта для керування апаратним забезпеченням на Linux, яка дозволяє користувачам налаштовувати продуктивність і енергоспоживання процесорів та відеокарт.&#x20;

<figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption><p>  CoreCrtl</p></figcaption></figure>

### Встановлення  CoreCtrl

```bash
sudo dnf install corectrl
```

### Налаштування CoreCtrl

#### **Запуск CoreCtrl при старті сеансу**

Виконайте наступну команду в терміналі:

```bash
cp /usr/share/applications/org.corectrl.CoreCtrl.desktop ~/.config/autostart/org.corectrl.CoreCtrl.desktop
```

Для CoreCtrl версії 1.3 та старіших використовуйте цю команду:

```bash
cp /usr/share/applications/org.corectrl.corectrl.desktop ~/.config/autostart/org.corectrl.CoreCtrl.desktop
```

#### **Не запитувати пароль користувача**

CoreCtrl використовує помічник з правами root для керування системою. Щоб запустити помічника, система запропонує ввести ваш пароль через доступний агент аутентифікації Polkit. Якщо ви хочете уникнути запиту пароля кожного разу, ви можете постійно надати доступ до помічника.

1. Перевірте версію Polkit за допомогою команди:

```bash
pkaction --version
```

2. Якщо версія Polkit < 0.106

Створіть файл **/etc/polkit-1/localauthority/50-local.d/90-corectrl.pkla** з таким вмістом:

```bash
[User permissions]
Identity=unix-group:your-user-group
Action=org.corectrl.*
ResultActive=yes
```

Замість **your-user-group** вкажіть вашу групу користувача.

3. Якщо версія Polkit >= 0.106

Створіть файл **/etc/polkit-1/rules.d/90-corectrl.rules** з таким вмістом:

```bash
polkit.addRule(function(action, subject) {
    if ((action.id == "org.corectrl.helper.init" ||
         action.id == "org.corectrl.helperkiller.init") &&
        subject.local == true &&
        subject.active == true &&
        subject.isInGroup("your-user-group")) {
            return polkit.Result.YES;
    }
});
```

Замість **your-user-group** вкажіть вашу групу користувача.

#### Повний контроль над GPU

Для того, щоб мати повний контроль над вашою відеокартою, використовуючи драйвер **amdgpu**, вам потрібно додати параметр завантаження **amdgpu.ppfeaturemask=0xffffffff** до конфігурації завантажувача та перезавантажити систему.

**Завантажувач GRUB**

1. Відредагуйте файл **/etc/default/grub** з правами root і додайте **amdgpu.ppfeaturemask=0xffffffff** до **GRUB\_CMDLINE\_LINUX\_DEFAULT**:

```bash
GRUB_CMDLINE_LINUX_DEFAULT="... amdgpu.ppfeaturemask=0xffffffff"
```

{% hint style="info" %}
**УВАГА:** У наведеному прикладі **...** представляє інші існуючі параметри. Не додавайте **...** до вашого **GRUB\_CMDLINE\_LINUX\_DEFAULT**. Тільки додайте **amdgpu.ppfeaturemask=0xffffffff**.
{% endhint %}

2. Потім оновіть конфігурацію завантажувача за допомогою команди:

```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

3. Перезавантажте систему.

Тепер у вас повинно бути більше налаштувань при виборі режиму **Advanced** як **Performance**.
