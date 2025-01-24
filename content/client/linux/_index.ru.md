---
title: Linux 
weight: 4
---

### Установка

#### Ubuntu (≥ 18)

```sh
# игнорируйте предупреждение "wrong disk usage"
sudo apt install -fy ./rustdesk-<version>.deb
```

Для Ubuntu 18.04, пожалуйста, сначала выполните следующие действия для [pipewire](https://github.com/rustdesk/rustdesk/discussions/6148#discussioncomment-9295883).
```sh
sudo apt install software-properties-common
sudo add-apt-repository ppa:pipewire-debian/pipewire-upstream
sudo apt update
```

#### CentOS/Fedora (≥ 28)

```sh
sudo yum localinstall ./rustdesk-<version>.rpm
```

#### Arch Linux/Manjaro

```sh
sudo pacman -U ./rustdesk-<version>.pkg.tar.zst
```

#### Opensuse (>= Leap 15.0)

```sh
sudo zypper install --allow-unsigned-rpm ./rustdesk-<version>-suse.rpm
```

#### AppImage

```sh
# Для Fedora
sudo yum install libnsl
./rustdesk-<version>.AppImage
```

```sh
# Для Ubuntu
sudo yum install libfuse2
./rustdesk-<version>.AppImage
```

#### Flatpak

```sh
flatpak --user remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak --user install ./rustdesk-<version>.flatpak
flatpak run com.rustdesk.RustDesk
```
### ~~X11 обязателен~~
~~RustDesk пока не поддерживает Wayland. Необходимо перейти на X11 вручную.~~

В RustDesk теперь есть экспериментальная поддержка Wayland. Возможно, вам потребуется скачать ночную версию, чтобы включить эту функцию.

#### Сервер отображения

[Ubuntu](https://askubuntu.com/questions/1260142/ubuntu-set-default-login-desktop) | 
[Fedora](https://docs.fedoraproject.org/en-US/quick-docs/configuring-xorg-as-default-gnome-session/) | 
[Arch Linux](https://bbs.archlinux.org/viewtopic.php?id=218319)

##### Экран входа в систему

Экран входа в систему с помощью Wayland пока не поддерживается. Если вы хотите получить доступ к экрану входа в систему после перезагрузки или выхода из системы RustDesk, вам нужно изменить экран входа в систему на X11, пожалуйста, измените строку ниже на "WaylandEnable=false" в "/etc/gdm/custom.conf" или "/etc/gdm3/custom.conf".:

```ini
#WaylandEnable=false
```

{{% notice note %}}
**Перезагрузите** ваш компьютер, чтобы применить изменения
{{% /notice %}}

#### Проблема разрешений

Если SELinux включен, RustDesk не будет работать должным образом ни в средах X11, ни в Wayland, связанных [issues](https://github.com/search?q=repo%3Arustdesk%2Frustdesk+SElinux&type=issues).

Вы можете запустить:

```sh
$ sudo grep 'comm="rustdesk"' /var/log/audit/audit.log | tail -1
type=AVC msg=audit(1697902459.165:707): avc:  denied  { name_connect } for  pid=31346 comm="rustdesk" dest=53330 scontext=system_u:system_r:init_t:s0 tcontext=system_u:object_r:ephemeral_port_t:s0 tclass=tcp_socket permissive=0
```


{{% notice note %}}
**Перезагрузите** ваш компьютер, чтобы применить изменения
{{% /notice %}}

Если выходные данные содержат `avc: denied`, то вам необходимо добавить политики SELinux, пожалуйста, обратитесь к [SELinux](https://rustdesk.com/docs/en/client/linux/selinux/).
