Задание 1
 Управление пользователями
 ```
$ sudo grep student /etc/passwd /etc/shadow
$ sudo useradd user1
$ sudo passwd user1

$ sudo grep user1 /etc/passwd /etc/shadow

$ cat /etc/default/useradd

$ cat /etc/login.defs 

$ sudo useradd -s /bin/ksh user2
$ sudo passwd user2

. $ sudo grep user1 /etc/shadow

$ sudo chage -E 2013-12-1 user1

$ sudo grep user1 /etc/shadow

$ sudo usermod -L user1

$ sudo passwd user1
```
Задание 2
```
 Упаравление группами

$ sudo useradd -m rocky
$ sudo useradd -m bullwinkle
$ sudo passwd rocky
$ sudo passwd bullwinkle
$ ls -l /home
$ sudo groupadd friends
$ sudo groupadd -g 490 bosses
$ grep -e friends -e bosses /etc/group

$ sudo usermod -G friends,bosses rocky
$ sudo usermod -G friends Bullwinkle
$ grep -e rocky -e bullwinkle /etc/group

$ groups rocky Bullwinkle

$ ssh rocky@localhost
$ cd ~
$ mkdir somedir
$ chgrp bosses somedir
$ ls -l
$ chmod a+x .

$ ssh bullwinkle@localhost
$ touch /home/rocky/somedir/somefile
$ exit

$ sudo usermod -a -G bosses Bullwinkle
$ ssh bullwinkle@localhost
$ touch /home/rocky/somedir/somefile
$ ls -al /home/rocky/somedir
```

Задание 3
```
 Управление правами

$ touch  afile
$ chmod u=r,g=w,o=x afile
$ chmod u=+w,g=-w,o=+rw afile
$ chmod ug=rwx,o=-rw afile
```
