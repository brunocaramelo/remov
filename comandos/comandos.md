### webApp install dependencies

#### Laravel App

ansible-playbook -i 192.168.238.82, webapp/app-servers.yml -u 4052250  -kK -vvv

#### WP server

ansible-playbook -i 192.168.238.81,  webapp/app-servers.yml -u 4052250 -kK -vvv

#### Mysql

ansible-playbook -i 192.168.238.84,  mysql/ansible/playbook.yml -u 4052250 -kK -vvv

#### Redis

ansible-playbook -i 192.168.238.83,  redis/main.yml -u 4052250 -kK -vvv
