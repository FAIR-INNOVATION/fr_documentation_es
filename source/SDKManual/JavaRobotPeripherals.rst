Periféricos del robot
=====================

.. toctree:: 
    :maxdepth: 5

Configurar la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Configurar la pinza
    * @param  [in] config .company  Fabricante de la pinza, 1-Robotiq, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing
    * @param  [in] config .device  Número de dispositivo, Robotiq(0-serie 2F-85), Huiling(0-serie NK, 1-Z-EFG-100), Tianji(0-TEG-110), Dahuan(0-PGI-140), Zhixing(0-CTPM2F20)
    * @param  [in] config .softvesion  Número de versión de software, aún no utilizado, valor predeterminado 0
    * @param  [in] config .bus Posición del bus del extremo donde está montado el dispositivo, aún no utilizado, valor predeterminado 0
    * @return  Código de error
    */
    int SetGripperConfig(DeviceConfig config);

Obtener la configuración de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la configuración de la pinza
    * @param  [out] config .company  Fabricante de la pinza, 1-Robotiq, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing
    * @param  [out] config .device  Número de dispositivo, Robotiq(0-serie 2F-85), Huiling(0-serie NK, 1-Z-EFG-100), Tianji(0-TEG-110), Dahuan(0-PGI-140), Zhixing(0-CTPM2F20)
    * @param  [out] config .softvesion  Número de versión de software, aún no utilizado, valor predeterminado 0
    * @param  [out] config .bus Posición del bus del extremo donde está montado el dispositivo, aún no utilizado, valor predeterminado 0
    * @return  Código de error
    */
    int GetGripperConfig(DeviceConfig config);

Activar la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Activar la pinza
    * @param  [in] index  Número de la pinza
    * @param  [in] act  0-reiniciar, 1-activar
    * @return  Código de error
    */
    int ActGripper(int index, int act); 

Controlar la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Controlar la pinza
    * @param  [in] index  Número de la pinza
    * @param  [in] pos  Porcentaje de posición, rango [0~100]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] force  Porcentaje de par, rango [0~100]
    * @param  [in] max_time  Tiempo máximo de espera, rango [0~30000], unidad ms
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [in] type Tipo de pinza, 0-pinza paralela; 1-pinza giratoria
    * @param  [in] rotNum Número de vueltas de rotación
    * @param  [in] rotVel Porcentaje de velocidad de rotación [0-100]
    * @param  [in] rotTorque Porcentaje de par de rotación [0-100]
    * @return Código de error
    */
    int MoveGripper(int index, int pos, int vel, int force, int max_time, int block, int type, double rotNum, int rotVel, int rotTorque); 

Obtener el estado de movimiento de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el estado de movimiento de la pinza (a partir de la versión 401, la definición de retroalimentación del estado de movimiento de la pinza del protocolo del extremo y la de los dispositivos adaptados están unificadas)
    * @param  [out] fault  0-sin error, otro-con error
    * @param  [out] staus  0-movimiento no completado, 1-movimiento completado sin detección de objeto, 2-movimiento completado con detección de objeto, 3-movimiento completado con detección de caída de objeto
    * @return  Código de error
    */
    public List<Integer> GetGripperMotionDone()
    
Esperar el estado de movimiento de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Esperar el estado de movimiento de la pinza (a partir de la versión 401, la definición de retroalimentación del estado de movimiento de la pinza del protocolo del extremo y la de los dispositivos adaptados están unificadas)
    * @param  [in]  staus  0-movimiento no completado, 1-movimiento completado sin detección de objeto, 2-movimiento completado con detección de objeto, 3-movimiento completado con detección de caída de objeto
    * @param  [in] timeout Tiempo de espera (ms) -1 espera permanente
    * @param  [in] strategy  0-detener con error, 1-continuar la ejecución
    * @param  [in] type  0-pinza paralela, 1-pinza giratoria
    * @return  Código de error
    */
    public int GripperWaitMotionDone(int staus, int timeout, int strategy, int type)

Ejemplo de código de espera del estado de movimiento de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public void TestGetGripperMotionDone()
    {
        int rtn;
        int status = 0;
        int fault = 0;
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        // Abrir la pinza
        rtn = robot.MoveGripper(2, 50, 50, 100, 30000, 0, 0, 0, 0, 0);
        System.out.println("MoveGripper(apertura) ret=" + rtn);
        robot.Sleep(2000);
        pkg = robot.GetRobotRealTimeState();
        System.out.println(" gripper_motiondone " + pkg.gripper_motiondone);
        // Cerrar la pinza
        rtn = robot.MoveGripper(2, 90, 100, 100, 30000, 0, 0, 0, 0, 0);
        System.out.println("MoveGripper(cierre) ret=" + rtn);
        robot.Sleep(2000);
        pkg = robot.GetRobotRealTimeState();
        System.out.println(" gripper_motiondone " + pkg.gripper_motiondone);
        // Esperar a que finalice el movimiento sin detección de objeto, tiempo de espera 5s, detener con error
        rtn = robot.GripperWaitMotionDone(2, 5000, 0, 0);
        System.out.println("GripperWaitMotionDone(esperar finalización sin detección de objeto) ret=" + rtn);

        while (true)
        {
            List<Integer> result = robot.GetGripperMotionDone();
            fault = result.get(1);
            status = result.get(2);
            System.out.println("motion status:" + fault + "," + status);
            pkg = robot.GetRobotRealTimeState();
            System.out.println(" error code " + pkg.main_code + "," + pkg.sub_code);
            robot.Sleep(500);
        }
    }

Obtener el estado de activación de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el estado de activación de la pinza
    * @return  List[0]:código de error; List[1] : fault  0-sin error, 1-con error; List[2]: status  bit0~bit15 corresponden a los números de pinza 0~15, bit=0 no activada, bit=1 activada
    */
    List<Number> GetGripperActivateStatus()

Obtener la posición de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la posición de la pinza
    * @return  List[0]:código de error; List[1] : fault  0-sin error, 1-con error; List[2]: position  porcentaje de posición, rango 0~100%
    */
    List<Number> GetGripperCurPosition()

Obtener la velocidad de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la velocidad de la pinza
    * @return  List[0]:código de error; List[1] : fault  0-sin error, 1-con error; List[2]: speed  porcentaje de velocidad, rango 0~100%
    */
    List<Number> GetGripperCurSpeed()

Obtener la corriente de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la corriente de la pinza
    * @return  List[0]:código de error; List[1] : fault  0-sin error, 1-con error; List[2]: current  porcentaje de corriente, rango 0~100%
    */
    List<Number> GetGripperCurCurrent()

Obtener el voltaje de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el voltaje de la pinza
    * @return List[0]:código de error; List[1] : fault  0-sin error, 1-con error; List[2]:voltage  voltaje, unidad 0.1V
    */
    List<Number> GetGripperVoltage()

Obtener la temperatura de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la temperatura de la pinza
    * @return List[0]:código de error; List[1] : fault  0-sin error, 1-con error; List[2]:temp  temperatura, unidad ℃
    */
    List<Number> GetGripperTemp()

Calcular el punto de preagarre - visión
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcular el punto de preagarre - visión 
    * @param [in] desc_pos  Pose cartesiana del punto de agarre
    * @param [in] zlength   Desplazamiento del eje z
    * @param [in] zangle    Desplazamiento de rotación alrededor del eje z
    * @param [out] pre_pos  Punto de agarre
    * @return Código de error 
    */ 
    int ComputePrePick(DescPose desc_pos, double zlength, double zangle, DescPose pre_pos);

Calcular el punto de retirada - visión
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcular el punto de retirada - visión 
    * @param [in] desc_pos  Pose cartesiana del punto de agarre
    * @param [in] zlength   Desplazamiento del eje z 
    * @param [in] zangle    Desplazamiento de rotación alrededor del eje z
    * @param [out] post_poss Punto de retirada
    * @return Código de error 
    */ 
    int ComputePostPick(DescPose desc_pos, double zlength, double zangle, DescPose post_pos);

Ejemplo de código de operación de la pinza del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGripper(Robot robot)
    {
        int company = 4;
        int device = 0;
        int softversion = 0;
        int bus = 2;
        int index = 2;
        int act = 0;
        int max_time = 30000;
        int block = 0;

        int current_pos = 0;
        int current = 0;
        int voltage = 0;
        int temp = 0;
        int speed = 0;

        DeviceConfig cnn=new DeviceConfig(company,device,softversion,bus);
        robot.SetGripperConfig(cnn);
        robot.GetGripperConfig(cnn);

        robot.ActGripper(index, act);
        robot.Sleep(1000);
        act = 1;
        robot.ActGripper(index, act);
        robot.Sleep(1000);

        robot.MoveGripper(index, 100, 50, 50, max_time, block, 0, 0, 0, 0);
        robot.Sleep(1000);
        robot.MoveGripper(index, 0, 50, 0, max_time, block, 0, 0, 0, 0);

        List<Integer> stat=new ArrayList<>();
        stat=robot.GetGripperMotionDone();

        List<Number> list=new ArrayList<>();
        list=robot.GetGripperActivateStatus();

        list=robot.GetGripperCurPosition();

        list=robot.GetGripperCurCurrent();

        list=robot.GetGripperVoltage();

        list=robot.GetGripperTemp();

        list=robot.GetGripperCurSpeed();

        int retval = 0;
        DescPose prepick_pose = new DescPose(){};
        DescPose postpick_pose = new DescPose(){};

        DescPose p1Desc=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        retval = robot.ComputePrePick(p1Desc, 10, 0, prepick_pose);

        retval = robot.ComputePostPick(p2Desc, -10, 0, postpick_pose);
        return 0;
    }

Obtener el número de vueltas de rotación de la pinza giratoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el número de vueltas de rotación de la pinza giratoria
    * @return List[0]:código de error List[1]: 0-sin error, 1-con error List[2]:número de vueltas de rotación
    */
    List<Number> GetGripperRotNum(); 

Obtener el porcentaje de velocidad de rotación de la pinza giratoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el porcentaje de velocidad de rotación de la pinza giratoria
    * @return List[0]:código de error List[1]: 0-sin error, 1-con error List[2]:porcentaje de velocidad de rotación
    */
    List<Number> GetGripperRotSpeed(); 

Obtener el porcentaje de par de rotación de la pinza giratoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el porcentaje de par de rotación de la pinza giratoria
    * @return List[0]:código de error List[1]: 0-sin error, 1-con error List[2]:porcentaje de par de rotación
    */
    List<Number> GetGripperRotTorque(); 

Ejemplo de código de obtención del estado de la pinza giratoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestRotGripperState(Robot robot)
    {
        int fault = 0;
        List<Number> rotNum=new ArrayList<>();
        List<Number> rotSpeed=new ArrayList<>();
        List<Number> rotTorque=new ArrayList<>();

        rotNum=robot.GetGripperRotNum();
        rotSpeed=robot.GetGripperRotSpeed();
        rotTorque=robot.GetGripperRotTorque();
        System.out.println("gripper rot num :"+rotNum.get(2)+ ", gripper rotSpeed :"+rotSpeed.get(2)+",gripper rotTorque : "+rotTorque.get(2));

        return 0;
    }

Inicio y parada de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Inicio y parada de la cinta transportadora
    * @param  [in] status Estado, 1-iniciar, 0-detener
    * @return  Código de error
    */
    int ConveyorStartEnd(int status);

Registrar el punto de detección IO
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registrar el punto de detección IO
    * @return  Código de error
    */
    int ConveyorPointIORecord();

Registrar el punto A
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registrar el punto A
    * @return  Código de error
    */
    int ConveyorPointARecord(); 

Registrar el punto de referencia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registrar el punto de referencia
    * @return  Código de error
    */
    int ConveyorRefPointRecord();

Registrar el punto B
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registrar el punto B
    * @return Código de error
    */
    int ConveyorPointBRecord(); 

Detección IO de la pieza en la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Detección IO de la pieza en la cinta transportadora
    * @param [in] max_t Tiempo máximo de detección, unidad ms
    * @return Código de error 
    */ 
    int ConveyorIODetect(int max_t);

Obtener la posición actual del objeto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener la posición actual del objeto
    * @param [in] mode 1-agarre con seguimiento, 2-movimiento con seguimiento, 3-seguimiento TPD
    * @return Código de error 
    */ 
    int ConveyorGetTrackData(int mode);

Inicio del seguimiento de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Inicio del seguimiento de la cinta transportadora
    * @param [in] status Estado, 1-iniciar, 0-detener
    * @return Código de error 
    */ 
    int ConveyorTrackStart(int status);

Detención del seguimiento de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Detención del seguimiento de la cinta transportadora
    * @return Código de error 
    */ 
    int ConveyorTrackEnd();

Configuración de parámetros de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief  Configuración de parámetros de la cinta transportadora
    * @param [in] encChannel Canal del codificador 1~2
    * @param [in] resolution Número de pulsos por vuelta del codificador
    * @param [in] lead Distancia recorrida por la cinta por vuelta del codificador
    * @param [in] wpAxis Número del sistema de coordenadas de pieza; para la función de movimiento con seguimiento seleccione el número del sistema de coordenadas de pieza; agarre con seguimiento y seguimiento TPD se establecen en 0
    * @param [in] vision Si se configura visión  0 no configurar  1 configurar
    * @param [in] speedRadio Relación de velocidad  para la opción de agarre con seguimiento de la cinta (1-100); las demás opciones toman el valor predeterminado 1
    * @return Código de error
    */
    int ConveyorSetParam(int encChannel, int resolution, double lead, int wpAxis, int vision, double speedRadio, int followType, int startDis, int endDis); 

Establecer la compensación del punto de agarre de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer la compensación del punto de agarre de la cinta transportadora
    * @param [in] cmp Posición de compensación double[3]{x, y, z}
    * @return Código de error 
    */ 
    int ConveyorCatchPointComp(Object[] cmp);

Movimiento lineal de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Movimiento lineal
    * @param [in] name Descripción del punto de movimiento
    * @param [in] tool Número de coordenada de herramienta, rango [0~14]
    * @param [in] wobj Número de coordenada de pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @return Código de error 
    */ 
    int ConveyorTrackMoveL(String name, int tool, int wobj, double vel, double acc, double ovl, double blendR);   

Detección de entrada de comunicación de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Detección de entrada de comunicación de la cinta transportadora
    * @param [in] timeout Tiempo de espera máximo en ms
    * @return Código de error
    */
    int ConveyorComDetect(int timeout);

Disparo de detección de entrada de comunicación de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Disparo de detección de entrada de comunicación de la cinta transportadora
    * @param [in] timeout Tiempo de espera máximo en ms
    * @return Código de error
    */
    int ConveyorComDetectTrigger();

Programa de ejemplo de operación de la cinta transportadora del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestConveyor(Robot robot)
    {
        int retval = 0;

        retval = robot.ConveyorStartEnd(1);

        retval = robot.ConveyorPointIORecord();

        retval = robot.ConveyorPointARecord();

        retval = robot.ConveyorRefPointRecord();

        retval = robot.ConveyorPointBRecord();

        retval = robot.ConveyorStartEnd(0);

        retval = 0;

        retval = robot.ConveyorSetParam(1,10000,200,0,0,20,0,0,100);

        Object[] cmp = new Object[]{ 0.0, 0.0, 0.0 };
        retval = robot.ConveyorCatchPointComp(cmp);

        int index = 1;
        int max_time = 30000;
        int block = 0;
        retval = 0;

        DescPose p1Desc=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);


        retval = robot.MoveCart(p1Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);

        retval = robot.WaitMs(1);

        retval = robot.ConveyorTrackStart(1);

        retval = robot.ConveyorTrackMoveL("cvrCatchPoint", 1, 0, 100, 100, 100, -1.0);

        retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0);

        retval = robot.ConveyorTrackMoveL("cvrRaisePoint", 1, 0, 100, 100, 100, -1.0);

        retval = robot.ConveyorTrackEnd();

        robot.MoveCart(p2Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);

        retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0);

        return 0;
    }

Configuración de parámetros de seguimiento en el lugar de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Configuración de parámetros de seguimiento en el lugar de la cinta transportadora
    * @param  [in] trackMode 0-tiempo; 1-distancia; 2-tiempo y distancia, se cumple cualquiera de los dos
    * @param  [in] trackTime Tiempo de seguimiento, unidad s
    * @param  [in] trackDis Distancia de seguimiento
    * @return  Código de error
    */
    public int SetStationaryTrackPara(int trackMode, double trackTime, int trackDis)

Ejemplo de código de seguimiento en el lugar de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestStationaryTrack(Robot robot)
    {
        System.out.println("\n========== Prueba de seguimiento estacionario de la cinta transportadora ==========");

        int rtn;

        JointPos j1 = new JointPos(-35.146, -102.684, 120.805, -100.401, -90.295, 150.105);
        DescPose d1 = new DescPose(-121.814, -348.341, 209.978, -173.152, -3.585, -5.446);

        ExaxisPos ex = new ExaxisPos(0, 0, 0, 0);
        DescPose zeroOff = new DescPose(0, 0, 0, 0, 0, 0);

        int tool = 1;
        int workpiece = 1;

        rtn = robot.ConveyorSetParam(0, 10000, 200, 0, 0, 10,0,0,0);


        robot.MoveJ(j1, d1, tool, workpiece, 100, 100, 100, ex, -1, 0, zeroOff);

        // Step 1: SetDO señal de control
        System.out.println("--- Step 1: SetDO(6,1) ---");
        rtn = robot.SetDO(6, 1, 0, 0);
        System.out.println("  SetDO(6,1) rtn=" + rtn);

        // Step 2: inicio del seguimiento de la cinta transportadora
        System.out.println("--- Step 2: ConveyorTrackStart(2) ---");
        rtn = robot.ConveyorTrackStart(2);
        System.out.println("  ConveyorTrackStart(2) rtn=" + rtn);

        // Step 3: detección IO de la pieza
        System.out.println("--- Step 3: ConveyorIODetect(10000) ---");
        rtn = robot.ConveyorIODetect(10000);
        System.out.println("  ConveyorIODetect(10000) rtn=" + rtn);

        // Step 4: obtener los datos de seguimiento
        System.out.println("--- Step 4: ConveyorGetTrackData(2) ---");
        rtn = robot.ConveyorGetTrackData(2);
        System.out.println("  ConveyorGetTrackData(2) rtn=" + rtn);

        // Step 5: configuración de parámetros de seguimiento estacionario (modo tiempo, 200s, distancia 5)
        System.out.println("--- Step 5: SetStationaryTrackPara(0,200,5) ---");
        rtn = robot.SetStationaryTrackPara(0, 5, 5);
        System.out.println("  SetStationaryTrackPara(0,200,5) rtn=" + rtn);

        // Step 6: ejecutar el movimiento de seguimiento estacionario
        System.out.println("--- Step 6: MoveStationary() ---");
        rtn = robot.MoveStationary();
        robot.WaitStationaryMotionDone();
        System.out.println("  MoveStationary() rtn=" + rtn);

        // Step 7: fin del seguimiento de la cinta transportadora
        System.out.println("--- Step 7: ConveyorTrackEnd() ---");
        rtn = robot.ConveyorTrackEnd();
        System.out.println("  ConveyorTrackEnd() rtn=" + rtn);

        // Step 8: SetDO señal de apagado
        System.out.println("--- Step 8: SetDO(6,0) ---");
        rtn = robot.SetDO(6, 0, 0, 0);
        System.out.println("  SetDO(6,0) rtn=" + rtn);

        System.out.println("\n========== Prueba de seguimiento estacionario completada ==========");
        return 0;
    }

Configuración del sensor del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Configuración del sensor del extremo
    * @param [in] config idCompany Fabricante, 18-JUNKONG; 25-HUIDE
    * @param [in] config idDevice Tipo, 0-JUNKONG/RYR6T.V1.0
    * @param [in] config idSoftware Versión de software, 0-J1.0/HuiDe1.0 (aún no disponible)
    * @param [in] config idBus Posición de montaje, 1-puerto 1 del extremo; 2-puerto 2 del extremo...8-puerto 8 del extremo (aún no disponible)
    * @return Código de error
    */
    int AxleSensorConfig(DeviceConfig config);

Obtener la configuración del sensor del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener la configuración del sensor del extremo
    * @param [out] config idCompany Fabricante, 18-JUNKONG; 25-HUIDE
    * @param [out] config idDevice Tipo, 0-JUNKONG/RYR6T.V1.0
    * @return Código de error
    */
    int AxleSensorConfigGet(DeviceConfig config);

Activación del sensor del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Activación del sensor del extremo
    * @param [in] actFlag 0-reiniciar; 1-activar
    * @return Código de error
    */
    int AxleSensorActivate(int actFlag);

Escritura de registro del sensor del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Escritura de registro del sensor del extremo
    * @param [in] devAddr  Número de dirección del dispositivo 0-255
    * @param [in] regHAddr 8 bits altos de la dirección del registro
    * @param [in] regLAddr 8 bits bajos de la dirección del registro
    * @param [in] regNum  Número de registros 0-255
    * @param [in] data1 Valor 1 a escribir en el registro
    * @param [in] data2 Valor 2 a escribir en el registro
    * @param [in] isNoBlock 0-bloqueante; 1-no bloqueante
    * @return Código de error
    */
    int AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Ejemplo de código del sensor del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAxleSensor(Robot robot)
    {
        DeviceConfig con=new DeviceConfig(18,0,0,1);
        robot.AxleSensorConfig(con);
        int company = -1;
        int type = -1;
        robot.AxleSensorConfigGet(con);

        int rtn = robot.AxleSensorActivate(1);

        robot.Sleep(1000);

        rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
        return 0;
    }

Obtener el protocolo de periféricos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener el protocolo de periféricos del robot
    * @return List[0]:código de error; List[1] : int protocol Número de protocolo de periféricos del robot 4096-tarjeta de control del eje extendido; 4097-ModbusSlave; 4098-ModbusMaster 
    */
    List<Integer> GetExDevProtocol();

Establecer el protocolo de periféricos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el protocolo de periféricos del robot
    * @param [in] protocol Número de protocolo de periféricos del robot 4096-tarjeta de control del eje extendido; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Código de error 
    */ 
    int SetExDevProtocol(int protocol);

Ejemplo de programa de establecimiento del protocolo de periféricos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestExDevProtocol(Robot robot)
    {
        int protocol = 4096;
        int rtn = robot.SetExDevProtocol(protocol);
        List<Integer> integer=new ArrayList<>();
        integer = robot.GetExDevProtocol();

        return 0;
    }

Obtener los parámetros de comunicación del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener los parámetros de comunicación del extremo
    * @param [out] param Parámetros de comunicación del extremo
    * @return Código de error 
    */
    int GetAxleCommunicationParam(AxleComParam param)

Establecer los parámetros de comunicación del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer los parámetros de comunicación del extremo
    * @param [in] param Parámetros de comunicación del extremo
    * @return Código de error 
    */
    int SetAxleCommunicationParam(AxleComParam param)

Establecer el tipo de transferencia de archivos del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el tipo de transferencia de archivos del extremo
    * @param [in] type 1-archivo de actualización de MCU; 2-archivo LUA
    * @return  Código de error
    */
    public int SetAxleFileType(int type)

Establecer la habilitación de ejecución de LUA del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la habilitación de ejecución de LUA del extremo
    * @param [in] enable 0-no habilitar; 1-habilitar
    * @return  Código de error
    */
    public int SetAxleLuaEnable(int enable)

Recuperación de errores anómalos del archivo LUA del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Recuperación de errores anómalos del archivo LUA del extremo
    * @param [in] status 0-no recuperar; 1-recuperar
    * @return  Código de error
    */
    public int SetRecoverAxleLuaErr(int status)

Obtener el estado de habilitación de ejecución de LUA del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el estado de habilitación de ejecución de LUA del extremo
    * @param [out] status[0]: 0-no habilitado; 1-habilitado
    * @return  Código de error
    */
    int GetAxleLuaEnableStatus(int[] status)

Establecer el tipo de dispositivo del extremo habilitado por LUA del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el tipo de dispositivo del extremo habilitado por LUA del extremo
    * @param forceSensorEnable Estado de habilitación del sensor de fuerza, 0-no habilitar; 1-habilitar
    * @param gripperEnable Estado de habilitación de la pinza, 0-no habilitar; 1-habilitar
    * @param IOEnable Estado de habilitación del dispositivo IO, 0-no habilitar; 1-habilitar
    * @param dexhandEnable Estado de habilitación de la mano diestra, 0-no habilitar; 1-habilitar
    * @return  Código de error
    */
    public int SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable, int dexhandEnable)

Obtener el tipo de dispositivo del extremo habilitado por LUA del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Obtener el tipo de dispositivo del extremo habilitado por LUA del extremo
     * @param enable enable[0]:forceSensorEnable Estado de habilitación del sensor de fuerza, 0-no habilitar; 1-habilitar
     * @param enable enable[1]:gripperEnable Estado de habilitación de la pinza, 0-no habilitar; 1-habilitar
     * @param enable enable[2]:IOEnable Estado de habilitación del dispositivo IO, 0-no habilitar; 1-habilitar
     * @param enable enable[3]:dexhandEnable Estado de habilitación de la mano diestra, 0-no habilitar; 1-habilitar
     * @return  Código de error
     */
    public int GetAxleLuaEnableDeviceType(int[] enable)

Obtener el dispositivo del extremo configurado actualmente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Obtener el dispositivo del extremo configurado actualmente
     * @param forceSensorEnable Número del dispositivo habilitado del sensor de fuerza 0-no habilitado; 1-habilitado
     * @param gripperEnable Número del dispositivo habilitado de la pinza, 0-no habilitar; 1-habilitar
     * @param IODeviceEnable Número del dispositivo habilitado de IO, 0-no habilitar; 1-habilitar
     * @param dexhandEnable Estado de habilitación de la mano diestra, 0-no habilitar; 1-habilitar
     * @return  Código de error
     */
    public int GetAxleLuaEnableDevice(int[] forceSensorEnable, int[] gripperEnable, int[] IODeviceEnable, int[] dexhandEnable)


Establecer la habilitación de la función de control de acciones de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Establecer la habilitación de la función de control de acciones de la pinza
     * @param id Número del dispositivo de pinza
     * @param func func[0]-habilitación de la pinza; func[1]-inicialización de la pinza; func[2]-configuración de posición; func[3]-configuración de velocidad; func[4]-configuración de par; func[6]-leer estado de la pinza;
        func[7]-leer estado de inicialización; func[8]-leer código de fallo; func[9]-leer posición; func[10]-leer velocidad; func[11]-leer par; func[12]-configuración de vueltas de rotación de la pinza giratoria;
        func[13]-configuración de velocidad de rotación de la pinza giratoria; func[14]-configuración de par de rotación de la pinza giratoria; func[15]-leer estado de la pinza giratoria; func[16]-leer estado de inicialización de la pinza giratoria;
        func[17]-leer vueltas de la pinza giratoria; func[18]-leer velocidad de la pinza giratoria; func[19]-leer par de la pinza giratoria; func[20]-configuración de movimiento síncrono multieje; func[21]-instrucción de borrado de fallos;
        func[22]-estado de funcionamiento de eje único; func[23]-estado de funcionamiento de todos los ejes;
     * @return  Código de error
     */
    public int SetAxleLuaGripperFunc(int id, int[] func)

Obtener la habilitación de la función de control de acciones de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Obtener la habilitación de la función de control de acciones de la pinza
     * @param id Número del dispositivo de pinza
     * @param func func[0]-habilitación de la pinza; func[1]-inicialización de la pinza; func[2]-configuración de posición; func[3]-configuración de velocidad; func[4]-configuración de par; func[6]-leer estado de la pinza;
        func[7]-leer estado de inicialización; func[8]-leer código de fallo; func[9]-leer posición; func[10]-leer velocidad; func[11]-leer par; func[12]-configuración de vueltas de rotación de la pinza giratoria;
        func[13]-configuración de velocidad de rotación de la pinza giratoria; func[14]-configuración de par de rotación de la pinza giratoria; func[15]-leer estado de la pinza giratoria; func[16]-leer estado de inicialización de la pinza giratoria;
        func[17]-leer vueltas de la pinza giratoria; func[18]-leer velocidad de la pinza giratoria; func[19]-leer par de la pinza giratoria; func[20]-configuración de movimiento síncrono multieje; func[21]-instrucción de borrado de fallos;
        func[22]-estado de funcionamiento de eje único; func[23]-estado de funcionamiento de todos los ejes;
     * @return  Código de error
     */
    public int GetAxleLuaGripperFunc(int id, int[] func)

Escritura del archivo del esclavo Ethercat del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Escritura del archivo del esclavo Ethercat del robot
     * @param type Tipo de archivo del esclavo, 1-actualizar archivo del esclavo; 2-actualizar archivo de configuración del esclavo
     * @param slaveID Número de esclavo
     * @param fileName Nombre del archivo a subir
     * @return  Código de error
     */
    public int SlaveFileWrite(int type, int slaveID, String fileName)

Subir el archivo de protocolo abierto LUA del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Subir el archivo de protocolo abierto LUA del extremo
     * @param filePath Nombre de ruta del archivo lua local ".../AXLE_LUA_End_DaHuan.lua"
     * @return Código de error
     */
    public int AxleLuaUpload(String filePath)

Entrada del esclavo Ethercat del robot en modo boot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Entrada del esclavo Ethercat del robot en modo boot
     * @return  Código de error
     */
    public int SetSysServoBootMode()

Ejemplo de código de operación del archivo LUA del extremo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAxleLua(Robot robot)
    {
        robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua");

        AxleComParam param=new AxleComParam(7, 8, 1, 0, 5, 3, 1);
        robot.SetAxleCommunicationParam(param);

        robot.GetAxleCommunicationParam(param);

        robot.SetAxleLuaEnable(1);
        int[] luaEnableStatus = new int[]{0};
        robot.GetAxleLuaEnableStatus(luaEnableStatus);
        robot.SetAxleLuaEnableDeviceType(0, 1, 0);

        int forceEnable = 0;
        int gripperEnable = 0;
        int ioEnable = 0;
        int [] enable=new int[]{0,0,0};
        robot.GetAxleLuaEnableDeviceType(enable);

        int[] func = { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 };
        robot.SetAxleLuaGripperFunc(1, func);
        int[] getFunc = { 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0};
        robot.GetAxleLuaGripperFunc(1, getFunc);
        int[] getforceEnable = { 0,0,0,0,0,0,0,0};
        int[] getgripperEnable = { 0,0,0,0,0,0,0,0};
        int[] getioEnable = { 0,0,0,0,0,0,0,0};
        robot.GetAxleLuaEnableDevice(getforceEnable, getgripperEnable, getioEnable);
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getforceEnable[i]);
        }
        System.out.println("getgripperEnable status : ");
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getgripperEnable[i]);
        }
        System.out.println("getioEnable status : ");
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getioEnable[i]);
        }
        robot.ActGripper(1, 0);
        robot.Sleep(2000);
        robot.ActGripper(1, 1);
        robot.Sleep(2000);
        robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0);
        int pos = 0;
        while (true)
        {
            ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
            pkg=robot.GetRobotRealTimeState();
            System.out.println("gripper pos is:"+pkg.gripper_position);
            robot.Sleep(100);
        }

    }

Obtener el estado de los botones de SmartTool
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el estado de los botones de SmartTool
    * @param [out] state Estado de los botones del mango SmartTool;(bit0:0-comunicación normal; 1-comunicación desconectada; bit1-deshacer operación; bit2-borrar programa; bit3-tecla A; bit4-tecla B; bit5-tecla C; bit6-tecla D; bit7-tecla E; bit8-tecla IO; bit9-manual/automático; bit10-inicio)
    * @return Código de error
    */
    int GetSmarttoolBtnState(int[] state)

Ejemplo de código de los botones de SmartTool
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args) 
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true, 100, 500);//Establecer el número de reconexiones y el intervalo
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn == 0) {
            System.out.println("rpc conexión success");
        } else {
            System.out.println("rpc conexión fail");
            return;
        }

        int[] state = {0};
        while (true)
        {
            robot.GetSmarttoolBtnState(state);

            String binaryString = String.format("%32s", Integer.toBinaryString(state[0])).replace(' ', '0');
            System.out.println("GetSmarttoolBtnState:"+binaryString);
            robot.Sleep(100);
        }
    }

Subir el archivo LUA de protocolo abierto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Subir el archivo LUA de protocolo abierto
    * @param  filePath Nombre de ruta del archivo lua de protocolo abierto local
    * @return Código de error
    */
    public int OpenLuaUpload(String filePath)


Obtener los parámetros de la placa esclava
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener los parámetros de la placa esclava
    * @param  type  0-Ethercat, 1-CClink, 3-Ethercat, 4-EIP
    * @param  version  Versión del protocolo
    * @param  connState  0-no conectado, 1-conectado
    * @return  Código de error
    */
    public int GetFieldBusConfig(int[] type, int[] version, int[] connState)

Escribir DO del esclavo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
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
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /*
    * @brief  Escribir AO del esclavo
    * @param  AOIndex Número de AO
    * @param  wirteNum Cantidad a escribir
    * @param  status Arreglo de valores a escribir (máximo 8), AO0~AO15 son de tipo entero, AO16~AO31 son de tipo flotante
    * @return  Código de error
    */
    public int FieldBusSlaveWriteAO(int AOIndex, int wirteNum, double[] status)

Leer DI del esclavo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
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
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
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
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
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
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
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

Ejemplo de código de instrucciones de interfaz relacionadas con el modo esclavo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testFieldBusBoard(Robot robot)
    {
        //Subir y cargar el archivo de protocolo abierto
        robot.OpenLuaUpload("D://zUP/1111/CtrlDev_field.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        robot.Sleep(8000);
        int[] type=new int[1];
        int[] version=new int[1];
        int[] connState=new int[1];
        //Obtener el tipo de protocolo, la versión de software y el estado de conexión con el PLC de la placa esclava
        robot.GetFieldBusConfig(type, version, connState);
        System.out.println("type is: "+type[0]+", version is : "+version[0]+", connState is : "+connState[0]);
        //Escribir DO0 = 1, DO1 = 0, DO2 = 1
        int[] ctrl =new int[8];
        ctrl[0] = 1;
        ctrl[1] = 0;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);
        //Escribir AO2 = 0x1000
        int[] ctrlAO =new int[8];
        ctrlAO[0] = 0x1000;
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO);
        int[] DI=new int[4];
        double[] AI=new double[3];
        //Monitorear cíclicamente DI0~DI3 AI0~AI2
        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, DI);
            System.out.println("DI0 is: "+DI[0]+", DI1 is: "+DI[1]+",DI2 is: "+DI[2]+",DI3 is: "+DI[3]);
            robot.FieldBusSlaveReadAI(0, 3, AI);
            System.out.println("AI0 is: "+AI[0]+ ",AI1 is: "+AI[1]+",AI2 is: "+AI[2]);
            robot.Sleep(10);
        }
        //Esperar si DI0 es 1, tiempo de espera 100ms, e imprimir el resultado
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        System.out.println("FieldBusSlaveWaitDI result is: "+ ret);
        //Esperar si AI0 es mayor que 400, tiempo de espera 100ms, e imprimir el resultado
        ret = robot.FieldBusSlaveWaitAI(0,0,400.00,100);
        System.out.println("FieldBusSlaveWaitAI result is: "+ ret);
        robot.CloseRPC();
    }

Controlar la ventosa de matriz
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Controlar la ventosa de matriz
    * @param  slaveID Número de esclavo
    * @param  len Longitud
    * @param  ctrlValue Valor de control 1-aspirar a vacío máximo 2-aspirar a vacío configurado 3-detener la aspiración
    * @return Código de error
    */
    public int SetSuckerCtrl(int slaveID, int len, int[] ctrlValue)

Obtener el estado de la ventosa de matriz
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el estado de la ventosa de matriz
    * @param  slaveID Número de esclavo
    * @param  state Estado de aspiración 0-liberar objeto 1-detección de aspiración exitosa de la pieza 2-no se aspiró ningún objeto 3-el objeto se ha desprendido
    * @param  pressValue Vacío actual, unidad kPa
    * @param  error Código de error actual de la ventosa
    * @return Código de error
    */
    public int GetSuckerState(int slaveID, int[] state, int[] pressValue, int[] error)

Esperar el estado de la ventosa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Esperar el estado de la ventosa
    * @param  slaveID Número de esclavo
    * @param  state Estado de aspiración 0-liberar objeto 1-detección de aspiración exitosa de la pieza 2-no se aspiró ningún objeto 3-el objeto se ha desprendido
    * @param  ms Tiempo máximo de espera
    * @return Código de error
    */
    public int WaitSuckerState(int slaveID, int state, int ms)

Ejemplo de código de instrucciones de control de la ventosa de matriz
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testSucker(Robot robot)
    {
        //Subir y cargar el archivo de protocolo abierto
        robot.OpenLuaUpload("C：//项目/外设SDK/CtrlDev_sucker.lua");
        robot.Sleep(2000);
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        robot.Sleep(1000);
        //En modo de difusión de control de ventosas, aspirar según la capacidad máxima
        int[] ctrl = {1};
        robot.SetSuckerCtrl(0, 1, ctrl);
        int[] state=new int[1];
        int[] pressVlaue=new int[1];
        int[] error=new int[1];
        //Monitorear cíclicamente el estado de la ventosa 1 y la ventosa 12
        for (int i = 0; i < 100; i++)
        {
            robot.GetSuckerState(1, state,pressVlaue, error);
            System.out.println("sucker1 state is:"+state[0]+",pressVlaue is:"+pressVlaue[0]+",error num is"+error[0]);
            robot.GetSuckerState(12, state, pressVlaue, error);
            System.out.println("sucker12 state is :"+state[0]+", pressVlaue is:"+pressVlaue[0]+",error num is:"+error[0]);
            robot.Sleep(100);
        }
        //Esperar si la ventosa 1 está en estado de aspiración exitosa de la pieza, tiempo de espera 100ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        System.out.println("WaitSuckerState result is:"+ ret);
        //Desactivar en modo unicast las ventosas 1 y 12
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);
        robot.CloseRPC();
    }

Función de encendido y apagado del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Función de encendido y apagado del periférico láser
     * @param [in] OnOff 0-apagar 1-encender
     * @param [in] weldId ID de la soldadura, por defecto 0
     * @return Código de error
     */
    public int LaserTrackingLaserOnOff(int OnOff, int weldId)
    
Función de inicio y fin del seguimiento láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:
    
    /**
     * @brief Función de inicio y fin del seguimiento láser
     * @param [in] OnOff 0-finalizar 1-iniciar
     * @param [in] coordId Número del sistema de coordenadas de la herramienta del periférico láser
     * @return Código de error
     */
    public int LaserTrackingTrackOnOff(int OnOff, int coordId)

Búsqueda de posición láser - dirección fija
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Búsqueda de posición láser - dirección fija
     * @param [in] direction 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
     * @param [in] vel Velocidad, unidad %
     * @param [in] distance Distancia máxima de búsqueda de posición, unidad mm
     * @param [in] timeout Tiempo de espera máximo de búsqueda de posición, unidad ms
     * @param [in] posSensorNum Número de coordenada de herramienta de calibración láser
     * @return Código de error
     */
    public int LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum)
    
Búsqueda de posición láser - dirección arbitraria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Búsqueda de posición láser - dirección arbitraria
     * @param [in] directionPoint Coordenadas xyz del punto introducido para la búsqueda de posición
     * @param [in] vel Velocidad, unidad %
     * @param [in] distance Distancia máxima de búsqueda de posición, unidad mm
     * @param [in] timeout Tiempo de espera máximo de búsqueda de posición, unidad ms
     * @param [in] posSensorNum Número de coordenada de herramienta de calibración láser
     * @return Código de error
     */
    public int LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum)
   
Fin de búsqueda de posición láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
   :linenos:

   /**
    * @brief  Fin de búsqueda de posición láser
    * @return Código de error
    */
    public int LaserTrackingSearchStop()

Configuración de IP del láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
   :linenos:

    /**
     * @brief Configuración de IP del láser
     * @param [in] ip Dirección IP del periférico láser
     * @param [in] port Número de puerto del periférico láser
     * @return Código de error
     */
    public int LaserTrackingSensorConfig(String ip, int port)

Configuración del período de muestreo del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Configuración del período de muestreo del periférico láser
     * @param [in] period Período de muestreo del periférico láser, unidad ms
     * @return Código de error
     */
    public int LaserTrackingSensorSamplePeriod(int period)

Carga del controlador del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Carga del controlador del periférico láser
     * @param [in] type Tipo de protocolo del controlador del periférico láser 101-Ruiniu 102-Chuangxiang 103-Quanshi 104-Tongzhou 105-Aotai
     * @return Código de error
     */
    public int LoadPosSensorDriver(int type)

Descarga del controlador del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Descarga del controlador del periférico láser
     * @return Código de error
     */
    public int UnLoadPosSensorDriver()

Registro de trayectoria de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Registro de trayectoria de soldadura láser
     * @param [in] status 0-detener registro 1-seguimiento en tiempo real  2-iniciar registro
     * @param [in] delayTime Tiempo de retardo, unidad ms
     * @return Código de error
     */
    public int LaserSensorRecord1(int status, int delayTime)

Reproducción de trayectoria de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Reproducción de trayectoria de soldadura láser
     * @param [in] delayTime Tiempo de retardo, unidad ms
     * @param [in] speed Velocidad, unidad %
     * @return Código de error
     */
    public int LaserSensorReplay(int delayTime, double speed)

Reproducción de seguimiento láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Reproducción de seguimiento láser
     * @return Código de error
     */
    public int MoveLTR()

Reproducción de trayectoria de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
    * @brief Reproducción de trayectoria de soldadura láser
    * @param delayMode Modo 0-tiempo de retardo 1-distancia de retardo
    * @param delayTime Tiempo de retardo, unidad ms
    * @param delayDisExAxisNum Número de eje extendido
    * @param delayDis Distancia de retardo, unidad mm
    * @param sensitivePara Coeficiente de sensibilidad de compensación
    * @param trackMode Tipo de seguimiento de punto fijo. 0-movimiento asíncrono del eje extendido; 1-robot
    * @param triggerMode Modo de disparo del seguimiento de punto fijo. 0-duración del seguimiento; 1-IO
    * @param runTime Duración del seguimiento de punto fijo del robot (s)
    * @param speed Velocidad, unidad %
    * @return Código de error
    */
    public int LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum, double delayDis, double sensitivePara, int trackMode, int triggerMode, double runTime, double speed)
    
Moverse al punto de inicio del registro de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Moverse al punto de inicio del registro de soldadura
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl Velocidad, unidad %
     * @return Código de error
     */
    public int MoveToLaserRecordStart(int moveType, double ovl)

Moverse al punto final del registro de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Moverse al punto final del registro de soldadura
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl Velocidad, unidad %
     * @return Código de error
     */
    public int MoveToLaserRecordEnd(int moveType, double ovl)

Moverse al punto de búsqueda de posición del sensor láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Moverse al punto de búsqueda de posición del sensor láser
     * @param [in] moveFlag Tipo de movimiento: 0-PTP; 1-LIN
     * @param [in] ovl Factor de escala de velocidad, 0-100
     * @param [in] dataFlag Selección de datos de caché de soldadura: 0-ejecutar datos de planificación; 1-ejecutar datos de registro
     * @param [in] plateType Tipo de placa: 0-placa ondulada; 1-placa corrugada; 2-placa de cerca; 3-barril de aceite; 4-acero ondulado
     * @param [in] trackOffectType Tipo de desplazamiento del sensor láser: 0-sin desplazamiento; 1-desplazamiento del sistema de coordenadas base; 2-desplazamiento del sistema de coordenadas de herramienta; 3-desplazamiento de datos originales del sensor láser
     * @param [in] offset Cantidad de desplazamiento
     * @return Código de error
     */
    public int MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset)
    
Obtener la información de coordenadas del punto de búsqueda de posición del sensor láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Obtener la información de coordenadas del punto de búsqueda de posición del sensor láser
     * @param [in] trackOffectType Tipo de desplazamiento del sensor láser: 0-sin desplazamiento; 1-desplazamiento del sistema de coordenadas base; 2-desplazamiento del sistema de coordenadas de herramienta; 3-desplazamiento de datos originales del sensor láser
     * @param [in] offset Cantidad de desplazamiento
     * @param [out] jPos Posición de articulaciones [°]
     * @param [out] descPos Posición cartesiana [mm]
     * @param [out] tool Sistema de coordenadas de herramienta
     * @param [out] user Sistema de coordenadas de la pieza
     * @param [out] exaxis Posición del eje extendido [mm]
     * @return Código de error
     */
    public int GetLaserSeamPos(int trackOffectType, DescPose offset, JointPos jPos, DescPose descPos, int[] tool, int[] user, ExaxisPos exaxis)

Ejemplo de código de configuración y depuración de parámetros del sensor periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testLaserConfig(Robot robot)
    {
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);

        robot.LaserTrackingSensorSamplePeriod(20);

        robot.LoadPosSensorDriver(101);
        robot.LaserTrackingLaserOnOff(0,0);

        robot.Sleep(3000);

        robot.LaserTrackingLaserOnOff(1, 0);

        robot.CloseRPC();
    }

Ejemplo de código de escaneo de trayectoria láser y reproducción de trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testLaserRecordAndReplay(Robot robot)
    {
        //Subir y cargar el archivo de protocolo abierto
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);

        for (int i=0;i<10;++i){
            JointPos startjointPos=new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose=new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
            DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserSensorRecord1(2, 10);

            JointPos endjointPos=new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose=new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 50, 100, 100, -1,0, exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserSensorRecord1(0, 10);

            robot.MoveToLaserRecordStart(1, 30);

            robot.LaserSensorReplay(10, 100);

            robot.MoveLTR();

            robot.LaserSensorRecord1(0, 10);
        }

        robot.CloseRPC();
    }

Ejemplo de código de búsqueda de posición láser y seguimiento en tiempo real
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testLasertrack(Robot robot)
    {
        //Subir y cargar el archivo de protocolo abierto
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        for(int i=0;i<10;++i){
            JointPos startjointPos=new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose=new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
            DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
            DescTran directionPoint=new DescTran();
            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3);
            robot.LaserTrackingSearchStop();

            //robot.GetRobotTeachingPoint(name, data);
            robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);
            //printf("%f, %f, %f,%f, %f, %f,%f, %f, %f,%f, %f, %f\n", data[0], data[1], data[2], data[3], data[4], data[5], data[6], data[7], data[8], data[9], data[10], data[11]);

            robot.LaserTrackingTrackOnOff(1, 3);
            //robot.LaserTrackingTrackOn(3);
            JointPos endjointPos=new JointPos(68.809,-87.100,121.120,-127.233,-95.038,-109.555);
            DescPose enddescPose=new DescPose(-103.555,-464.234,13.076,174.179,-1.344,-91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserTrackingTrackOnOff(0, 3);
            System.out.println("La iteración actual es la número "+(i+1));
        }
        robot.CloseRPC();
    }

Ejemplo de código de registro y reproducción láser + oscilación normal
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestLaserReproduceNormalWeave(Robot robot)
    {
        JointPos startjointPos = new JointPos(68.930, -70.217, -121.821, -75.522, 91.216, 137.289);
        DescPose startdescPose = new DescPose(216.097, 304.517, 34.164, -3.871, 0.792, 132.864);
        JointPos endjointPos = new JointPos(58.092, -78.843, -115.569, -73.420, 91.662, 126.457);
        DescPose enddescPose = new DescPose(296.276, 307.453, 34.803, -3.868, 0.783, 132.864);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos exaxis0Pos = new ExaxisPos(0, 174.957, 0, 0);
        ExaxisPos exaxis1Pos = new ExaxisPos(0, 105.003, 0, 0);

        robot.Sleep(1000);

        // MoveL to start position(Exaxis 0,174.957,0,0)
        int rtn = robot.MoveL(startjointPos, startdescPose, 5, 0, 100, 100, 100, -1, 0, exaxis0Pos, 0, 0, offdese, 100, 0, 0, 10);
        System.out.printf("MoveL start: %d\n", rtn);

        // Start laser record
        rtn = robot.LaserSensorRecord1(2, 10);
        System.out.printf("LaserSensorRecord start: %d\n", rtn);

        // MoveL to end position
        rtn = robot.MoveL(endjointPos, enddescPose, 5, 0, 100, 100, 100, -1, 0, exaxis0Pos, 0, 0, offdese, 100, 0, 0, 10);
        System.out.printf("MoveL end: %d\n", rtn);

        // Stop laser record
        rtn = robot.LaserSensorRecord1(0, 10);
        System.out.printf("LaserSensorRecord stop: %d\n", rtn);

        // MoveL return to start position
        rtn = robot.MoveL(startjointPos, startdescPose, 5, 0, 100, 100, 100, -1, 0, exaxis0Pos, 0, 0, offdese, 100, 0, 0, 10);
        System.out.printf("MoveL back: %d\n", rtn);

        // LIN move to laser record weld start point
        rtn = robot.MoveToLaserRecordStart(1, 30);
        System.out.printf("MoveToLaserRecordStart: %d\n", rtn);

        // Start normal weave
        rtn = robot.WeaveStart(0);
        System.out.printf("WeaveStart: %d\n", rtn);

        // Start record replay
        rtn = robot.LaserSensorRecord1(3, 10);
        System.out.printf("LaserSensorRecord replay: %d\n", rtn);

        // Laser track replay motion
        rtn = robot.MoveLTR();
        System.out.printf("MoveLTR: %d\n", rtn);

        robot.Sleep(3000);

        // Stop record replay
        rtn = robot.LaserSensorRecord1(0, 10);
        System.out.printf("LaserSensorRecord stop: %d\n", rtn);

        // Stop normal weave
        rtn = robot.WeaveEnd(0);
        System.out.printf("WeaveEnd: %d\n", rtn);

        robot.Sleep(1000);
    }
    
Ejemplo de código de registro y reproducción láser + movimiento asíncrono del eje extendido + oscilación de punto fijo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestLaserRecordReplayExaxisWithWave(Robot robot)
    {
        JointPos startjointPos = new JointPos(105.600, -65.393, -93.638, -79.687, 79.175, 134.046);
        DescPose startdescPose = new DescPose(42.376, 533.597, 362.564, -34.957, -0.564, 169.063);
        JointPos endjointPos = new JointPos(105.600, -65.393, -93.638, -79.687, 79.175, 134.046);
        DescPose enddescPose = new DescPose(42.376, 533.597, 362.564, -34.957, -0.564, 169.063);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos exaxis0Pos = new ExaxisPos(0, 134.296, 0, 0);
        ExaxisPos exaxis1Pos = new ExaxisPos(0, 74.335, 0, 0);
        // MoveJ to safe point(Exaxis 0,174.957,0,0)
        int rtn = robot.MoveJ(startjointPos, startdescPose, 5, 0, 100, 100, 50, exaxis0Pos, -1, 0, offdese);
        System.out.printf("MoveJ start: %d\n", rtn);

        // Exaxis async move to start position 105.003
        rtn = robot.ExtAxisMove(exaxis1Pos, 50, -1);
        System.out.printf("ExtAxisMove 105.003: %d\n", rtn);

        robot.Sleep(3000);

        // MoveL to start point
        rtn = robot.MoveL(endjointPos, enddescPose, 5, 0, 100, 100, 50, -1, 0, exaxis1Pos, 0, 0, offdese, 100, 0, 0, 10);
        System.out.printf("MoveL end: %d\n", rtn);

        // Start laser record
        rtn = robot.LaserSensorRecord1(2, 10);
        System.out.printf("LaserSensorRecord start: %d\n", rtn);

        // Exaxis move to 174.957 during recording
        rtn = robot.ExtAxisMove(exaxis0Pos, 50, -1);
        System.out.printf("ExtAxisMove 174.957: %d\n", rtn);

        robot.Sleep(3000);

        // Stop laser record
        rtn = robot.LaserSensorRecord1(0, 10);
        System.out.printf("LaserSensorRecord stop: %d\n", rtn);

        // Exaxis move back to 105.003, MoveL return to start point
        rtn = robot.ExtAxisMove(exaxis1Pos, 50, -1);
        System.out.printf("ExtAxisMove back: %d\n", rtn);

        // MoveL to start point
        rtn = robot.MoveL(endjointPos, enddescPose, 5, 0, 100, 100, 50, -1, 0, exaxis1Pos, 0, 0, offdese, 100, 0, 0, 10);
        System.out.printf("MoveL back: %d\n", rtn);

        // PTP move to laser record weld start point
        rtn = robot.MoveToLaserRecordStart(0, 30);
        System.out.printf("MoveToLaserRecordStart: %d\n", rtn);

        // Start replay
        rtn = robot.LaserSensorRecord1(3, 10);
        System.out.printf("LaserSensorRecord replay: %d\n", rtn);

        // Start fixed-point weave
        DescPose refPoint = new DescPose(49.381, 533.608, 362.556, -34.961, -0.564, 169.062);
        rtn = robot.OriginPointWeaveStart(0, 1, refPoint, 5);
        System.out.printf("OriginPointWeaveStart: %d\n", rtn);

        // Exaxis move to 174.957 during weaving
        rtn = robot.ExtAxisMove(exaxis0Pos, 50, -1);
        System.out.printf("ExtAxisMove replay: %d\n", rtn);

        // Stop weave
        rtn = robot.OriginPointWeaveEnd();
        System.out.printf("OriginPointWeaveEnd: %d\n", rtn);

        // Stop replay
        rtn = robot.LaserSensorRecord1(0, 10);
        System.out.printf("LaserSensorRecord stop: %d\n", rtn);

        robot.Sleep(1000);
    }

Ejemplo de código de seguimiento láser sincronizado entre el eje extendido y el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testLasertrackandExitAxis(Robot robot)
    {
        ExaxisPos startexaxisPos =new ExaxisPos( 0,0,0,0 );
        ExaxisPos seamexaxisPos = new ExaxisPos(-10,0,0,0 );
        ExaxisPos endexaxisPos = new ExaxisPos(-30, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0 );
        JointPos seamjointPos=new JointPos(0, 0, 0, 0, 0, 0);
        DescPose seamdescPose=new DescPose(0, 0, 0, 0, 0, 0);

        for(int i =0;i<10;++i) {
            //Moverse al punto de inicio que necesita búsqueda de posición
            JointPos startjointPos = new JointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose = new DescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);

            System.out.println("11111");
            //Iniciar la búsqueda de posición a lo largo de la dirección -y
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            System.out.println("2222");
            int[] tool = new int[1];
            int[] user = new int[1];
            robot.GetLaserSeamPos(0, offdese, seamjointPos, seamdescPose, tool, user, startexaxisPos);
            System.out.println(seamjointPos.J1 + ", " + seamjointPos.J2 + ", " +
                    seamjointPos.J3 + ", " + seamjointPos.J4 + ", " +
                    seamjointPos.J5 + ", " + seamjointPos.J6 + ", " +
                    seamdescPose.tran.x + ", " + seamdescPose.tran.y + ", " +
                    seamdescPose.tran.z + ", " + seamdescPose.rpy.rx + ", " +
                    seamdescPose.rpy.ry + ", " + seamdescPose.rpy.rz);
            //Si la búsqueda de posición es exitosa
            if (ret == 0) {
                //El robot y el eje extendido se mueven sincronizadamente al punto de búsqueda de posición
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);

                //Iniciar el seguimiento láser a lo largo del punto de búsqueda de posición y el movimiento sincronizado con el eje extendido
                System.out.println("3333");
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos = new JointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose = new DescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);
                ;
                //Detener el seguimiento
                robot.LaserTrackingTrackOnOff(0, 2);
                System.out.println("44444");
            }
            System.out.println("El número de ejecuciones actual es: "+i);
        }
        robot.CloseRPC();
    }

Interfaz SDK de apertura y cierre de la función de transmisión transparente del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Habilitar la función de transmisión transparente general del extremo
    * @param Habilitación, 0-cerrar, 1-abrir
    * @return Código de error
    */
    public int SetAxleGenComEnable(int mode)

Interfaz SDK de envío y recepción de datos no periódicos de la función de transmisión transparente del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Enviar datos no periódicos desde el extremo y esperar la respuesta
    * @param lenSnd Longitud de envío
    * @param sndBuff Datos de envío
    * @param lenRcv Longitud de recepción seleccionada
    * @param [out] rcvData Datos de respuesta
    * @return Código de error
    */
    public int SndRcvAxleGenComCmdData(int lenSnd, int[] sndBuff, int lenRcv, int[] rcvData)
    
Ejemplo de código de comunicación de datos no periódicos del cabezal de moxibustión Beiyikang basado en la función de transmisión transparente del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testAxleGenCom(Robot robot) {
    int[] led_on = {0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79};
    int[] led_off = {0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78};
    int[] version = {0xAB, 0xBA, 0x11, 0x00, 0x76};
    int[] state = {0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B};

    int[] rcvdata = new int[16];
    int ret = 0;
    int cnt = 1;

    JointPos p1Joint = new JointPos(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
    DescPose p1Desc = new DescPose(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);

    JointPos p2Joint = new JointPos(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
    DescPose p2Desc = new DescPose(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);

    ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
    DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

    // Activar la función de transmisión transparente del extremo
    robot.SetAxleGenComEnable(1);
    robot.SetAxleLuaEnable(1);

    while (cnt <= 10000) {
        // Leer el número de versión
        ret = robot.SndRcvAxleGenComCmdData(5, version, 10, rcvdata);
        if (ret == 0) {
            System.out.printf(" hard version : %d,hard code:%d, soft version:%d %d, soft code:%d \n",
                    rcvdata[4], rcvdata[5], rcvdata[6], rcvdata[7], rcvdata[8]);
        } else {
            System.out.println("SndRcvAxleGenComCmdData version fail: " + ret);
            break;
        }
        robot.Sleep(1000);

        // Leer el estado de presencia del cabezal de moxibustión
        ret = robot.SndRcvAxleGenComCmdData(6, state, 6, rcvdata);
        if (ret == 0) {
            System.out.printf(" state : %d \n", rcvdata[4]);
        }
        robot.Sleep(1000);

        // Encender el láser del cabezal de moxibustión
        ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, rcvdata);
        if (ret == 0) {
            System.out.printf("led on rcv data is: %d, %d, %d, %d, %d, %d\n",
                    rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        }
        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100.0, 100.0, 100.0, exaxisPos, -1.0, 0, offdese);
        robot.Sleep(4000);

        // Apagar el láser del cabezal de moxibustión
        ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, rcvdata);
        if (ret == 0) {
            System.out.printf("led off rcv data is: %d, %d, %d, %d, %d, %d \n",
                    rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        }
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100.0, 100.0, 100.0, exaxisPos, -1.0, 0, offdese);
        robot.Sleep(1000);

        System.out.println("***********************complete No. " + cnt + " SDK test*****************************");
        cnt++;
    }
    }  
    
Descargar archivo Lua de protocolo abierto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Descargar archivo Lua de protocolo abierto
    * @param fileName Nombre del archivo de protocolo abierto "CtrlDev_XXX.lua"
    * @param savePath Ruta de guardado del protocolo abierto
    * @return Código de error
    */
    public int OpenLuaDownload(string fileName, string savePath)

Eliminar archivo Lua de protocolo abierto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Eliminar archivo Lua de protocolo abierto
    * @param [in] fileName Nombre del archivo lua de protocolo abierto a eliminar "CtrlDev_XXX.lua"
    * @return Código de error
    */
    public int OpenLuaDelete(string fileName)
        
Eliminar todos los archivos Lua de protocolo abierto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Eliminar todos los archivos Lua de protocolo abierto
    * @return Código de error
    */
    public int AllOpenLuaDelete()

Ejemplo de código de carga, descarga y eliminación del protocolo abierto de periféricos del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    public static int TestCtrlOpenLuaOperate(Robot robot) {
        int rtn;
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua");
        System.out.println("OpenLuaUpload rtn is " + rtn);
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua");
        System.out.println("OpenLuaUpload rtn is " + rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/");
        System.out.println("OpenLuaDownload rtn is " + rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/");
        System.out.println("OpenLuaDownload rtn is " + rtn);

        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua");
        System.out.println("SetCtrlOpenLUAName rtn is " + rtn);
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua");
        System.out.println("SetCtrlOpenLUAName rtn is " + rtn);

        String[] names = new String[4];
        rtn = robot.GetCtrlOpenLUAName(names);
        System.out.println("GetCtrlOpenLUAName rtn is " + rtn + ", names: " +
                names[0] + ", " + names[1] + ", " + names[2] + ", " + names[3]);

        rtn = robot.LoadCtrlOpenLUA(1);
        System.out.println("LoadCtrlOpenLUA rtn is " + rtn);
        robot.Sleep(2000);
        rtn = robot.UnloadCtrlOpenLUA(1);
        System.out.println("UnloadCtrlOpenLUA rtn is " + rtn);

        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua");
        System.out.println("OpenLuaDelete rtn is " + rtn);
        rtn = robot.AllOpenLuaDelete();
        System.out.println("AllOpenLuaDelete rtn is " + rtn);

        robot.Sleep(1000);
        return 0;
    }
    
Controlar el movimiento de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Controlar el movimiento de la mano diestra
    * @param idstart Número de esclavo inicial
    * @param slaveNum Cantidad
    * @param pos Matriz de posiciones, longitud 16, rango (-360~360)
    * @param speed Matriz de porcentaje de velocidad, longitud 16, rango [0~100]
    * @param force Matriz de porcentaje de par, longitud 16, rango [0~100]
    * @param max_time Tiempo máximo de espera, rango [0~30000], unidad ms
    * @return Código de error
    */
    public int SetDexterousHandsMove(int idstart, int slaveNum, double[] pos, int[] speed, int[] force, int max_time) 
        
Controlar la activación de reinicio de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Controlar la activación de reinicio de la mano diestra
    * @param id Número de esclavo
    * @param act 0-reiniciar 1-activar
    * @return Código de error
    */
    public int SetDexterousHandsAct(int id, int act)
            
Borrar errores de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Borrar errores de la mano diestra
    * @return Código de error
    */
    public int ClearDexterousHandsError()
                
Establecer la habilitación de la función de control de acciones de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la habilitación de la función de control de acciones de la mano diestra
    * @param id Número de esclavo de la mano diestra
    * @param func Arreglo de funciones, longitud 32, Bit0-disparo de agarre, Bit1-inicialización de pinza, Bit2-configuración de posición, Bit3-configuración de velocidad, Bit4-configuración de par, Bit6-leer estado de pinza, Bit7-leer estado de inicialización, Bit8-leer código de fallo, Bit9-leer posición, Bit10-leer velocidad, Bit11-leer par, Bit12-configuración de vueltas de rotación, Bit13-configuración de velocidad de rotación, Bit14-configuración de par de rotación, Bit15-leer estado de pinza de rotación, Bit16-leer estado de inicialización de rotación, Bit17-leer vueltas de rotación, Bit18-leer velocidad de rotación, Bit19-leer par de rotación, Bit20-configuración de movimiento síncrono multieje, Bit21-instrucción de borrado de fallos, Bit22-estado de funcionamiento de eje único, Bit23-estado de funcionamiento de todos los ejes
    * @return Código de error
    */
    public int SetDexterousHandsFunc(int id, int[] func)
                    
Obtener la habilitación de la función de control de acciones de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener la habilitación de la función de control de acciones de la mano diestra
    * @param id Número del dispositivo de mano diestra
    * @param func Arreglo de parámetros de salida, longitud 32, Bit0-disparo de agarre, Bit1-inicialización de pinza, Bit2-configuración de posición, Bit3-configuración de velocidad, Bit4-configuración de par, Bit6-leer estado de pinza, Bit7-leer estado de inicialización, Bit8-leer código de fallo, Bit9-leer posición, Bit10-leer velocidad, Bit11-leer par, Bit12-configuración de vueltas de rotación, Bit13-configuración de velocidad de rotación, Bit14-configuración de par de rotación, Bit15-leer estado de pinza de rotación, Bit16-leer estado de inicialización de rotación, Bit17-leer vueltas de rotación, Bit18-leer velocidad de rotación, Bit19-leer par de rotación, Bit20-configuración de movimiento síncrono multieje, Bit21-instrucción de borrado de fallos, Bit22-estado de funcionamiento de eje único, Bit23-estado de funcionamiento de todos los ejes
    * @return Código de error
    */
    public int GetDexterousHandsFunc(int id, int[] func)
                    
Ejemplo de código de configuración y movimiento de la mano diestra del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    public static int TestDexterousHands(Robot robot) {
        int id = 1;
        int slaveNum = 4;
        int max_time = 8000;
        int[] speed = new int[16]; 
        int[] force = new int[16]; 

        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        for (int i = 0; i < 16; i++) {
            force[i] = (i < 4) ? 50 : 0;
        }

        final double[] pos = new double[16];

        JointPos j1 = new JointPos(-91.876, -85.920, 109.279, -86.239, -96.664, -28.563);
        JointPos j2 = new JointPos(-40.954, -85.920, 109.279, -86.239, -96.664, -28.563);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        int ret = robot.ClearDexterousHandsError();
        System.out.println("ClearDexterousHandsError -> " + ret);

        int[] setFunc = new int[32];
        setFunc[2] = 1;
        setFunc[4] = 1;
        setFunc[9] = 1;
        setFunc[10] = 1;
        setFunc[11] = 1;
        setFunc[22] = 1;

        ret = robot.SetDexterousHandsFunc(id, setFunc);

        int[] getFunc = new int[32];
        ret = robot.GetDexterousHandsFunc(id, getFunc);
        System.out.println("GetDexterousHandsFunc -> " + ret);
        if (ret == 0) {
            for (int i = 0; i < getFunc.length; i++) {
                System.out.print("  [" + i + "]=" + getFunc[i]);
                if ((i + 1) % 8 == 0) {
                    System.out.println();
                } else if (i < getFunc.length - 1) {
                    System.out.print(", ");
                }
            }
            if (getFunc.length % 8 != 0) {
                System.out.println();
            }
        }

        ret = robot.SetDexterousHandsAct(id, 1);
        if (ret != 0) {
            return ret;
        }

        setPositions(pos, 20, 20, 20, 20);
        ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
        robot.Sleep(5000);
        
        for (int iteration = 1; iteration <= 10; iteration++) {
            robot.MoveJ(j1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            setPositions(pos, 10, 10, 10, 10);
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
            robot.Sleep(1000);

            robot.MoveJ(j2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
            setPositions(pos, 50, 50, 50, 50);
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
            robot.Sleep(1000);
        }
        return 0;
    }