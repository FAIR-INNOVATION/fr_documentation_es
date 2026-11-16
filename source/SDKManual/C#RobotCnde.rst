CNDE
=================

.. toctree:: 
    :maxdepth: 5

Configurar la lista de datos y el período de actualización de CNDE del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Configurar la lista de datos y el período de actualización de la retroalimentación de estado en tiempo real del robot (sobrescribe la configuración anterior)
    * @param [in] states Lista de enumeraciones de estado que se van a suscribir; el orden determina el orden de disposición en el paquete de datos.
    * @param [in] period Período de actualización de datos, en milisegundos, rango de valores [8, 1000]
    * @return Devuelve 0 en caso de éxito; en caso de fallo devuelve un código de error negativo (como ERR_STATE_INVALID, ERR_PARAM_VALUE, etc.)
    */
    public int SetRobotRealtimeStateConfig(List<RobotState> states, int period)

Añadir un elemento de estado a la lista de retroalimentación de estado existente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Añadir un elemento de estado a la lista de retroalimentación de estado existente
    * @param [in] state Valor de enumeración del estado que se va a añadir.
    * @return Devuelve 0 en caso de éxito; en caso de fallo devuelve un código de error negativo (como ERR_STATE_ALREADY_EXISTS, ERR_STATE_INVALID, etc.)
    */
    public int AddRobotRealtimeState(RobotState state)
    
Eliminar un elemento de estado de la lista de retroalimentación de estado existente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Eliminar un elemento de estado de la lista de retroalimentación de estado existente (se conserva al menos un estado)
    * @param [in] state Valor de enumeración del estado que se va a eliminar
    * @return Devuelve 0 en caso de éxito; en caso de fallo devuelve un código de error negativo (como ERR_STATE_INVALID, ERR_NEED_AT_LEAST_ONE_STATE)
    */
    public int DeleteRobotRealtimeState(RobotState state)
        
Modificar únicamente el período de actualización de la retroalimentación de estado
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

     /**
    * @brief Modificar únicamente el período de actualización de la retroalimentación de estado, sin cambiar la lista de estados
    * @param [in] period Nuevo período de actualización, en milisegundos, rango de valores [8, 1000]
    * @return Devuelve 0 en caso de éxito; en caso de fallo devuelve un código de error negativo (como ERR_PARAM_VALUE)
    */
    public int SetRobotRealtimeStatePeriod(int period)
        
Obtener la lista de retroalimentación de estado y el período de actualización configurados actualmente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la lista de retroalimentación de estado y el período de actualización configurados actualmente
    * @param [out] states Devuelve la lista de enumeraciones de estado suscritas actualmente
    * @param [out] period Devuelve el período de actualización de datos actual, en milisegundos
    * @return Devuelve 0 en caso de éxito; en caso de fallo devuelve un código de error negativo.
    */
    public int GetRobotRealtimeStateConfig(out List<RobotState> states, out int period)

Ejemplo de código SDK relacionado con la configuración de CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private async void TestRobotRealtimeStates()
    {
        // 1. Definir los campos de estado que se van a suscribir
        List<RobotState> requiredStates = new List<RobotState>
        {
            RobotState.JointCurPos,
            RobotState.ToolCurPos, 
            RobotState.JointDriverTemperature,
            RobotState.RobotTime,
        };

        // 2. Configurar la retroalimentación de estado (período 8 ms)
        int periodMs = 8;
        int ret = robot.SetRobotRealtimeStateConfig(requiredStates, periodMs);
        if (ret != 0)
        {
            Console.WriteLine($"配置状态失败，错误码: {ret}");
            return;
        }
        Console.WriteLine($"状态配置成功，共 {requiredStates.Count} 个字段，周期 {periodMs} ms");

        // Verificar si la configuración ha surtido efecto
        List<RobotState> actualStates;
        int actualPeriod;
        robot.GetRobotRealtimeStateConfig(out actualStates, out actualPeriod);
        Console.WriteLine($"实际生效的状态数: {actualStates.Count}, 周期: {actualPeriod} ms");
        Thread.Sleep(3000);
        // 3. Establecer la conexión RPC (el handshake de CNDE se completa automáticamente de forma interna)
        robot.SetReconnectParam(true, 10, 1000);
        ret = robot.RPC("192.168.58.2");  // Modifique según la IP real del robot
        if (ret != 0)
        {
            Console.WriteLine($"RPC 连接失败，错误码: {ret}");
            return;
        }
        // 4. Leer e imprimir cíclicamente los datos de estado
        DateTime startTime = DateTime.Now;
        const int durationSeconds = 500;

        while ((DateTime.Now - startTime).TotalSeconds < durationSeconds)
        {
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            ret = robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($"GetRobotRealTimeState: {ret}");

            //Posición de articulaciones (grados)
            if (pkg.jt_cur_pos != null && pkg.jt_cur_pos.Length >= 6)
                Console.WriteLine($"关节位置(°): J1={pkg.jt_cur_pos[0]:F2}, J2={pkg.jt_cur_pos[1]:F2}, J3={pkg.jt_cur_pos[2]:F2}, J4={pkg.jt_cur_pos[3]:F2}, J5={pkg.jt_cur_pos[4]:F2}, J6={pkg.jt_cur_pos[5]:F2}");

            //Pose TCP (mm /°)
            if (pkg.tl_cur_pos != null && pkg.tl_cur_pos.Length >= 6)
                Console.WriteLine($"TCP位姿(mm/°): X={pkg.tl_cur_pos[0]:F2}, Y={pkg.tl_cur_pos[1]:F2}, Z={pkg.tl_cur_pos[2]:F2}, RX={pkg.tl_cur_pos[3]:F2}, RY={pkg.tl_cur_pos[4]:F2}, RZ={pkg.tl_cur_pos[5]:F2}");
    
            // Temperatura de las articulaciones
            if (pkg.jointDriverTemperature != null && pkg.jointDriverTemperature.Length >= 6)
                Console.WriteLine($"关节温度(°C): J1={pkg.jointDriverTemperature[0]:F2}, J2={pkg.jointDriverTemperature[1]:F2}, J3={pkg.jointDriverTemperature[2]:F2}, J4={pkg.jointDriverTemperature[3]:F2}, J5={pkg.jointDriverTemperature[4]:F2}, J6={pkg.jointDriverTemperature[5]:F2}");

            // Hora del robot
            Console.WriteLine($"机器人时间: {pkg.robotTime.year}-{pkg.robotTime.mouth:D2}-{pkg.robotTime.day:D2} {pkg.robotTime.hour:D2}:{pkg.robotTime.minute:D2}:{pkg.robotTime.second:D2}.{pkg.robotTime.millisecond:D3}");

            await Task.Delay(100);
        }

        // 5. Desconectar
        robot.CloseRPC();
    }

Ejemplo de código SDK para añadir/eliminar estados de configuración de CNDE y establecer el período de comunicación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private async void TestAddDeleteCNDE()
    {
        List<RobotState> finalStates;
        int finalPeriod;
        // Configuración inicial: no solicitar ningún estado (configuración predeterminada)
        List<RobotState> emptyStates = new List<RobotState>();
        int ret = robot.SetRobotRealtimeStateConfig(emptyStates, 20);

        robot.SetRobotRealtimeStatePeriod(10);
        // Eliminar dos estados
        ret = robot.DeleteRobotRealtimeState(RobotState.JointCurPos);
        Console.WriteLine($"删除 JointCurPos 结果: {ret}");
        ret = robot.DeleteRobotRealtimeState(RobotState.ToolCurPos);
        Console.WriteLine($"删除 ToolCurPos 结果: {ret}");
        // Añadir un estado
        ret = robot.AddRobotRealtimeState(RobotState.CollisionLevel);
        Console.WriteLine($"新增 CollisionLevel 结果: {ret}");

        // Obtener la lista de configuración actual y reenviarla
        List<RobotState> currentStates;
        int currentPeriod;
        robot.GetRobotRealtimeStateConfig(out currentStates, out currentPeriod);
        Console.WriteLine($"当前配置状态数: {currentStates.Count}");
        ret = robot.SetRobotRealtimeStateConfig(currentStates, currentPeriod);
        Console.WriteLine($"应用新配置结果: {ret}"); Console.WriteLine($"初始配置结果: {ret}");
        robot.GetRobotRealtimeStateConfig(out finalStates, out finalPeriod);
        Console.WriteLine($"配置状态数量: {finalStates.Count}");
        foreach (var s in finalStates) Console.WriteLine($"  {s}");
        Console.WriteLine($"周期: {finalPeriod} ms");

        Thread.Sleep(1000);
        //  Establecer la conexión RPC (conexión automática a CNDE de forma interna)
        robot.SetReconnectParam(true, 100, 1000);
        ret = robot.RPC("192.168.58.2");
        if (ret != 0)
        {
            Console.WriteLine($"RPC 连接失败: {ret}");
            return;
        }

        // Imprimir cíclicamente los estados eliminados y añadidos; los estados eliminados se imprimen como 0, los estados añadidos pueden obtenerse normalmente en tiempo real
        DateTime lastTime = DateTime.Now;
        int frameCount = 0;
        DateTime startTime = DateTime.Now;
        while ((DateTime.Now - startTime).TotalSeconds < 10)
        {
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.GetRobotRealTimeState(ref pkg);
            DateTime now = DateTime.Now;
            double interval = (now - lastTime).TotalMilliseconds;
            lastTime = now;
            frameCount++;

            if (pkg.jt_cur_pos != null && pkg.jt_cur_pos.Length >= 6)
            {
                Console.WriteLine($"  关节位置(°): J1={pkg.jt_cur_pos[0]:F2}, J2={pkg.jt_cur_pos[1]:F2}, J3={pkg.jt_cur_pos[2]:F2}, J4={pkg.jt_cur_pos[3]:F2}, J5={pkg.jt_cur_pos[4]:F2}, J6={pkg.jt_cur_pos[5]:F2}");
            }
            if (pkg.tl_cur_pos != null && pkg.tl_cur_pos.Length >= 6)
            {
                Console.WriteLine($"  TCP位姿(mm/°): X={pkg.tl_cur_pos[0]:F2}, Y={pkg.tl_cur_pos[1]:F2}, Z={pkg.tl_cur_pos[2]:F2}, RX={pkg.tl_cur_pos[3]:F2}, RY={pkg.tl_cur_pos[4]:F2}, RZ={pkg.tl_cur_pos[5]:F2}");
            }
            // Nivel de colisión
            if (pkg.collisionLevel != null && pkg.collisionLevel.Length >= 6)
                Console.WriteLine($"碰撞等级: J1={pkg.collisionLevel[0]}, J2={pkg.collisionLevel[1]}, J3={pkg.collisionLevel[2]}, J4={pkg.collisionLevel[3]}, J5={pkg.collisionLevel[4]}, J6={pkg.collisionLevel[5]}");

            await Task.Delay(50);
        }
        //Desconectar
        robot.CloseRPC();
        Console.WriteLine("测试完成。");
    }