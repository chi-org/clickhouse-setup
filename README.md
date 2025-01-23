# clickhouse-replication-setup

#### 1. Prerequisites

- 1 Ansible host
- 3 Clickhouse replica hosts



#### 2. Clickhouse Setup

Clone this repo and run this script on Ansible host:

1. Install necessary packages:
   ```bash
   ansible-galaxy collection install -r requirements.yml --upgrade
   ```

2. Modify `inventory.yml` for your target hosts. Default host number is 3 but you can define more host for more replicas.

3. Run playbook:

   ```bash
   ansible-playbook clickhouse_replication_setup.yml -i inventory.yml -k -K
   ```


4. Additional: Uncomment `Uninstall ClickHouse Database` task and comment other tasks to remove ClickHouse.
