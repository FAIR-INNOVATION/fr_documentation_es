Consulta del estado del robot
===================================

.. toctree:: 
    :maxdepth: 5

Obtener la posición actual de las articulaciones (ángulo)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la posición actual de las articulaciones (ángulo)
    * @param  [out] jPos Posición de las seis articulaciones obtenida, unidad deg
    * @return  Código de error
    */
    int GetActualJointPosDegree(JointPos jPos); 

Obtener la velocidad de retroalimentación de las articulaciones - deg/s
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener la velocidad de retroalimentación de las articulaciones - deg/s 
    * @param [out] speed Velocidad de las seis articulaciones
    * @return Código de error 
    */
    int GetActualJointSpeedsDegree(Object[] speed);

Obtener la aceleración de retroalimentación de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la aceleración de retroalimentación de las articulaciones - deg/s^2
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] acc Aceleración de las seis articulaciones
    * @return  Código de error
    */
    public int GetActualJointAccDegree(int flag, Object[] acc)

Obtener la velocidad compuesta de comando del TCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la velocidad de comando del TCP
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] tcp_speed Velocidad lineal
    * @param  [out] ori_speed Velocidad de orientación
    * @return  Código de error
    */
    public int GetTargetTCPCompositeSpeed(int flag, double tcp_speed, double ori_speed)

Obtener la velocidad compuesta de retroalimentación del TCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la velocidad compuesta de retroalimentación del TCP
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] tcp_speed Velocidad lineal
    * @param  [out] ori_speed Velocidad de orientación
    * @return  Código de error
    */
    public int GetActualTCPCompositeSpeed(int flag, double tcp_speed, double ori_speed)

Obtener la velocidad de comando del TCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la velocidad de comando del TCP
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] speed Velocidad [x,y,z,rx,ry,rz]
    * @return  Código de error
    */
    public int GetTargetTCPSpeed(int flag, Object[] speed)

Obtener la velocidad de retroalimentación del TCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la velocidad de retroalimentación del TCP
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] speed Velocidad [x,y,z,rx,ry,rz]
    * @return  Código de error
    */
    public int GetActualTCPSpeed(int flag, Object[] speed)

Obtener la pose actual de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la pose actual de la herramienta
    * @param  [out] desc_pos  Pose de la herramienta
    * @return  Código de error
    */
    int GetActualTCPPose(DescPose desc_pos); 

Obtener el número del sistema de coordenadas de herramienta actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el número del sistema de coordenadas de herramienta actual
    * @param  [in] flag  0-bloqueante, 1-no bloqueante
    * @param  [out] id  Número del sistema de coordenadas de herramienta
    * @return  Código de error
    */
    int GetActualTCPNum(int flag, int[] id)

Obtener el número del sistema de coordenadas de la pieza actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el número del sistema de coordenadas de la pieza actual
    * @param  [in] flag  0-bloqueante, 1-no bloqueante
    * @param  [out] id  Número del sistema de coordenadas de la pieza
    * @return  Código de error
    */
    public int GetActualWObjNum(int flag, int[] id)

Obtener la pose actual de la brida del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la pose actual de la brida del extremo
    * @param  [in] flag  0-bloqueante, 1-no bloqueante
    * @param  [out] desc_pos  Pose de la brida
    * @return  Código de error
    */
    public int GetActualToolFlangePose(int flag, DescPose desc_pos)

Obtener el par actual de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el par actual de las articulaciones
    * @param  [in]  flag 0-bloqueante, 1-no bloqueante
    * @param  [out]  torques Par de las articulaciones
    * @return  Código de error
    */
    int GetJointTorques(int flag, Object[] torques);

Obtener la hora del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la hora del sistema
    * @return  List[0]:int código de error; List[1]:double t_ms unidad ms
    */
    List<Number> GetSystemClock();

Sincronizar la hora del sistema con el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener la hora actual del sistema del PC anfitrión y enviarla al robot, sincronizar la hora del sistema (debido a las limitaciones del sistema QNX, la precisión de sincronización es de nivel de minuto)
    * @return Código de error
    */
    public int SetRobottime()

Ejemplo de código de sincronización de la hora del sistema con el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testSetAndGetRobotTime(Robot robot) 
    {
        // 1. Obtener la hora antes del ajuste
        List<Number> resultBefore = robot.GetSystemClock();
        int retBefore = (int) resultBefore.get(0);
        
        if (retBefore == 0) {
            double t_ms = (double) resultBefore.get(1);
            System.out.println("system clock : " + t_ms);
            
            // Convertir la marca de tiempo en milisegundos a DateTime (hora UTC)
            java.time.Instant instant = java.time.Instant.ofEpochMilli((long) t_ms);
            java.time.LocalDateTime utcTime = java.time.LocalDateTime.ofInstant(instant, java.time.ZoneOffset.UTC);
            System.out.println("BEFORE UTC Time   : " + 
                utcTime.format(java.time.format.DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss")));
        } else {
            System.out.println("GetSystemClock failed, ret:" + retBefore);
        }

        // 2. Ajustar la hora del robot
        int retSet = robot.SetRobotTime();
        if (retSet != 0) {
            System.out.println("SetRobotTime failed, ret:" + retSet);
            return;
        }

        // 3. Obtener la hora después del ajuste
        List<Number> resultAfter = robot.GetSystemClock();
        int retAfter = (int) resultAfter.get(0);
        
        if (retAfter == 0) {
            double t_ms_after = (double) resultAfter.get(1);
            System.out.println("system clock after: " + t_ms_after);
            
            // Convertir a hora UTC
            java.time.Instant instantAfter = java.time.Instant.ofEpochMilli((long) t_ms_after);
            java.time.LocalDateTime robotTimeAfter = java.time.LocalDateTime.ofInstant(instantAfter, java.time.ZoneOffset.UTC);

            // Obtener la hora actual del PC (como valor esperado)
            java.time.LocalDateTime pcTimeBefore = java.time.LocalDateTime.now(java.time.ZoneOffset.UTC);

            // Truncar a nivel de minuto para la comparación (debido a las limitaciones del sistema QNX, la precisión de sincronización es de nivel de minuto)
            java.time.LocalDateTime pcMinute = pcTimeBefore.withSecond(0).withNano(0);
            java.time.LocalDateTime robotMinute = robotTimeAfter.withSecond(0).withNano(0);

            // Comparar la consistencia
            boolean isConsistent = pcMinute.equals(robotMinute);
            if (isConsistent) {
                System.out.println("Consistent     | PC time: " + 
                    pcMinute.format(java.time.format.DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm")) + 
                    "  | Robot time: " + 
                    robotMinute.format(java.time.format.DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm")));
            } else {
                System.out.println("[Inconsistent | PC time: " + 
                    pcMinute.format(java.time.format.DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm")) + 
                    "  | Robot time: " + 
                    robotMinute.format(java.time.format.DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm")));
            }
        } else {
            System.out.println("GetSystemClock failed, ret:" + retAfter);
        }
    }

Consultar si el movimiento del robot ha finalizado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Consultar si el movimiento del robot ha finalizado
    * @param   [out] state  0-no finalizado, 1-finalizado
    * @return  Código de error
    */
    public int GetRobotMotionDone(int[] state)

Consultar la longitud de la caché de la cola de movimiento del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Consultar la longitud de la caché de la cola de movimiento del robot
    * @param   [out] len  Longitud de la caché
    * @return  Código de error
    */
    public int GetMotionQueueLength(int[] len)

Obtener el estado de parada de emergencia del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el estado de parada de emergencia del robot
    * @param [out] state Estado de parada de emergencia, 0-no parada de emergencia, 1-parada de emergencia
    * @return Código de error
    */
    public int GetRobotEmergencyStopState(int[] state)

Obtener el estado de comunicación entre el SDK y el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el estado de comunicación entre el SDK y el robot
    * @return state Estado de comunicación, 0-comunicación normal, 1-comunicación anormal
    */
    public int GetSDKComState()

Obtener la señal de parada de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener la señal de parada de seguridad
    * @param  [out] si0_state Señal de parada de seguridad SI0, 0-inválida, 1-válida
    * @param  [out] si1_state Señal de parada de seguridad SI1, 0-inválida, 1-válida
    * @return Código de error
    */
    public int GetSafetyStopState(int[] si0_state, int[] si1_state)

Obtener la temperatura del controlador de las articulaciones del robot (℃)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener la temperatura del controlador de las articulaciones del robot (℃)
    * @param  [out] temperature Temperatura
    * @return Código de error
    */
    public int GetJointDriverTemperature(double[] temperature)

Obtener el par del controlador de las articulaciones del robot (Nm)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el par del controlador de las articulaciones del robot (Nm)
    * @param  [out] torque Par
    * @return Código de error
    */
    public int GetJointDriverTorque(double[] torque)

Obtener la estructura del estado en tiempo real del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener la estructura del estado en tiempo real del robot
    * @return Estructura del estado en tiempo real
    */
    public ROBOT_STATE_PKG GetRobotRealTimeState()

Ejemplo de código de consulta del estado del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetStatus(Robot robot)
    {
        List<Number> angle=new ArrayList<>();
        angle=robot.GetRobotInstallAngle();
        System.out.println("yangle:"+angle.get(1)+",zangle:"+angle.get(2));

        JointPos j_deg =new JointPos(){};
        robot.GetActualJointPosDegree( j_deg);

        Object[] jointSpeed =new Object[] { 0,0,0,0,0,0 };
        robot.GetActualJointSpeedsDegree(jointSpeed);

        Object[] jointAcc = new Object[]{0,0,0,0,0,0 };
        robot.GetActualJointAccDegree(0, jointAcc);

        double tcp_speed = 0.0;
        double ori_speed = 0.0;
        robot.GetTargetTCPCompositeSpeed(0, tcp_speed, ori_speed);

        robot.GetActualTCPCompositeSpeed(0, tcp_speed, ori_speed);

        Object[] targetSpeed =new Object[] { 0,0,0,0,0,0 };
        robot.GetTargetTCPSpeed(0, targetSpeed);

        Object[] actualSpeed =new Object[] {0,0,0,0,0,0 };
        robot.GetActualTCPSpeed(0, actualSpeed);

        DescPose tcp = new DescPose(){};
        robot.GetActualTCPPose(tcp);

        DescPose flange = new DescPose(){};
        robot.GetActualToolFlangePose(0, flange);

        int[] id = {};
        robot.GetActualTCPNum(0, id);

        robot.GetActualWObjNum(0, id);

        List<Number> jtorque=new ArrayList<>();
        jtorque=robot.GetJointTorques(0);

        List<Number> t_ms = new ArrayList<>();
        t_ms=robot.GetSystemClock();

        List<Integer> config = new ArrayList<>();
        config=robot.GetRobotCurJointsConfig();

        int motionDone = 0;
        robot.GetRobotMotionDone(motionDone);

        int[] len ={0 };
        robot.GetMotionQueueLength(len);

        int[] emergState = {0};
        robot.GetRobotEmergencyStopState(emergState);

        int comstate = 0;
        comstate=robot.GetSDKComState();

        int[] si0_state=new int[]{0}, si1_state=new int[]{0};
        robot.GetSafetyStopState(si0_state, si1_state);

        double[] temp =new double[] { 0,0,0,0,0,0 };
        robot.GetJointDriverTemperature(temp);

        double[] torque = new double[]{ 0,0,0,0,0,0 };
        robot.GetJointDriverTorque(torque);

        ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
        pkg=robot.GetRobotRealTimeState();

        return 0;
    }

Solución de cinemática inversa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Solución de cinemática inversa
    * @param  [in] type 0-pose absoluta (sistema de coordenadas base), 1-pose incremental (sistema de coordenadas base), 2-pose incremental (sistema de coordenadas de herramienta)
    * @param  [in] desc_pos Pose cartesiana
    * @param  [in] config Configuración del espacio de articulaciones, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param  [out] joint_pos Posición de las articulaciones
    * @return  Código de error
    */ 
    int GetInverseKin(int type, DescPose desc_pos, int config, JointPos joint_pos);

Solución de cinemática inversa (posición de referencia)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Solución de cinemática inversa, resolver con referencia a la posición de articulaciones especificada
    * @param  [in] posMode 0-pose absoluta, 1-pose relativa - sistema de coordenadas base, 2-pose relativa - sistema de coordenadas de herramienta
    * @param  [in] desc_pos Pose cartesiana
    * @param  [in] joint_pos_ref Posición de articulaciones de referencia
    * @param  [out] joint_pos Posición de las articulaciones
    * @return  Código de error
    */   
    int GetInverseKinRef(int posMode, DescPose desc_pos, JointPos joint_pos_ref, JointPos joint_pos); 

Solución de cinemática inversa, el espacio cartesiano incluye la posición del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Solución de cinemática inversa, el espacio cartesiano incluye la posición del eje extendido
    * @param  type 0-pose absoluta (sistema de coordenadas base), 1-pose incremental (sistema de coordenadas base), 2-pose incremental (sistema de coordenadas de herramienta)
    * @param  desc_pos Pose cartesiana
    * @param  exaxis Posición del eje extendido
    * @param  tool Número de herramienta
    * @param  workPiece Número de pieza
    * @param  joint_pos Posición de las articulaciones
    * @param  config -1: resolución automática, 0-7 corresponden a las ocho soluciones
    * @return Código de error
    */
    public int GetInverseKinExaxis(int type, DescPose desc_pos, ExaxisPos exaxis, int tool, int workPiece, JointPos joint_pos, int config)
    
Ejemplo de código de solución de cinemática inversa con posición del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void  TestInverseKinExaxis(Robot robot)
    {
        DescPose desc=new DescPose(99.957, -0.002, 29.994, -176.569, -6.757, -167.462);
        ExaxisPos exaxis=new ExaxisPos(100.0, 0.0, 0.0, 0.0);
        JointPos jointPos =new JointPos();
        DescPose offsetPos =new DescPose();

        ROBOT_STATE_PKG pkg=robot.GetRobotRealTimeState();
        int toolnum = pkg.tool;
        int workPcsNum = pkg.user;
        robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum, jointPos, 0);
        System.out.printf("GetInverseKinExaxis joint is %f, %f, %f, %f, %f, %f\n", jointPos.J1, jointPos.J2, jointPos.J3, jointPos.J4, jointPos.J5, jointPos.J6);

        robot.ExtAxisMove(exaxis, 100, -1);
        robot.MoveJ(jointPos, desc, toolnum, workPcsNum, 100.0, 100.0, 100.0, exaxis, -1, 0, offsetPos);

    }

Obtener si la cinemática inversa tiene solución
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Solución de cinemática inversa, determinar con referencia a la posición de articulaciones especificada si tiene solución
    * @param  [in] posMode 0-pose absoluta, 1-pose relativa - sistema de coordenadas base, 2-pose relativa - sistema de coordenadas de herramienta
    * @param  [in] desc_pos Pose cartesiana
    * @param  [in] joint_pos_ref Posición de articulaciones de referencia
    * @return  Código de error  List[0]:código de error; List[1]: int hasResult 0-sin solución, 1-con solución
    */   
    List<Integer> GetInverseKinHasSolution(int posMode, DescPose desc_pos, JointPos joint_pos_ref);  

Obtener las 8 soluciones de cinemática inversa del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief  Obtener las 8 soluciones de cinemática inversa
     * @param [in] tcp_pose Pose cartesiana
     * @param [in] tool Sistema de coordenadas de herramienta
     * @param [in] workpiece Sistema de coordenadas de la pieza
     * @param [in] exPos Posición del eje extendido
     * @param [out] jPos Salida de las 8 soluciones de ángulos de articulaciones
     * @return Código de error
     */
    public int TCFToAllJoint(DescPose tcp_pose, int tool, int workpiece, ExaxisPos exPos, JointPos[] jPos)

Ejemplo de código para obtener las 8 soluciones de cinemática inversa del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestTCFToAllJoint(Robot robot)
    {
        DescPose curTcp = new DescPose(0, 0, 0, 0, 0, 0);
        int rtn = robot.GetActualTCPPose(curTcp);
        if (rtn != 0)
        {
            return rtn;
        }
        ExaxisPos exPos = new ExaxisPos(0, 0, 0, 0);

        JointPos[] allJoints = new JointPos[8];

        rtn = robot.TCFToAllJoint(curTcp, 0, 0, exPos, allJoints);
        if (rtn != 0)
        {
            return rtn;
        }

        for (int i = 0; i < 8; i++)
        {
            JointPos joint = allJoints[i];

            System.out.printf("JOINT%d: j1=%.3f, j2=%.3f, j3=%.3f, j4=%.3f, j5=%.3f, j6=%.3f\n",
                    i + 1, joint.J1, joint.J2, joint.J3, joint.J4, joint.J5, joint.J6);

            DescPose pos = new DescPose(0, 0, 0, 0, 0, 0);
            rtn = robot.GetForwardKin(joint, pos);
            if (rtn != 0)
            {
                continue;
            }

            System.out.printf("POS%d: x=%.3f, y=%.3f, z=%.3f, a=%.3f, b=%.3f, c=%.3f\n",
                    i + 1, pos.tran.x, pos.tran.y, pos.tran.z,
                    pos.rpy.rx, pos.rpy.ry, pos.rpy.rz);
        }

        return 0;
    }

Solución de cinemática directa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Solución de cinemática directa
    * @param  [in] joint_pos Posición de las articulaciones
    * @param  [out] desc_pos Pose cartesiana
    * @return  Código de error
    */
    int GetForwardKin(JointPos joint_pos, DescPose desc_pos); 

Ejemplo de código de cálculo de cinemática directa e inversa del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestInverseKin(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);

        JointPos inverseRtn = new JointPos(){};

        robot.GetInverseKin(0, desc_pos1, -1, inverseRtn);
        robot.GetInverseKinRef(0, desc_pos1, j1, inverseRtn);

        int hasResut = 0;
        robot.GetInverseKinHasSolution(0, desc_pos1, j1);

        DescPose forwordResult = new DescPose(){};
        robot.GetForwardKin(j1, forwordResult);

        return 0;
    }

Consultar los datos de los puntos de enseñanza del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Consultar los datos de los puntos de enseñanza del robot 
    * @param [in]  name  Nombre del punto
    * @return  List[0]:código de error; List[1] - List[20] : datos del punto double[20]{x,y,z,rx,ry,rz,j1,j2,j3,j4,j5,j6,tool,wobj,speed,acc,e1,e2,e3,e4} 
    */ 
    List<Number> GetRobotTeachingPoint(String name); 

Obtener el valor de compensación de los parámetros DH del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el valor de compensación de los parámetros DH del robot
    * @param dhCompensation Valor de compensación de los parámetros DH del robot (mm) [cmpstD1,cmpstA2,cmpstA3,cmpstD4,cmpstD5,cmpstD6]
    * @return Código de error
    */
    public int GetDHCompensation(Object[] dhCompensation)

Obtener el código SN de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el código SN de la caja de control
    * @param [out] SNCode Código SN de la caja de control
    * @return Código de error
    */
    int GetRobotSN(String[] SNCode);

Ejemplo de código de consulta de los datos de los puntos de enseñanza del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetTeachPoint(Robot robot)
    {
        String name = "P1";
        List<Number> data=new ArrayList<>();
        data = robot.GetRobotTeachingPoint(name);
        System.out.println(name+" name is: "+data.get(0));
        for (int i = 0; i < 20; i++)
        {
            System.out.println("data is: "+ data.get(i+1));
        }

        int[] que_len = {0};
        int rtn = robot.GetMotionQueueLength(que_len);
        System.out.println("GetMotionQueueLength rtn is:"+rtn+", queue length is:"+ que_len[0]);

        Object[] dh = new Object[]{ 0,0,0,0,0,0 };
        int retval = 0;
        retval = robot.GetDHCompensation(dh);
        System.out.println("retval is: "+retval);

        String[] SN = new String[]{""};
        robot.GetRobotSN(SN);
        System.out.println("robot SN is "+SN[0]);
        return 0;
    }

Obtener el sistema de coordenadas de herramienta según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
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
    int GetToolCoordWithID(int id, DescPose coord, int[] type, int[] install, int[] toolID, int[] loadNo)

Obtener el sistema de coordenadas de la pieza según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas de la pieza según el número
    * @param [in] id Número del sistema de coordenadas de la pieza
    * @param [out] coord Valor del sistema de coordenadas
    * @param [out] refFrame Sistema de coordenadas de referencia
    * @return Código de error
    */
    public int GetWObjCoordWithID(int id, DescPose coord, int[] refFrame)

Obtener el sistema de coordenadas de herramienta externa según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas de herramienta externa según el número
    * @param [in] id Número del sistema de coordenadas de herramienta externa, 20-39 corresponden a los sistemas de coordenadas de herramienta externa 0-19
    * @param [out] coord Pose del TCP de la herramienta fija externa del robot
    * @param [out] tcoord Pose del sistema de coordenadas de la pieza instalada en el extremo del robot
    * @return Código de error
    */
    public int GetExToolCoordWithID(int id, DescPose coord, DescPose tcoord)

Obtener el sistema de coordenadas del eje extendido según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas del eje extendido según el número
    * @param [in] id Número del sistema de coordenadas de herramienta externa
    * @param [out] coord Valor del sistema de coordenadas
    * @param [out] axisCoordNum Número del eje extendido; bit0-bit3 corresponden al eje extendido 1-eje extendido 4; si el valor de axisCoordNum es 3, corresponde a la aplicación del eje extendido [1, 2]
    * @param [out] calibFlag Indicador de calibración; 0-no calibrado; 1-calibrado
    * @return Código de error
    */
    public int GetExAxisCoordWithID (int id, DescPose coord, int[] axisCoordNum, int[] calibFlag)

Obtener el sistema de coordenadas de herramienta actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Obtener el sistema de coordenadas de herramienta actual
     * @param [out] coord Valor del sistema de coordenadas
     * @return Código de error
     */
    public int GetCurToolCoord(DescPose coord)

Obtener el sistema de coordenadas de la pieza actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Obtener el sistema de coordenadas de la pieza actual
     * @param [out] coord Valor del sistema de coordenadas
     * @return Código de error
     */
    public int GetCurWObjCoord(DescPose coord)

Obtener el sistema de coordenadas de herramienta externa actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Obtener el sistema de coordenadas de herramienta externa actual
     * @param  [out] coord Valor del sistema de coordenadas
     * @return Código de error
     */
    public int GetCurExToolCoord(DescPose coord)

Obtener el sistema de coordenadas del eje extendido actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Obtener el sistema de coordenadas del eje extendido actual
     * @param [out] coord Valor del sistema de coordenadas
     * @return Código de error
     */
    public int GetCurExAxisCoord(DescPose coord)

Ejemplo de código para obtener los sistemas de coordenadas y la carga del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestCoord(Robot robot)
    {
        int id = 1;
        DescPose toolCoord = new DescPose();
        DescPose extoolCoord = new DescPose();
        DescPose exworkpieceCoord = new DescPose();
        DescPose wobjCoord = new DescPose();
        DescPose exAxisCoord = new DescPose();
        int[] type = new int[1];
        int[] install = new int[1];
        int[] toolID = new int[1];
        int[] loadNo = new int[1];
        robot.GetToolCoordWithID(id, toolCoord, type, install, toolID, loadNo);
        System.out.printf("GetToolCoordWithID %d, %f %f %f %f %f %f,  type = %d, install = %d, toolID = %d, loadNo = %d\n", id,
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz, type[0], install[0], toolID[0], loadNo[0]);
        int[] refFrame = new int[1];
        robot.GetWObjCoordWithID(id, wobjCoord, refFrame);
        System.out.printf("GetWObjCoordWithID %d, %f %f %f %f %f %f, refFrame = %d\n", id,
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz, refFrame[0]);


        robot.GetExToolCoordWithID(21, extoolCoord, exworkpieceCoord);
        System.out.printf("GetExToolCoordWithID %d, %f %f %f %f %f %f\n", id,
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz,
            exworkpieceCoord.tran.x, exworkpieceCoord.tran.y, exworkpieceCoord.tran.z,
            exworkpieceCoord.rpy.rx, exworkpieceCoord.rpy.ry, exworkpieceCoord.rpy.rz);

        int[] axisCoordNum = new int[1];
        int[] calibFlag = new int[1];
        robot.GetExAxisCoordWithID(id, exAxisCoord, axisCoordNum, calibFlag);
        System.out.printf("GetExAxisCoordWithID %d, %f %f %f %f %f %f, axisCoordNum = %d, calibFlag = %d\n", id,
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz, axisCoordNum[0], calibFlag[0]);

        double[] weight = new double[1];
        DescTran cog = new DescTran();
        robot.GetTargetPayloadWithID(id, weight, cog);
        System.out.println("GetTargetPayload is " + weightT.get(0) + " cogT is  " + cogT.x + "  " + cogT.y + "  " + cogT.z);
        robot.GetCurToolCoord(toolCoord);
        System.out.printf("GetCurToolCoord %f %f %f %f %f %f\n",
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz);
        robot.GetCurWObjCoord(wobjCoord);
        System.out.printf("GetCurWObjCoord %f %f %f %f %f %f\n",
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz);
        robot.GetCurExToolCoord(extoolCoord);
        System.out.printf("GetExToolCoordWithID %f %f %f %f %f %f\n",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);
        robot.GetCurExAxisCoord(exAxisCoord);
        System.out.printf("GetCurExAxisCoord %f %f %f %f %f %f\n",
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz);
        DescTran cogT = new DescTran();
        List<Number> weightT = robot.GetTargetPayload(0);
        robot.GetTargetPayloadCog(0, cogT);
        System.out.printf("GetTargetPayload %f %f %f %f\n", weightT.get(0),
            cogT.x, cogT.y, cogT.z);
        DescPose coordSet = new DescPose(0, 1, 2, 3, 4, 5);
        robot.SetToolCoord(1, coordSet, 0, 0, 1, 0);
        robot.SetWObjCoord(1, coordSet, 0);
        robot.SetLoadWeight(1, 1.3);
        cog.x = 10;
        cog.y = 20;
        cog.z = 30;
        robot.SetLoadCoord(1, cog);
        DescPose etcp = new DescPose(0, 0, 100, 0, 0, 0);
        DescPose etool = new DescPose(0, 0, 50, 0, 0, 0);
        int rtn = robot.SetExToolCoord(21, etcp, etool);
        System.out.printf("SetExToolCoord rtn is %d\n", rtn);
        robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1);
        return 0;
    }