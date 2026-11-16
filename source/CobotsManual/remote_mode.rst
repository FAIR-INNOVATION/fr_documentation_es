Modo remoto del robot
=============================================================

.. toctree:: 
   :maxdepth: 6
   
Descripción general
-------------------------

Para facilitar el control de movimiento del robot por parte del PLC mediante distintos protocolos de bus industrial (CC-Link, Profinet, Ethernet/IP y EtherCAT), se añaden en la caja de control mini integrada las tarjetas FRH-PCIeN-EC/EIP/CC/PN-RJ-V10 y el módulo FRJ-PCIeN-EIP/CC/PN-RJ-V10, con las siguientes funciones:

1) Compatibilidad con el protocolo CC-Link slave;
2) Compatibilidad con el protocolo Profinet slave;
3) Compatibilidad con el protocolo Ethernet/IP slave;
4) Compatibilidad con el protocolo EtherCAT slave (la tarjeta FRJ-PCIeN-EIP/CC/PN-RJ-V10 no es compatible).

Configuración del entorno
--------------------------------------------

Instalación de la tarjeta
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(1) Verificación del material: el aspecto de las tarjetas FRH-PCIeN y FRJ-PCIeN, así como de la pieza de chapa metálica correspondiente, se muestra a continuación.

.. image:: remote_mode/001.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-1 Chapa de instalación (frontal)

.. image:: remote_mode/002.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-2 Chapa de instalación (posterior)

.. image:: remote_mode/003.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-3 Tarjeta FRH-PCIeN-EC/EIP/CC/PN-RJ-V10

.. image:: remote_mode/004.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-4 Tarjeta FRJ-PCIeN-EIP/CC/PN-RJ-V10

(2) Instalar la tarjeta en la caja de control mini integrada, como se muestra en la figura.

.. image:: remote_mode/005.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-5 Esquema de instalación de la chapa metálica

.. image:: remote_mode/006.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-6 Esquema de instalación de la placa base principal FRH-PCIeN

.. image:: remote_mode/007.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-7 Esquema de instalación de la tarjeta de expansión de puerto de red (RJ45) FRH-PCIeN

.. image:: remote_mode/008.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-8 Esquema de instalación de la placa base principal FRJ-PCIeN

.. image:: remote_mode/009.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-9 Esquema de instalación de la tarjeta de expansión de puerto de red (RJ45) FRJ-PCIeN

.. note:: Nota: todos los tornillos deben apretarse.

(3) El cableado de la caja de control del robot y del PLC se muestra en la figura siguiente.

.. image:: remote_mode/010.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-10 Diagrama de cableado caja de control y PLC Mitsubishi    

.. image:: remote_mode/011.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-11 Diagrama de cableado caja de control y PLC Siemens

.. image:: remote_mode/012.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-12 Diagrama de cableado caja de control y PLC Omron

.. image:: remote_mode/013.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-13 Diagrama de cableado caja de control y PLC Omron

.. note:: 
    1: caja de control del robot (puerto de red de la tarjeta);
    2: conmutador;
    3: PC portátil;
    4: PLC Mitsubishi (puerto de red CC-Link IEF Basic);
    5: PLC Siemens (puerto de red Profinet);
    6: PLC Omron (puerto de red Ethernet/IP);
    7: PLC Omron (puerto de red EtherCAT);

Cuando el protocolo se conmuta al bus EtherCAT, los puertos de red de la tarjeta deben distinguirse entre EtherCAT_IN y EtherCAT_OUT; en este momento, el puerto de red EtherCAT del PLC Omron debe conectarse directamente mediante un cable de red al puerto de red EtherCAT_IN de la tarjeta.

Configuración del entorno del PLC
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

El entorno de prueba construido para implementar las instrucciones de esclavo de cada protocolo se muestra en la tabla siguiente, que incluye los modelos de PLC utilizados en cada protocolo, las versiones de firmware y el software de prueba.

.. centered:: Tabla 2-1 Entorno de prueba

.. list-table:: 
   :widths: 20 40 40
   :header-rows: 1
   :align: center

   * - Protocolo
     - Profinet
     - CC-link
  
   * - Marca
     - Siemens
     - Mitsubishi
  
   * - Modelo
     - CPU 1515-2 PN
     - FX5S-30TR/DS
  
   * - Firmware
     - 6ES75152AM020AB0
     - 30MR/ES V1.3
  
   * - Software
     - TIA Portal V17
     - GXWorks3V1.097B
  
   * - Dirección IP de la tarjeta
     - "192.168.0.2"
     - "192.168.0.113"
  
   * - Dirección IP del PLC
     - IP no requiere mismo segmento de red
     - "192.168.0.15"(IP mismo segmento de red)
		
.. list-table:: 
   :widths: 20 40 40
   :header-rows: 1
   :align: center

   * - Protocolo
     - Ethernet/IP
     - EtherCAT

   * - Marca
     - Omron
     - Omron

   * - Modelo
     - NX102-1100
     - NX102-1100

   * - Firmware
     - V1.3
     - V1.3

   * - Software
     - SysmacStudioV1.50
     - SysmacStudioV1.50

   * - Dirección IP de la tarjeta
     - "192.168.0.112"
     - "192.168.0.2"

   * - Dirección IP del PLC
     - "192.168.0.88"(IP mismo segmento de red)
     - "192.168.0.88" (IP mismo segmento de red)
		
Profinet de Siemens
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

(1) Importación del archivo GSD (archivo XML)

Abrir el software de programación de Siemens TIA Portal V17, crear un nuevo proyecto de PLC, seleccionar "Dispositivos y redes" y, en el "Catálogo de hardware" de la derecha, hacer doble clic en 6ES7 515-2AM02-0AB0 para añadir el módulo de PLC.

.. image:: remote_mode/014.png
   :width: 6in
   :align: center

En la barra de menú del software TIA PORTAL, seleccionar "Opciones"->"Gestionar archivos de descripción de estación general (GSD)" para instalar o eliminar los archivos GSD ya instalados.

.. image:: remote_mode/015.png
   :width: 6in
   :align: center

Instalar el archivo GSD: como se ha indicado, seleccionar "Gestionar archivos de descripción de estación general (GSD)" y aparecerá la ventana "Gestionar archivo de descripción de estación general".

Seleccionar en "Ruta de origen" la carpeta donde se encuentra el archivo GSD que se desea instalar, seleccionar en la lista de archivos GSD mostrada uno o varios archivos que se deseen instalar y hacer clic en el botón "Instalar". Como se muestra en la figura siguiente.

.. image:: remote_mode/016.png
   :width: 6in
   :align: center

Tras una instalación correcta, se puede encontrar el dispositivo del archivo GSD instalado en el catálogo de hardware, en otros dispositivos de campo, como se muestra en la figura siguiente.

.. image:: remote_mode/017.png
   :width: 6in
   :align: center

Asignar IO: buscar el módulo en el catálogo y arrastrar Input y Output.

.. image:: remote_mode/018.png
   :width: 6in
   :align: center

Descargar el programa al dispositivo: hacer doble clic en "Dispositivos y redes" del árbol de proyectos de la izquierda, hacer clic con el botón derecho en el módulo "PLC_1", seleccionar "Descargar al dispositivo" en el menú desplegable y hacer clic en "Hardware y software (solo cambios)":

.. image:: remote_mode/019.png
   :width: 6in
   :align: center

Buscar y descargar el dispositivo: tras aparecer la ventana emergente, configurar el tipo de interfaz PG/PC como se muestra en la figura siguiente, hacer clic en iniciar búsqueda, seleccionar el dispositivo al que se desea descargar el programa y hacer clic en descargar:

.. image:: remote_mode/020.png
   :width: 6in
   :align: center

.. image:: remote_mode/021.png
   :width: 6in
   :align: center

CC-link de Mitsubishi
++++++++++++++++++++++++++++++++++++++++++++++++++++

(1) Importación del archivo de configuración
Abrir GxWorks3, seleccionar "Herramientas"→"Gestión de archivos de configuración"→"Iniciar sesión"; tras aparecer la ventana emergente, seleccionar el archivo de comunicación correspondiente y hacer clic en iniciar sesión para completar la importación del archivo de configuración.

.. image:: remote_mode/022.png
   :width: 6in
   :align: center

.. image:: remote_mode/023.png
   :width: 6in
   :align: center

.. image:: remote_mode/024.png
   :width: 6in
   :align: center

(2) Configuración de CC-Link IEF Basic

Crear el proyecto de PLC y activar el uso de CC-link: seleccionar "Puerto Ethernet" en el menú de navegación de la izquierda y configurar la dirección IP del PLC, garantizando que esté en el mismo segmento de red que la dirección de la tarjeta Hilscher. Hacer clic en "Uso de CC-link IEF Basic" y seleccionar "Usar".

.. image:: remote_mode/025.png
   :width: 6in
   :align: center

Configuración de red de CC-Link: igualmente en la configuración de CC-Link IEF Basic, seleccionar "Configuración de red" y seleccionar el módulo Hilscher CIFX Digital I/O como módulo. Arrastrarlo a la parte inferior izquierda de la vista para completar la configuración de hardware.

.. image:: remote_mode/026.png
   :width: 6in
   :align: center

Configuración de refresco de CC-Link: igualmente en la configuración de CC-Link IEF Basic, hacer clic en configuración de refresco y personalizar la configuración de transmisión: 256 bytes de recepción, 256 bytes de envío.

.. image:: remote_mode/027.png
   :width: 6in
   :align: center

(3) Descarga del programa

Tras abrir el programa de prueba, hacer clic en "En línea"→"Escribir en controlador programable" para entrar en la interfaz de descarga

.. image:: remote_mode/028.png
   :width: 6in
   :align: center

Tras abrir la interfaz de descarga, hacer clic en "Parámetros + programa" de la parte superior izquierda y, a continuación, hacer clic en "Ejecutar" de la esquina inferior derecha para descargar, esperando a que finalice la descarga.

.. image:: remote_mode/029.png
   :width: 6in
   :align: center

Ethernet/IP de Omron
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

(1) Crear un nuevo proyecto de PLC (este caso toma como ejemplo el modelo NX102-1100, PLC Omron 1.47):

.. image:: remote_mode/030.png
   :width: 6in
   :align: center

Crear variables globales:

.. image:: remote_mode/031.png
   :width: 6in
   :align: center

(2) Importación del archivo EDS

Hacer clic en "Herramientas"→"Configuración de conexión EtherNet/IP":

.. image:: remote_mode/032.png
   :width: 6in
   :align: center

Entrar en la configuración del PLC al que se desea conectar:

.. image:: remote_mode/033.png
   :width: 6in
   :align: center

En el espacio en blanco del grupo de etiquetas, hacer clic con el botón derecho para crear un nuevo grupo de etiquetas:

.. image:: remote_mode/034.png
   :width: 6in
   :align: center

Hacer clic con el botón derecho en el grupo de etiquetas recién creado y crear una etiqueta; la entrada y la salida son iguales, con una longitud de 256 bytes:

.. image:: remote_mode/035.png
   :width: 6in
   :align: center

.. image:: remote_mode/036.png
   :width: 6in
   :align: center

Entrar en la configuración de conexión; en el espacio en blanco de la caja de herramientas, hacer clic con el botón derecho y mostrar la biblioteca EDS:

.. image:: remote_mode/037.png
   :width: 6in
   :align: center

Instalar el archivo EDS:

.. image:: remote_mode/038.png
   :width: 6in
   :align: center

Hacer clic en "Caja de herramientas" "+" para añadir el dispositivo objetivo e introducir la dirección IP del dispositivo objetivo:

.. image:: remote_mode/039.png
   :width: 6in
   :align: center

Hacer clic en "Añadir" en la esquina inferior derecha; tras añadirlo correctamente, se muestra el dispositivo objetivo:

.. image:: remote_mode/040.png
   :width: 6in
   :align: center

(3) Configuración de parámetros de EtherNet/IP

Hacer clic con el botón derecho en el dispositivo objetivo añadido y hacer clic en "Editar":

.. image:: remote_mode/041.png
   :width: 6in
   :align: center

La longitud de mapeo de datos del dispositivo actual es de 256 bytes; cambiar 0001 y 0002 a 256 y confirmar:

.. image:: remote_mode/042.png
   :width: 6in
   :align: center

Hacer doble clic en el dispositivo objetivo, rellenar la entrada y la salida y seleccionar la variable inicial:

.. image:: remote_mode/043.png
   :width: 6in
   :align: center

(4) Descarga del programa

Abrir el programa de prueba, modificar la dirección IP del PLC para que esté en el mismo segmento de red que la tarjeta, descargar el programa y ejecutarlo.

EtherCAT de Omron
+++++++++++++++++++++++++++++++++++++++++++++++++

(1) Crear un nuevo proyecto de PLC (este caso toma como ejemplo el modelo NX102-1100, PLC Omron 1.47):

.. image:: remote_mode/044.png
   :width: 6in
   :align: center

Crear variables globales:

.. image:: remote_mode/045.png
   :width: 6in
   :align: center

(2) Importación del archivo XML

Hacer doble clic en "EtherCAT" para entrar en la interfaz de configuración del maestro y, con el botón derecho, seleccionar "Mostrar biblioteca ESI"

.. image:: remote_mode/046.png
   :width: 6in
   :align: center

.. image:: remote_mode/047.png
   :width: 6in
   :align: center

Seleccionar en la caja de herramientas de la derecha el dispositivo objetivo añadido y hacer doble clic para añadir el esclavo:

.. image:: remote_mode/048.png
   :width: 6in
   :align: center

(3) Configuración del esclavo EtherCAT

Configurar el esclavo "Reloj distribuido válido" como "Iniciar DC":

.. image:: remote_mode/049.png
   :width: 6in
   :align: center

(4) Mapeo de I/O

Hacer doble clic en "Mapeo de I/O" para vincular las variables con las direcciones:

.. image:: remote_mode/050.png
   :width: 6in
   :align: center

(5) Descarga del programa

Abrir el programa de prueba, modificar la dirección IP del PLC para que esté en el mismo segmento de red que la tarjeta, descargar el programa y ejecutarlo.

Descripción de las operaciones relacionadas con el modo remoto del robot
----------------------------------------------------------------------------

(1) Introducir en el navegador la IP 192.168.58.2, con cuenta admin y contraseña 123; hacer clic en "Iniciar sesión" para entrar en la interfaz Web de la caja de control del robot.

.. image:: remote_mode/051.png
   :width: 6in
   :align: center

.. centered:: Figura 18.2-14 Interfaz Web de la caja de control

(2) Hacer clic en "Configuración del sistema"->"Acerca de"->interfaz de actualización de software; hacer clic en el botón "Actualizar", cargar el paquete de software que se desea actualizar y hacer clic en "Actualizar" para comenzar la actualización; tras completarla, reiniciar la caja de control.

.. image:: remote_mode/052.png
   :width: 6in
   :align: center

.. centered:: Figura 18.2-15 Actualización de software

(3) Hacer clic en el botón de expansión de la esquina superior derecha para abrir la barra de menú y hacer clic en modo local para cambiar al modo remoto.

.. image:: remote_mode/053.png
   :width: 4in
   :align: center

.. centered:: Figura 18.2-16 Cambio al modo remoto

(4) Seleccionar el protocolo de esclavo del controlador y si se necesita la función de inicio automático, y hacer clic en el botón "Configurar".

.. image:: remote_mode/054.png
   :width: 6in
   :align: center

.. centered:: Figura 18.2-17 Configuración del protocolo de comunicación

.. note:: Para conmutar a un protocolo diferente, es necesario hacer clic primero en el botón "Desinstalar" y, a continuación, realizar la configuración de otros protocolos.   

Actualización del firmware de la tarjeta
----------------------------------------------------------------------------

Tarjeta FRH-PCIeN-EC/EIP/CC/PN-RJ-V10
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

（1）Seleccionar el paquete de firmware que se desea actualizar, con el nombre BoardFirm_xxx.tar.gz, y hacer clic en el botón "Actualizar", esperando a que finalice la actualización;

.. image:: remote_mode/056.png
   :width: 3in
   :align: center

.. centered:: Figura 18.3-1 Paquete de actualización de firmware

（2）Tras completar la actualización, reiniciar la caja de control;

.. image:: remote_mode/057.png
   :width: 6in
   :align: center

.. centered:: Figura 18.3-2 Actualización completada
   
（3）Reiniciar la caja de control; si aparece el mensaje de advertencia mostrado en la figura, significa que la actualización de firmware ha fallado. Tras borrar dicha advertencia, volver a realizar la operación de actualización.

.. image:: remote_mode/058.png
   :width: 3in
   :align: center

.. centered:: Figura 18.3-3 Fallo de la actualización de firmware

Apéndice
-------------------

Lista de instrucciones
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table:: 
   :widths: 20 80
   :header-rows: 1
   :align: center

   * - Código de comando
     - Descripción de la instrucción

   * - 0x1000
     - Habilitación del robot

   * - 0x1001
     - Restablecer todos los errores

   * - 0x1002
     - Detener el movimiento del robot

   * - 0x1003
     - Leer la posición real

   * - 0x1004
     - Establecer la velocidad del robot

   * - 0x1005
     - Reanudar el movimiento del robot

   * - 0x1006
     - Pausar el movimiento del robot

   * - 0x1007
     - Calcular la posición cartesiana a partir de la posición articular

   * - 0x1008
     - Calcular la posición articular a partir de la posición cartesiana

   * - 0x2000
     - Escribir información de la herramienta

   * - 0x2001
     - Leer información de la herramienta

   * - 0x2002
     - Escribir información de la pieza

   * - 0x2003
     - Leer información de la pieza

   * - 0x2004
     - Escribir información de la carga

   * - 0x2005
     - Leer información de la carga

   * - 0x2006
     - Escribir información de dinámica de referencia

   * - 0x2007
     - Leer información de dinámica de referencia

   * - 0x2008
     - Escribir información de dinámica predeterminada

   * - 0x2009
     - Leer información de dinámica predeterminada

   * - 0x2010
     - Escribir información de límite suave

   * - 0x2011
     - Leer información de límite suave

   * - 0x3000
     - MoveAxes (basado en ángulos articulares)

   * - 0x3001
     - MoveLinear

   * - 0x3002
     - MoveDirect (basado en el sistema de coordenadas cartesiano)

   * - 0x3003
     - Movimiento jog

   * - 0x3004
     - Parada de jog