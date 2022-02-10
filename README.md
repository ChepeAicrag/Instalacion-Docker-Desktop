<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

# Instalación de Docker Desktop en Windows
Manual de instalación de Docker Desktop para Windows.

##  1. <a name='TabladeContenido'></a>Tabla de Contenido 
* 1. [Prerequisitos](#Prerequisitos)
	* 1.1. [Verificar versión de Windows](#VerificarVersionWindows)
	* 1.2. [Verificar el estado de la virsualización en Windows](#VerificarVirtualizacionWindows)
	* 1.3. [Verificar por cual método instalar Docker Desktop](#VerificarMetodo)

* 2. [Instalar en versiones antiguas (7, 8 y 10 home)](#VersionAntigua)
	* 2.1. [Descargar el instalador Docker ToolBox](#DockerToolBox)
	* 2.2. [Ejecutar el instalador](#EjecutarInstalador)
    * 2.3. [Ejecutar Docekr Quickstart](#VerificarversindeWindowsows)
	
* 3. [Instalar en versiones más recientes](#VersionReciente)
    * 3.1 [Pasos para instalación con WSL-2](#InstalacionWSL)
    * 3.2 [Pasos para instalación con Hyper-V](#InstalacionHyper-V)
	* 3.3 [Crear una cuenta en Docker Hub](#DockerHub)
    * 3.4 [Instalar Docker Desktop for Windows](#DescargarEInstalarDockerForWindows)
    * 3.5 [Configurar Docker Desktop](#ConfigDockerDesktop)
 
##  2. <a name='Prerequisitos'></a>Prerequisitos
Primeramente debemos tener nociones sobre nuestro sistema operativo, la versión y el build que posee, así cómo conocer si tiene habilitada la opción de virtualización.

###  2.1. <a name='VerificarVersionWindows'></a>Verificar versión de Windows
Las instalaciones son diferentes entre Windows Pro Edition y Windows Home Edition, ya que Windows Home no incluye la función Hyper-V (necesaria para ejecutar "Docker for Windows").

1. Ejecutar **win + R**
   <p align="center">
    <img src="./images/win+z.jpg" />
   </p>
2. Escribir el comando **msinfo32** en la ventana que se abre (Ejecutar)
   <p align="center">
    <img src="./images/msinfo32.jpg" />
   </p>
3. Verificar la información de:
    * Nombre del SO
    * Versión
    * Tipo de Sistema (Arquitectura)
    * Mememoria física Instalada (RAM)
    <p align="center">
     <img src="./images/info_sym.jpg" />
    </p>

###  2.2. <a name='VerificarVirtualizacionWindows'></a>Verificar el estado de la virtualización en Windows
Ahora debemos verificar información respecto a la virtualización, especificamente debes ver si nuestro sistema operativo tiene habilitada la virtualización. Para comprobar esto, sigue los siguientes pasos. 

1. Ejecutar **win + R**
   <p align="center">
    <img src="./images/win+z.jpg" />
   </p>
2. Escribir el comando **taskmgr** en la ventana que se abre (Ejecutar)
   <p align="center">
    <img src="./images/taskmgr.jpg" />
   </p>
3. Se abrirá el administrador de tareas, aquí debemos dirigirnos a la pestaña de *Performance* o *rendimiento*.
   <p align="center">
    <img src="./images/performance.jpg" />
   </p>
4. Posteriormente, aquí vamos a comprobar si la virtualización está habilitada o no. Así cómo se muestra en la imagen, en mi caso está habilitada. 
   <p align="center">
    <img src="./images/option_virtualization.jpg" />
   </p>

###  2.2. <a name='VerificarMetodo'></a>Verificar por cual método instalar Docker Desktop

Ahora ya conocemos la información de nuestro sistema operativo, esto nos dará la pauta para poder evaluar si cumplimos con lo necesario para instalar Docker Desktop, así mismo para definir que método utilizar. Las condiciones que debemos tener son las que se presentan en la siguiente tabla. 

| Sistema Operativo     | Arquitectura | Build        | Método                     | Apto |
| --------------------- | ------------ | ------------ | -------------------------- | ---- |
| Windows 10 Home       | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | ✅    |
| Windows 10 Pro        | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | ✅    |
| Windows 10 Education  | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | ✅    |
| Windows 10 Enterprise | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | ✅    |
| Windows 10 Home       | 32 bits      | Cualquiera   | Ninguno                    | ❌    |
| Windows 10 Pro        | 32 bits      | Cualquiera   | Ninguno                    | ❌    |
| Windows 10 Education  | 32 bits      | Cualquiera   | Ninguno                    | ❌    |
| Windows 10 Enterprise | 32 bits      | Cualquiera   | Ninguno                    | ❌    |
| Windows 11 Home       | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | ✅    |
| Windows 11 Pro        | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | ✅    |
| Windows 11 Education  | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | ✅    |
| Windows 11 Enterprise | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | ✅    |
| Windows 11 Home       | 32 bits      | Cualquiera   | Ninguno                    | ❌    |
| Windows 11 Pro        | 32 bits      | Cualquiera   | Ninguno                    | ❌    |
| Windows 11 Education  | 32 bits      | Cualquiera   | Ninguno                    | ❌    |
| Windows 11 Enterprise | 32 bits      | Cualquiera   | Ninguno                    | ❌    |
| Windows 8             | 64 bits      | Cualquiera   | Docker  ToolBox            | ✅    |
| Windows 8.1           | 64 bits      | Cualquiera   | Docker  ToolBox            | ✅    |
| Windows 7             | 64 bits      | Cualquiera   | Docker  ToolBox            | ✅    |

De acuerdo con la documentación, el requisito fundamnetal es que la arquitectura de la computadora sea de 64 bits, por lo que se desonoce si funcione en una arquitectura de 32 bits, lo más probable es que no.
**Nota:** Actualizaré el repositorio si tuviera información de versiones en las que si se les puede instalar.

##  3. <a name='Instalarenversionesantiguas78y10home'></a>Instalar en versiones antiguas (7, 8 y 10 home)
A continuación se describen los pasos a realizar para la instalación de Docker Desktop en versines antiguas de Windows. 
Así cómo lo menciona la documentación oficial de Docker. este método es poco garantizado, debido a que el soporte para estas versiones del sistema operativo quedó descontinuado desde el 2019, por lo que programa a instalar es con la última versión de dicho año.

[Documentación ofical de Docker](https://docs.docker.com/toolbox/)

###  3.1. <a name='DescargarelinstaladorDockerToolBox'></a>Descargar el instalador Docker ToolBox
Los primero es descargar el siguiente instalador. Para garantizar que es de confianza, se descarga del reposiotario oficial.  


<p align="center">
 <a href="https://github.com/docker-archive/toolbox/releases/tag/v19.03.1">Docker Toolbox Código (GitHub).
 </a>
</p>

<p align="center">
 <a href="https://github.com/docker-archive/toolbox/releases/download/v19.03.1/DockerToolbox-19.03.1.exe">Docker Toolbox Instalador.
 </a>
</p>

¿Qué contiene este programa?
* Docker
  
  Los binarios de Docker están disponibles para crear y ejecutar contenedores en su computadora. Al instalar Docker, obtiene una CLI de Docker para comunicarse con un servidor Docker. De esta manera, puede lanzar instrucciones y se ejecutarán en sus contenedores.
* Docker-Machine
  
  Una herramienta que maneja el aprovisionamiento en sus contenedores (instalación de paquetes, eliminación de paquetes, ejecución, etc.).

* Docker-Compose
  
  Una herramienta para entornos que contienen múltiples contenedores con diferentes entornos. De esta forma, puede iniciar varios contenedores juntos o detenerlos juntos.
  
* Kitermatic
  
  Una dulce interfaz gráfica para que controle sus contenedores en Windows y Mac.

* Boot2Docker ISO

  Una pequeña distribución de Linux para ejecutar Docker en Windows.

* VirtualBox

  Hipervisor de código abierto para Windows y se utiliza para emular sistemas operativos en su sistema Windows.


###  3.2. <a name='Ejecutarelinstalador'></a>Ejecutar el instalador
Una vez descargado, lo que se procede a realizar es ejecutar el intalador.

1.- 

###  3.3. <a name='EjecutarDockerQuickstart'></a>Ejecutar Docker Quickstart
Ahora que Docker está instalado, procedemos a ejecutar el proceso de Docker Quickstart.
1. Double-click on the icon to start Docker Quickstart.

2. 

##  4. <a name='VersionReciente'></a>Instalar en versiones recientes
A continuación se describen los pasos a realizar para la instalación de Docker Desktop en versines recientes de Windows. 
Hay dos formas de realizar la instalación, la primera forma es con WSL-2 y la otra con Hyper-V. Aunque recomendaría realizar ambos procesos para aprovecahr mejor el rendimiento de Docker Desktop. 
###  4.1. <a name='InstalacionWSL'></a>Instalación WSL-2
A continuación se presenta el manual donde se detallan los pasos a seguir para tener el ambiente de WSL-2 listo para la instalación de Docker Desktop.

<p align="center">
 <a href="./wsl2.md">Munual de WSL-2.
 </a>
</p>

###  4.2. <a name='InstalacionHyper-V'></a>Instalación Hyper-V
A continuación se presenta el manual donde se detallan los pasos a seguir para tener el ambiente de Hyper-V listo para la instalación de Docker Desktop.

<p align="center">
 <a href="./hyper-v.md">Munual de Hyper-V.
 </a>
</p>

###  4.3. <a name='DockerHub'></a>Crear una cuenta en Docker Hub
A continuación se presentarán los pasos a seguir para poder crear una cuenta de Docker Hub, esto con la finalidad de poder aprovechar las ventajas que nos da Docker Desktop para los usuarios que no son anonimos (Con ID de Docker Hub). 


Alguna de las ventajas son: 
* Obtener el doble de pulls (200) cada 6 horas, en comparación de un usuario anonimo. 
* Poder implementar una gestión de acceso. 
* Acceso a solo contenido de confianza. 
* Mayor seguridad en general. 

1. Acceder al portal de [Docker Hub](https://hub.docker.com/). Y dirigirse a la opción de **sign up**.
   <p align="center">
    <img src="./images/dockerhub-signup.jpg" />
   </p>
2. Proceder a rellenar los campos que solicita, para crearse una cuenta. Luego acceder al correo que registremos y activar la cuenta. 
   <p align="center">
    <img src="./images/dockerhub-signup2.jpg" />
   </p>
3. Luego acceder al login para loguearse. 
   <p align="center">
    <img src="./images/dockerhub-login.jpg" />
   </p>
4. Colocar nuestro usuario o nuestro emial y nuestra respectiva contraseña para acceder. 
   <p align="center">
    <img src="./images/dockerhub-login2.jpg" />
   </p>
5. Al acceder, podemos verificar que ya tenemos nuestra cuenta de Docker Hub, ahora este usuario lo vamos a utilizar para acceder a Docker Desktop. 
   <p align="center">
    <img src="./images/dockerhub-login3.jpg" />
   </p>

###  4.4. <a name='DescargarEInstalarDockerForWindows'></a>Descargar e Instalar Docker Desktop for Windows



###  4.4. <a name='ConfigurarDockerDesktop'></a>Configurar Docker Desktop