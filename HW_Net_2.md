#  Решение домашнего задания к занятию "3.7. Компьютерные сети, лекция 2"
1. Проверьте список доступных сетевых интерфейсов на вашем компьютере. Какие команды есть для этого в Linux и в Windows?
* Linux

```
# ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: tunl0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ipip 0.0.0.0 brd 0.0.0.0
3: sit0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/sit 0.0.0.0 brd 0.0.0.0
28: eth0@if29: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default
    link/ether 02:42:ac:11:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
```

* Windows

```
>ipconfig

Настройка протокола IP для Windows


Неизвестный адаптер OpenVPN Wintun:

   Состояние среды. . . . . . . . : Среда передачи недоступна.
   DNS-суффикс подключения . . . . . :

Адаптер Ethernet Ethernet 3:

   DNS-суффикс подключения . . . . . :
   Локальный IPv6-адрес канала . . . : fe80::2533:d391:e9ac:85f7%6
   IPv4-адрес. . . . . . . . . . . . : тут был ip адрес)
   Маска подсети . . . . . . . . . . : 255.255.255.0
   Основной шлюз. . . . . . . . . : тут был ip шлюза)

Неизвестный адаптер OpenVPN TAP-Windows6:

   Состояние среды. . . . . . . . : Среда передачи недоступна.
   DNS-суффикс подключения . . . . . :

Адаптер Ethernet vEthernet (WSL):

   DNS-суффикс подключения . . . . . :
   Локальный IPv6-адрес канала . . . : fe80::74fa:d2ae:9ecd:c089%38
   IPv4-адрес. . . . . . . . . . . . : 172.20.144.1
   Маска подсети . . . . . . . . . . : 255.255.240.0
   Основной шлюз. . . . . . . . . :
```

2. Какой протокол используется для распознавания соседа по сетевому интерфейсу? Какой пакет и команды есть в Linux для этого?
* Изпользуется протокол LLDP. Пакет называется lldpd. Чтобы установить его нужно использовать команду представленную ниже:

```
# apt install lldpd
```

* Для обнаружения соседей можно использовать следующую команду:

```
$ sudo lldpcli show neighbors
```

3. Какая технология используется для разделения L2 коммутатора на несколько виртуальных сетей? Какой пакет и команды есть в Linux для этого? Приведите пример конфига.

* Технология называется VLAN (Virtual Local Area Network).
* Для того чтобы можно было настроить VLAN на ubuntu необходимо установить пакет vlan 

```
# apt install vlan
```

* Привет конфига /etc/network/interfaces

```
auto eth0@if146.20
iface eth0@if146.20 inet dhcp
vlan-raw-device eth0@if146
```

* Также vlan можно настроить через утилиту ip. Например:
```
# ip link add link eth0 name eth0.20 type vlan id 20
```

* Затем нужно присвоить ip и активировать интерфейс:

```
# ip addr add 172.16.20.109/24 brd 172.16.20.255 dev eth0.20
# ip link set dev eth0.20 up
```

