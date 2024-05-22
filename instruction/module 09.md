Подключить к виртуальной машине 5 дополнительных жестких дисков

Создание раздела на файле

```
dd if=/dev/zero of=imagefile bs=1M count=1024
```
```
mkfs.ext4 imagefile
```
```
mkdir mntpoint
mount -o loop imagefile mntpoint
```
Создаем раздел на диске

```
fdisk /dev/sdb
создайте первичный раздел на 500 МБ
mkfs.ext4 /dev/sdb1
mkdir mnt/sdb1
mount /dev/sdb1 /mnt/sdb1
```
Подключение диска
```
nano /etc/fstab
```
```
/dev/sdb1 /mnt/sdb1 ext4 defaults 0 0
```

```
mount /mnt/sdb1
```


Cоздание SWAP
```
cat /proc/swaps
```
```
dd if=/dev/zero of=swpfile bs=1M count=1024
mkswap swpfile
swapon swpfile
```
LVM

Подключить к виртуальной машине 5 дополнительных жестких дисков

Установка LVM в Debian/Ubuntu
```
# apt install lvm2
```
Инициализация диска (можно раздела) для включения его в группу томов
```
# pvcreate /dev/sd{x} 

# pvs
# pvdisplay
```
Создаем новую группу томов (volume group) и добавляем туда свободный диск/раздел
```
# vgcreate vg1 /dev/sdb /… все ваши диски
# pvs
# pvdisplay
# vgdisplay vg1
```
Создаем логический том (logical volume) занимающий пространство в группе томов vg1
```
# lvcreate -n lv1 -L 1000M vg1
# lvdisplay
# lvdisplay /dev/vg1/lv1
```
Создаем файловую систему на логическом томе
```
# mkfs.ext4 /dev/vg1/lv1
  или
# mkfs.ext4 /dev/mapper/vg1-lv1
```
```
# mount /dev/vg1/lv1 /disk2
  или
# mount /dev/mapper/vg1-lv1 /disk2
```
```
# blkid /dev/mapper/vg1-lv1
```
Добавляем новый диск sdc к группе томов (volume group)
```
# pvcreate /dev/sdc
# vgextend vg1 /dev/sdc
# pvs
# pvdisplay
# vgdisplay vg1
```
Расширяем логический том (logical volume)
```
# lvextend -l +100%FREE /dev/vg1/lv1
```
Расширяем файловую систему
```
# resize2fs /dev/vg1/lv1
# df -h
```
Освобождаем диск sdb из группы томов
```
# umount /disk2
```
Уменьшаем размер файловой системы в томе (e2fsck обязательна)
```
# e2fsck -f /dev/vg1/lv1
# resize2fs /dev/vg1/lv1 990M
```
Уменьшаем размер логического тома
```
# lvreduce /dev/vg1/lv1 -L 1000M
  Rounding up size to full physical extent 1000.00 MiB
  WARNING: Reducing active logical volume to 1000.00 MiB
  THIS MAY DESTROY YOUR DATA (filesystem etc.)
Do you really want to reduce lv1? [y/n]: y
  Reducing logical volume lv1 to 1000.00 MiB
  Logical volume lv1 successfully resized
```
Монтируем логический том и продолжаем с ним работать
```
# mount /dev/vg1/lv1 /disk2
```
Переносим в "горячем режиме" данные с освобождаемого диска
```
# pvmove /dev/sdb
```
Отключаем диск от группы томов
```
# vgreduce vg1 /dev/sdb
  Removed "/dev/sdb" from volume group "vg1"

root@gate:~# pvremove /dev/sdb

root@gate:~# pvs
```
