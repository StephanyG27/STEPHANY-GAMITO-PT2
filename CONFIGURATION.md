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


