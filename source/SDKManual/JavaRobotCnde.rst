CNDE
=============

.. toctree:: 
    :maxdepth: 5

Configurar la retroalimentación de estado del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Configurar la retroalimentación de estado del robot
    * @param state Lista de enumeraciones de estado del robot
    * @param period Período de retroalimentación de estado, rango 8-1000
    * @return Código de error, normal-0, parámetro anómalo-4, campo de estado inexistente-18, total de bytes superior a 4K-20
    */
    public int SetRobotRealtimeStateConfig(List<RobotState> state, int period)
    
Añadir un estado del robot a la configuración de estado CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Añadir un estado del robot a la lista de configuración
    * @param state Enumeración de estado del robot
    * @return Código de error, normal-0, estado ya existente-17, campo de estado inexistente-18, superior a 4K-20
    */
    public int AddRobotRealtimeState(RobotState state)
    
Eliminar un estado del robot de la configuración de estado CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Eliminar un estado del robot de la lista de configuración
    * @param state Enumeración de estado del robot
    * @return Código de error, normal-0, estado inexistente-18, mantener al menos un estado-19
    */
    public int DeleteRobotRealtimeState(RobotState state)
        
Establecer el período de retroalimentación de estado CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el período de retroalimentación de estado CNDE
    * @param period Período de retroalimentación de estado, rango 8-1000
    * @return Código de error, normal-0, parámetro anómalo-4
    */
    public int SetRobotRealtimeStatePeriod(int period)
            
Obtener el conjunto de todos los estados y el período de la retroalimentación de estado CNDE actual
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Obtener el conjunto de todos los estados y el período actuales
     * @return Estructura de resultado de configuración que contiene la lista de estados y el período
    */
    public StateConfigResult GetRobotRealtimeStateConfig()
                
Ejemplo de código de uso de la retroalimentación de estado CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ejemplo de uso de la interfaz de configuración de estado en tiempo real CNDE
    */
    public static void TestRealtimeStateConfig(Robot robot)
    {
        
        // 1. Crear la lista de estados inicial
        List<RobotState> stateList1 = new ArrayList<>();
        stateList1.add(RobotState.ProgramState);
        stateList1.add(RobotState.RobotState);
        stateList1.add(RobotState.JointCurPos);
        stateList1.add(RobotState.ToolCurPos);
        
        // 2. Primera llamada a SetRobotRealtimeStateConfig para configurar estados y período
        int period1 = 100;  // 100ms周期
        int rtn = robot.SetRobotRealtimeStateConfig(stateList1, period1);
        System.out.printf("1. SetRobotRealtimeStateConfig (initial list, period=%d) rtn: %d%n", period1, rtn);
        
        if (rtn == 0) {
            // 3. Añadir un estado adicional
            rtn = robot.AddRobotRealtimeState(RobotState.RobotTime);
            System.out.printf("2. AddRobotRealtimeState (RobotTime) rtn: %d%n", rtn);
            
            // 4. Llamar de nuevo a SetRobotRealtimeStateConfig para reconfigurar (lista de estados diferente)
            List<RobotState> stateList2 = new ArrayList<>();
            stateList2.add(RobotState.ProgramState);
            stateList2.add(RobotState.RobotState);
            stateList2.add(RobotState.MainCode);
            stateList2.add(RobotState.SubCode);
            stateList2.add(RobotState.JointCurPos);
            stateList2.add(RobotState.ToolCurPos);
            stateList2.add(RobotState.ActualJointTorque);
            
            int period2 = 50;  // 50ms周期
            rtn = robot.SetRobotRealtimeStateConfig(stateList2, period2);
            System.out.printf("3. SetRobotRealtimeStateConfig (updated list, period=%d) rtn: %d%n", period2, rtn);
            
            // 5. Modificar el período
            int newPeriod = 80;  // 80ms周期
            rtn = robot.SetRobotRealtimeStatePeriod(newPeriod);
            System.out.printf("4. SetRobotRealtimeStatePeriod (period=%d) rtn: %d%n", newPeriod, rtn);
            
            // 6. Obtener la configuración actual e imprimirla
            Robot.StateConfigResult configResult = robot.GetRobotRealtimeStateConfig();
            System.out.println("5. GetRobotRealtimeStateConfig result:");
            System.out.printf("   - Period: %d ms%n", configResult.period);
            System.out.println("   - Configured States:");
            for (int i = 0; i < configResult.stateList.size(); i++) {
                System.out.printf("     [%d] %s%n", i, configResult.stateList.get(i));
            }
            
            rtn = robot.RPC("192.168.58.2");
            if (rtn == 0) {
                System.out.println("rpc连接 success");
            } else {
                System.out.println("rpc连接 fail");
                return;
            }
            // 等待CNDE连接建立
            System.out.println("等待CNDE连接建立...");
            while (robot.CNDEGetStateData() == null) {
                robot.Sleep(100);
            }
            System.out.println("CNDE连接已建立，开始接收数据...");

            // 7. Leer cíclicamente el estado en tiempo real para verificar si la configuración ha surtido efecto
            System.out.println("6. Reading real-time states...");
            while(true) {
                robot.Sleep(1000);
                // Obtener los datos de estado a través de CNDE
                ROBOT_STATE_PKG pkg = robot.CNDEGetStateData();
                if (pkg == null) {
                    System.out.println("状态数据为空，CNDE连接断开，等待重连");
                    continue;  // 连接断开时继续循环，等待重连
                }
                System.out.println("\n--- 机器人时间 ---");
                if (pkg.robotTime != null) {
                    System.out.println("robotTime: " + pkg.robotTime.year + "-" + pkg.robotTime.month + "-" + pkg.robotTime.day +
                            " " + pkg.robotTime.hour + ":" + pkg.robotTime.minute + ":" + pkg.robotTime.second +
                            "." + pkg.robotTime.millisecond);
                }

                System.out.println("   --- 状态信息 ---");
                System.out.printf("   program_state: %d%n", pkg.program_state);
                System.out.printf("   robot_state: %d%n", pkg.robot_state);
                System.out.printf("   main_code: %d%n", pkg.main_code);
                System.out.printf("   sub_code: %d%n", pkg.sub_code);
                System.out.println("   --- 关节位置 (actual_joint_pos) ---");
                System.out.printf("   jt_cur_pos[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_pos[0], pkg.jt_cur_pos[1], pkg.jt_cur_pos[2]);
                System.out.printf("   jt_cur_pos[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_pos[3], pkg.jt_cur_pos[4], pkg.jt_cur_pos[5]);
                System.out.println("   --- TCP位置 (actual_TCP_pos) ---");
                System.out.printf("   tl_cur_pos[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.tl_cur_pos[0], pkg.tl_cur_pos[1], pkg.tl_cur_pos[2]);
                System.out.printf("   tl_cur_pos[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.tl_cur_pos[3], pkg.tl_cur_pos[4], pkg.tl_cur_pos[5]);
                System.out.println("   --- 关节力矩 (actual_joint_torque) ---");
                System.out.printf("   jt_cur_tor[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_tor[0], pkg.jt_cur_tor[1], pkg.jt_cur_tor[2]);
                System.out.printf("   jt_cur_tor[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_tor[3], pkg.jt_cur_tor[4], pkg.jt_cur_tor[5]);
                robot.Sleep(500);
            }
        } else {
            System.out.printf("SetRobotRealtimeStateConfig failed with error: %d%n", rtn);
        }
    }