### webApp install dependencies

#### Laravel App

ansible-playbook webapp/app-servers.yml --extra-vars "target=192.168.238.82 ansible_connection=ssh ansible_ssh_user=4052250 ansible_ssh_pass=Bes05836"

#### Wordpress App

ansible-playbook webapp/app-servers.yml --extra-vars "target=192.168.238.81 ansible_connection=ssh ansible_ssh_user=4052250 ansible_ssh_pass=Bes05836"

