# 🖥️ Servidor Web
---
##### Fecha Creación: 15/09/2026
##### Fecha Actualizada: 26/10/2026
##### Ciclo formativo: DAW2
##### Alumno: Santiago González Vicente
---
#### 📑 Índice
- 1.[Instalación y configuración inicial](#1-instalación-y-configuración-inicial)
  - 1.1.[Configuración de la máquina virtual](#11-Configuración-de-la-máquina-virtual)
  - 1.2.[Instalación de Ubuntu](#12-Instalación-de-Ubuntu)
  - 1.3.[Configuración de red](#13-Configuración-de-red)
  - 1.4.[Configuración de la hora](#14-Configuración-de-la-hora)
  - 1.5.[Actualización del sistema](#15-Actualización-del-sistema)
  - 1.6.[Instalación y configuración de SSH](#16-Instalación-y-configuración-de-SSH)
  - 1.7.[Configuración del firewall UFW](#17-Configuración-del-firewall-UFW)
  - 1.8.[Instalación del antivirus](#18-Instalación-del-antivirus)
- 2.[Cuentas de administración](#2-Cuentas-de-administración)
  - 2.1.[Creación del usuario](#21-Creación-del-usuario)
  - 2.2.[Comprobación de grupos](#22-Comprobación-de-grupos)
  - 2.3.[Asignación de permisos administrativos](#23-Asignación-de-permisos-administrativos)
  - 2.4.[Comprobación de permisos](#24-Comprobación-de-permisos)
- 3.[Servidor web Apache y PHP](#3-Servidor-web-Apache-y-PHP)
  - 3.1.[Apertura del puerto HTTP](#31-Apertura-del-puerto-HTTP)
  - 3.2.[Instalación de Apache](#32-Instalación-de-Apache)
  - 3.2.[Instalación de PHP-FPM](#33-Instalación-de-PHP-FPM)
  - 3.2.[Configuración de PHP](#34-Configuración-de-PHP)
  - 3.2.[Configuración del registro de errores](#35-Configuración-del-registro-de-errores)
- 4.[Cuentas de desarrollo](4-Cuentas-de-desarrollo)
  - 4.1.[Creación del usuario](#41-Creación-del-usuario)
  - 4.2.[Asignación de contraseña](#42-Asignación-de-contraseña)
  - 4.3.[Cambio de propietario y grupo](#43-Cambio-de-propietario-y-grupo)
  - 4.4.[Configuración de permisos](#44-Configuración-de-permisos)
  - 4.5.[Comprobación del usuario y del directorio web](#45-Comprobación-del-usuario-y-del-directorio-web)
- 5.[Configuración de HTTPS](#5-Configuración-de-HTTPS)
  - 5.1.[Apertura del puerto HTTPS](#51-Apertura-del-puerto-HTTPS)
  - 5.2.[Creación de un certificado SSL autofirmado](#52-Creación-de-un-certificado-SSL-autofirmado)
  - 5.3.[Habilitación del módulo SSL](#53-Habilitación-del-módulo-SSL)
  - 5.4.[Configuración del sitio virtual seguro](#54-Configuración-del-sitio-virtual-seguro)
  - 5.5.[Activación del sitio virtual](#55-Activación-del-sitio-virtual)
  - 5.6.[Habilitación de mod_rewrite](#56-Habilitación-de-mod_rewrite)
  - 5.7.[Configuración de .htaccess](#57-Configuración-de-.htaccess)
- 6.[MariaDB y phpMyAdmin](#6-MariaDB-y-phpMyAdmin)
  - 6.1.[Instalación de MariaDB](#61-Instalación-de-MariaDB)
  - 6.2.[Comprobación del puerto](#62-Comprobación-del-puerto)
  - 6.3.[Configuración del acceso remoto](#63-Configuración-del-acceso-remoto)
  - 6.4.[Mantenimiento del servicio MariaDB](#64-Mantenimiento-del-servicio-MariaDB)
  - 6.5.[Creación de un usuario administrador](#65-Creación-de-un-usuario-administrador)
  - 6.6.[Seguridad de MariaDB](#66-Seguridad-de-MariaDB)
  - 6.7.[Instalación del módulo MySQL para PHP](#67-Instalación-del-módulo-MySQL-para-PHP)
  - 6.8.[Instalación de phpMyAdmin](#68-Instalación-de-phpMyAdmin)
- 7.[Chequeo final](#7-Chequeo-final)
  - 7.1.[Comprobación de las reglas del firewall](#71-Comprobación-de-las-reglas-del-firewall)
  - 7.2.[Eliminación de reglas innecesarias](#72-Eliminación-de-reglas-innecesarias)
  - 7.3.[Lista de comprobación final](#73-Lista-de-comprobación-final)
---

## 1. Instalación y configuración inicial

### 1.1. Configuración de la máquina virtual

Antes de comenzar la instalación, configura la máquina virtual con los siguientes parámetros:

*   **Nombre: SGV-USUD**
*   **Sistema operativo: Ubuntu Server.**
*   **Memoria RAM: 2 GB.**
*   **Disco duro: 500 GB.**
*   **ISO: imagen de instalación de Ubuntu.**
*   **Importante: desconecta la tarjeta de red de la máquina virtual durante la instalación inicial.**

### 1.2. Instalación de Ubuntu

Sigue estos pasos durante el proceso de instalación:

*   Selecciona el idioma Español.
*   Selecciona la opción predeterminada de Ubuntu.
*   No configures la red por el momento.
*   Continúa con las opciones predeterminadas hasta llegar a la configuración del almacenamiento.
*   Selecciona la opción Custom para crear las particiones manualmente.
*   Particionado del disco

Divide el disco de 500 GB en dos particiones:

| Partición | Tamaño | Sistema de archivos | Punto de montaje |
| --- | --- | --- | --- |
| Sistema | 150 GB | ext4 | / |
| Datos y servicios | Espacio restante | ext4 | /var |

Para crear cada partición:

*   Selecciona Espacio disponible.
*   Pulsa Add GPT Partition.
*   Selecciona el tamaño correspondiente.
*   Elige el formato ext4.
*   Establece el punto de montaje indicado.
*   Repite el proceso para la segunda partición.
*   Cuando termines, pulsa Hecho.

Finalización de la instalación

*   Introduce tu nombre.
*   Establece el nombre de la máquina.
*   Crea el primer usuario y su contraseña.
*   Continúa sin añadir SSH ni Ubuntu Pro.
*   Espera a que finalice la instalación.
*   Reinicia el servidor.
*   Cuando se solicite, pulsa Intro para expulsar la ISO de instalación.

### 1.3. Configuración de red

Edita el archivo de configuración de Netplan:

bash
``` bash
sudo nano /etc/netplan/00-installer-config.yaml
```

Configura la dirección IP siguiendo el esquema de red de tu entorno. La sintaxis y la indentación YAML deben ser correctas.
- **Parámetros para CLASE (IES Los Sauces):**
  - **Address (IP):** `10.199.9.184/22`
  - **Gateway (Puerta de enlace):** `10.199.8.1`
  - **Name servers (DNS):** `10.151.123.21, 10.151.126.21`

- **Parámetros para CASA:**
  - **Subnet:** `192.168.0.100/24`
  - **Address (IP):** `192.168.0.1/24`
  - **Gateway (Puerta de enlace):** `192.168.1.1`
  - **Name servers (DNS):** `8.8.8.8, 8.8.4.4`

Una vez guardado el archivo, aplica los cambios:

bash
``` bash
sudo netplan apply
```

Comprueba que tienes conectividad haciendo ping a otra máquina de la red:

bash
``` bash
ping DIRECCION_IP
```

Sustituye DIRECCION_IP por la dirección IP de la máquina que quieras comprobar.

### 1.4. Configuración de la hora

Configura la zona horaria de España:

bash
``` bash
sudo timedatectl set-timezone Europe/Madrid
```

Comprueba la fecha y la hora actuales:

bash
``` bash
date
```

También puedes consultar la configuración horaria mediante:

bash
``` bash
timedatectl
```

### 1.5. Actualización del sistema

Realiza este paso después de configurar la dirección IP y la hora.

Actualiza la lista de paquetes y los paquetes instalados:

bash
``` bash
sudo apt-get update -y && sudo apt-get upgrade -y
```
### 1.6. Instalación y configuración de SSH

Instala el servidor SSH:

bash
``` bash
sudo apt install openssh-server
```

Si aparecen errores relacionados con la descarga de paquetes, puedes probar:

bash
``` bash
sudo apt install openssh-server --fix-missing
```

Permite el tráfico SSH en el firewall:

bash
``` bash
sudo ufw allow 22/tcp
```

Comprueba el estado del servicio:

bash
``` bash
sudo systemctl status ssh
```

Finalmente, intenta conectarte desde otra máquina:

bash
``` bash
ssh usuario@DIRECCION_IP
```

Sustituye usuario y DIRECCION_IP por los datos de tu servidor.

### 1.7. Configuración del firewall UFW

Activa el firewall:

bash
``` bash
sudo ufw enable
```

Permite las conexiones SSH:

bash
``` bash
sudo ufw allow 22/tcp
```

Comprueba las reglas activas y sus detalles:

bash
``` bash
sudo ufw status verbose
```

Los puertos adicionales se habilitarán a medida que se instalen y configuren los servicios.

### 1.8. Instalación del antivirus

Instala ClamAV y su servicio en segundo plano:

bash
``` bash
sudo apt install clamav clamav-daemon -y
```

Actualiza las definiciones de virus:

bash
``` bash
sudo freshclam
```

Inicia y habilita el servicio de actualización automática:

bash
``` bash
sudo systemctl start clamav-freshclam
sudo sytemctl enable clamav-freshclam
```

## 2. Cuentas de administración

En este apartado se creará una cuenta administrativa llamada miadmin2.

### 2.1. Creación del usuario

Crea el usuario:

bash
``` bash
sudo adduser miadmin2
```

Introduce la contraseña:

text
paso


Completa los datos adicionales que solicite el sistema.

### 2.2. Comprobación de grupos

Consulta los grupos del usuario actual:

bash
``` bash
sudo id
```

En la salida, busca el apartado groups= para identificar los grupos a los que pertenece.

### 2.3. Asignación de permisos administrativos

Añade el usuario miadmin2 a los grupos indicados:

bash
``` bash
sudo usermod -aG sudo,dip,adm,cdrom,plugdev,lxd miadmin2
```
### 2.4. Comprobación de permisos

Cambia a la cuenta creada:

bash
``` bash
sudo su - miadmin2
```

Comprueba los permisos disponibles:

bash
``` bash
sudo -l
```

El resultado permite verificar qué comandos puede ejecutar el usuario mediante sudo.

## 3. Servidor web Apache y PHP
### 3.1. Apertura del puerto HTTP

Permite el tráfico HTTP en el firewall:

bash
``` bash
sudo ufw allow 80/tcp
```
### 3.2. Instalación de Apache

Instala Apache:

bash
``` bash
sudo apt install apache2 --fix-missing
```

Comprueba el estado del servicio:

bash
``` bash
sudo systemctl status apache2
```

Si el servicio está activo, abre un navegador desde otra máquina e introduce la dirección IP del servidor.

Deberías visualizar la página predeterminada de Apache o el contenido del archivo index que hayas configurado.

### 3.3. Instalación de PHP-FPM

Instala PHP-FPM:

bash
``` bash
sudo apt install php8.5-fpm
```

Habilita la configuración de PHP-FPM y los módulos necesarios de Apache:

bash
``` bash
sudo a2enconf php8.5-fpm
sudo a2nmod proxy_fcgi setenvif
```

Recarga Apache para aplicar los cambios:

bash
``` bash
sudo systemctl reload apache2
```
Nota: comprueba que la versión 8.5 está disponible en los repositorios de tu sistema. La versión de PHP debe coincidir con los paquetes y las rutas instalados.
### 3.4. Configuración de PHP

Abre el archivo de configuración de PHP-FPM:

bash
``` bash
sudo nano /etc/php/8.5/fpm/php.ini
```

Utiliza Ctrl + W para buscar las directivas que debas modificar o comprobar.

Guarda los cambios y reinicia PHP-FPM:

bash
``` bash
sudo systemctl restart php8.5-fpm
```
### 3.5. Configuración del registro de errores

Crea el archivo de registro:

bash
``` bash
sudo touch /var/log/php_errors.log
```

Asigna como propietario y grupo a www-data:

bash
``` bash
sudo chown www-data:www-data /var/log/php_errors.log
```

Comprueba que las directivas de registro de errores de php.ini apuntan al archivo correspondiente si deseas utilizarlo para registrar los errores de PHP.
## 4. Cuentas de desarrollo

En este apartado se crea la cuenta operadorweb, destinada a trabajar con los archivos del sitio web.

### 4.1. Creación del usuario

Crea el usuario sin generar automáticamente un directorio personal y establece /var/www/html como directorio de trabajo:

bash
``` bash
sudo useradd -M -d /var/www/html -g www-data -s /bin/bash operadorweb
```
### 4.2. Asignación de contraseña

Establece la contraseña del usuario:

bash
``` bash
sudo passwd operadorweb
```

Introduce la contraseña correspondiente.

### 4.3. Cambio de propietario y grupo

Asigna la propiedad del directorio web al usuario operadorweb y al grupo www-data:

bash
``` bash
sudo chown -R operadorweb:www-data /var/www/html
```
### 4.4. Configuración de permisos

Establece permisos de lectura, escritura y ejecución para el propietario y el grupo:

bash
``` bash
sudo chmod -R 775 /var/www/html
```

Con esta configuración:

* Propietario: puede leer, escribir y acceder a los directorios.
* Grupo: puede leer, escribir y acceder a los directorios.
* Otros usuarios: pueden leer y acceder, pero no modificar los archivos.

### 4.5. Comprobación del usuario y del directorio web

Cambia a la cuenta de desarrollo:

bash
``` bash
su - operadorweb
```

Comprueba el contenido del directorio web:

bash
``` bash
cd /var/www/html
ls -l
```


Si el usuario existe y tiene acceso al directorio, podrás trabajar con los archivos del sitio web según los permisos asignados.

## 5. Configuración de HTTPS
### 5.1. Apertura del puerto HTTPS

Permite el tráfico HTTPS:

bash
``` bash
sudo ufw allow 443/tcp
```
### 5.2. Creación de un certificado SSL autofirmado

Genera una clave privada y un certificado autofirmado con una validez de 365 días:

bash
``` bash
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-keyout
```/etc/ssl/private/apache-selfsigned.key \
-out /etc/ssl/certs/apache-selfsigned.crt


Durante el proceso, OpenSSL solicitará varios datos:

Campo	Valor
Country Name	ES para España
State or Province Name	Provincia o comunidad correspondiente
Locality Name	Nombre de la localidad
Organization Name	Nombre de la organización, preferiblemente en mayúsculas
Organizational Unit Name	Departamento, por ejemplo IT Department, o dejarlo vacío
Common Name	Dominio, nombre del servidor o dirección IP correspondiente
Email Address	Puede dejarse vacío

El campo Common Name no debe contener espacios en blanco.

Nota de seguridad: al ser un certificado autofirmado, el navegador mostrará una advertencia de confianza. Para un servicio público o de producción, utiliza un certificado emitido por una autoridad certificadora reconocida.
### 5.3. Habilitación del módulo SSL

Activa el módulo SSL de Apache:

bash
``` bash
sudo a2enmod ssl
```
### 5.4. Configuración del sitio virtual seguro

Realiza una copia de seguridad del archivo de configuración original:

bash
``` bash
sudo cp /etc/apache2/sites-available/default-ssl.conf \
/etc/ap
```che2/sites-available/defaultsafecopy-ssl.conf


Edita el archivo de configuración SSL:

bash
``` bash
sudo nano /etc/apache2/sites-available/default-ssl.conf
```

Configura el sitio virtual para utilizar HTTPS:

apache
<VirtualHost *:443>
    ServerName your_domain_or_ip
    DocumentRoot /var/www/your_ip

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/apache-selfsigned.crt
    SSLCertificateKeyFile /etc/ssl/private/apache-selfsigned.key
</VirtualHost>


Sustituye your_domain_or_ip y /var/www/your_ip por los valores que correspondan a tu servidor y a la ubicación real de tu sitio web.

### 5.5. Activación del sitio virtual

Activa el sitio SSL:

bash
``` bash
sudo a2ensite default-ssl.conf
```

Comprueba que la configuración no contiene errores:

bash
``` bash
sudo apache2ctl configtest
```

Si la configuración es correcta, recarga Apache:

bash
``` bash
sudo systemctl reload apache2
```
### 5.6. Habilitación de mod_rewrite

Activa el módulo de reescritura de Apache:

bash
``` bash
sudo a2enmod rewrite
```
### 5.7. Configuración de .htaccess

Accede al directorio web:

bash
``` bash
cd /var/www/html
```

Cambia al usuario de desarrollo:

bash
``` bash
sudo su - operadorweb
```

Crea o edita el archivo .htaccess:

bash
``` bash
nano /var/www/html/.htaccess
```

Configuración original de redirección:

``` bash
apache
RewriteEngine On
RewriteCond %{SERVER_PORT} 80
RewriteRule ^(.*)$ 10.199.9.174/$1 [R,L]
```

Asegúrate de que el sitio HTTPS funciona antes de habilitar una redirección permanente.

## 6. MariaDB y phpMyAdmin
### 6.1. Instalación de MariaDB

Actualiza los repositorios e instala MariaDB:

bash
``` bash
sudo apt update &&
sudo apt install mariadb-server -y
``` 
### 6.2. Comprobación del puerto

MariaDB utiliza normalmente el puerto TCP 3306.

Comprueba los sockets y puertos asociados al servicio:

bash
``` bash
sudo ss -lntp | grep 3306
```

También puedes consultar los procesos relacionados con MariaDB:

bash
``` bash
sudo ss -punta | grep mariadb
```
### 6.3. Configuración del acceso remoto

Edita el archivo de configuración:

bash
``` bash
sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf
```

Localiza la directiva:

ini
``` bash
bind-address = 127.0.0.1
```

Para permitir que MariaDB escuche en todas las interfaces, cámbiala por:

ini
``` bash
bind-address = 0.0.0.0
```


Guarda el archivo y reinicia el servicio:

bash
``` bash
sudo systemctl restart mariadb
```

Advertencia de seguridad: 0.0.0.0 permite escuchar en todas las interfaces de red. El acceso remoto debe limitarse mediante el firewall, las cuentas de usuario y las reglas de red. No expongas el puerto 3306 a Internet sin las medidas de seguridad adecuadas.
### 6.4. Mantenimiento del servicio MariaDB

Consulta el estado del servicio:

bash
``` bash
sudo systemctl status mariadb
```

Inicia el servicio:

bash
``` bash
sudo systemctl start mariadb
```

Reinicia el servicio:

bash
``` bash
sudo systemctl restart mariadb
```

Habilita el inicio automático:

bash
``` bash
sudo systemctl enable mariadb
```
### 6.5. Creación de un usuario administrador

Entra en la consola de MariaDB:

bash
``` bash
sudo mariadb
```

Crea el usuario adminsql:

sql
``` bash
CREATE USER 'adminsql'@'%' IDENTIFIED BY 'paso';
```


Asigna privilegios administrativos globales:

sql
``` bash
GRANT ALL ON *.* TO 'adminsql'@'%' WITH GRANT OPTION;
```


Sal de la consola:

sql
``` bash
EXIT;
```

Importante: el usuario 'adminsql'@'%' puede conectarse desde cualquier host que sea accesible y cumpla el resto de las condiciones. La contraseña paso es únicamente un ejemplo de laboratorio; utiliza una contraseña robusta y limita el origen de las conexiones siempre que sea posible.

### 6.6. Seguridad de MariaDB

Ejecuta el asistente de seguridad:

bash
``` bash
sudo mariadb-secure-installation
```

Sigue las indicaciones para reforzar la configuración del servidor.

Contraseña actual de root: pulsa Enter si todavía no hay una contraseña configurada y el sistema la solicita.
Establecer contraseña de root: configura una contraseña si el método de autenticación utilizado lo permite y el asistente lo solicita.
Eliminar usuarios anónimos: responde Sí.
Deshabilitar el acceso remoto de root: responde Sí.
Eliminar la base de datos de prueba: responde Sí.
Recargar las tablas de privilegios: responde Sí.

Las preguntas concretas pueden variar según la versión de MariaDB y el método de autenticación configurado.

### 6.7. Instalación del módulo MySQL para PHP

Instala el módulo necesario para conectar PHP con MariaDB/MySQL:

bash
``` bash
sudo apt install php8.5-mysql
```

Reinicia PHP-FPM:

bash
``` bash
sudo systemctl restart php8.5-fpm
```
### 6.8. Instalación de phpMyAdmin

Instala phpMyAdmin y sus dependencias:

bash
``` bash
sudo apt install phpmyadmin php-mbstring php-zip php-gd php-json php-curl --fix-missing -y
```

Durante la instalación:

Selección del servidor web: selecciona apache2.
Si apache2 aparece resaltado, pero todavía no está seleccionado, pulsa Espacio para marcarlo. Después pulsa Tab y Enter para continuar.
Configuración de la base de datos: selecciona Yes cuando se pregunte si deseas utilizar dbconfig-common.
Contraseña de la aplicación: introduce y confirma la contraseña que utilizará phpMyAdmin para acceder a su base de datos de configuración.

Puedes utilizar paso únicamente en un entorno de prácticas aislado; en cualquier otro caso, utiliza una contraseña robusta.

Una vez terminada la instalación, comprueba que Apache, PHP-FPM y MariaDB funcionan correctamente.

## 7. Chequeo final
### 7.1. Comprobación de las reglas del firewall

Muestra las reglas de UFW con sus números:

bash
``` bash
sudo ufw status numbered
```

Revisa los puertos permitidos y comprueba que solo estén abiertos los necesarios.

En este servidor se utilizan, como mínimo, los siguientes puertos según los servicios habilitados:

Puerto	Protocolo	Servicio
22	TCP	SSH
80	TCP	HTTP
443	TCP	HTTPS
3306	TCP	MariaDB, si se permite el acceso remoto
### 7.2. Eliminación de reglas innecesarias

Si aparecen reglas IPv6 duplicadas que deseas eliminar, identifica primero el número de la regla:

bash
``` bash
sudo ufw status numbered
```

Después, elimina la regla correspondiente:

bash
``` bash
sudo ufw delete NUMERO
```

Sustituye NUMERO por el identificador real de la regla.

Importante: no elimines automáticamente todas las reglas IPv6. IPv6 puede ser necesario para el funcionamiento normal de la red. Elimina únicamente las reglas que hayas confirmado que no necesitas.
### 7.3. Lista de comprobación final
Ubuntu está instalado y actualizado.
Las particiones / y /var están configuradas.
La dirección IP y la zona horaria son correctas.
SSH está instalado y permite conexiones desde otra máquina.
UFW está activo y contiene las reglas necesarias.
ClamAV está instalado y actualizado.
El usuario miadmin2 dispone de los permisos administrativos previstos.
Apache está instalado y sirve la página web.
PHP-FPM está instalado y configurado.
HTTPS funciona con el certificado configurado.
MariaDB está instalado y protegido.
phpMyAdmin está instalado.
El usuario operadorweb puede trabajar con el directorio web.
Los puertos y las reglas del firewall han sido revisados.
