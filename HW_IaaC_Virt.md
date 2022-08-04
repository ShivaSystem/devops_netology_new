# Решение домашнего задания к занятию "5.2. Применение принципов IaaC в работе с виртуальными машинами"

## Задача 1
* Опишите своими словами основные преимущества применения на практике IaaC паттернов.
 ** Использование IaaC значительно повышает эффективность команды. Позволяет стандартизировать и автоматизировать инфраструктуру. В случае сбоев гораздо проще восстановить. Позволяет минизировать дрифт конфигураций. Применяется идемпотентность.
 ** Идемпотентность
 
## Задача 2
* Чем Ansible выгодно отличается от других систем управление конфигурациями?
 ** Ansible использует push метод. Для управления хостами использует существующую ssh инфраструктуру. Не требует сложной установки основого сервера и разворачивания агентов.
* Какой, на ваш взгляд, метод работы систем конфигурации более надёжный push или pull?
  ** По моему мнению более надежен PUSH метод. Так как при использовании данного метода можно сразу понять применились ли изменения.
  
## Задача 3
* Установить на личный компьютер VirtualBox, Vagrant, Ansible

```
# vboxmanage --version
6.1.34_Ubuntur150636
```

```
# vagrant --version
Vagrant 2.2.6
```

```
# ansible --version
ansible [core 2.13.2]
config file = /home/netology/hw_IaaC/vagrant/ansible.cfg 
configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']    
ansible python module location = /usr/local/lib/python3.8/dist-packages/ansible         
ansible collection location = /root/.ansible/collections:/usr/share/ansible/collections   
executable location = /usr/local/bin/ansible                                 
python version = 3.8.10 (default, Jun 22 2022, 20:18:18) [GCC 9.4.0]  
jinja version = 3.1.2    
libyaml = True  
```



