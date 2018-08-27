# Installing Bosun with OpenTSDB backend
Bosun is an open-source monitoring and alerting system by Stack Exchange. To Learn more visit - https://bosun.org/

This ansible playbook automates the following tasks:
- JDK Installation
- GoLang Installation
- Install/Configure HBase to run on top of Hadoop Distributed File System (HDFS)
- Install OpenTSDB on HBase nodes
- Install Bosun

Follow the steps given below to get up and running with bosun.

### Install ansible and git 
$ sudo yum install -y ansible git


### Clone this repository
$ cd ~ && git clone https://github.com/bishwash-devops/ansible.git


### Run the Playbook:
$ ansible-playbook -i 'localhost,' -c local bosun.yml


### Once The Ansible Playbook is Executed without any errors:
Switch user:

$ sudo su hadmin


### Run following commands:
$ hdfs namenode -format

Note: If prompted for reformat hit N


### Start Hadoop:
$ start-dfs.sh

$ start-yarn.sh

Access Hadoop Web: http://PUBLIC_IP:50070

Validate: You must have NameNode and 1 DataNode Running.

### Start Hbase
$ start-hbase.sh

Access Hbase Web: http://PUBLIC_IP:16010

Validate: Make sure at least 1 of the regionservers is running


### Start Opentsdb
$ cd /opt/hadmin/opentsdb

$ env COMPRESSION=NONE ./src/create_table.sh

$ nohup ./build/tsdb tsd &

Acess Opentsdb Web: http://PUBLIC_IP:4242


### Start Bosun
$ cd /opt/hadmin/bosun

$ nohup ./bosun &

Access Bosun Web: http://PUBLIC_IP:8070

