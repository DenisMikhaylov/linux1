Модуль 2 Лабораторные


Задание 1: Установка ОС

1. Скачать актуальный дистрибутив
2. Установить систему, не менять значения по умолчанию в процессе инсталляции
3. добавить пользователя student/password
4. Установить в linux ssh


Задание 2: Анализ оборудования

1. посмотреть оборудование установленное в ОС , использую команду lshw и dmesg
```
# dmesg | grep eth
# dmesg | grep Memory
# dmesg | grep sda */
```
2. Получть информацию использую папку proc
```
# cat /proc/interrupts

# cat /proc/cpuinfo
```
3. добавить пользователя student/password
4. Установить в linux ssh

Задание 3: Анализ ядра, модулей

1. Выяснить версию ядра
```
# uname -a
```
2. Вывод списка модулей. 
```
# find /lib/modules/`uname -r`/kernel/
# sysctl -a
```
3. Выяснить дистрибутив
```
$ lsb_release -a

$ cat /etc/os-release
$ cat /etc/*-release

$ cat /etc/issue

$ cat /etc/debian_version
```
Задание 4: Анализ процессов

1. Выяснить какие процессы запущены
```
$ps

$top

$htop
```
2. Выяснить состояние SSH службы
```
$systemctl status sshd
```
