
Для эксперементов добавьте дополнительный сетевой адаптер в виртуальной машине и подключите к приватному свитчу.
```
apt install net-tools
```
Задание 1
```
$ ip addr show eth0
$ ip route

$ cp /etc/resolv.conf resolv.conf.keep

$ ifconfig eth0

$ route -n


$ sudo ip link set eth0 down

or

$ sudo ifconfig eth0 down
```
Задание 2
```

$ sudo sh -c "echo <ip host> mysystem.mydomain >> /etc/hosts"

$ ping mysystem.mydomain

$ sudo sh -c "echo 127.0.0.1 ad.doubleclick.net >> /etc/hosts"

$ ping ad.doubleclick.net

```
Задание 3
```
$ sudo nmcli con

$ sudo nmcli con show "Имя адаптера" | grep IP4.ADDRESS

$ nmcli con show <UUID из команды выше>

$ sudo nmcli con modify " Имя адаптера " +ipv4.addresses 172.16.2.140/24

$ sudo nmcli con up " Имя адаптера "

$ sudo nmcli con modify " Имя адаптера " -ipv4.addresses 172.16.2.140/24

$ sudo nmcli con up " Имя адаптера "

```
Задание 4
```
$ route

$ ip route

$ sudo nmcli conn mod " Имя адаптера " +ipv4.routes "192.168.100.0/24 172.16.2.1"

$ route

$ sudo nmcli conn up " Имя адаптера "

$ route

$ sudo nmcli conn mod " Имя адаптера " -ipv4.routes "192.168.100.0/24 172.16.2.1"

$ sudo nmcli conn up " Имя адаптера "

$ sudo ip route add 192.168.100.0/24 via 172.16.2.1

$ sudo route
```
Задание 5
```
Посмотреть название сетевого адаптера
ip a

Настройка сетевого интерфейса
nano /etc/network/interfaces



auto lo
iface lo inet loopback

auto <название сетевого адаптера>
iface <название сетевого адаптера> inet static
        address 172.16.1.10
        netmask 255.255.255.0
        gateway 172.16.1.254

альтернативный вариант

auto <название сетевого адаптера>
iface <название сетевого адаптера> inet static
        address 172.16.1.10/24
        gateway 172.16.1.254
```
Возможное будущее
https://github.com/canonical/netplan/tree/main/examples
