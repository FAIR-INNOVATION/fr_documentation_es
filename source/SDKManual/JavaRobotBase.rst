Fundamentos del robot
=============================

.. toctree:: 
    :maxdepth: 5

Instanciar el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Constructor de la clase de interfaz del robot
    */
    Robot robot = new Robot(); 

Establecer comunicación con el controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer comunicación con el controlador del robot
    * @param  [in] ip  Dirección IP del controlador, valor predeterminado de fábrica 192.168.58.2
    * @return Código de error
    */
    int RPC(String ip);

Cerrar la comunicación con el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Cerrar la comunicación con el robot
    * @return Código de error 
    */ 
    int CloseRPC(); 

Consultar el número de versión del SDK
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Consultar el número de versión del SDK 
    * @return Número de versión 
    */  
    String GetSDKVersion();

Obtener la IP del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la IP del controlador
    * @param  [out] ip  IP del controlador
    * @return  Código de error
    */
    int GetControllerIP(String[] ip);

Controlar la entrada o salida del modo de enseñanza por arrastre del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Controlar la entrada o salida del modo de enseñanza por arrastre del robot
    * @param  [in] state 0-salir del modo de enseñanza por arrastre, 1-entrar en el modo de enseñanza por arrastre
    * @return  Código de error
    */
    int DragTeachSwitch(int state);

Consultar si el robot está en modo de enseñanza por arrastre
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Consultar si el robot está en modo de enseñanza por arrastre
    * @param  [in] state 0-modo no de enseñanza por arrastre, 1-modo de enseñanza por arrastre
    * @return  Código de error
    */
    int IsInDragTeach(List<Number> state);

Controlar la habilitación o deshabilitación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Controlar la habilitación o deshabilitación del robot; tras el encendido, el robot se habilita automáticamente de forma predeterminada
    * @param  [in] state  0-deshabilitar, 1-habilitar
    * @return  Código de error
    */
    int RobotEnable(int state); 

Controlar el cambio de modo manual/automático del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Controlar el cambio de modo manual/automático del robot
    * @param [in] mode 0-modo automático, 1-modo manual
    * @return Código de error
    */
    int Mode(int mode);

Apagar el sistema operativo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Apagar el sistema operativo del robot
    * @return Código de error
    */
    int ShutDownRobotOS();

Establecer los parámetros de reconexión de comunicación con el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer los parámetros de reconexión de comunicación con el robot
    * @param [in] enable Si se habilita, true:habilitar, false:no habilitar
    * @param [in] times Número de reconexiones
    * @param [in] period Intervalo de tiempo de reconexión
    * @return Código de error
    */
    int SetReconnectParam(boolean enable, int times, int period);

Inicializar los parámetros del registro
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicializar los parámetros del registro
    * @param [in] logType Modo de salida, DIRECT-salida directa; BUFFER-salida con búfer; ASYNC-salida asíncrona
    * @param [in] logLevel Nivel de filtrado del registro, ERROR-error; WARNING-advertencia; INFO-información; DEBUG-depuración
    * @param [in] filePath Ruta de guardado del archivo, como "D://Log/"
    * @param [in] saveFileNum Número de archivos a guardar; los archivos que superen simultáneamente el número de archivos a guardar y los días de guardado serán eliminados
    * @param [in] saveDays Días de guardado de archivos; los archivos que superen simultáneamente el número de archivos a guardar y los días de guardado serán eliminados
    * @return Código de error
    */
    int LoggerInit(FrLogType logType, FrLogLevel logLevel, String filePath, int saveFileNum, int saveDays)

Establecer el nivel de filtrado del registro
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el nivel de filtrado del registro
    * @param [in] logLevel Nivel de filtrado del registro, ERROR-error; WARNING-advertencia; INFO-información; DEBUG-depuración
    * @return Código de error
    */
    int SetLoggerLevel(FrLogLevel logLevel)

Ejemplo de código de control básico del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("rpc连接 success");
        }
        else
        {
            System.out.println("rpc连接 fail");
            return ;
        }
        String[] ip={""};
        String version = "";
        version=robot.GetSDKVersion();
        System.out.println("SDK version : " + version);
        int rtn = robot.GetControllerIP(ip);
        System.out.println("controller ip : " +  ip[0] + "  " + rtn);
        robot.Mode(1);//1-手动模式  0-自动模式
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);//进入拖动模式
        robot.Sleep(1000);
        ROBOT_STATE_PKG pkg = robot.GetRobotRealTimeState();
        System.out.println("drag state : " + pkg.robot_state);
        robot.Sleep(1000);
        robot.DragTeachSwitch(0);//退出拖动模式
        robot.Sleep(1000);
        pkg = robot.GetRobotRealTimeState();
        System.out.println("drag state : " + pkg.robot_state);
        
        if (pkg.robot_state ==4){
           System.out.println("拖动模式");
        }else {
           System.out.println("非拖动模式");
        }
    }

Obtener la versión de software del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener la versión de software del robot
    * @param [out] robotModel Modelo del robot
    * @param [out] webVersion Versión web
    * @param [out] controllerVersion Versión del controlador
    * @return Código de error 
    */
    int GetSoftwareVersion(String robotModel, String webVersion, String controllerVersion);

Obtener la versión de hardware del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener la versión de hardware del robot
    * @param [out] ctrlBoxBoardVersion Versión de hardware de la placa base de la caja de control
    * @param [out] driver1Version Versión de hardware del accionamiento 1
    * @param [out] driver1Version Versión de hardware del accionamiento 2
    * @param [out] driver1Version Versión de hardware del accionamiento 3
    * @param [out] driver1Version Versión de hardware del accionamiento 4
    * @param [out] driver1Version Versión de hardware del accionamiento 5
    * @param [out] driver1Version Versión de hardware del accionamiento 6
    * @param [out] endBoardVersion Versión de hardware de la placa del extremo
    * @return Código de error 
    */
    int GetHardwareVersion(String ctrlBoxBoardVersion, String driver1Version, String driver2Version, String driver3Version,
                                          String driver4Version, String driver5Version, String driver6Version, String endBoardVersion);

Obtener la versión de firmware del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener la versión de firmware del robot
    * @param [out] ctrlBoxBoardVersion Versión de firmware de la placa base de la caja de control
    * @param [out] driver1Version Versión de firmware del accionamiento 1
    * @param [out] driver1Version Versión de firmware del accionamiento 2
    * @param [out] driver1Version Versión de firmware del accionamiento 3
    * @param [out] driver1Version Versión de firmware del accionamiento 4
    * @param [out] driver1Version Versión de firmware del accionamiento 5
    * @param [out] driver1Version Versión de firmware del accionamiento 6
    * @param [out] endBoardVersion Versión de firmware de la placa del extremo
    * @return Código de error 
    */
    int GetFirmwareVersion(String ctrlBoxBoardVersion, String driver1Version, String driver2Version, String driver3Version,
                                          String driver4Version, String driver5Version, String driver6Version, String endBoardVersion);

Ejemplo de código para obtener las versiones de software y firmware del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);//设置重连次数、间隔
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("rpc连接 success");
        }
        else
        {
            System.out.println("rpc连接 fail");
            return ;
        }
        String ctrlBoxBoardVersion = "";
        String driver1Version = "";
        String driver2Version = "";
        String driver3Version = "";
        String driver4Version = "";
        String driver5Version = "";
        String driver6Version = "";
        String endBoardVersion = "";
        robot.GetHardwareVersion(ctrlBoxBoardVersion ,driver1Version,  driver2Version,  driver3Version,
                 driver4Version,  driver5Version,  driver6Version,  endBoardVersion);

        robot.GetFirmwareVersion(ctrlBoxBoardVersion, driver1Version, driver2Version, driver3Version,
                driver4Version, driver5Version, driver6Version, endBoardVersion);
    }

Ejemplo de código de control básico del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestRobotCtrl(Robot robot)
    {
        int rtn = -1;
        String version = "";
        version = robot.GetSDKVersion();
        System.out.println("SDK version:"+version);
        String[] ip={""};
        robot.GetControllerIP(ip);
        System.out.println("ip: "+ip[0]);

        robot.Mode(1);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.Sleep(1000);
        ROBOT_STATE_PKG pkg=robot.GetRobotRealTimeState();
        System.out.println("drag state :" +pkg.robot_state);

        robot.Sleep(3000);
        robot.DragTeachSwitch(0);
        robot.Sleep(1000);
        pkg=robot.GetRobotRealTimeState();
        System.out.println("drag state :" +pkg.robot_state);
        robot.Sleep(3000);

        robot.RobotEnable(0);
        robot.Sleep(3000);
        robot.RobotEnable(1);

        robot.Mode(0);
        robot.Sleep(1000);
        robot.Mode(1);

        robot.Sleep(1000);
        rtn = robot.HiSpeedManualSwitch(1);
        System.out.println("change high speed mode"+ rtn);
        robot.Sleep(1000);
        rtn = robot.HiSpeedManualSwitch(0);
        System.out.println("change low speed mode"+ rtn);
        robot.Sleep(3000);
        System.out.println("Press any key to exit!");
        return 0;
    }

Cambiar al modo manual de alta velocidad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Cambiar al modo manual de alta velocidad
    * @param [in] state 0-salir de la alta velocidad manual; 1-entrar en la alta velocidad manual
    * @return Código de error
    */
    public int HiSpeedManualSwitch(int state)