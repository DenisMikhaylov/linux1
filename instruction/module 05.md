Задание 7.1 Git
```
# apt install git
# mkdir git-test
# cd git-test
# git init
# ls -l .git

# echo some junk > somejunkfile
# git add somejunkfile
# git status
# git config user.name "Another Genius"
# git config user.email b_genius@linux.com
# echo another line >> somejunkfile
# git diff
# git commit -m "My initial commit"
# git log

Задание 7.3 APT

Обновление списка доступных пакетов
# apt update

Поиск пакета
# apt search antivirus

Информация о найденном пакете
# apt show clamav-daemon

Какие пакеты зависят от пакета
# apt depends ssh

Установка/обновление пакета
# apt install clamav-daemon
# DEBIAN_FRONTEND=noninteractive apt -y install postfix

Удаление пакета

# apt remove snort
# apt autoremove

Полное (с конфигами и данными) удаление пакета

# apt purge snort

Отключение автоматических обновлений
# apt purge unattended-upgrades

Какие пакеты можно/нужно обновить
Ubuntu security notices

# apt list --upgradable

# apt-show-versions -i

# apt-show-versions -u

# apt-show-versions -u | grep security

# ubuntu-support-status --show-all

Задание 7.3 SNAP


# snap refresh

# snap search firefox

# snap install hello

# snap list

# find /snap/ | grep hello

# hello

# snap refresh hello

# snap remove hello

```
