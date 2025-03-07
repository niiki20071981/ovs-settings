# ovs-settings
Что-бы настроить ovs понадобится скачать его
apt-get update && apt-get install -y openvswitch

Включить в авто загрузку
systemctl enable --now openvswitch

Создать все интерфейсы

Создать мост ovs
ovs-vsctl add-br *имя моста*

Создать папку интерфейса MGMT

Заполнить options
***
TYPE - тип интерфейса (internal);(ovsport)
BOOTPROTO - определяет как будут назначаться сетевые параметры (static);
CONFIG_IPV4 - определяет использовать конфигурацию протокола IPv4 или нет (yes);
BRIDGE - определяет к какому мосту необходимо добавить данный интерфейс;
VID - определяет принадлежность интерфейса к VLAN;(330-110)
DISABLED - определяет состояние инерфейса (No);
***

Назначаем ip и шлюз в MGMT

В default ставим ovs_remove no

Создаем виртуальные интерфейсы и назначаем транки
ovs-vsctl add-port *имя моста* ens19 trunk=110,220,330

включаем модуль ядра 8021q
modprobe 8021q

