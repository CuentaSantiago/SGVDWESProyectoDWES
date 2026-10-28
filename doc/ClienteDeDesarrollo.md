# Cliente Desarrollo
---
##### Fecha Creación: 15/09/2026
##### Fecha Actualizada: 26/10/2026
##### Ciclo formativo: DAW2
##### Alumno: Santiago González Vicente
---
#### 📑 Índice
- 1.[CLIENTE DE DESARROLLO - WINDOWS 10](#1-CLIENTE_DE_DESARROLLO-WINDOWS-10)
- 2.[Navegadores](#2-Navegadores)
  - 2.1.[Google](#21-Google)
  - 2.2.[Microsoft Edge](#22-Microsoft-Edge)
- 3.[Netbeans](#3-Netbeans)
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

## 1. CLIENTE DE DESARROLLO - WINDOWS 10

*   **Nombre del dispositivo: ED49000391P393.educa.jcyl.es**
*   **Sistema operativo: Windows 10 pro.**
*   **Procesador: Intel(R) Core(TM) i5-7400 CPU @ 3.00GHz**
*   **Tarjeta gráfica: NVIDIA GeForce GTX 1050 (2 GB), Intel(R) HD Graphics 630 (128 MB)**
*   **Version: Versión 22H2.**
*   **Memoria RAM: 16 GB.**
*   **Disco duro: 1.13 TB.**
*   **Partición Alumno(D:): 931 GB.**

## 2. Navegadores

### 2.1. Google

*   **Navegador Por defecto**
*   **Vesion: Versión 156.0.8078.47 (Build oficial) (64 bits)**
*   **Uso Principal: Para servidor, html, css, js**

| Nombre de la extension | Versión | Enlace |
| --- | --- | --- |
| HTML Visual Validation | 0.3.0 | [Enlace](https://chromewebstore.google.com/detail/html-visual-validation/hicjdabjhdmaaabgackleegipabmeack) |
| Refined GitHub | 26.10.26 | [Enlace](https://chromewebstore.google.com/detail/refined-github/hlepfoohegkhhmjieoechaddaejaokhf?hl=es&utm_source=ext_sidebar) |
| Selector de color hexagonal | 3.1.0| [Enlace](https://chromewebstore.google.com/detail/selector-de-color-hexagon/eamkimleiebmdpifljjfilhbaehclahg?hl=es&utm_source=ext_sidebar) |

### 2.2. Microsoft Edge

*   **Vesion: Versión 156.0.4314.42 (Compilación oficial) (64 bits)**
*   **Uso Principal: buscar y documentar**

## 3. Netbeans

### 3.1. Caracteristicas
*   **Version: Apache NetBeans IDE 20**
*   **Ruta utilizada: D:\ProyectosNetbeans**
*   **Utilidad: creación y trabajo en proyectos, github, sftp**

### 3.2. Plugins

| Nombre | Proposito | Versión | Enlace |
| --- | --- | --- | --- |
| netbeans-markdown | Este complemento añade algunas funcionalidades adicionales al editor de Markdown de Apache NetBeans: - Vista previa - Ventana dividida - Sugerencias - Exportación a DOCX, PDF y HTML | netbeans-markdown-4.0.nbm | [Enlace](https://plugins.netbeans.apache.org/catalogue/?id=93) |

## 4. VScode

### 3.1. Caracteristicas
*   **Version: Apache NetBeans IDE 20**
*   **Utilidad: creación y trabajo en proyectos, github, sftp, ssh**

### 3.2. Extensions

| Nombre | Proposito | Versión | Enlace |
| --- | --- | --- | --- |
| GitHub Actions | La extensión de GitHub Actions te permite gestionar tus flujos de trabajo, consultar el historial de ejecución de los mismos y te ayuda en la creación de flujos de trabajo. | 0.32.3 | [Enlace](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-github-actions) |
| vscode-pdf | Muestran Ficheros PDF en vscode | 1.2.2 | [Enlace](https://marketplace.visualstudio.com/items?itemName=tomoki1207.pdf) |
| Start git-bash | Añade un comando bash a VS Code que permite iniciar git-bash en la carpeta raíz del espacio de trabajo actual.  | 1.2.1 | [Enlace](https://marketplace.visualstudio.com/items?itemName=McCarter.start-git-bash) |
| SQLTools MySQL/MariaDB/TiDB Driver | Parte de un paquete, enlace [link](https://vscode-sqltools.mteixeira.dev/en/home) | 0.32.3 | [Enlace](https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools-driver-mysql) |
| SQLTools | SQLTools es un conjunto de extensiones para VS Code que permiten conectarse a un gestor de bases de datos SQL, realizar consultas y mostrar los resultados.  | 0.28.6 | [Enlace](https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools) |
| Live Server | Inicia un servidor de desarrollo local con funcionalidad de recarga en tiempo real para páginas estáticas y dinámicas. | 5.7.10 | [Enlace](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) |
| Remote Repositories | La extensión Remote Repositories se integra con las extensiones GitHub Repositories y Azure Repos, lo que te permite explorar, buscar, editar y realizar commits en repositorios Git remotos de forma rápida, directamente desde Visual Studio Code. | 0.42.0 | [Enlace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.remote-repositories) |
| Remote Explorer | Las extensiones Remote - SSH y Remote - Tunnels te permiten utilizar cualquier máquina remota como tu entorno de desarrollo. | 0.5.0 | [Enlace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.remote-explorer) |
| Remote - SSH: Editing Configuration Files | La extensión Remote - SSH te permite utilizar cualquier máquina remota que cuente con un servidor SSH como tu entorno de desarrollo. | 0.87.0 | [Enlace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh-edit) |
| Remote - SSH | Abre cualquier carpeta en una máquina remota mediante SSH y aprovecha el conjunto completo de funcionalidades de VS Code. | 0.128.0 | [Enlace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) |