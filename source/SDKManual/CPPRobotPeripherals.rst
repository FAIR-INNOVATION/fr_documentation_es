Periféricos del robot
=====================

.. toctree:: 
    :maxdepth: 5

Configurar la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

	/**
	 * @brief  Configurar la pinza
	 * @param  [in] company  Fabricante de la pinza, 1-ROBOTIQ, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing, 6-Junduo, 7-Meituan, 8-Zengguang
	 * @param  [in] device  Número de dispositivo, ROBOTIQ(0-2F-85;1-2F-140;2-pinza de vacío;3-pinza de tres dedos;4-Hand-E),
								   Huiling(0-Z-EFG-RNM;1-Z-EFG-100;2-Z-EFG-20P;3-Z-EFG-50), Tianji(0-TEG-110), Dahuan(0-PGI-140),
								   Zhixing(0-CTPM2F20), Junduo(0-RG,1-REG), Meituan(0-MT-ACTUATOR), Zengguang(0-RM-GB-11-40-2-ITG)
	 * @param  [in] softvesion  Número de versión del software, no se utiliza por ahora, por defecto 0
	 * @param  [in] bus Posición del bus del extremo donde está conectado el dispositivo, no se utiliza por ahora, por defecto 0
	 * @return  Código de error
	 */
	errno_t SetGripperConfig(int company, int device, int softvesion, int bus);

Obtener la configuración de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

	/**
	 *@brief  Obtener la configuración de la pinza
	 *@param  [out] company  Fabricante de la pinza, 1-Robotiq, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing, 6-Junduo, 7-Meituan, 8-Zengguang
	 *@param  [out] device  Número de dispositivo, ROBOTIQ(0-2F-85;1-2F-140;2-pinza de vacío;3-pinza de tres dedos;4-Hand-E),
								   Huiling(0-Z-EFG-RNM;1-Z-EFG-100;2-Z-EFG-20P;3-Z-EFG-50), Tianji(0-TEG-110), Dahuan(0-PGI-140),
								   Zhixing(0-CTPM2F20), Junduo(0-RG,1-REG), Meituan(0-MT-ACTUATOR), Zengguang(0-RM-GB-11-40-2-ITG)
	 *@param  [out] softvesion  Número de versión del software, no se utiliza por ahora, por defecto 0
	 *@param  [out] bus Posición del bus del extremo donde está conectado el dispositivo, no se utiliza por ahora, por defecto 0
	 *@return  Código de error
	 */
	errno_t GetGripperConfig(int *company, int *device, int *softvesion, int *bus);

Activar la pinza
++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Activar la pinza
    * @param  [in] index  Número de la pinza
    * @param  [in] act  0-restablecer, 1-activar
    * @return  Código de error
    */
    errno_t  ActGripper(int index, uint8_t act);

Controlar la pinza
++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
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
	errno_t MoveGripper(int index, int pos, int vel, int force, int max_time, uint8_t block, int type, double rotNum, int rotVel, int rotTorque);

Obtener el estado de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado de movimiento de la pinza (a partir de la versión 401, el protocolo del extremo está unificado con la definición de retroalimentación del estado de movimiento de la pinza de los dispositivos ya adaptados)
    * @param [out] fault 0-sin error, otro-con error
    * @param [out] status 0-movimiento no completado, 1-movimiento completado sin detección de objeto;2-movimiento completado con detección de objeto;3-movimiento completado con detección de caída del objeto;
    * @return Código de error
    */
    errno_t GetGripperMotionDone(int& fault,int& status);

Obtener el estado de activación de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener el estado de activación de la pinza
     * @param  [out] fault  0-sin error, 1-con error
     * @param  [out] status  bit0~bit15 corresponden a los números de pinza 0~15; bit=0 no activada, bit=1 activada
     * @return  Código de error
     */
    errno_t  GetGripperActivateStatus(uint16_t *fault, uint16_t *status);

Obtener la posición de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener la posición de la pinza
     * @param  [out] fault  0-sin error, 1-con error
     * @param  [out] position  Porcentaje de posición, rango 0~100%
     * @return  Código de error
     */
    errno_t  GetGripperCurPosition(uint16_t *fault, uint8_t *position);

Obtener la velocidad de la pinza
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener la velocidad de la pinza
     * @param  [out] fault  0-sin error, 1-con error
     * @param  [out] speed  Porcentaje de velocidad, rango 0~100%
     * @return  Código de error
     */
    errno_t  GetGripperCurSpeed(uint16_t *fault, int8_t *speed);

Obtener la corriente de la pinza
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener la corriente de la pinza
     * @param  [out] fault  0-sin error, 1-con error
     * @param  [out] current  Porcentaje de corriente, rango 0~100%
     * @return  Código de error
     */
    errno_t  GetGripperCurCurrent(uint16_t *fault, int8_t *current);

Obtener la tensión de la pinza
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener la tensión de la pinza
     * @param  [out] fault  0-sin error, 1-con error
     * @param  [out] voltage  Tensión, unidad 0.1V
     * @return  Código de error
     */
    errno_t  GetGripperVoltage(uint16_t *fault, int *voltage);

Obtener la temperatura de la pinza
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Obtener la temperatura de la pinza
     * @param  [out] fault  0-sin error, 1-con error
     * @param  [out] temp  Temperatura, unidad ℃
     * @return  Código de error
     */
    errno_t  GetGripperTemp(uint16_t *fault, int *temp);

Calcular el punto de preagarre - visión
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Calcular el punto de preagarre - visión
     * @param  [in] desc_pos  Pose cartesiana del punto de agarre
     * @param  [in] zlength  Desplazamiento del eje z
     * @param  [in] zangle   Desplazamiento de rotación alrededor del eje z
     * @return  Código de error 
     */
    errno_t  ComputePrePick(DescPose *desc_pos, double zlength, double zangle, DescPose *pre_pos);

Calcular el punto de retirada - visión
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Calcular el punto de retirada - visión
     * @param  [in] desc_pos  Pose cartesiana del punto de agarre
     * @param  [in] zlength  Desplazamiento del eje z
     * @param  [in] zangle   Desplazamiento de rotación alrededor del eje z
     * @return  Código de error 
     */
    errno_t  ComputePostPick(DescPose *desc_pos, double zlength, double zangle, DescPose *post_pos);

Ejemplo de código de operación de la pinza del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestGripper(void)
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
      int company = 4;
      int device = 0;
      int softversion = 0;
      int bus = 2;
      int index = 2;
      int act = 0;
      int max_time = 30000;
      uint8_t block = 0;
      uint8_t status;
      uint16_t fault;
      uint16_t active_status = 0;
      uint8_t current_pos = 0;
      int8_t current = 0;
      int voltage = 0;
      int temp = 0;
      int8_t speed = 0;
      robot.SetGripperConfig(company, device, softversion, bus);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.GetGripperConfig(&company, &device, &softversion, &bus);
      printf("gripper config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.ActGripper(index, act);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      act = 1;
      robot.ActGripper(index, act);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.MoveGripper(index, 100, 50, 50, max_time, block, 0, 0, 0, 0);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.MoveGripper(index, 0, 50, 0, max_time, block, 0, 0, 0, 0);
      robot.GetGripperMotionDone(&fault, &status);
      printf("motion status:%u,%u\n", fault, status);
      robot.GetGripperActivateStatus(&fault, &active_status);
      printf("gripper active fault is: %u, status is: %u\n", fault, active_status);
      robot.GetGripperCurPosition(&fault, &current_pos);
      printf("fault is:%u, current position is: %u\n", fault, current_pos);
      robot.GetGripperCurCurrent(&fault, &current);
      printf("fault is:%u, current current is: %d\n", fault, current);
      robot.GetGripperVoltage(&fault, &voltage);
      printf("fault is:%u, current voltage is: %d \n", fault, voltage);
      robot.GetGripperTemp(&fault, &temp);
      printf("fault is:%u, current temperature is: %d\n", fault, temp);
      robot.GetGripperCurSpeed(&fault, &speed);
      printf("fault is:%u, current speed is: %d\n", fault, speed);
      int retval = 0;
      DescPose prepick_pose = {};
      DescPose postpick_pose = {};
      DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      retval = robot.ComputePrePick(&p1Desc, 10, 0, &prepick_pose);
      printf("ComputePrePick retval is: %d\n", retval);
      printf("xyz is: %f, %f, %f; rpy is: %f, %f, %f\n", prepick_pose.tran.x, prepick_pose.tran.y, prepick_pose.tran.z, prepick_pose.rpy.rx, prepick_pose.rpy.ry, prepick_pose.rpy.rz);
      retval = robot.ComputePostPick(&p2Desc, -10, 0, &postpick_pose);
      printf("ComputePostPick retval is: %d\n", retval);
      printf("xyz is: %f, %f, %f; rpy is: %f, %f, %f\n", postpick_pose.tran.x, postpick_pose.tran.y, postpick_pose.tran.z, postpick_pose.rpy.rx, postpick_pose.rpy.ry, postpick_pose.rpy.rz);
      robot.CloseRPC();
      return 0;
    }

Obtener el número de vueltas de la pinza rotativa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: añadido en la versión 3.7.6

.. code-block:: c++
    :linenos:

    /**
	 * @brief  Obtener el número de vueltas de la pinza rotativa
	 * @param  [out] fault  0-sin error, 1-con error
	 * @param  [out] num  Número de vueltas de rotación
	 * @return  Código de error
	 */
	errno_t GetGripperRotNum(uint16_t* fault, double* num);

Obtener la velocidad de rotación de la pinza rotativa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: V3.7.6

.. code-block:: c++
    :linenos:

    /**
	 * @brief  Obtener la velocidad de rotación de la pinza rotativa
	 * @param  [out] fault  0-sin error, 1-con error
	 * @param  [out] speed  Porcentaje de velocidad de rotación
	 * @return  Código de error
	 */
	errno_t GetGripperRotSpeed(uint16_t* fault, int* speed);

Obtener el par de rotación de la pinza rotativa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: V3.7.6

.. code-block:: c++
    :linenos:

    /**
	 * @brief  Obtener el par de rotación de la pinza rotativa
	 * @param  [out] fault  0-sin error, 1-con error
	 * @param  [out] torque  Porcentaje de par de rotación
	 * @return  Código de error
	 */
	errno_t GetGripperRotTorque(uint16_t* fault, int* torque);

Ejemplo de código de obtención del estado de la pinza rotativa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestRotGripperState(void)
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
      uint16_t fault = 0;
      double rotNum = 0.0;
      int rotSpeed = 0;
      int rotTorque = 0;
      robot.GetGripperRotNum(&fault, &rotNum);
      robot.GetGripperRotSpeed(&fault, &rotSpeed);
      robot.GetGripperRotTorque(&fault, &rotTorque);
      printf("gripper rot num : %lf, gripper rotSpeed : %d, gripper rotTorque : %d\n", rotNum, rotSpeed, rotTorque);
      robot.CloseRPC();
      return 0;
    }

Esperar el estado de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Esperar el estado de movimiento de la pinza (a partir de la versión 401, el protocolo del extremo está unificado con la definición de retroalimentación del estado de movimiento de la pinza de los dispositivos ya adaptados)
    * @param [in] staus 0-movimiento no completado, 1-movimiento completado sin detección de objeto;2-movimiento completado con detección de objeto;3-movimiento completado con detección de caída del objeto
    * @param [in] timeout Tiempo de espera agotado (ms) -1 espera permanente
    * @param [in] strategy 0-detener con error, 1-continuar en ejecución
    * @param [in] type 0-pinza paralela, 1-pinza rotativa
    * @return Código de error
    */
    errno_t GripperWaitMotionDone(int staus, int timeout, int strategy, int type);
    
Ejemplo de código de espera del estado de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetGripperMotionDone()
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
        uint8_t status = 0;
        uint16_t fault = 0;
        // Abrir la pinza
        rtn = robot.MoveGripper(2, 50, 50, 100, 30000, 0, 0, 0, 0, 0);
        printf("MoveGripper(open) ret=%d\n", rtn);
        std::this_thread::sleep_for(std::chrono::milliseconds(2000));
        robot.GetRobotRealTimeState(&pkg);
        printf(" gripper_motiondone %d)\n", pkg.gripper_motiondone);
        // Cerrar la pinza
        rtn = robot.MoveGripper(2, 90, 100, 100, 30000, 0, 0, 0, 0, 0);
        printf("MoveGripper(close) ret=%d\n", rtn);
        std::this_thread::sleep_for(std::chrono::milliseconds(2000));
        robot.GetRobotRealTimeState(&pkg);
        printf(" gripper_motiondone %d)\n", pkg.gripper_motiondone);
        // Esperar a que finalice el movimiento sin detección de objeto, tiempo de espera 5 s, detener con error
        rtn = robot.GripperWaitMotionDone(2, 5000, 0, 0);
        printf("GripperWaitMotionDone(wait for completion, no object detected) ret=%d\n", rtn);
        while (true)
        {
            robot.GetGripperMotionDone(&fault, &status);
            printf("motion status:%d,%d\n", fault, status);
            robot.GetRobotRealTimeState(&pkg);
            printf(" error code %d,%d\n", pkg.main_code, pkg.sub_code);
            std::this_thread::sleep_for(std::chrono::milliseconds(500));
        }
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Inicio y parada de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio y parada de la cinta transportadora
    * @param [in] status Estado, 1-iniciar, 0-detener 
    * @return Código de error
    */
    errno_t ConveyorStartEnd(uint8_t status);

Registro del punto de detección IO
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Registro del punto de detección IO
    * @return Código de error
    */
    errno_t ConveyorPointIORecord();

Registro del punto A
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Registro del punto A
    * @return Código de error
    */
    errno_t ConveyorPointARecord();

Registro del punto de referencia
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Registro del punto de referencia
    * @return Código de error
    */
    errno_t ConveyorRefPointRecord();

Registro del punto B
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Registro del punto B
    * @return Código de error
    */
    errno_t ConveyorPointBRecord();

Detección IO de piezas en la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Detección IO de piezas en la cinta transportadora
    * @param [in] max_t Tiempo máximo de detección, unidad ms
    * @return Código de error
    */
    errno_t ConveyorIODetect(int max_t);

Obtener la posición actual del objeto
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la posición actual del objeto
    * @param [in] mode 
    * @return Código de error
    */
    errno_t ConveyorGetTrackData(int mode);

Inicio del seguimiento de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio del seguimiento de la cinta transportadora
    * @param [in] status Estado, 1-iniciar, 0-detener 
    * @return Código de error
    */
    errno_t ConveyorTrackStart(uint8_t status);

Parada del seguimiento de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Parada del seguimiento de la cinta transportadora
    * @return Código de error
    */
    errno_t ConveyorTrackEnd();

Configuración de parámetros de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Configuración de parámetros de la cinta transportadora
    * @param [in] para[0] Canal del codificador 1~2
    * @param [in] para[1] Número de pulsos por vuelta del codificador
    * @param [in] para[2] Distancia recorrida por la cinta transportadora por vuelta del codificador
    * @param [in] para[3] Número del sistema de coordenadas de pieza; para la función de movimiento con seguimiento seleccione el número del sistema de coordenadas de pieza; para el agarre con seguimiento y el seguimiento TPD se establece en 0
    * @param [in] para[4] Si se configura visión 0 no configurar 1 configurar
    * @param [in] para[5] Relación de velocidad para la opción de agarre con seguimiento de cinta transportadora (1-100); para otras opciones el valor predeterminado es 1 
    * @return Código de error
    */
    errno_t ConveyorSetParam(float para[6], int followType = 0, int startDis = 0, int endDis = 100);

Compensación del punto de agarre de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

	/**
	 * @brief Compensación del punto de agarre de la cinta transportadora
	 * @param [in] cmp Posición de compensación double[3]{x, y, z}
	 * @return Código de error
	 */
    errno_t ConveyorCatchPointComp(double cmp[3]);

Movimiento lineal de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento lineal de la cinta transportadora
    * @param [in] status Estado, 1-iniciar, 0-detener 
    * @return Código de error
    */
    errno_t TrackMoveL(char name[32], int tool, int wobj, float vel, float acc, float ovl, float blendR, uint8_t flag, uint8_t type);

Detección de entrada de comunicación de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Detección de entrada de comunicación de la cinta transportadora
    * @param [in] timeout Tiempo de espera máximo ms
    * @return Código de error
    */
    errno_t ConveyorComDetect(int timeout);

Disparo de la detección de entrada de comunicación de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Disparo de la detección de entrada de comunicación de la cinta transportadora
    * @return Código de error
    */
    errno_t ConveyorComDetectTrigger();

Ejemplo de programa de operación de la cinta transportadora del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestConveyor(void)
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
      int retval = 0;
      retval = robot.ConveyorStartEnd(1);
      printf("ConveyorStartEnd retval is: %d\n", retval);
      retval = robot.ConveyorPointIORecord();
      printf("ConveyorPointIORecord retval is: %d\n", retval);
      retval = robot.ConveyorPointARecord();
      printf("ConveyorPointARecord retval is: %d\n", retval);
      retval = robot.ConveyorRefPointRecord();
      printf("ConveyorRefPointRecord retval is: %d\n", retval);
      retval = robot.ConveyorPointBRecord();
      printf("ConveyorPointBRecord retval is: %d\n", retval);
      retval = robot.ConveyorStartEnd(0);
      printf("ConveyorStartEnd retval is: %d\n", retval);
      retval = 0;
      float param[6] = { 1,10000,200,0,0,20 };
      retval = robot.ConveyorSetParam(param);
      printf("ConveyorSetParam retval is: %d\n", retval);
      double cmp[3] = { 0.0, 0.0, 0.0 };
      retval = robot.ConveyorCatchPointComp(cmp);
      printf("ConveyorCatchPointComp retval is: %d\n", retval);
      int index = 1;
      int max_time = 30000;
      uint8_t block = 0;
      retval = 0;
      DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      retval = robot.MoveCart(&p1Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);
      printf("MoveCart retval is: %d\n", retval);
      retval = robot.WaitMs(1);
      printf("WaitMs retval is: %d\n", retval);
      retval = robot.ConveyorIODetect(10000);
      printf("ConveyorIODetect retval is: %d\n", retval);
      retval = robot.ConveyorGetTrackData(1);
      printf("ConveyorGetTrackData retval is: %d\n", retval);
      retval = robot.ConveyorTrackStart(1);
      printf("ConveyorTrackStart retval is: %d\n", retval);
      retval = robot.TrackMoveL("cvrCatchPoint", 1, 0, 100, 100, 100, -1.0, 0, 0);
      printf("TrackMoveL retval is: %d\n", retval);
      retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0);
      printf("MoveGripper retval is: %d\n", retval);
      retval = robot.TrackMoveL("cvrRaisePoint", 1, 0, 100, 100, 100, -1.0, 0, 0);
      printf("TrackMoveL retval is: %d\n", retval);
      retval = robot.ConveyorTrackEnd();
      printf("ConveyorTrackEnd retval is: %d\n", retval);
      robot.MoveCart(&p2Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);
      retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0);
      printf("MoveGripper retval is: %d\n", retval);
      rtn = robot->ConveyorComDetect(1000 * 10);
      printf("ConveyorComDetect rtn is: %d\n", rtn);
      robot.Sleep(2000);
      rtn = robot->ConveyorComDetectTrigger();
      printf("ConveyorComDetectTrigger rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Configuración del seguimiento en el lugar de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configuración de parámetros del seguimiento en el lugar de la cinta transportadora
    * @param [in] trackMode 0-tiempo; 1-distancia; 2-tiempo y distancia, se cumple cualquiera de los dos
    * @param [in] trackTime Tiempo de seguimiento, unidad s
    * @param [in] trackDis Distancia de seguimiento, unidad mm
    * @return Código de error
    */
    int SetStationaryTrackPara(int trackMode, double trackTime, int trackDis);
    
Ejemplo de código de seguimiento en el lugar de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    int TestStationaryTrack()
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
        printf("\n========== Prueba de seguimiento estacionario de cinta transportadora ==========");
        JointPos j1(-35.146, -102.684, 120.805, -100.401, -90.295, 150.105);
        DescPose d1(-121.814, -348.341, 209.978, -173.152, -3.585, -5.446);
        ExaxisPos ex(0, 0, 0, 0);
        DescPose zeroOff(0, 0, 0, 0, 0, 0);
        int tool = 1;
        int workpiece = 1;
        float conveyorParam[6] = { 0, 10000, 200, 0, 0, 10 };
        rtn = robot.ConveyorSetParam(conveyorParam);
        robot.MoveJ(&j1, &d1, tool, workpiece, 100, 100, 100, &ex, -1, 0, &zeroOff);
        // Paso 1: Señal de control SetDO
        printf("--- Paso 1: SetDO(6,1) ---\n");
        rtn = robot.SetDO(6, 1, 0, 0);
        printf("  SetDO(6,1) rtn={0}\n", rtn);
        // Paso 2: Inicio del seguimiento de la cinta transportadora
        printf("--- Paso 2: ConveyorTrackStart(2) ---\n");
        rtn = robot.ConveyorTrackStart(2);
        printf("  ConveyorTrackStart(2) rtn={0}\n", rtn);
        // Paso 3: Detección IO de pieza
        printf("--- Paso 3: ConveyorIODetect(10000) ---\n");
        rtn = robot.ConveyorIODetect(10000);
        printf("  ConveyorIODetect(10000) rtn={0}\n", rtn);
        // Paso 4: Obtener datos de seguimiento
        printf("--- Paso 4: ConveyorGetTrackData(2) ---\n");
        rtn = robot.ConveyorGetTrackData(2);
        printf("  ConveyorGetTrackData(2) rtn={0}\n", rtn);
        // Paso 5: Configuración de parámetros de seguimiento estacionario (modo tiempo, 200s, distancia 5)
        printf("--- Paso 5: SetStationaryTrackPara(0,200,5) ---\n");
        rtn = robot.SetStationaryTrackPara(0, 5, 5);
        printf("  SetStationaryTrackPara(0,200,5) rtn={0}\n", rtn);
        // Paso 6: Ejecutar el movimiento de seguimiento estacionario
        printf("--- Paso 6: MoveStationary() ---\n");
        rtn = robot.MoveStationary();
        rtn = robot.WaitStationaryMotionDone();
        printf("  MoveStationary() rtn={0}\n", rtn);
        // Paso 7: Fin del seguimiento de la cinta transportadora
        printf("--- Paso 7: ConveyorTrackEnd() ---\n");
        rtn = robot.ConveyorTrackEnd();
        printf("  ConveyorTrackEnd() rtn={0}\n", rtn);
        // Paso 8: Señal de cierre SetDO
        printf("--- Paso 8: SetDO(6,0) ---\n");
        rtn = robot.SetDO(6, 0, 0, 0);
        printf("  SetDO(6,0) rtn={0}\n", rtn);
        printf("\n========== Prueba de seguimiento estacionario completada ==========\n");
        return 0;
    }

Configuración del sensor del extremo
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configuración del sensor del extremo
    * @param [in] idCompany Fabricante, 18-JUNKONG; 25-HUIDE
    * @param [in] idDevice Tipo, 0-JUNKONG/RYR6T.V1.0
    * @param [in] idSoftware Versión del software, 0-J1.0/HuiDe1.0 (aún no disponible)
    * @param [in] idBus Posición de montaje, 1-puerto 1 del extremo; 2-puerto 2 del extremo... 8-puerto 8 del extremo (aún no disponible)
    * @return Código de error
    */
    errno_t AxleSensorConfig(int idCompany, int idDevice, int idSoftware, int idBus);

Obtener la configuración del sensor del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Obtener la configuración del sensor del extremo
     * @param [out] idCompany Fabricante, 18-JUNKONG; 25-HUIDE
     * @param [out] idDevice Tipo, 0-JUNKONG/RYR6T.V1.0
     * @return Código de error
     */
    errno_t AxleSensorConfigGet(int& idCompany, int& idDevice);

Activación del sensor del extremo
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Activación del sensor del extremo
     * @param [in] actFlag 0-restablecer; 1-activar
     * @return Código de error
     */
    errno_t AxleSensorActivate(int actFlag);

Escritura de registros del sensor del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Escritura de registros del sensor del extremo
     * @param [in] devAddr Número de dirección del dispositivo 0-255
     * @param [in] regHAddr Dirección de registro, 8 bits altos
     * @param [in] regLAddr Dirección de registro, 8 bits bajos
     * @param [in] regNum Número de registros 0-255
     * @param [in] data1 Valor 1 a escribir en el registro
     * @param [in] data2 Valor 2 a escribir en el registro
     * @param [in] isNoBlock 0-bloqueante; 1-no bloqueante
     * @return Código de error
     */
    errno_t AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Ejemplo de código del sensor del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestAxleSensor(void)
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
      robot.AxleSensorConfig(18, 0, 0, 1);
      int company = -1;
      int type = -1;
      robot.AxleSensorConfigGet(company, type);
      printf("company is %d, type is %d\n", company, type);
      rtn = robot.AxleSensorActivate(1);
      printf("AxleSensorActivate rtn is %d\n", rtn);
      robot.Sleep(1000);
      rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
      printf("AxleSensorRegWrite rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }
        
Obtener el protocolo de periféricos del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el protocolo de periféricos del robot
    * @param [out] protocol Número de protocolo de periféricos del robot 4096-tarjeta de control del eje extendido; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Código de error
    */
    errno_t GetExDevProtocol(int *protocol);

Establecer el protocolo de periféricos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el protocolo de periféricos del robot
    * @param [in] protocol Número de protocolo de periféricos del robot 4096-tarjeta de control del eje extendido; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Código de error
    */
    errno_t SetExDevProtocol(int protocol);

Ejemplo de programa de configuración del protocolo de periféricos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:
    
    int TestExDevProtocol(void)
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
      int protocol = 4096;
      rtn = robot.SetExDevProtocol(protocol);
      std::cout << "SetExDevProtocol rtn " << rtn << std::endl;
      rtn = robot.GetExDevProtocol(&protocol);
      std::cout << "GetExDevProtocol rtn " << rtn << " protocol is: " << protocol << std::endl;
      robot.CloseRPC();
      return 0;
    }

Obtener los parámetros de comunicación del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener los parámetros de comunicación del extremo
    * @param param Parámetros de comunicación del extremo
    * @return  Código de error
    */
    errno_t GetAxleCommunicationParam(AxleComParam* param);

Establecer los parámetros de comunicación del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer los parámetros de comunicación del extremo
    * @param param  Parámetros de comunicación del extremo
    * @return  Código de error
    */
    errno_t SetAxleCommunicationParam(AxleComParam param);

Establecer el tipo de transferencia de archivos del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el tipo de transferencia de archivos del extremo
    * @param type 1-archivo de actualización de MCU; 2-archivo LUA
    * @return  Código de error
    */
    errno_t SetAxleFileType(int type);

Establecer la habilitación de ejecución de LUA en el extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la habilitación de ejecución de LUA en el extremo
    * @param enable 0-no habilitar; 1-habilitar
    * @return  Código de error
    */
    errno_t SetAxleLuaEnable(int enable);

Recuperación de errores anómalos del archivo LUA del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Recuperación de errores anómalos del archivo LUA del extremo
    * @param status 0-no recuperar; 1-recuperar
    * @return  Código de error
    */
    errno_t SetRecoverAxleLuaErr(int status);

Recuperación de errores anómalos del archivo LUA del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado de habilitación de ejecución de LUA en el extremo
    * @param status status[0]: 0-no habilitado; 1-habilitado
    * @return  Código de error
    */
    errno_t GetAxleLuaEnableStatus(int status[]);

Establecer el tipo de dispositivo del extremo habilitado para LUA en el extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el tipo de dispositivo del extremo habilitado para LUA en el extremo
    * @param forceSensorEnable Estado de habilitación del sensor de fuerza, 0-no habilitar; 1-habilitar
    * @param gripperEnable Estado de habilitación de la pinza, 0-no habilitar; 1-habilitar
    * @param IOEnable Estado de habilitación del dispositivo IO, 0-no habilitar; 1-habilitar
    * @param dexhandEnable Estado de habilitación de la mano diestra, 0-no habilitar; 1-habilitar
    * @return  Código de error
    */
    errno_t SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable, int dexhandEnable);

Establecer el tipo de dispositivo del extremo habilitado para LUA en el extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:
        
    /**
    * @brief Obtener el tipo de dispositivo del extremo habilitado para LUA en el extremo
    * @param enable enable[0]:forceSensorEnable Estado de habilitación del sensor de fuerza, 0-no habilitar; 1-habilitar
    * @param enable enable[1]:gripperEnable Estado de habilitación de la pinza, 0-no habilitar; 1-habilitar
    * @param enable enable[2]:IOEnable Estado de habilitación del dispositivo IO, 0-no habilitar; 1-habilitar
    * @param enable enable[3]:dexhandEnable Estado de habilitación de la mano diestra, 0-no habilitar; 1-habilitar
    * @return Código de error
    */
    errno_t GetAxleLuaEnableDeviceType(int* forceSensorEnable, int* gripperEnable, int* IOEnable, int* dexhandEnable);

Obtener el dispositivo del extremo configurado actualmente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el dispositivo del extremo configurado actualmente
    * @param [out] forceSensorEnable Número de dispositivo habilitado del sensor de fuerza 0-no habilitado; 1-habilitado
    * @param [out] gripperEnable Número de dispositivo habilitado de la pinza, 0-no habilitar; 1-habilitar
    * @param [out] IODeviceEnable Número de dispositivo habilitado del dispositivo IO, 0-no habilitar; 1-habilitar
    * @param [out] decHandEnable Número de dispositivo habilitado de la mano diestra, 0-no habilitar; 1-habilitar
    * @return Código de error
    */
    errno_t GetAxleLuaEnableDevice(int forceSensorEnable[], int gripperEnable[], int IODeviceEnable[], int decHandEnable[]);

Establecer la habilitación de la función de control de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la habilitación de la función de control de movimiento de la pinza
    * @param id Número de dispositivo de la pinza
    * @param func func[0]-habilitación de la pinza; func[1]-inicialización de la pinza; func[2]-establecimiento de posición; func[3]-establecimiento de velocidad; func[4]-establecimiento de par; func[6]-lectura del estado de la pinza;
        func[7]-lectura del estado de inicialización; func[8]-lectura del código de fallo; func[9]-lectura de posición; func[10]-lectura de velocidad; func[11]-lectura de par; func[12]-establecimiento del número de vueltas de la pinza rotativa; 
        func[13]-establecimiento de la velocidad de rotación de la pinza rotativa; func[14]-establecimiento del par de rotación de la pinza rotativa; func[15]-lectura del estado de la pinza rotativa; func[16]-lectura del estado de inicialización de la pinza rotativa;
        func[17]-lectura del número de vueltas de la pinza rotativa; func[18]-lectura de la velocidad de la pinza rotativa; func[19]-lectura del par de la pinza rotativa; func[20]-establecimiento del movimiento sincronizado multieje; func[21]-instrucción de borrado de fallos;
        func[22]-estado de funcionamiento de un solo eje; func[23]-estado de funcionamiento de todos los ejes;
    * @return  Código de error
    */
    errno_t SetAxleLuaGripperFunc(int id, int func[32]);

Obtener la habilitación de la función de control de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la habilitación de la función de control de movimiento de la pinza
    * @param id Número de dispositivo de la pinza
    * @param func func[0]-habilitación de la pinza; func[1]-inicialización de la pinza; func[2]-establecimiento de posición; func[3]-establecimiento de velocidad; func[4]-establecimiento de par; func[6]-lectura del estado de la pinza;
        func[7]-lectura del estado de inicialización; func[8]-lectura del código de fallo; func[9]-lectura de posición; func[10]-lectura de velocidad; func[11]-lectura de par; func[12]-establecimiento del número de vueltas de la pinza rotativa; 
        func[13]-establecimiento de la velocidad de rotación de la pinza rotativa; func[14]-establecimiento del par de rotación de la pinza rotativa; func[15]-lectura del estado de la pinza rotativa; func[16]-lectura del estado de inicialización de la pinza rotativa;
        func[17]-lectura del número de vueltas de la pinza rotativa; func[18]-lectura de la velocidad de la pinza rotativa; func[19]-lectura del par de la pinza rotativa; func[20]-establecimiento del movimiento sincronizado multieje; func[21]-instrucción de borrado de fallos;
        func[22]-estado de funcionamiento de un solo eje; func[23]-estado de funcionamiento de todos los ejes;
    * @return  Código de error
    */
    errno_t GetAxleLuaGripperFunc(int id, int func[32]);

Escritura del archivo de esclavo Ethercat del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Escritura del archivo de esclavo Ethercat del robot
    * @param type Tipo de archivo de esclavo, 1-actualizar archivo de esclavo; 2-actualizar archivo de configuración de esclavo
    * @param slaveID Número de esclavo
    * @param fileName Nombre del archivo a cargar
    * @return  Código de error
    */
    errno_t SlaveFileWrite(int type, int slaveID, std::string fileName);

Cargar el archivo de protocolo abierto LUA del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Cargar el archivo de protocolo abierto LUA del extremo
    * @param filePath Ruta y nombre del archivo lua local ".../AXLE_LUA_End_DaHuan.lua"
    * @return Código de error
    */
    errno_t AxleLuaUpload(std::string filePath);

Entrada del esclavo Ethercat del robot en modo boot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Entrada del esclavo Ethercat del robot en modo boot
    * @return  Código de error
    */
    errno_t SetSysServoBootMode();

Ejemplo de código de operación del archivo LUA del extremo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestAxleLua(void)
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
        robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua");
        AxleComParam param(7, 8, 1, 0, 5, 3, 1);
        robot.SetAxleCommunicationParam(param);
        AxleComParam getParam;
        robot.GetAxleCommunicationParam(&getParam);
        printf("GetAxleCommunicationParam param is %d %d %d %d %d %d %d\n", getParam.baudRate, getParam.dataBit, getParam.stopBit, getParam.verify, getParam.timeout, getParam.timeoutTimes, getParam.period);
        robot.SetAxleLuaEnable(1);
        int luaEnableStatus = 0;
        robot.GetAxleLuaEnableStatus(&luaEnableStatus);
        robot.SetAxleLuaEnableDeviceType(0, 1, 0, 0);
        int forceEnable = 0;
        int gripperEnable = 0;
        int ioEnable = 0;
        int dexhandEnable = 0;
        robot.GetAxleLuaEnableDeviceType(&forceEnable, &gripperEnable, &ioEnable, &dexhandEnable);
        printf("GetAxleLuaEnableDeviceType param is %d %d %d %d\n", forceEnable, gripperEnable, ioEnable, dexhandEnable);
        int func[32] = { 0,1,1,1,1,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0 };
        rtn = robot.SetAxleLuaGripperFunc(2, func);
        printf("SetAxleLuaGripperFunc rtn is %d\n", rtn);
        int getFunc[32] = { 0 };
        rtn = robot.GetAxleLuaGripperFunc(2, getFunc);
        printf("GetAxleLuaGripperFunc rtn is %d\n", rtn);
        int getforceEnable[16] = { 0 };
        int getgripperEnable[16] = { 0 };
        int getioEnable[16] = { 0 };
        int dexhandEnable1[16] = { 0 };
        robot.GetAxleLuaEnableDevice(getforceEnable, getgripperEnable, getioEnable, dexhandEnable1);
        printf("\ngetforceEnable status : ");
        for (int i = 0; i < 16; i++)
        {
            printf("%d,", getforceEnable[i]);
        }
        printf("\ngetgripperEnable status : ");
        for (int i = 0; i < 16; i++)
        {
            printf("%d,", getgripperEnable[i]);
        }
        printf("\ngetioEnable status : ");
        for (int i = 0; i < 16; i++)
        {
            printf("%d,", getioEnable[i]);
        }
        printf("\n");
        robot.ActGripper(2, 0);
        robot.Sleep(2000);
        robot.ActGripper(2, 1);
        robot.Sleep(2000);
        robot.MoveGripper(2, 1, 10, 100, 50000, 0, 0, 0, 0, 0);
        int pos = 0;
        while (true)
        {
            robot.GetRobotRealTimeState(&pkg);
            printf("gripper pos is %u\n", pkg.gripper_position);
            robot.Sleep(100);
        }
        robot.CloseRPC();
        return 0;
    }

Obtener el estado de los botones de SmartTool
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado de los botones de SmartTool
    * @param [out] state Estado de los botones del mango SmartTool;(bit0:0-comunicación normal; 1-comunicación interrumpida; bit1-deshacer operación; bit2-vaciar programa;
    bit3-tecla A; bit4-tecla B; bit5-tecla C; bit6-tecla D; bit7-tecla E; bit8-tecla IO; bit9-manual/automático; bit10-iniciar)
    * @return Código de error
    */
    errno_t GetSmarttoolBtnState(int& state);
    
Ejemplo de código de botones de SmartTool
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int main(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;

      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      robot.SetReConnectParam(true, 30000, 500);

      while (true)
      {
        int btn = 0;
        robot.GetSmarttoolBtnState(btn);
        cout << "smarttool " << std::bitset<sizeof(btn) * 8>(btn) << endl;

        Sleep(100);
      }
    }

Control de la ventosa en matriz
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Control de la ventosa en matriz
    * @param [in] slaveID Número de esclavo
    * @param [in] len Longitud
    * @param [in] ctrlValue Valor de control
    * @return Código de error
    */
    errno_t FRRobot::SetSuckerCtrl(uint8_t slaveID, uint8_t len, uint8_t ctrlValue[20]);

Obtener el estado de la ventosa en matriz
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado de la ventosa en matriz
    * @param [in] slaveID Número de esclavo
    * @param [out] state Estado de aspiración 0-liberar objeto 1-detección de aspiración de pieza correcta 2-no se ha aspirado ningún objeto 3-objeto desprendido
    * @param [out] pressValue Vacío actual, unidad kpa 
    * @param [out] error Código de error actual de la ventosa
    * @return Código de error
    */
	errno_t FRRobot::GetSuckerState(uint8_t slaveID, uint8_t* state, int* pressValue, int* error);

Esperar el estado de la ventosa
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Esperar el estado de la ventosa
    * @param [in] slaveID Número de esclavo
    * @param [in] state Estado de aspiración 0-liberar objeto 1-detección de aspiración de pieza correcta 2-no se ha aspirado ningún objeto 3-objeto desprendido
    * @param [in] ms Tiempo máximo de espera
    * @return Código de error
    */
    errno_t FRRobot::WaitSuckerState(uint8_t slaveID, uint8_t state, int ms);

Ejemplo de código de instrucciones de control de la ventosa en matriz
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    void testSucker()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;

        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        //Cargar y aplicar el archivo de protocolo abierto
        robot.OpenLuaUpload("E://项目/外设SDK/CtrlDev_sucker.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(1, "CtrlDev_sucker.lua");
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        robot.Sleep(1000);

        //Controlar la ventosa en modo difusión, aspirando según la capacidad máxima
        ctrl[0] = 1;
        robot.SetSuckerCtrl(0, 1, ctrl);

        //Supervisar en bucle el estado de la ventosa 1 y la ventosa 12
        for (int i = 0; i < 100; i++)
        {
            robot.GetSuckerState(1, &state, &pressVlaue, &error);
            printf("sucker1 state is %d, pressVlaue is %d, error num is %d\n", state, pressVlaue, error);
            robot.GetSuckerState(12, &state, &pressVlaue, &error);
            printf("sucker12 state is %d, pressVlaue is %d, error num is %d\n", state, pressVlaue, error);
            robot.Sleep(100);
        }

        //Esperar a que la ventosa 1 esté en estado de aspiración de objeto, tiempo de espera 100 ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        printf("WaitSuckerState result is  %d\n", ret);

        //Modo unidifusión para apagar las ventosas 1 y 12
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);

        robot.CloseRPC();
    }

Cargar el archivo LUA de protocolo abierto de periféricos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

	/**
	 * @brief Cargar archivo Lua
	 * @param [in] filePath Ruta y nombre del archivo lua local
	 * @return Código de error
	 */
    errno_t OpenLuaUpload(std::string filePath);

Obtener los parámetros de la placa de esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener los parámetros de la placa de esclavo
    * @param  [out] type  0-Ethercat, 1-CClink, 3-Ethercat, 4-EIP
    * @param  [out] version  Versión del protocolo
    * @param  [out] connState  0-no conectado 1-conectado
    * @return  Código de error
    */
    errno_t GetFieldBusConfig(uint8_t* type, uint8_t* version, uint8_t* connState);

Escribir DO del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Escribir DO del esclavo
    * @param  [in] DOIndex  Número de DO
    * @param  [in] wirteNum  Cantidad a escribir
    * @param  [in] status[8] Valores a escribir, máximo 8
    * @return  Código de error
    */
    errno_t FieldBusSlaveWriteDO(uint8_t DOIndex, uint8_t wirteNum, uint8_t status[8]);

Escribir AO del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Escribir AO del esclavo
    * @param  [in] AOIndex  Número de AO
    * @param  [in] wirteNum  Cantidad a escribir
    * @param  [in] status[8] Valores a escribir, máximo 8
    * @return  Código de error
    */
    errno_t FieldBusSlaveWriteAO(uint8_t AOIndex, uint8_t wirteNum, double status[8]);

Leer DI del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Leer DI del esclavo
    * @param  [in] DOIndex  Número de DI
    * @param  [in] readeNum  Cantidad a leer
    * @param  [out] status[8] Valores leídos, máximo 8
    * @return  Código de error
    */
    errno_t FieldBusSlaveReadDI(uint8_t DOIndex, uint8_t readNum, uint8_t status[8]);

Leer AI del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Leer AI del esclavo
    * @param  [in] AOIndex  Número de AI
    * @param  [in] readeNum  Cantidad a leer
    * @param  [out] status[8] Valores leídos, máximo 8
    * @return  Código de error
    */
    errno_t FieldBusSlaveReadAI(uint8_t AIIndex, uint8_t readNum, double status[8]);

Esperar entrada DI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Esperar entrada DI extendida
    * @param [in] DIIndex Número de DI
    * @param [in] status 0-nivel bajo; 1-nivel alto
    * @param [in] waitMs Tiempo máximo de espera (ms)
    * @return Código de error
    */
    errno_t FRRobot::FieldBusSlaveWaitDI(uint8_t DIIndex, bool status, int waitMs);

Esperar entrada AI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Esperar entrada AI extendida
    * @param [in] AIIndex Número de AI
    * @param [in] waitType 0-mayor que; 1-menor que
    * @param [in] value Valor de AI
    * @param [in] waitMs Tiempo máximo de espera (ms)
    * @return Código de error
    */
    errno_t FRRobot::FieldBusSlaveWaitAI(uint8_t AIIndex, uint8_t waitType, double value, int waitMs);

Ejemplo de código de instrucciones de interfaz relacionadas con el modo esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    void testFieldBusBoard()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t type = 0, version = 0, connState = 0;
        uint8_t ctrl[8];
        double ctrlAO[8];
        static uint8_t DI[8];
        static double AI[8];
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        //Subir y cargar el archivo de protocolo abierto
        robot.OpenLuaUpload("E://项目/外设SDK/CtrlDev_field.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        robot.Sleep(8000);

        //Obtener el tipo de protocolo, la versión de software y el estado de conexión con el PLC de la placa esclava
        robot.GetFieldBusConfig(&type, &version, &connState);
        printf("type is %d, version is %d,connState is %d\n", type, version, connState);

        //Escribir DO0 = 1, DO1 = 0, DO2 = 1
        ctrl[0] = 0;
        ctrl[1] = 1;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);

        //Escribir AO2 = 0x1000
        ctrlAO[0] = 0x1005;
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO);

        //Monitorear cíclicamente DI0~DI3 AI0~AI2
        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, DI);
            printf("DI0 is %d, DI1 is %d,DI2 is %d,DI3 is %d\n", DI[0], DI[1], DI[2], DI[3]);
            robot.FieldBusSlaveReadAI(0, 3, AI);
            printf("AI0 is %d, AI1 is %d,AI2 is %d\n", AI[0], AI[1], AI[2]);
            robot.Sleep(10);
        }

        //Esperar si DI0 es 1, tiempo de espera 100ms, e imprimir el resultado
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        printf("FieldBusSlaveWaitDI result is  %d\n", ret);

        //Esperar si AI0 es mayor que 400, tiempo de espera 100ms, e imprimir el resultado
        ret = robot.FieldBusSlaveWaitAI(0,0,400.00,100);
        printf("FieldBusSlaveWaitAI result is  %d\n", ret);

        robot.CloseRPC();
    }

Encendido y apagado del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
	 * @brief Función de encendido y apagado del periférico láser
	 * @param [in] OnOff 0-apagar 1-encender
	 * @param [in] weldId ID de la soldadura, por defecto 0
	 * @return Código de error
	 */
	errno_t LaserTrackingLaserOnOff(int OnOff,int weldId);
        
Inicio y fin del seguimiento láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
	 * @brief Función de inicio y fin del seguimiento láser
	 * @param [in] OnOff 0-finalizar 1-iniciar
	 * @param [in] coordId Número del sistema de coordenadas de la herramienta del periférico láser
	 * @return Código de error
	 */
 	errno_t LaserTrackingTrackOnOff(int OnOff, int coordId); 
            
Inicio de búsqueda de posición láser - dirección fija
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Búsqueda de posición láser - dirección fija
    * @param [in] direction 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
    * @param [in] vel Velocidad, unidad %
    * @param [in] distance Distancia máxima de búsqueda de posición, unidad mm
    * @param [in] distance Tiempo de espera máximo de búsqueda de posición, unidad ms
    * @param [in] posSensorNum Número de coordenada de herramienta de calibración láser
    * @return Código de error
    */
    errno_t LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum);
                
Inicio de búsqueda de posición láser - dirección de punto arbitrario
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
	 * @brief Búsqueda de posición láser - dirección arbitraria
	 * @param [in] directionPoint Coordenadas xyz del punto introducido para la búsqueda de posición
	 * @param [in] vel Velocidad, unidad %
	 * @param [in] distance Distancia máxima de búsqueda de posición, unidad mm
	 * @param [in] distance Tiempo de espera máximo de búsqueda de posición, unidad ms
	 * @param [in] posSensorNum Número de coordenada de herramienta de calibración láser
	 * @return Código de error
	 */
    errno_t LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum);
                    
Fin de búsqueda de posición láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
	 * @brief Fin de búsqueda de posición láser
	 * @return Código de error
	 */
    errno_t LaserTrackingSearchStop();

Configuración de parámetros de red del láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
	 * @brief Configuración de parámetros de red del láser
	 * @param [in] ip Dirección IP del periférico láser
	 * @param [in] port Número de puerto del periférico láser
	 * @return Código de error
	 */
    errno_t LaserTrackingSensorConfig(std::string ip, int port);
    
Configuración del período de muestreo del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configuración del período de muestreo del periférico láser
    * @param [in] period Período de muestreo del periférico láser, unidad ms
    * @return Código de error
    */
    errno_t LaserTrackingSensorSamplePeriod(int period);
        
Carga del controlador del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
	 * @brief Carga del controlador del periférico láser
	 * @param [in] type Tipo de protocolo del controlador del periférico láser 101-Ruiniu 102-Chuangxiang 103-Quanshi 104-Tongzhou 105-Aotai
	 * @return Código de error
	 */
    errno_t LoadPosSensorDriver(int type);
            
Descarga del controlador del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
	 * @brief Descarga del controlador del periférico láser
	 * @return Código de error
	 */
    errno_t UnLoadPosSensorDriver();
                
Registro de trayectoria de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Registro de trayectoria de soldadura láser
    * @param [in] status 0-detener registro 1-seguimiento en tiempo real  2-iniciar registro
    * @param [in] delayTime Tiempo de retardo, unidad ms
    * @return Código de error
    */
    errno_t LaserSensorRecord1(int status, int delayTime); 
                    
Reproducción de trayectoria de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
	 * @brief Reproducción de trayectoria de soldadura láser
	 * @param [in] delayTime Tiempo de retardo, unidad ms
	 * @param [in] speed Velocidad, unidad %
	 * @return Código de error
	 */
    errno_t LaserSensorReplay(int delayTime, double speed);
                        
Reproducción de seguimiento láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
	 * @brief Reproducción de seguimiento láser
	 * @return Código de error
	 */
    errno_t MoveLTR();
                            
Registro y reproducción de trayectoria de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Registro y reproducción de trayectoria de soldadura láser
    * @param [in] delayMode Modo 0-tiempo de retardo 1-distancia de retardo
    * @param [in] delayTime Tiempo de retardo, unidad ms
    * @param [in] delayDisExAxisNum Número de eje extendido
    * @param [in] delayDis Distancia de retardo, unidad mm
    * @param [in] sensitivePara Coeficiente de sensibilidad de compensación
    * @param [in] trackMode Tipo de seguimiento de punto fijo. 0-movimiento asíncrono del eje extendido; 1-robot
    * @param [in] triggerMode Modo de disparo del seguimiento de punto fijo. 0-duración del seguimiento; 1-IO
    * @param [in] runTime Duración del seguimiento de punto fijo del robot (s)
    * @param [in] speed Velocidad, unidad %
    * @return Código de error
    */
    errno_t LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum, double delayDis, double sensitivePara, int trackMode, int triggerMode, double runTime, double speed);
                                
Moverse al punto de inicio del registro de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Moverse al punto de inicio del registro de soldadura
    * @param [in] moveType 0-moveJ 1-moveL
    * @param [in] ovl Velocidad, unidad %
    * @return Código de error
    */
    errno_t MoveToLaserRecordStart(int moveType, double ovl);
                                    
Moverse al punto final del registro de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Moverse al punto final del registro de soldadura
    * @param [in] moveType 0-moveJ 1-moveL
    * @param [in] ovl Velocidad, unidad %
    * @return Código de error
    */
    errno_t MoveToLaserRecordEnd(int moveType, double ovl);
                                        
Moverse al punto de búsqueda de posición del sensor láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
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
    errno_t MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset);
                                            
Obtener las coordenadas del punto de búsqueda de posición del sensor láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
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
    errno_t GetLaserSeamPos(int trackOffectType, DescPose offset, JointPos& jPos, DescPose& descPos, int& tool, int& user, ExaxisPos& exaxis); 
                                                
Ejemplo de código de configuración y depuración de parámetros del sensor periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    void testLaserConfig()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;
        robot.CloseRPC();
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        //Establecer la dirección IP y el número de puerto
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        //Establecer el período de muestreo
        robot.LaserTrackingSensorSamplePeriod(20);
        //Cargar el controlador
        robot.LoadPosSensorDriver(101);
        //Apagar el periférico láser
        robot.LaserTrackingLaserOnOff(0,0);
        robot.Sleep(3000);
        //Encender el periférico láser
        robot.LaserTrackingLaserOnOff(1, 0);
        robot.CloseRPC();
    }
                                                    
Ejemplo de código de escaneo de trayectoria láser y reproducción de trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    void testLaserRecordAndReplay()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;
        robot.CloseRPC();
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        //Subir y cargar el archivo de protocolo abierto
        robot.OpenLuaUpload("E://openlua/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        int cnt = 1;
        while(cnt<31)
        { 
            //Moverse al punto de inicio del escaneo
            JointPos startjointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos(0, 0, 0, 0);
            DescPose offdese(0, 0, 0, 0, 0, 0);
            robot.MoveL(&startjointPos, &startdescPose, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
            //Iniciar el registro de trayectoria
            robot.LaserSensorRecord1(2, 10);
            //Moverse al punto final que se necesita registrar
            JointPos endjointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(&endjointPos, &enddescPose, 1, 0, 30, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
            //Detener el registro
            robot.LaserSensorRecord1(0, 10);
            //Moverse al punto de inicio de la soldadura registrada
            robot.MoveToLaserRecordStart(1, 30);
            //Iniciar la reproducción de trayectoria
            robot.LaserSensorReplay(10, 100);
            robot.MoveLTR();
            //Detener la reproducción de trayectoria
            robot.LaserSensorRecord1(0, 10);
            printf("Prueba de estabilidad de escaneo láser + reproducción de trayectoria, iteración n.º %d\n", cnt);
            cnt++;
        }
        robot.CloseRPC();
    }
                                                        
Ejemplo de código de búsqueda de posición láser y seguimiento en tiempo real
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    void testLasertrack()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;
        robot.CloseRPC();
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");

        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        //Subir y cargar el archivo de protocolo abierto
        robot.OpenLuaUpload("E://openlua/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        int cnt = 1;
        while (cnt < 2)
        {
            //Moverse al punto de inicio que necesita búsqueda de posición
            JointPos startjointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            ExaxisPos exaxisPos(0, 0, 0, 0);
            DescPose offdese(0, 0, 0, 0, 0, 0);
            DescTran directionPoint;
            robot.MoveL(&startjointPos, &startdescPose, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);

            //Iniciar la búsqueda de posición a lo largo de la dirección -y
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            //Si la búsqueda de posición es exitosa
            if (ret == 0)
            {
                //Moverse al punto de búsqueda de posición
                robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);
                //Iniciar el seguimiento láser a lo largo del punto de búsqueda de posición
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.MoveL(&endjointPos, &enddescPose, 1, 0, 20, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
                //Detener el seguimiento
                robot.LaserTrackingTrackOnOff(0, 2);

            }
            cnt++;
        }
        robot.CloseRPC();
    }
                                                            
Ejemplo de código de seguimiento láser sincronizado entre el eje extendido y el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    void testLasertrackandExitAxis()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;
        robot.CloseRPC();
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");

        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        ExaxisPos startexaxisPos = { 0,0,0,0 };
        ExaxisPos seamexaxisPos = { -10,0,0,0 };
        ExaxisPos endexaxisPos = { -30, 0, 0, 0 };
        DescPose offdese = { 0, 0, 0, 0, 0, 0 };
        JointPos seamjointPos(0, 0, 0, 0, 0, 0);
        DescPose seamdescPose(0, 0, 0, 0, 0, 0);
        
        int cnt = 1;
        while (cnt < 31)
        {
            //Moverse al punto de inicio que necesita búsqueda de posición
            JointPos startjointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);

            //Iniciar la búsqueda de posición a lo largo de la dirección -y
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            int tool = 0;
            int user = 0;
            robot.GetLaserSeamPos(0, offdese, seamjointPos, seamdescPose, tool, user, startexaxisPos);
            printf("%f, %f, %f,%f, %f, %f,%f, %f, %f,%f, %f, %f\n", seamjointPos.jPos[0], seamjointPos.jPos[1], seamjointPos.jPos[2], seamjointPos.jPos[3], seamjointPos.jPos[4], seamjointPos.jPos[5], seamdescPose.tran.x, seamdescPose.tran.y, seamdescPose.tran.z, seamdescPose.rpy.rx, seamdescPose.rpy.ry, seamdescPose.rpy.rz);

            //Si la búsqueda de posición es exitosa
            if (ret == 0)
            {
                //El robot y el eje extendido se mueven sincronizadamente al punto de búsqueda de posición
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);

                //Iniciar el seguimiento láser a lo largo del punto de búsqueda de posición y el movimiento sincronizado con el eje extendido
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);;
                //Detener el seguimiento
                robot.LaserTrackingTrackOnOff(0, 2);
            }
            cnt++;
            printf("Seguimiento láser sincronizado entre el eje extendido y el robot, iteración n.º %d\n", cnt);
        }
        robot.CloseRPC();
    } 
                                                            
Ejemplo de código de registro y reproducción láser + movimiento asíncrono del eje extendido + oscilación de punto fijo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    void TestLaserRecordReplayExaxisWithWave()
    {
    ROBOT_STATE_PKG pkg = {};
    FRRobot robot = {};
    robot.LoggerInit();
    robot.SetLoggerLevel(1);
    robot.SetReConnectParam(true, 30000, 500);
    int rtn = robot.RPC("192.168.58.2");
    if (rtn != 0)
    {
        return;
    }
    JointPos startjointPos = JointPos(105.600, -65.393, -93.638, -79.687, 79.175, 134.046);
    DescPose startdescPose = DescPose(42.376, 533.597, 362.564, -34.957, -0.564, 169.063);
    JointPos endjointPos = JointPos(105.600, -65.393, -93.638, -79.687, 79.175, 134.046);
    DescPose enddescPose = DescPose(42.376, 533.597, 362.564, -34.957, -0.564, 169.063);
    DescPose offdese = DescPose(0, 0, 0, 0, 0, 0);
    ExaxisPos exaxis0Pos(0, 134.296, 0, 0);
    ExaxisPos exaxis1Pos(0, 74.335, 0, 0);
    // MoveJ to safe point(Exaxis 0,174.957,0,0)
    rtn = robot.MoveJ(&startjointPos, &startdescPose, 5, 0, 100, 100, 50, &exaxis0Pos, -1, 0, &offdese);
    printf("MoveJ start: %d\n", rtn);
    // Exaxis async move to start position 105.003
    rtn = robot.ExtAxisMove(exaxis1Pos, 50, -1);
    printf("ExtAxisMove 105.003: %d\n", rtn);
    robot.Sleep(3000);
    // MoveL to start point
    rtn = robot.MoveL(&endjointPos, &enddescPose, 5, 0, 100, 100, 50, -1, 0, &exaxis1Pos, 0, 0, &offdese, 100, 0, 0, 10);
    printf("MoveL end: %d\n", rtn);
    // Start laser record
    rtn = robot.LaserSensorRecord1(2, 10);
    printf("LaserSensorRecord start: %d\n", rtn);
    // Exaxis move to 174.957 during recording
    rtn = robot.ExtAxisMove(exaxis0Pos, 50, -1);
    printf("ExtAxisMove 174.957: %d\n", rtn);
    robot.Sleep(3000);
    // Stop laser record
    rtn = robot.LaserSensorRecord1(0, 10);
    printf("LaserSensorRecord stop: %d\n", rtn);
    // Exaxis move back to 105.003, MoveL return to start point
    rtn = robot.ExtAxisMove(exaxis1Pos, 50, -1);
    printf("ExtAxisMove back: %d\n", rtn);
    // MoveL to start point
    rtn = robot.MoveL(&endjointPos, &enddescPose, 5, 0, 100, 100, 50, -1, 0, &exaxis1Pos, 0, 0, &offdese, 100, 0, 0, 10);
    printf("MoveL back: %d\n", rtn);
    // PTP move to laser record weld start point
    rtn = robot.MoveToLaserRecordStart(0, 30);
    printf("MoveToLaserRecordStart: %d\n", rtn);
    // Start replay
    rtn = robot.LaserSensorRecord1(3, 10);
    printf("LaserSensorRecord replay: %d\n", rtn);
    // Start fixed point weave
    DescPose refPoint = DescPose(49.381, 533.608, 362.556, -34.961, -0.564, 169.062);
    rtn = robot.OriginPointWeaveStart(0, 1, refPoint, 5);
    printf("OriginPointWeaveStart: %d\n", rtn);
    // Exaxis move to 174.957 during weaving
    rtn = robot.ExtAxisMove(exaxis0Pos, 50, -1);
    printf("ExtAxisMove replay: %d\n", rtn);
    // Stop weave
    rtn = robot.OriginPointWeaveEnd();
    printf("OriginPointWeaveEnd: %d\n", rtn);
    // Stop replay
    rtn = robot.LaserSensorRecord1(0, 10);
    printf("LaserSensorRecord stop: %d\n", rtn);
    robot.CloseRPC();
    robot.Sleep(1000);
    }
                                                            
Ejemplo de código de registro y reproducción láser + oscilación normal
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    void TestLaserReproduceNormalWeave()
    {
    ROBOT_STATE_PKG pkg = {};
    FRRobot robot = {};
    robot.LoggerInit();
    robot.SetLoggerLevel(1);
    robot.SetReConnectParam(true, 30000, 500);
    int rtn = robot.RPC("192.168.58.2");
    if (rtn != 0)
    {
        return;
    }

    JointPos startjointPos = JointPos(68.930, -70.217, -121.821, -75.522, 91.216, 137.289);
    DescPose startdescPose = DescPose(216.097, 304.517, 34.164, -3.871, 0.792, 132.864);
    JointPos endjointPos = JointPos(58.092, -78.843, -115.569, -73.420, 91.662, 126.457);
    DescPose enddescPose = DescPose(296.276, 307.453, 34.803, -3.868, 0.783, 132.864);
    DescPose offdese = DescPose(0, 0, 0, 0, 0, 0);
    ExaxisPos exaxis0Pos(0, 174.957, 0, 0);
    ExaxisPos exaxis1Pos(0, 105.003, 0, 0);

    robot.Sleep(1000);

    // MoveL to start position(Exaxis 0,174.957,0,0)
    rtn = robot.MoveL(&startjointPos, &startdescPose, 5, 0, 100, 100, 100, -1, 0, &exaxis0Pos, 0, 0, &offdese, 100, 0, 0, 10);
    printf("MoveL start: %d\n", rtn);

    // Start laser record
    rtn = robot.LaserSensorRecord1(2, 10);
    printf("LaserSensorRecord start: %d\n", rtn);

    // MoveL to end position
    rtn = robot.MoveL(&endjointPos, &enddescPose, 5, 0, 100, 100, 100, -1, 0, &exaxis0Pos, 0, 0, &offdese, 100, 0, 0, 10);
    printf("MoveL end: %d\n", rtn);

    // Stop laser record
    rtn = robot.LaserSensorRecord1(0, 10);
    printf("LaserSensorRecord stop: %d\n", rtn);

    // MoveL return to start position
    rtn = robot.MoveL(&startjointPos, &startdescPose, 5, 0, 100, 100, 100, -1, 0, &exaxis0Pos, 0, 0, &offdese, 100, 0, 0, 10);
    printf("MoveL back: %d\n", rtn);

    // LIN move to laser record weld start point
    rtn = robot.MoveToLaserRecordStart(1, 30);
    printf("MoveToLaserRecordStart: %d\n", rtn);

    // Start normal weave
    rtn = robot.WeaveStart(0);
    printf("WeaveStart: %d\n", rtn);

    // Start record replay
    rtn = robot.LaserSensorRecord1(3, 10);
    printf("LaserSensorRecord replay: %d\n", rtn);

    // Laser track replay motion
    rtn = robot.MoveLTR();
    printf("MoveLTR: %d\n", rtn);

    robot.Sleep(3000);

    // Stop record replay
    rtn = robot.LaserSensorRecord1(0, 10);
    printf("LaserSensorRecord stop: %d\n", rtn);

    // Stop normal weave
    rtn = robot.WeaveEnd(0);
    printf("WeaveEnd: %d\n", rtn);

    robot.CloseRPC();
    robot.Sleep(1000);
    }
                                                            
Apertura y cierre de la función de transmisión transparente del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Apertura y cierre de la función de transmisión transparente del extremo
    * @param [in]  Habilitación, 0-cerrar, 1-abrir
    * @return Código de error
    */
    errno_t SetAxleGenComEnable(int mode);
                                                            
Envío y recepción de datos no periódicos de la función de transmisión transparente del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:
    
    /**
    * @brief Envío y recepción de datos no periódicos de la función de transmisión transparente del extremo
    * @param [in] len_snd Longitud de envío
    * @param [in] sndBuff Datos de envío
    * @param [in] len_rcv Longitud de recepción seleccionada
    * @param [out] rcvBuff Datos de respuesta
    * @return Código de error
    */
    errno_t SndRcvAxleGenComCmdData(int lenSnd, int sndBuff[130], int lenRcv, int rcvData[130]);
                                                                
Ejemplo de código de comunicación de datos no periódicos del cabezal de moxibustión Beiyikang basado en la función de transmisión transparente del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int testAxleGenCom()
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
      int led_on[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79 };
      int led_off[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
      int version[5] = { 0xAB, 0xBA, 0x11, 0x00, 0x76 };
      int state[6] = { 0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B };
      int cycleState[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
      int rcvdata[16] = {0};
      int ret = 0;
      int cnt = 1;
      JointPos p1Joint(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
      DescPose p1Desc(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);
      JointPos p2Joint(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
      DescPose p2Desc(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      //Activar la función de transmisión transparente del extremo
      robot.SetAxleGenComEnable(1);
      robot.SetAxleLuaEnable(1);
      while (cnt <= 10000)
      {
        //Leer el número de versión
        ret = robot.SndRcvAxleGenComCmdData(5, version, 10, rcvdata);
        printf(" hard version : %d,hard code:%d, soft version:%d %d, soft code:%d \n", rcvdata[4], rcvdata[5], rcvdata[6] ,rcvdata[7], rcvdata[8]);
        if (ret != 0)
        {
          break;
        }
        robot.Sleep(1000);
        //Leer el estado de presencia del cabezal de moxibustión
        ret = robot.SndRcvAxleGenComCmdData(6, state, 6, rcvdata);
        printf(" state : %d \n", rcvdata[4]);
        robot.Sleep(1000);
        //Encender el láser del cabezal de moxibustión
        ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, rcvdata);
        printf("led on rcv data is: %d, %d, %d, %d, %d, %d  \n", rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.Sleep(4000);
        //Apagar el láser del cabezal de moxibustión
        ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, rcvdata);
        printf("led off rcv data is: %d, %d, %d, %d, %d, %d \n", rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.Sleep(1000);
        printf("***********************complate No. %d SDK test*****************************\n", cnt);
        cnt++;
      }
      robot.CloseRPC();
    }

Descargar archivo Lua de protocolo abierto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Descargar archivo Lua de protocolo abierto
    * @param [in] fileName Nombre del archivo de protocolo abierto "CtrlDev_XXX.lua"
    * @param [in] savePath Ruta de guardado del protocolo abierto
    * @return Código de error
    */
    errno_t OpenLuaDownload(std::string fileName, std::string savePath);
    
Eliminar archivo Lua de protocolo abierto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Eliminar archivo Lua de protocolo abierto
    * @param [in] fileName Nombre del archivo lua de protocolo abierto a eliminar "CtrlDev_XXX.lua"
    * @return Código de error
    */
    errno_t OpenLuaDelete(std::string fileName);
        
Eliminar todos los archivos Lua de protocolo abierto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Eliminar todos los archivos Lua de protocolo abierto
    * @return Código de error
    */
    errno_t AllOpenLuaDelete();

Ejemplo de código de carga, descarga y eliminación del protocolo abierto de periféricos del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestCtrlOpenLuaOperate()
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
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua");
        printf("OpenLuaUpload rtn is %d\n", rtn);
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua");
        printf("OpenLuaUpload rtn is %d\n", rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/");
        printf("OpenLuaDownload rtn is %d\n", rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/");
        printf("OpenLuaDownload rtn is %d\n", rtn);
        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua");
        printf("SetCtrlOpenLUAName rtn is %d\n", rtn);
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua");
        printf("SetCtrlOpenLUAName rtn is %d\n", rtn);
        std::string name[4] = {};
        rtn = robot.GetCtrlOpenLUAName(name);
        printf("ctrl open lua names : %s, %s, %s, %s\n", name[0].c_str(), name[1].c_str(), name[2].c_str(), name[3].c_str());
        rtn = robot.LoadCtrlOpenLUA(1);
        printf("LoadCtrlOpenLUA rtn is %d\n", rtn);
        robot.Sleep(2000);
        rtn = robot.UnloadCtrlOpenLUA(1);
        printf("UnloadCtrlOpenLUA rtn is %d\n", rtn);
        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua");
        printf("OpenLuaDelete rtn is %d\n", rtn);
        rtn = robot.AllOpenLuaDelete();
        printf("AllOpenLuaDelete rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }
    
Controlar el movimiento de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Controlar el movimiento de la mano diestra
    * @param [in] idstart Número de esclavo inicial
    * @param [in] slaveNum Cantidad
    * @param [in] pos Matriz de posiciones, longitud 16, rango (-360~360)
    * @param [in] speed Matriz de porcentaje de velocidad, longitud 16, rango [0~100]
    * @param [in] force Matriz de porcentaje de par, longitud 16, rango [0~100]
    * @param [in] max_time Tiempo máximo de espera, rango [0~30000], unidad ms
    * @return Código de error, devuelve 0 en caso de éxito
    */
    errno_t SetDexterousHandsMove(int idstart, int slaveNum, double pos[16], int speed[16], int force[16], int max_time);
        
Controlar la activación de reinicio de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Controlar la activación de reinicio de la mano diestra
    * @param [in] id Número de esclavo
    * @param [in] act 0-reiniciar 1-activar
    * @return Código de error, devuelve 0 en caso de éxito
    */
    errno_t SetDexterousHandsAct(int id, int act);
            
Borrar errores de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Borrar errores de la mano diestra
    * @return Código de error, devuelve 0 en caso de éxito
    */
    errno_t ClearDexterousHandsError();
                
Establecer la habilitación de la función de control de acciones de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la habilitación de la función de control de acciones de la mano diestra
    * @param [in] id Número del dispositivo de mano diestra
    * @param [in] func 0-disparo de agarre, 1-inicialización de pinza, 2-configuración de posición, 3-configuración de velocidad, 4-configuración de par, 6-leer estado de pinza, 7-leer estado de inicialización, 8-leer código de fallo, 9-leer posición, 10-leer velocidad, 11-leer par, 12-configuración de vueltas de rotación, 13-configuración de velocidad de rotación, 14-configuración de par de rotación, 15-leer estado de pinza de rotación, 16-leer estado de inicialización de rotación, 17-leer vueltas de rotación, 18-leer velocidad de rotación, 19-leer par de rotación, 20-configuración de movimiento síncrono multieje, 21-instrucción de borrado de fallos, 22-estado de funcionamiento de eje único, 23-estado de funcionamiento de todos los ejes
    * @return Código de error
    */
    errno_t SetDexterousHandsFunc(int id, int func[32]);
                    
Obtener la habilitación de la función de control de acciones de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la habilitación de la función de control de acciones de la mano diestra
    * @param [in] id Número del dispositivo de mano diestra
    * @param [out] func 0-disparo de agarre, 1-inicialización de pinza, 2-configuración de posición, 3-configuración de velocidad, 4-configuración de par, 6-leer estado de pinza, 7-leer estado de inicialización, 8-leer código de fallo, 9-leer posición, 10-leer velocidad, 11-leer par, 12-configuración de vueltas de rotación, 13-configuración de velocidad de rotación, 14-configuración de par de rotación, 15-leer estado de pinza de rotación, 16-leer estado de inicialización de rotación, 17-leer vueltas de rotación, 18-leer velocidad de rotación, 19-leer par de rotación, 20-configuración de movimiento síncrono multieje, 21-instrucción de borrado de fallos, 22-estado de funcionamiento de eje único, 23-estado de funcionamiento de todos los ejes
    * @return Código de error
    */
    errno_t GetDexterousHandsFunc(int id, int func[32]);
                        
Ejemplo de código de configuración y movimiento de la mano diestra del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestDexterousHands()
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
    int id = 1;        // Número de esclavo
    int slaveNum = 4;     // Controlar 4 dedos
    int max_time = 8000;   // Tiempo máximo de espera 8 segundos
    int speed[16] = {0};   // Matriz de velocidad, todo 0 significa usar la velocidad predeterminada
    int force[16] = {0};   // Matriz de par
    // Inicializar la matriz de par: los primeros 4 dedos se establecen al 50%, el resto a 0 (enviar valores mediante la instrucción Move)
    for (int i = 0; i < 16; i++)
    {
        force[i] = (i < 4) ? 50 : 0;
    }
    // Función auxiliar: establecer la matriz de posiciones (los primeros 4 dedos son válidos)
    double pos[16] = {0.0};
    JointPos j1(-91.876, -85.920, 109.279, -86.239, -96.664, -28.563);
    JointPos j2(-40.954, -85.920, 109.279, -86.239, -96.664, -28.563);
    ExaxisPos epos(0, 0, 0, 0);
    DescPose offset_pos(0, 0, 0, 0, 0, 0);
    printf("===== Inicio de la prueba completa de funciones de la mano diestra =====\n");
    // 1. Borrar errores
    int ret = robot.ClearDexterousHandsError();
    printf("ClearDexterousHandsError rtn %d\n", ret);
    // ========== 2. Establecer interruptores de funciones ==========
    int setFunc[32] = {0};
    setFunc[2] = 1;  // Habilitar la función de configuración de posición
    setFunc[4] = 1;  // Habilitar la función de configuración de par
    setFunc[9] = 1;  // Leer posición
    setFunc[10] = 1;  // Leer par
    setFunc[11] = 1;  // Leer estado
    setFunc[22] = 1;  // Estado de movimiento de eje único
    ret = robot.SetDexterousHandsFunc(id, setFunc);
    printf("SetDexterousHandsFunc(habilitación+inicialización+funciones de posición/velocidad/par habilitadas) rtn %d\n", ret);
    // ========== 3. Leer el estado de las funciones (verificar si la configuración ha surtido efecto) ==========
    int getFunc[32] = {0}; // GetDexterousHandsFunc devuelve 32 enteros
    ret = robot.GetDexterousHandsFunc(id, getFunc);
    printf("GetDexterousHandsFunc rtn %d\n", ret);
    if (ret == 0)
    {
        // Imprimir los 32 valores completos
        printf("GetDexterousHandsFunc devuelve los 32 valores completos:");
        for (int i = 0; i < 32; i++)
        {
        printf(" [%d]={%d}", i, getFunc[i]);
        if ((i + 1) % 8 == 0)
        {
            printf("\n");
        } 
        else if (i < 31)
        {
            printf(", ");
        }
        }
    }
    // ========== 4. Activar la mano diestra ==========
    ret = robot.SetDexterousHandsAct(id, 1);
    printf("SetDexterousHandsAct(activación) rtn %d\n", ret);
    if (ret != 0)
    {
        printf("La activación falló, prueba abortada");
        return -1;
    }
    // ========== 5. Movimiento inicial a 20° (enviar valores de posición y par mediante la instrucción Move) ==========
    memset(pos, 0, sizeof(pos));
    pos[0] = 20;
    pos[1] = 20;
    pos[2] = 20;
    pos[3] = 20;
    ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
    printf("Movimiento inicial 20° -> %d\n", ret);
    robot.Sleep(5000);
    // ========== 6. Movimiento alternativo 10 veces (10° ↔ 50°) ==========
    printf("Iniciando movimiento alternativo 10 veces...");
    for (int iteration = 1; iteration <= 10; iteration++)
    {
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        memset(pos, 0, sizeof(pos));
        pos[0] = 10;
        pos[1] = 10;
        pos[2] = 10;
        pos[3] = 10;
        ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
        printf("Moverse a 10° -> %d\n", ret);
        robot.Sleep(1000);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        memset(pos, 0, sizeof(pos));
        pos[0] = 50;
        pos[1] = 50;
        pos[2] = 50;
        pos[3] = 50;
        ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
        printf("Moverse a 50° -> %d\n", ret);
        robot.Sleep(1000);
    }
    printf("Prueba completada (configuración/lectura de interruptores de funciones + activación + 10 movimientos alternativos).");
    return 0;
    }