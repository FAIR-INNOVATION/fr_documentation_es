Fundamentos del robot
=====================

.. toctree:: 
    :maxdepth: 5

Instanciación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Constructor de la clase de interfaz del robot
    * @param [in] _TLSEnable Habilitación del cifrado de comunicación del protocolo de instrucciones integrado en el SDK del robot; deshabilitado por defecto
    */
    FRRobot(bool _TLSEnable = false);

Establecer comunicación con el controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer comunicación con el controlador del robot
    * @param  [in] ip  Dirección IP del controlador, por defecto de fábrica 192.168.58.2
    * @return Código de error
    */
    errno_t  RPC(const char *ip);

Cerrar la comunicación con el controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Cerrar la comunicación con el controlador del robot
     * @return Código de error
     */
    errno_t  CloseRPC();

Consultar el número de versión del SDK
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Consultar el número de versión del SDK
    * @param  [out] version   Número de versión del SDK
    * @return  Código de error
    */  
    errno_t  GetSDKVersion(char *version);

Obtener la IP del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener la IP del controlador
    * @param  [out] ip  IP del controlador
    * @return  Código de error
    */
    errno_t  GetControllerIP(char *ip);

Controlar la entrada o salida del modo de enseñanza por arrastre del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Controlar la entrada o salida del modo de enseñanza por arrastre del robot
    * @param  [in] state 0-salir del modo de enseñanza por arrastre, 1-entrar en el modo de enseñanza por arrastre
    * @return  Código de error
    */
    errno_t  DragTeachSwitch(uint8_t state);

Consultar si el robot está en modo de arrastre
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Consultar si el robot está en modo de enseñanza por arrastre
    * @param  [out] state 0-modo de enseñanza por arrastre no activo, 1-modo de enseñanza por arrastre activo
    * @return  Código de error
    */
    errno_t  IsInDragTeach(uint8_t *state);

Controlar la habilitación o deshabilitación del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Controlar la habilitación o deshabilitación del robot; tras el encendido, el robot se habilita automáticamente por defecto
    * @param  [in] state  0-deshabilitar, 1-habilitar
    * @return  Código de error
    */
    errno_t  RobotEnable(uint8_t state);

Controlar el cambio de modo manual/automático del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Controlar el cambio de modo manual/automático del robot
    * @param [in] mode 0-modo automático, 1-modo manual
    * @return Código de error
    */
    errno_t  Mode(int mode);

Apagar el sistema operativo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Apagar el sistema operativo del robot
    * @return Código de error
    */
    errno_t ShutDownRobotOS();

Cambiar al modo manual de alta velocidad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Cambiar al modo manual de alta velocidad
    * @param [in] state 0-salir de la alta velocidad manual; 1-entrar en la alta velocidad manual
    * @return Código de error
    */
    errno_t HiSpeedManualSwitch(int state);

Establecer los parámetros de reconexión de comunicación con el robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer los parámetros de reconexión de comunicación con el robot
    * @param [in] enable Habilitar la reconexión en caso de fallo de red true-habilitar false-no habilitar
    * @param [in] reconnectTime Tiempo de reconexión, unidad ms
    * @param [in] period Período de reconexión, unidad ms
    * @return Código de error
    */
    errno_t SetReConnectParam(bool enable, int reconnectTime = 30000, int period = 50);

Apagar el sistema operativo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Apagar el sistema operativo del robot
    * @return Código de error
    */
    int ShutDownRobotOS();

Inicializar los parámetros del registro
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inicializar los parámetros del registro;
    * @param output_model: modo de salida, 0-salida directa; 1-salida en búfer; 2-salida asíncrona;
    * @param file_path: ruta de guardado del archivo + nombre, longitud máxima 256, el nombre debe tener la forma xxx.log, por ejemplo /home/fr/linux/fairino.log;
    * @param file_num: número de archivos de almacenamiento rotativo, 1~20. Límite de 50M por archivo;
    * @return errno_t Código de error;
    */
	errno_t LoggerInit(int output_model = 0, std::string file_path = "", int file_num = 5);

Establecer el nivel de filtrado del registro
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el nivel de filtrado del registro;
    * @param lvl: valor del nivel de filtrado, cuanto menor es el valor menos registro se emite, valor por defecto 1. 1-error, 2-warnning, 3-inform, 4-debug;
    */
    void SetLoggerLevel(int lvl = 1);

Ejemplo de código de control básico del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestRobotCtrl(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.57.2");
        
        char ip[64] = "";
        char version[64] = "";
        uint8_t state;
        robot.GetSDKVersion(version);
        printf("SDK version:%s\n", version);
        robot.GetControllerIP(ip);
        printf("controller ip:%s\n", ip);
        robot.Mode(1);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.Sleep(1000);
        robot.IsInDragTeach(&state);
        printf("drag state :%u\n", state);
        robot.Sleep(3000);
        robot.DragTeachSwitch(0);
        robot.Sleep(1000);
        robot.IsInDragTeach(&state);
        printf("drag state :%u\n", state);
        robot.Sleep(3000);
        robot.RobotEnable(0);
        robot.Sleep(3000);
        robot.RobotEnable(1);
        robot.Mode(0);
        robot.Sleep(2000);
        robot.Mode(1);
        robot.Sleep(1000);
        rtn = robot.HiSpeedManualSwitch(1);
        printf("change high speed mode %d\n", rtn);
        robot.Sleep(3000);
        rtn = robot.HiSpeedManualSwitch(0);
        printf("change low speed mode %d\n", rtn);
        robot.Sleep(3000);
        robot.ShutDownRobotOS();
        robot.CloseRPC();
        return 0;
    }

Ejemplo de código de obtención de la versión del software del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la versión del software del robot
    * @param[out]	robotModel Modelo del robot
    * @param[out]	webversion Versión web
    * @param[out]	controllerVersion Versión del controlador
    * @return Código de error
    */
    errno_t GetSoftwareVersion(char robotModel[64], char webVersion[64], char controllerVersion[64]);

Obtener la versión del hardware del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la versión del hardware del robot
    * @param[out] ctrlBoxBoardversion Versión de hardware de la placa base del armario de control
    * @param[out] driver1version Versión de hardware del accionamiento 1
    * @param[out] driver2version Versión de hardware del accionamiento 2
    * @param[out] driver3version Versión de hardware del accionamiento 3
    * @param[out] driver4version Versión de hardware del accionamiento 4
    * @param[out] driver5version Versión de hardware del accionamiento 5
    * @param[out] driver6version Versión de hardware del accionamiento 6
    * @param[out] endBoardversion Versión de hardware de la placa del extremo
    */
    errno_t GetHardwareVersion(char ctrlBoxBoardversion[128], char driver1version[128], char driver2version[128], char driver3version[128], char driver4version[128], char driver5version[128], char driver6version[128], char endBoardversion[128]);

Obtener la versión del firmware del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la versión del firmware del robot
    * @param[out] ctrlBoxBoardversion Versión de firmware de la placa base del armario de control
    * @param[out] driver1version Versión de firmware del accionamiento 1
    * @param[out] driver2version Versión de firmware del accionamiento 2
    * @param[out] driver3version Versión de firmware del accionamiento 3
    * @param[out] driver4version Versión de firmware del accionamiento 4
    * @param[out] driver5version Versión de firmware del accionamiento 5
    * @param[out] driver6version Versión de firmware del accionamiento 6
    * @param[out] endBoardversion Versión de firmware de la placa del extremo
    */
    errno_t GetFirmwareVersion(char ctrlBoxBoardversion[128], char driver1version[128], char driver2version[128], char driver3version[128], char driver4version[128], char driver5version[128], char driver6version[128], char endBoardversion[128]);

Ejemplo de código de obtención de la versión de software y firmware del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetVersions(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         char robotModel[64] = { 0 };
         char webversion[64] = { 0 };
         char controllerVersion[64] = { 0 };
         char ctrlBoxBoardversion[128] = { 0 };
         char driver1version[128] = { 0 };
         char driver2version[128] = { 0 };
         char driver3version[128] = { 0 };
         char driver4version[128] = { 0 };
         char driver5version[128] = { 0 };
         char driver6version[128] = { 0 };
         char endBoardversion[128] = { 0 };
         rtn = robot.GetSoftwareVersion(robotModel, webversion, controllerVersion);
         printf("Getsoftwareversion rtn is: %d\n", rtn);
         printf("robotmodel is: %s, webversion is: %s, controllerVersion is: %s \n\n", robotModel, webversion, controllerVersion);
         rtn = robot.GetHardwareVersion(ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         printf("GetHardwareversion rtn is: %d\n", rtn);
         printf("GetHardwareversion get hardware versoin is: %s, %s, %s, %s, %s, %s, %s, %s\n\n", ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         rtn = robot.GetFirmwareVersion(ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         printf("GetFirmwareversion rtn is: %d\n", rtn);
         printf("GetHardwareversion get hardware versoin is: %s, %s, %s, %s, %s, %s, %s, %s\n\n", ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         robot.CloseRPC();
         return 0;
     }