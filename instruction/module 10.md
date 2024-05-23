Задача 1

Создание пустого файла

```
# mkdir /disk2
# dd if=/dev/zero of=/disk2/filedisk bs=1M count=100
```
CPIO
Создание архива
```
# cd /; find etc/ | cpio -o | bzip2 -c > /mnt/etc.cpio.bz2

# cd /; find etc/ -name '*,v' | sed -e 's/RCS\///' -e 's/,v//' | cpio -o | bzip2 -c > /mnt/etc.cpio.bz2
# cd /; find etc/ -ctime -1 | cpio -o | bzip2 -c | cat > etc.cpio.bz2
```
Просмотр содержимого архива
```
# bzcat /mnt/etc.cpio.bz2 | cpio -t
```
Распаковка отдельных файлов/каталогов архива
```
# cd /tmp; bzcat /mnt/etc.cpio.bz2 | cpio -id etc/clamav/clamd.conf

# cd /tmp; bzcat /mnt/etc.cpio.bz2 | cpio -id -E fstab
```
Распаковка всего архива
```
# cd /tmp; bzcat /mnt/etc.cpio.bz2 | cpio -id
```
TAR
Создание архива
```
# mkdir /disk2
# chmod 750 /disk2
# cd /; tar -c -f /disk2/etc.tar etc/

# tar -c -f /disk2/etc.tar -C / etc/

# cd /; sudo /bin/tar -cjf - etc/ | ssh backup.isp.un "cat > etc.tbz"
```
Просмотр содержимого архива
```
# tar -t -f /disk2/etc.tar

# tar -t -v -f /disk2/etc.tar
```
Распаковка архива
```
# cd
# tar -xvf /disk2/etc.tar

# tar -xvf /disk2/etc.tar etc/fstab

# tar -xOf /disk2/etc.tar etc/fstab  #вывести на экран (STDOUT)

# tar -xf /disk2/etc.tar etc/ssh/

# tar -xf etc.tar --wildcards '*conf'

# tar -xf /disk2/etc.tar -C /tmp/

# ls /tmp/etc/
```
Задача 2
```
# mkdir /tmp/backup
```
```
# cd /usr ; tar zcvf /tmp/backup/include.tar.gz include
# cd /usr ; tar jcvf /tmp/backup/include.tar.bz2 include
# cd /usr ; tar Jcvf /tmp/backup/include.tar.xz include

du -sh /usr/include
ls -lh include.tar.*
tar tvf include.tar.xz

# cd .. ; mkdir restore ; cd restore
# tar xvf ../backup/include.tar.bz2
```
Задача 3

Использование rsync для резервного копирования

```
$ rm -rf include
$ rsync -av /usr/include .
$ rsync -av /usr/include .
$ rsync -av /usr/include include
$ rsync -av --delete /usr/include .
$ rm -rf include/xen
$ rsync -av --delete --dry-run /usr/include .
$ rsync -av --delete 	/usr/include .
```vpn.
