# STEPHANY-GAMITO-PT2

## Instalación y configuración de OwnCloud

### Instalación y configuración de la maquina, servidor, librerias...

-Para comenzar he creado una máquina de ISARDVDI llamada "Práctica OwnCloud".

![image](https://github.com/user-attachments/assets/1f7e4d17-1ec0-46d3-b93f-62a65b6d7faf)

-Dentro de la máquina, lo primero es actualizar la maquina.
```console
sudo apt update
```
```console
sudo apt upgrade
```
![image](https://github.com/user-attachments/assets/065f8747-8fd0-4ba4-80b0-01710c2f5e21)
![image](https://github.com/user-attachments/assets/7c8b19e0-f95d-4ea9-b837-729a0386544e)

-Una vez actualizado, lo siguiente es instalar el servidor web "apache2".
```console
sudo apt install -y apache2
```
![image](https://github.com/user-attachments/assets/d07b9666-877d-4da3-b755-724cd6a4e563)

-Ahora hay que instalar el servidor de la base de datos "mysql".
```console
sudo apt install -y mysql-server
```
![image](https://github.com/user-attachments/assets/9c3dd9aa-f9d8-4809-8c22-d45024a78257)

-Ahora lo siguiente sería la instalación de algunas librerias de "php".
```console
sudo apt install -y php libapache2-mod-php
```
```console
sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl
```
![image](https://github.com/user-attachments/assets/2db19255-b51f-431d-b677-48f200a52226)
![image](https://github.com/user-attachments/assets/b8760ae0-db12-4e1e-8e9c-5848a789ee48)

-Ya instalado solo falta reiniciar el servidor de "apache2".
```console
sudo systemctl restart apache2
```
![image](https://github.com/user-attachments/assets/abe8d21d-31ba-4cfc-930a-8b00f9eb3d2b)


### Configuración de MySQL

-Ahora toca acceder a la consola desde terminal, para esto debes ser "root".
```console
sudo mysql
```
![image](https://github.com/user-attachments/assets/31fb4489-bb6a-480c-b5f6-ea8ab6f7545e)

-Ahora que ya estamos dentro de la consola, es momento de crear una base de datos llamada "bbdd".

```console
CREATE DATABASE bbdd;
```
![image](https://github.com/user-attachments/assets/1cc22bc1-6245-4255-b9ea-ee68094b9d5a)

-Ahora toca crear el usuario.

```console
CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

![image](https://github.com/user-attachments/assets/3bc8a58b-6fc7-42e9-946e-94629947f607)

-Una vez creado, damos todos los privilegios al usuario "localhost".
```console
GRANT ALL ON bbdd.* to 'usuario'@'localhost';
```
![image](https://github.com/user-attachments/assets/c22feabd-4c83-49f6-a287-c682dc7397bb)

-Y ya concedidos los permisos salimos de la consola.

```console
exit
```
![image](https://github.com/user-attachments/assets/aa7a1d71-32a1-4139-9d8c-0841d307e18e)

-Ahora toca probar si se puede conectar a la base sin privilegios.
```console
mysql -u usuario -p
```

![image](https://github.com/user-attachments/assets/6234d50d-e783-497e-91f4-540b1e7dc437)


## Descarga de Owncloud

-He descargado Owncloud desde este link.
```console
https://download.owncloud.com/server/stable/owncloud-complete-20240724.zip
```
![image](https://github.com/user-attachments/assets/90920df7-79a9-48f1-b72d-7fb5562420ff)

-Una vez descargado el zip, lo primero será instalar los requisitos previos de PPA.

```console
sudo apt install software-properties-common -y
```
![image](https://github.com/user-attachments/assets/ea81d030-eba8-4045-82cf-f68698acb2bf)

-Lo siguiente es la instalación de las herramientas para trabajar con los archivos PPA.

```console
LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y
```
![image](https://github.com/user-attachments/assets/bb597bf0-1440-4a7a-9c52-5619f3fb2184)

-Ahora se debe volver a actualizar los repositorios.

```console
sudo apt update
```
![image](https://github.com/user-attachments/assets/caf91ffe-d56a-4c5d-b8bb-0b0f874863c2)

-Una vez actualizado, se instala las librerias de PHP en su versión 7.4.

```console
sudo apt install php7.4 -y
```
![image](https://github.com/user-attachments/assets/c36176ec-326b-4097-a6ca-4c11b0e0c4c7)

```console
sudo apt install -y php libapache2-mod-php7.4
```
![image](https://github.com/user-attachments/assets/bd3533ef-9394-4ef4-b818-a1237d2acfd7)

```console
sudo apt install -y php7.4-fpm php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl
```
![image](https://github.com/user-attachments/assets/07d454b2-094e-4a90-93b9-48c8ae4b501b)

-Ahora se selecciona la versión PHP que desees, en mi caso escogí el 2.

```console
sudo update-alternatives --config php
```
![image](https://github.com/user-attachments/assets/8766b20d-a813-43c9-9e48-a48edc995a6e)

-Ahora toca activar los módulos de apache2.

```console
sudo a2enmod proxy_fcgi setenvif
```

```console
sudo a2enconf php7.4-fpm
```

![image](https://github.com/user-attachments/assets/27c72968-3b30-4be4-b8d4-ad45fd823ac1)

-Y se reinicia apache2.

```console
sudo service apache2 restart
```

## Descompresión del archivo a la carpeta /var/www/html

-Lo primero es ir al directorio de /var/www/html y descomprimir los archivos del zip.
Es importante cambiar "Baixades" por "Descargas" y "app-web" por el nombre de la carpeta.

```console
sudo cp ~/Baixades/app-web.zip /var/www/html
```

![image](https://github.com/user-attachments/assets/8342eaa7-d81d-43c0-b147-9b5201bd8d3c)

-Ahora vamos al directorio /var/www/html y dentro descomprimimos el fichero, cambiando "app-web" al igual que antes.

```console
cd /var/www/html
```
![image](https://github.com/user-attachments/assets/fb40328b-8b2e-4471-99c0-6cbaed02ef5b)


```console
sudo unzip app-web.zip
```
![image](https://github.com/user-attachments/assets/22210cf8-eea4-4ad4-a058-165119ef310c)


-Ahora se copia los ficheros a la carpeta de /var/www/html y luego se elimina la carpeta donde hemos hecho el unzip.

```console
sudo cp -R app-web/. /var/www/html
```
![image](https://github.com/user-attachments/assets/2d8b275c-152b-4158-9eec-43390163435f)


```console
sudo rm -rf app-web/
```
![image](https://github.com/user-attachments/assets/c015b17f-4674-4a7a-af2a-b29ca346c84e)

-Ahora tocaría eliminar el fichero de index.html de apache2.

```console
sudo rm -rf /var/www/html/index.html
```
![image](https://github.com/user-attachments/assets/6bc21109-ad24-4ffd-a7c1-2d08a1570f7b)


## Aplicar permisos a la aplicación web.

-Aplicaremos permisos al directorio /var/www/html


```console
cd /var/www/html
```

```console
sudo chmod -R 775 .
```
```console
sudo chown -R usuario:www-data .
```
![image](https://github.com/user-attachments/assets/f6ec6243-f9e5-49fb-ad9b-499f1d1c4d8b)

-Y ahora tocaría entrar en el navegador y entramos a la dirección de http://localhost/ y se configura la cloud.

![image](https://github.com/user-attachments/assets/8a758a78-fa0b-4919-9376-49f0fbf8d0a8)

-La información a poner es la siguiente:

* **usuario:** usuario
* **contraseña:** password
* **base de datos:** bbdd
* **dominio:** localhost

![image](https://github.com/user-attachments/assets/5056b458-fa83-441f-8718-085868d02306)
![image](https://github.com/user-attachments/assets/bc1d4a45-d86e-4a9b-9770-d8776305a993)
![image](https://github.com/user-attachments/assets/b05c6cd3-c4b4-40c3-97e8-d3784d7ca0d5)

## Subir archivos a Owncloud

-Ya dentro, subiremos los archivos en carpetas para mantener el espacio organizado.
Nos dirigiremos al + y en el símbolo de carpeta escribiremos un nombre.
![image](https://github.com/user-attachments/assets/615a75a2-e187-44a3-a066-b89471324130)
![image](https://github.com/user-attachments/assets/15a482b6-c472-45a0-b868-35a7602d436e)
![image](https://github.com/user-attachments/assets/cfd84c3a-81da-4ba5-abe4-4a288e02035f)
![image](https://github.com/user-attachments/assets/1f2abb3f-cd78-4a3f-8f2d-d760b8d17b28)

-Ahora compartiremos el enlace de la carpeta a otros usuarios, añadiendole una fecha de caducidad por precaución.
![image](https://github.com/user-attachments/assets/55e292e6-6a78-47a8-ac54-d41c277d0c82)


-Crearemos 3 usuarios con roles distintos (admin, editor y visualizador) desde el desplegable. 

![image](https://github.com/user-attachments/assets/d221a223-1251-483a-9141-25f0bb342da3)

![image](https://github.com/user-attachments/assets/64eb6123-e3b3-4c1d-b053-8a13b5a5d697)

-Una vez creados, procederemos a crear los respectivos grupos y a asignar usuarios dentro de ellos.

![image](https://github.com/user-attachments/assets/27b646c2-25a1-4221-b208-843a991ee9eb)

![image](https://github.com/user-attachments/assets/99f4cf77-60c5-4e56-bde7-d1dad09bc0ee)



