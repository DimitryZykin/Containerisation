## Урок 2. Механизмы контрольных групп
Скрыть
apt-get install lxc debootstrap bridge-utils lxc-templates
apt-get install lxd-installer
lxd init(Здесь просто нажимаем на Enter что уствновились значения по умолчанию)
Проверяем
lxc storage list
lxc storage list
И создаем контейнер
lxc-create -n test01 -t ubuntu -f /usr/share/doc/lxc/example/lxc-veth.conf
apt-get install lxc debootstrap bridge-utils lxc-templates
apt-get install lxd-installer
lxd init(Здесь просто нажимаем на Enter что уствновились значения по умолчанию)
Проверяем
lxc storage list
lxc storage list
И создаем контейнер
lxc-create -n test123 -t ubuntu -f /usr/share/doc/lxc/example/lxc-veth.conf
nano /var/lib/lxc/test123/config-открываем
lxc.rootfs.path = dir:/var/lib/lxc/test1234/rootfs — путь
lxc.uts.name = test1234 -- имя
__
# Network configuration — Конфигурация сети
.
.
.
lxc.cgroup2.memory.max = 256M -- ограничиваем

Задание 1:
1) запустить контейнер с ubuntu, используя механизм LXC
2) ограничить контейнер 256 Мб ОЗУ и проверить, что ограничение работает
3) По желанию
4) добавить автозапуск контейнеру, перезагрузить ОС и убедиться, что контейнер действительно запустился самостоятельн
5) при создании указать файл, куда записывать логи
6) после перезагрузки проанализировать логи
