Otras interfaces
================

.. toctree:: 
    :maxdepth: 5

Obtener la clave pública SSH
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener la clave pública SSH
    * @param [out] keygen Clave pública
    * @return Código de error
    */
    int GetSSHKeygen(String[] keygen)

Enviar comando SCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /** 
    * @brief Enviar comando SCP
    * @param [in] mode 0-carga (PC anfitrión->controlador), 1-descarga (controlador->PC anfitrión)
    * @param [in] sshname Nombre de usuario del PC anfitrión
    * @param [in] sship Dirección IP del PC anfitrión
    * @param [in] usr_file_url Ruta del archivo en el PC anfitrión
    * @param [in] robot_file_url Ruta del archivo en el controlador del robot
    * @return Código de error
    */
    int SetSSHScpCmd(int mode, String sshname, String sship, String usr_file_url, String robot_file_url)

Calcular el valor MD5 del archivo en la ruta especificada
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calcular el valor MD5 del archivo en la ruta especificada
    * @param [in] file_path Ruta del archivo incluido el nombre del archivo; la ruta predeterminada de la carpeta Traj es: "/fruser/traj/", por ejemplo "/fruser/traj/trajHelix_aima_1.txt"
    * @param [out] md5 Valor MD5 del archivo
    * @return Código de error
    */
    int ComputeFileMD5(String file_path, String[] md5)

Ejemplo de código de las instrucciones SSH y MD5 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSSHMd5(Robot robot)
    {
        String file_path= "/fruser/airlab.lua";
        String[] md5 =new String[]{""};

        String[] ssh_keygen=new String[]{""};
        int retval = robot.GetSSHKeygen(ssh_keygen);
        System.out.println(ssh_keygen[0]);

        String ssh_name = "fr";
        String ssh_ip = "192.168.58.45";
        String ssh_route = "/home/fr";
        String ssh_robot_url = "/root/robot/dhpara.config";
        retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
        System.out.println("SetSSHScpCmd retval is:"+ retval);
        System.out.println("robot url is:"+ ssh_robot_url);

        robot.ComputeFileMD5(file_path, md5);
        System.out.println("md5 is:+"+ md5[0]);
        return 0;
    }

Establecer el período de retroalimentación del puerto 20004 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el período de retroalimentación del puerto 20004 del robot
    * @param [in] period Período de retroalimentación del puerto 20004 del robot (ms)
    * @return  Código de error
    */
    public int SetRobotRealtimeStateSamplePeriod(int period)

Obtener el período de retroalimentación del puerto 20004 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el período de retroalimentación del puerto 20004 del robot
    * @return  List[0]:código de error; List[1]:período de retroalimentación del puerto 20004 del robot (ms)
    */
    public List<Integer> GetRobotRealtimeStateSamplePeriod()

Ejemplo de código de configuración del período de retroalimentación de estado del puerto 20004 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestRealtimePeriod(Robot robot)
    {
        robot.SetRobotRealtimeStateSamplePeriod(10);
        List<Integer> getPeriod = new ArrayList<>();
        getPeriod=robot.GetRobotRealtimeStateSamplePeriod();
        robot.Sleep(1000);

        return 0;
    }

Actualización del software del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Actualización del software del robot
     * @param [in] filePath Ruta completa del paquete de actualización de software
     * @param [in] block Si se bloquea hasta completar la actualización true:bloquear; false:no bloquear
     * @return  Código de error
     */
    public int SoftwareUpgrade(String filePath, boolean block)

Obtener el estado de actualización del software del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el estado de actualización del software del robot
    * @return  List[0]:código de error; List[1]:estado de actualización del software del robot 0-inactivo o subiendo paquete de actualización; 1~100: porcentaje completado de la actualización; -1:fallo al actualizar el software; -2:fallo de verificación; -3:fallo de verificación de versión; -4:fallo de descompresión; -5:fallo de actualización de la configuración de usuario; -6:fallo de actualización de la configuración de periféricos; -7:fallo de actualización de la configuración del eje extendido; -8:fallo de actualización de la configuración del robot; -9:fallo de actualización de la configuración de parámetros DH
    */
    public List<Integer> GetSoftwareUpgradeState()

Ejemplo de código de actualización del software del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestUpgrade(Robot robot)
    {
        robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", false);
        while (true)
        {
            List<Integer> inter=new ArrayList<>();
            inter=robot.GetSoftwareUpgradeState();
            System.out.println("upgrade state is:"+ inter.get(1));
            robot.Sleep(300);
        }
    }

Descargar la base de datos de la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Descargar la base de datos de la tabla de puntos 
    * @param [in] pointTableName Nombre de la tabla de puntos a descargar    pointTable1.db
    * @param [in] saveFilePath Ruta de guardado de la tabla de puntos a descargar   C://test/
    * @return Código de error 
    */
    int PointTableDownLoad(String pointTableName, String saveFilePath);

Subir la base de datos de la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Subir la base de datos de la tabla de puntos 
    * @param [in] pointTableFilePath Nombre de ruta completo de la tabla de puntos a subir   C://test/pointTable1.db
    * @return Código de error 
    */
    int PointTableUpLoad(String pointTableFilePath);

Actualizar el archivo lua de la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Actualizar el archivo lua de la tabla de puntos
    * @param [in] pointTableName Nombre de la tabla de puntos a cambiar   "pointTable1.db"; cuando la tabla de puntos está vacía, es decir "", indica que el programa lua se actualiza al programa inicial sin aplicar la tabla de puntos
    * @param [in] luaFileName Nombre del archivo lua a actualizar   "testPointTable.lua"
    * @param [out] errorStr Información de error del cambio de tabla de puntos
    * @return Código de error 
    */
    int PointTableUpdateLua(String pointTableName, String luaFileName, String errorStr);

Ejemplo de código de operación de la tabla de puntos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestPointTable(Robot robot)
    {
        String save_path = "D://zDOWN/";
        String point_table_name = "point_table_FR5.db";
        int rtn = robot.PointTableDownLoad(point_table_name, save_path);

        String upload_path = "D://zUP/point_table_FR5.db";
        rtn = robot.PointTableUpLoad(upload_path);

        String point_tablename = "point_table_FR5.db";
        String lua_name = "airlab.lua";
        String err="";
        rtn = robot.PointTableUpdateLua(point_tablename, lua_name,err);

        robot.CloseRPC();
        return 0;
    }

Descarga del registro del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Descarga del registro del controlador
    * @param [in] savePath Ruta de guardado del archivo "D://zDown/"
    * @return Código de error
    */
    int RbLogDownload(String savePath);

Descarga de todas las fuentes de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Descarga de todas las fuentes de datos
    * @param [in] savePath Ruta de guardado del archivo "D://zDown/"
    * @return Código de error
    */
    int AllDataSourceDownload(String savePath);

Descarga del paquete de copia de seguridad de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Descarga del paquete de copia de seguridad de datos
    * @param [in] savePath Ruta de guardado del archivo "D://zDown/"
    * @return Código de error
    */
    int DataPackageDownload(String savePath);

Ejemplo de código de descarga de datos del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestDownLoadRobotData(Robot robot)
    {
        int rtn = robot.RbLogDownload("D://zDOWN/");

        rtn = robot.AllDataSourceDownload("D://zDOWN/");

        rtn = robot.DataPackageDownload("D://zDOWN/");
        return 0;
    }

Establecer la actualización del codificador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la actualización del codificador
    * @param [in] path Ruta completa local del paquete de actualización (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    int SetEncoderUpgrade(String path)

Establecer la actualización del firmware de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la actualización del firmware de las articulaciones
    * @param [in] type Tipo de archivo de actualización; 1-actualizar firmware; 2-actualizar archivo de configuración de esclavo
    * @param [in] path Ruta completa local del paquete de actualización (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    public int SetJointFirmwareUpgrade(int type, String path)

Establecer la actualización del firmware de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la actualización del firmware de la caja de control
    * @param [in] type Tipo de archivo de actualización; 1-actualizar firmware; 2-actualizar archivo de configuración de esclavo
    * @param [in] path Ruta completa local del paquete de actualización (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    public int SetCtrlFirmwareUpgrade(int type, String path)

Establecer la actualización del firmware del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la actualización del firmware del extremo
    * @param [in] type Tipo de archivo de actualización; 1-actualizar firmware; 2-actualizar archivo de configuración de esclavo
    * @param [in] path Ruta completa local del paquete de actualización (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    public int SetEndFirmwareUpgrade(int type, String path)

Actualización del archivo de configuración de todos los parámetros de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Actualización del archivo de configuración de todos los parámetros de las articulaciones
    * @param [in] path Ruta completa local del paquete de actualización (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    public int JointAllParamUpgrade(String path)

Obtener el porcentaje de progreso de la actualización de todos los parámetros de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el porcentaje de progreso de la actualización de todos los parámetros de las articulaciones
    * @return List[0]:código de error; List[1]:porcentaje de progreso de la actualización [0-100], -1:fallo de la actualización
    */
    public List<Integer> GetJointAllParamUpgradeProgress()

Ejemplo de código de actualización de todos los parámetros de las articulaciones y consulta del progreso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestJointAllParamUpgrade(Robot robot)
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        int rtn = 0;

        robot.RobotEnable(0);
        robot.Sleep(200);

        rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/FR3WMS/jointallparameters.db");
        System.out.println("robot JointAllParamUpgrade rtn is " + rtn);
        int upgradeProgress = 0;
        while (upgradeProgress < 100)
        {
            List<Integer> state = robot.GetJointAllParamUpgradeProgress();
            upgradeProgress = state.get(1);
            System.out.println("robot joint all param upgrade progress : " + upgradeProgress);
            robot.Sleep(200);
        }
    }
    
Ejemplo de código de actualización del firmware del esclavo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestFirmWareUpgrade(Robot robot)
    {
        robot.RobotEnable(0);
        robot.Sleep(200);
        int rtn = robot.JointAllParamUpgrade("D://zUP/standardQX/jointallparametersFR56.0.db");
        System.out.println("robot JointAllParamUpgrade rtn is:"+ rtn);

        rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
        System.out.println("robot SetCtrlFirmwareUpgrade config param rtn is:"+ rtn);

        rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
        System.out.println("robot SetEndFirmwareUpgrade config param rtn is:"+ rtn);

        robot.SetSysServoBootMode();
        rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/standardQX/FR_CTRL_PRIMCU_FV201010_MAIN_U4_T01_20240529.bin");
        System.out.println("robot SetCtrlFirmwareUpgrade rtn is:"+ rtn);

        rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/standardQX/FR_END_FV201010_MAIN_U01_T01_20250522.bin");
        System.out.println("robot SetEndFirmwareUpgrade rtn is:"+ rtn);

        rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/standardQX/FR_SERVO_FV502211_MAIN_U7_T07_20250217.bin");
        System.out.println("robot SetJointFirmwareUpgrade rtn is:"+ rtn);

        robot.CloseRPC();
    }

Actualización del sistema operativo del robot (caja de control LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Actualización del sistema operativo del robot (caja de control LA)
     * @param [in] filePath Ruta completa del paquete de actualización del sistema operativo
     * @return  Código de error
     */
    public int KernelUpgrade(String filePath)

Obtener el resultado de la actualización del sistema operativo del robot (caja de control LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Obtener el resultado de la actualización del sistema operativo del robot (caja de control LA)
     * @param [out] result Resultado de la actualización: 0:éxito; -1:fallo
     * @return  Código de error
     */
    public int GetKernelUpgradeResult(int[] result)

Generación del registro MCU del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Generación del registro MCU del robot
    * @return Código de error
    */
    public int RobotMCULogCollect()

Establecer la detención del robot al desconectarse la comunicación del puerto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la detención del robot al desconectarse la comunicación del puerto
    * @param pordID Número de puerto 0-8080; 1-8083; 2-20002; 3-20004
    * @param enable 0-desactivar; 1-activar
    * @param confirmTime Duración de confirmación de interrupción de comunicación (ms) [0-5000]
    * @return Código de error
    */
    public int SetRobotStopOnComDisc(int portID, bool enable, int confirmTime)
    
Obtener los parámetros de detención del robot al desconectarse la comunicación del puerto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener los parámetros de detención del robot al desconectarse la comunicación del puerto
    * @param pordID Número de puerto 0-8080; 1-8083; 2-20002; 3-20004
    * @param enable Arreglo de resultados, index 0: 0-desactivar; 1-activar
    * @param confirmTime Arreglo de resultados, index 0: duración de confirmación de interrupción de comunicación (ms) [0-5000] 
    * @return Código de error
    */
    public int GetRobotStopOnComDisc(int pordID, int[] enable, int[] confirmTime)

Ejemplo de código de los parámetros de detención del robot al desconectarse la comunicación del puerto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    void TestRobotStopOnComDisc(Robot robot)
    {
        int[] enable = {0};
        int[] confirmTime = {0};
        int rtn = 0;
        rtn = robot.SetRobotStopOnComDisc(0, true, 330);
        rtn = robot.SetRobotStopOnComDisc(1, true, 550);
        rtn = robot.SetRobotStopOnComDisc(2, true, 110);
        rtn = robot.SetRobotStopOnComDisc(3, true, 220);
        System.out.printf("SetRobotStopOnComDisc %d\n", rtn);

        robot.GetRobotStopOnComDisc(0, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 8080 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);
        robot.GetRobotStopOnComDisc(1, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 8083 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);
        robot.GetRobotStopOnComDisc(2, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 20002 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);
        robot.GetRobotStopOnComDisc(3, enable, confirmTime);
        System.out.printf("GetRobotStopOnComDisc 20004 rtn %d; enable is %d; confirm time is %d\n", rtn, enable[0], confirmTime[0]);

        return;
    }

Envío de trama de instrucciones por UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Envío de trama de instrucciones por UDP
    * @param trama de instrucciones
    * @return Código de error
    */
    public int SendUDPFrame(String frame)
    
Ejemplo de código SDK sobre la comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestRobotUDP (Robot robot) {
        robot.udpCmdClient.SetUDPCmdRpyCallback((srcType, count, cmdID, dataLen, content) -> {
            System.out.println("\n[Respuesta UDP recibida del robot]");
            System.out.println("srcType: " + srcType);
            System.out.println("count: " + count);
            System.out.println("cmdID: " + cmdID);
            System.out.println("dataLen: " + dataLen);
            System.out.println("contenido (content): " + content);
            return 0;
        });
        // Enviar trama
        String frameToSend = "/f/bIII52III236III7IIIMode(1)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII52III236III7IIIMode(0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII41III201III153IIIMoveJ(53.857,-89.441,119.453,-22.664,61.059,3.369,-54.249,-491.930,375.396,96.474,-6.896,-7.783,0,0,100,100,100,0.000,0.000,0.000,0.000,-1,0,0,0,0,0,0,0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII42III203III163IIIMoveL(81.736,-85.284,114.974,-23.261,88.746,6.799,125.744,-506.570,375.396,96.474,-6.896,-7.783,0,0,100,100,100,-1,0,0.000,0.000,0.000,0.000,0,0,0,0,0,0,0,0,100,0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
        frameToSend = "/f/bIII47III400III15IIIGetMCVersion(1)III/b/f/f/bIII48III424III21IIIGetSlaveFirmVersion()III/b/f";
        robot.SendUDPFrame(frameToSend);
        robot.Sleep(2000);
    }
        
Establecer el color de la luz del extremo del robot personalizado por el usuario
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el color de la luz del extremo del robot personalizado por el usuario
    * @param r Control de la luz roja del extremo; 0-apagada; 1-encendida
    * @param g Control de la luz verde del extremo; 0-apagada; 1-encendida
    * @param b Control de la luz azul del extremo; 0-apagada; 1-encendida
    * @return Código de error
    */
    public int SetUserLEDColor(bool r, bool g, bool b)
            
Ejemplo de código SDK de establecimiento del color de la luz del extremo del robot personalizado por el usuario
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public void testled(robot)
    {
        robot.SetUserLEDColor(true, true, true);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(true, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, true, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, true);
    }
                
Enviar trama de instrucciones personalizada a través de TCP 8080
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Enviar trama de instrucciones personalizada a través de TCP 8080 (en modo mTLS se realiza automáticamente a través del canal cifrado)
    * @param frame Trama de instrucciones completa, como "/f/bIII52III236III7IIIMode(0)III/b/f"
    * @return Código de error
    */
    public int SendTCPFrame(String frame)
                    
Ejemplo de código de envío de trama de instrucciones personalizada a través de TCP 8080
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Verificación solo del canal TCP 8080
    */
    public static void TestSendModeTcp(Robot robot)
    {
        String program_name = "mtls.lua";
        String[] loaded_name = {""};
        int[] state = {0};
        int[] line = {0};

        System.out.println("========== Verificación del canal TCP 8080 de la instrucción Mode ==========");
        System.out.println(robot.IsEncryptEnabled() ? "[Estado] mTLS habilitado" : "[Estado] modo en texto plano (referencia)");

        robot.SetTcpFrameListener(frame ->
                System.out.println("[Respuesta TCP] " + frame));

        String mode0 = "/f/bIII52III236III7IIIMode(0)III/b/f";
        String mode1 = "/f/bIII52III236III7IIIMode(1)III/b/f";

        System.out.println("[Enviar] " + mode0);
        robot.SendTCPFrame(mode0);
        robot.Sleep(1000);
        System.out.println("[Enviar] " + mode1);
        robot.SendTCPFrame(mode1);
        robot.Sleep(1000);
        System.out.println("[Enviar] " + mode0);
        robot.SendTCPFrame(mode0);

        robot.Mode(0);
        robot.LoadDefaultProgConfig(0, program_name);
        robot.ProgramLoad(program_name);

        robot.SetSpeedInstant(50);

        robot.ProgramRun();
        robot.Sleep(5000);
        robot.PauseMotion();
        robot.GetProgramState(state);
        System.out.println("program state:" + state[0]);
        java.util.List<Integer> lineRtn = robot.GetCurrentLine();
        System.out.println("current line:" + lineRtn.get(1));
        robot.GetLoadedProgram(loaded_name);
        System.out.println("program name:" + loaded_name[0]);

        robot.ResumeMotion();
        robot.Sleep(2000);
        robot.PauseMotion();
        robot.Sleep(2000);

        System.out.println("========== Fin de la verificación TCP (respuestas en la impresión anterior) ==========");
    }

Actualización por carga del paquete de copia de seguridad de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Actualización por carga del paquete de copia de seguridad de datos
    * @param [in] filePath Ruta del archivo del paquete de copia de seguridad de datos a subir; D://zUP/fr_user_data.tar.gz
    * @return Código de error
    */
    public int DataPackageUpgrade(String filePath)

Obtener el porcentaje de progreso de la actualización del paquete de copia de seguridad de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el porcentaje de progreso de la actualización del paquete de copia de seguridad de datos
    * @return List[0]:código de error; List[1]:porcentaje de progreso de la actualización [0-100], -1:fallo de la actualización
    */
    public List<Integer> GetDataPackageUpgradeProgress()

Ejemplo de código de actualización por carga del paquete de copia de seguridad de datos y consulta del progreso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestDataPackageUpgrade(Robot robot)
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        int rtn = 0;
        robot.Sleep(200);

        rtn = robot.DataPackageUpgrade("D://zUP/upgrade/FR3WMS/fr_user_data.tar.gz");
        System.out.println("robot DataPackageUpgrade rtn is " + rtn);

        int upgradeProgress = 0;
        while (upgradeProgress < 100)
        {
            List<Integer> state = robot.GetDataPackageUpgradeProgress();
            upgradeProgress = state.get(1);
            System.out.println("robot data package upgrade progress : " + upgradeProgress);
            robot.Sleep(200);
        }
    }