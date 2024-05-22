Управление юнитами Systemd
```
$ systemctl -a
$ systemctl list-units

# find /lib/systemd/system/

# find /etc/default/

$ systemctl status ssh

# systemctl stop ssh
# systemctl start ssh
# systemctl reload ssh

# systemctl disable ssh
# systemctl enable ssh

```
```
# cat /etc/systemd/system/sshvpn.service
```
Посмотреть содержимое файла.

Создание fake сервиса
```
nano /etc/systemd/system/fake2.service
```
```
[Unit]
Description=fake2
After=network.target
[Service]
ExecStart=/bin/sh -c '/bin/echo I am starting the fake2 service ; /bin/sleep 30'
ExecStop=/bin/echo I am stopping the fake2 service
[Install]
WantedBy=multi-user.target
```

Тетирование сервиса

```
systemctl start fake2.service
systemctl status fake2.service
systemctl stop fake2.service
```

Проверка лога
```
tail -f /var/log/messages
```
```
systemctl enable fake2.service
systemctl disable fake2.service
```
