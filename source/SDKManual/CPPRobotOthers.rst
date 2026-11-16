Otras interfaces
=================

.. toctree:: 
    :maxdepth: 5

Obtener la clave pública SSH
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la clave pública SSH
    * @param [out] keygen Clave pública
    * @return Código de error
    */
    errno_t GetSSHKeygen(char keygen[1024]);

Enviar la instrucción SCP
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Enviar la instrucción SCP
    * @param [in] mode 0-cargar (PC superior->controlador), 1-descargar (controlador->PC superior)
    * @param [in] sshname Nombre de usuario del PC superior
    * @param [in] sship Dirección IP del PC superior
    * @param [in] usr_file_url Ruta del archivo en el PC superior
    * @param [in] robot_file_url Ruta del archivo en el controlador del robot
    * @return Código de error
    */
    errno_t SetSSHScpCmd(int mode, char sshname[32], char sship[32], char usr_file_url[128], char robot_file_url[128]);

Calcular el valor MD5 del archivo en la ruta especificada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Calcular el valor MD5 del archivo en la ruta especificada
    * @param [in] file_path Ruta del archivo incluyendo el nombre del archivo; la ruta predeterminada de la carpeta Traj es: "/fruser/traj/", por ejemplo "/fruser/traj/trajHelix_aima_1.txt"
    * @param [out] md5 Valor MD5 del archivo
    * @return Código de error
    */
    errno_t ComputeFileMD5(char file_path[256], char md5[256]);

Ejemplo de código de instrucciones SSH y MD5 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSSHMd5(void)
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
      char file_path[256] = "/fruser/airlab.lua";
      char md5[256] = { 0 };
      uint8_t emerg_state = 0;
      uint8_t si0_state = 0;
      uint8_t si1_state = 0;
      int sdk_com_state = 0;
      char ssh_keygen[1024] = { 0 };
      int retval = robot.GetSSHKeygen(ssh_keygen);
      printf("GetSSHKeygen retval is: %d\n", retval);
      printf("ssh key is: %s \n", ssh_keygen);
      char ssh_name[32] = "fr";
      char ssh_ip[32] = "192.168.58.45";
      char ssh_route[128] = "/home/fr";
      char ssh_robot_url[128] = "/root/robot/dhpara.config";
      retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
      printf("SetSSHScpCmd retval is: %d\n", retval);
      printf("robot url is: %s\n", ssh_robot_url);
      robot.ComputeFileMD5(file_path, md5);
      printf("md5 is: %s \n", md5);
      robot.CloseRPC();
      return 0;
    }

Establecer el período de retroalimentación del puerto 20004 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el período de retroalimentación del puerto 20004 del robot
    * @param [in] period Período de retroalimentación del puerto 20004 del robot (ms)
    * @return Código de error
    */
    errno_t SetRobotRealtimeStateSamplePeriod(int period);

Obtener el período de retroalimentación del puerto 20004 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el período de retroalimentación del puerto 20004 del robot
    * @param [out] period Período de retroalimentación del puerto 20004 del robot (ms)
    * @return Código de error
    */
    errno_t GetRobotRealtimeStateSamplePeriod(int& period);

Ejemplo de código de configuración del período de retroalimentación de estado del puerto 20004 del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestRealtimePeriod(void)
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
      robot.SetRobotRealtimeStateSamplePeriod(10);
      int getPeriod = 0;
      robot.GetRobotRealtimeStateSamplePeriod(getPeriod);
      cout << "period is " << getPeriod << endl;
      robot.Sleep(1000);
      robot.CloseRPC();
      return 0;
    }


Actualización del software del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Actualización del software del robot
    * @param [in] filePath Ruta completa del paquete de actualización de software
    * @param [in] block Si se bloquea hasta completar la actualización true:bloqueante; false:no bloqueante
    * @return Código de error
    */
    errno_t SoftwareUpgrade(std::string filePath, bool block);

Obtener el estado de actualización del software del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado de actualización del software del robot
    * @param [out] state Estado de actualización del paquete de software del robot (0-inactivo o cargando el paquete de actualización; 1~100: porcentaje de actualización completado; -1: fallo de actualización del software; -2: fallo de verificación; -3: fallo de verificación de versión; -4: fallo de descompresión; -5: fallo de actualización de la configuración de usuario; -6: fallo de actualización de la configuración de periféricos; -7: fallo de actualización de la configuración del eje extendido; -8: fallo de actualización de la configuración del robot; -9: fallo de actualización de la configuración de parámetros DH)
    * @return Código de error
    */
    errno_t GetSoftwareUpgradeState(int &state);

Ejemplo de código de actualización del software del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestUpgrade(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(3);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      robot.SoftwareUpgrade("D://zUP/QNX/software.tar.gz", false);
      while (true)
      {
        int curState = -1;
        robot.GetSoftwareUpgradeState(curState);
        printf("upgrade state is %d\n", curState);
        robot.Sleep(300);
      }
      robot.CloseRPC();
      return 0;
    }

Descargar la base de datos de la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Descargar la base de datos de la tabla de puntos
    * @param [in] pointTableName Nombre de la tabla de puntos a descargar    pointTable1.db
    * @param [in] saveFilePath Ruta de guardado de la tabla de puntos descargada   C://test/
    * @return Código de error
    */
    errno_t PointTableDownLoad(const std::string &pointTableName, const std::string &saveFilePath);

Cargar la base de datos de la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Cargar la base de datos de la tabla de puntos
    * @param [in] pointTableFilePath Ruta completa de la tabla de puntos a cargar   C://test/pointTable1.db
    * @return Código de error
    */
    errno_t PointTableUpLoad(const std::string &pointTableFilePath);

Actualizar el archivo lua con la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Actualizar el archivo lua con la tabla de puntos
    * @param [in] pointTableName Nombre de la tabla de puntos a cambiar   "pointTable1.db"; cuando la tabla de puntos está vacía, es decir "" indica que el programa lua se actualiza al programa inicial sin aplicar la tabla de puntos
    * @param [in] luaFileName Nombre del archivo lua a actualizar   "testPointTable.lua"
    * @param [out] errorStr Información de error del cambio de tabla de puntos
    * @return Código de error
    */
    errno_t PointTableUpdateLua(const std::string &pointTableName, const std::string &luaFileName);

Cambiar la tabla de puntos y aplicarla
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Cambiar la tabla de puntos y aplicarla
    * @param [in] pointTableName Nombre de la tabla de puntos a cambiar pointTable1.db
    * @return Código de error
    */
    errno_t PointTableSwitch(const std::string pointTableName);

Ejemplo de código de operación de la tabla de puntos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestPointTable(void)
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
      string save_path = "D://zDOWN/";
      string point_table_name = "point_table_FR5.db";
      rtn = robot.PointTableDownLoad(point_table_name, save_path);
      cout << "download : " << point_table_name << " fail: " << rtn << endl;
      string upload_path = "D://zUP/point_table_FR5.db";
      rtn = robot.PointTableUpLoad(upload_path);
      cout << "retval is: " << rtn << endl;
      string point_tablename = "point_table_FR5.db";
      string lua_name = "airlab.lua";
      rtn = robot.PointTableUpdateLua(point_tablename, lua_name);
      cout << "retval is: " << rtn << endl;
      robot.CloseRPC();
      return 0;
    }

Descarga del registro del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Descarga del registro del controlador
    * @param [in] savePath Ruta del archivo de guardado "D://zDown/"
    * @return Código de error
    */
    errno_t RbLogDownload(std::string savePath);

Descarga de todas las fuentes de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Descarga de todas las fuentes de datos
    * @param [in] savePath Ruta del archivo de guardado "D://zDown/"
    * @return Código de error
    */
    errno_t AllDataSourceDownload(std::string savePath);

Descarga del paquete de copia de seguridad de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Descarga del paquete de copia de seguridad de datos
    * @param [in] savePath Ruta del archivo de guardado "D://zDown/"
    * @return Código de error
    */
    errno_t DataPackageDownload(std::string savePath);

Ejemplo de código de descarga de datos del controlador
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestDownLoadRobotData(void)
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
      rtn = robot.RbLogDownload("D://zDOWN/");
      cout << "RbLogDownload rtn is " << rtn << endl;
      rtn = robot.AllDataSourceDownload("D://zDOWN/");
      cout << "AllDataSourceDownload rtn is " << rtn << endl;
      rtn = robot.DataPackageDownload("D://zDOWN/");
      cout << "DataPackageDownload rtn is " << rtn << endl;
      robot.CloseRPC();
      return 0;
    }

Establecer la actualización del firmware de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la actualización del firmware de las articulaciones
    * @param [in] type Tipo de archivo de actualización; 1-actualizar firmware (antes de usar es necesario que el robot entre en modo boot); 2-actualizar archivo de configuración del esclavo (antes de usar es necesario deshabilitar el robot)
    * @param [in] path Ruta completa del paquete de actualización local (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    errno_t SetJointFirmwareUpgrade(int type, std::string path);
  
Establecer la actualización del firmware del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la actualización del firmware del armario de control
    * @param [in] type Tipo de archivo de actualización; 1-actualizar firmware (antes de usar es necesario que el robot entre en modo boot); 2-actualizar archivo de configuración del esclavo (antes de usar es necesario deshabilitar el robot)
    * @param [in] path Ruta completa del paquete de actualización local (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    errno_t SetCtrlFirmwareUpgrade(int type, std::string path);
  
Establecer la actualización del firmware del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la actualización del firmware del extremo
    * @param [in] type Tipo de archivo de actualización; 1-actualizar firmware (antes de usar es necesario que el robot entre en modo boot); 2-actualizar archivo de configuración del esclavo (antes de usar es necesario deshabilitar el robot)
    * @param [in] path Ruta completa del paquete de actualización local (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    errno_t SetEndFirmwareUpgrade(int type, std::string path);

Actualización del archivo de configuración de todos los parámetros de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Actualización del archivo de configuración de todos los parámetros de las articulaciones (antes de usar es necesario deshabilitar el robot)
    * @param [in] path Ruta completa del paquete de actualización local (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    errno_t JointAllParamUpgrade(std::string path);

Obtener el porcentaje de progreso de la actualización de todos los parámetros de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el porcentaje de progreso de la actualización de todos los parámetros de las articulaciones
    * @param [out] progress Porcentaje de progreso de la actualización [0-100], -1: fallo de actualización
    * @return Código de error
    */
    errno_t GetJointAllParamUpgradeProgress(int& progress);
    
Ejemplo de código de actualización de todos los parámetros de las articulaciones y consulta del progreso de actualización
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestJointAllParamUpgrade()
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
        robot.RobotEnable(0);
        robot.Sleep(200);
        rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/FR3WMS/jointallparameters.db");
        printf("robot JointAllParamUpgrade rtn is %d\n", rtn);
        
        int upgradeProgress = 0;
        while (upgradeProgress < 100)
        {
            robot.GetJointAllParamUpgradeProgress(upgradeProgress);
            printf("robot joint all param upgrade progress : %d\n", upgradeProgress);
            robot.Sleep(200);
        }
        robot.CloseRPC();
        return 0;
    }
    
Ejemplo de código de actualización del firmware del esclavo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestFirmWareUpgrade()
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
    robot.RobotEnable(0);
    robot.Sleep(200);
    rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/jointallparameters.db");
    printf("robot JointAllParamUpgrade rtn is %d\n", rtn);
    rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
    printf("robot SetCtrlFirmwareUpgrade config param rtn is %d\n", rtn);
    rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
    printf("robot SetEndFirmwareUpgrade config param rtn is %d\n", rtn);
    robot.SetSysServoBootMode();
    rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/upgrade/FR_CTRL_PRIMCU_FV201212_MAIN_U4_T01_20250428(MT).bin");
    printf("robot SetCtrlFirmwareUpgrade rtn is %d\n", rtn);
    rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/upgrade/FR_END_FV201009_MAIN_U1_T01_20250428.bin");
    printf("robot SetEndFirmwareUpgrade rtn is %d\n", rtn);
    rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/upgrade/FR_SERVO_FV504214_MAIN_U7_T07_20250519.bin");
    printf("robot SetJointFirmwareUpgrade rtn is %d\n", rtn);
    robot.CloseRPC();
    return 0;
    }

Actualización del sistema operativo del robot (armario de control LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Actualización del sistema operativo del robot (armario de control LA)
    * @param [in] filePath Ruta completa del paquete de actualización del sistema operativo
    * @return Código de error
    */
    errno_t KernelUpgrade(std::string filePath);
        
Obtener el resultado de la actualización del sistema operativo del robot (armario de control LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el resultado de la actualización del sistema operativo del robot (armario de control LA)
    * @param [out] result Resultado de la actualización: 0: éxito; -1: fallo
    * @return Código de error
    */
    errno_t GetKernelUpgradeResult(int& result);
        
Generación del registro MCU del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Generación del registro MCU del robot
    * @return Código de error
    */
    errno_t RobotMCULogCollect();
        
Establecer la parada del robot al desconectarse la comunicación del puerto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la parada del robot al desconectarse la comunicación del puerto
    * @param [in] pordID Número de puerto 0-8080; 1-8083; 2-20002; 3-20004
    * @param [in] enable 0-desactivar; 1-activar
    * @param [in] confirmTime Duración de confirmación de interrupción de comunicación (ms) [0-5000]
    * @return Código de error
    */
    errno_t SetRobotStopOnComDisc(int pordID, bool enable, int confirmTime);
        
Obtener los parámetros de parada del robot al desconectarse la comunicación del puerto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener los parámetros de parada del robot al desconectarse la comunicación del puerto
    * @param [in] pordID Número de puerto 0-8080; 1-8083; 2-20002; 3-20004
    * @param [out] enable 0-desactivar; 1-activar
    * @param [out] confirmTime Duración de confirmación de interrupción de comunicación (ms) [0-5000]
    * @return Código de error
    */
    errno_t GetRobotStopOnComDisc(int pordID, bool &enable, int &confirmTime);

Ejemplo de código de parámetros de parada del robot al desconectarse la comunicación del puerto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestRobotStopOnComDisc()
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
        bool enable = false;
        int confirmTime = 0;
        rtn = robot.SetRobotStopOnComDisc(0, true, 330);
        rtn = robot.SetRobotStopOnComDisc(1, true, 550);
        rtn = robot.SetRobotStopOnComDisc(2, true, 110);
        rtn = robot.SetRobotStopOnComDisc(3, true, 220);
        printf("SetRobotStopOnComDisc %d\n", rtn);
        robot.GetRobotStopOnComDisc(0, enable, confirmTime);
        printf("GetRobotStopOnComDisc 8080 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.GetRobotStopOnComDisc(1, enable, confirmTime);
        printf("GetRobotStopOnComDisc 80803 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.GetRobotStopOnComDisc(2, enable, confirmTime);
        printf("GetRobotStopOnComDisc 20002 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.GetRobotStopOnComDisc(3, enable, confirmTime);
        printf("GetRobotStopOnComDisc 20004 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Enviar trama de instrucción por UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Enviar trama de instrucción por UDP
    * @param [in] frame Cadena de trama de datos a enviar, como: /f/bIII20III303III7IIIMode(0)III/b/f
    * @return Código de error
    */
    errno_t SendUDPFrame(std::string frame);

Establecer la función de callback del resultado de ejecución de las instrucciones enviadas por el SDK a través de UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la función de callback del resultado de ejecución de las instrucciones enviadas por el SDK a través de UDP
    * @param [in] CallBack Función de callback; comType-tipo de respuesta de comunicación del resultado de la instrucción 0-TCP, 1-UDP; count-contador de tramas de respuesta de la instrucción; cmdID-número de la instrucción; contentLen-longitud de datos; content-contenido de datos
    * @return Código de error
    */
    errno_t SetCmdRpyCallback(void (*CallBack)(int comType, int count, int cmdID, int contentLen, std::string content));

Ejemplo de código de envío de instrucciones UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestSendUDPFrame()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.SetCmdRpyCallback(UDPFrameCallBack);
        printf("SetCmdRpyCallback rtn is %d\n", rtn);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f");
        printf("SendUDPFrame Mode(0) rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII21III303III7IIIMode(1)III/b/f");
        printf("SendUDPFrame Mode(1) rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII49III201III184IIIMoveJ(-15.625, -82.680, 101.654, -110.950, -88.290, 0.017, -383.012, -2.325, 242.655, -178.024, 1.710, 74.416, 0, 0, 100, 100, 100, 0.000, 0.000, 0.000, 0.000, -1, 0, 0, 0, 0, 0, 0, 0)III/b/f");
        printf("SendUDPFrame MoveJ(-15.625 rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII48III203III199IIIMoveL(-75.622, -82.680, 101.654, -110.950, -88.290, 0.017, -193.537, 330.525, 242.657, -178.024, 1.710, 14.420, 0, 0, 100, 100, 100, -1, 0, 0.000, 0.000, 0.000, 0.000, 0, 0, 0, 0, 0, 0, 0, 0, 100, 0)III/b/f");
        printf("SendUDPFrame MoveL(-75.622 rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII4III905III20IIIGetSoftwareVersion()III/b/f");
        printf("SendUDPFrame GetSoftwareVersion() rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("III20III303III7IIIMode(0)III/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/bIII20III303III6IIIMode(0)III/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/b|||20|||303|||7|||Mode(0)|||/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/bII20II303II7IIMode(0)II/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }
    
Establecer el color de la luz del extremo del robot definido por el usuario
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el color de la luz del extremo del robot definido por el usuario
    * @param [in] r Control de la luz roja del extremo; 0-apagada; 1-encendida
    * @param [in] g Control de la luz verde del extremo; 0-apagada; 1-encendida
    * @param [in] b Control de la luz azul del extremo; 0-apagada; 1-encendida
    * @return Código de error
    */
    errno_t SetUserLEDColor(bool r, bool g, bool b);
        
Ejemplo de código de configuración del color de la luz del extremo del robot definido por el usuario
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestUserLedColor()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        robot.SetUserLEDColor(true, true, true);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(true, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, true, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, true);
        robot.Sleep(1000);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }
            
Enviar trama de instrucción personalizada a través de TCP 8080
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Enviar trama de instrucción personalizada a través de TCP 8080 (en modo mTLS a través del canal cifrado automáticamente)
    * @param [in] frame Trama de instrucción completa, como "/f/bIII52III236III7IIIMode(0)III/b/f"
    * @return Código de error
    */
    errno_t SendTCPFrame(std::string frame);
                
Ejemplo de código de envío de trama de instrucción personalizada a través de TCP 8080
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestSendModeTcp()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot(true);
        int rtn = 0;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        rtn = robot.SetCmdRpyCallback(UDPFrameCallBack);
        printf("SetCmdRpyCallback rtn is %d\n", rtn);
        robot.MtlsLink("");
        robot.SetReConnectParam(true, 300000, 50);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        std::string program_name = "tls.lua";
        unsigned char state = 0;
        int line = 0;
        std::string mode0 = "/f/bIII52III236III7IIIMode(0)III/b/f";
        std::string mode1 = "/f/bIII52III236III7IIIMode(1)III/b/f";
        printf("[SEND] %s\n", mode0.c_str());
        robot.SendTCPFrame(mode0);
        robot.Sleep(1000);
        printf("[SEND] %s\n", mode1.c_str());
        robot.SendTCPFrame(mode1);
        robot.Sleep(1000);
        printf("[SEND] %s\n", mode0.c_str());
        robot.SendTCPFrame(mode0);
        robot.Mode(0);
        robot.LoadDefaultProgConfig(0, (char*)program_name.c_str());
        robot.ProgramLoad((char*)program_name.c_str());
        robot.SetSpeedInstant(50);
        robot.ProgramRun();
        robot.Sleep(5000);
        robot.PauseMotion();
        robot.GetProgramState(&state);
        printf("program state:%u\n\n", state);
        robot.GetCurrentLine(&line);
        printf("current line:%d\n\n", line);
        char loaded_name[256] = "";
        robot.GetLoadedProgram(loaded_name);
        printf("program name:%s\n\n", loaded_name);
        robot.ResumeMotion();
        robot.Sleep(2000);
        robot.PauseMotion();
        robot.Sleep(2000);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Carga y actualización del paquete de copia de seguridad de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Carga y actualización del paquete de copia de seguridad de datos
    * @param [in] filePath Ruta del archivo del paquete de copia de seguridad de datos a cargar; D://zUP/fr_user_data.tar.gz
    * @return Código de error
    */
    errno_t DataPackageUpgrade(std::string filePath);
    
Obtener el porcentaje de progreso de la actualización del paquete de copia de seguridad de datos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el porcentaje de progreso de la actualización del paquete de copia de seguridad de datos
    * @param [out] progress Porcentaje de progreso de la actualización [0-100], -1: fallo de actualización
    * @return Código de error
    */
    errno_t GetDataPackageUpgradeProgress(int& progress);
        
Ejemplo de código de carga y actualización del paquete de copia de seguridad de datos y consulta del progreso de actualización
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestDataPackageUpgrade()
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
        robot.Sleep(200);
        rtn = robot.DataPackageUpgrade("D://zUP/upgrade/FR5/fr_user_data.tar.gz");
        printf("robot DataPackageUpgrade rtn is %d\n", rtn);
        
        int upgradeProgress = 0;
        while (upgradeProgress < 100)
        {
            robot.GetDataPackageUpgradeProgress(upgradeProgress);
            printf("robot data package upgrade progress : %d\n", upgradeProgress);
            robot.Sleep(200);
        }
        robot.CloseRPC();
        return 0;
    }