Задание  Размеры каталогов Linux 
Используйте утилиту du для расчета общего размера каждого из каталогов верхнего уровня вашей системы.
Введите команду:
```
$ du --help
```

Чтобы получить полный список каталогов / вместе с их размером,
Введите команду:
```
$ sudo du --max-depth=1 -hx /
```
Где мы использовали опции:
• --maxdepth=1: указатель на сколько уровней провести анализ, в данном случае на один уровень вниз от корневого каталога.
• -h: вывести на экран информацию в удобном формате (KB, MB, GB).
• -x отключить каталоги которых нет на файловой системе, например:
/dev /proc /run /sys
потому что это псевдофайловые системы, которые существуют только в памяти; это просто пустые точки монтирования, когда система не работает. Для система RHEL 7, следующие точки монтирования:
/bin /sbin /lib /lib64
поскольку они просто символически ссылки /usr.

Задание  Папка файловой системы/proc 

1. Под пользователем root, перейдите в /proc и отобразить список каталогов и файлов:
```
$ cd /proc
$ ls -F
```

Обратите внимание, что многие имена каталогов являются числами; каждый соответствует запущенному процессу, а имя - это процесс, про них мы узнаем в следующем модуле.


2. Посмотрите содержимое файлов:
```
• /proc/cpuinfo:
• /proc/meminfo:
• /proc/mounts:
• /proc/swaps:
• /proc/version:
• /proc/partitions:
• /proc/interrupts:
```
```
touch appendit
lsattr appendit
----ia-------e- appendit
$ chattr -ia appendit
$ rm appendit
rm: remove regular file `appendit'? y
$ ls appendit
ls: cannot access appendit: No such file or directory
```
```
$ cd /tmp
$ touch appendit
$ ls -l appendit
$ cat /etc/hosts > appendit
$ diff /etc/hosts appendit
$ chattr +a appendit
$ chattr +a appendit
$ lsattr appendit
$ cat /etc/passwd > appendit
$ sudo -i
$ cat /etc/passwd > appendit
bash: appendit: Operation not permitted
$ exit

$ cat /etc/passwd >> /tmp/appendit
$ cat appendit
$ sudo chattr +i appendit
$ lsattr appendit
----ia-------e- appendit
$ echo hello >> appendit
$ mv appendit appendit.rename
$ ln appendit appendit.hardlink
$ rm -f appendit
$ sudo -i
$ echo hello >> appendit
$ mv appendit appendit.rename
$ ln appendit appendit.hardlink
$ rm -f appendit
$ exit
```
