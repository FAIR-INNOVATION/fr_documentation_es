CNDE
=============

.. toctree:: 
    :maxdepth: 5

Configurar la retroalimentación de estado CNDE del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Configurar la retroalimentación de estado CNDE del robot
    * @param [in] states Lista de estados configurables
    * @param [in] period Período de retroalimentación de estado
    * @return Código de error
    */
    errno_t SetRobotRealtimeStateConfig(std::vector<RobotState> states, int period);
    
Añadir un estado del robot a la configuración de estados CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Añadir un estado del robot a la configuración de estados CNDE
    * @param [in] state Estado configurable
    * @return Código de error
    */
    errno_t AddRobotRealtimeState(RobotState state);
        
Eliminar un estado del robot de la configuración de estados CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Eliminar un estado del robot de la configuración de estados CNDE
    * @param [in] state Estado configurable
    * @return Código de error
    */
    errno_t DeleteRobotRealtimeState(RobotState state);
            
Establecer el período de retroalimentación de estado CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el período de retroalimentación de estado CNDE
    * @param [in] period Período de retroalimentación de estado configurable 4-1000ms
    * @return Código de error
    */
    errno_t SetRobotRealtimeStatePeriod(int period);
                
Obtener el conjunto de todos los estados y el período de la retroalimentación de estado CNDE actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el conjunto de todos los estados y el período de la retroalimentación de estado CNDE actual
    * @param [out] states Lista de estados configurables
    * @param [out] period Período de retroalimentación de estado configurable
    * @return Código de error
    */
    errno_t GetRobotRealtimeStateConfig(std::vector<RobotState>& states, int& period);
                
Ejemplo de código de uso de la retroalimentación de estado CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int PrintRobotPosVelTorque() 
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        int rtn = 0;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        std::vector<RobotState> states = { RobotState::JointCurPos, RobotState::TargetJointPos,
        RobotState::ToolCurPos, RobotState::TargetTCPPos,
        RobotState::FlangeCurPos, RobotState::ActualTCPForce,
        RobotState::ActualJointVel, RobotState::TargetJointVel,
        RobotState::ActualJointAcc, RobotState::TargetJointAcc,
        RobotState::TargetTCPCmpSpeed, RobotState::ActualTCPCmpSpeed,
        RobotState::TargetTCPSpeed, RobotState::ActualTCPSpeed,
        RobotState::ActualJointTorque, RobotState::JointDriverTorque, RobotState::TargetJointTorque,
        RobotState::TargetJointCurrent, RobotState::ActualJointCurrent };
        rtn = robot.SetRobotRealtimeStateConfig(states, 8);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            printf("robot RPC failed\n");
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        std::vector<RobotState> getConfigState = {};
        int getPeriod = 0;
        rtn = robot.GetRobotRealtimeStateConfig(getConfigState, getPeriod);
        printf("GetRobotRealtimeStateConfig rtn is %d; period is %d\n", rtn, getPeriod);
        for (int k = 0; k < getConfigState.size(); k++)
        {
            printf("getConfigState include %d\n", getConfigState[k]);
        }
        while (true)
        {
            robot.GetRobotRealTimeState(&pkg);
            printf("joint actual pos is %f %f %f %f %f %f\n", pkg.jt_cur_pos[0], pkg.jt_cur_pos[1], pkg.jt_cur_pos[2], pkg.jt_cur_pos[3], pkg.jt_cur_pos[4], pkg.jt_cur_pos[5]);
            printf("joint target pos is %f %f %f %f %f %f\n", pkg.targetJointPos[0], pkg.targetJointPos[1], pkg.targetJointPos[2], pkg.targetJointPos[3], pkg.targetJointPos[4], pkg.targetJointPos[5]);
            printf("tool actual pos is %f %f %f %f %f %f\n", pkg.tl_cur_pos[0], pkg.tl_cur_pos[1], pkg.tl_cur_pos[2], pkg.tl_cur_pos[3], pkg.tl_cur_pos[4], pkg.tl_cur_pos[5]);
            printf("tool target pos is %f %f %f %f %f %f\n", pkg.targetTCPPos[0], pkg.targetTCPPos[1], pkg.targetTCPPos[2], pkg.targetTCPPos[3], pkg.targetTCPPos[4], pkg.targetTCPPos[5]);
            printf("joint actual velocity is %f %f %f %f %f %f\n", pkg.actual_qd[0], pkg.actual_qd[1], pkg.actual_qd[2], pkg.actual_qd[3], pkg.actual_qd[4], pkg.actual_qd[5]);
            printf("joint target velocity is %f %f %f %f %f %f\n", pkg.targetJointVel[0], pkg.targetJointVel[1], pkg.targetJointVel[2], pkg.targetJointVel[3], pkg.targetJointVel[4], pkg.targetJointVel[5]);
            printf("joint actual acc is %f %f %f %f %f %f\n", pkg.actual_qdd[0], pkg.actual_qdd[1], pkg.actual_qdd[2], pkg.actual_qdd[3], pkg.actual_qdd[4], pkg.actual_qdd[5]);
            printf("joint target acc is %f %f %f %f %f %f\n", pkg.targetJointAcc[0], pkg.targetJointAcc[1], pkg.targetJointAcc[2], pkg.targetJointAcc[3], pkg.targetJointAcc[4], pkg.targetJointAcc[5]);
            printf("tcp actual cmp speed is %f %f\n", pkg.actual_TCP_CmpSpeed[0], pkg.actual_TCP_CmpSpeed[1]);
            printf("tcp target cmp speed is %f %f\n", pkg.target_TCP_CmpSpeed[0], pkg.target_TCP_CmpSpeed[1]);
            printf("tcp actual velocity is %f %f %f %f %f %f\n", pkg.actual_TCP_Speed[0], pkg.actual_TCP_Speed[1], pkg.actual_TCP_Speed[2], pkg.actual_TCP_Speed[3], pkg.actual_TCP_Speed[4], pkg.actual_TCP_Speed[5]);
            printf("tcp target velocity is %f %f %f %f %f %f\n", pkg.target_TCP_Speed[0], pkg.target_TCP_Speed[1], pkg.target_TCP_Speed[2], pkg.target_TCP_Speed[3], pkg.target_TCP_Speed[4], pkg.target_TCP_Speed[5]);
            printf("joint actual torque is %f %f %f %f %f %f\n", pkg.jt_cur_tor[0], pkg.jt_cur_tor[1], pkg.jt_cur_tor[2], pkg.jt_cur_tor[3], pkg.jt_cur_tor[4], pkg.jt_cur_tor[5]);
            printf("joint driver torque is %f %f %f %f %f %f\n", pkg.jointDriverTorque[0], pkg.jointDriverTorque[1], pkg.jointDriverTorque[2], pkg.jointDriverTorque[3], pkg.jointDriverTorque[4], pkg.jointDriverTorque[5]);
            printf("joint target torque is %f %f %f %f %f %f\n", pkg.jt_tgt_tor[0], pkg.jt_tgt_tor[1], pkg.jt_tgt_tor[2], pkg.jt_tgt_tor[3], pkg.jt_tgt_tor[4], pkg.jt_tgt_tor[5]);
            printf("joint actual current is %f %f %f %f %f %f\n", pkg.actualJointCurrent[0], pkg.actualJointCurrent[1], pkg.actualJointCurrent[2], pkg.actualJointCurrent[3], pkg.actualJointCurrent[4], pkg.actualJointCurrent[5]);
            printf("joint target current is %f %f %f %f %f %f\n", pkg.targetJointCurrent[0], pkg.targetJointCurrent[1], pkg.targetJointCurrent[2], pkg.targetJointCurrent[3], pkg.targetJointCurrent[4], pkg.targetJointCurrent[5]);
            printf("flange actual pos is %f %f %f %f %f %f\n", pkg.flange_cur_pos[0], pkg.flange_cur_pos[1], pkg.flange_cur_pos[2], pkg.flange_cur_pos[3], pkg.flange_cur_pos[4], pkg.flange_cur_pos[5]);
            printf("tcp actual force is %f %f %f %f %f %f\n\n", pkg.actualTCPForce[0], pkg.actualTCPForce[1], pkg.actualTCPForce[2], pkg.actualTCPForce[3], pkg.actualTCPForce[4], pkg.actualTCPForce[5]);
            robot.Sleep(300);
        }
        robot.Sleep(1000);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }