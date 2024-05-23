Задача 1
```
# Apt install stress
```
```
$ stress –help
stress -c 8 -i 4 -m 6 -t 20s
```

Задача 2
```
$ ps -ef
$ ps aux
$ ps -o pid,pri,ni,cmd

$ bash

$ nice -n 10 bash

$ ps -o pid,pri,ni,cmd
$ renice 15 -p 22171
$ ps -o pid,pri,ni,cmd
$ top
```
Задача 3
```
$ dd if=/dev/urandom of=/dev/null &
$ ps -C dd -o pid,cmd,stat
$ fg
$ ^Z
$ ps -C dd -o pid,cmd,stat
```
```
$ jobs
[1]+ Stopped dd if=/dev/urandom of=/dev/null
$ fg
$ kill {id process}
```

Задача 4
```
$ bonnie++ -help

$ time sudo bonnie++ -n 0 -u 0 -r 100 -f -b -d /mnt

$ bon_csv2html < bonnie++.out > bonnie++.html
или
# echo 'csv' | bon_csv2html > bonnie++.html
```
Задача 5
```
$ fs_mark -d /tmp -n 1000 -s 10240
$ fs_mark -d /mnt/sdb1 -n 1000 -s 10240
```
Пока это работает, соберите расширенную статистику iostat с помощью:
```
$ iostat -x -d /dev/sda 2 20
```
Цифры, которые вы обязательно должны отметить, — это количество файлов в секунду, сообщаемое fs mark, и процент используемого процессорного времени, сообщаемый iostat. Если это значение приближается к 100 процентам, вы ограничены вводом-выводом.

В зависимости от того, какую файловую систему вы используете, вы можете улучшить результаты, изменив параметры монтирования.

Например, для ext3 или ext4 вы можете попробовать:
```
# mount -o remount,journal_async_commit /tmp
# mount -o remount,journal_async_commit /mnt/sdb1
```
