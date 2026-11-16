Formato del protocolo de tramas de datos CNDE
=============================================================

El protocolo de comunicación CNDE del robot colaborativo es el siguiente. Tanto el envío de datos del cliente al robot como la retroalimentación de datos del robot al cliente deben seguir este protocolo; el protocolo distingue las tramas de datos de diferentes funciones mediante el tipo de trama, y la definición del tipo de trama se muestra en la Tabla 2-2; los diferentes tipos de trama corresponden a contenidos de datos diferentes, y la definición específica del contenido de datos se muestra en las Tablas 3-1 ~ 3-7.

.. centered:: Tabla 2-1 Formato de la trama de datos CNDE del robot

.. list-table::
   :widths: 20 20 20 20 20 20 20
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nombre**
     - **Cabecera de trama**
     - **Contador de trama**
     - **Tipo de trama**
     - **Longitud de datos**
     - **Contenido**
     - **Cola de trama**
   
   * - **Longitud (byte)**
     - 2
     - 1
     - 1
     - 2
     - --
     - 2
   
   * - **Contenido**
     - 0x5A5A
     - 0 ~ 255
     - 0 ~ 8
     - Número de bytes del "contenido de datos"
     - Contenido de la trama de datos
     - 0xA5A5

.. centered:: Tabla 2-2 Tipos de tramas de datos CNDE del robot

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Tipo**
     - **Valor**
     - **Dirección de la trama de datos**

   * - Trama de configuración de entrada (configuración de control)
     - 0x00
     - Client->Robot

   * - Trama de configuración de salida (configuración de estado)
     - 0x01
     - Client->Robot

   * - Inicio de salida CNDE
     - 0x02
     - Client->Robot

   * - Parada de salida CNDE
     - 0x03
     - Client->Robot

   * - Trama de datos de salida (datos de estado)
     - 0x04
     - Robot->Client

   * - Trama de datos de entrada (datos de control)
     - 0x05
     - Client->Robot

   * - Mensaje de aviso de caracteres
     - 0x06
     - Client->Robot, Robot->Client

   * - Establecer el número de versión del protocolo CNDE del robot
     - 0x07
     - Client->Robot

   * - Obtener la versión de software y firmware del robot
     - 0x08
     - Client->Robot, Robot->Client