Conceptos básicos del robot
=====================================

.. toctree:: 
    :maxdepth: 5

Instanciación del robot
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Constructor de la clase de interfaz del robot
    */
    Robot(); 

Establecer comunicación con el controlador
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer comunicación con el controlador del robot
    * @param  [in] ip  Dirección IP del controlador, por defecto de fábrica 192.168.58.2
    * @return Código de error
    */
    int RPC(string ip);

Desconectar la comunicación con el robot
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Desconectar la comunicación con el controlador del robot 
    * @return Código de error 
    */ 
    int CloseRPC(); 

Consultar el número de versión del SDK
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Consultar el número de versión del SDK 
    * @param [out] version Número de versión del SDK 
    * @return Código de error 
    */  
    int GetSDKVersion(ref string version);

Obtener la IP del controlador
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la IP del controlador
    * @param  [out] ip  IP del controlador
    * @return  Código de error
    */
    int GetControllerIP(ref string ip);

Controlar la entrada o salida del modo de enseñanza por arrastre del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Controlar la entrada o salida del modo de enseñanza por arrastre del robot
    * @param  [in] state 0-salir del modo de enseñanza por arrastre, 1-entrar en el modo de enseñanza por arrastre
    * @return  Código de error
    */
    int DragTeachSwitch(byte state);

Consultar si el robot está en modo de arrastre
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Consultar si el robot está en modo de enseñanza por arrastre
    * @param  [out] state 0-modo de enseñanza por arrastre no activo, 1-modo de enseñanza por arrastre activo
    * @return  Código de error
    */
    int IsInDragTeach(ref byte state); 

Controlar la habilitación o deshabilitación del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Controlar la habilitación o deshabilitación del robot; tras el encendido, el robot se habilita automáticamente por defecto
    * @param  [in] state  0-deshabilitar, 1-habilitar
    * @return  Código de error
    */
    int RobotEnable(byte state); 

Controlar el cambio de modo manual/automático del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Controlar el cambio de modo manual/automático del robot
    * @param [in] mode 0-modo automático, 1-modo manual
    * @return Código de error
    */
    int Mode(int mode);

Apagar el sistema operativo del robot
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Apagar el sistema operativo del robot
    * @return Código de error
    */
    int ShutDownRobotOS();

Ejemplo de código
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button6_Click(object sender, EventArgse)
    {   
        int rtn = robot.ShutDownRobotOS();
        Console.WriteLine($"ShutDownRobotOS rtn is {rtn}");
    }

Establecer los parámetros de reconexión de comunicación con el robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer los parámetros de reconexión de comunicación con el robot
    * @param [in] enable Si se activa true-habilitar, false-no habilitar
    * @param [in] times Número de reconexiones
    * @param [in] period Intervalo de tiempo entre reconexiones (milisegundos)
    */
    void SetReconnectParam(bool enable, int times, int period);

Ejemplo de código
+++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnStandard_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true, 100, 20000);//parámetros de reconexión tras desconexión
        robot.RPC("192.168.58.2"); 

        string ip = "";
        string version = "";
        byte state = 0;

        robot.GetSDKVersion(ref version);
        Console.WriteLine($"SDK version : {version}");
        robot.GetControllerIP(ref ip);
        Console.WriteLine($"controller ip : {ip}");

        robot.Mode(1);
        Thread.Sleep(1000);
        robot.DragTeachSwitch(1);
        int rtn = robot.IsInDragTeach(ref state);
        Console.WriteLine($"drag state : {state}");
        Thread.Sleep(3000);
        robot.DragTeachSwitch(0);
        Thread.Sleep(1000);
        robot.IsInDragTeach(ref state);
        Console.WriteLine($"drag state : {state}");
        Thread.Sleep(3000);
        robot.RobotEnable(0);
        Thread.Sleep(3000);
        robot.RobotEnable(1);

        robot.Mode(0);
        Thread.Sleep(1000);
        robot.Mode(1);

        rtn = robot.HiSpeedManualSwitch(1);
        Console.WriteLine($"change high speed mode {rtn}");
        Thread.Sleep(10000);

        rtn = robot.HiSpeedManualSwitch(0);
        Console.WriteLine($"change low speed mode {rtn}");
        Thread.Sleep(1000);
    }

Inicializar los parámetros del registro
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Inicializar los parámetros del registro
    * @param [in] logType：modo de salida, DIRECT-salida directa; BUFFER-salida en búfer; ASYNC-salida asíncrona
    * @param [in] logLevel：nivel de filtrado del registro, ERROR-error; WARNING-advertencia; INFO-información; DEBUG-depuración
    * @param [in] filePath: ruta de guardado del archivo, como "D://Log/"
    * @param [in] saveFileNum：número de archivos a guardar; los archivos que superen tanto el número de archivos a guardar como los días de guardado se eliminarán
    * @param [in] saveDays: días de guardado de archivos; los archivos que superen tanto el número de archivos a guardar como los días de guardado se eliminarán
    * @return Código de error
    */
    int LoggerInit(FrLogType logType = FrLogType.DIRECT, FrLogLevel logLevel = FrLogLevel.INFO, string filePath = "", int saveFileNum = 10, int saveDays = 10);

Establecer el nivel de filtrado del registro
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el nivel de filtrado del registro
    * @param [in] logLevel: nivel de filtrado del registro, ERROR-error; WARNING-advertencia; INFO-información; DEBUG-depuración
    * @return Código de error
    */
    int SetLoggerLevel(FrLogLevel logLevel);

Obtener la versión del software del robot
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la información de la versión del software del robot
    * @param [out] robotModel Modelo del robot
    * @param [out] webVersion Versión web
    * @param [out] controllerVersion Versión del controlador
    * @return Código de error 
    */ 
    int GetSoftwareVersion(ref string robotModel, ref string webVersion, ref string controllerVersion);
    
Obtener la versión del hardware del robot
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la información de la versión del hardware del robot
    * @param [out] ctrlBoxBoardVersion Versión de hardware de la placa base del armario de control
    * @param [out] driver1Version Versión de hardware del accionamiento 1
    * @param [out] driver1Version Versión de hardware del accionamiento 2
    * @param [out] driver1Version Versión de hardware del accionamiento 3
    * @param [out] driver1Version Versión de hardware del accionamiento 4
    * @param [out] driver1Version Versión de hardware del accionamiento 5
    * @param [out] driver1Version Versión de hardware del accionamiento 6
    * @param [out] endBoardVersion Versión de hardware de la placa del extremo
    * @return Código de error 
    */ 
    int GetHardwareVersion(ref string ctrlBoxBoardVersion, ref string driver1Version, ref string driver2Version, ref string driver3Version,ref string driver4Version, ref string driver5Version, ref string driver6Version, ref string endBoardVersion);

Obtener la versión del firmware del robot
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la información de la versión del firmware del robot
    * @param [out] ctrlBoxBoardVersion Versión de firmware de la placa base del armario de control
    * @param [out] driver1Version Versión de firmware del accionamiento 1
    * @param [out] driver1Version Versión de firmware del accionamiento 2
    * @param [out] driver1Version Versión de firmware del accionamiento 3
    * @param [out] driver1Version Versión de firmware del accionamiento 4
    * @param [out] driver1Version Versión de firmware del accionamiento 5
    * @param [out] driver1Version Versión de firmware del accionamiento 6
    * @param [out] endBoardVersion Versión de firmware de la placa del extremo
    * @return Código de error 
    */ 
    int GetFirmwareVersion(ref string ctrlBoxBoardVersion, ref string driver1Version, ref string driver2Version, ref string driver3Version,ref string driver4Version, ref string driver5Version, ref string driver6Version, ref string endBoardVersion);

Ejemplo de código
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnGetVersions_Click(object sender, EventArgs e)
    {
        string[] ver = new string[20];
        int rtn = 0;
        rtn = robot.GetSoftwareVersion(ref ver[0], ref ver[1], ref ver[2]);
        rtn = robot.GetHardwareVersion(ref ver[3], ref ver[4], ref ver[5], ref ver[6], ref ver[7], ref ver[8], ref ver[9], ref ver[10]);
        rtn = robot.GetFirmwareVersion(ref ver[11], ref ver[12], ref ver[13], ref ver[14], ref ver[15], ref ver[16], ref ver[17], ref ver[18]);
        Console.WriteLine($"robotmodel  is: {ver[0]}");
        Console.WriteLine($"webVersion  is: {ver[1]}");
        Console.WriteLine($"controllerVersion  is: {ver[2]}");
        Console.WriteLine($"Hard ctrlBox Version  is: {ver[3]}");
        Console.WriteLine($"Hard driver1 Version  is: {ver[4]}");
        Console.WriteLine($"Hard driver2 Version  is: {ver[5]}");
        Console.WriteLine($"Hard driver3 Version  is: {ver[6]}");
        Console.WriteLine($"Hard driver4 Version  is: {ver[7]}");
        Console.WriteLine($"Hard driver5 Version  is: {ver[8]}");
        Console.WriteLine($"Hard driver6 Version  is: {ver[9]}");
        Console.WriteLine($"Hard end Version  is: {ver[10]}");
        Console.WriteLine($"Firm ctrlBox Version  is: {ver[11]}");
        Console.WriteLine($"Firm driver1 Version  is: {ver[12]}");
        Console.WriteLine($"Firm driver2 Version  is: {ver[13]}");
        Console.WriteLine($"Firm driver3 Version  is: {ver[14]}");
        Console.WriteLine($"Firm driver4 Version  is: {ver[15]}");
        Console.WriteLine($"Firm driver5 Version  is: {ver[16]}");
        Console.WriteLine($"Firm driver6 Version  is: {ver[17]}");
        Console.WriteLine($"Firm end Version  is: {ver[18]}");
    }
    
Cambiar al modo manual de alta velocidad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Cambiar al modo manual de alta velocidad
    * @param [in] state 0-salir de la alta velocidad manual; 1-entrar en la alta velocidad manual
    * @return Código de error
    */
    public int HiSpeedManualSwitch(int state)