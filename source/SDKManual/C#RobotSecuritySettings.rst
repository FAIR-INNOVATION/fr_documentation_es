Configuración de seguridad del robot
=====================================

.. toctree:: 
    :maxdepth: 5

Establecer el nivel de colisión
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el nivel de colisión
    * @param  [in]  mode  0-nivel, 1-porcentaje
    * @param  [in]  level Umbral de colisión; para el nivel, rango [], para el porcentaje, rango [0~1]
    * @param  [in]  config 0-no actualizar el archivo de configuración, 1-actualizar el archivo de configuración
    * @return  Código de error
    */
    int SetAnticollision(int mode, double[] level, int config); 

Establecer la estrategia tras la colisión
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer la estrategia tras la colisión
    * @param  [in] strategy  0-pausar con error; 1-continuar en ejecución; 2-detener con error; 3-modo de par de gravedad; 4-modo de respuesta oscilatoria; 5-modo de rebote tras colisión
    * @param  [in] safeTime  Tiempo de parada segura [1000 - 2000] ms
    * @param  [in] safeDistance  Distancia de parada segura [1-150] mm
    * @param  [in] safeVel  Velocidad de parada segura del TCP [50-250] mm/s
    * @param  [in] safetyMargin  Coeficiente de seguridad j1-j6 [1-10]
    * @return  Código de error
    */
    int SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safeVel,int[] safetyMargin);

Inicio de la función de umbral de detección de colisiones personalizado
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inicio de la función de umbral de detección de colisiones personalizado; establece los umbrales de detección de colisiones del extremo de las articulaciones y del TCP
    * @param  [in] flag 1-solo detección de articulaciones activada; 2-solo detección de TCP activada; 3-detección de articulaciones y de TCP activadas simultáneamente
    * @param  [in] jointDetectionThreshould Umbral de detección de colisiones de las articulaciones j1-j6
    * @param  [in] tcpDetectionThreshould Umbral de detección de colisiones del TCP, xyzabc
    * @param  [in] block 0-no bloqueante; 1-bloqueante
    * @return  Código de error
    */
    int CustomCollisionDetectionStart(int flag, double[] jointDetectionThreshould, double[] tcpDetectionThreshould, int block);

Cierre de la función de umbral de detección de colisiones personalizado
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Cierre de la función de umbral de detección de colisiones personalizado
    * @return  Código de error
    */
    int CustomCollisionDetectionEnd()

Ejemplo de código de configuración del nivel de colisión del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button24_Click(object sender, EventArgs e)
    {
        int mode = 0;
        int config = 1;
        double[] level1 = { 1.0f, 2.0f, 3.0f, 4.0f, 5.0f, 6.0f };
        double[] level2 = { 50.0f, 20.0f, 30.0f, 40.0f, 50.0f, 60.0f };

        int rtn = robot.SetAnticollision(mode, level1, config);
        Console.WriteLine($"SetAnticollision mode 0 rtn is {rtn}");
        mode = 1;
        rtn = robot.SetAnticollision(mode, level2, config);
        Console.WriteLine($"SetAnticollision mode 1 rtn is {rtn}");

        JointPos p1Joint = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos p2Joint = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose p1Desc = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose p2Desc = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0.0f, 0.0f, 0.0f, 0.0f);
        DescPose offdese = new DescPose(0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f);
        robot.MoveL( p2Joint,  p2Desc, 0, 0, 100, 100, 100, 2,  exaxisPos, 0, 0,  offdese);
        robot.ResetAllError();
        int[] safety = { 5, 5, 5, 5, 5, 5 };
        rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
        Console.WriteLine($"SetCollisionStrategy rtn is {rtn}");

        double[] jointDetectionThreshould = { 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
        double[] tcpDetectionThreshould = { 60, 60, 60, 60, 60, 60 };
        rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
        Console.WriteLine($"CustomCollisionDetectionStart rtn is {rtn}");

        robot.MoveL( p1Joint,  p1Desc, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
        robot.MoveL( p2Joint,  p2Desc, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
        rtn = robot.CustomCollisionDetectionEnd();
        Console.WriteLine($"CustomCollisionDetectionEnd rtn is {rtn}");
    }

Establecer el límite positivo
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el límite positivo
    * @param  [in] limit Posiciones de las seis articulaciones, unidad deg
    * @return  Código de error
    */
    int SetLimitPositive(double[] limit); 

Establecer el límite negativo
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el límite negativo
    * @param  [in] limit Posiciones de las seis articulaciones, unidad deg
    * @return  Código de error
    */
    int SetLimitNegative(double[] limit); 

Obtener los ángulos del límite software de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener los ángulos del límite software de las articulaciones
    * @param  [in] flag 0-bloqueante, 1-no bloqueante	 
    * @param  [out] negative  Ángulos del límite negativo, unidad deg
    * @param  [out] positive  Ángulos del límite positivo, unidad deg
    * @return  Código de error
    */
    int GetJointSoftLimitDeg(byte flag, ref double[] negative, ref double[] positive);

Ejemplo de código de configuración de los límites del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        double[] plimit = { 170.0f, 80.0f, 150.0f, 80.0f, 170.0f, 160.0f };
        robot.SetLimitPositive(plimit);
        double[] nlimit = { -170.0f, -260.0f, -150.0f, -260.0f, -170.0f, -160.0f };
        robot.SetLimitNegative(nlimit);

        double[] neg_deg = new double[6] {0,0,0,0,0,0 };
        double[] pos_deg = new double[6] { 0, 0, 0, 0, 0, 0 };
        robot.GetJointSoftLimitDeg(0, ref neg_deg,ref pos_deg);
        Console.WriteLine($"neg limit deg:{neg_deg[0]},{neg_deg[1]},{neg_deg[2]},{neg_deg[3]},{neg_deg[4]},{neg_deg[5]}");
        Console.WriteLine($"pos limit deg:{pos_deg[0]},{pos_deg[1]},{pos_deg[2]},{pos_deg[3]},{pos_deg[4]},{pos_deg[5]}");
    }

Establecer el método de detección de colisiones del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el método de detección de colisiones del robot
    * @param  [in] method Método de detección de colisiones: 0-modo de corriente; 1-doble codificador; 2-corriente y doble codificador activados simultáneamente
    * @param [in] thresholdMode Modo de umbral del nivel de colisión; 0-modo de umbral fijo del nivel de colisión; 1-umbral de detección de colisión personalizado
    * @return  Código de error
    */
    int SetCollisionDetectionMethod(int method,int thresholdMode=0);


Establecer la activación/desactivación de la detección de colisiones en estado estático
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la activación/desactivación de la detección de colisiones en estado estático
    * @param  [in] status 0-desactivar; 1-activar
    * @return  Código de error
    */
    int SetStaticCollisionOnOff(int status);

Ejemplo de código de configuración del método de detección de colisiones del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button26_Click(object sender, EventArgs e)
    {
        int rtn = robot.SetCollisionDetectionMethod(0, 0);

        rtn = robot.SetStaticCollisionOnOff(1);
        Console.WriteLine($"SetStaticCollisionOnOff On rtn is {rtn}");
        Thread.Sleep(5000);
        rtn = robot.SetStaticCollisionOnOff(0);
        Console.WriteLine($"SetStaticCollisionOnOff Off rtn is {rtn}");
    }

Detección de potencia y par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Detección de potencia y par de las articulaciones
    * @param  [in] status 0-desactivar; 1-activar
    * @param  [in] power Potencia máxima establecida (W)
    * @return  Código de error
    */
    int SetPowerLimit(int status, double power);

Ejemplo de código de detección de potencia y par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button26_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        double[] torques = { 0, 0, 0, 0, 0, 0 };
        robot.GetJointTorques(1, torques);

        int count = 100;
        robot.ServoJTStart();
        int error = 0;
        while (count > 0)
        {
            error = robot.ServoJT(torques, 0.001f);
            count--;
            Thread.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);
    }

Establecer los parámetros de velocidad de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer los parámetros de velocidad de seguridad
    * @param [in] enable 0-desactivar; 1-activar en modo manual; 2-activar en todos los modos (no admite limitación automática de velocidad)
    * @param [in] maxTCPVel Limitar la velocidad TCP máxima; [0-1000] mm/s
    * @param [in] strategy Estrategia tras exceso de velocidad; 0-detener con alarma; 1-limitación automática de velocidad; 2-detener con alarma y deshabilitar
    * @param [in] maxJointVel Velocidad máxima de las 6 articulaciones (°/s), por defecto 45°/s
    * @return Código de error
    */
    public int SetVelReducePara(int enable, double maxTCPVel, int strategy, double[] maxJointVel = null)
    
Ejemplo de código SDK de configuración de los parámetros de velocidad de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int TestSetVelReducePara()
    {
        int rtn = 0;
        JointPos j1 = new JointPos(10.220, -11.121, -118.086, -46.739, 82.036, 131.503);
        JointPos j2 = new JointPos(89.782, -11.122, -118.086, -46.740, 82.036, 131.504);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        double[] maxJointVel = new double[] { 100.0, 100.0, 100.0, 100.0, 100.0, 100.0 };

        robot.SetSpeed(20);
        rtn = robot.SetVelReducePara(0, 200, 0, maxJointVel);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);

        // 1st
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel);
        Console.WriteLine($"SetVelReduceParaA param error rtn is {rtn}");
        robot.MoveJ(j1, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);

        // 2rd
        maxJointVel = new double[] { 20.0, 20.0, 20.0, 20.0, 20.0, 20.0 };
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel);
        Console.WriteLine($"SetVelReduceParaB reduce vel rtn is {rtn}");
        robot.MoveJ(j1, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        return 0; 
    }
        
Obtener la suma de verificación de los parámetros de configuración de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:  

    /**
    * @brief  Obtener la suma de verificación de los parámetros de configuración de seguridad
    * @param  [out] status Estado de verificación, 0-válido, 1-en verificación, 2-verificación fallida
    * @param  [out] checksum Suma de verificación de 8 dígitos hexadecimales
    * @return  Código de error
    */
    public int GetSafetyParamsCheckSum(ref int status, ref uint checksum)
        
Establecer la habilitación del cifrado mTLS y la ruta de los certificados
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:  

    // Interruptor general de mTLS: por defecto false; establecer false antes de la inicialización de RPC para forzar el modo en claro
    public bool EnableMtls { get; set; } = false;

    // Directorio de certificados mTLS: por defecto null = certs/ en el mismo directorio que la dll del SDK; debe establecerse antes de RPC()
    public string MtlsCertDir { get; set; }
        
Ejemplo de código de configuración de la habilitación del cifrado mTLS y la ruta de los certificados
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:  

    public Form1()
    {
        InitializeComponent();
        robot = new Robot();//instanciar el objeto robot
        string path = "D://log/";
        robot.LoggerInit(FrLogType.BUFFER, FrLogLevel.INFO, path, 5, 5);
        robot.SetLoggerLevel(FrLogLevel.INFO);

        // Consultar la configuración final de CNDE
        List<RobotState> finalStates;
        int finalPeriod;
        robot.GetRobotRealtimeStateConfig(out finalStates, out finalPeriod);
        Console.WriteLine($"最终配置状态数量: {finalStates.Count}");
        foreach (var s in finalStates) Console.WriteLine($"  {s}");
        Console.WriteLine($"最终周期: {finalPeriod} ms");
        robot.SetReconnectParam(true, 1000, 500);//parámetros de reconexión tras desconexión
            
        robot.EnableMtls = true;
        robot.MtlsCertDir = @"D:\C#SDK\MTLS-certs";   // si no se establece la ruta de los certificados, por defecto es <directorio de libfairino.dll>\certs
        rrpc = robot.RPC("192.168.58.2"); //establecer conexión con el armario de control
                                            //tiempo de espera agotado de recepción del puerto 20004
                                            //robot.SetReceivePortTimeout(40);
    }
        
Verificación de la contraseña de operaciones de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:  

    /**
    * @brief  Verificación de la contraseña de operaciones de seguridad
    * @param  [in] status Verificación, 0-activar, 1-desactivar
    * @param  [in] password Contraseña
    * @return  Código de error
    */
    public int SafetyOPPasswordCheck(int status, string password)
            
Ejemplo de código de obtención de la suma de verificación de los parámetros de configuración de seguridad y de verificación de la contraseña de operaciones de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:  

    public void TestSafetyParamsCheckSum()
    {
        int status = 0;
        uint checksum = 0;

        int error = robot.GetSafetyParamsCheckSum(ref status, ref checksum);
        Console.WriteLine("GetSafetyParamsCheckSum: error={0}, status={1}, hex_code={2:X8}", error, status, checksum);
        Thread.Sleep(3000);

        error = robot.SafetyOPPasswordCheck(0, "12345678");
        Console.WriteLine("SafetyOPPasswordCheck: error={0}", error);

        if (error == 0)
        {
            error = robot.SetAnticollision(0, new double[] { 2.0, 2.0, 2.0, 2.0, 2.0, 2.0 }, 1);
            Console.WriteLine("SetAnticollision: error={0}", error);

            error = robot.SetCollisionStrategy(0, 1000, 150, 0, new int[] { 10, 10, 10, 10, 10, 10 });
            Console.WriteLine("SetCollisionStrategy: error={0}", error);
        }

        Thread.Sleep(1000);

        error = robot.GetSafetyParamsCheckSum(ref status, ref checksum);
        Console.WriteLine("GetSafetyParamsCheckSum(again): error={0}, status={1}, hex_code={2:X8}", error, status, checksum);
    }