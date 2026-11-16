Configuración de seguridad del robot
====================================

.. toctree:: 
    :maxdepth: 5

Establecer el nivel de colisión
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el nivel de colisión
    * @param  [in]  mode  0-nivel, 1-porcentaje
    * @param  [in]  level Umbral de colisión; el nivel corresponde al rango [1 - 10 corresponde a los niveles 1-10, 100-desactivar]; el porcentaje corresponde al rango [0~10 corresponde a 0% - 100%]
    * @param  [in]  config 0-no actualizar el archivo de configuración, 1-actualizar el archivo de configuración
    * @return  Código de error
    */
    int SetAnticollision(int mode, Object[] level, int config); 

Establecer la estrategia posterior a la colisión
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer la estrategia posterior a la colisión
    * @param  [in] strategy  0-detener con error, 1-continuar ejecutando
    * @param  [in] safeTime  Tiempo de parada segura [1000 - 2000] ms
    * @param  [in] safeDistance  Distancia de parada segura [1-150] mm
    * @param  [in] safetyMargin  Coeficiente de seguridad j1-j6 [1-10]
    * @return  Código de error  
    */
    int SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safetyMargin[]); 

Inicio de la función de umbral de detección de colisión personalizado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /**
    * @brief  Inicio de la función de umbral de detección de colisión personalizado; establecer los umbrales de detección de colisión del lado de las articulaciones y del lado del TCP
    * @param  [in] flag 1-solo detección de articulaciones activada; 2-solo detección de TCP activada; 3-detección de articulaciones y TCP activadas simultáneamente
    * @param  [in] jointDetectionThreshould Umbral de detección de colisión de articulaciones j1-j6
    * @param  [in] tcpDetectionThreshould  Umbral de detección de colisión de TCP, xyzabc
    * @param  [in] block 0-no bloqueante; 1-bloqueante
    * @return  Código de error
    */   
    public int CustomCollisionDetectionStart(int flag, double[] jointDetectionThreshould, double[] tcpDetectionThreshould, int block);

Cierre de la función de umbral de detección de colisión personalizado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /**
    * @brief  Cierre de la función de umbral de detección de colisión personalizado
    * @return  Código de error
    */   
    public int CustomCollisionDetectionEnd();

Ejemplo de código de configuración del nivel de colisión del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestCollision(Robot robot)
    {
        int mode = 0;
        int config = 1;
        Object[] level1 = new Object[]{ 1.0,2.0,3.0,4.0,5.0,6.0 };
        Object[] level2 = new Object[]{ 50.0,20.0,30.0,40.0,50.0,60.0 };

        int rtn = robot.SetAnticollision(mode, level1, config);
        System.out.println("SetAnticollision mode 0 rtn is: "+ rtn);
        mode = 1;
        rtn = robot.SetAnticollision(mode, level2, config);
        System.out.println("SetAnticollision mode 1 rtn is :"+ rtn);

        JointPos p1Joint=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos p2Joint=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose p1Desc=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offdese=new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        robot.MoveL(p2Joint, p2Desc, 0, 0, 100, 100, 100, 2,0, exaxisPos, 0, 0, offdese,0,10);
        robot.ResetAllError();
        int[] safety = new int[]{ 5,5,5,5,5,5 };
        rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
        System.out.println("SetCollisionStrategy rtn is:"+ rtn);

        double[] jointDetectionThreshould = new double[]{ 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
        double[] tcpDetectionThreshould =new double[] { 60,60,60,60,60,60 };
        rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
        System.out.println("CustomCollisionDetectionStart rtn is :"+ rtn);

        robot.MoveL(p1Joint, p1Desc, 0, 0, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);
        robot.MoveL(p2Joint, p2Desc, 0, 0, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);
        rtn = robot.CustomCollisionDetectionEnd();
        System.out.println("CustomCollisionDetectionEnd rtn is: "+ rtn);
        return 0;
    }

Establecer el límite positivo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el límite positivo
    * @param  [in] limit Posición de las seis articulaciones, unidad deg
    * @return  Código de error
    */
    int SetLimitPositive(Object[] limit); 

Establecer el límite negativo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el límite negativo
    * @param  [in] limit Posición de las seis articulaciones, unidad deg
    * @return  Código de error
    */
    int SetLimitNegative(Object[] limit); 

Obtener el ángulo del límite suave de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el ángulo del límite suave de las articulaciones
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] negative  Ángulo del límite negativo, unidad deg
    * @param  [out] positive  Ángulo del límite positivo, unidad deg
    * @return  Código de error
    */
    int GetJointSoftLimitDeg(int flag, Object[] negative, Object[] positive); 

Ejemplo de código de configuración de límites del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLimit(Robot robot)
    {
        Object[] plimit =new Object[] { 170.0,80.0,150.0,80.0,170.0,160.0 };
        robot.SetLimitPositive(plimit);
        Object[] nlimit =new Object[] { -170.0,-260.0,-150.0,-260.0,-170.0,-160.0 };
        robot.SetLimitNegative(nlimit);

        Object[] neg_deg =new Object[] {0, 0 , 0, 0, 0, 0}, pos_deg = new Object[]{0, 0 , 0, 0, 0, 0};
        robot.GetJointSoftLimitDeg(1,  neg_deg,  pos_deg);
        System.out.println("neg limit deg:"+ neg_deg[0]+","+ neg_deg[1]+","+ neg_deg[2]+","+ neg_deg[3]+","+ neg_deg[4]+","+ neg_deg[5]);
        System.out.println("pos limit deg:"+pos_deg[0]+","+ pos_deg[1]+","+ pos_deg[2]+","+ pos_deg[3]+","+ pos_deg[4]+","+pos_deg[5]);
        return 0;
    }

Establecer el método de detección de colisión del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el método de detección de colisión del robot
    * @param [in] method Método de detección de colisión: 0-modo de corriente; 1-doble codificador; 2-corriente y doble codificador activados simultáneamente
    * @param [in] thresholdMode Modo de umbral del nivel de colisión; 0-modo de umbral fijo por nivel de colisión; 1-umbral de detección de colisión personalizado
    * @return Código de error
    */
    int SetCollisionDetectionMethod(int method,int thresholdMode)

Establecer el inicio y cierre de la detección de colisión en estado estático
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el inicio y cierre de la detección de colisión en estado estático
    * @param  [in] status 0-cerrar; 1-abrir
    * @return  Código de error
    */
    public int SetStaticCollisionOnOff(int status)

Ejemplo de código de configuración del método de detección de colisión del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestCollisionMethod(Robot robot)
    {
        int rtn = robot.SetCollisionDetectionMethod(0);

        rtn = robot.SetStaticCollisionOnOff(1);
        System.out.println("SetStaticCollisionOnOff On rtn is:"+ rtn);
        robot.Sleep(5000);
        rtn = robot.SetStaticCollisionOnOff(0);
        System.out.println("SetStaticCollisionOnOff Off rtn is:"+ rtn);

        robot.CloseRPC();
        return 0;
    }

Detección de potencia de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Detección de potencia de par de las articulaciones
    * @param  [in] status 0-cerrar; 1-abrir
    * @param  [in] power Potencia máxima configurada (W)
    * @return  Código de error
    */
    public int SetPowerLimit(int status, double power)

Ejemplo de código de detección de potencia de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestPowerLimit(Robot robot)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        List<Number> joint_toq=new ArrayList<>();
        joint_toq=robot.GetJointTorques(1);

        int count = 100;
        robot.ServoJTStart(); //   #inicio de servoJT
        int error = 0;
        while (count > 0)
        {
            count = count - 1;
            robot.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);

        robot.CloseRPC();
        return 0;
    }
    
Establecer los parámetros de velocidad de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer los parámetros de velocidad de seguridad
    * @param enable 0-desactivado; 1-activado en modo manual; 2-activado en todos los modos (no admite limitación automática de velocidad)
    * @param maxTCPVel Limitar la velocidad máxima del TCP;[0-1000] mm/s
    * @param strategy Estrategia tras exceso de velocidad; 0-detener y alarmar; 1-limitación automática de velocidad; 2-detener, alarmar y deshabilitar
    * @param maxJointVel Velocidad máxima de las 6 articulaciones (°/s), por defecto 45°/s
    * @return Código de error
    */
    public int SetVelReducePara(int enable, double maxTCPVel, int strategy, double[] maxJointVel)
        
Ejemplo de código SDK para establecer los parámetros de velocidad de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSetVelReducePara(Robot robot) {
        int rtn = 0;

        JointPos j1 = new JointPos(0, -90, 90, 0, 0, 0);
        JointPos j2 = new JointPos(90, -90, 90, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        robot.SetSpeed(80);
        rtn = robot.SetVelReducePara(2, 30, 1);
        System.out.printf("SetVelReducePara param error rtn is %d\n", rtn);

        rtn = robot.SetVelReducePara(0, 30, 1);
        System.out.printf("SetVelReducePara disable reduce vel rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        rtn = robot.SetVelReducePara(1, 30, 1);
        System.out.printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        rtn = robot.SetVelReducePara(2, 30, 2);
        System.out.printf("SetVelReducePara disable robot rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        robot.Sleep(2000);
        robot.ResetAllError();
        robot.RobotEnable(1);
        robot.Sleep(1000);

        rtn = robot.SetVelReducePara(2, 30, 0);
        System.out.printf("SetVelReducePara report error rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        robot.Sleep(1000);
        return 0;
    }
            
Ejemplo de código de configuración de la velocidad de seguridad de las articulaciones del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSetJointVelReducePara(Robot robot) {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        JointPos j1 = new JointPos(10.220, -11.121, -118.086, -46.739, 82.036, 131.503);
        JointPos j2 = new JointPos(89.782, -11.122, -118.086, -46.740, 82.036, 131.504);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        robot.SetSpeed(20);

        double[] maxJointVelA = {100.0, 100.0, 100.0, 100.0, 100.0, 100.0};
        int rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelA);
        System.out.printf("SetVelReducePara param error rtn is %d\n", rtn);
        robot.MoveJ(j1, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);

        double[] maxJointVelB = {20.0, 20.0, 20.0, 20.0, 20.0, 20.0};
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelB);
        System.out.printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(j1, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);

        robot.Sleep(2000);
        return 0;
    }

Obtener la suma de verificación de los parámetros de configuración de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener la suma de verificación de los parámetros de configuración de seguridad
    * @param status Estado de verificación, 0-válido, 1-en verificación, 2-verificación fallida
    * @param checksum Suma de verificación, 8 dígitos hexadecimales
    * @return Código de error
    */
    public int GetSafetyParamsCheckSum(int[] status, long[] checksum)

Verificación de la contraseña de operación de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Verificación de la contraseña de operación de seguridad
    * @param status Verificación, 0-abrir, 1-cerrar
    * @param password Contraseña
    * @return Código de error
    */
    public int SafetyOPPasswordCheck(int status, String password)

Ejemplo de código de obtención de la suma de verificación de los parámetros de configuración de seguridad y verificación de la contraseña de operación de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestSafetyParamsCheckSum(Robot robot)
    {
        int[] status = new int[1];
        long[] checksum = new long[1];

        int error = robot.GetSafetyParamsCheckSum(status, checksum);
        System.out.println(String.format("GetSafetyParamsCheckSum: error=%d, status=%d, hex_code=%08X", 
            error, status[0], checksum[0]));
        
        try {
            Thread.sleep(3000);
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }

        error = robot.SafetyOPPasswordCheck(0, "12345678");
        System.out.println(String.format("SafetyOPPasswordCheck: error=%d", error));

        if (error == 0)
        {
            Object[] level = {2.0, 2.0, 2.0, 2.0, 2.0, 2.0};
            error = robot.SetAnticollision(0, level, 1);
            System.out.println(String.format("SetAnticollision: error=%d", error));

            error = robot.SetCollisionStrategy(0, 1000, 150, 0, new int[]{10, 10, 10, 10, 10, 10});
            System.out.println(String.format("SetCollisionStrategy: error=%d", error));
        }

        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }

        error = robot.GetSafetyParamsCheckSum(status, checksum);
        System.out.println(String.format("GetSafetyParamsCheckSum(again): error=%d, status=%d, hex_code=%08X", 
            error, status[0], checksum[0]));
    }
    
Establecer la habilitación del cifrado mTLS y la ruta del certificado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    //Interruptor general de mTLS: valor predeterminado false; establecer false antes de la inicialización de RPC para forzar el modo en texto plano
    public bool EnableMtls = false;

    /**
    * @brief Establecer la ruta del certificado de cifrado TLS
    * @param [in] certPath  Ruta del certificado; si está vacío, por defecto es el certificado ubicado en el directorio del archivo ejecutable; nombres de certificado: ca.crt;client.crt;client.key
    * @return Código de error
    */
    public MtlsLink(String certDir)

Ejemplo de código para establecer la ruta del certificado de cifrado TLS
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

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
    }