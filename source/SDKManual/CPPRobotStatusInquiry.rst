Consulta del estado del robot
==================================

.. toctree:: 
    :maxdepth: 5

Obtener la posición actual de las articulaciones (ángulo)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener la posición actual de las articulaciones (ángulo)
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] jPos Posición de las seis articulaciones, unidad deg
    * @return  Código de error
    */
    errno_t  GetActualJointPosDegree(uint8_t flag, JointPos *jPos);

Obtener la velocidad de retroalimentación de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener la velocidad de retroalimentación de las articulaciones-deg/s
     * @param  [in] flag 0-bloqueante, 1-no bloqueante
     * @param  [out] speed Velocidad de las seis articulaciones
     * @return  Código de error 
     */ 
    errno_t  GetActualJointSpeedsDegree(uint8_t flag, float speed[6]);

Obtener la aceleración de retroalimentación de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener la aceleración de retroalimentación de las articulaciones-deg/s^2
     * @param  [in] flag 0-bloqueante, 1-no bloqueante
     * @param  [out] acc Aceleración de las seis articulaciones
     * @return  Código de error 
     */ 
    errno_t  GetActualJointAccDegree(uint8_t flag, float acc[6]);   

Obtener la velocidad compuesta de comando del TCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener la velocidad compuesta de comando del TCP
     * @param  [in] flag 0-bloqueante, 1-no bloqueante
     * @param  [out] tcp_speed Velocidad lineal
     * @param  [out] ori_speed Velocidad de orientación
     * @return  Código de error 
     */
    errno_t  GetTargetTCPCompositeSpeed(uint8_t flag, float *tcp_speed, float *ori_speed);

Obtener la velocidad compuesta de retroalimentación del TCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener la velocidad compuesta de retroalimentación del TCP
     * @param  [in] flag 0-bloqueante, 1-no bloqueante
     * @param  [out] tcp_speed Velocidad lineal
     * @param  [out] ori_speed Velocidad de orientación
     * @return  Código de error 
     */ 
    errno_t  GetActualTCPCompositeSpeed(uint8_t flag, float *tcp_speed, float *ori_speed);

Obtener la velocidad de comando del TCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener la velocidad de comando del TCP
     * @param  [in] flag 0-bloqueante, 1-no bloqueante
     * @param  [out] speed Velocidad [x,y,z,rx,ry,rz]
     * @return  Código de error 
     */ 
    errno_t  GetTargetTCPSpeed(uint8_t flag, float speed[6]);

Obtener la velocidad de retroalimentación del TCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener la velocidad de retroalimentación del TCP
     * @param  [in] flag 0-bloqueante, 1-no bloqueante
     * @param  [out] speed Velocidad [x,y,z,rx,ry,rz]
     * @return  Código de error 
     */ 
    errno_t  GetActualTCPSpeed(uint8_t flag, float speed[6]);

Obtener la pose actual de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener la pose actual de la herramienta
    * @param  [in] flag  0-bloqueante, 1-no bloqueante
    * @param  [out] desc_pos  Pose de la herramienta
    * @return  Código de error
    */
    errno_t  GetActualTCPPose(uint8_t flag, DescPose *desc_pos);

Obtener el número del sistema de coordenadas de herramienta actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el número del sistema de coordenadas de herramienta actual
    * @param  [in] flag  0-bloqueante, 1-no bloqueante
    * @param  [out] id  Número del sistema de coordenadas de herramienta
    * @return  Código de error
    */
    errno_t  GetActualTCPNum(uint8_t flag, int *id);

Obtener el número del sistema de coordenadas de la pieza actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el número del sistema de coordenadas de la pieza actual
    * @param  [in] flag  0-bloqueante, 1-no bloqueante
    * @param  [out] id  Número del sistema de coordenadas de la pieza
    * @return  Código de error
    */
    errno_t  GetActualWObjNum(uint8_t flag, int *id);  

Obtener la pose actual de la brida del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener la pose actual de la brida del extremo
    * @param  [in] flag  0-bloqueante, 1-no bloqueante
    * @param  [out] desc_pos  Pose de la brida
    * @return  Código de error
    */
    errno_t  GetActualToolFlangePose(uint8_t flag, DescPose *desc_pos);  

Obtener el par actual de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el par actual de las articulaciones
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] torques Par de las articulaciones
    * @return  Código de error
    */
    errno_t  GetJointTorques(uint8_t flag, float torques[6]);

Obtener la hora del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener la hora del sistema
    * @param  [out] t_ms Unidad ms
    * @return  Código de error
    */
    errno_t  GetSystemClock(float *t_ms);

Sincronizar la hora del sistema con el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la hora actual del sistema del PC anfitrión y enviarla al robot, sincronizar la hora del sistema (debido a las limitaciones del sistema QNX, la precisión de sincronización es de nivel de minuto)
    * @return Código de error
    */
    errno_t SetRobotTime();

Ejemplo de código de configuración y lectura de la hora del sistema del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    void TestSetAndGetRobotTime() 
    {
    ROBOT_STATE_PKG pkg = {};
    FRRobot robot;
    robot.LoggerInit();
    robot.SetLoggerLevel(1);
    robot.SetReConnectParam(true, 30000, 500);
    int rtn = robot.RPC("192.168.58.2");
    if (rtn != 0) {
        return;
    }
    float t_ms = 0.0f;
    int ret = robot.GetSystemClock(&t_ms);
    if (ret == 0) {
        constexpr int64_t OFFSET_8H_MS = 8LL * 3600LL * 1000LL;
        int64_t rawMs = static_cast<int64_t>(t_ms);
        int64_t fixedMs = rawMs - OFFSET_8H_MS;
        std::time_t sec = static_cast<std::time_t>(fixedMs / 1000LL);
        std::tm utcTm {};
        #if defined (_WIN32) || defined (_WIN64)
            localtime_s(&utcTm, &sec);
        #else
            localtime_r(&sec, &utcTm);
        #endif
            char utcBuf[64] = { 0 };
            strftime(utcBuf, sizeof(utcBuf), "%Y-%m-%d %H:%M:%S", &utcTm);
            printf("system clock : %.0f\n", t_ms);
            printf("BEFORE UTC Time : %s\n", utcBuf);
        }
        else {
            printf("GetSystemClock failed, ret:%d\n", ret);
        }

        robot.SetRobotTime();
        robot.Sleep(1000);
        float t_ms_after = 0.0f;
        ret = robot.GetSystemClock(&t_ms_after);
        if (ret == 0) {
            printf("system clock : %.0f\n", t_ms_after);

            constexpr int64_t OFFSET_8H_MS = 8LL * 3600LL * 1000LL;
            int64_t robotMs = static_cast<int64_t>(t_ms_after);
            int64_t robotMsFixed = robotMs - OFFSET_8H_MS;

            auto nowSys = std::chrono::system_clock::now();
            int64_t pcMs = std::chrono::duration_cast<std::chrono::milliseconds>(nowSys.time_since_epoch()).count();
            constexpr int64_t MS_PER_MINUTE = 60LL * 1000LL;
            bool isConsistent = ((robotMsFixed / MS_PER_MINUTE) == (pcMs / MS_PER_MINUTE));

            std::time_t robotSec = robotMsFixed / 1000LL;
            std::tm robotTm {};
        #if defined (_WIN32) || defined (_WIN64)
            localtime_s(&robotTm, &robotSec);
        #else
            localtime_r(&robotSec, &robotTm);
        #endif

            std::time_t pcSec = pcMs / 1000LL;
            std::tm pcTm {};
        #if defined (_WIN32) || defined (_WIN64)
            localtime_s(&pcTm, &pcSec);
        #else
            localtime_r(&pcSec, &pcTm);
        #endif

        char pcBuf[64] = { 0 };
        char robotBuf[64] = { 0 };
        strftime(pcBuf, sizeof(pcBuf), "%Y-%m-%d %H:%M", &pcTm);
        strftime(robotBuf, sizeof(robotBuf), "%Y-%m-%d %H:%M", &robotTm);
        if (isConsistent) {
        printf("Consistent | PC time: %s | Robot time: %s\n", pcBuf, robotBuf);
        }
        else {
        printf("[Inconsistent] | PC time: %s | Robot time: %s\n", pcBuf, robotBuf);
        }
    }
    else {
        printf("GetSystemClock failed, ret:%d\n", ret);
    }
    robot.Sleep(1000);
    robot.CloseRPC();
    robot.Sleep(1000);
    }

Consultar si el movimiento del robot ha finalizado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Consultar si el movimiento del robot ha finalizado
    * @param  [out]  state  0-no finalizado, 1-finalizado
    * @return  Código de error
    */   
    errno_t  GetRobotMotionDone(uint8_t *state);

Consultar la longitud de la caché de la cola de movimiento del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Consultar la longitud de la caché de la cola de movimiento del robot
     * @param  [out]  len  Longitud de la caché
     * @return  Código de error
     */ 
    errno_t  GetMotionQueueLength(int *len);

Obtener el estado de parada de emergencia del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado de parada de emergencia del robot
    * @param [out] state Estado de parada de emergencia, 0-no parada de emergencia, 1-parada de emergencia
    * @return Código de error 
    */
    errno_t GetRobotEmergencyStopState(uint8_t *state);

Obtener el estado de comunicación entre el SDK y el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado de comunicación entre el SDK y el robot
    * @param [out] state Estado de comunicación, 0-comunicación normal, 1-comunicación anormal
    */
    errno_t GetSDKComState(int *state);

Obtener la señal de parada de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la señal de parada de seguridad
    * @param [out] si0_state Señal de parada de seguridad SI0, 0-inválida, 1-válida
    * @param [out] si1_state Señal de parada de seguridad SI1, 0-inválida, 1-válida
    */
    errno_t GetSafetyStopState(uint8_t *si0_state, uint8_t *si1_state);

Obtener la temperatura del controlador de las articulaciones del robot (℃)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la temperatura del controlador de las articulaciones del robot (℃)
    * @return Código de error
    */
    errno_t GetJointDriverTemperature(double temperature[]);

Obtener el par del controlador de las articulaciones del robot (Nm)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el par del controlador de las articulaciones del robot (Nm)
    * @return Código de error
    */
    errno_t GetJointDriverTorque(double torque[]);
        
Obtener la estructura del estado en tiempo real del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la estructura del estado en tiempo real del robot
    * @param [out] pkg Estructura del estado en tiempo real del robot
    * @return Código de error
    */
    errno_t GetRobotRealTimeState(ROBOT_STATE_PKG *pkg);

Ejemplo de código de consulta del estado del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos: 

    int TestGetStatus(void)
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
      float yangle, zangle;
      robot.GetRobotInstallAngle(&yangle, &zangle);
      printf("yangle:%f,zangle:%f\n", yangle, zangle);
      JointPos j_deg = {};
      robot.GetActualJointPosDegree(0, &j_deg);
      printf("joint pos deg:%f,%f,%f,%f,%f,%f\n", j_deg.jPos[0], j_deg.jPos[1], j_deg.jPos[2], j_deg.jPos[3], j_deg.jPos[4], j_deg.jPos[5]);
      float jointSpeed[6] = { 0.0 };
      robot.GetActualJointSpeedsDegree(0, jointSpeed);
      printf("joint speeds deg:%f,%f,%f,%f,%f,%f\n", jointSpeed[0], jointSpeed[1], jointSpeed[2], jointSpeed[3], jointSpeed[4], jointSpeed[5]);
      float jointAcc[6] = { 0.0 };
      robot.GetActualJointAccDegree(0, jointAcc);
      printf("joint acc deg:%f,%f,%f,%f,%f,%f\n", jointAcc[0], jointAcc[1], jointAcc[2], jointAcc[3], jointAcc[4], jointAcc[5]);
      float tcp_speed = 0.0;
      float ori_speed = 0.0;
      robot.GetTargetTCPCompositeSpeed(0, &tcp_speed, &ori_speed);
      printf("GetTargetTCPCompositeSpeed tcp %f; ori %f\n", tcp_speed, ori_speed);
      robot.GetActualTCPCompositeSpeed(0, &tcp_speed, &ori_speed);
      printf("GetActualTCPCompositeSpeed tcp %f; ori %f\n", tcp_speed, ori_speed);
      float targetSpeed[6] = { 0.0 };
      robot.GetTargetTCPSpeed(0, targetSpeed);
      printf("GetTargetTCPSpeed %f,%f,%f,%f,%f,%f\n", targetSpeed[0], targetSpeed[1], targetSpeed[2], targetSpeed[3], targetSpeed[4], targetSpeed[5]);
      float actualSpeed[6] = { 0.0 };
      robot.GetActualTCPSpeed(0, actualSpeed);
      printf("GetTargetTCPSpeed %f,%f,%f,%f,%f,%f\n", actualSpeed[0], actualSpeed[1], actualSpeed[2], actualSpeed[3], actualSpeed[4], actualSpeed[5]);
      DescPose tcp = {};
      robot.GetActualTCPPose(0, &tcp);
      printf("tcp pose:%f,%f,%f,%f,%f,%f\n", tcp.tran.x, tcp.tran.y, tcp.tran.z, tcp.rpy.rx, tcp.rpy.ry, tcp.rpy.rz);
      DescPose flange = {};
      robot.GetActualToolFlangePose(0, &flange);
      printf("flange pose:%f,%f,%f,%f,%f,%f\n", flange.tran.x, flange.tran.y, flange.tran.z, flange.rpy.rx, flange.rpy.ry, flange.rpy.rz);
      int id = 0;
      robot.GetActualTCPNum(0, &id);
      printf("tcp num:%d\n", id);
      robot.GetActualWObjNum(0, &id);
      printf("wobj num:%d\n", id);
      float jtorque[6] = { 0.0 };
      robot.GetJointTorques(0, jtorque);
      printf("torques:%f,%f,%f,%f,%f,%f\n", jtorque[0], jtorque[1], jtorque[2], jtorque[3], jtorque[4], jtorque[5]);
      float t_ms = 0.0;
      robot.GetSystemClock(&t_ms);
      printf("system clock:%f\n", t_ms);
      int config = 0;
      robot.GetRobotCurJointsConfig(&config);
      printf("joint config:%d\n", config);
      uint8_t motionDone = 0;
      robot.GetRobotMotionDone(&motionDone);
      printf("GetRobotMotionDone :%d\n", motionDone);
      int len = 0;
      robot.GetMotionQueueLength(&len);
      printf("GetMotionQueueLength :%d\n", len);
      uint8_t emergState = 0;
      robot.GetRobotEmergencyStopState(&emergState);
      printf("GetRobotEmergencyStopState :%d\n", emergState);
      int comstate = 0;
      robot.GetSDKComState(&comstate);
      printf("GetSDKComState :%d\n", comstate);
      uint8_t si0_state, si1_state;
      robot.GetSafetyStopState(&si0_state, &si1_state);
      printf("GetSafetyStopState :%d %d\n", si0_state, si1_state);
      double temp[6] = { 0.0 };
      robot.GetJointDriverTemperature(temp);
      printf("Temperature:%f,%f,%f,%f,%f,%f\n", temp[0], temp[1], temp[2], temp[3], temp[4], temp[5]);
      double torque[6] = { 0.0 };
      robot.GetJointDriverTorque(torque);
      printf("torque:%f,%f,%f,%f,%f,%f\n", torque[0], torque[1], torque[2], torque[3], torque[4], torque[5]);
      robot.GetRobotRealTimeState(&pkg);
      robot.CloseRPC();
      return 0;
    }

Solución de cinemática inversa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Solución de cinemática inversa
    * @param  [in] type 0-pose absoluta (sistema de coordenadas base), 1-pose incremental (sistema de coordenadas base), 2-pose incremental (sistema de coordenadas de herramienta)
    * @param  [in] desc_pos Pose cartesiana
    * @param  [in] config Configuración del espacio de articulaciones, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param  [out] joint_pos Posición de las articulaciones
    * @return  Código de error
    */
    errno_t  GetInverseKin(int type, DescPose *desc_pos, int config, JointPos *joint_pos);

Solución de cinemática inversa (posición de referencia)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Solución de cinemática inversa, resolver con referencia a la posición de articulaciones especificada
    * @param  [in] type 0-pose absoluta (sistema de coordenadas base), 1-pose incremental (sistema de coordenadas base), 2-pose incremental (sistema de coordenadas de herramienta)
    * @param  [in] desc_pos Pose cartesiana
    * @param  [in] joint_pos_ref Posición de articulaciones de referencia
    * @param  [out] joint_pos Posición de las articulaciones
    * @return  Código de error
    */   
    errno_t  GetInverseKinRef(int type, DescPose *desc_pos, JointPos *joint_pos_ref, JointPos *joint_pos);

Solución de cinemática inversa, el espacio cartesiano incluye la posición del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Solución de cinemática inversa, el espacio cartesiano incluye la posición del eje extendido
    * @param [in] type 0-pose absoluta (sistema de coordenadas base), 1-pose incremental (sistema de coordenadas base), 2-pose incremental (sistema de coordenadas de herramienta)
    * @param [in] desc_pos Pose cartesiana
    * @param [in] exaxis Posición del eje extendido
    * @param [in] tool Número de herramienta
    * @param [in] workPiece Número de pieza
    * @param [out] joint_pos Posición de las articulaciones
    * @param [in] config Configuración del espacio de articulaciones, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return Código de error
    */
    errno_t GetInverseKinExaxis(int type, DescPose desc_pos, ExaxisPos exaxis, int tool, int workPiece, JointPos& joint_pos, int config = -1);

Ejemplo de código de solución de cinemática inversa con posición del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestInverseKinExaxis()
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
        DescPose desc(99.957, -0.002, 29.994, -176.569, -6.757, -167.462);
        ExaxisPos exaxis(100.0, 0.0, 0.0, 0.0);
        JointPos jointPos = {};
        DescPose offsetPos = {};
        robot.GetRobotRealTimeState(&pkg);
        int toolnum = pkg.tool;
        int workPcsNum = pkg.user;
        robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum, jointPos);
        printf("GetInverseKinExaxis joint is %f, %f, %f, %f, %f, %f\n", jointPos.jPos[0], jointPos.jPos[1], jointPos.jPos[2], jointPos.jPos[3], jointPos.jPos[4], jointPos.jPos[5]);
        robot.ExtAxisMove(exaxis, 100, -1);
        robot.MoveJ(&jointPos, &desc, toolnum, workPcsNum, 100.0, 100.0, 100.0, &exaxis, -1, 0, &offsetPos);
        robot.CloseRPC();
        robot.Sleep(9999999);
        return 0;
    }

Obtener si la cinemática inversa tiene solución
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Solución de cinemática inversa, determinar con referencia a la posición de articulaciones especificada si tiene solución
    * @param  [in] type 0-pose absoluta (sistema de coordenadas base), 1-pose incremental (sistema de coordenadas base), 2-pose incremental (sistema de coordenadas de herramienta)
    * @param  [in] desc_pos Pose cartesiana
    * @param  [in] joint_pos_ref Posición de articulaciones de referencia
    * @param  [out] result 0-sin solución, 1-con solución
    * @return  Código de error
    */   
    errno_t  GetInverseKinHasSolution(int type, DescPose *desc_pos, JointPos *joint_pos_ref, uint8_t *result);

Obtener las 8 soluciones de cinemática inversa del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener las 8 soluciones de cinemática inversa del robot
    * @param [in] tcfPose Pose cartesiana
    * @param [in] tool Sistema de coordenadas de herramienta
    * @param [in] workpiece Sistema de coordenadas de la pieza
    * @param [in] exPos Posición del eje extendido
    * @param [out] jointPos Salida de las 8 soluciones de ángulos de articulaciones
    * @return Código de error
    */
    errno_t TCFToAllJoint(DescPose tcfPose, int tool, int workpiece, ExaxisPos exPos, std::vector<JointPos>& jointPos);

Ejemplo de código para obtener las 8 soluciones de cinemática inversa del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestTCFToAllJoint()
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
        DescPose curTcp(0, 0, 0, 0, 0, 0);
        rtn = robot.GetActualTCPPose(1, &curTcp);
        if (rtn != 0)
        {
            return rtn;
        }
        std::cout << std::fixed << std::setprecision(3);
        std::cout << "cur TCF: x=" << curTcp.tran.x << ", y=" << curTcp.tran.y << ", z=" << curTcp.tran.z << ", "
            << "a=" << curTcp.rpy.rx << ", b=" << curTcp.rpy.ry << ", c=" << curTcp.rpy.rz << std::endl;
        ExaxisPos exPos(0, 0, 0, 0);
        std::vector<JointPos> allJoints(8, JointPos(0, 0, 0, 0, 0, 0));
        rtn = robot.TCFToAllJoint(curTcp, 0, 0, exPos, allJoints);
        if (rtn != 0)
        {
            return rtn;
        }
        for (int i = 0; i < 8; i++)
        {
            JointPos joint = allJoints[i];
            std::cout << "JOINT" << (i + 1) << ": "
                << "j1=" << joint.jPos[0] << ", j2=" << joint.jPos[1] << ", j3=" << joint.jPos[2] << ", "
                << "j4=" << joint.jPos[3] << ", j5=" << joint.jPos[4] << ", j6=" << joint.jPos[5] << std::endl;
            DescPose pos(0, 0, 0, 0, 0, 0);
            rtn = robot.GetForwardKin(&joint, &pos);
            if (rtn != 0)
            {
                continue;
            }
            std::cout << "POS" << (i + 1) << ": "
                << "x=" << pos.tran.x << ", y=" << pos.tran.y << ", z=" << pos.tran.z << ", "
                << "a=" << pos.rpy.rx << ", b=" << pos.rpy.ry << ", c=" << pos.rpy.rz << std::endl;
        }
        return 0;
    }

Solución de cinemática directa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Solución de cinemática directa
    * @param  [in] joint_pos Posición de las articulaciones
    * @param  [out] desc_pos Pose cartesiana
    * @return  Código de error
    */
    errno_t  GetForwardKin(JointPos *joint_pos, DescPose *desc_pos);

Ejemplo de código de cálculo de cinemática directa e inversa del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestInverseKin(void)
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
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      JointPos inverseRtn = {};
      robot.GetInverseKin(0, &desc_pos1, -1, &inverseRtn);
      printf("dcs1 GetInverseKin rtn is %f %f %f %f %f %f \n", inverseRtn.jPos[0], inverseRtn.jPos[1], inverseRtn.jPos[2], inverseRtn.jPos[3], inverseRtn.jPos[4], inverseRtn.jPos[5]);
      robot.GetInverseKinRef(0, &desc_pos1, &j1, &inverseRtn);
      printf("dcs1 GetInverseKinRef rtn is %f %f %f %f %f %f \n", inverseRtn.jPos[0], inverseRtn.jPos[1], inverseRtn.jPos[2], inverseRtn.jPos[3], inverseRtn.jPos[4], inverseRtn.jPos[5]);
      uint8_t hasResut = 0;
      robot.GetInverseKinHasSolution(0, &desc_pos1, &j1, &hasResut);
      printf("dcs1 GetInverseKinRef result %d\n", hasResut);
      DescPose forwordResult = {};
      robot.GetForwardKin(&j1, &forwordResult);
      printf("jpos1 forwordResult rtn is %f %f %f %f %f %f \n", forwordResult.tran.x, forwordResult.tran.y, forwordResult.tran.z, forwordResult.rpy.rx, forwordResult.rpy.ry, forwordResult.rpy.rz);
      robot.CloseRPC();
      return 0;
    }

Consultar los datos de los puntos de enseñanza del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Consultar los datos de los puntos de enseñanza del robot
     * @param  [in]  name  Nombre del punto
     * @param  [out]  data   Datos del punto
     * @return  Código de error
     */ 
    errno_t  GetRobotTeachingPoint(char name[64], float data[20]);

Obtener el valor de compensación de los parámetros DH del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el valor de compensación de los parámetros DH del robot
    * @param [out] dhCompensation Valor de compensación de los parámetros DH del robot (mm) [cmpstD1,cmpstA2,cmpstA3,cmpstD4,cmpstD5,cmpstD6]
    * @return Código de error
    */
    errno_t GetDHCompensation(double dhCompensation[6]);

Obtener el código SN de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el código SN de la caja de control
    * @param [out] SNCode Código SN de la caja de control
    * @return Código de error
    */
    errno_t GetRobotSN(std::string& SNCode);

Ejemplo de código de consulta de los datos de los puntos de enseñanza del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetTeachPoint(void)
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
      char name[64] = "P1";
      float data[20] = { 0 };
      rtn = robot.GetRobotTeachingPoint(name, data);
      printf(" %d name is: %s \n", rtn, name);
      for (int i = 0; i < 20; i++)
      {
        printf("data is: %f \n", data[i]);
      }
      int que_len = 0;
      rtn = robot.GetMotionQueueLength(&que_len);
      printf("GetMotionQueueLength rtn is: %d, queue length is: %d \n", rtn, que_len);
      double dh[6] = { 0 };
      int retval = 0;
      retval = robot.GetDHCompensation(dh);
      cout << "retval is: " << retval << endl;
      cout << "dh is: " << dh[0] << " " << dh[1] << " " << dh[2] << " " << dh[3] << " " << dh[4] << " " << dh[5] << endl;
      string SN = "";
      robot.GetRobotSN(SN);
      cout << "robot SN is " << SN << endl;
      robot.CloseRPC();
      return 0;
    }

Obtener el sistema de coordenadas de herramienta según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas de herramienta según el número
    * @param [in] id Número del sistema de coordenadas de herramienta
    * @param [out] coord Valor del sistema de coordenadas
    * @param [out] type Tipo de herramienta 0-herramienta; 1-sensor
    * @param [out] install Posición de instalación 0-extremo del robot; 1-exterior del robot
    * @param [out] toolID ID de la herramienta 
    * @param [out] loadNo Número de carga
    * @return Código de error
    */
    errno_t GetToolCoordWithID(int id, DescPose& coord, int& type, int& install, int& toolID, int& loadNo);

Obtener el sistema de coordenadas de la pieza según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas de la pieza según el número
    * @param [in] id Número del sistema de coordenadas de la pieza
    * @param [out] coord Valor del sistema de coordenadas
    * @param [out] refFrame Sistema de coordenadas de referencia
    * @return Código de error
    */
    errno_t GetWObjCoordWithID(int id, DescPose& coord, int& refFrame);
    
Obtener el sistema de coordenadas de herramienta externa según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas de herramienta externa según el número
    * @param [in] id Número del sistema de coordenadas de herramienta externa, 20-39 corresponden a los sistemas de coordenadas de herramienta externa 0-19
    * @param [out] coord Pose del TCP de la herramienta fija externa del robot
    * @param [out] tcoord Pose del sistema de coordenadas de la pieza instalada en el extremo del robot
    * @return Código de error
    */
    errno_t GetExToolCoordWithID(int id, DescPose& coord, DescPose& tcoord);
    
Obtener el sistema de coordenadas del eje extendido según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas del eje extendido según el número
    * @param [in] id Número del sistema de coordenadas de herramienta externa
    * @param [out] coord Valor del sistema de coordenadas
    * @param [out] axisCoordNum Número del eje extendido; bit0-bit3 corresponden al eje extendido 1-eje extendido 4; si el valor de axisCoordNum es 3, corresponde a la aplicación del eje extendido [1, 2]
    * @param [out] calibFlag Indicador de calibración; 0-no calibrado; 1-calibrado
    * @return Código de error
    */
    errno_t GetExAxisCoordWithID(int id, DescPose& coord, int& axisCoordNum, int& calibFlag);

Obtener la masa y el centro de masa de la carga según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la masa y el centro de masa de la carga según el número
    * @param [in] id Número de carga
    * @param [out] weight Masa de la carga
    * @param [out] cog Centro de masa de la carga
    * @return Código de error
    */
    errno_t GetTargetPayloadWithID(int id, double& weight, DescTran& cog);
    
Obtener el sistema de coordenadas de herramienta actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:
    
    /**
    * @brief Obtener el sistema de coordenadas de herramienta actual
    * @param [out] coord Valor del sistema de coordenadas
    * @return Código de error
    */
    errno_t GetCurToolCoord(DescPose& coord);
        
Obtener el sistema de coordenadas de la pieza actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas de la pieza actual
    * @param [out] coord Valor del sistema de coordenadas
    * @return Código de error
    */
    errno_t GetCurWObjCoord(DescPose& coord);
            
Obtener el sistema de coordenadas de herramienta externa actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas de herramienta externa actual
    * @param [out] coord Valor del sistema de coordenadas
    * @return Código de error
    */
    errno_t GetCurExToolCoord(DescPose& coord);
                
Obtener el sistema de coordenadas del eje extendido actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas del eje extendido actual
    * @param [out] coord Valor del sistema de coordenadas
    * @return Código de error
    */
    errno_t GetCurExAxisCoord(DescPose& coord);

Ejemplo de código para obtener los sistemas de coordenadas y la carga del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    int TestCoord()
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
        robot.Sleep(2000);
        int id = 1;
        DescPose toolCoord = {};
        DescPose extoolCoord = {};
        DescPose exworkpieceCoord = {};
        DescPose wobjCoord = {};
        DescPose exAxisCoord = {};
        int type = 0, install = 0, toolID = 0, loadNo = 0;
        robot.GetToolCoordWithID(id, toolCoord, type, install, toolID, loadNo);
        printf("GetToolCoordWithID %d, %f %f %f %f %f %f,  type = %d, install = %d, toolID = %d, loadNo = %d\n", id,
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz, type, install, toolID, loadNo);
        int refFrame = 0;
        robot.GetWObjCoordWithID(id, wobjCoord, refFrame);
        printf("GetWObjCoordWithID %d, %f %f %f %f %f %f, refFrame = %d\n", id,
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz, refFrame);
        robot.GetExToolCoordWithID(21, extoolCoord, exworkpieceCoord);
        printf("GetExToolCoordWithID %d, %f %f %f %f %f %f\n", id,
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz,
            exworkpieceCoord.tran.x, exworkpieceCoord.tran.y, exworkpieceCoord.tran.z,
            exworkpieceCoord.rpy.rx, exworkpieceCoord.rpy.ry, exworkpieceCoord.rpy.rz);
        int axisCoordNum = 0, calibFlag = 0;
        robot.GetExAxisCoordWithID(id, exAxisCoord, axisCoordNum, calibFlag);
        printf("GetExAxisCoordWithID %d, %f %f %f %f %f %f, axisCoordNum = %d, calibFlag = %d\n", id,
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz, axisCoordNum, calibFlag);
        double weight = 0.0;
        DescTran cog = {};
        robot.GetTargetPayloadWithID(id, weight, cog);
        printf("GetTargetPayloadWithID %d, %f %f %f %f\n", id, weight,
            cog.x, cog.y, cog.z);
        robot.GetCurToolCoord(toolCoord);
        printf("GetCurToolCoord %f %f %f %f %f %f\n",
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz);
        robot.GetCurWObjCoord(wobjCoord);
        printf("GetCurWObjCoord %f %f %f %f %f %f\n",
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz);
        robot.GetCurExToolCoord(extoolCoord);
        printf("GetExToolCoordWithID %f %f %f %f %f %f\n",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);
        robot.GetCurExAxisCoord(exAxisCoord);
        printf("GetCurExAxisCoord %f %f %f %f %f %f\n",
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz);
        float weightT = 0.0;
        DescTran cogT = {};
        robot.GetTargetPayload(0, &weightT);
        robot.GetTargetPayloadCog(0, &cogT);
        printf("GetTargetPayload %f %f %f %f\n", weightT,
            cogT.x, cogT.y, cogT.z);
        DescPose coordSet(0, 1, 2, 3, 4, 5);
        robot.SetToolCoord(1, &coordSet, 0, 0, 1, 0);
        robot.SetWObjCoord(1, &coordSet, 0);
        robot.SetLoadWeight(1, 1.3);
        //DescTran cog = {};
        cog.x = 10;
        cog.y = 20;
        cog.z = 30;
        robot.SetLoadCoord(1, &cog);
        DescPose etcp(0, 0, 100, 0, 0, 0);
        DescPose etool(0, 0, 50, 0, 0, 0);
        rtn = robot.SetExToolCoord(21, &etcp, &etool);
        printf("SetExToolCoord rtn is %d\n", rtn);
        robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1);
        robot.CloseRPC();
        return 0;
    }