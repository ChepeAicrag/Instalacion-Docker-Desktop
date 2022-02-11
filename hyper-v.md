# INSTALACIÓN Hyper-V
## Requerimientos
* Es importante aclarar que para poder instalar WSL-2 debemos cumplir con los prerequisitos explicados en el tutorial principal.
* Solo se puede habilitar en Windows 10 Enterprise, Pro, o Education.

**Requerimientos de Hardware:**

Aunque este documento no proporciona una lista completa del hardware compatible con Hyper-V, los siguientes elementos son necesarios:
* Procesador de 64 bits con traducción de direcciones de segundo nivel (SLAT).
* Soporte de CPU para VM Monitor Mode Extension (VT-x en CPU Intel).
* Mínimo de 4 GB de memoria. Dado que las máquinas virtuales comparten memoria con el host de Hyper-V, deberá proporcionar suficiente memoria para manejar la carga de trabajo virtual esperada.

Los siguientes elementos deberán estar habilitados en el BIOS del sistema:

* Tecnología de virtualización: puede tener una etiqueta diferente según el fabricante de la placa base.
* Prevención de ejecución de datos forzada por hardware.

## Verificar compatibilidad de hardware
Después de verificar el sistema operativo y los requisitos de hardware anteriores, verifique la compatibilidad del hardware en Windows.
1. Abra la terminal *CMD* o *PowerShell*.
2. Ejecuta el siguiente comando. 
   ```bash
   systeminfo
   ```
3. La salida del comando anterior mostrará información respecto a
   
   Luego verifique la sección Re. Si todos los requisitos de Hyper-V enumerados tienen un valor de Sí, su sistema puede ejecutar el rol de Hyper-V. Si algún elemento devuelve No, verifique los requisitos enumerados en este documento y haga los ajustes donde sea posible.

   <p align="center">
    <img src="./images/systeminfo.png" />
   </p>
   
## Procedimiento

1. Vamos a buscar la *Power Shell* y la ejecutamos cómo administrador. 
   <p align="center">
    <img src="./images/shell.png" />
   </p>
   
2. Ahora vamos a instalar WSL de forma general. Para ello escribimos el comando **wsl --install**.

  ```bash
  Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
  ```
3. Reiniciamos la computadora.
4. Ahora, podemos comprobarlo si lo tenemos activado. Para ello vamos a hacer clic derecho en el botón de Windows y seleccionamos *Aplicaciones y características*.
5. Seleccionamos *Programas y características* a la derecha debajo de la configuración relacionada.
6. Seleccionamos *Activar o desactivar las funciones de Windows*.
7. Seleccionamos *Hyper-V* y luego clic en Aceptar.
   <p align="center">
    <img src="./images/hyperv.png" />
   </p> 
8. Reiniciamos la computadora.

## Referencias
Para mayor información pueden visitar la documentación oficial de Microsoft [aquí](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
