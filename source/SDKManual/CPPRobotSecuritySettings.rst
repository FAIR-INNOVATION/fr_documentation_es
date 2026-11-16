Configuración de seguridad del robot
====================================

.. toctree:: 
    :maxdepth: 5

Establecer el nivel de colisión
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer el nivel de colisión
    * @param  [in]  mode  0-nivel, 1-porcentaje
    * @param  [in]  level Umbral de colisión, rango correspondiente al nivel [], rango correspondiente al porcentaje [0~1]
    * @param  [in]  config 0-no actualizar el archivo de configuración, 1-actualizar el archivo de configuración
    * @return  Código de error
    */
    errno_t  SetAnticollision(int mode, float level[6], int config);

Establecer la estrategia posterior a la colisión
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
	 * @brief  Establecer la estrategia posterior a la colisión
	 * @param  [in] strategy  0-pausar con error; 1-continuar ejecutando; 2-detener con error; 3-modo de par de gravedad; 4-modo de respuesta oscilante; 5-modo de rebote por colisión 
	 * @param  [in] safeTime  Tiempo de parada segura [1000 - 2000]ms
	 * @param  [in] safeDistance  Distancia de parada segura [1-150]mm
	 * @param  [in] safetyMargin  Coeficiente de seguridad j1-j6 [1-10]
	 * @return  Código de error
	 */
	errno_t SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safetyMargin[]);

Inicio de la función de umbral de detección de colisión personalizado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

	 /**
	 * @brief  Inicio de la función de umbral de detección de colisión personalizado, establecer los umbrales de detección de colisión del lado de las articulaciones y del lado del TCP
	 * @param  [in] flag 1-solo detección de articulaciones activada; 2-solo detección de TCP activada; 3-detección de articulaciones y TCP activadas simultáneamente
	 * @param  [in] jointDetectionThreshould Umbral de detección de colisión de articulaciones j1-j6
	 * @param  [in] tcpDetectionThreshould Umbral de detección de colisión de TCP, xyzabc
	 * @param  [in] block 0-no bloqueante; 1-bloqueante
	 * @return  Código de error
	 */
	errno_t CustomCollisionDetectionStart(int flag, double jointDetectionThreshould[6], double tcpDetectionThreshould[6], int block);

Fin de la función de umbral de detección de colisión personalizado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

	/**
	 * @brief  Cierre de la función de umbral de detección de colisión personalizado
	 * @return  Código de error
	 */
	errno_t CustomCollisionDetectionEnd();

Ejemplo de código de configuración del nivel de colisión del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestCollision(void)
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
         int mode = 0;
         int config = 1;
         float level1[6] = { 1.0,2.0,3.0,4.0,5.0,6.0 };
         float level2[6] = { 50.0,20.0,30.0,40.0,50.0,60.0 };
         rtn = robot.SetAnticollision(mode, level1, config);
         printf("SetAnticollision mode 0 rtn is %d\n", rtn);
         mode = 1;
         rtn = robot.SetAnticollision(mode, level2, config);
         printf("SetAnticollision mode 1 rtn is %d\n", rtn);
         JointPos p1Joint(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos p2Joint(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0.0, 0.0, 0.0, 0.0);
         DescPose offdese(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
         robot.MoveL(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, 2, &exaxisPos, 0, 0, &offdese);
         robot.ResetAllError();
         int safety[6] = { 5,5,5,5,5,5 };
         rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
         printf("SetCollisionStrategy rtn is %d\n", rtn);
         double jointDetectionThreshould[6] = { 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
         double tcpDetectionThreshould[6] = { 60,60,60,60,60,60 };
         rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
         cout << "CustomCollisionDetectionStart rtn is " << rtn << endl;
         robot.MoveL(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
         robot.MoveL(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
         rtn = robot.CustomCollisionDetectionEnd();
         cout << "CustomCollisionDetectionEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Establecer límite positivo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer límite positivo
    * @param  [in] limit Posición de las seis articulaciones, unidad deg
    * @return  Código de error
    */
    errno_t  SetLimitPositive(float limit[6]);

Establecer límite negativo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer límite negativo
    * @param  [in] limit Posición de las seis articulaciones, unidad deg
    * @return  Código de error
    */
    errno_t  SetLimitNegative(float limit[6]);   

Obtener el ángulo del límite suave de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el ángulo del límite suave de las articulaciones
    * @param  [in] flag 0-bloqueante, 1-no bloqueante    
    * @param  [out] negative  Ángulo del límite negativo, unidad deg
    * @param  [out] positive  Ángulo del límite positivo, unidad deg
    * @return  Código de error
    */
    errno_t  GetJointSoftLimitDeg(uint8_t flag, float negative[6], float positive[6]);
    
Ejemplo de código de configuración de límites del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestLimit(void)
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
      float plimit[6] = { 170.0,80.0,150.0,80.0,170.0,160.0 };
      robot.SetLimitPositive(plimit);
      float nlimit[6] = { -170.0,-260.0,-150.0,-260.0,-170.0,-160.0 };
      robot.SetLimitNegative(nlimit);
      float neg_deg[6] = { 0.0 }, pos_deg[6] = { 0.0 };
      robot.GetJointSoftLimitDeg(0, neg_deg, pos_deg);
      printf("neg limit deg:%f,%f,%f,%f,%f,%f\n", neg_deg[0], neg_deg[1], neg_deg[2], neg_deg[3], neg_deg[4], neg_deg[5]);
      printf("pos limit deg:%f,%f,%f,%f,%f,%f\n", pos_deg[0], pos_deg[1], pos_deg[2], pos_deg[3], pos_deg[4], pos_deg[5]);
      robot.CloseRPC();
      return 0;
    }

Establecer el método de detección de colisión del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el método de detección de colisión del robot
    * @param [in] method Método de detección de colisión: 0-modo de corriente; 1-doble codificador; 2-corriente y doble codificador activados simultáneamente
    * @param [in] thresholdMode Modo de umbral del nivel de colisión; 0-modo de umbral fijo por nivel de colisión; 1-umbral de detección de colisión personalizado
    * @return  Código de error
    */
    errno_t SetCollisionDetectionMethod(int method, int thresholdMode = 0);

Establecer el inicio y cierre de la detección de colisión en estado estático
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Establecer el inicio y cierre de la detección de colisión en estado estático
     * @param [in] status 0-cerrar; 1-abrir
     * @return Código de error
     */
    errno_t SetStaticCollisionOnOff(int status);

Ejemplo de código de configuración del método de detección de colisión del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    int TestCollisionMethod(void)
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
      rtn = robot.SetCollisionDetectionMethod(0, 0);
      printf("SetCollisionDetectionMethod rtn is %d\n", rtn);
      rtn = robot.SetStaticCollisionOnOff(1);
      printf("SetStaticCollisionOnOff On rtn is %d\n", rtn);
      rtn = robot.Sleep(5000);
      rtn = robot.SetStaticCollisionOnOff(0);
      printf("SetStaticCollisionOnOff Off rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Detección de potencia de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Detección de potencia de par de las articulaciones
     * @param [in] status 0-cerrar; 1-abrir
     * @param [in] power Potencia máxima configurada (W);
     * @return Código de error
     */
    errno_t SetPowerLimit(int status, double power);

Ejemplo de código de detección de potencia de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestPowerLimit(void)
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
       robot.DragTeachSwitch(1);
       robot.SetPowerLimit(1, 200);
       float torques[] = { 0, 0, 0, 0, 0, 0 };
       robot.GetJointTorques(1, torques);
       int count = 100;
       robot.ServoJTStart(); 
       int error = 0;
       while (count > 0)
       {
          error = robot.ServoJT(torques, 0.001);
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
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer los parámetros de velocidad de seguridad
    * @param [in] enable 0-desactivado; 1-activado en modo manual; 2-activado en todos los modos
    * @param [in] maxTCPVel Limitar la velocidad máxima del TCP; [0-1000]mm/s
    * @param [in] strategy Estrategia tras exceso de velocidad; 0-detener y alarmar; 1-limitación automática de velocidad; 2-detener, alarmar y deshabilitar
    * @param [in] maxJointVel Velocidad máxima de las 6 articulaciones (°/s), por defecto 45°/s
    * @return Código de error
    */
    errno_t SetVelReducePara(int enable, double maxTCPVel, int strategy, std::vector<double> maxJointVel = {45.0, 45.0, 45.0, 45.0, 45.0, 45.0});
        
Ejemplo de código SDK para establecer los parámetros de velocidad de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestSetVelReducePara()
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
        JointPos j1(0, -90, 90, 0, 0, 0);
        JointPos j2(90, -90, 90, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.SetSpeed(80);
        rtn = robot.SetVelReducePara(2, 30, 1);
        printf("SetVelReducePara param error rtn is %d\n", rtn);
        rtn = robot.SetVelReducePara(0, 30, 1);
        printf("SetVelReducePara disable reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        rtn = robot.SetVelReducePara(1, 30, 1);
        printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        rtn = robot.SetVelReducePara(2, 30, 2);
        printf("SetVelReducePara disable robot rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(2000);
        robot.ResetAllError();
        robot.RobotEnable(1);
        robot.Sleep(1000);
        rtn = robot.SetVelReducePara(2, 30, 0);
        printf("SetVelReducePara report error rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Ejemplo de código de configuración de la velocidad de seguridad de las articulaciones del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:    

    int TestSetJointVelReducePara()
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
        JointPos j1(10.220, -11.121, -118.086, -46.739, 82.036, 131.503);
        JointPos j2(89.782, -11.122, -118.086, -46.740, 82.036, 131.504);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.SetSpeed(20);

        std::vector<double> maxJointVelA = {100.0, 100.0, 100.0, 100.0, 100.0, 100.0 };
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelA);
        printf("SetVelReducePara param error rtn is %d\n", rtn);
        robot.MoveJ(&j1, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        std::vector<double> maxJointVelB = { 20.0, 20.0, 20.0, 20.0, 20.0, 20.0 };
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelB);
        printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(2000);
        robot.CloseRPC();
        return 0;
    }
    
Obtener la suma de verificación de los parámetros de configuración de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:   

    /**
    * @brief Obtener la suma de verificación de los parámetros de configuración de seguridad
    * @param [out] status Estado de verificación, 0-válido, 1-en verificación, 2-verificación fallida
    * @param [out] checksum Suma de verificación, 8 dígitos hexadecimales
    * @return  Código de error 
    */
    errno_t GetSafetyParamsCheckSum(int& status, uint32_t& checksum);
    
Verificación de la contraseña de operación de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:   

    /**
    * @brief Verificación de la contraseña de operación de seguridad
    * @param [in] status Verificación, 0-abrir, 1-cerrar
    * @param [in] password Contraseña
    * @return Código de error
    */
    errno_t SafetyOPPasswordCheck(int status, std::string password);
        
Ejemplo de código de verificación de la contraseña de los parámetros de configuración de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:   

    int TestSafetyParamsCheckSum()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        int status = 0;
        uint32_t checksum = 0;
        rtn = robot.GetSafetyParamsCheckSum(status, checksum);
        printf("GetSafetyParamsCheckSum: error=%d, status=%d, hex_code=  0x%x  \n", rtn, status, checksum);
        robot.Sleep(3000);
        rtn = robot.SafetyOPPasswordCheck(0, "123");
        printf("SafetyOPPasswordCheck: error= %d\n", rtn);
        float level1[6] = { 2.0, 2.0, 2.0, 2.0, 2.0, 2.0 };
        rtn = robot.SetAnticollision(0, level1, 1);
        printf("SetAnticollision: error=%d\n", rtn);
        int safety[6] = { 10, 10, 10, 10, 10, 10 };
        rtn = robot.SetCollisionStrategy(0, 1000, 150, 0, safety);
        printf("SetCollisionStrategy rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.GetSafetyParamsCheckSum(status, checksum);
        printf("GetSafetyParamsCheckSum(again): error=%d, status=%d, hex_code=  0x%x  \n", rtn, status, checksum);
        robot.Sleep(2000);
        robot.CloseRPC();
        return 0;
    }
            
Establecer la ruta del certificado de cifrado TLS
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:   

    /**
    * @brief Establecer la ruta del certificado de cifrado TLS
    * @param [in] certPath  Ruta del certificado; si está vacío, por defecto es el certificado ubicado en el directorio del archivo ejecutable; nombres de certificado: ca.crt;client.crt;client.key
    * @return Código de error
    */
    errno_t MtlsLink(std::string certPath = "");
            
Ejemplo de código para establecer la ruta del certificado de cifrado TLS
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
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
        robot.MtlsLink("D://TLSCERTS/");
        robot.SetReConnectParam(true, 300000, 50);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }

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
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }