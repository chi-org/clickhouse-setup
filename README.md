# clickhouse-setup

#### 1. Prerequisites

- 1 Ansible host
- 3 Clickhouse hosts



#### 2. Clickhouse Setup

Clone this repo and run this script on Ansible host:

1. Install necessary packages:
   ```bash
   ansible-galaxy collection install -r requirements.yml --upgrade
   ```

2. Modify `inventory.yml` for your target hosts. Default host number is 3 but you can define more host for more replicas and shards.

3. Run playbook:

   ```bash
   ansible-playbook clickhouse_setup.yml -i inventory.yml -k -K
   ```


4. Additional: Uncomment `Uninstall ClickHouse Database` task and comment other tasks to remove ClickHouse.

5. Change to sharding:
- Modify `shard` and `replication` in `inventory.yml`
- Modify `remote-servers.xml.j2`
- Comment setup tasks in `clickhouse_setup.yml`
- Notice: After changing the config file, the old tables configs remain the same. It only affects the new tables.



#### 3. MariaDB to ClickHouse data migration

- python is required
- user with permission in mariadb is required
- user with permission in clickhouse db is required

```bash
pip install clickhouse-mysql

clickhouse-mysql --src-server-id 1 --migrate-table --src-wait --nice-pause 1 --src-host=<maria-host> --src-port <maria-port> --src-user=<maria-user> --src-password=<maria-pw> --src-schemas <maria-db> --src-tables <maria-table(s)> --dst-host=<ch-host> --dst-user=<ch-user> --dst-password=<ch-pw> --with-create-database --dst-create-table --log-level=info
```

