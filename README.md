# clickhouse-setup

#### 1. Prerequisites

- 1 Ansible host
- 3 Clickhouse replica hosts



#### 2. Clickhouse Setup

Clone this repo and run this script on Ansible host:

1. Install necessary packages:
   ```bash
   ansible-galaxy collection install -r requirements.yml --upgrade
   ```

2. Run playbook:
   ```bash
   ansible-playbook clickhouse_replication_setup.yml -i inventory.yml -k -K
   ```

   

