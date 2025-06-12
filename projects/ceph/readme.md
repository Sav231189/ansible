Установка Ceph Cluster for clear nodes (check: ubuntu_24).
> cephadm_deploy.yml - hosts: bootstrap - Загружает образ ceph и устанавливаем cephadm.
> cephadm_bootstrap.yml - hosts: bootstrap - Производит Bootstrap первой ceph-ноды (так же автоматически обновляет версию quay.io/ceph/ceph). Назначается mgr (Manager daemon).
> cephadm_add_mon.yml - hosts: mon_nodes - Устанавливает мониторы.
> auto_osd.yml - hosts: all - Автоматическое добавление OSD на свободные диски.
