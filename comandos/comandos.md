### webApp install dependencies

#### Laravel App

ansible-playbook -i 192.168.238.82, webapp/app-servers.yml -u 4052250 -e "ansible_ssh_pass=Bes05836"

ansible-playbook -i 192.168.238.82,  webapp/app-servers.yml -u 4052250 -kK -vvv

#### Wordpress App

ansible-playbook -i 192.168.238.81,  webapp/app-servers.yml -u 4052250 -kK -vvv

#### Redis

ansible-playbook -i 192.168.238.83,  webapp/app-servers.yml -u 4052250 -kK -vvv
