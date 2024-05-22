Потоки
```
$ ps ax > ps.txt

$ > ps.txt ps ax

$ less ps.txt

$ grep init ps.txt
```

Работа с конвеером
```
$ ps ax > ps.txt
$ grep init < ps.txt

или

$ ps ax | grep init

$ du -s /usr/share/* | sort -n | tail -n 1

```
Работа с командой Cat
```
$ cat /etc/passwd
```

При отсутствии аргументов читает с STDIN, пишет на STDOUT
```
$ cat

$ cat < /etc/passwd

$ cat > f.txt

$ cat < f.txt > f2.txt
```

Файловый дескриптор номер 2 - STDERR
```
$ ls fhgfdgbdfhsd

$ ls errfilename > ls_res.txt

$ ls errfilename 2> ls_err.txt

$ ls /bin /b1n 2>&1 | tee full_log.txt

$ ls /bin /errdirname > ls.txt 2>&1

$ ls /sdfgsdfgsd > /dev/null 2>&1

$ ls /sdfgsdfgsd 2>/dev/null >&2

$ ls /sdfgsdfgsd &>/dev/null
```
Настройка командных интерпретаторов
```
$ PS1="[\h:\W] # "

```
Переменная ? - код завершения последнего запущенного процесса
```
$ ls /bin
$ echo $?

$ ls /noexistfile
$ echo $?
```
Сигналы
```
# kill -l
```
Определение PID процесса
```
# /usr/sbin/sshd

# ps ax | grep ssh | grep -v grep

# cat /var/run/sshd.pid
```
TERM
чаще всего - остановка процесса
```
# kill <PID>

# kill -TERM <PID>
```

KILL
```
# kill -9 <PID>

# kill -KILL <PID>
```
