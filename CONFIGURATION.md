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

-Ahora se selecciona la versión PHP que desees.

```console
sudo update-alternatives --config php
```
0.![image](https://github.com/user-attachments/assets/8766b20d-a813-43c9-9e48-a48edc995a6e)



```console

```


