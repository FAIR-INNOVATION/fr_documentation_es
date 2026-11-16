Periféricos del robot
=====================

.. toctree:: 
    :maxdepth: 5

Configurar la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Configurar la pinza
    * @param  [in] company  Fabricante de la pinza, pendiente de definir
    * @param  [in] device  Número de dispositivo, no se utiliza por ahora, por defecto 0
    * @param  [in] softvesion  Número de versión del software, no se utiliza por ahora, por defecto 0
    * @param  [in] bus Posición del bus del extremo donde está conectado el dispositivo, no se utiliza por ahora, por defecto 0
    * @return  Código de error
    */
    int SetGripperConfig(int company, int device, int softvesion, int bus);

Obtener la configuración de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la configuración de la pinza
    * @param  [in] company  Fabricante de la pinza, pendiente de definir
    * @param  [in] device  Número de dispositivo, no se utiliza por ahora, por defecto 0
    * @param  [in] softvesion  Número de versión del software, no se utiliza por ahora, por defecto 0
    * @param  [in] bus Posición del bus del extremo donde está conectado el dispositivo, no se utiliza por ahora, por defecto 0
    * @return  Código de error
    */
    int GetGripperConfig(int *company, int *device, int *softvesion, int *bus);

Activar la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Activar la pinza
    * @param  [in] index  Número de la pinza
    * @param  [in] act  0-restablecer, 1-activar
    * @return  Código de error
    */
    int ActGripper(int index, byte act); 

Controlar la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Controlar la pinza
    * @param  [in] index  Número de la pinza
    * @param  [in] pos  Porcentaje de posición, rango [0~100]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] force  Porcentaje de par, rango [0~100]
    * @param  [in] max_time  Tiempo máximo de espera, rango [0~30000], unidad ms
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [in] type Tipo de pinza, 0-pinza paralela; 1-pinza rotativa
    * @param  [in] rotNum Número de vueltas de rotación
    * @param  [in] rotVel Porcentaje de velocidad de rotación [0-100]
    * @param  [in] rotTorque Porcentaje de par de rotación [0-100]
    * @return  Código de error
    */
    int MoveGripper(int index, int pos, int vel, int force, int max_time, byte block, int type, double rotNum, int rotVel, int rotTorque);

Obtener el estado de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el estado de movimiento de la pinza (a partir de la versión 401, el protocolo del extremo está unificado con la definición de retroalimentación del estado de movimiento de la pinza de los dispositivos ya adaptados)
    * @param  [out] fault  0-sin error, otro-con error
    * @param  [out] staus  0-movimiento no completado, 1-movimiento completado sin detección de objeto 2-movimiento completado con detección de objeto 3-movimiento completado con detección de caída del objeto
    * @return  Código de error
    */
    int GetGripperMotionDone(ref int fault, ref int status); 

Obtener el estado de activación de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el estado de activación de la pinza
    * @param  [out] fault  0-sin error, 1-con error
    * @param  [out] status  bit0~bit15 corresponden a los números de pinza 0~15; bit=0 no activada, bit=1 activada
    * @return  Código de error
    */
    int GetGripperActivateStatus(ref int fault, ref int status);

Esperar el estado de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Esperar el estado de movimiento de la pinza (a partir de la versión 401, el protocolo del extremo está unificado con la definición de retroalimentación del estado de movimiento de la pinza de los dispositivos ya adaptados)
    * @param  [in]  staus  0-movimiento no completado, 1-movimiento completado sin detección de objeto 2-movimiento completado con detección de objeto 3-movimiento completado con detección de caída del objeto
    * @param  [in] timeout Tiempo de espera agotado (ms) -1 espera permanente
    * @param  [in] strategy  0-detener con error, 1-continuar en ejecución
    * @param  [in] type  0-pinza paralela, 1-pinza rotativa
    * @return  Código de error
    */
    public int GripperWaitMotionDone(int staus, int timeout, int strategy, int type) 
    
Ejemplo de código de espera del estado de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestGetGripperMotionDone()
    {
        int rtn;
        int status = 0;
        int fault = 0;
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        // Abrir la pinza
        rtn = robot.MoveGripper(2, 50, 50, 100, 30000, 0, 0, 0, 0, 0);
        Console.WriteLine("MoveGripper(张开) ret={0}", rtn);
        Thread.Sleep(2000);
        robot.GetRobotRealTimeState(ref pkg);
        Console.WriteLine(" gripper_motiondone {0})", pkg.gripper_motiondone);
        // Cerrar la pinza
        rtn = robot.MoveGripper(2, 90, 100, 100, 30000, 0, 0, 0, 0, 0);
        Console.WriteLine("MoveGripper(闭合) ret={0}", rtn);
        Thread.Sleep(2000);
        robot.GetRobotRealTimeState(ref pkg);
        Console.WriteLine(" gripper_motiondone {0}", pkg.gripper_motiondone);
        // Esperar a que el movimiento finalice sin detectar objeto, tiempo de espera 5 s, detener con error
        rtn = robot.GripperWaitMotionDone(2, 5000, 0, 0);
        Console.WriteLine("GripperWaitMotionDone(等待完成未检测到物体) ret={0}", rtn);

        while (true)
        {

            robot.GetGripperMotionDone(ref fault, ref status);
            Console.WriteLine("motion status:{0},{1}\n", fault, status);
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine(" error code {0},{1}", pkg.main_code, pkg.sub_code);
            Thread.Sleep(500);

        }
    }

Obtener la posición de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la posición de la pinza
    * @param  [out] fault  0-sin error, 1-con error
    * @param  [out] position  Porcentaje de posición, rango 0~100%
    * @return  Código de error
    */
    int GetGripperCurPosition(ref int fault, ref int position);

Obtener la velocidad de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la velocidad de la pinza
    * @param  [out] fault  0-sin error, 1-con error
    * @param  [out] speed  Porcentaje de velocidad, rango 0~100%
    * @return  Código de error
    */
    int GetGripperCurSpeed(ref int fault, ref int speed);
     
Obtener la corriente de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la corriente de la pinza
    * @param  [out] fault  0-sin error, 1-con error
    * @param  [out] current  Porcentaje de corriente, rango 0~100%
    * @return  Código de error
    */
    int GetGripperCurCurrent(ref int fault, ref int current);

Obtener la tensión de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la tensión de la pinza
    * @param  [out] fault  0-sin error, 1-con error
    * @param  [out] voltage  Tensión, unidad 0.1V
    * @return  Código de error
    */
    int GetGripperVoltage(ref int fault, ref int voltage);

Obtener la temperatura de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la temperatura de la pinza
    * @param  [out] fault  0-sin error, 1-con error
    * @param  [out] temp  Temperatura, unidad ℃
    * @return  Código de error
    */
    int GetGripperTemp(ref int fault, ref int temp);

Calcular el punto de preagarre - visión
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Calcular el punto de preagarre - visión 
    * @param [in] desc_pos Pose cartesiana del punto de agarre 
    * @param [in] zlength Desplazamiento del eje z 
    * @param [in] zangle Desplazamiento de rotación alrededor del eje z
    * @param [out] pre_pos Punto de preagarre
    * @return Código de error 
    */ 
    int ComputePrePick(DescPose desc_pos, double zlength, double zangle, ref DescPose pre_pos);

Calcular el punto de retirada - visión
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Calcular el punto de retirada - visión 
    * @param [in] desc_pos Pose cartesiana del punto de retirada 
    * @param [in] zlength Desplazamiento del eje z 
    * @param [in] zangle Desplazamiento de rotación alrededor del eje z
    * @param [out] post_pos Punto de retirada
    * @return Código de error 
    */ 
    int ComputePostPick(DescPose desc_pos, double zlength, double zangle, ref DescPose post_pos);

Ejemplo de código de operación de la pinza del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button36_Click(object sender, EventArgs e)
    {
        int company = 4;
        int device = 0;
        int softversion = 0;
        int bus = 2;
        int index = 2;
        byte act = 0;
        int max_time = 30000;
        byte block = 0;
        int status=0;
        int fault=0;
        int active_status = 0;
        int current_pos = 0;
        int current = 0;
        int voltage = 0;
        int temp = 0;
        int speed = 0;

        robot.SetGripperConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.GetGripperConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine("gripper config:{0},{1},{2},{3}\n", company, device, softversion, bus);

        robot.ActGripper(index, act);
        Thread.Sleep(1000);
        act = 1;
        robot.ActGripper(index, act);
        Thread.Sleep(1000);

        robot.MoveGripper(index, 90, 50, 50, max_time, block, 0, 0, 0, 0);
        Thread.Sleep(1000);
        robot.MoveGripper(index, 30, 50, 0, max_time, block, 0, 0, 0, 0);

        robot.GetGripperMotionDone(ref fault, ref status);
        Console.WriteLine("motion status:{0},{1}\n", fault, status);

        robot.GetGripperActivateStatus(ref fault, ref active_status);
        Console.WriteLine("gripper active fault is: {0}, status is: {1}\n", fault, active_status);

        robot.GetGripperCurPosition(ref fault, ref current_pos);
        Console.WriteLine("fault is:{0}, current position is: {1}\n", fault, current_pos);

        robot.GetGripperCurCurrent(ref fault, ref current);
        Console.WriteLine("fault is:{0}, current current is: {1}\n", fault, current);

        robot.GetGripperVoltage(ref fault, ref voltage);
        Console.WriteLine("fault is:{0}, current voltage is: {1} \n", fault, voltage);

        robot.GetGripperTemp(ref fault, ref temp);
        Console.WriteLine("fault is:{0}, current temperature is: {1}\n", fault, temp);

        robot.GetGripperCurSpeed(ref fault, ref speed);
        Console.WriteLine("fault is:{0}, current speed is: {1}\n", fault, speed);

        int retval = 0;
        DescPose prepick_pose = new DescPose();
        DescPose postpick_pose = new DescPose();

        DescPose p1Desc = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose p2Desc = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        retval = robot.ComputePrePick(p1Desc, 10, 0, ref prepick_pose);
        Console.WriteLine("ComputePrePick retval is: {0}\n", retval);
        Console.WriteLine("xyz is: {0}, {1}, {2}; rpy is: {3}, {4}, {5}\n",
            prepick_pose.tran.x, prepick_pose.tran.y, prepick_pose.tran.z,
            prepick_pose.rpy.rx, prepick_pose.rpy.ry, prepick_pose.rpy.rz);

        retval = robot.ComputePostPick( p2Desc, -10, 0, ref postpick_pose);
        Console.WriteLine("ComputePostPick retval is: {0}\n", retval);
        Console.WriteLine("xyz is: {0}, {1}, {2}; rpy is: {3}, {4}, {5}\n",
            postpick_pose.tran.x, postpick_pose.tran.y, postpick_pose.tran.z,
            postpick_pose.rpy.rx, postpick_pose.rpy.ry, postpick_pose.rpy.rz);

    }

Obtener el número de vueltas de la pinza rotativa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el número de vueltas de la pinza rotativa
    * @param  [out] fault  0-sin error, 1-con error
    * @param  [out] num  Número de vueltas de rotación
    * @return  Código de error
    */
    int GetGripperRotNum(ref UInt16 fault, ref double num);

Obtener el porcentaje de velocidad de rotación de la pinza rotativa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el porcentaje de velocidad de rotación de la pinza rotativa
    * @param  [out] fault  0-sin error, 1-con error
    * @param  [out] speed  Porcentaje de velocidad de rotación
    * @return  Código de error
    */
    int GetGripperRotSpeed(ref UInt16 fault, ref int speed);

Obtener el porcentaje de par de rotación de la pinza rotativa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el porcentaje de par de rotación de la pinza rotativa
    * @param  [out] fault  0-sin error, 1-con error
    * @param  [out] torque  Porcentaje de par de rotación
    * @return  Código de error
    */
    int GetGripperRotTorque(ref UInt16 fault, ref int torque);

Ejemplo de código de obtención del estado de la pinza rotativa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    int MoveRotGripper(int pos, double rotPos)
    {
        robot.ResetAllError();
        robot.ActGripper(1, 1);
        Thread.Sleep(1000);
        int rtn = robot.MoveGripper(1, pos, 50, 50, 5000, 1, 1, rotPos, 50, 100);
        Console.WriteLine($"move gripper rtn is {rtn}" );
        UInt16 fault = 0;
        double rotNum = 0.0;
        int rotSpeed = 0;
        int rotTorque = 0;
        robot.GetGripperRotNum(ref fault, ref rotNum);
        robot.GetGripperRotSpeed(ref fault, ref rotSpeed);
        robot.GetGripperRotTorque(ref fault, ref rotTorque);
        Console.WriteLine($"gripper rot num :{ rotNum}, gripper rotSpeed :{rotSpeed}, gripper rotTorque : { rotTorque}");
        return 0;
    }

Inicio y parada de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Inicio y parada de la cinta transportadora 
    * @param [in] status Estado, 1-iniciar, 0-detener
    * @return Código de error 
    */ 
    int ConveyorStartEnd(byte status); 

Registro del punto de detección IO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Registro del punto de detección IO 
    * @return Código de error 
    */ 
    int ConveyorPointIORecord(); 

Registro del punto A
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Registro del punto A 
    * @return Código de error 
    */ 
    int ConveyorPointARecord();

Registro del punto de referencia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Registro del punto de referencia 
    * @return Código de error 
    */ 
    int ConveyorRefPointRecord(); 

Registro del punto B
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Registro del punto B 
    * @return Código de error 
    */ 
    int ConveyorPointBRecord();

Detección IO de piezas en la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Detección IO de piezas en la cinta transportadora 
    * @param [in] max_t Tiempo máximo de detección, unidad ms
    * @return Código de error 
    */ 
    int ConveyorIODetect(int max_t);

Obtener la posición actual del objeto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la posición actual del objeto 
    * @param [in] mode 1-agarre con seguimiento, 2-movimiento con seguimiento, 3-seguimiento TPD
    * @return Código de error 
    */ 
    int ConveyorGetTrackData(int mode);

Inicio del seguimiento de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Inicio del seguimiento de la cinta transportadora 
    * @param [in] status Estado, 1-iniciar, 0-detener
    * @return Código de error 
    */
    int ConveyorTrackStart(byte status);

Parada del seguimiento de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Parada del seguimiento de la cinta transportadora 
    * @return Código de error 
    */
    int ConveyorTrackEnd();

Configuración de parámetros del seguimiento en el lugar de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Configuración de parámetros del seguimiento en el lugar de la cinta transportadora
    * @param  [in] trackMode 0-tiempo; 1-distancia; 2-tiempo y distancia, se cumple cualquiera de los dos
    * @param  [in] trackTime Tiempo de seguimiento, unidad s
    * @param  [in] trackDis Distancia de seguimiento
    * @return  Código de error
    */
    public int SetStationaryTrackPara(int trackMode, double trackTime, int trackDis)
    
Esperar a que finalice el movimiento en vacío en el lugar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Esperar a que finalice el movimiento en vacío en el lugar
    * @return Código de error
    */
    public int WaitStationaryMotionDone()
        
Ejemplo de código de movimiento de seguimiento en el lugar de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int TestStationaryTrack()
    {
        Console.WriteLine("\n========== Stationary Track Test ==========");

        int rtn;

        JointPos j1 = new JointPos(-35.146, -102.684, 120.805, -100.401, -90.295, 150.105);
        DescPose d1 = new DescPose(-121.814, -348.341, 209.978, -173.152, -3.585, -5.446);

        ExaxisPos ex = new ExaxisPos(0, 0, 0, 0);
        DescPose zeroOff = new DescPose(0, 0, 0, 0, 0, 0);

        int tool = 1;
        int workpiece = 1;

        rtn = robot.ConveyorSetParam(0, 10000, 200, 0, 0, 10);

        robot.MoveJ(j1, d1, tool, workpiece, 100, 100, 100, ex, -1, 0, zeroOff);

        // Paso 1: Activar la señal de control SetDO
        Console.WriteLine("--- Step 1: SetDO(6,1) ---");
        rtn = robot.SetDO(6, 1, 0, 0);
        Console.WriteLine("  SetDO(6,1) rtn={0}", rtn);

        // Paso 2: Iniciar el seguimiento de la cinta transportadora
        Console.WriteLine("--- Step 2: ConveyorTrackStart(2) ---");
        rtn = robot.ConveyorTrackStart(2);
        Console.WriteLine("  ConveyorTrackStart(2) rtn={0}", rtn);

        // Paso 3: Detección IO de piezas
        Console.WriteLine("--- Step 3: ConveyorIODetect(10000) ---");
        rtn = robot.ConveyorIODetect(10000);
        Console.WriteLine("  ConveyorIODetect(10000) rtn={0}", rtn);

        // Paso 4: Obtener los datos de seguimiento
        Console.WriteLine("--- Step 4: ConveyorGetTrackData(2) ---");
        rtn = robot.ConveyorGetTrackData(2);
        Console.WriteLine("  ConveyorGetTrackData(2) rtn={0}", rtn);

        // Paso 5: Establecer los parámetros del seguimiento en el lugar (modo tiempo, 200 s, distancia 5)
        Console.WriteLine("--- Step 5: SetStationaryTrackPara(0,200,5) ---");
        rtn = robot.SetStationaryTrackPara(0, 5, 5);
        Console.WriteLine("  SetStationaryTrackPara(0,200,5) rtn={0}", rtn);

        // Paso 6: Ejecutar el movimiento en el lugar
        Console.WriteLine("--- Step 6: MoveStationary() ---");
        rtn = robot.MoveStationary();
        Console.WriteLine("  MoveStationary() rtn={0}", rtn);

        // Paso 7: Esperar a que finalice el movimiento en el lugar
        Console.WriteLine("--- Step 7: WaitStationaryMotionDone() ---");
        rtn = robot.WaitStationaryMotionDone();
        Console.WriteLine("  WaitStationaryMotionDone() rtn={0}", rtn);

        // Paso 8: Finalizar el seguimiento de la cinta transportadora
        Console.WriteLine("--- Step 8: ConveyorTrackEnd() ---");
        rtn = robot.ConveyorTrackEnd();
        Console.WriteLine("  ConveyorTrackEnd() rtn={0}", rtn);

        // Paso 9: Desactivar la señal de control SetDO
        Console.WriteLine("--- Step 9: SetDO(6,0) ---");
        rtn = robot.SetDO(6, 0, 0, 0);
        Console.WriteLine("  SetDO(6,0) rtn={0}", rtn);

        Console.WriteLine("\n========== Stationary Track Test Complete ==========");
        return 0;
    }

Configuración de parámetros de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Configuración de parámetros de la cinta transportadora
    * @param [in] para[0] Canal del codificador 1~2
    * @param [in] para[1] Número de pulsos por vuelta del codificador
    * @param [in] para[2] Distancia recorrida por la cinta transportadora por vuelta del codificador
    * @param [in] para[3] Número del sistema de coordenadas de pieza; para la función de movimiento con seguimiento seleccione el número del sistema de coordenadas de pieza; para el agarre con seguimiento y el seguimiento TPD se establece en 0
    * @param [in] para[4] Si se configura visión  0 no configurar  1 configurar
    * @param [in] para[5] Relación de velocidad  para la opción de agarre con seguimiento de cinta transportadora (1-100); para otras opciones el valor predeterminado es 1 
    * @return Código de error
    */
    int ConveyorSetParam(int encChannel, int resolution, double lead, int wpAxis, int vision, double speedRadio, int followType, int startDis=0, int endDis=100);

Establecer la compensación del punto de agarre de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer la compensación del punto de agarre de la cinta transportadora 
    * @param [in] cmp Posición de compensación double[3]{x, y, z}
    * @return Código de error 
    */
    int ConveyorCatchPointComp(double[] cmp);

Movimiento lineal con seguimiento de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Movimiento lineal con seguimiento de la cinta transportadora 
    * @param [in] name Nombre del punto de movimiento
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14] 
    * @param [in] wobj Número del sistema de coordenadas de pieza, rango [0~14] 
    * @param [in] vel Porcentaje de velocidad, rango [0~100] 
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible 
    * @param [in] ovl Factor de escala de velocidad, rango [0~100] 
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm  
    * @return Código de error 
    */
    int ConveyorTrackMoveL(string name, int tool, int wobj, float vel, float acc, float ovl, float blendR);

Detección de entrada de comunicación de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Detección de entrada de comunicación de la cinta transportadora
    * @param [in] timeout Tiempo de espera máximo ms
    * @return Código de error
    */
    public int ConveyorComDetect(int timeout)

Disparo de la detección de entrada de comunicación de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Disparo de la detección de entrada de comunicación de la cinta transportadora
    * @return Código de error
    */
    int ConveyorComDetectTrigger();

Programa de ejemplo de disparo de la detección de entrada de comunicación de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button3_Click(object sender, EventArgs e)
    {

        // Desactivar el botón para evitar clics repetidos
        button3.Enabled = false;

        // Ejecutar la operación costosa en un hilo en segundo plano
        Thread conveyorThread = new Thread(ConveyorTest);
        conveyorThread.IsBackground = true;
        conveyorThread.Start();
    }

    private void button4_Click(object sender, EventArgs e)
    {
        // Obtener la entrada del usuario
        string input = texBox.Text;
        Console.WriteLine($"please input a number to trigger:{input}");
    
        int rtn = robot.ConveyorComDetectTrigger();
        Console.WriteLine($"ConveyorComDetectTrigger 返回值: {rtn}");
        
    }

    private void ConveyorTest()
    {
        // Usar Invoke para actualizar los controles del hilo de la interfaz de usuario
        this.Invoke((MethodInvoker)delegate {
            Console.WriteLine("开始传送带测试...");
        });

        int retval = 0;
        int index = 1;
        int max_time = 30000;
        bool block = false;
        retval = 0;

        /* Flujo de agarre de la cinta transportadora */
        DescPose startdescPose = new DescPose(139.176f, 4.717f, 9.088f, -179.999f, -0.004f, -179.990f);
        JointPos startjointPos = new JointPos(-34.129f, -88.062f, 97.839f, -99.780f, -90.003f, -34.140f);

        DescPose homePose = new DescPose(139.177f, 4.717f, 69.084f, -180.000f, -0.004f, -179.989f);
        JointPos homejointPos = new JointPos(-34.129f, -88.618f, 84.039f, -85.423f, -90.003f, -34.140f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        // Moverse a la posición segura
        retval = robot.MoveL(homejointPos, homePose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);
        Console.WriteLine($"MoveL 到安全位置返回值: {retval}");

        // Detección de la cinta transportadora
        retval = robot.ConveryComDetect(1000 * 10);
        Console.WriteLine($"ConveyorComDetect 返回值: {retval}");

        // Obtener los datos de seguimiento
        retval = robot.ConveyorGetTrackData(2);
        Console.WriteLine($"ConveyorGetTrackData 返回值: {retval}");

        // Iniciar el seguimiento
        retval = robot.ConveyorTrackStart(2);
        Console.WriteLine($"ConveyorTrackStart 返回值: {retval}");

        // Moverse a la posición inicial
        robot.MoveL(startjointPos, startdescPose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);
        robot.MoveL(startjointPos, startdescPose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);

        // Finalizar el seguimiento
        retval = robot.ConveyorTrackEnd();
        Console.WriteLine($"ConveyorTrackEnd 返回值: {retval}");

        // Volver a la posición segura
        robot.MoveL(homejointPos, homePose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);

        this.Invoke((MethodInvoker)delegate {
            Console.WriteLine("传送带测试完成!");
            button3.Enabled = true;
        });
    }

Programa de ejemplo de operación de la cinta transportadora del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnConvert_Click(object sender, EventArgs e)
    {
        // Seguimiento de la cinta transportadora
        DescPose pos1 = new DescPose(-354.549, 63.914, 270.176, -179.679, -0.134, 2.468);
        DescPose pos2 = new DescPose(-351.203, -213.393, 351.054, -179.932, -0.508, 2.472);

        double[] cmp = { 0.0, 0.0, 0.0 };
        int rtn = robot.ConveyorCatchPointComp(cmp); // Establecer la compensación del punto de agarre de la cinta transportadora
        if (rtn != 0)
        {
            return;
        }
        Console.WriteLine("ConveyorCatchPointComp: rtn  " + rtn);

        rtn = robot.MoveCart(pos1, 1, 0, (float)30.0, (float)180.0, (float)100.0, (float)-1.0, -1);
        Console.WriteLine("MoveCart: rtn  " + rtn);

        rtn = robot.ConveyorIODetect(10000); // Detección IO de piezas en la cinta transportadora
        Console.WriteLine("ConveyorIODetect: rtn   " + rtn);

        robot.ConveyorGetTrackData(1); // Configurar el seguimiento de la cinta transportadora para el agarre
        rtn = robot.ConveyorTrackStart(1); // Iniciar el seguimiento
        Console.WriteLine("ConveyorTrackStart: rtn  " + rtn);

        rtn = robot.ConveyorTrackMoveL("cvrCatchPoint", 1, 0, (float)100.0, (float)0.0, (float)100.0, (float)-1.0, 0, 0);
        Console.WriteLine("ConveyorTrackMoveL: rtn  " + rtn);

        rtn = robot.MoveGripper(2, 30, 60, 30, 30000, 0, 0, 0, 50, 50);
        Console.WriteLine("ConveyorTrackMoveL: rtn  " + rtn);
            

        rtn = robot.ConveyorTrackMoveL("cvrRaisePoint", 1, 0, (float)100.0, (float)0.0, (float)100.0, (float)-1.0, 0, 0);
        Console.WriteLine("ConveyorTrackMoveL: rtn   " + rtn);

        rtn = robot.ConveyorTrackEnd(); // Detener el seguimiento de la cinta transportadora
        Console.WriteLine("ConveyorTrackEnd: rtn  " + rtn);

        rtn = robot.MoveCart(pos2, 1, 0, (float)30.0, (float)180.0, (float)100.0, (float)-1.0, -1);
        Console.WriteLine("MoveCart: rtn  " + rtn);

        rtn = robot.MoveGripper(2, 100, 60, 30, 30000, 0,0,0,50,50);
        Console.WriteLine("MoveGripper: rtn  " + rtn);

    }

Configuración del sensor del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Configuración del sensor del extremo
    * @param  [in] idCompany Fabricante, 18-JUNKONG; 25-HUIDE
    * @param  [in] idDevice Tipo, 0-JUNKONG/RYR6T.V1.0
    * @param  [in] idSoftware Versión del software, 0-J1.0/HuiDe1.0 (aún no disponible)
    * @param  [in] idBus Posición de montaje, 1-puerto 1 del extremo; 2-puerto 2 del extremo... 8-puerto 8 del extremo (aún no disponible)
    * @return  Código de error
    */
    int AxleSensorConfig(int idCompany, int idDevice, int idSoftware, int idBus);

Obtener la configuración del sensor del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la configuración del sensor del extremo
    * @param  [out] idCompany Fabricante, 18-JUNKONG; 25-HUIDE
    * @param  [out] idDevice Tipo, 0-JUNKONG/RYR6T.V1.0
    * @return  Código de error
    */
    int AxleSensorConfigGet(ref int idCompany, ref int idDevice);

Activación del sensor del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Activación del sensor del extremo
    * @param  [in] actFlag 0-restablecer; 1-activar
    * @return  Código de error
    */
    int AxleSensorActivate(int actFlag);

Escritura de registros del sensor del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Escritura de registros del sensor del extremo
    * @param  [in] devAddr  Número de dirección del dispositivo 0-255
    * @param  [in] regHAddr Dirección de registro, 8 bits altos
    * @param  [in] regLAddr Dirección de registro, 8 bits bajos
    * @param  [in] regNum  Número de registros 0-255
    * @param  [in] data1 Valor 1 a escribir en el registro
    * @param  [in] data2 Valor 2 a escribir en el registro
    * @param  [in] isNoBlock 0-bloqueante; 1-no bloqueante
    * @return  Código de error
    */
     int AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Ejemplo de código del sensor del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button2_Click_1(object sender, EventArgs e)
    {
        robot.AxleSensorConfig(18, 0, 0, 1);
        int company = -1;
        int type = -1;
        robot.AxleSensorConfigGet(ref company, ref type);
        Console.WriteLine("company is " + company + ", type is " + type);

        int rtn = robot.AxleSensorActivate(1);
        Console.WriteLine("AxleSensorActivate rtn is " + rtn);

        Thread.Sleep(1000);

        rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
        Console.WriteLine("AxleSensorRegWrite rtn is " + rtn);   
    }

Obtener el protocolo de periféricos del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener el protocolo de periféricos del robot
    * @param [out] protocol Número de protocolo de periféricos del robot 4096-tarjeta de control del eje extendido; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Código de error 
    */
    int GetExDevProtocol(ref int protocol);

Establecer el protocolo de periféricos del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el protocolo de periféricos del robot
    * @param [in] protocol Número de protocolo de periféricos del robot 4096-tarjeta de control del eje extendido; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Código de error 
    */
    int SetExDevProtocol(int protocol);

Programa de ejemplo de configuración del protocolo de periféricos del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnSetProto_Click(object sender, EventArgs e)
    {
      int protocol = 4096;
      int rtn = robot.SetExDevProtocol(protocol);
      Console.WriteLine("SetExDevProtocol rtn " + rtn);
      rtn = robot.GetExDevProtocol(ref protocol);
      Console.WriteLine("GetExDevProtocol rtn " + rtn + " protocol is: " + protocol);
    }

Obtener los parámetros de comunicación del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener los parámetros de comunicación del extremo
    * @param param Parámetros de comunicación del extremo
    * @return  Código de error
    */
    int GetAxleCommunicationParam(ref AxleComParam getParam);

Establecer los parámetros de comunicación del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer los parámetros de comunicación del extremo
    * @param param  Parámetros de comunicación del extremo
    * @return  Código de error
    */
    int SetAxleCommunicationParam(AxleComParam param);

Establecer el tipo de transferencia de archivos del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el tipo de transferencia de archivos del extremo
    * @param type 1-archivo de actualización de MCU; 2-archivo LUA
    * @return  Código de error
    */
    int SetAxleFileType(int type);

Establecer la habilitación de ejecución de LUA en el extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la habilitación de ejecución de LUA en el extremo
    * @param enable 0-no habilitar; 1-habilitar
    * @return  Código de error
    */
    int SetAxleLuaEnable(int enable);

Recuperación de errores anómalos del archivo LUA del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Recuperación de errores anómalos del archivo LUA del extremo
    * @param status 0-no recuperar; 1-recuperar
    * @return  Código de error
    */
    int SetRecoverAxleLuaErr(int status);

Obtener el estado de habilitación de ejecución de LUA en el extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado de habilitación de ejecución de LUA en el extremo
    * @param [out] status 0-no habilitado; 1-habilitado
    * @return  Código de error
    */
    int GetAxleLuaEnableStatus(ref int status);

Establecer el tipo de dispositivo del extremo habilitado para LUA en el extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el tipo de dispositivo del extremo habilitado para LUA en el extremo
    * @param [in] forceSensorEnable Estado de habilitación del sensor de fuerza, 0-no habilitar; 1-habilitar
    * @param [in] gripperEnable Estado de habilitación de la pinza, 0-no habilitar; 1-habilitar
    * @param [in] IOEnable Estado de habilitación del dispositivo IO, 0-no habilitar; 1-habilitar
    * @param [in] dexhandEnable Estado de habilitación del dispositivo mano diestra, 0-no habilitar; 1-habilitar
    * @return  Código de error
    */
    public int SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable, int dexhandEnable)

Obtener el tipo de dispositivo del extremo habilitado para LUA en el extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el tipo de dispositivo del extremo habilitado para LUA en el extremo
    * @param [out] forceSensorEnable Estado de habilitación del sensor de fuerza, 0-no habilitar; 1-habilitar
    * @param [out] gripperEnable Estado de habilitación de la pinza, 0-no habilitar; 1-habilitar
    * @param [out] IOEnable Estado de habilitación del dispositivo IO, 0-no habilitar; 1-habilitar
    * @param [out] dexhandEnable Estado de habilitación del dispositivo mano diestra, 0-no habilitar; 1-habilitar
    * @return  Código de error
    */
    public int GetAxleLuaEnableDeviceType(ref int forceSensorEnable, ref int gripperEnable, ref int IOEnable, ref int dexhandEnable)

Obtener el dispositivo del extremo configurado actualmente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el dispositivo del extremo configurado actualmente
    * @param [out] forceSensorEnable Número de dispositivo habilitado del sensor de fuerza 0-no habilitado; 1-habilitado
    * @param [out] gripperEnable Número de dispositivo habilitado de la pinza, 0-no habilitar; 1-habilitar
    * @param [out] IODeviceEnable Número de dispositivo habilitado del dispositivo IO, 0-no habilitar; 1-habilitar
    * @param [out] decHandEnable Número de dispositivo habilitado de la mano diestra, 0-no habilitar; 1-habilitar
    * @return  Código de error
    */
    public int GetAxleLuaEnableDevice(ref int[] forceSensorEnable, ref int[] gripperEnable, ref int[] IODeviceEnable, ref int[] decHandEnable)

Establecer la habilitación de la función de control de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la habilitación de la función de control de movimiento de la pinza
    * @param [in] id Número de dispositivo de la pinza
    * @param [in] func func[0]-habilitación de la pinza; func[1]-inicialización de la pinza; func[2]-establecimiento de posición; func[3]-establecimiento de velocidad; func[4]-establecimiento de par; func[6]-lectura del estado de la pinza;
        func[7]-lectura del estado de inicialización; func[8]-lectura del código de fallo; func[9]-lectura de posición; func[10]-lectura de velocidad; func[11]-lectura de par; func[12]-establecimiento del número de vueltas de la pinza rotativa; 
        func[13]-establecimiento de la velocidad de rotación de la pinza rotativa; func[14]-establecimiento del par de rotación de la pinza rotativa; func[15]-lectura del estado de la pinza rotativa; func[16]-lectura del estado de inicialización de la pinza rotativa;
        func[17]-lectura del número de vueltas de la pinza rotativa; func[18]-lectura de la velocidad de la pinza rotativa; func[19]-lectura del par de la pinza rotativa; func[20]-establecimiento del movimiento sincronizado multieje; func[21]-instrucción de borrado de fallos;
        func[22]-estado de funcionamiento de un solo eje; func[23]-estado de funcionamiento de todos los ejes;
    * @return  Código de error
    */
    public int SetAxleLuaGripperFunc(int id, int[] func)

Obtener la habilitación de la función de control de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la habilitación de la función de control de movimiento de la pinza
    * @param [in] id Número de dispositivo de la pinza
    * @param [out] func func[0]-habilitación de la pinza; func[1]-inicialización de la pinza; func[2]-establecimiento de posición; func[3]-establecimiento de velocidad; func[4]-establecimiento de par; func[6]-lectura del estado de la pinza;
        func[7]-lectura del estado de inicialización; func[8]-lectura del código de fallo; func[9]-lectura de posición; func[10]-lectura de velocidad; func[11]-lectura de par; func[12]-establecimiento del número de vueltas de la pinza rotativa; 
        func[13]-establecimiento de la velocidad de rotación de la pinza rotativa; func[14]-establecimiento del par de rotación de la pinza rotativa; func[15]-lectura del estado de la pinza rotativa; func[16]-lectura del estado de inicialización de la pinza rotativa;
        func[17]-lectura del número de vueltas de la pinza rotativa; func[18]-lectura de la velocidad de la pinza rotativa; func[19]-lectura del par de la pinza rotativa; func[20]-establecimiento del movimiento sincronizado multieje; func[21]-instrucción de borrado de fallos;
        func[22]-estado de funcionamiento de un solo eje; func[23]-estado de funcionamiento de todos los ejes;
    * @return  Código de error
    */
    public int GetAxleLuaGripperFunc(int id, ref int[] func) 

Escritura del archivo de esclavo Ethercat del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Escritura del archivo de esclavo Ethercat del robot
    * @param [in] type Tipo de archivo de esclavo, 1-actualizar archivo de esclavo; 2-actualizar archivo de configuración de esclavo
    * @param [in] slaveID Número de esclavo
    * @param [in] fileName Nombre del archivo a cargar
    * @return  Código de error
    */
    int SlaveFileWrite(int type, int slaveID, string fileName);

Cargar el archivo de protocolo abierto LUA del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Cargar el archivo de protocolo abierto LUA del extremo
    * @param filePath Ruta y nombre del archivo lua local ".../AXLE_LUA_End_DaHuan.lua"
    * @return Código de error 
    */
    int AxleLuaUpload(string filePath);

Entrada del esclavo Ethercat del robot en modo boot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Entrada del esclavo Ethercat del robot en modo boot
    * @return  Código de error
    */
    int SetSysServoBootMode();

Ejemplo de código de operación del archivo LUA del extremo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button41_Click(object sender, EventArgs e)
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_JunDuo_V0.4_20260602.lua");

        AxleComParam param = new AxleComParam(7, 8, 1, 0, 5, 3, 1);
        robot.SetAxleCommunicationParam(param);

        AxleComParam getParam = new AxleComParam();
        robot.GetAxleCommunicationParam(ref getParam);
        Console.WriteLine("GetAxleCommunicationParam param is {0} {1} {2} {3} {4} {5} {6}",
            getParam.baudRate, getParam.dataBit, getParam.stopBit, getParam.verify,
            getParam.timeout, getParam.timeoutTimes, getParam.period);

        robot.SetAxleLuaEnable(1);
        int luaEnableStatus = 0;
        robot.GetAxleLuaEnableStatus(ref luaEnableStatus);
        robot.SetAxleLuaEnableDeviceType(0, 1, 0, 0);

        int forceEnable = 0;
        int gripperEnable = 0;
        int ioEnable = 0;
        int dexhandEnable = 0;
        robot.GetAxleLuaEnableDeviceType(ref forceEnable, ref gripperEnable, ref ioEnable, ref dexhandEnable);
        Console.WriteLine("GetAxleLuaEnableDeviceType param is {0} {1} {2}", forceEnable, gripperEnable, ioEnable);

        int[] func = { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
        robot.SetAxleLuaGripperFunc(1, func);

        int[] getFunc = new int[32];
        robot.GetAxleLuaGripperFunc(1, ref getFunc);
        int[] getforceEnable = new int[16];
        int[] getgripperEnable = new int[16];
        int[] getioEnable = new int[16];
        int[] dexhandEnable1 = new int[16];
        robot.GetAxleLuaEnableDevice(ref getforceEnable, ref getgripperEnable, ref getioEnable,ref dexhandEnable1);
        Console.WriteLine("\ngetforceEnable status : ");
        foreach (int i in getforceEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine("\ngetgripperEnable status : ");
        foreach (int i in getgripperEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine("\ngetioEnable status : ");
        foreach (int i in getioEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine();
        robot.ActGripper(1, 0);
        Thread.Sleep(3000);
        robot.ActGripper(1, 1);
        Thread.Sleep(4000);
        robot.MoveGripper(1, 50, 10, 100, 50000, 0, 0, 0, 0, 0);
        int pos = 0;
        while (true)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine("gripper pos is " + pkg.gripper_position);
            Thread.Sleep(100);
        }
    } 

Obtener el estado de los botones de SmartTool
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado de los botones de SmartTool
    * @param [out] state Estado de los botones del mango SmartTool; (bit0:0-comunicación normal; 1-comunicación interrumpida; bit1-deshacer operación; bit2-vaciar programa;
        bit3-tecla A; bit4-tecla B; bit5-tecla C; bit6-tecla D; bit7-tecla E; bit8-tecla IO; bit9-manual/automático; bit10-iniciar)
    * @return Código de error
    */
    int GetSmarttoolBtnState(ref int state);

Ejemplo de código
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void button11_Click(object sender, EventArgs e)
    {

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        int state = 0;
        while (true)
        {
            int rtn = robot.GetSmarttoolBtnState(ref state);
            string binaryString = Convert.ToString(state, 2).PadLeft(32, '0');
            Console.WriteLine($"GetSmarttoolBtnState rtn (binary): {binaryString}");
            Thread.Sleep(100);
        }

    }

Cargar el archivo Lua de protocolo abierto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Cargar el archivo Lua de protocolo abierto
    * @param  filePath Ruta y nombre del archivo lua de protocolo abierto local
    * @return Código de error
    */
    public int OpenLuaUpload(string filePath)


Obtener los parámetros de la placa de esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener los parámetros de la placa de esclavo
    * @param  type  0-Ethercat, 1-CClink, 3-Ethercat, 4-EIP
    * @param  version  Versión del protocolo
    * @param  connState  0-no conectado 1-conectado
    * @return  Código de error
    */
    public int GetFieldBusConfig(int[] type, int[] version, int[] connState)

Escribir DO del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Escribir DO del esclavo
    * @param   DOIndex  Número de DO
    * @param   wirteNum  Cantidad a escribir
    * @param   status Valores a escribir, máximo 8
    * @return  Código de error
    */
    public int FieldBusSlaveWriteDO(int DOIndex, int wirteNum, int[] status)

Escribir AO del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Escribir AO del esclavo
    * @param [in] AOIndex Número de AO
    * @param [in] wirteNum Cantidad a escribir
    * @param [in] status Array de valores a escribir (máximo 8); AO0~AO15 son enteros, AO16~AO31 son flotantes
    * @return Código de error
    */
    public int FieldBusSlaveWriteAO(int AOIndex, int wirteNum, double[] status)

Leer DI del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Leer DI del esclavo
    * @param  DOIndex  Número de DI
    * @param  readNum  Cantidad a leer
    * @param  status Valores leídos, máximo 8
    * @return  Código de error
    */
    public int FieldBusSlaveReadDI(int DOIndex, int readNum, int[] status)

Leer AI del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Leer AI del esclavo
    * @param  AIIndex  Número de AI
    * @param  readNum  Cantidad a leer
    * @param  status Valores leídos, máximo 8
    * @return  Código de error
    */
    public int FieldBusSlaveReadAI(int AIIndex, int readNum, double[] status)

Esperar la entrada DI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Esperar la entrada DI extendida
    * @param  DIIndex Número de DI
    * @param  status 0-nivel bajo; 1-nivel alto
    * @param  waitMs Tiempo máximo de espera (ms)
    * @return Código de error
    */
    public int FieldBusSlaveWaitDI(int DIIndex, int status, int waitMs)

Esperar la entrada AI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Esperar la entrada AI extendida
    * @param  AIIndex Número de AI
    * @param  waitType 0-mayor que; 1-menor que
    * @param  value Valor de AI
    * @param  waitMs Tiempo máximo de espera (ms)
    * @return Código de error
    */
    public int FieldBusSlaveWaitAI(int AIIndex, int waitType, double value, int waitMs)

Ejemplo de código de instrucciones relacionadas con el modo esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button101_Click(object sender, EventArgs e)
    {
        int rtn = 0;
    
        int type = 0, version = 0, connState = 0;
        int[] ctrl = new int[8];
        double[] ctrlAO = new double[8];
        int[] DI = new int[8];
        double[] AI = new double[8];
        if (rtn != 0)
        {
            return;
        }
        // Cargar y aplicar el archivo de protocolo abierto
        robot.OpenLuaUpload("E://temp /CtrlDev_field.lua");
        Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        Thread.Sleep(8000);
    
        // Obtener el tipo de protocolo, la versión del software y el estado de conexión con el PLC
        robot.GetFieldBusConfig(ref type, ref version, ref connState);
        Console.WriteLine($"type is {type}, version is {version}, connState is {connState}");
    
        // Escribir DO0 = 1, DO1 = 0, DO2 = 1
        ctrl[0] = 1;
        ctrl[1] = 0;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);
    
        // Escribir AO2 = 0x1000
        ctrlAO[0] = 0x1000;
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO);

        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, ref DI);
            Console.WriteLine($"DI0 is {DI[0]}, DI1 is {DI[1]}, DI2 is {DI[2]}, DI3 is {DI[3]}");
            robot.FieldBusSlaveReadAI(0, 3, ref AI);
            Console.WriteLine($"AI0 is {AI[0]}, AI1 is {AI[1]}, AI2 is {AI[2]}");
            Thread.Sleep(10);
        }
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        Console.WriteLine($"FieldBusSlaveWaitDI result is {ret}");

        ret = robot.FieldBusSlaveWaitAI(0, 0, 400.00f, 100);
        Console.WriteLine($"FieldBusSlaveWaitAI result is {ret}"); 
    }

Control de la ventosa en matriz
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Control de la ventosa en matriz
    * @param  slaveID Número de esclavo
    * @param  len Longitud
    * @param  ctrlValue Valor de control 1-aspirar con el vacío máximo 2-aspirar con el vacío configurado 3-detener la aspiración
    * @return Código de error
    */
    public int SetSuckerCtrl(int slaveID, int len, int[] ctrlValue)

Obtener el estado de la ventosa en matriz
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado de la ventosa en matriz
    * @param  slaveID Número de esclavo
    * @param  state Estado de aspiración 0-liberar objeto 1-detección de aspiración de pieza correcta 2-no se ha aspirado ningún objeto 3-objeto desprendido
    * @param  pressValue Vacío actual, unidad kpa
    * @param  error Código de error actual de la ventosa
    * @return Código de error
    */
    public int GetSuckerState(int slaveID, int[] state, int[] pressValue, int[] error)

Esperar el estado de la ventosa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Esperar el estado de la ventosa
    * @param  slaveID Número de esclavo
    * @param  state Estado de aspiración 0-liberar objeto 1-detección de aspiración de pieza correcta 2-no se ha aspirado ningún objeto 3-objeto desprendido
    * @param  ms Tiempo máximo de espera
    * @return Código de error
    */
    public int WaitSuckerState(int slaveID, int state, int ms)

Ejemplo de código de instrucciones de control de la ventosa en matriz
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void TestSucker(Robot robot)
    {
    
        int[] ctrl = new int[20];
        int state=0;
        int pressValue=0;
        int error=0;
        int rtn;
    
    
        // Cargar y aplicar el archivo de protocolo abierto
        robot.OpenLuaUpload(@"C:\SDK\CtrlDev_sucker.lua");
        Thread.Sleep(2000);
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        Thread.Sleep(1000);
    
        // Controlar la ventosa en modo difusión con la capacidad de aspiración máxima
        ctrl[0] = 1;
        robot.SetSuckerCtrl(0, 1, ctrl);
    
        // Supervisar en bucle los estados de la ventosa 1 y la ventosa 12
        for (int i = 0; i < 100; i++)
        {
            robot.GetSuckerState(1, ref state, ref pressValue, ref error);
            Console.WriteLine($"sucker1 state is {state}, pressValue is {pressValue}, error num is {error}");
            robot.GetSuckerState(12, ref state, ref pressValue, ref error);
            Console.WriteLine($"sucker12 state is {state}, pressValue is {pressValue}, error num is {error}");
            Thread.Sleep(100);
        }
        // Esperar a que la ventosa 1 alcance el estado de aspiración, tiempo de espera 100 ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        Console.WriteLine($"WaitSuckerState result is {ret}");
    
        // Modo unidifusión para apagar las ventosas 1 y 12
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);
    
        robot.CloseRPC();
    }

Función de encendido y apagado del periférico láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Función de encendido y apagado del periférico láser
     * @param [in] OnOff 0-apagar 1-encender
     * @param [in] weldId ID de la soldadura, por defecto 0
     * @return Código de error
     */
    public int LaserTrackingLaserOnOff(int OnOff, int weldId)
    
Función de inicio y fin del seguimiento láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    
    /**
     * @brief Función de inicio y fin del seguimiento láser
     * @param [in] OnOff 0-finalizar 1-iniciar
     * @param [in] coordId Número del sistema de coordenadas de herramienta del periférico láser
     * @return Código de error
     */
    public int LaserTrackingTrackOnOff(int OnOff, int coordId)

Búsqueda de posición láser - dirección fija
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Búsqueda de posición láser - dirección fija
     * @param [in] direction 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
     * @param [in] vel Velocidad en %
     * @param [in] distance Distancia máxima de búsqueda de posición en mm
     * @param [in] timeout Tiempo de espera agotado de la búsqueda de posición en ms
     * @param [in] posSensorNum Número del sistema de coordenadas de herramienta de calibración láser
     * @return Código de error
     */
    public int LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum)
    
Búsqueda de posición láser - dirección arbitraria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Búsqueda de posición láser - dirección arbitraria
     * @param [in] directionPoint Coordenadas xyz del punto introducido para la búsqueda de posición
     * @param [in] vel Velocidad en %
     * @param [in] distance Distancia máxima de búsqueda de posición en mm
     * @param [in] timeout Tiempo de espera agotado de la búsqueda de posición en ms
     * @param [in] posSensorNum Número del sistema de coordenadas de herramienta de calibración láser
     * @return Código de error
     */
    public int LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum)
   
Fin de la búsqueda de posición láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
    * @brief  Fin de la búsqueda de posición láser
    * @return Código de error
    */
    public int LaserTrackingSearchStop()

Configuración de la IP del láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Configuración de la IP del láser
     * @param [in] ip Dirección IP del periférico láser
     * @param [in] port Número de puerto del periférico láser
     * @return Código de error
     */
    public int LaserTrackingSensorConfig(string ip, int port)

Configuración del período de muestreo del periférico láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Configuración del período de muestreo del periférico láser
     * @param [in] period Período de muestreo del periférico láser en ms
     * @return Código de error
     */
    public int LaserTrackingSensorSamplePeriod(int period)

Carga del controlador del periférico láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Carga del controlador del periférico láser
     * @param [in] type Tipo de protocolo del controlador del periférico láser 101-Ruiniu 102-Chuangxiang 103-Quanshi 104-Tongzhou 105-Aotai
     * @return Código de error
     */
    public int LoadPosSensorDriver(int type)

Descarga del controlador del periférico láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Descarga del controlador del periférico láser
     * @return Código de error
     */
    public int UnLoadPosSensorDriver()

Registro de la trayectoria de soldadura láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Registro de la trayectoria de soldadura láser
     * @param [in] status 0-detener el registro 1-seguimiento en tiempo real  2-iniciar el registro
     * @param [in] delayTime Tiempo de retardo en ms
     * @return Código de error
     */
    public int LaserSensorRecord1(int status, int delayTime)

Reproducción de la trayectoria de soldadura láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Reproducción de la trayectoria de soldadura láser
     * @param [in] delayTime Tiempo de retardo en ms
     * @param [in] speed Velocidad en %
     * @return Código de error
     */
    public int LaserSensorReplay(int delayTime, double speed)

Reproducción del seguimiento láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Reproducción del seguimiento láser
     * @return Código de error
     */
    public int MoveLTR()

Registro y reproducción de la trayectoria de soldadura láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Registro y reproducción de la trayectoria de soldadura láser
    * @param [in] delayMode Modo 0-tiempo de retardo 1-distancia de retardo
    * @param [in] delayTime Tiempo de retardo en ms
    * @param [in] delayDisExAxisNum Número del eje extendido
    * @param [in] delayDis Distancia de retardo en mm
    * @param [in] sensitivePara Coeficiente de sensibilidad de compensación
    * @param [in] trackMode Tipo de seguimiento en punto fijo. 0-movimiento asíncrono del eje extendido; 1-robot
    * @param [in] triggerMode Modo de disparo del seguimiento en punto fijo. 0-duración del seguimiento; 1-IO
    * @param [in] runTime Duración del seguimiento en punto fijo del robot (s)
    * @param [in] speed Velocidad en %
    * @return Código de error
    */
    public int LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum,double delayDis, double sensitivePara, int trackMode, int triggerMode,double runTime, double speed)
    
Moverse al punto inicial del registro de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Moverse al punto inicial del registro de soldadura
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl Velocidad en %
     * @return Código de error
     */
    public int MoveToLaserRecordStart(int moveType, double ovl)

Moverse al punto final del registro de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Moverse al punto final del registro de soldadura
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl Velocidad en %
     * @return Código de error
     */
    public int MoveToLaserRecordEnd(int moveType, double ovl)

Moverse al punto de búsqueda de posición del sensor láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Moverse al punto de búsqueda de posición del sensor láser
     * @param [in] moveFlag Tipo de movimiento: 0-PTP; 1-LIN
     * @param [in] ovl Factor de escala de velocidad, 0-100
     * @param [in] dataFlag Selección de datos de caché de soldadura: 0-ejecutar datos planificados; 1-ejecutar datos registrados
     * @param [in] plateType Tipo de placa: 0-placa ondulada; 1-placa corrugada; 2-placa de cerca; 3-barril de petróleo; 4-acero corrugado con caparazón
     * @param [in] trackOffectType Tipo de desplazamiento del sensor láser: 0-sin desplazamiento; 1-desplazamiento en el sistema de coordenadas base; 2-desplazamiento en el sistema de coordenadas de herramienta; 3-desplazamiento de los datos brutos del sensor láser
     * @param [in] offset Magnitud del desplazamiento
     * @return Código de error
     */
    public int MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset)
    
Obtener la información de coordenadas del punto de búsqueda de posición del sensor láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Obtener la información de coordenadas del punto de búsqueda de posición del sensor láser
     * @param [in] trackOffectType Tipo de desplazamiento del sensor láser: 0-sin desplazamiento; 1-desplazamiento en el sistema de coordenadas base; 2-desplazamiento en el sistema de coordenadas de herramienta; 3-desplazamiento de los datos brutos del sensor láser
     * @param [in] offset Magnitud del desplazamiento
     * @param [out] jPos Posición articular [°]
     * @param [out] descPos Posición cartesiana [mm]
     * @param [out] tool Sistema de coordenadas de herramienta
     * @param [out] user Sistema de coordenadas de pieza
     * @param [out] exaxis Posición del eje extendido [mm]
     * @return Código de error
     */
    public int GetLaserSeamPos(int trackOffectType, DescPose offset, ref JointPos jPos, ref DescPose descPos, ref int tool, ref int user, ref ExaxisPos exaxis)

Ejemplo de código de configuración y depuración de parámetros del sensor del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    void testLaserConfig()
    {
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);
        robot.LaserTrackingLaserOnOff(0, 0);
        System.Threading.Thread.Sleep(3000);
        robot.LaserTrackingLaserOnOff(1, 0);
    }

Ejemplo de código de escaneo de trayectoria láser y reproducción de trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    void testLaserRecordAndReplay()
    { 
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        System.Threading.Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        System.Threading.Thread.Sleep(8000);
        for (int i=0;i<10;++i)
        {
            JointPos startjointPos = new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose = new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
            DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserSensorRecord1(2, 10);

            JointPos endjointPos = new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose = new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 50, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);

            robot.LaserSensorRecord1(0, 10);
            robot.MoveToLaserRecordStart(1, 30);
            robot.LaserSensorReplay(10, 100);
            robot.MoveLTR();
            robot.LaserSensorRecord1(0, 10);
            Console.WriteLine($"Number of completions : {i+1} ");
        }
                
    }

Ejemplo de código de búsqueda de posición láser y seguimiento en tiempo real
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    public static void testLasertrack()
    {
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        System.Threading.Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        System.Threading.Thread.Sleep(8000);
        for (int i = 0; i < 10; ++i)
        {
            JointPos startjointPos = new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose = new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
            DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
            DescTran directionPoint = new DescTran();

            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3);
            robot.LaserTrackingSearchStop();
            robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);

            robot.LaserTrackingTrackOnOff(1, 3);

            JointPos endjointPos = new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose = new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserTrackingTrackOnOff(0, 3);
            Console.WriteLine($"Number of completions : {i + 1} ");
        }
    }

Ejemplo de código de seguimiento láser sincronizado con el eje extendido y el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    public void TestLaserTrackAndExitAxis()
    {   
        ExaxisPos startexaxisPos = new ExaxisPos(0, 0, 0, 0);
        ExaxisPos seamexaxisPos = new ExaxisPos(-10, 0, 0, 0);
        ExaxisPos endexaxisPos = new ExaxisPos(-30, 0, 0, 0);      
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);     
        JointPos startjointPos = new JointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
        DescPose startdescPose = new DescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
        for (int i=0;i<10;++i)
        {
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);
            Console.WriteLine("11111");
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            Console.WriteLine("2222");
            int tool = 0;
            int user = 0;
            JointPos seamjointPos = new JointPos();
            DescPose seamdescPose = new DescPose();
            robot.GetLaserSeamPos(0, offdese, ref seamjointPos, ref seamdescPose, ref tool, ref user, ref startexaxisPos);
            Console.WriteLine($"{seamjointPos.jPos[0]}, {seamjointPos.jPos[1]}, {seamjointPos.jPos[2]}, " +
                            $"{seamjointPos.jPos[3]}, {seamjointPos.jPos[4]}, {seamjointPos.jPos[5]}, " +
                            $"{seamdescPose.tran.x}, {seamdescPose.tran.y}, {seamdescPose.tran.z}, " +
                            $"{seamdescPose.rpy.rx}, {seamdescPose.rpy.ry}, {seamdescPose.rpy.rz}");
            if (ret == 0)
            {
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);
                Console.WriteLine("3333");
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos = new JointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose = new DescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);
                robot.LaserTrackingTrackOnOff(0, 2);
            }
            Console.WriteLine($"Number of completions : {i + 1} ");
        }     
    }

Ejemplo de código de registro y reproducción láser + oscilación convencional
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    void TestLaserReproduceNormalWeave()
    {
        JointPos startjointPos = new JointPos(69.655, -71.524, -119.568, -76.454, 91.188, 138.014);
        DescPose startdescPose = new DescPose(214.765, 311.139, 41.255, 7.693, -0.287, 37.080);
        JointPos endjointPos = new JointPos(58.803, -79.528, -113.688, -74.599, 91.637, 127.167);
        DescPose enddescPose = new DescPose(294.942, 311.153, 41.302, 7.701, -0.283, 37.081);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        int rtn = 0;

        // WaitMs(1000)
        Thread.Sleep(1000);

        // MoveL a la posición inicial (eje extendido 0,174.957,0,0)
        rtn = robot.MoveL(startjointPos, startdescPose, 5, 0, 100, 100, 100, -1, 0, new ExaxisPos(0, 174.957, 0, 0), 0, 0, offdese, 100, 0, 0, 10);

        Console.WriteLine($"MoveL start: {rtn}");

        // Iniciar el registro láser
        rtn = robot.LaserSensorRecord1(2, 10);
        Console.WriteLine($"LaserSensorRecord start: {rtn}");

        // MoveL a la posición final
        rtn = robot.MoveL(endjointPos, enddescPose, 5, 0, 100, 100, 100, -1, 0, new ExaxisPos(0, 174.957, 0, 0), 0, 0, offdese, 100, 0, 0, 10);
        Console.WriteLine($"MoveL end: {rtn}");

        // Detener el registro láser
        rtn = robot.LaserSensorRecord1(0, 10);
        Console.WriteLine($"LaserSensorRecord stop: {rtn}");

        // MoveL de vuelta a la posición inicial
        rtn = robot.MoveL(startjointPos, startdescPose, 5, 0, 100, 100, 100, -1, 0, new ExaxisPos(0, 174.957, 0, 0), 0, 0, offdese, 100, 0, 0, 10);
        Console.WriteLine($"MoveL back: {rtn}");

        // Movimiento LIN al inicio de la ruta de registro láser
        rtn = robot.MoveToLaserRecordStart(1, 30);
        Console.WriteLine($"MoveToLaserRecordStart: {rtn}");

        // Iniciar la oscilación convencional
        rtn = robot.WeaveStart(0);
        Console.WriteLine($"WeaveStart: {rtn}");

        // Iniciar la reproducción del registro
        rtn = robot.LaserSensorRecord1(3, 10);
        Console.WriteLine($"LaserSensorRecord replay: {rtn}");

        // Movimiento de reproducción del seguimiento láser
        rtn = robot.MoveLTR();
        Console.WriteLine($"MoveLTR: {rtn}");
        Thread.Sleep(3000);

        // Detener la reproducción del registro
        rtn = robot.LaserSensorRecord1(0, 10);
        Console.WriteLine($"LaserSensorRecord stop: {rtn}");

        // Finalizar la oscilación convencional
        rtn = robot.WeaveEnd(0);
        Console.WriteLine($"WeaveEnd: {rtn}");
    }

Ejemplo de código de registro y reproducción láser + movimiento asíncrono del eje extendido + oscilación en punto fijo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    void TestLaserRecordReplayExaxisWithWave()
    {
        JointPos startjointPos = new JointPos(106.245, -63.397, -93.331, -80.809, 80.389, 134.561);
        DescPose startdescPose = new DescPose(33.534, 516.527, 371.029, 14.712, -31.379, 71.734);
        JointPos endjointPos = new JointPos(105.534, -64.685, -93.681, -79.071, 80.772, 133.952);
        DescPose enddescPose = new DescPose(33.536, 528.536, 364.924, 14.712, -31.379, 71.734);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        int rtn = 0;

        // MoveJ al punto seguro (eje extendido 0,174.957,0,0)
        rtn = robot.MoveJ(startjointPos, startdescPose, 5, 0, 100, 100, 50, new ExaxisPos(0, 174.957, 0, 0), -1, 0, offdese);
        Console.WriteLine($"MoveJ start: {rtn}");

        // Movimiento asíncrono del eje extendido al punto inicial 105.003
        rtn = robot.ExtAxisMove(new ExaxisPos(0, 105.003, 0, 0), 50, -1);
        Console.WriteLine($"ExtAxisMove 105.003: {rtn}");
        Thread.Sleep(3000);

        // MoveL al punto inicial
        rtn = robot.MoveL(endjointPos, enddescPose, 5, 0, 100, 100, 50, -1, 0, new ExaxisPos(0, 105.003, 0, 0), 0, 0, offdese, 100, 0, 0, 10);
        Console.WriteLine($"MoveL end: {rtn}");

        // Iniciar el registro láser
        rtn = robot.LaserSensorRecord1(2, 10);
        Console.WriteLine($"LaserSensorRecord start: {rtn}");

        // El eje extendido se mueve a 174.957 durante el registro
        rtn = robot.ExtAxisMove(new ExaxisPos(0, 174.957, 0, 0), 50, -1);
        Console.WriteLine($"ExtAxisMove 174.957: {rtn}");
        Thread.Sleep(3000);

        // Detener el registro láser
        rtn = robot.LaserSensorRecord1(0, 10);
        Console.WriteLine($"LaserSensorRecord stop: {rtn}");


        // El eje extendido vuelve a 105.003, MoveL de vuelta al punto inicial
        rtn = robot.ExtAxisMove(new ExaxisPos(0, 105.003, 0, 0), 50, -1);
        Console.WriteLine($"ExtAxisMove back: {rtn}");

        // MoveL al punto inicial
        rtn = robot.MoveL(endjointPos, enddescPose, 5, 0, 100, 100, 50, -1, 0, new ExaxisPos(0, 105.003, 0, 0), 0, 0, offdese, 100, 0, 0, 10);
        Console.WriteLine($"MoveL back: {rtn}");

        // Movimiento PTP al inicio de la ruta de registro láser
        rtn = robot.MoveToLaserRecordStart(0, 30);
        Console.WriteLine($"MoveToLaserRecordStart: {rtn}");

        // Iniciar la reproducción
        rtn = robot.LaserSensorRecord1(3, 10);
        Console.WriteLine($"LaserSensorRecord replay: {rtn}");

        // Iniciar la oscilación en punto fijo
        DescPose refPoint = new DescPose(61.087, 512.431, 370.523, 14.335, -31.333, 69.014);
        rtn = robot.OriginPointWeaveStart(0, 1, refPoint, 5);
        Console.WriteLine($"OriginPointWeaveStart: {rtn}");

        // El eje extendido se mueve a 174.957 durante la oscilación
        rtn = robot.ExtAxisMove(new ExaxisPos(0, 174.957, 0, 0), 50, -1);
        Console.WriteLine($"ExtAxisMove replay: {rtn}");

        // Finalizar la oscilación
        rtn = robot.OriginPointWeaveEnd();
        Console.WriteLine($"OriginPointWeaveEnd: {rtn}");

        // Detener la reproducción
        rtn = robot.LaserSensorRecord1(0, 10);
        Console.WriteLine($"LaserSensorRecord stop: {rtn}");
    }

Activación y desactivación de la función de transmisión transparente del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Activar la función de transmisión transparente general del extremo
    * @param [in] habilitación, 0-desactivar, 1-activar
    * @return Código de error
    */
    public int SetAxleGenComEnable(int mode)

Envío y recepción de datos no periódicos de la función de transmisión transparente del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief El extremo envía datos no periódicos y espera la respuesta
    * @param [in]  len_snd，longitud enviada
    * @param [in]  sndBuff[]，datos enviados
    * @param [in]  len_rcv，longitud de recepción seleccionada
    * @param [out]  rcvBuff[]，datos de respuesta
    * @return Código de error
    */
    public int SndRcvAxleGenComCmdData(int len_snd, int[] sndBuff, int len_rcv, ref int[] rcvdata)

Ejemplo de código de comunicación de datos no periódicos del cabezal de moxibustión Beiyikang basado en la función de transmisión transparente del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void testAxleGenCom()
    {
        int[] led_on = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79 };
        int[] led_off = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
        int[] version = new int[5]{ 0xAB, 0xBA, 0x11, 0x00, 0x76 };
        int[] state = new int[6] { 0xAB, 0xBA, 0x1B,0x01, 0xAA, 0x2B };
        int[] cycleState = new int[6] { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };

        int[] rcvdata = new int[16];
        int ret = 0;
        int cnt = 1;

        JointPos p1Joint = new JointPos(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
        DescPose p1Desc = new DescPose(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);

        JointPos p2Joint = new JointPos(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
        DescPose p2Desc = new DescPose(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        //Activar la función de transmisión transparente del extremo
        robot.SetAxleGenComEnable(1);
        robot.SetAxleLuaEnable(1);

        while(cnt<=10)
        { 
            //Leer el número de versión
            ret = robot.SndRcvAxleGenComCmdData(5, version, 10, ref rcvdata);
            Console.WriteLine($" hard version : {rcvdata[4]},hard code:{rcvdata[5]}, soft version:{rcvdata[6]} {rcvdata[7]}, soft code:{rcvdata[8]}");
            if (ret != 0)
            {
                break;
            }
            Thread.Sleep(1000);
            //Leer el estado de presencia del cabezal de moxibustión
            ret = robot.SndRcvAxleGenComCmdData(6, state, 6, ref rcvdata);
            Console.WriteLine($" state : {rcvdata[4]}");
            Thread.Sleep(1000);
            //Encender el láser del cabezal de moxibustión
            ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, ref rcvdata);
            Console.WriteLine($"led on rcv data is: {rcvdata[0]},{rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}");
            robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
            Thread.Sleep(4000);
            //Apagar el láser del cabezal de moxibustión
            ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, ref rcvdata);
            Console.WriteLine($"led off rcv data is: {rcvdata[0]},{rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}");
            robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
            Thread.Sleep(1000);
            Console.WriteLine($"***********************complate No. {cnt}  SDK test*****************************");
            cnt++;
        }

    }

Descargar el archivo Lua de protocolo abierto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Descargar el archivo Lua de protocolo abierto
    * @param [in] fileName Nombre del archivo de protocolo abierto "CtrlDev_XXX.lua"
    * @param [in] savePath Ruta del archivo de guardado del protocolo abierto
    * @return Código de error
    */
    public int OpenLuaDownload(string fileName, string savePath)
    
Eliminar el archivo Lua de protocolo abierto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Eliminar el archivo Lua de protocolo abierto
    * @param [in] fileName Nombre del archivo lua de protocolo abierto a eliminar "CtrlDev_XXX.lua"
    * @return Código de error
    */
    public int OpenLuaDelete(string fileName)
        
Eliminar todos los archivos Lua de protocolo abierto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Eliminar todos los archivos Lua de protocolo abierto
    * @return Código de error
    */
    public int AllOpenLuaDelete()

Ejemplo de código SDK de operación de archivos Lua de protocolo abierto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public int TestCtrlOpenLuaOperate()
    {
        int rtn;

        // Cargar el archivo Lua al robot
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua");
        Console.WriteLine($"OpenLuaUpload rtn is {rtn}");
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua");
        Console.WriteLine($"OpenLuaUpload rtn is {rtn}");

        // Descargar el archivo Lua desde el robot
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/");
        Console.WriteLine($"OpenLuaDownload rtn is {rtn}");
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/");
        Console.WriteLine($"OpenLuaDownload rtn is {rtn}");

        // Establecer el nombre del Lua de protocolo abierto de control
        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua");
        Console.WriteLine($"SetCtrlOpenLUAName rtn is {rtn}");
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua");
        Console.WriteLine($"SetCtrlOpenLUAName rtn is {rtn}");

        // Obtener el nombre del Lua de protocolo abierto de control
        string[] name = new string[4];
        rtn = robot.GetCtrlOpenLUAName(ref name);
        Console.WriteLine($"ctrl open lua names : {name[0]}, {name[1]}, {name[2]}, {name[3]}");

        // Cargar y descargar el Lua de protocolo abierto
        rtn = robot.LoadCtrlOpenLUA(1);
        Console.WriteLine($"LoadCtrlOpenLUA rtn is {rtn}");
        robot.Sleep(2000);
        rtn = robot.UnloadCtrlOpenLUA(1);
        Console.WriteLine($"UnloadCtrlOpenLUA rtn is {rtn}");

        // Eliminar el archivo Lua especificado y todos los archivos Lua
        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua");
        Console.WriteLine($"OpenLuaDelete rtn is {rtn}");
        rtn = robot.AllOpenLuaDelete();
        Console.WriteLine($"AllOpenLuaDelete rtn is {rtn}");

        return 0;
    }

Control del movimiento de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:    

    /**
    * @brief  Control del movimiento de la mano diestra
    * @param  [in] idstart  Número de esclavo inicial
    * @param  [in] slaveNum  Cantidad
    * @param  [in] pos[16]  Posición (-360~360) 
    * @param  [in] speed[16]  Porcentaje de velocidad, rango [0~100]
    * @param  [in] force[16]  Porcentaje de par, rango [0~100]
    * @param  [in] max_time  Tiempo máximo de espera, rango [0~30000], unidad ms
    * @return  Código de error
    */
    public int SetDexterousHandsMove(int idstart, int slaveNum, double[] pos, int[] speed, int[] force, int max_time)
    
Control del restablecimiento y activación de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:   

    /**
    * @brief  Control del restablecimiento y activación de la mano diestra
    * @param  [in] id  Número de esclavo
    * @param  [in] act  0-restablecer 1-activar
    * @return  Código de error
    */
    public int SetDexterousHandsAct(int id, int act)
    
Borrado de errores de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:   

    /**
    * @brief  Borrado de errores de la mano diestra
    * @return  Código de error
    */
    public int ClearDexterousHandsError()
    
Establecer la habilitación de la función de control de movimiento de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:   

    /**
    * @brief Establecer la habilitación de la función de control de movimiento de la mano diestra
    * @param [in] id Número de esclavo de la mano diestra
    * @param [in] 0-disparo de agarre, 1-inicialización de la pinza, 2-establecimiento de posición, 3-establecimiento de velocidad, 4-establecimiento de par, 6-lectura del estado de la pinza, 7-lectura del estado de inicialización, 8-lectura del código de fallo, 9-lectura de posición, 10-lectura de velocidad, 11-lectura de par, 12-establecimiento del número de vueltas de rotación, 13-establecimiento de la velocidad de rotación, 14-establecimiento del par de rotación, 15-lectura del estado de la pinza rotativa, 16-lectura del estado de inicialización de la rotación, 17-lectura del número de vueltas de rotación, 18-lectura de la velocidad de rotación, 19-lectura del par de rotación, 20-establecimiento del movimiento sincronizado multieje, 21-instrucción de borrado de fallos, 22-estado de funcionamiento de un solo eje, 23-estado de funcionamiento de todos los ejes
    * @return  Código de error
    */
    public int SetDexterousHandsFunc(int id, int[] func)
    
Obtener la habilitación de la función de control de movimiento de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:   

    /**
    * @brief Obtener la habilitación de la función de control de movimiento de la mano diestra
    * @param [in] id Número de dispositivo de la mano diestra
    * @param [out]0-disparo de agarre, 1-inicialización de la pinza, 2-establecimiento de posición, 3-establecimiento de velocidad, 4-establecimiento de par, 6-lectura del estado de la pinza, 7-lectura del estado de inicialización, 8-lectura del código de fallo, 9-lectura de posición, 10-lectura de velocidad, 11-lectura de par, 12-establecimiento del número de vueltas de rotación, 13-establecimiento de la velocidad de rotación, 14-establecimiento del par de rotación, 15-lectura del estado de la pinza rotativa, 16-lectura del estado de inicialización de la rotación, 17-lectura del número de vueltas de rotación, 18-lectura de la velocidad de rotación, 19-lectura del par de rotación, 20-establecimiento del movimiento sincronizado multieje, 21-instrucción de borrado de fallos, 22-estado de funcionamiento de un solo eje, 23-estado de funcionamiento de todos los ejes
    */
    public int GetDexterousHandsFunc(int id, ref int[] func)

Ejemplo de código de configuración y movimiento de la mano diestra del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    private void button105_Click(object sender, EventArgs e)
    {
        int id = 1;               // Número de estación esclava
        int slaveNum = 4;         // Controlar 4 dedos
        int max_time = 8000;      // Tiempo máximo de espera 8 segundos
        int[] speed = new int[16]; // Array de velocidad, todos 0 significa usar la velocidad predeterminada
        int[] force = new int[16]; // Array de par

        // Inicializar el array de par: los 4 primeros dedos al 50%, el resto 0 (los valores se envían mediante el comando Move)
        for (int i = 0; i < 16; i++)
            force[i] = (i < 4) ? 50 : 0;

        // Función auxiliar: establecer el array de posiciones (solo los 4 primeros dedos son efectivos)
        double[] pos = new double[16];
        void SetPositions(double v1, double v2, double v3, double v4)
        {
            for (int i = 0; i < 16; i++)
                pos[i] = 0;
            pos[0] = v1;
            pos[1] = v2;
            pos[2] = v3;
            pos[3] = v4;
        }

        JointPos j1 = new JointPos(-91.876, -85.920, 109.279, -86.239, -96.664, -28.563);
        JointPos j2 = new JointPos(-40.954, -85.920, 109.279, -86.239, -96.664, -28.563);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        Console.WriteLine("===== Dexterous Hand Full Function Test Started =====");

        // 1. Borrar errores
        int ret = robot.ClearDexterousHandsError();
        Console.WriteLine($"ClearDexterousHandsError -> {ret}");

        // ========== 2. Establecer los interruptores de función ==========
        int[] setFunc = new int[32];
        setFunc[2] = 1;   // Habilitar la función de establecimiento de posición
        setFunc[4] = 1;   // Habilitar la función de establecimiento de par
        setFunc[9] = 1;   // Leer posición
        setFunc[10] = 1;  // Leer par
        setFunc[11] = 1;  // Leer estado
        setFunc[22] = 1;  // Estado de movimiento de un solo eje

        ret = robot.SetDexterousHandsFunc(id, setFunc);
        Console.WriteLine($"SetDexterousHandsFunc(enable + init + position/torque functions enabled) -> {ret}");

        // ========== 3. Leer el estado de las funciones (verificar que la configuración ha surtido efecto) ==========
        int[] getFunc = new int[32];  // GetDexterousHandsFunc devuelve 32 enteros
        ret = robot.GetDexterousHandsFunc(id, ref getFunc);
        Console.WriteLine($"GetDexterousHandsFunc -> {ret}");
        if (ret == 0)
        {
            // Imprimir los 32 valores
            Console.WriteLine("All 32 values returned by GetDexterousHandsFunc:");
            for (int i = 0; i < getFunc.Length; i++)
            {
                Console.Write($"  [{i}]={getFunc[i]}");
                if ((i + 1) % 8 == 0)
                    Console.WriteLine();          // Nueva línea cada 8 elementos
                else if (i < getFunc.Length - 1)
                    Console.Write(", ");
            }
            if (getFunc.Length % 8 != 0)
                Console.WriteLine();              // Añadir nueva línea si la última línea tiene menos de 8 elementos
        }

        // ========== 4. Activar la mano diestra ==========
        ret = robot.SetDexterousHandsAct(id, 1);
        Console.WriteLine($"SetDexterousHandsAct(activate) -> {ret}");
        if (ret != 0)
        {
            Console.WriteLine("Activation failed, test aborted");
            return;
        }

        // ========== 5. Movimiento inicial a 20° (enviar valores de posición y par mediante el comando Move) ==========
        SetPositions(20, 20, 20, 20);
        ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
        Console.WriteLine($"Initial move to 20° -> {ret}");
        robot.Sleep(5000);

        // ========== 6. Movimiento alternativo 10 veces (10° ↔ 50°) ==========
        Console.WriteLine("Starting 10 reciprocating motions...");
        for (int iteration = 1; iteration <= 10; iteration++)
        {
            robot.MoveJ(j1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            SetPositions(10, 10, 10, 10);
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
            Console.WriteLine($"[{iteration}] Move to 10° -> {ret}");
            robot.Sleep(1000);

            robot.MoveJ(j2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            SetPositions(50, 50, 50, 50);
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
            Console.WriteLine($"[{iteration}] Move to 50° -> {ret}");
            robot.Sleep(1000);
        }

        Console.WriteLine("Test completed (function switch set/read + activation + 10 reciprocating motions).");
    }