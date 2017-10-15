# Ansible Playbooks

## Install Hadoop in Centos/Rhel 7

In Reference To : http://linuxpitstop.com/configure-distributed-hbase-cluster-on-centos-linux-7/

Install ansible and git - $ sudo yum install -y ansible git

Clone this repository - $ cd ~ && git clone https://github.com/bishwash-devops/ansible.git

Run the Playbook:
$ ansible-playbook -i 'localhost,' -c local bosun.yml

Once It Complete's without errors:
Switch user:
$ sudo su hadmin

Start Hadoop:
$ start-dfs.sh
$ start-yarn.sh

Access Hadoop Web: http://PUBLIC_IP:50070
Validate: You must have NameNode and 1 DataNode Running.

Start Hbase
$ start-hbase.sh

Access Hbase Web: http://PUBLIC_IP:16010
Validate: Make sure at least 1 of the regionservers is running


