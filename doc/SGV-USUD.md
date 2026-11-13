# 🖥️ Servidor Web
---
##### Fecha Creación: 15/09/2026
##### Fecha Actualizada: 26/10/2026
##### Ciclo formativo: DAW2
##### Alumno: Santiago González Vicente
---
#### 📑 Índice
- [🖥️ Servidor Web](#️-servidor-web)
        - [Fecha Creación: 15/09/2026](#fecha-creación-15092026)
        - [Fecha Actualizada: 26/10/2026](#fecha-actualizada-26102026)
        - [Ciclo formativo: DAW2](#ciclo-formativo-daw2)
        - [Alumno: Santiago González Vicente](#alumno-santiago-gonzález-vicente)
      - [📑 Índice](#-índice)
  - [1. Instalación y configuración inicial](#1-instalación-y-configuración-inicial)
    - [1.1. Configuración de la máquina virtual](#11-configuración-de-la-máquina-virtual)
    - [1.2. Instalación de Ubuntu](#12-instalación-de-ubuntu)
    - [1.3. Configuración de red](#13-configuración-de-red)
    - [1.4. Configuración de la hora](#14-configuración-de-la-hora)
    - [1.5. Actualización del sistema](#15-actualización-del-sistema)
  - [2. SSH](#2-ssh)
  - [3. UFW](#3-ufw)
  - [4. ClamAV](#4-clamav)
  - [5. Cuentas de administración](#5-cuentas-de-administración)
    - [5.1. Creación del usuario](#51-creación-del-usuario)
    - [5.2. Comprobación de grupos](#52-comprobación-de-grupos)
    - [5.3. Asignación de permisos administrativos](#53-asignación-de-permisos-administrativos)
    - [5.4. Comprobación de permisos](#54-comprobación-de-permisos)
  - [6. Usuarios Enjaulados](#6-usuarios-enjaulados)
    - [6.1 Creación de Grupo](#61-creación-de-grupo)
    - [6.2 Creacion de Usuario Y cambio de contraseña](#62-creacion-de-usuario-y-cambio-de-contraseña)
  - [7. Servidor web Apache](#7-servidor-web-apache)
    - [7.1. Apertura del puerto HTTP](#71-apertura-del-puerto-http)
    - [7.2. Instalación de Apache](#72-instalación-de-apache)
    - [3.2. Registro de errores y página para errores 404](#32-registro-de-errores-y-página-para-errores-404)
  - [8. PHP FPM](#8-php-fpm)
    - [8.1. Configuración de PHP](#81-configuración-de-php)
    - [8.2. Configuración del registro de errores](#82-configuración-del-registro-de-errores)
  - [9. Cuentas de desarrollo](#9-cuentas-de-desarrollo)
    - [9.1. Creación del usuario](#91-creación-del-usuario)
    - [9.2. Asignación de contraseña](#92-asignación-de-contraseña)
    - [9.3. Cambio de propietario y grupo](#93-cambio-de-propietario-y-grupo)
    - [9.4. Configuración de permisos](#94-configuración-de-permisos)
    - [9.5. Comprobación del usuario y del directorio web](#95-comprobación-del-usuario-y-del-directorio-web)
  - [10. Configuración de HTTPS](#10-configuración-de-https)
    - [10.1. Apertura del puerto HTTPS](#101-apertura-del-puerto-https)
    - [10.2. Creación de un certificado SSL autofirmado](#102-creación-de-un-certificado-ssl-autofirmado)
    - [10.3. Habilitación del módulo SSL](#103-habilitación-del-módulo-ssl)
    - [10.4. Configuración del sitio virtual seguro](#104-configuración-del-sitio-virtual-seguro)
    - [10.5. Activación del sitio virtual](#105-activación-del-sitio-virtual)
    - [10.6. Habilitación de mod\_rewrite](#106-habilitación-de-mod_rewrite)
    - [10.7. Havilitar AllowOverdrive apache](#107-havilitar-allowoverdrive-apache)
    - [10.8. Configuración de .htaccess](#108-configuración-de-htaccess)
  - [11. Pagina Error apache](#11-pagina-error-apache)
  - [11. MariaDB y phpMyAdmin](#11-mariadb-y-phpmyadmin)
    - [11.1. Instalación de MariaDB](#111-instalación-de-mariadb)
    - [11.2. Comprobación del puerto](#112-comprobación-del-puerto)
    - [11.3. Configuración del acceso remoto](#113-configuración-del-acceso-remoto)
    - [11.4. Mantenimiento del servicio MariaDB](#114-mantenimiento-del-servicio-mariadb)
    - [11.5. Creación de un usuario administrador](#115-creación-de-un-usuario-administrador)
    - [11.6. Seguridad de MariaDB](#116-seguridad-de-mariadb)
    - [11.7. Instalación del módulo MySQL para PHP](#117-instalación-del-módulo-mysql-para-php)
    - [11.8. Instalación de phpMyAdmin](#118-instalación-de-phpmyadmin)
  - [12. Xdebug](#12-xdebug)
    - [12.1 Instalacion](#121-instalacion)
  - [13. Chequeo final](#13-chequeo-final)
    - [13.1. Comprobación de las reglas del firewall](#131-comprobación-de-las-reglas-del-firewall)
    - [13.2. Eliminación de reglas innecesarias](#132-eliminación-de-reglas-innecesarias)
    - [13.3. Modulos Apache](#133-modulos-apache)
    - [13.4. Modulos PHP](#134-modulos-php)
    - [13.2. Eliminación de reglas innecesarias](#132-eliminación-de-reglas-innecesarias-1)
    - [13.3. Lista de comprobación final](#133-lista-de-comprobación-final)

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

| Partición         | Tamaño           | Sistema de archivos | Punto de montaje |
| ----------------- | ---------------- | ------------------- | ---------------- |
| Sistema           | 150 GB           | ext4                | /                |
| Datos y servicios | Espacio restante | ext4                | /var             |

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
## 2. SSH

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

## 3. UFW

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

## 4. ClamAV

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

## 5. Cuentas de administración

En este apartado se creará una cuenta administrativa llamada miadmin2.

### 5.1. Creación del usuario

Crea el usuario:

bash
``` bash
sudo adduser miadmin2
```

Introduce la contraseña:

text
paso


Completa los datos adicionales que solicite el sistema.

### 5.2. Comprobación de grupos

Consulta los grupos del usuario actual:

bash
``` bash
sudo id
```

En la salida, busca el apartado groups= para identificar los grupos a los que pertenece.

### 5.3. Asignación de permisos administrativos

Añade el usuario miadmin2 a los grupos indicados:

bash
``` bash
sudo usermod -aG sudo,dip,adm,cdrom,plugdev,lxd miadmin2
```
### 5.4. Comprobación de permisos

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

## 6. Usuarios Enjaulados

### 6.1 Creación de Grupo

Primero Creamos el Grupo con:
``` bash
sudo addgroup sftpusers
```

### 6.2 Creacion de Usuario Y cambio de contraseña
Utilizamos este comando
``` bash
sudo useradd -g www-data -G sftpusers -m -d /var/www/enjaulado1 enjaulado1
```

Ponemos la contraseña, la contraseña es paso
``` bash
sudo passwd enjaulado1
```

## 7. Servidor web Apache

### 7.1. Apertura del puerto HTTP

Permite el tráfico HTTP en el firewall:

bash
``` bash
sudo ufw allow 80/tcp
```
### 7.2. Instalación de Apache

Instala Apache:


``` bash
sudo apt install apache2 --fix-missing
```

Comprueba el estado del servicio:


``` bash
sudo systemctl status apache2
```

Si el servicio está activo, abre un navegador desde otra máquina e introduce la dirección IP del servidor.

Deberías visualizar la página predeterminada de Apache o el contenido del archivo index que hayas configurado.

### 3.2. Registro de errores y página para errores 404

Se crea un directorio para guardar los archivos relacionados con los errores:

``` bash
sudo mkdir /var/www/html/error
sudo touch /var/www/html/error/error.log
```
Antes de modificar la configuración del sitio web predeterminado, se guarda una copia del archivo original:

``` bash
cd /etc/apache2/sites-available
sudo cp 000-default.conf 000-default.conf.backup
sudo nano 000-default.conf
```

Dentro del bloque <VirtualHost *:80>, se añaden o se modifican estas directivas:

``` bash
ErrorLog /var/www/html/error/error.log
ErrorDocument 404 /error/404.html
```
ErrorLog indica dónde se guardan los errores de Apache. ErrorDocument 404 establece la página que se mostrará cuando no se encuentre el recurso solicitado. Para que esta última directiva funcione como se espera, debe existir el archivo /var/www/html/error/404.html.

## 8. PHP FPM

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
### 8.1. Configuración de PHP

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
### 8.2. Configuración del registro de errores

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
## 9. Cuentas de desarrollo

En este apartado se crea la cuenta operadorweb, destinada a trabajar con los archivos del sitio web.

### 9.1. Creación del usuario

Crea el usuario sin generar automáticamente un directorio personal y establece /var/www/html como directorio de trabajo:

bash
``` bash
sudo useradd -M -d /var/www/html -g www-data -s /bin/bash operadorweb
```
### 9.2. Asignación de contraseña

Establece la contraseña del usuario:

bash
``` bash
sudo passwd operadorweb
```

Introduce la contraseña correspondiente.

### 9.3. Cambio de propietario y grupo

Asigna la propiedad del directorio web al usuario operadorweb y al grupo www-data:

bash
``` bash
sudo chown -R operadorweb:www-data /var/www/html
```
### 9.4. Configuración de permisos

Establece permisos de lectura, escritura y ejecución para el propietario y el grupo:

bash
``` bash
sudo chmod -R 775 /var/www/html
```

Con esta configuración:

* Propietario: puede leer, escribir y acceder a los directorios.
* Grupo: puede leer, escribir y acceder a los directorios.
* Otros usuarios: pueden leer y acceder, pero no modificar los archivos.

### 9.5. Comprobación del usuario y del directorio web

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

## 10. Configuración de HTTPS
### 10.1. Apertura del puerto HTTPS

Permite el tráfico HTTPS:

bash
``` bash
sudo ufw allow 443/tcp
```
### 10.2. Creación de un certificado SSL autofirmado

Genera una clave privada y un certificado autofirmado con una validez de 365 días:

bash
``` bash
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/apache-selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt
```

Durante el proceso, OpenSSL solicitará varios datos:

``` bash
Campo	Valor
Country Name	ES para España
State or Province Name	Provincia o comunidad correspondiente
Locality Name	Nombre de la localidad
Organization Name	Nombre de la organización, preferiblemente en mayúsculas
Organizational Unit Name	Departamento, por ejemplo IT Department, o dejarlo vacío
Common Name	Dominio, nombre del servidor o dirección IP correspondiente
Email Address	Puede dejarse vacío
```

El campo Common Name no debe contener espacios en blanco.

Nota de seguridad: al ser un certificado autofirmado, el navegador mostrará una advertencia de confianza. Para un servicio público o de producción, utiliza un certificado emitido por una autoridad certificadora reconocida.
### 10.3. Habilitación del módulo SSL

Activa el módulo SSL de Apache:

bash
``` bash
sudo a2enmod ssl
```
### 10.4. Configuración del sitio virtual seguro

Realiza una copia de seguridad del archivo de configuración original:

bash
``` bash
sudo cp /etc/apache2/sites-available/default-ssl.conf \
/etc/apche2/sites-available/defaultsafecopy-ssl.conf
```


Edita el archivo de configuración SSL:

bash
``` bash
sudo nano /etc/apache2/sites-available/default-ssl.conf
```

Configura el sitio virtual para utilizar HTTPS:
``` bash
apache
<VirtualHost *:443>
    ServerName your_domain_or_ip
    DocumentRoot /var/www/html
    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/apache-selfsigned.crt
    SSLCertificateKeyFile /etc/ssl/private/apache-selfsigned.key
</VirtualHost>
```

Sustituye your_domain_or_ip por los valores que correspondan a tu servidor y a la ubicación real de tu sitio web.

### 10.5. Activación del sitio virtual

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
### 10.6. Habilitación de mod_rewrite

Activa el módulo de reescritura de Apache:

bash
``` bash
sudo a2enmod rewrite
```

### 10.7. Havilitar AllowOverdrive apache

Entrar al archivo de configuracion usando:

``` bash
sudo nano /etc/apache2/apache2.conf
```

con ctl + W var a <Directory /var/www/>
y modificas
``` bash
<Directory /var/www/>
  ...
  AllowOverride All
</Directory>
```
### 10.8. Configuración de .htaccess

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

## 11. Pagina Error apache


## 11. MariaDB y phpMyAdmin
### 11.1. Instalación de MariaDB

Actualiza los repositorios e instala MariaDB:

bash
``` bash
sudo apt update &&
sudo apt install mariadb-server -y
``` 
### 11.2. Comprobación del puerto

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
### 11.3. Configuración del acceso remoto

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
### 11.4. Mantenimiento del servicio MariaDB

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
### 11.5. Creación de un usuario administrador

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

### 11.6. Seguridad de MariaDB

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

### 11.7. Instalación del módulo MySQL para PHP

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
### 11.8. Instalación de phpMyAdmin

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

## 12. Xdebug
### 12.1 Instalacion

Introduce este comando para instalar x-debug
``` bash
 sudo apt install php8.5-xdebug
```

entras en xdebug.ini
``` bash
sudo nano /etc/php/8.5/mods-available/xdebug.ini
``` 

introduces debajo de zend_extension=xdebug.so esto 
``` bash
xdebug.mode=develop,debug
xdebug.start_with_request=yes
xdebug.client_host=127.0.0.1
xdebug.client_port=9003
xdebug.log_level=7
xdebug.idekey="netbeans-xdebug"
xdebug.discover_client_host=1
``` 

abres el puerto 9003 en ubuntu server
``` bash
sudo ufw allow 9003
``` 

despues reinicias php8.5-fpm
``` bash
sudo systemctl restart php8.5-fpm 
``` 

## 13. Chequeo final
### 13.1. Comprobación de las reglas del firewall

Muestra las reglas de UFW con sus números:

bash
``` bash
sudo ufw status numbered
```

Revisa los puertos permitidos y comprueba que solo estén abiertos los necesarios.

En este servidor se utilizan, como mínimo, los siguientes puertos según los servicios habilitados:

| Puerto | Protocolo | Servicio                                |
| ------ | --------- | --------------------------------------- |
| 22     | TCP       | SSH                                     |
| 80     | TCP       | HTTP                                    |
| 443    | TCP       | HTTPS                                   |
| 3306   | TCP       | MariaDB, si se permite el acceso remoto |

### 13.2. Eliminación de reglas innecesarias

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

### 13.3. Modulos Apache

Con este comando lo compruebas
bash
``` bash
apache2ctl -M
```

y Estos son los unicos modulos que tienen que estar en los estados indicados
| Modulo               | Estado   |
| -------------------- | -------- |
| core_module          | (static) |
| so_module            | (static) |
| watchdog_module      | (static) |
| http_module          | (static) |
| log_config_module    | (static) |
| logio_module         | (static) |
| version_module       | (static) |
| unixd_module         | (static) |
| systemd_module       | (static) |
| access_compat_module | (shared) |
| alias_module         | (shared) |
| auth_basic_module    | (shared) |
| authn_core_module    | (shared) |
| authn_file_module    | (shared) |
| authz_core_module    | (shared) |
| authz_host_module    | (shared) |
| authz_user_module    | (shared) |
| autoindex_module     | (shared) |
| deflate_module       | (shared) |
| dir_module           | (shared) |
| env_module           | (shared) |
| filter_module        | (shared) |
| mime_module          | (shared) |
| mpm_event_module     | (shared) |
| negotiation_module   | (shared) |
| proxy_module         | (shared) |
| proxy_fcgi_module    | (shared) |
| reqtimeout_module    | (shared) |
| rewrite_module       | (shared) |
| setenvif_module      | (shared) |
| socache_shmcb_module | (shared) |
| ssl_module           | (shared) |
| status_module        | (shared) |

### 13.4. Modulos PHP

Con este comando lo compruebas
bash
``` bash
apache2ctl -M
```

y Estos son los unicos modulos que tienen que estar en los estados indicados
| PHP Modules  |
| ------------ |
| bcmath       |
| bz2          |
| calendar     |
| Core         |
| ctype        |
| curl         |
| date         |
| dom          |
| exif         |
| FFI          |
| fileinfo     |
| filter       |
| ftp          |
| gd           |
| gettext      |
| hash         |
| iconv        |
| json         |
| lexbor       |
| libxml       |
| mbstring     |
| mcrypt       |
| mysqli       |
| mysqlnd      |
| openssl      |
| pcntl        |
| pcre         |
| PDO          |
| pdo_mysql    |
| Phar         |
| posix        |
| random       |
| readline     |
| Reflection   |
| session      |
| shmop        |
| SimpleXML    |
| sockets      |
| sodium       |
| SPL          |
| standard     |
| sysvmsg      |
| sysvsem      |
| sysvshm      |
| tokenizer    |
| uri          |
| xdebug       |
| xml          |
| xmlreader    |
| xmlwriter    |
| xsl          |
| Zend OPcache |
| zip          |
| zlib         |
| [Zend Modules] |
| Xdebug         |
| Zend OPcache   |

### 13.2. Eliminación de reglas innecesarias

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
### 13.3. Lista de comprobación final
* Ubuntu está instalado y actualizado.
* Las particiones / y /var están configuradas.
* La dirección IP y la zona horaria son correctas.
* SSH está instalado y permite conexiones desde otra máquina.
* UFW está activo y contiene las reglas necesarias.
* ClamAV está instalado y actualizado.
* El usuario miadmin2 dispone de los permisos administrativos previstos.
* Apache está instalado y sirve la página web.
* PHP-FPM está instalado y configurado.
* HTTPS funciona con el certificado configurado.
* MariaDB está instalado y protegido.
* phpMyAdmin está instalado.
* El usuario operadorweb puede trabajar con el directorio web.
* Los puertos y las reglas del firewall han sido revisados.
