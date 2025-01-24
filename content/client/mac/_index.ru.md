---
title: Mac 
weight: 3
---

### Установка

Откройте файл .dmg и перетащите `RustDesk` в `Applications` как на картинке ниже.

![](/docs/en/client/mac/images/dmg.png)

Убедитесь, что вы закрыли все запущенные приложения RustDesk. Также убедитесь, что вы закрыли службу RustDesk.

![](/docs/en/client/mac/images/tray.png)

### Разрешение на запуск RustDesk

| Разблокируйте для изменения | Нажмите на "App Store and identified developers" |
| ---- | ---- |
|![](/docs/en/client/mac/images/allow2.png)|![](/docs/en/client/mac/images/allow.png)|

### Включение разрешений

{{% notice note %}}
Из-за изменения политики безопасности MacOS наш API, который захватывает входные данные на локальной стороне, не работает
больше. Вам необходимо включить разрешение «Input Monitoring» на локальной стороне Mac.
Пожалуйста, следуйте этому
[https://github.com/rustdesk/rustdesk/issues/974#issuecomment-1185644923](https://github.com/rustdesk/rustdesk/issues/974#issuecomment-1185644923)

Похоже, быстрого решения не будет, нам нужно исправить это вместе с нашей версией Flutter.
{{% /notice %}}

Чтобы захватывать экран требуются разрешения **accessibility** и **screen recording**. RustDesk поможет их настроить.

| Окно RustDesk | Окно настроек |
| ---- | ---- |
|![](/docs/en/client/mac/images/acc.png)|![](/docs/en/client/mac/images/acc3.png?v2)|

Если разрешения включены, но RustDesk их не видит, то уберите RustDesk из списка при помощи кнопки `-`, затем нажмите кнопку `+` и выберите RustDesk в `/Applications`.

{{% notice note %}}
[https://github.com/rustdesk/rustdesk/issues/3261](https://github.com/rustdesk/rustdesk/issues/3261) <br>
Другие беспомощные попытки: <br>
`tccutil reset ScreenCapture com.carriez.RustDesk` <br>
`tccutil reset Accessibility com.carriez.RustDesk` <br>
Перезагрузка по-прежнему требуется.
{{% /notice %}}

| Кнопки `-` и `+` | Выбор RustDesk |
| ---- | ---- |
|![](/docs/en/client/mac/images/acc2.png)|![](/docs/en/client/mac/images/add.png?v2)|

Пройдите те же шаги для настройки разрешения **screen recording**.

![](/docs/en/client/mac/images/screen.png?v2)
