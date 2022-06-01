## Instação de ambiente

### Execução de passos

#### 1.0 Premissas

1 - Caso use Windows : Ansible instalado Com suporte do WSL
1 - Instalação nos servidores , pacote sshpass

#### 2.0 Instalação 
##### Redis

Observação:  alterar redis/vars.yml para definir a senha desejada

1 - Executar no host:

ansible-playbook -i 192.168.238.83,  redis/main.yml -u 4052250 -kK -vvv

##### Mysql

1 - Executar no host:

ansible-playbook -i 192.168.238.84,  mysql/ansible/playbook.yml -u 4052250 -kK -vvv

Pos instalação
 1 - executar no terminal : mysql_secure_installation
    1.1 definir parametros de segurança e senha do root
 2 - acessar como root
    1.1 - mysql -u root -p
    1.2 - executar comandos de criação de usuario
        1.2.1 CREATE USER 'usuarioapp'@'%' IDENTIFIED BY 'senha';
            GRANT ALL PRIVILEGES ON * . * TO 'usuarioapp'@'%' IDENTIFIED BY 'senha';
            FLUSH PRIVILEGES;

##### Backend

1 - Executar no host:

ansible-playbook -i 192.168.238.81,  webapp/backend-server.yml -u 4052250 -kK -vvv


Pos instalação
1 - Baixar aplicação no servidor
    1.1 cd /var/www/html/
    1.2 git clone  https://4052250:Bes05836@repositorios.banese.com.br/Banese/arpex-novoportal-backendbanese.git
2 - Alterar arquivo wp-config.php
    Alterar arquivos com dados da nova conexao com o banco de dados, como exemplo abaixo
    
    $connectstr_dbhost = 'hbes803.banese.com.br';
    $connectstr_dbname = 'hbes_wp_content';
    $connectstr_dbusername = 'sandbox';
    $connectstr_dbpassword = 'sandbox';

3 - Copiar arquivo de configuração web server
    3.1 - arquivo contido em: webapp/config/backend/000-default.conf
    3.1 - copiar para /etc/httpd/conf.d/000-default.conf no servidor

4 - Reiniciar servidor web
    4.1 - sudo systemctl restart httpd


##### Frontend

1 - Executar no host:

ansible-playbook -i 192.168.238.82, webapp/frontend-server.yml -u 4052250  -kK -vvv


Pos instalação
1 - Baixar aplicação no servidor
    1.1 cd /var/www/html/
    1.2 git clone  https://4052250:Bes05836@repositorios.banese.com.br/Banese/arpex-novoportal-internetbanese.git
2 - Enviar arquivo .env para a raiz do projeto
    3.1 - arquivo contido em: webapp/config/frontend/.env
    3.2 - alterar modelo com os novos dados 
    3.3 - enviar arquivo para : /var/www/html/arpex-novoportal-internetbanese/.env
    

3 - Copiar arquivo de configuração web server
    3.1 - arquivo contido em: webapp/config/frontend/000-default.conf
    3.1 - copiar para /etc/httpd/conf.d/000-default.conf no servidor

4 - Reiniciar servidor web
    4.1 - sudo systemctl restart httpd

    