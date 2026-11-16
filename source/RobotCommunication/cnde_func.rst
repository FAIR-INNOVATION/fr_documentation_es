Operaciones de funciones CNDE
=================================================

Configuración de entrada y datos de entrada
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

El cliente envía tramas de datos al robot a través de CNDE para controlar las salidas DO y AO del robot, los registros de entrada, etc. Antes de enviar los datos de entrada, es necesario configurar primero el contenido de las funciones que se van a controlar. La Tabla 2-1 muestra el formato del contenido de configuración de entrada de CNDE, que incluye el número de receta y una serie de nombres de funciones de configuración de entrada (Tabla 1-2); la Tabla 3-2 correspondiente muestra el formato del contenido de los datos de entrada, que incluye el número de receta y el grupo de bytes de datos de entrada.

La entrada de datos de CNDE admite hasta 8 recetas. Al enviar los datos de entrada, el robot emparejará, según el número de receta de los datos recibidos, el grupo de nombres de funciones de configuración de receta correspondiente, y analizará los datos para obtener el valor de los datos de entrada de cada nombre de función, controlando así el robot según los datos de entrada.

.. centered:: Tabla 3-1 Formato del contenido de configuración de entrada

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nombre**
     - **Número de receta**
     - **Cadena de nombres de funciones**

   * - Longitud (byte)
     - 1
     - --

   * - Contenido
     - 0 ~ 7
     - Una serie de nombres de funciones de datos de entrada

.. centered:: Tabla 3-2 Formato del contenido de los datos de entrada

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nombre**
     - **Número de receta**
     - **Grupo de bytes de datos**

   * - Longitud (byte)
     - 1
     - --

   * - Contenido
     - 0 ~ 7
     - Contenido de los datos de entrada

Durante la configuración de entrada, tras recibir el grupo de nombres de configuración, el controlador del robot validará cada nombre. Si los nombres de funciones configurados son correctos, el robot devolverá los nombres de los tipos de datos de todas las funciones configuradas separados por ","; si los nombres de funciones configurados son incorrectos, el robot devolverá el contenido de error correspondiente. A continuación se muestra un ejemplo de trama de datos de configuración de entrada (hexadecimal):

.. image:: cnde/001.png
   :width: 6in
   :align: center

En él, la longitud total del grupo de nombres de funciones de entrada configurado es de 54 bytes; añadiendo 1 byte del número de receta de entrada, son 55 bytes en total, que en hexadecimal es 0x0037. En modo little-endian, la longitud de datos correspondiente en la trama de datos de entrada es "37 00".

En este momento, el robot devolverá una trama de datos de tipo mensaje de aviso de caracteres (mensaje de aviso de caracteres de la sección 3.3.1 de este documento):

.. image:: cnde/002.png
   :width: 6in
   :align: center

El tipo de mensaje "00" indica que se trata de un mensaje de respuesta de ejecución correcta. El cliente puede extraer el "tipo de configuración de datos de entrada" y compararlo con la Tabla 1-3 para obtener la longitud en bytes de la configuración de entrada; en este ejemplo, la longitud total de datos es 1*5+4*30+8*30 = 365 bytes.

Si el nombre de la configuración de entrada es incorrecto:

.. image:: cnde/003.png
   :width: 6in
   :align: center

La información de respuesta correspondiente es:

.. image:: cnde/004.png
   :width: 6in
   :align: center

Los datos de entrada pueden introducirse cíclicamente según un período determinado, o introducirse solo cuando sea necesario. En la entrada cíclica, el período más rápido que el robot puede procesar es de 1 ms, pero un período de entrada más rápido conlleva cierto consumo de recursos del sistema del robot; se recomienda configurar razonablemente el período de entrada de datos según la situación real.

Además, al enviar tramas de datos al robot, el robot no devolverá información de respuesta, salvo que la longitud de la trama de datos enviada o los datos sean anómalos. A continuación se muestra un ejemplo de trama de datos de entrada, en la que el número de receta de los datos de entrada y la longitud del grupo de bytes de datos de entrada deben coincidir con la configuración de entrada:

.. image:: cnde/005.png
   :width: 6in
   :align: center

Configuración de salida y datos de salida
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

El cliente puede personalizar el contenido y el período de la retroalimentación de estado según sea necesario para obtener la retroalimentación de estado del robot a través de CNDE. El uso de la retroalimentación de estado CNDE del robot requiere los siguientes tres pasos: ① configuración de salida; ② inicio de la salida; ③ recepción de los datos de salida.

Configuración de salida
+++++++++++++++++++++++

El contenido de la trama de configuración de salida incluye el período de salida y el grupo de nombres de funciones de salida (todos los nombres configurables se muestran en la Tabla 1-1). El rango configurable del período de salida es de 1 ~ 200 ms, y el número máximo de bytes de datos de salida admitido es de 4096 bytes. El grupo de nombres de funciones de salida es una serie de cadenas de nombres de funciones de salida separadas por ",". Tras enviar el cliente la trama de configuración de salida, el robot validará los nombres de funciones configurados. Si todos los nombres de funciones configurados son nombres de funciones admitidos actualmente por el CNDE del robot, el robot devolverá una serie de combinaciones de tipos de datos separadas por ","; de lo contrario, si falla la validación de los nombres de configuración de salida, se devolverá la información de error correspondiente.

.. centered:: Tabla 3-3 Contenido de la configuración de salida

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nombre**
     - **Período de salida (ms)**
     - **Cadena de nombres de funciones**

   * - Longitud (byte)
     - 2
     - --

   * - Contenido
     - 1-200
     - Grupo de nombres de funciones de salida

Por ejemplo, la trama de configuración de salida es la siguiente:

.. image:: cnde/006.png
   :width: 6in
   :align: center

En ella, la longitud total del grupo de nombres de funciones de salida configurado es de 48 bytes; añadiendo 2 bytes del período de salida, son 50 bytes en total, que en hexadecimal es 0x0032. En modo little-endian, la longitud de datos correspondiente en la trama de datos de entrada es "32 00".

En este momento, el robot devolverá una trama de datos de tipo mensaje de aviso de caracteres (mensaje de aviso de caracteres de la sección 3.3.1 de este documento):

.. image:: cnde/007.png
   :width: 6in
   :align: center

El tipo de mensaje "00" indica que se trata de un mensaje de respuesta de ejecución correcta. El cliente puede extraer el "tipo de configuración de datos de salida" y compararlo con la Tabla 1-3 para obtener la longitud en bytes de la configuración de salida; en este ejemplo, la longitud total de datos es 1+8*10+4 = 85 bytes.

Si el nombre de la configuración de entrada es incorrecto, por ejemplo, si "queue" se escribe erróneamente como "quene":

.. image:: cnde/008.png
   :width: 6in
   :align: center

La información de respuesta correspondiente es:

.. image:: cnde/009.png
   :width: 6in
   :align: center

Inicio y parada de la salida
+++++++++++++++++++++++++++++++++++++++

Una vez completada la configuración de salida CNDE del robot, se envía la instrucción de inicio de salida CNDE y el robot realizará la retroalimentación de estado de salida según el período y el contenido de salida configurados. Del mismo modo, al enviar la instrucción de parada de salida CNDE, el robot detendrá la retroalimentación de estado de salida. Las instrucciones de inicio y parada de CNDE no tienen contenido de instrucción, y la longitud de datos correspondiente es 0.

.. centered:: Tabla 3-4 Contenido de inicio y parada de salida CNDE

.. list-table::
   :widths: 40 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nombre**
     - **Grupo de bytes de datos**

   * - Longitud (byte)
     - 0

   * - Contenido
     - Ninguno

A continuación se muestra un ejemplo de trama de datos de inicio de salida CNDE del robot:

.. image:: cnde/010.png
   :width: 3in
   :align: center

Recepción de datos de salida por el cliente
+++++++++++++++++++++++++++++++++++++++++++++++++++

Una vez iniciada la salida de datos CNDE del robot, el cliente necesita recibir cíclicamente la información de datos devuelta por el robot, y la frecuencia de recepción cíclica del cliente debe ser superior a la frecuencia de los datos de salida configurados; de lo contrario, pueden producirse pérdidas de paquetes. El contenido de los datos de salida del robot se muestra en la Tabla 3-5; la longitud del grupo de bytes de datos de salida del robot es la suma de las longitudes en bytes de todos los datos de funciones de la configuración de salida, y el array de bytes es la combinación de todos los datos de estado alineados a 1 byte en el orden de las funciones configuradas.

.. centered:: Tabla 3-5 Contenido de los datos de salida CNDE

.. list-table::
   :widths: 40 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nombre**
     - **Grupo de bytes de datos**

   * - Longitud (byte)
     - --

   * - Contenido
     - Grupo de bytes de datos de salida

A continuación se muestra un ejemplo de trama de datos de salida del robot:

.. image:: cnde/011.png
   :width: 4in
   :align: center

Funciones auxiliares de CNDE
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Mensajes de aviso de caracteres
++++++++++++++++++++++++++++++++++++++++++++++++++++++

El cliente y el robot pueden enviarse mutuamente mensajes de aviso de caracteres a través de CNDE. El contenido del mensaje incluye el tipo de mensaje y la cadena del mensaje (Tabla 3-6), y la definición del tipo de mensaje se muestra en la Tabla 3-7. Cuando el cliente CNDE envía al robot instrucciones como configuración de entrada, configuración de salida, inicio de salida, parada de salida, etc., el robot responde con un mensaje de aviso de caracteres.

Si la instrucción anterior se ejecuta correctamente, el tipo de mensaje de respuesta del robot es "éxito", con el código numérico de tipo de mensaje 0x00; por el contrario, si la instrucción anterior falla en su ejecución, el tipo de mensaje de respuesta del robot es "error", con el valor numérico de tipo de mensaje 0x03. El cliente puede determinar el resultado de la ejecución de la instrucción según el tipo de mensaje de respuesta; si el tipo de mensaje es "error", puede extraer la información de error para analizar la causa del error.

.. centered:: Tabla 3-6 Contenido de los mensajes de aviso de caracteres

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nombre**
     - **Tipo de mensaje**
     - **Cadena del mensaje**

   * - Longitud (byte)
     - 1
     - --

   * - Contenido
     - 0 ~ 4
     - Cadena del mensaje

.. centered:: Tabla 3-7 Tipos de mensajes de aviso de caracteres CNDE del robot

.. list-table::
   :widths: 40 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Tipo**
     - **Valor**

   * - Éxito
     - 0x00

   * - Información
     - 0x01

   * - Advertencia
     - 0x02

   * - Error
     - 0x03

   * - Fallo
     - 0x04

Cambio del número de versión del protocolo CNDE del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Actualmente, el CNDE del robot solo tiene una versión, con número de versión "FR-CNDE-V0001", por lo que esta función es una función reservada y aún no está disponible.

Obtención de la información de versión del software y firmware del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

El cliente envía al robot a través de CNDE la instrucción de obtención de la información de versión del software y firmware. El contenido de la instrucción está vacío. Tras recibir la solicitud, el robot devuelve un mensaje de aviso de caracteres cuyo contenido incluye información relacionada como el modelo del robot, la versión del software del robot, la versión del firmware del robot y la versión del hardware del robot.

Obtención de datos periódicos de la función de transmisión transparente del extremo (CNDE)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Descripción de la configuración CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Una vez activada la función de transmisión transparente del extremo, se puede configurar en CNDE la opción "axle_gen_com_data" y su período, para obtener los datos periódicos de los periféricos leídos por el extremo. La trama de datos de respuesta se define a continuación.

.. centered:: Tabla 3-8  Definición del protocolo de respuesta CNDE de datos periódicos de la función de transmisión transparente del extremo

.. list-table::
   :widths: 30 30 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Byte 1**
     - **Byte 2**
     - **Byte 3-130**

   * - ErrorCode
     - Len
     - Data

   * - 0-Comunicación normal
     - Longitud de los datos periódicos
     - Búfer de la trama de datos

   * - 1-Comunicación anómala entre el extremo y el robot
     - La longitud se pone a cero cuando el código de error no es 0
     - El búfer se pone a cero cuando el código de error no es 0

   * - 2-Comunicación 485 del extremo anómala	
     - 
     - 

Tomando como ejemplo la configuración de datos periódicos del periférico cabezal de moxibustión Beiyikang, el código muestra la configuración para obtener los datos de transmisión transparente periódicos del extremo, con un período de obtención de 50 ms.

Esquema del código de configuración CNDE de transmisión transparente del extremo:

.. code-block:: 
    :linenos:

    tring outputCfg = "axle_gen_com_data";    //Obtener los datos periódicos de transmisión transparente del extremo
    byte[] sendBuffer = new byte[] { };
    byte[] cfgBuffer = Encoding.UTF8.GetBytes(outputCfg);
    CNDEPkg pkg  = new CNDEPkg();
    pkg.type = 1;  //Configuración de salida
    pkg.len = (ushort)(2 + outputCfg.Length);
    pkg.data.Clear();
    UInt16 period = 50;   //actualización cada 50ms
    byte[] periodBt = new byte[2] {0, 0};
    Int16ToByte(period, ref periodBt);
    pkg.data.AddRange(periodBt);  //Período de comunicación
    pkg.data.AddRange(cfgBuffer); 
    pkg.ToBytes(ref sendBuffer);

Ejemplo de código de desempaquetado de datos periódicos del cabezal de moxibustión Beiyikang basado en CNDE:
  
.. code-block:: 
    :linenos:

    if (pkg.type == 4)
    {
        int size = Marshal.SizeOf(putDate);
        IntPtr structPtr = Marshal.AllocHGlobal(size);
        Marshal.Copy(pkg.data.ToArray(), 0, structPtr, size);
        putDate = (OUTPKG)Marshal.PtrToStructure(structPtr, typeof(OUTPKG));

        int errorcode = putDate.axle_gen_com_data[0];
        int datalen = putDate.axle_gen_com_data[1];
        // Filtrar paquetes anómalos
        if ((errorcode != 0) || (datalen == 0) ||
        (putDate.axle_gen_com_data[2] != 0xAB) || 
        (putDate.axle_gen_com_data[3] != 0xBA))
        {
            Console.WriteLine($"rcv data is error");
            continue;
        }
        // Empaquetar según el protocolo del cabezal de moxibustión Beiyikang
        int curTem = putDate.axle_gen_com_data[6];
        int targetTem = putDate.axle_gen_com_data[7];
        int genData1 = putDate.axle_gen_com_data[8] << 8 | putDate.axle_gen_com_data[9];
        int genData2 = putDate.axle_gen_com_data[10] << 8 | putDate.axle_gen_com_data[11];
        int genData3 = putDate.axle_gen_com_data[12] << 8 | putDate.axle_gen_com_data[13];
        int genData4 = putDate.axle_gen_com_data[14] << 8 | putDate.axle_gen_com_data[15];
        int genData5 = putDate.axle_gen_com_data[16] << 8 | putDate.axle_gen_com_data[17];
        int genData6 = putDate.axle_gen_com_data[18] << 8 | putDate.axle_gen_com_data[19];

        Console.WriteLine($"the data is errorcode {errorcode};  datalen  {datalen}  curTem  {curTem}; targetTem  {targetTem}  genData1  {genData1}  genData2  {genData2}  genData3  {genData3}  genData4  {genData4}  genData5  {genData5}  genData6  {genData6}  ");
        udpClient.Client.ReceiveTimeout = 100;
        Marshal.FreeHGlobal(structPtr);
    }

Ejemplo de código de comunicación de datos no periódicos del cabezal de moxibustión Beiyikang basado en la función de transmisión transparente del extremo:
  
.. code-block:: 
    :linenos:

    void testAxleGenCom()
    {
        int[] led_on = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79 };
        int[] led_off = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
        int[] version = new int[5]{ 0xAB, 0xBA, 0x11, 0x00, 0x76 };
        int[] state = new int[6] { 0xAB, 0xBA, 0x1B,0x01, 0xAA, 0x2B };
        int[] cycleState = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };

        int[] rcvdata = new int[16];
        int ret = 0;
        int cnt = 1;

        JointPos p1Joint = new JointPos(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
        DescPose p1Desc = new DescPose(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);

        JointPos p2Joint = new JointPos(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
        DescPose p2Desc = new DescPose(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        //Activar la función de transmisión transparente del extremo
        robot.SetAxleGenComEnable(1);
        robot.SetAxleLuaEnable(1);

        while(cnt<=10)
        { 
            //Leer el número de versión
            ret = robot.SndRcvAxleGenComCmdData(5, version, 10, ref rcvdata);
            Console.WriteLine($" hard version : {rcvdata[4]},hard code:{rcvdata[5]}, soft version:{rcvdata[6]} {rcvdata[7]}, soft code:{rcvdata[8]}");
            if (ret != 0)
            {
                break;
            }
            Thread.Sleep(1000);
            //Leer el estado de presencia del cabezal de moxibustión
            ret = robot.SndRcvAxleGenComCmdData(6, state, 6, ref rcvdata);
            Console.WriteLine($" state : {rcvdata[4]}");
            Thread.Sleep(1000);
            //Encender el láser del cabezal de moxibustión
            ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, ref rcvdata);
            Console.WriteLine($"led on rcv data is: {rcvdata[0]},{rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}");
            robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
            Thread.Sleep(4000);
            //Apagar el láser del cabezal de moxibustión
            ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, ref rcvdata);
            Console.WriteLine($"led off rcv data is: {rcvdata[0]},{rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}");
            robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
            Thread.Sleep(1000);
            Console.WriteLine($"***********************complate No. {cnt}  SDK test*****************************");
            cnt++;
        }

    }