Consulta del estado del robot
====================================

.. toctree:: 
    :maxdepth: 5

Obtener la posición actual de las articulaciones (ángulos)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la posición actual de las articulaciones (ángulos)
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] jPos Posición de las seis articulaciones, unidad deg
    * @return  Código de error
    */
    int GetActualJointPosDegree(byte flag, ref JointPos jPos); 

Obtener la posición actual de las articulaciones (radianes)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la posición actual de las articulaciones (radianes)
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] jPos Posición de las seis articulaciones, unidad rad
    * @return  Código de error
    */   
    int GetActualJointPosRadian(byte flag, ref JointPos jPos);

Obtener la velocidad de retroalimentación de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la velocidad de retroalimentación de las articulaciones - deg/s 
    * @param [in] flag 0-bloqueante, 1-no bloqueante 
    * @param [out] speed Velocidad de las seis articulaciones 
    * @return Código de error 
    */
    int GetActualJointSpeedsDegree(byte flag, ref double[] speed);

Obtener la aceleración de retroalimentación de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la aceleración de retroalimentación de las articulaciones - deg/s^2 
    * @param [in] flag 0-bloqueante, 1-no bloqueante 
    * @param [out] acc Aceleración de las seis articulaciones 
    * @return Código de error 
    */
    int GetActualJointAccDegree(byte flag, ref double[] acc); 

Obtener la velocidad de instrucción TCP - velocidad compuesta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la velocidad de instrucción TCP - velocidad compuesta 
    * @param [in] flag 0-bloqueante, 1-no bloqueante 
    * @param [out] tcp_speed Velocidad lineal 
    * @param [out] ori_speed Velocidad de orientación 
    * @return Código de error 
    */
    int GetTargetTCPCompositeSpeed(byte flag, ref double tcp_speed, ref double ori_speed); 

Obtener la velocidad de retroalimentación TCP - velocidad compuesta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
    
    /** 
    * @brief Obtener la velocidad de retroalimentación TCP - velocidad compuesta
    * @param [in] flag 0-bloqueante, 1-no bloqueante 
    * @param [out] tcp_speed Velocidad lineal 
    * @param [out] ori_speed Velocidad de orientación 
    * @return Código de error 
    */
    int GetActualTCPCompositeSpeed(byte flag, ref double tcp_speed, ref double ori_speed);

Obtener la velocidad de instrucción TCP - velocidades por componente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la velocidad de instrucción TCP - velocidades por componente
    * @param [in] flag 0-bloqueante, 1-no bloqueante 
    * @param [out] speed Velocidad [x,y,z,rx,ry,rz] 
    * @return Código de error 
    */
    int GetTargetTCPSpeed(byte flag, ref double[] speed);

Obtener la velocidad de retroalimentación TCP - velocidades por componente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la velocidad de retroalimentación TCP - velocidades por componente
    * @param [in] flag 0-bloqueante, 1-no bloqueante 
    * @param [out] speed Velocidad [x,y,z,rx,ry,rz] 
    * @return Código de error 
    */
    int GetActualTCPSpeed(byte flag, ref double[] speed);

Obtener la pose actual de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la pose actual de la herramienta
    * @param  [in] flag  0-bloqueante, 1-no bloqueante
    * @param  [out] desc_pos  Pose de la herramienta
    * @return  Código de error
    */
    int GetActualTCPPose(byte flag, ref DescPose desc_pos); 

Obtener el número del sistema de coordenadas de herramienta actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el número del sistema de coordenadas de herramienta actual
    * @param  [in] flag  0-bloqueante, 1-no bloqueante
    * @param  [out] id  Número del sistema de coordenadas de herramienta
    * @return  Código de error
    */
    int GetActualTCPNum(byte flag, ref int id);  

Obtener el número del sistema de coordenadas de pieza actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el número del sistema de coordenadas de pieza actual
    * @param  [in] flag  0-bloqueante, 1-no bloqueante
    * @param  [out] id  Número del sistema de coordenadas de pieza
    * @return  Código de error
    */
    int GetActualWObjNum(byte flag, ref int id);

Obtener la pose actual de la brida del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la pose actual de la brida del extremo
    * @param  [in] flag  0-bloqueante, 1-no bloqueante
    * @param  [out] desc_pos  Pose de la brida
    * @return  Código de error
    */
    int GetActualToolFlangePose(byte flag, ref DescPose desc_pos);   

Obtener el par actual de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el par actual de las articulaciones
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] torques Par de las articulaciones
    * @return  Código de error
    */
    int GetJointTorques(byte flag, float[] torques); 

Obtener la hora del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la hora del sistema
    * @param  [out] t_ms Unidad ms, convertible según la hora UTC; en estado de fallo del robot, la obtención de CLock devuelve 0 y un código de error
    * @return  Código de error
    */
    public int GetSystemClock(ref double t_ms)

Sincronizar la hora del sistema con el robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la hora actual del sistema del PC superior y enviarla al robot para sincronizar la hora del sistema (debido a las limitaciones del sistema QNX, la precisión de sincronización es de nivel de minuto)
    * @return Código de error
    */
    public int SetRobottime()

Ejemplo de código de sincronización de la hora del sistema con el robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void testSetAndGetRobotTime()
    {
        double t_ms = 0.0;

        int ret = robot.GetSystemClock(ref t_ms);
        if (ret == 0)
        {
            Console.WriteLine($"system clock : {t_ms}");
            // Convertir la marca de tiempo en milisegundos a DateTime (hora UTC)
            DateTime utcTime = new DateTime(1970, 1, 1, 0, 0, 0, DateTimeKind.Utc).AddMilliseconds(t_ms);
            Console.WriteLine($"BEFORE UTC Time   : {utcTime:yyyy-MM-dd HH:mm:ss}");
        }
        else
        {
            Console.WriteLine($"GetSystemClock failed,ret:{ret}");
        }

        robot.SetRobottime();

        // Obtener la hora del robot tras la configuración
        double t_ms_after = 0;
        ret = robot.GetSystemClock(ref t_ms_after);
        if (ret == 0)
        {
            Console.WriteLine($"system clock : {t_ms}");
            DateTime robotTimeAfter = DateTimeOffset.FromUnixTimeMilliseconds((long)t_ms_after).UtcDateTime;

            // Obtener la hora del PC antes de la configuración (como valor esperado)
            DateTime pcTimeBefore = DateTime.Now;

            // Truncar tanto la hora esperada (hora del PC) como la hora del robot a minutos
            DateTime pcMinute = new DateTime(pcTimeBefore.Year, pcTimeBefore.Month, pcTimeBefore.Day,
                                                pcTimeBefore.Hour, pcTimeBefore.Minute, 0, DateTimeKind.Utc);
            DateTime robotMinute = new DateTime(robotTimeAfter.Year, robotTimeAfter.Month, robotTimeAfter.Day,
                                                robotTimeAfter.Hour, robotTimeAfter.Minute, 0, DateTimeKind.Utc);

            // Comparar la consistencia
            bool isConsistent = (pcMinute == robotMinute);
            if (isConsistent)
            {
                Console.WriteLine($"Consistent     | PC time: {pcMinute:yyyy-MM-dd HH:mm}  | Robot time: {robotMinute:yyyy-MM-dd HH:mm}");
            }
            else
            {
                Console.WriteLine($"[Inconsistent | PC time: {pcMinute:yyyy-MM-dd HH:mm}  | Robot time: {robotMinute:yyyy-MM-dd HH:mm}");
            }
        }
        else
        {
            Console.WriteLine($"GetSystemClock failed,ret:{ret}");
        }
    }

Consultar si el movimiento del robot ha finalizado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Consultar si el movimiento del robot ha finalizado
    * @param  [out]  state  0-no finalizado, 1-finalizado
    * @return  Código de error
    */   
    int GetRobotMotionDone(ref byte state);

Consultar la longitud de la cola de movimiento del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Consultar la longitud de la cola de movimiento del robot 
    * @param [out] len   Longitud de la cola
    * @return Código de error 
    */
    int GetMotionQueueLength(ref int len);

Obtener el estado de parada de emergencia del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado de parada de emergencia del robot
    * @param [out] state Estado de parada de emergencia, 0-sin parada de emergencia, 1-parada de emergencia
    * @return Código de error  
    */
    int GetRobotEmergencyStopState(ref byte state);

Obtener el estado de comunicación entre el SDK y el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado de comunicación entre el SDK y el robot
    * @param [out]  state Estado de comunicación, 0-comunicación normal, 1-comunicación anómala
    */
    int GetSDKComState(ref int state);

Obtener la señal de parada de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la señal de parada de seguridad
    * @param [out]  si0_state Señal de parada de seguridad SI0, 0-no válida, 1-válida
    * @param [out]  si1_state Señal de parada de seguridad SI1, 0-no válida, 1-válida
    */
    int GetSafetyStopState(ref byte si0_state, ref byte si1_state);

Obtener la temperatura del accionamiento de las articulaciones del robot (℃)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la temperatura del accionamiento de las articulaciones del robot (℃)
    * @return Código de error
    */
    int GetJointDriverTemperature(double[] temperature);

Obtener el par del accionamiento de las articulaciones del robot (Nm)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el par del accionamiento de las articulaciones del robot (Nm)
    * @return Código de error
    */
    int GetJointDriverTorque(double torque[]);

Obtener la última trama de datos de estado en tiempo real del robot (cambio del mecanismo interno)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la última trama de datos de estado en tiempo real del robot (el hilo interno se actualiza continuamente; esta interfaz devuelve directamente los datos en caché)
    * @param [out] pkg Parámetro de referencia, utilizado para recibir los datos de estado del robot (estructura ROBOT_STATE_PKG)
    * @return Devuelve 0 en caso de éxito; en caso de fallo devuelve un código de error negativo (por ejemplo, error de comunicación de red)
    */
    public int GetRobotRealTimeState(ref ROBOT_STATE_PKG pkg)

Ejemplo de código de consulta del estado del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button29_Click(object sender, EventArgs e)
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        double yangle = 0, zangle = 0;
        robot.GetRobotInstallAngle(ref yangle, ref zangle);
        Console.WriteLine($"yangle:{yangle},zangle:{zangle}");

        JointPos j_deg = new JointPos(0,0,0,0,0,0);
        robot.GetActualJointPosDegree(0, ref j_deg);
        Console.WriteLine($"joint pos deg:{j_deg.jPos[0]},{j_deg.jPos[1]},{j_deg.jPos[2]},{j_deg.jPos[3]},{j_deg.jPos[4]},{j_deg.jPos[5]}");

        double[] jointSpeed = new double[6];
        robot.GetActualJointSpeedsDegree(0, ref jointSpeed);
        Console.WriteLine($"joint speeds deg:{jointSpeed[0]},{jointSpeed[1]},{jointSpeed[2]},{jointSpeed[3]},{jointSpeed[4]},{jointSpeed[5]}");

        double[] jointAcc = new double[6];
        robot.GetActualJointAccDegree(0, ref jointAcc);
        Console.WriteLine($"joint acc deg:{jointAcc[0]},{jointAcc[1]},{jointAcc[2]},{jointAcc[3]},{jointAcc[4]},{jointAcc[5]}");

        double tcp_speed = 0, ori_speed = 0;
        robot.GetTargetTCPCompositeSpeed(0, ref tcp_speed, ref ori_speed);
        Console.WriteLine($"GetTargetTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}");

        robot.GetActualTCPCompositeSpeed(0, ref tcp_speed, ref ori_speed);
        Console.WriteLine($"GetActualTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}");

        double[] targetSpeed = new double[6];
        robot.GetTargetTCPSpeed(0,ref targetSpeed);
        Console.WriteLine($"GetTargetTCPSpeed {targetSpeed[0]},{targetSpeed[1]},{targetSpeed[2]},{targetSpeed[3]},{targetSpeed[4]},{targetSpeed[5]}");

        double[] actualSpeed = new double[6];
        robot.GetActualTCPSpeed(0, ref actualSpeed);
        Console.WriteLine($"GetTargetTCPSpeed {actualSpeed[0]},{actualSpeed[1]},{actualSpeed[2]},{actualSpeed[3]},{actualSpeed[4]},{actualSpeed[5]}");

        DescPose tcp = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetActualTCPPose(0, ref tcp);
        Console.WriteLine($"tcp pose:{tcp.tran.x},{tcp.tran.y},{tcp.tran.z},{tcp.rpy.rx},{tcp.rpy.ry},{tcp.rpy.rz}");

        DescPose flange = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetActualToolFlangePose(0, ref flange);
        Console.WriteLine($"flange pose:{flange.tran.x},{flange.tran.y},{flange.tran.z},{flange.rpy.rx},{flange.rpy.ry},{flange.rpy.rz}");

        int id = 0;
        robot.GetActualTCPNum(0, ref id);
        Console.WriteLine($"tcp num:{id}");

        robot.GetActualWObjNum(0, ref id);
        Console.WriteLine($"wobj num:{id}");

        double[] jtorque = new double[6];
        robot.GetJointTorques(0, jtorque);
        Console.WriteLine($"torques:{jtorque[0]},{jtorque[1]},{jtorque[2]},{jtorque[3]},{jtorque[4]},{jtorque[5]}");

        double t_ms = 0;
        robot.GetSystemClock(ref t_ms);
        Console.WriteLine($"system clock:{t_ms}");

        int config = 0;
        robot.GetRobotCurJointsConfig(ref config);
        Console.WriteLine($"joint config:{config}");

        byte motionDone = 0;
        robot.GetRobotMotionDone(ref motionDone);
        Console.WriteLine($"GetRobotMotionDone :{motionDone}");

        int len = 0;
        robot.GetMotionQueueLength(ref len);
        Console.WriteLine($"GetMotionQueueLength :{len}");

        byte emergState = 0;
        robot.GetRobotEmergencyStopState(ref emergState);
        Console.WriteLine($"GetRobotEmergencyStopState :{emergState}");

        int comstate = 0;
        robot.GetSDKComState(ref comstate);
        Console.WriteLine($"GetSDKComState :{comstate}");

        byte si0_state = 0, si1_state = 0;
        robot.GetSafetyStopState(ref si0_state, ref si1_state);
        Console.WriteLine($"GetSafetyStopState :{si0_state} {si1_state}");

        double[] temp = new double[6];
        robot.GetJointDriverTemperature(temp);
        Console.WriteLine($"Temperature:{temp[0]},{temp[1]},{temp[2]},{temp[3]},{temp[4]},{temp[5]}");

        double[] torque = new double[6];
        robot.GetJointDriverTorque(torque);
        Console.WriteLine($"torque:{torque[0]},{torque[1]},{torque[2]},{torque[3]},{torque[4]},{torque[5]}");

        robot.GetRobotRealTimeState(ref pkg);
    }

Resolución de cinemática inversa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Resolución de cinemática inversa
    * @param  [in] type 0-pose absoluta (sistema de coordenadas base), 1-pose incremental (sistema de coordenadas base), 2-pose incremental (sistema de coordenadas de herramienta)
    * @param  [in] desc_pos Pose cartesiana
    * @param  [in] config Configuración del espacio de articulaciones, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param  [out] joint_pos Posición de las articulaciones
    * @return  Código de error
    */ 
    int GetInverseKin(int type, DescPose desc_pos, int config, ref JointPos joint_pos);

Resolución de cinemática inversa (posición de referencia)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Resolución de cinemática inversa, con referencia a la posición articular especificada para determinar si tiene solución
    * @param  [in] type 0-pose absoluta (sistema de coordenadas base), 1-pose incremental (sistema de coordenadas base), 2-pose incremental (sistema de coordenadas de herramienta)
    * @param  [in] desc_pos Pose cartesiana
    * @param  [in] joint_pos_ref Posición articular de referencia
    * @param  [out] result 0-sin solución, 1-con solución
    * @return  Código de error
    */   
    int GetInverseKinRef(int posMode, DescPose desc_pos, JointPos joint_pos_ref, ref JointPos joint_pos); 

Resolución de cinemática inversa con posición del eje extendido en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Resolución de cinemática inversa con posición del eje extendido en el espacio cartesiano
    * @param [in] type 0-pose absoluta (sistema de coordenadas base), 1-pose incremental (sistema de coordenadas base), 2-pose incremental (sistema de coordenadas de herramienta)
    * @param [in] desc_pos Pose cartesiana
    * @param [in] exaxis Posición del eje extendido
    * @param [in] tool Número de herramienta
    * @param [in] workPiece Número de pieza
    * @param [out] joint_pos Posición de las articulaciones
    * @param [in] config -1: resolución automática; 0-7 corresponden a ocho grupos de soluciones
    * @return Código de error
    */
    public int GetInverseKinExaxis(int type, DescPose desc_pos, ExaxisPos exaxis, int tool, int workPiece, ref JointPos joint_pos, int config = -1);

Ejemplo de código de resolución de cinemática inversa con posición del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestInverseKinExaxis()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        robot.GetRobotRealTimeState(ref pkg);
        int toolnum = pkg.tool;
        int workPcsNum = pkg.user;

        DescPose desc = new DescPose(-547.469, -47.361, 184.149, 169.843, 4.579, 82.557);
        ExaxisPos exaxis = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        JointPos jointPos = new JointPos(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);

        robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum, ref jointPos, 0);
        Console.WriteLine($"GetInverseKinExaxis joint is {jointPos.jPos[0]}, {jointPos.jPos[1]}, {jointPos.jPos[2]}, {jointPos.jPos[3]}, {jointPos.jPos[4]}, {jointPos.jPos[5]}");
    }

Obtener si la cinemática inversa tiene solución
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Resolución de cinemática inversa, determina si la posición articular de referencia especificada tiene solución
    * @param [in] posMode 0-pose absoluta, 1-pose relativa al sistema de coordenadas base, 2-pose relativa al sistema de coordenadas de herramienta 
    * @param [in] desc_pos Pose cartesiana 
    * @param [in] joint_pos_ref Posición articular de referencia 
    * @param [out] hasResult 0-sin solución, 1-con solución 
    * @return Código de error 
    */ 
    int GetInverseKinHasSolution(int posMode, DescPose desc_pos, JointPos joint_pos_ref, ref bool hasResult);  

Obtener las 8 soluciones de cinemática inversa del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener las 8 soluciones de cinemática inversa
    * @param [in] tcp_pose Pose cartesiana 
    * @param [in] tool Sistema de coordenadas de herramienta
    * @param [in] workpiece Sistema de coordenadas de pieza
    * @param [in] exPos Posición del eje extendido
    * @param [out] jPos Devuelve 8 grupos de ángulos articulares
    * @return Código de error
    */
    public int TCFToAllJoint( DescPose tcp_pose, int tool, int workpiece, ExaxisPos exPos , ref JointPos[] jPos)

Ejemplo de código de obtención de las 8 soluciones de cinemática inversa del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int TestTCFToAllJoint()
    {
        // Obtener la pose TCP actual
        DescPose curTcp = new DescPose(0, 0, 0, 0, 0, 0);
        int rtn = robot.GetActualTCPPose(1, ref curTcp);
        if (rtn != 0)
        {
            return rtn;
        }
        Console.WriteLine($"当前TCP位姿: x={curTcp.tran.x:F3}, y={curTcp.tran.y:F3}, z={curTcp.tran.z:F3}, " +
                            $"a={curTcp.rpy.rx:F3}, b={curTcp.rpy.ry:F3}, c={curTcp.rpy.rz:F3}");

        // Posición del eje extendido, todos ceros aquí
        ExaxisPos exPos = new ExaxisPos(0, 0, 0, 0);

        // 8 grupos de resultados de cinemática inversa
        JointPos[] allJoints = new JointPos[8];
        for (int i = 0; i < 8; i++)
        {
            allJoints[i] = new JointPos(0, 0, 0, 0, 0, 0);
        }

        // Llamar a TCFToAllJoint para obtener 8 grupos de soluciones inversas, tool=0, workpiece=0
        rtn = robot.TCFToAllJoint(curTcp, 0, 0, exPos, ref allJoints);
        if (rtn != 0)
        {
            return rtn;
        }

        // Verificar cada solución mediante cinemática directa
        for (int i = 0; i < 8; i++)
        {
            JointPos joint = allJoints[i];

            Console.WriteLine($"JOINT{i + 1}: " +
                                $"j1={joint.jPos[0]:F3}, j2={joint.jPos[1]:F3}, j3={joint.jPos[2]:F3}, " +
                                $"j4={joint.jPos[3]:F3}, j5={joint.jPos[4]:F3}, j6={joint.jPos[5]:F3}");

            // Pose cartesiana correspondiente a la i-ésima solución inversa
            DescPose pos = new DescPose(0, 0, 0, 0, 0, 0);
            rtn = robot.GetForwardKin(joint, ref pos);
            if (rtn != 0)
            {
                // El fallo de un grupo no afecta a los demás
                continue;
            }

            Console.WriteLine($"POS{i + 1}: " +
                                $"x={pos.tran.x:F3}, y={pos.tran.y:F3}, z={pos.tran.z:F3}, " +
                                $"a={pos.rpy.rx:F3}, b={pos.rpy.ry:F3}, c={pos.rpy.rz:F3}");
        }

        return 0;
    }

Resolución de cinemática directa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Resolución de cinemática directa
    * @param  [in] joint_pos Posición de las articulaciones
    * @param  [out] desc_pos Pose cartesiana
    * @return  Código de error
    */
    int GetForwardKin(JointPos joint_pos, ref DescPose desc_pos); 

Ejemplo de código de cálculo de cinemática directa e inversa del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button30_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        DescPose desc_pos1 = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);

        JointPos inverseRtn = new JointPos(0, 0, 0, 0, 0, 0);

        robot.GetInverseKin(0, desc_pos1, -1, ref inverseRtn);
        Console.WriteLine($"dcs1 GetInverseKin rtn is {inverseRtn.jPos[0]} {inverseRtn.jPos[1]} {inverseRtn.jPos[2]} {inverseRtn.jPos[3]} {inverseRtn.jPos[4]} {inverseRtn.jPos[5]}");
        robot.GetInverseKinRef(0,  desc_pos1, j1, ref inverseRtn);
        Console.WriteLine($"dcs1 GetInverseKinRef rtn is {inverseRtn.jPos[0]} {inverseRtn.jPos[1]} {inverseRtn.jPos[2]} {inverseRtn.jPos[3]} {inverseRtn.jPos[4]} {inverseRtn.jPos[5]}");

        bool hasResut = false;
        robot.GetInverseKinHasSolution(0,  desc_pos1,  j1, ref hasResut);
        Console.WriteLine($"dcs1 GetInverseKinRef result {hasResut}");

        DescPose forwordResult = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetForwardKin(j1, ref forwordResult);
        Console.WriteLine($"jpos1 forwordResult rtn is {forwordResult.tran.x} {forwordResult.tran.y} {forwordResult.tran.z} {forwordResult.rpy.rx} {forwordResult.rpy.ry} {forwordResult.rpy.rz}");
    }

Consultar los datos de los puntos de gestión de enseñanza del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Consultar los datos de los puntos de gestión de enseñanza del robot 
    * @param [in] name    Nombre del punto
    * @param [out] data   Datos del punto double[20]{x,y,z,rx,ry,rz,j1,j2,j3,j4,j5,j6,tool, wobj,speed,acc,e1,e2,e3,e4}
    * @return Código de error 
    */ 
    int GetRobotTeachingPoint(string name, ref double[] data); 

Obtener los valores de compensación de los parámetros DH del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener los valores de compensación de los parámetros DH del robot 
    * @param [out] dhCompensation Valores de compensación de los parámetros DH del robot (mm) [cmpstD1,cmpstA2,cmpstA3,cmpstD4,cmpstD5,cmpstD6]
    * @return Código de error 
    */
    int GetDHCompensation(ref double[] dhCompensation);


Obtener el código SN del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el código SN del armario de control
    * @param [out] SNCode Código SN del armario de control
    * @return Código de error
    */
    int GetRobotSN(ref string SNCode);

Ejemplo de código de consulta de los datos de los puntos de gestión de enseñanza del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button31_Click(object sender, EventArgs e)
    {
        string name = "A0";
        double[] data = new double[20];
        int rtn = robot.GetRobotTeachingPoint(name, ref data);
        Console.WriteLine(" {0} name is: {1} \n", rtn, name);
        for (int i = 0; i < 20; i++)
        {
            Console.WriteLine("data is: {0} \n", data[i]);
        }

        int que_len = 0;
        rtn = robot.GetMotionQueueLength(ref que_len);
        Console.WriteLine("GetMotionQueueLength rtn is: {0}, queue length is: {1} \n", rtn, que_len);

        double[] dh = { 0, 0, 0, 0, 0, 0 };
        int retval = 0;
        retval = robot.GetDHCompensation(ref dh);
        Console.WriteLine($"retval is  {retval}");
        Console.WriteLine($"dh is {dh[0]}, {dh[1]}, {dh[2]}, {dh[3]}, {dh[4]}, {dh[5]}");
        string SN = "";
        robot.GetRobotSN(ref SN);
        Console.WriteLine($"robot SN is  {SN}");
    }

Obtener el sistema de coordenadas de herramienta según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
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
    int GetToolCoordWithID(int id, ref DescPose coord, ref int type, ref int install, ref int toolID, ref int loadNo)

Obtener el sistema de coordenadas de pieza según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas de pieza según el número
    * @param [in] id Número del sistema de coordenadas de pieza
    * @param [out] coord Valor del sistema de coordenadas
    * @param [out] refFrame Sistema de coordenadas de referencia
    * @return Código de error
    */
    public int GetWObjCoordWithID(int id, ref DescPose coord, ref int refFrame)

Obtener el sistema de coordenadas de herramienta externa según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas de herramienta externa según el número
    * @param [in] id Número del sistema de coordenadas de herramienta externa; 20-39 corresponden al sistema de coordenadas de herramienta externa 0-19
    * @param [out] coord Pose TCP de la herramienta fija externa del robot
    * @param [out] tcoord Pose del sistema de coordenadas de pieza instalado en el extremo del robot
    * @return Código de error
    */
    public int GetExToolCoordWithID(int id, ref DescPose coord, ref DescPose tcoord)

Obtener el sistema de coordenadas del eje extendido según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas del eje extendido según el número
    * @param [in] id Número del sistema de coordenadas de herramienta externa
    * @param [out] coord Valor del sistema de coordenadas
    * @param [out] axisCoordNum Número del eje extendido; bit0-bit3 corresponden a los ejes extendidos 1-4; por ejemplo, si el valor de axisCoordNum es 3, corresponde a la aplicación de los ejes extendidos [1, 2]
    * @param [out] calibFlag Indicador de calibración; 0-no calibrado; 1-calibrado
    * @return Código de error
    */
    public int GetExAxisCoordWithID(int id, ref DescPose coord, ref int axisCoordNum, ref int calibFlag)

Obtener el sistema de coordenadas de herramienta actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Obtener el sistema de coordenadas de herramienta actual
     * @param [out] coord Valor del sistema de coordenadas
     * @return Código de error
     */
    public int GetCurToolCoord(ref DescPose coord)

Obtener el sistema de coordenadas de pieza actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Obtener el sistema de coordenadas de pieza actual
     * @param [out] coord Valor del sistema de coordenadas
     * @return Código de error
     */
    public int GetCurWObjCoord(ref DescPose coord)

Obtener el sistema de coordenadas de herramienta externa actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Obtener el sistema de coordenadas de herramienta externa actual
     * @param  [out] coord Valor del sistema de coordenadas
     * @return Código de error
     */
    public int GetCurExToolCoord(ref DescPose coord)

Obtener el sistema de coordenadas del eje extendido actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Obtener el sistema de coordenadas del eje extendido actual
     * @param [out] coord Valor del sistema de coordenadas
     * @return Código de error
     */
    public int GetCurExAxisCoord(ref DescPose coord)

Ejemplo de código de obtención de coordenadas según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-V3.9.8

.. code-block:: c#
    :linenos:

    public int TestCoord()
    {
        int rtn;
        int id = 1;

        // GetToolCoordWithID
        DescPose toolCoord = new DescPose(0, 0, 0, 0, 0, 0);
        int type = 0, install = 0, toolID = 0, loadNo = 0;
        rtn = robot.GetToolCoordWithID(id, ref toolCoord, ref type, ref install, ref toolID, ref loadNo);
        Console.WriteLine("GetToolCoordWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3} {5:F3} {6:F3}, type={7}, install={8}, toolID={9}, loadNo={10}",
            id, toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz, type, install, toolID, loadNo);

        // GetWObjCoordWithID
        DescPose wobjCoord = new DescPose(0, 0, 0, 0, 0, 0);
        int refFrame = 0;
        rtn = robot.GetWObjCoordWithID(id, ref wobjCoord, ref refFrame);
        Console.WriteLine("GetWObjCoordWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3} {5:F3} {6:F3}, refFrame={7}",
            id, wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz, refFrame);

        // GetExToolCoordWithID
        DescPose extoolCoord = new DescPose(0, 0, 0, 0, 0, 0);
        DescPose exworkpieceCoord = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.GetExToolCoordWithID(21, ref extoolCoord, ref exworkpieceCoord);
        Console.WriteLine("GetExToolCoordWithID 21, {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);
        Console.WriteLine("  tcoord: {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            exworkpieceCoord.tran.x, exworkpieceCoord.tran.y, exworkpieceCoord.tran.z,
            exworkpieceCoord.rpy.rx, exworkpieceCoord.rpy.ry, exworkpieceCoord.rpy.rz);

        // GetExAxisCoordWithID
        DescPose exAxisCoord = new DescPose(0, 0, 0, 0, 0, 0);
        int axisCoordNum = 0, calibFlag = 0;
        rtn = robot.GetExAxisCoordWithID(id, ref exAxisCoord, ref axisCoordNum, ref calibFlag);
        Console.WriteLine("GetExAxisCoordWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3} {5:F3} {6:F3}, axisCoordNum={7}, calibFlag={8}",
            id, exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz, axisCoordNum, calibFlag);

        // GetTargetPayloadWithID
        double weight = 0.0;
        DescTran cog = new DescTran(0, 0, 0);
        rtn = robot.GetTargetPayloadWithID(id, ref weight, ref cog);
        Console.WriteLine("GetTargetPayloadWithID {0}, {1:F3} {2:F3} {3:F3} {4:F3}",
            id, weight, cog.x, cog.y, cog.z);

        // GetCurToolCoord
        rtn = robot.GetCurToolCoord(ref toolCoord);
        Console.WriteLine("GetCurToolCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz);

        // GetCurWObjCoord
        rtn = robot.GetCurWObjCoord(ref wobjCoord);
        Console.WriteLine("GetCurWObjCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz);

        // GetCurExToolCoord
        rtn = robot.GetCurExToolCoord(ref extoolCoord);
        Console.WriteLine("GetCurExToolCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);

        // GetCurExAxisCoord
        rtn = robot.GetCurExAxisCoord(ref exAxisCoord);
        Console.WriteLine("GetCurExAxisCoord {0:F3} {1:F3} {2:F3} {3:F3} {4:F3} {5:F3}",
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz);

        // GetTargetPayload / GetTargetPayloadCog
        double weightT = 0.0;
        DescTran cogT = new DescTran(0, 0, 0);
        robot.GetTargetPayload(0, ref weightT);
        robot.GetTargetPayloadCog(0, ref cogT);
        Console.WriteLine("GetTargetPayload {0:F3} {1:F3} {2:F3} {3:F3}",
            weightT, cogT.x, cogT.y, cogT.z);

        // SetToolCoord
        DescPose coordSet = new DescPose(0, 1, 2, 3, 4, 5);
        rtn = robot.SetToolCoord(1, coordSet, 0, 0, 1, 0);
        Console.WriteLine("SetToolCoord(1) rtn={0}", rtn);

        // SetWObjCoord
        rtn = robot.SetWObjCoord(1, coordSet, 0);
        Console.WriteLine("SetWObjCoord(1) rtn={0}", rtn);

        // SetLoadWeight + SetLoadCoord
        rtn = robot.SetLoadWeight(1, 1.3f);
        Console.WriteLine("SetLoadWeight(1,1.3) rtn={0}", rtn);

        DescTran loadCog = new DescTran(10, 20, 30);
        rtn = robot.SetLoadCoord(1, loadCog);
        Console.WriteLine("SetLoadCoord(1,10,20,30) rtn={0}", rtn);

        // SetExToolCoord
        DescPose etcp = new DescPose(0, 0, 100, 0, 0, 0);
        DescPose etool = new DescPose(0, 0, 50, 0, 0, 0);
        rtn = robot.SetExToolCoord(21, etcp, etool);
        Console.WriteLine("SetExToolCoord(21) rtn={0}", rtn);
        // SetExToolList
        rtn = robot.SetExToolList(21, etcp, etool);
        Console.WriteLine("SetExToolList(21) rtn={0}", rtn);

        // ExtAxisActiveECoordSys
        rtn = robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1);
        Console.WriteLine("ExtAxisActiveECoordSys(1,1,..,1) rtn={0}", rtn);

        return 0;
    }