#UBUNTU

1.- Primeramente vamos a instalar Apache, MySQL y PHP. Todo lo podemos instalar con este código:

$ sudo apt install apache2 php mysql-server mysql

1.1.- Si deseamos podemos correr unas pruebas para comprobar si todo quedo listo.

$ sudo service apache2 start

$ sudo service mysql start 

$ php ==version

2.- Para sacar la base de datos colocamos el siguiente comando:

$ cd /var/www/html

$ sudo git clone https://github.com/dgeti-cetis108/Programacion-M4S2-2018.git

3.- Ya aquí, nuestra base de datos va a tener el nombre de Programacion-M4S2-2018 y le vamos a cambiar el nombre a library.com

$ sudo mv Programacion-M4S2-2018 library.com

4.- Le vamos a agregar la base de datos a nuestro html.

$ cd library.com/db

$ sudo -i

mysql>source  /var/www/html/library.com/db/library.sql

5.- Ahora, vamos a crear un usuario y una contraseña.

mysql>create user ´brayan´@´localhost´ identified by ´123´;

6.- Una vez creada le damos permisos.

mysql>grant all on library.* to ´brayan´@´localhost´;

7.- Y ahora procedemos a salirnos de MySQL.

mysql>exit

8.- Comprobamos la conexión de mysql con nuestro nuevo usuario.

$ mysql -u brayan -p

9.- Editaremos nuestro library.com

$ sudo nano /var/www/html/library.com/classes/conexion.php

$ sudo apt install php-mysql

$ sudo service apache2 restart

10.- Modificamos nuestra IP para que al poner library.com nos redireccione.

c:\>windows\system32\drivers\etc\hosts

$ cd /etc/apache2/sities-available

$ sudo nano library.com.conf

<VirtualHost *:80>

​	ServerName "library.com"

​	ServerAlias "www.library.com"

​	Server Admin "brayan92_mp@hotmail.com"

​	DocumentRoot "/var/www/html/library.com"

​	ErrorLog "/var/log/library.com-error.log"

​	CustomLog "/var/log/library.com-access.log" common

"</VirtualHost>"

11.- Y ya para terminar agregamos los siguientes códigos para que funcione.

$ sudo a2ensite library.com

$ sudo service apache2 restart





