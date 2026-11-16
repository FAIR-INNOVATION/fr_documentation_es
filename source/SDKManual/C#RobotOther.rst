Otras interfaces
================

.. toctree:: 
    :maxdepth: 5

Obtener la clave pública SSH
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la clave pública SSH 
    * @param [out] keygen Clave pública
    * @return Código de error 
    */
    int GetSSHKeygen(ref string keygen);

Enviar la instrucción SCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
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
    int SetSSHScpCmd(int mode, string sshname, string sship, string usr_file_url, string robot_file_url);

Calcular el valor MD5 del archivo en la ruta especificada
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Calcular el valor MD5 del archivo en la ruta especificada 
    * @param [in] file_path Ruta del archivo incluyendo el nombre del archivo; la ruta predeterminada de la carpeta Traj es: "/fruser/traj/", por ejemplo "/fruser/traj/trajHelix_aima_1.txt"
    * @param [out] md5 Valor MD5 del archivo
    * @return Código de error 
    */
    int ComputeFileMD5(string file_path, ref string md5);

Ejemplo de código de instrucciones SSH y MD5 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    private void button46_Click(object sender, EventArgs e)
    {
        string file_path = "/fruser/airlab.lua";
        string md5 = "";
        byte emerg_state = 0;
        byte si0_state = 0;
        byte si1_state = 0;
        int sdk_com_state = 0;

        string ssh_keygen = "";
        int retval = robot.GetSSHKeygen(ref ssh_keygen);
        Console.WriteLine("GetSSHKeygen retval is: {0}", retval);
        Console.WriteLine("ssh key is: {0}", ssh_keygen);

        string ssh_name = "fr";
        string ssh_ip = "192.168.58.45";
        string ssh_route = "/home/fr";
        string ssh_robot_url = "/root/robot/dhpara.config";
        retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
        Console.WriteLine("SetSSHScpCmd retval is: {0}", retval);
        Console.WriteLine("robot url is: {0}", ssh_robot_url);

        robot.ComputeFileMD5(file_path, ref md5);
        Console.WriteLine("md5 is: {0}", md5);
    }

Establecer el período de retroalimentación del puerto 20004 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el período de retroalimentación del puerto 20004 del robot
    * @param [in] period Período de retroalimentación del puerto 20004 del robot (ms)
    * @return Código de error
    */
    int SetRobotRealtimeStateSamplePeriod(int period);

Obtener el período de retroalimentación del puerto 20004 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el período de retroalimentación del puerto 20004 del robot
    * @param [out] period Período de retroalimentación del puerto 20004 del robot (ms)
    * @return Código de error
    */
    int GetRobotRealtimeStateSamplePeriod((ref int period);   

Ejemplo de código de configuración del período de retroalimentación de estado del puerto 20004 del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button47_Click(object sender, EventArgs e)
    {
        robot.SetRobotRealtimeStateSamplePeriod(10);
        int getPeriod = 0;
        robot.GetRobotRealtimeStateSamplePeriod(ref getPeriod);
        Console.WriteLine("period is {0}", getPeriod);
        Thread.Sleep(1000);
    }

Actualización del software del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Actualización del software del robot
    * @param [in] filePath Ruta completa del paquete de actualización de software
    * @param [in] block Si se bloquea hasta completar la actualización true:bloqueante; false:no bloqueante
    * @return  Código de error
    */
    int SoftwareUpgrade(string filePath, bool block);

Obtener el estado de actualización del software del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el estado de actualización del software del robot
    * @param [out] state Estado de actualización del paquete de software del robot  0-inactivo o cargando el paquete de actualización; 1~100: porcentaje de actualización completado; -1: fallo de actualización del software; -2: fallo de verificación; -3: fallo de verificación de versión; -4: fallo de descompresión; -5: fallo de actualización de la configuración de usuario; -6: fallo de actualización de la configuración de periféricos; -7: fallo de actualización de la configuración del eje extendido; -8: fallo de actualización de la configuración del robot; -9: fallo de actualización de la configuración de parámetros DH
    * @return  Código de error
    */
    int GetSoftwareUpgradeState(ref int state);

Ejemplo de código de actualización del software del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button48_Click(object sender, EventArgs e)
    {
        robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", false);
        while (true)
        {
            int curState = -1;
            robot.GetSoftwareUpgradeState(ref curState);
            Console.WriteLine("upgrade state is {0}", curState);
            Thread.Sleep(300);
        }
    }

Descargar la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Descargar la tabla de puntos desde el controlador del robot al ordenador local 
    * @param [in] pointTableName Nombre de la tabla de puntos en el controlador: pointTable1.db
    * @param [in] saveFilePath Ruta del ordenador donde se descarga la tabla de puntos C://test/
    * @return Código de error 
    */
    int PointTableDownLoad(string pointTableName, string saveFilePath);

Cargar la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Cargar la tabla de puntos desde el ordenador local al controlador del robot 
    * @param [in] pointTableFilePath Ruta absoluta de la tabla de puntos en el ordenador local C://test/pointTabl e1.db
    * @return Código de error 
    */
    int PointTableUpLoad(string pointTableFilePath);

Actualizar el programa Lua con la tabla de puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Actualizar los puntos del programa lua con la tabla de puntos dada
    * @param [in] pointTableName Nombre de la tabla de puntos en el controlador: "pointTable1.db"; cuando la tabla de puntos está vacía, es decir "", indica que el programa lua se actualiza al programa inicial sin aplicar la tabla de puntos
    * @param [in] luaFileName Nombre del archivo lua a actualizar   "test.lua"
    * @param [out] errorStr Información de error de la actualización del programa lua con la tabla de puntos  
    * @return Código de error 
    */
    int PointTableUpdateLua(string pointTableName, string luaFileName, ref string errorStr);

Cambiar la tabla de puntos y aplicarla
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Cambiar la tabla de puntos y aplicarla
    * @param [in] pointTableName Nombre de la tabla de puntos a cambiar   "pointTable1.db"
    * @param [out] errorStr Información de error del cambio de tabla de puntos   
    * @return Código de error 
    */
    int PointTableSwitch(string pointTableName, ref string errorStr);

Ejemplo de código de operación de la tabla de puntos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnUpload_Click(object sender, EventArgs e)
    {
        string save_path = "D://zDOWN/";
        string point_table_name = "test_point_A.db";
        int rtn = robot.PointTableDownLoad(point_table_name, save_path);
        Console.WriteLine("download : {0} fail: {1}", point_table_name, rtn);

        string upload_path = "D://zUP/test_point_A.db";
        rtn = robot.PointTableUpLoad(upload_path);
        Console.WriteLine("retval is: {0}", rtn);

        string point_tablename = "test_point_A.db";
        string lua_name = "Text1.lua";

        string errorStr = "";
        rtn = robot.PointTableUpdateLua(point_tablename, lua_name, ref errorStr);
        Console.WriteLine("retval is: {0}", rtn);
    }

Descarga del registro del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Descarga del registro del controlador
    * @param [in] savePath Ruta del archivo de guardado "D://zDown/"
    * @return  Código de error
    */
    int RbLogDownload(string savePath);

Descarga de todas las fuentes de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Descarga de todas las fuentes de datos
    * @param [in] savePath Ruta del archivo de guardado "D://zDown/"
    * @return  Código de error
    */
    int AllDataSourceDownload(string savePath);

Descarga del paquete de copia de seguridad de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Descarga del paquete de copia de seguridad de datos
    * @param [in] savePath Ruta del archivo de guardado "D://zDown/"
    * @return  Código de error
    */
    int DataPackageDownload(string savePath);

Ejemplo de código de descarga de datos del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button50_Click(object sender, EventArgs e)
    {
        int rtn = robot.RbLogDownload("D://zDOWN/");
        Console.WriteLine("RbLogDownload rtn is {0}", rtn);

        rtn = robot.AllDataSourceDownload("D://zDOWN/");
        Console.WriteLine("AllDataSourceDownload rtn is {0}", rtn);

        rtn = robot.DataPackageDownload("D://zDOWN/");
        Console.WriteLine("DataPackageDownload rtn is {0}", rtn);
    }

Actualización del sistema operativo del robot (armario de control LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Actualización del sistema operativo del robot (armario de control LA)
     * @param [in] filePath Ruta completa del paquete de actualización del sistema operativo
     * @return  Código de error
     */
    public int KernelUpgrade(string filePath)

Obtener el resultado de la actualización del sistema operativo del robot (armario de control LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Obtener el resultado de la actualización del sistema operativo del robot (armario de control LA)
     * @param [out] result Resultado de la actualización: 0: éxito; -1: fallo
     * @return  Código de error
     */
    public int GetKernelUpgradeResult(ref int[] result)

Establecer la actualización del codificador
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la actualización del codificador
    * @param [in] path Ruta completa del paquete de actualización local (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    int SetEncoderUpgrade(string path);

Establecer la actualización del firmware de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la actualización del firmware de las articulaciones
    * @param [in] type Tipo de archivo de actualización; 1-actualizar firmware; 2-actualizar archivo de configuración del esclavo
    * @param [in] path Ruta completa del paquete de actualización local (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    int SetJointFirmwareUpgrade(int type, string path);

Establecer la actualización del firmware del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la actualización del firmware del armario de control
    * @param [in] type Tipo de archivo de actualización; 1-actualizar firmware; 2-actualizar archivo de configuración del esclavo
    * @param [in] path Ruta completa del paquete de actualización local (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    int SetCtrlFirmwareUpgrade(int type, string path);

Establecer la actualización del firmware del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la actualización del firmware del extremo
    * @param [in] type Tipo de archivo de actualización; 1-actualizar firmware; 2-actualizar archivo de configuración del esclavo
    * @param [in] path Ruta completa del paquete de actualización local (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    int SetEndFirmwareUpgrade(int type, string path);

Actualización del archivo de configuración de todos los parámetros de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Actualización del archivo de configuración de todos los parámetros de las articulaciones
    * @param [in] path Ruta completa del paquete de actualización local (D://zUP/XXXXX.bin)
    * @return Código de error
    */
    int JointAllParamUpgrade(string path);

Ejemplo de código de actualización del firmware del esclavo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    private void button83_Click(object sender, EventArgs e)
    {
        robot.RobotEnable(0);
        Thread.Sleep(200);
        int rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/jointallparameters.db");
        Console.WriteLine($"robot JointAllParamUpgrade rtn is{rtn}");
        rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
        Console.WriteLine($"robot SetCtrlFirmwareUpgrade rtn is{rtn}");
        rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
        Console.WriteLine($"robot SetEndFirmwareUpgrade rtn is {rtn}");
        robot.SetSysServoBootMode();
        rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/upgrade/FR_CTRL_PRIMCU_FV201212_MAIN_U4_T01_20250428(MT).bin");
        Console.WriteLine($"robot SetCtrlFirmwareUpgrade rtn is{rtn}");
        rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/upgrade/FR_END_FV201009_MAIN_U1_T01_20250428.bin");
        Console.WriteLine($"robot SetEndFirmwareUpgrade rtn is {rtn}");
        rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/upgrade/FR_SERVO_FV504214_MAIN_U7_T07_20250519.bin");
        Console.WriteLine($"robot SetJointFirmwareUpgrade rtn is{rtn}");
    }

Generación del registro MCU del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Generación del registro MCU del robot
    * @return Código de error
    */
    public int RobotMCULogCollect();

Establecer la parada del robot al desconectarse la comunicación del puerto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:
    
    /**
    * @brief Establecer la parada del robot al desconectarse la comunicación del puerto
    * @param [in] pordID Número de puerto 0-8080; 1-8083; 2-20002; 3-20004
    * @param [in] enable 0-desactivar; 1-activar
    * @param [in] confirmTime Duración de confirmación de interrupción de comunicación (ms) [0-5000]
    * @return  Código de error
    */
    public int SetRobotStopOnComDisc(int portID, bool enable, int confirmTime)

Obtener los parámetros de parada del robot al desconectarse la comunicación del puerto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:
    
    /**
    * @brief Obtener los parámetros de parada del robot al desconectarse la comunicación del puerto
    * @param [in] pordID Número de puerto 0-8080; 1-8083; 2-20002; 3-20004
    * @param [out] enable 0-desactivar; 1-activar
    * @param [out] confirmTime Duración de confirmación de interrupción de comunicación (ms) [0-5000]
    * @return  Código de error
    */
    public int GetRobotStopOnComDisc(int portID, ref bool enable, ref int confirmTime)
    
Ejemplo de código de parámetros de parada del robot al desconectarse la comunicación del puerto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:
    
    void TestRobotStopOnComDisc()
    {
        int rtn = 0;

        // Establecer los parámetros de los cuatro puertos
        rtn = robot.SetRobotStopOnComDisc(0, true, 330);
        rtn = robot.SetRobotStopOnComDisc(1, true, 550);
        rtn = robot.SetRobotStopOnComDisc(2, true, 110);
        rtn = robot.SetRobotStopOnComDisc(3, true, 220);
        Console.WriteLine($"SetRobotStopOnComDisc {rtn}");

        bool enable = false;
        int confirmTime = 0;

        // Obtener e imprimir la configuración de cada puerto
        robot.GetRobotStopOnComDisc(0, ref enable, ref confirmTime);
        Console.WriteLine($"GetRobotStopOnComDisc 8080 rtn {rtn}; enable is {(enable ? 1 : 0)}; confirm time is {confirmTime}");

        robot.GetRobotStopOnComDisc(1, ref enable, ref confirmTime);
        Console.WriteLine($"GetRobotStopOnComDisc 8083 rtn {rtn}; enable is {(enable ? 1 : 0)}; confirm time is {confirmTime}");

        robot.GetRobotStopOnComDisc(2, ref enable, ref confirmTime);
        Console.WriteLine($"GetRobotStopOnComDisc 20002 rtn {rtn}; enable is {(enable ? 1 : 0)}; confirm time is {confirmTime}");

        robot.GetRobotStopOnComDisc(3, ref enable, ref confirmTime);
        Console.WriteLine($"GetRobotStopOnComDisc 20004 rtn {rtn}; enable is {(enable ? 1 : 0)}; confirm time is {confirmTime}");

    }

Enviar trama de instrucción por UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Enviar trama de instrucción por UDP
    * @param [in] Trama de instrucción
    * @return Código de error
    */
    public int SendUDPFrame(string frame)
        
Ejemplo de código SDK basado en comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void TestRobotUDP()
    {
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[UDP响应] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };


        //Enviar trama
        string frameToSend = "/f/bIII52III236III7IIIMode(1)III/b/f";
        robot.SendUDPFrame(frameToSend);
        Thread.Sleep(2000);
        frameToSend = "/f/bIII52III236III7IIIMode(0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        Thread.Sleep(2000);
        frameToSend = "/f/bIII41III201III153IIIMoveJ(53.857,-89.441,119.453,-22.664,61.059,3.369,-54.249,-491.930,375.396,96.474,-6.896,-7.783,0,0,100,100,100,0.000,0.000,0.000,0.000,-1,0,0,0,0,0,0,0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        Thread.Sleep(2000);
        frameToSend = "/f/bIII42III203III163IIIMoveL(81.736,-85.284,114.974,-23.261,88.746,6.799,125.744,-506.570,375.396,96.474,-6.896,-7.783,0,0,100,100,100,-1,0,0.000,0.000,0.000,0.000,0,0,0,0,0,0,0,0,100,0)III/b/f";
        robot.SendUDPFrame(frameToSend);
        Thread.Sleep(2000);
        frameToSend = "/f/bIII47III400III15IIIGetMCVersion(1)III/b/f/f/bIII48III424III21IIIGetSlaveFirmVersion()III/b/f";
        robot.SendUDPFrame(frameToSend);
        Thread.Sleep(2000);

    }
        
Establecer el color de la luz del extremo del robot definido por el usuario
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el color de la luz del extremo del robot definido por el usuario
    * @param [in] r Control de la luz roja del extremo; 0-apagada; 1-encendida
    * @param [in] g Control de la luz verde del extremo; 0-apagada; 1-encendida
    * @param [in] b Control de la luz azul del extremo; 0-apagada; 1-encendida
    * @return Código de error
    */
    public int SetUserLEDColor(bool r, bool g, bool b)
            
Ejemplo de código SDK para establecer el color de la luz del extremo del robot definido por el usuario
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void testled()
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

Enviar trama de instrucción personalizada a través de TCP 8080
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Enviar trama de instrucción personalizada a través de TCP 8080 (en modo mTLS a través del canal cifrado automáticamente)
    * @param frame Trama de instrucción completa, como "/f/bIII52III236III7IIIMode(0)III/b/f"
    * @return Código de error
    */
    public int SendTCPFrame(string frame)

Ejemplo de código de envío de trama de instrucción personalizada a través de TCP 8080
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestServoJTcp()
    {
        Func<double[], string> fmtArr = a =>
        {
            string[] s = new string[a.Length];
            for (int i = 0; i < a.Length; i++)
                s[i] = a[i].ToString("F3");
            return string.Join(",", s);
        };

        int tcpRcvCnt = 0;
        robot.OnTcpFrameReceived += frame =>
        {
            tcpRcvCnt++;
            Console.WriteLine($"[TCP rpy #{tcpRcvCnt}] {DateTime.Now:HH:mm:ss.fff} {frame}");
        };

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 500;
        float dt = 0.1f;
        int cmdID = 0;
        int frameCount = 0;   

        while (true)
        {
            JointPos j = new JointPos(0, -90, 90, 0, 0, 0);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(0, -90, 90, 0, 0, 0);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
            int ret = robot.GetActualJointPosDegree(flag, ref j);
            if (ret == 0)
            {
                count = 500;
                cmdID += 1;

                {
                    string s = "ServoMoveStart()";
                    FRAME f = new FRAME
                    {
                        count = frameCount++,
                        cmdID = 689,
                        content = s,
                        contentLen = s.Length,
                        head = "/f/b",
                        tail = "/b/f"
                    };
                    robot.SendTCPFrame(FrameHandle.PackFrame(f));
                }

                while (count > 0)
                {
                    {
                        string jointStr = fmtArr(j.jPos);
                        string axisStr = fmtArr(epos.ePos);
                        string s = $"ServoJ({jointStr},{axisStr},{acc:F3},{vel:F3},{cmdT:F3},{filterT:F3},{gain:F3},{cmdID})";
                        FRAME f = new FRAME
                        {
                            count = frameCount++,
                            cmdID = 376,
                            content = s,
                            contentLen = s.Length,
                            head = "/f/b",
                            tail = "/b/f"
                        };
                        robot.SendTCPFrame(FrameHandle.PackFrame(f));
                    }

                    j.jPos[0] += dt;
                    j.jPos[3] += dt;
                    j.jPos[4] += dt;
                    j.jPos[5] += dt;
                    epos.ePos[0] += dt;
                    count -= 1;
                    Thread.Sleep(1);
                    robot.GetRobotRealTimeState(ref pkg);
                    Console.WriteLine($"Servoj命令数量: {pkg.servoJCmdNum}");
                    Console.WriteLine($"Servoj Count {pkg.servoJCmdNum}; last pos is {pkg.lastServoTarget[0]} {pkg.lastServoTarget[1]} {pkg.lastServoTarget[2]} {pkg.lastServoTarget[3]} {pkg.lastServoTarget[4]} {pkg.lastServoTarget[5]}");
                }

                {
                    string s = "ServoMoveEnd()";
                    FRAME f = new FRAME
                    {
                        count = frameCount++,
                        cmdID = 690,
                        content = s,
                        contentLen = s.Length,
                        head = "/f/b",
                        tail = "/b/f"
                    };
                    robot.SendTCPFrame(FrameHandle.PackFrame(f));
                }

                Thread.Sleep(1000);
            }
        }
    }
    
Carga y actualización del paquete de copia de seguridad de datos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Carga y actualización del paquete de copia de seguridad de datos
    * @param [in] filePath Ruta del archivo del paquete de copia de seguridad de datos a cargar; D://zUP/fr_user_data.tar.gz
    * @return Código de error
    */
    public int DataPackageUpgrade(string filePath)
    
Obtener el porcentaje de progreso de la actualización del paquete de copia de seguridad de datos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el porcentaje de progreso de la actualización del paquete de copia de seguridad de datos
    * @param [out] progress Porcentaje de progreso de la actualización [0-100], -1: fallo de actualización
    * @return Código de error
    */
    public int GetDataPackageUpgradeProgress(ref int progress)
    
Obtener el porcentaje de progreso de la actualización de todos los parámetros de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el porcentaje de progreso de la actualización de todos los parámetros de las articulaciones
    * @param [out] progress Porcentaje de progreso de la actualización [0-100], -1: fallo de actualización
    * @return Código de error
    */
    public int GetJointAllParamUpgradeProgress(ref int progress)
        
Ejemplo de código de carga y actualización del paquete de copia de seguridad de datos y consulta del progreso de actualización
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestDataPackageUpgrade()
    {
        int rtn = robot.DataPackageUpgrade("D://zUP/upgrade/FR5/fr_user_data.tar.gz");
        Console.WriteLine($"robot DataPackageUpgrade rtn is {rtn}");

        int upgradeProgress = 0;
        while (upgradeProgress < 100)
        {
            int ret = robot.GetDataPackageUpgradeProgress(ref upgradeProgress);
            Console.WriteLine($"robot data package upgrade progress : {upgradeProgress}, rtn : {ret}");
            if (ret != 0 || upgradeProgress == -1)
            {
                break;
            }
            Thread.Sleep(200);
        }
    }
            
Ejemplo de código de actualización de todos los parámetros de las articulaciones y consulta del progreso de actualización
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
    
    public void TestJointAllParamUpgrade()
    {
        robot.RobotEnable(0);
        Thread.Sleep(200);
        int rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/FR5/jointallparameters.db");
        Console.WriteLine($"robot JointAllParamUpgrade rtn is {rtn}");

        int upgradeProgress = 0;
        while (upgradeProgress < 100)
        {
            int ret = robot.GetJointAllParamUpgradeProgress(ref upgradeProgress);
            Console.WriteLine($"robot joint all param upgrade progress : {upgradeProgress}, rtn : {ret}");
            if (ret != 0 || upgradeProgress == -1)
            {
                break;
            }
            Thread.Sleep(200);
        }
    }