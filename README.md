# Ansible_Meetup
This Project starts 4 Docker Container

+------------+
| Reverse    |
| Proxy      |
|            |
+------+-----+
       |
       |
       |         +-------------+
       |         |Wordpress    |
       +---------+             +------+   +--------------+
       |         |             |      |   |MySQL         |
       |         +-------------+      |   |              |
       |         +-------------+      +---+              |
       |         |OwnCloud     |      |   |              |
       +---------+             +------+   +--------------+
                 |             |
                 +-------------+

## Usage:
- Edit hosts file for your remote host
- Ensure you have access and sudo prvilege on your remote host
- run : ansible-playbook start.yml -e pass=<password> -e role=<role>

## Available Roles
- docker_del --> Deletes all the Containers
- docker_mod --> starts Container with the legacy ansible docker Module 
- docker_comp --> starts Container with Docker Compose
- docker_mod2 --> starts Container with docker_service and scales the owncloud/wodpress to 6 Coontainers

## Known Issues
- the database-settings for MySQL integration in Ownlcoud has to be done manually 
- Can be done like this:
  - docker exec -ti <mysql-container> bash
  - # mysql -u root -p -e "create database <db>;"
  - # mysql -u root -p -e "create user <user>@'%' identified by <db>;"
  - # mysql -u root -p -e "grant all on <db>.* to <user>@'%';
  - <ctlr> + d

