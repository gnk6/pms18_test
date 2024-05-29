### Description ###
Ansible playbook to deploy Influxdb, Telegraf, Grafana and owncloud in Debian system. 
Influxdb and Telgraf are preconfigured to collect metrics from the running system's containers. This data is getting vizualizes in Grafana dashboard.



### About the directories ###
- Directory "container_files" contains the needed files for the containers to run, such as dockerfile, docker-compose.yml etc.
- Diectory "container_templates" contains j2 templates, .env file and telegraf.conf.
- Directory group_vars container the variables for the group "servers".



### How to run it ###
1. Enter the hostname or ip address of your servers in "hosts" file (make sure that ssh (root) access is feasible with pubkey). The file should look like the below
[servers]
server1
server2

2. Alter the content of file "group_vars/servers". An example of the configuration is the below. To create the influxdb token run "openssl rand -hex 32"
influxPass: password
influxToken: 43430rerfeferf3r32r23r23rf
influxOrganization: org
influxBucket: bucket
cloudadmin: admin
cloudpass: admin

3. Run the below to deploy it.
ansible-playbook system_deploy.yml
