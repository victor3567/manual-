El primer paso que deberemos proceder a realizar es el de crear un contenedor, con el comando:

lxc launch ubuntu:20.04 "nombre del contenedor"

Una vez que lo tengamos el contenedor creado lo procederemos a abrir con el siguiente comando:
lxc  "nombre del contenedor"

A continuacion procedemos a convertirnos en root:
sudo -s

Despues de estos pasos hacemos un update para actualizar paquete:
apt update

Despues procedemos a instalar apache2:
apt install -y apache2

Como siguiente paso tenemos instalar la base de datod del mysql:
apt install -y mysql-serve

Acto seguido tendremos que instalar algunas bibliotecas:
apt install php libapache2-mod-php
apt install php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl

En este momento reiniciaremos el servidor para que se implementen todos los cambios que hemos hecho:
systemctl restart apache2

Una vez hecho procedemos a crear una base de datos dentro del mysql:
CREATE DATABASE bbdd;

CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'contraseña que le queramos poner';

En este momento seguiremos con la creación de un usuario en la base de datos previamente creada:
CREATE USER 'usuario'@'192.168.22.100' IDENTIFIED WITH mysql_native_password BY 'password';
