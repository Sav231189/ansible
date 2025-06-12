# Установка Ceph Cluster for clear nodes (check: ubuntu_24).

> У вас должен быть Inventory c группой ceph (см. ansible/readme.md)
> 
> Минимум 3 хоста в группе ceph
> 
> Bootstrap только на 1 ноду
> 

**./deploy.yml** - hosts: bootstrap - Загружает образ ceph и устанавливаем cephadm.

**./bootstrap.yml** - hosts: bootstrap - Производит Bootstrap первой ceph-ноды (так же автоматически обновляет версию quay.io/ceph/ceph). Назначается mgr (Manager daemon).

**./add_mon.yml** - hosts: mon_nodes - Устанавливает мониторы.

**./auto_osd.yml** - hosts: all - Автоматическое добавление OSD на свободные диски.


### Масштабирование ➕
- Добавьте новую VPS в vpn-inventory → группу ceph (укажите ansible_host).
- ./deploy.yml — плейбук подхватит всех, скачает всем образы Ceph и установит Cephadm.
- ./bootstrap.yml — плейбук на 1 ноду для инициализации кластера, группа bootstrap (1 нода).
- ./add_mon.yml — плейбук для добавления MON на хосты группы mon-nodes.
- ./auto_osd.yml — плейбук для добавления OSD на хосты группы all.
