![image](https://user-images.githubusercontent.com/48169157/153631639-c7a28235-7ca5-4e83-ba88-3ab381c0e6f7.png)

# Instalaci贸n de Docker Desktop en Windows 馃悑
Manual de instalaci贸n de Docker Desktop para Windows.

##  1. <a name='TabladeContenido'></a>Tabla de Contenido 
1. [Prerequisitos](#Prerequisitos)
	* 1.1. [Verificar versi贸n de Windows](#VerificarVersionWindows)
	* 1.2. [Verificar el estado de la virsualizaci贸n en Windows](#VerificarVirtualizacionWindows)
	* 1.3. [Verificar por cual m茅todo instalar Docker Desktop](#VerificarMetodo)

2. [Instalar en versiones antiguas (7, 8 y 10 home)](#VersionAntigua)
	* 2.1. [Descargar el instalador Docker ToolBox](#DockerToolBox)
	* 2.2. [Ejecutar el instalador](#EjecutarInstaladorToolBox)
	* 2.3. [Ejecutar Docekr Quickstart](#EjecutarDockerQuickstart)
	
3. [Instalar en versiones m谩s recientes](#VersionReciente)
    	
	* 3.1 [Pasos para instalaci贸n con WSL-2](#InstalacionWSL)
   	* 3.2 [Pasos para instalaci贸n con Hyper-V](#InstalacionHyper-V)
	* 3.3 [Crear una cuenta en Docker Hub](#DockerHub)
	* 3.4 [Instalar Docker Desktop for Windows](#DescargarEInstalarDockerForWindows)
	* 3.5 [Configurar Docker Desktop](#ConfigurarDockerDesktop)
    	
4. [Solucion a problemas](#Problemas)
 	* 4.1 [This error may indicate that the docker daemon is not running. The system cannot find the file specified.](#Daemon)
 	* 4.2 [Docker Desktop stopped](#Stopped)

5. [Referencias](#Referencias)


##  2. <a name='Prerequisitos'></a>Prerequisitos
Primeramente debemos tener nociones sobre nuestro sistema operativo, la versi贸n y el build que posee, as铆 c贸mo conocer si tiene habilitada la opci贸n de virtualizaci贸n.

###  2.1. <a name='VerificarVersionWindows'></a>Verificar versi贸n de Windows
Las instalaciones son diferentes entre Windows Pro Edition y Windows Home Edition, ya que Windows Home no incluye la funci贸n Hyper-V (necesaria para ejecutar "Docker for Windows").

1. Ejecutar **win + R**
   <p align="center">
    <img src="./images/win+z.jpg" />
   </p>
2. Escribir el comando **msinfo32** en la ventana que se abre (Ejecutar)
   <p align="center">
    <img src="./images/msinfo32.jpg" />
   </p>
3. Verificar la informaci贸n de:
    * Nombre del SO
    * Versi贸n
    * Tipo de Sistema (Arquitectura)
    * Mememoria f铆sica Instalada (RAM)
    <p align="center">
     <img src="./images/info_sym.jpg" />
    </p>

###  2.2. <a name='VerificarVirtualizacionWindows'></a>Verificar el estado de la virtualizaci贸n en Windows
Ahora debemos verificar informaci贸n respecto a la virtualizaci贸n, especificamente debes ver si nuestro sistema operativo tiene habilitada la virtualizaci贸n. Para comprobar esto, sigue los siguientes pasos. 

1. Ejecutar **win + R**
   <p align="center">
    <img src="./images/win+z.jpg" />
   </p>
2. Escribir el comando **taskmgr** en la ventana que se abre (Ejecutar)
   <p align="center">
    <img src="./images/taskmgr.jpg" />
   </p>
3. Se abrir谩 el administrador de tareas, aqu铆 debemos dirigirnos a la pesta帽a de *Performance* o *rendimiento*.
   <p align="center">
    <img src="./images/performance.jpg" />
   </p>
4. Posteriormente, aqu铆 vamos a comprobar si la virtualizaci贸n est谩 habilitada o no. As铆 c贸mo se muestra en la imagen, en mi caso est谩 habilitada. 
   <p align="center">
    <img src="./images/option_virtualization.jpg" />
   </p>
**NOTA:** Si no tienes habilitada la virtualizaci贸n, te sugiero buscar un tutorial para activarlo, debido a que los m茅todos para activarla varia dependiendo del equipo, es decir, dependiendo del modelo y marca de la computadora. 

###  2.2. <a name='VerificarMetodo'></a>Verificar por cual m茅todo instalar Docker Desktop

Ahora ya conocemos la informaci贸n de nuestro sistema operativo, esto nos dar谩 la pauta para poder evaluar si cumplimos con lo necesario para instalar Docker Desktop, as铆 mismo para definir que m茅todo utilizar. Las condiciones que debemos tener son las que se presentan en la siguiente tabla. 

| Sistema Operativo     | Arquitectura | Build        | M茅todo                     | Apto |
| --------------------- | ------------ | ------------ | -------------------------- | ---- |
| Windows 10 Home       | 64 bits      | 20H1 o mayor | Docker Desktop for Windows | 鉁?    |
| Windows 10 Pro        | 64 bits      | 20H1 o mayor | Docker Desktop for Windows | 鉁?    |
| Windows 10 Education  | 64 bits      | 1909 o mayor | Docker Desktop for Windows | 鉁?    |
| Windows 10 Enterprise | 64 bits      | 1909 o mayor | Docker Desktop for Windows | 鉁?    |
| Windows 10 Home       | 32 bits      | Cualquiera   | Ninguno                    | 鉂?    |
| Windows 10 Pro        | 32 bits      | Cualquiera   | Ninguno                    | 鉂?    |
| Windows 10 Education  | 32 bits      | Cualquiera   | Ninguno                    | 鉂?    |
| Windows 10 Enterprise | 32 bits      | Cualquiera   | Ninguno                    | 鉂?    |
| Windows 11 Home       | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | 鉁?    |
| Windows 11 Pro        | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | 鉁?    |
| Windows 11 Education  | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | 鉁?    |
| Windows 11 Enterprise | 64 bits      | 21H2 o mayor | Docker Desktop for Windows | 鉁?    |
| Windows 8             | 64 bits      | Cualquiera   | Docker  ToolBox            | 鉁?    |
| Windows 8.1           | 64 bits      | Cualquiera   | Docker  ToolBox            | 鉁?    |
| Windows 7             | 64 bits      | Cualquiera   | Docker  ToolBox            | 鉁?    |

De acuerdo con la documentaci贸n, el requisito fundamnetal es que la arquitectura de la computadora sea de 64 bits, por lo que se desonoce si funcione en una arquitectura de 32 bits, lo m谩s probable es que no.
**Nota:** Actualizar茅 el repositorio si tuviera informaci贸n de versiones en las que si se les puede instalar.

##  3. <a name='VersionAntigua'></a>Instalar en versiones antiguas (7, 8 y 10 home)
A continuaci贸n se describen los pasos a realizar para la instalaci贸n de Docker Desktop en versines antiguas de Windows. 
As铆 c贸mo lo menciona la documentaci贸n oficial de Docker. este m茅todo es poco garantizado, debido a que el soporte para estas versiones del sistema operativo qued贸 descontinuado desde el 2019, por lo que programa a instalar es con la 煤ltima versi贸n de dicho a帽o.

[Documentaci贸n ofical de Docker](https://docs.docker.com/toolbox/)

###  3.1. <a name='DockerToolBox'></a>Descargar el instalador Docker ToolBox
Los primero es descargar el siguiente instalador. Para garantizar que es de confianza, se descarga del reposiotario oficial.  


<p align="center">
 <a href="https://github.com/docker-archive/toolbox/releases/tag/v19.03.1">Docker Toolbox C贸digo (GitHub).
 </a>
</p>

<p align="center">
 <a href="https://github.com/docker-archive/toolbox/releases/download/v19.03.1/DockerToolbox-19.03.1.exe">Docker Toolbox Instalador.
 </a>
</p>

驴Qu茅 contiene este programa?
* Docker
  
  Los binarios de Docker est谩n disponibles para crear y ejecutar contenedores en su computadora. Al instalar Docker, obtiene una CLI de Docker para comunicarse con un servidor Docker. De esta manera, puede lanzar instrucciones y se ejecutar谩n en sus contenedores.
* Docker-Machine
  
  Una herramienta que maneja el aprovisionamiento en sus contenedores (instalaci贸n de paquetes, eliminaci贸n de paquetes, ejecuci贸n, etc.).

* Docker-Compose
  
  Una herramienta para entornos que contienen m煤ltiples contenedores con diferentes entornos. De esta forma, puede iniciar varios contenedores juntos o detenerlos juntos.
  
* Kitermatic
  
  Una dulce interfaz gr谩fica para que controle sus contenedores en Windows y Mac.

* Boot2Docker ISO

  Una peque帽a distribuci贸n de Linux para ejecutar Docker en Windows.

* VirtualBox

  Hipervisor de c贸digo abierto para Windows y se utiliza para emular sistemas operativos en su sistema Windows.


###  3.2. <a name='EjecutarInstaladorToolBox'></a>Ejecutar el instalador
Una vez descargado, lo que se procede a realizar es ejecutar el intalador.

1.- Ejecutamos el instalador. Y se nos abrir谩 una ventana c贸mo la siguiente. Solo debemos dar clic en el bot贸n de *next*. 
   <p align="center">
    <img src="./images/toolbox-install-step1.jpg" />
   </p>

2.- Ahora vamos a seleccionar la ubicaci贸n en donde se instalar谩 el programa. Podemos dejar la que nos da por default o escribir una ruta que deseemos. 
   <p align="center">
    <img src="./images/toolbox-install-step2.jpg" />
   </p>

3.- Procedemos a seleccionar las herramientas que deseemos, les recomiendo dejar todas las que vienen seleccionadas por default. Entonces simplemente damos clic en el bot贸n de *next*.
   <p align="center">
    <img src="./images/toolbox-install-step3.jpg" />
   </p>

4.- Ahora seleccionamos los accesos directos que deseamos y la opci贸n de agregar el path, recomiendo dejar las opciones seleccionadas por default. Luego damos clic en el bot贸n de *next*.
   <p align="center">
    <img src="./images/toolbox-install-step4.jpg" />
   </p>

5.- Revisamos que vamos a instalar lo correcto, desde la ubicaci贸n que deseamos, los accesos directos y los componentes. Una vez que todo est谩 correcto, procedemos a dar clic en *instalar* y se empezar谩 a instalar el programa.
   <p align="center">
    <img src="./images/toolbox-install-step5.jpg" />
   </p>

6.- El tiempo de instalaci贸n depender谩 de su computadora pero suele durar entre 10 a 20 minutos.
   <p align="center">
    <img src="./images/toolbox-install-step6.jpg" />
   </p>

7.- Si al momento de instalar les sale que deben instalar un software, simplemente dan en la opci贸n de *Instalar*.
   <p align="center">
    <img src="./images/toolbox-install-step7.jpg" />
   </p>

8.- Una vez terminada la instalaci贸n, en la 煤ltima ventana vamos a dar clic en *Finish*.
   <p align="center">
    <img src="./images/toolbox-install-step8.jpg" />
   </p>

8.- Se nos abrir谩 el explorar de archivos, y ah铆 vamos a observar nuestros accesos directos. Con esto logramos garatnizar que hemos instalador correctamente Docker.
   <p align="center">
    <img src="./images/toolbox-install-step9.jpg" />
   </p>

###  3.3. <a name='EjecutarDockerQuickstart'></a>Ejecutar Docker Quickstart
Ahora que Docker est谩 instalado, procedemos a ejecutar el proceso de Docker Quickstart.
1. Ejecutamos el acceso directo denomiado *Docker Quickstart*. 
2. Se nos abrir谩 una ventana con la ejecuci贸n de un inicio r谩pido en Docker.


##  4. <a name='VersionReciente'></a>Instalar en versiones recientes
A continuaci贸n se describen los pasos a realizar para la instalaci贸n de Docker Desktop en versines recientes de Windows. 
Hay dos formas de realizar la instalaci贸n, la primera forma es con WSL-2 y la otra con Hyper-V. Aunque recomendar铆a realizar ambos procesos para aprovecahr mejor el rendimiento de Docker Desktop. 
###  4.1. <a name='InstalacionWSL'></a>Instalaci贸n WSL-2
A continuaci贸n se presenta el manual donde se detallan los pasos a seguir para tener el ambiente de WSL-2 listo para la instalaci贸n de Docker Desktop.

<p align="center">
 <a href="./wsl2.md">Munual de WSL-2.
 </a>
</p>

###  4.2. <a name='InstalacionHyper-V'></a>Instalaci贸n Hyper-V
A continuaci贸n se presenta el manual donde se detallan los pasos a seguir para tener el ambiente de Hyper-V listo para la instalaci贸n de Docker Desktop.

<p align="center">
 <a href="./hyper-v.md">Munual de Hyper-V.
 </a>
</p>

###  4.3. <a name='DockerHub'></a>Crear una cuenta en Docker Hub
A continuaci贸n se presentar谩n los pasos a seguir para poder crear una cuenta de Docker Hub, esto con la finalidad de poder aprovechar las ventajas que nos da Docker Desktop para los usuarios que no son anonimos (Con ID de Docker Hub). 


Alguna de las ventajas son: 
* Obtener el doble de pulls (200) cada 6 horas, en comparaci贸n de un usuario anonimo. 
* Poder implementar una gesti贸n de acceso. 
* Acceso a solo contenido de confianza. 
* Mayor seguridad en general. 

1. Acceder al portal de [Docker Hub](https://hub.docker.com/). Y dirigirse a la opci贸n de **sign up**.
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
4. Colocar nuestro usuario o nuestro emial y nuestra respectiva contrase帽a para acceder. 
   <p align="center">
    <img src="./images/dockerhub-login2.jpg" />
   </p>
5. Al acceder, podemos verificar que ya tenemos nuestra cuenta de Docker Hub, ahora este usuario lo vamos a utilizar para acceder a Docker Desktop. 
   <p align="center">
    <img src="./images/dockerhub-login3.jpg" />
   </p>

###  4.4. <a name='DescargarEInstalarDockerForWindows'></a>Descargar e Instalar Docker Desktop for Windows

Ahora, vamos a proceder a descargar el instalador *Desktop for Windows* para proceder con la instalaci贸n c贸mo tal del programa Docker Desktop.
1. Descargar el instalador del siguiente enlace. 
   <p align="center">
    <a href="https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe"> Instalador Desktop for Windows </a>
   </p>
2. Ejecutar el instalador descargado. Entonces se nos abrir谩 el instalador y automaticamente empezar谩 a descargar los archivos necesarios para la instalaci贸n.
   <p align="center">
    <img src="./images/dockerforwindows.jpg" />
   </p>
3. Luego de que termine de descargar algunos archivos, nos saldr谩 la siguiente ventana y en esta debemos seleccionar las dos opciones. Donde la primera son componentes para WSL-2 y la segunda es para agregar una acceso directo. Luego debemos dar clic en el bot贸n *Ok*.
   <p align="center">
    <img src="./images/dockerforwindows2.jpg" />
   </p>
4. Se empezar谩 a desempaquetar los diferentes archivos descargados, este proceso varia dependiende los recursos de tu computadora pero entre 5 a 10 minutos.
   <p align="center">
    <img src="./images/dockerforwindows3.jpg" />
   </p>
5. Una vez que se termine el proceso anterior. Se nos mostrar谩 una ventana c贸mo la siguiente, donde debemos dar clic en el bot贸n *Close*. Tambi茅n les puede salir un bot贸n con la opci贸n *Close and logout*, igual le da clic, y lo que har谩 es cerrarle la sesi贸n de su usuario de Windows.
   <p align="center">
    <img src="./images/dockerforwindows4.jpg" />
   </p>
6. Si nos dirigimos a nuestro escritorio, vamos a ver un icono c贸mo el siguiente, este es un acceso directo para ejecutar **Docker Desktop**. Le damos clic en 茅l para proceder a abrir el programa.
   <p align="center">
    <img src="./images/dockerforwindows5.jpg" />
   </p>
7. Al abrir Docker Desktop por pirmera vez, nos mostrar谩 una ventana con la licencia del programa, lo que debemos hacer leer toda la licencia y luego dar clic en el bot贸n *Accept*.
   <p align="center">
    <img src="./images/dockerforwindows6.jpg" />
   </p>
Y listo, tendr铆amos instalado Docker Desktop para poder utilizarlo. 

###  4.4. <a name='ConfigurarDockerDesktop'></a>Configurar Docker Desktop
1. Al iniciar por primer vez el programa, vamos a ver una ventana c贸mo la siguiente.
   Podemos seguir el tutorial que nos muestra o podemos saltarnos esta parte.
   <p align="center">
    <img src="./images/dockerforwindows-init.jpg" />
   </p>
2. Al terminar de completar el tutorial o de saltarse el paso, vamos a ver una ventana c贸mo la siguiente en la que nos muestra c贸mo podemos ejecutar un comando de Docker.
   <p align="center">
    <img src="./images/dockerforwindows-init2.jpg" />
   </p>
3. En la parte superior, aparece la opci贸n para poder iniciar sesi贸n con nuestro usuario de Doker Hub. En mi caso ya estoy logueado, pero es f谩cil este procedimiento, adem谩s que obtenemos m谩s ventajas al realizarlo.
   <p align="center">
    <img src="./images/dockerforwindows-init3.jpg" />
   </p>
Listo, ya tenemos Docker Desktop instalado y preparado para poder empezar a utiliarlo, para gestionar nuestras imagenes, volumenes y contenedores de Docker.

##  5. <a name='Problemas'></a>Problemas al ejecutar Docker Desktop
A continuaci贸n se presentan las soluciones a dos de los problemas tipicos que se pueden encontrar al ejecutar Docker Desktop. 

###  5.1 <a name='Daemon'></a>This error may indicate that the docker daemon is not running. The system cannot find the file specified.
Este error se visualiza cuando intentamos ejecutar alg煤n comando de Docker. Y en la siguiente imagen se puede apreciar. 
   <p align="center">
    <img src="./images/daemon.png" />
   </p>
   
La soluci贸n a este problema se da con los siguientes pasos: 

1. Desinstala Docker Desktop.
2. Reinicia la computadora.
3. Ejecuta el instalador de Docker Desktop c贸mo administrador.
4. Instala con los pasos de siempre.
5. Reinicia la computadora. 

Y listo, con eso se soluciona este error. Si por casualidad tu error persiste, puedes aplicar la misma soluci贸n del siguiente problema. 

###  5.2 <a name='Stopped'></a>Docker Desktop stopped
Este error consiste en que el demonio de Docker no inicia, por lo que no el servicio de Docker tampoco se encuentra funcionando. Y al abrir Docker Desktop vamos a ver un mensaje c贸mo el de la siguiente imagen.
   <p align="center">
    <img src="./images/stopped.png" />
   </p>
   
La soluci贸n para este problema es sencillo. Sigue los siguientes pasos.

1. Abre la terminal *CMD* o *Power Shell*.
2. Ejecuta el siguiente comando. Hay que esperar unos minutos, en los que se realiza el cambio. 
```bash
cd "C:\Program Files\Docker\Docker"
DockerCli.exe -SwitchDaemon
```
3. Reinicia la computadora. 

Y listo, ya tendr铆amos solucionado el problema. 

##  6. <a name='Referencias'></a>Referencias
Esta peque帽a gu铆a fue elaborada en base a la documentaci贸n oficial de Docker y Microsoft. 

* [Instalaci贸n de Docker en Windows](https://docs.docker.com/desktop/windows/install/).
* [Problemas al instalar Docker](https://docs.docker.com/desktop/windows/troubleshoot/).
* [Manual de usuario de Docker](https://docs.docker.com/desktop/windows/).
