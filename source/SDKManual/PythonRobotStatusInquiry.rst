Consulta del estado del robot
==============================

.. toctree:: 
    :maxdepth: 5

Obtener la posición articular actual (ángulo)
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualJointPosDegree(flag=1)``"
    "Descripción", "Obtener la posición articular actual (ángulo)"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante，predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``：posición articular actual (ángulo)"

Obtener la posición articular actual (radianes)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualJointPosRadian(flag=1)``"
    "Descripción", "Obtener la posición articular actual (radianes)"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``：posición articular actual (radianes)"

Obtener la velocidad de retroalimentación articular-deg/s
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualJointSpeedsDegree(flag=1)``"
    "Descripción", "Obtener la velocidad de retroalimentación articular-deg/s"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``speed=[j1,j2,j3,j4,j5,j6]``：velocidad de retroalimentación articular-deg/s"

Obtener la aceleración de retroalimentación articular-deg/s^2
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualJointAccDegree(flag=1)``"
    "Descripción", "Obtener la aceleración de retroalimentación articular-deg/s^2"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``acc=[j1,j2,j3,j4,j5,j6]``：aceleración de retroalimentación articular-deg/s^2"

Obtener la velocidad compuesta de comando TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTargetTCPCompositeSpeed(flag=1)``"
    "Descripción", "Obtener la velocidad compuesta de comando TCP"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``[tcp_speed,ori_speed]``：tcp_speed-velocidad lineal compuesta ori_speed-velocidad de orientación compuesta"

Obtener la velocidad compuesta de retroalimentación TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualTCPCompositeSpeed(flag=1)``"
    "Descripción", "Obtener la velocidad compuesta de retroalimentación TCP"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``[tcp_speed,ori_speed]``：tcp_speed-velocidad lineal compuesta ori_speed-velocidad de orientación compuesta"

Obtener la velocidad de comando TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTargetTCPSpeed(flag=1)``"
    "Descripción", "Obtener la velocidad de comando TCP"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``speed=[x,y,z,rx,ry,rz]``：velocidad de comando TCP，mm/s"

Obtener la velocidad de retroalimentación TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualTCPSpeed(flag=1)``"
    "Descripción", "Obtener la velocidad de retroalimentación TCP"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``speed=[x,y,z,rx,ry,rz]``：velocidad de retroalimentación TCP"

Obtener la pose actual de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualTCPPose(flag=1)``"
    "Descripción", "Obtener la pose actual de la herramienta"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``：pose actual de la herramienta"

Obtener el número del sistema de coordenadas de herramienta actual
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualTCPNum(flag=1)``"
    "Descripción", "Obtener el número del sistema de coordenadas de herramienta actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``tool_id``:número del sistema de coordenadas de herramienta"

Obtener el número del sistema de coordenadas de pieza actual
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualWObjNum(flag=1)``"
    "Descripción", "Obtener el número del sistema de coordenadas de pieza actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante  predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``wobj_id``:número del sistema de coordenadas de pieza"

Obtener la pose actual de la brida del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualToolFlangePose(flag=1)``"
    "Descripción", "Obtener la pose actual de la brida del extremo"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``flag``：0-bloqueante，1-no bloqueante  predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``flange_pose=[x,y,z,rx,ry,rz]``：pose actual de la brida del extremo"

Obtener el par articular actual
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetJointTorques(flag=1)``"
    "Descripción", "Obtener el par articular actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "``flag``：0-bloqueante，1-no bloqueante  predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``torques=[j1,j2,j3,j4,j5,j6]``：par articular"

Obtener la hora del sistema
++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSystemClock()``"
    "Descripción", "Obtener la hora del sistema"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``t_ms``: hora del sistema, unidad [ms]"

Sincronizar la hora del sistema con el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobottime(self)``"
    "Descripción", "Obtener la hora actual del sistema del PC anfitrión y enviarla al robot, sincronizar la hora del sistema (debido a las limitaciones del sistema QNX, la precisión de sincronización es de nivel de minuto)"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Ejemplo de código para sincronizar la hora del sistema con el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    from datetime import datetime, timedelta


    def main():
        # Establecer conexión con el controlador del robot
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)

        print("========== Prueba de establecimiento y obtención de la hora del robot ==========")

        # Obtener el reloj del sistema antes de configurar
        ret, t_ms = robot.GetSystemClock()
        if ret == 0 and t_ms is not None:
            print(f"system clock : {t_ms}")
            # El robot almacena UTC+8, convertir de vuelta a la hora del PC (restar 8 horas)
            robot_time = datetime.fromtimestamp(t_ms / 1000.0) - timedelta(hours=8)
            print(f"BEFORE Robot Time: {robot_time.strftime('%Y-%m-%d %H:%M:%S')}")
        else:
            print(f"GetSystemClock failed, ret:{ret}")

        # Establecer la hora del robot a la hora del PC
        ret = robot.SetRobottime()
        print(f"SetRobottime ret: {ret}")

        # Obtener la hora del robot después de configurar
        ret, t_ms_after = robot.GetSystemClock()
        if ret == 0 and t_ms_after is not None:
            print(f"system clock : {t_ms_after}")
            # El robot almacena UTC+8, convertir de vuelta a la hora del PC (restar 8 horas)
            robot_time = datetime.fromtimestamp(t_ms_after / 1000.0) - timedelta(hours=8)

            # Hora del PC - mostrar hora local del sistema
            pc_time = datetime.now()

            # Truncar ambas horas a minutos
            pc_minute = pc_time.replace(second=0, microsecond=0)
            robot_minute = robot_time.replace(second=0, microsecond=0)

            # Comparar consistencia
            is_consistent = (pc_minute == robot_minute)
            if is_consistent:
                print(f"Consistent     | PC time: {pc_minute.strftime('%Y-%m-%d %H:%M')}  | Robot time: {robot_minute.strftime('%Y-%m-%d %H:%M')}")
            else:
                print(f"Inconsistent | PC time: {pc_minute.strftime('%Y-%m-%d %H:%M')}  | Robot time: {robot_minute.strftime('%Y-%m-%d %H:%M')}")
        else:
            print(f"GetSystemClock failed, ret:{ret}")

        # Cerrar conexión
        robot.CloseRPC()


    if __name__ == "__main__":
        main()

Consultar si el movimiento del robot ha finalizado
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotMotionDone()``"
    "Descripción", "Consultar si el movimiento del robot ha finalizado"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``state``: estado de movimiento del robot，0-no completado，1-completado"

Consultar la longitud de la caché de la cola de movimiento del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetMotionQueueLength()``"
    "Descripción", "Consultar la longitud de la caché de la cola de movimiento del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``len``：longitud de la caché"

Obtener el estado de parada de emergencia del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotEmergencyStopState()``"
    "Descripción", "Obtener el estado de parada de emergencia del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``state``：estado de parada de emergencia，0-no parada de emergencia，1-parada de emergencia"

Obtener el estado de comunicación entre el SDK y el robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSDKComState()``"
    "Descripción", "Obtener el estado de comunicación entre el SDK y el robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``state``：estado de comunicación，0-comunicación normal，1-comunicación anormal"

Obtener la señal de parada de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSafetyStopState()``"
    "Descripción", "Obtener la señal de parada de seguridad"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``[si0_state,si1_state]``：si0_state señal de parada de seguridad SI0，0-inválida，1-válida si1_state señal de parada de seguridad SI1，0-inválida，1-válida"

Obtener la temperatura actual del accionamiento articular(℃)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetJointDriverTemperature()``"
    "Descripción", "Obtener la temperatura actual del accionamiento articular(℃)"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``data=[t1,t2,t3,t4,t5,t6]``：temperatura actual de cada articulación"

Obtener el par actual del accionamiento articular(Nm)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetJointDriverTorque()``"
    "Descripción", "Obtener el par actual del accionamiento articular(Nm)"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``data=[j1,j2,j3,j4,j5,j6]``：par articular [fx,fy,fz,tx,ty,tz]"

Obtener el estado del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotRealTimeState()``"
    "Descripción", "Obtener el estado del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``robot_state_pkg``：estructura del estado del robot"

Ejemplo de código de consulta del estado del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    error,[yangle, zangle] = robot.GetRobotInstallAngle()
    print(f"yangle:{yangle},zangle:{zangle}")
    error,j_deg = robot.GetActualJointPosDegree(0)
    print(f"joint pos deg:{j_deg[0]},{j_deg[1]},{j_deg[2]},{j_deg[3]},{j_deg[4]},{j_deg[5]}")
    error,jointSpeed = robot.GetActualJointSpeedsDegree(0)
    print(f"joint speeds deg:{jointSpeed[0]},{jointSpeed[1]},{jointSpeed[2]},{jointSpeed[3]},{jointSpeed[4]},{jointSpeed[5]}")
    error,jointAcc = robot.GetActualJointAccDegree(0)
    print(f"joint acc deg:{jointAcc[0]},{jointAcc[1]},{jointAcc[2]},{jointAcc[3]},{jointAcc[4]},{jointAcc[5]}")
    error,[tcp_speed, ori_speed] = robot.GetTargetTCPCompositeSpeed(0)
    print(f"GetTargetTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}")
    error,[tcp_speed, ori_speed] = robot.GetActualTCPCompositeSpeed(0)
    print(f"GetActualTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}")
    error,targetSpeed = robot.GetTargetTCPSpeed(0)
    print(f"GetTargetTCPSpeed {targetSpeed[0]},{targetSpeed[1]},{targetSpeed[2]},{targetSpeed[3]},{targetSpeed[4]},{targetSpeed[5]}")
    error,actualSpeed = robot.GetActualTCPSpeed(0)
    print(f"GetActualTCPSpeed {actualSpeed[0]},{actualSpeed[1]},{actualSpeed[2]},{actualSpeed[3]},{actualSpeed[4]},{actualSpeed[5]}")
    error,tcp = robot.GetActualTCPPose(0)
    print(f"tcp pose:{tcp[0]},{tcp[1]},{tcp[2]},{tcp[3]},{tcp[4]},{tcp[5]}")
    error,flange = robot.GetActualToolFlangePose(0)
    print(f"flange pose:{flange[0]},{flange[1]},{flange[2]},{flange[3]},{flange[4]},{flange[5]}")
    error,id = robot.GetActualTCPNum(0)
    print(f"tcp num:{id}")
    error,id = robot.GetActualWObjNum(0)
    print(f"wobj num:{id}")
    error,jtorque = robot.GetJointTorques(0)
    print(f"torques:{jtorque[0]},{jtorque[1]},{jtorque[2]},{jtorque[3]},{jtorque[4]},{jtorque[5]}")
    error,t_ms = robot.GetSystemClock()
    print(f"system clock:{t_ms}")
    error,config = robot.GetRobotCurJointsConfig()
    print(f"joint config:{config}")
    error,motionDone = robot.GetRobotMotionDone()
    print(f"GetRobotMotionDone:{motionDone}")
    error,len = robot.GetMotionQueueLength()
    print(f"GetMotionQueueLength:{len}")
    error,emergState = robot.GetRobotEmergencyStopState()
    print(f"GetRobotEmergencyStopState:{emergState}")
    error,comstate = robot.GetSDKComState()
    print(f"GetSDKComState:{comstate}")
    error,[si0_state, si1_state] = robot.GetSafetyStopState()
    print(f"GetSafetyStopState:{si0_state} {si1_state}")
    error,temp = robot.GetJointDriverTemperature()
    print(f"Temperature:{temp[0]},{temp[1]},{temp[2]},{temp[3]},{temp[4]},{temp[5]}")
    error,torque = robot.GetJointDriverTorque()
    print(f"torque:{torque[0]},{torque[1]},{torque[2]},{torque[3]},{torque[4]},{torque[5]}")
    error,pkg = robot.GetRobotRealTimeState()
    robot.CloseRPC()

Solución de cinemática inversa
++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetInverseKin(type,desc_pos,config=-1)``"
    "Descripción", "Cinemática inversa，pose cartesiana para resolver la posición articular "
    "Parámetros obligatorios", "- ``type``:0-pose absoluta(sistema de coordenadas base)，1-pose relativa(sistema de coordenadas base)，2-pose relativa(sistema de coordenadas de herramienta)
    - ``desc_pose``:[x,y,z,rx,ry,rz],pose de herramienta，unidad[mm][°]"
    "Parámetros predeterminados", "- ``config``:configuración articular，[-1]-resolver con referencia a la posición articular actual，[0~7]-resolver según la configuración articular predeterminado-1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``：solución de cinemática inversa，pose cartesiana para resolver la posición articular"

Solución de cinemática inversa-posición de referencia especificada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetInverseKinRef(type,desc_pos,joint_pos_ref)``"
    "Descripción", "Cinemática inversa，pose de herramienta para resolver la posición articular，resolver con referencia a la posición articular especificada"
    "Parámetros obligatorios", "- ``type``:0-pose absoluta(sistema de coordenadas base)，1-pose relativa(sistema de coordenadas base)，2-pose relativa(sistema de coordenadas de herramienta)
    - ``desc_pos``：[x,y,z,rx,ry,rz]pose de herramienta，unidad[mm][°]
    - ``joint_pos_ref``：[j1,j2,j3,j4,j5,j6]，posición articular de referencia，unidad[°]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``：solución de cinemática inversa，pose de herramienta para resolver la posición articular"

Solución de cinemática inversa, espacio cartesiano que incluye la posición del eje extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetInverseKinExaxis(type, desc_pos, exaxis, tool, workPiece, config = -1)``"
    "Descripción", "Solución de cinemática inversa, espacio cartesiano que incluye la posición del eje extendido"
    "Parámetros obligatorios", "- ``type``: 0-pose absoluta(sistema de coordenadas base)，1-pose incremental(sistema de coordenadas base)，2-pose incremental(sistema de coordenadas de herramienta)
    - ``desc_pos``: pose cartesiana
    - ``exaxis``: posición del eje extendido
    - ``tool``: número de herramienta
    - ``workPiece``: número de pieza
    - ``config -1``: solución automática，0-7 corresponden a ocho grupos de soluciones"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``joint_pos``：posición articular"

Ejemplo de código de solución de cinemática inversa que incluye la posición del eje extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    desc = [99.957, -0.002, 29.994, -176.569, -6.757, -167.462]
    exaxis = [100.0, 0.0, 0.0, 0.0]
    jointPos = [0.0] * 6
    offsetPos = [0.0] * 6
    rtn,pkg = robot.GetRobotRealTimeState()
    toolnum = pkg.tool
    workPcsNum = pkg.user
    rtn, jointPos = robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum)
    print(f"GetInverseKinExaxis joint is {jointPos[0]},{jointPos[1]},{jointPos[2]},{jointPos[3]},{jointPos[4]},{jointPos[5]}")
    robot.ExtAxisMove(exaxis, 100, -1)
    robot.MoveJ(joint_pos=jointPos, desc_pos=desc, tool=toolnum, user=workPcsNum, vel=100.0, acc=100.0, ovl=100.0, exaxis_pos=exaxis, blendT=-1, offset_flag=0, offset_pos=offsetPos)
    robot.CloseRPC()
    return 0

Solución de cinemática inversa-si tiene solución
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetInverseKinHasSolution(type,desc_pos,joint_pos_ref)``"
    "Descripción", "Cinemática inversa，pose de herramienta para resolver la posición articular si tiene solución"
    "Parámetros obligatorios", "- ``type``:0-pose absoluta(sistema de coordenadas base)，1-pose relativa(sistema de coordenadas base)，2-pose relativa(sistema de coordenadas de herramienta)
    - ``desc_pos``：[x,y,z,rx,ry,rz]pose de herramienta，unidad[mm][°]
    - ``joint_pos_ref``：[j1,j2,j3,j4,j5,j6]，posición articular de referencia，unidad[°]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``result``:“True”-tiene solución，“False”-sin solución"

Obtener las 8 soluciones inversas del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TCFToAllJoint(self, tcp_pose, tool, workpiece, exPos)``"
    "Descripción", "Obtener las 8 soluciones inversas"
    "Parámetros obligatorios", "
    - ``tcp_pose``: pose cartesiana，6 elementos[x,y,z,rx,ry,rz]
    - ``tool``: sistema de coordenadas de herramienta
    - ``workpiece``: sistema de coordenadas de pieza
    - ``exPos``: posición del eje extendido，4 elementos
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``jPos``：salida de 8 grupos de ángulos articulares，lista bidimensional，cada grupo con 6 valores articulares，48 valores en total"

Ejemplo de código para obtener las 8 soluciones inversas del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        # Establecer conexión con el controlador del robot
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        # Obtener la pose TCP actual
        ret, curTcp = robot.GetActualTCPPose(1)
        if ret != 0:
            print(f"GetActualTCPPose failed, ret:{ret}")
            robot.CloseRPC()
            return

        print(f"Current TCP pose: x={curTcp[0]:.3f}, y={curTcp[1]:.3f}, z={curTcp[2]:.3f}, "
            f"a={curTcp[3]:.3f}, b={curTcp[4]:.3f}, c={curTcp[5]:.3f}")

        # Posición del eje extendido, todos ceros aquí
        exPos = [0.0, 0.0, 0.0, 0.0]

        # Llamar a TCFToAllJoint para obtener 8 soluciones inversas, tool=0, workpiece=0
        rtn, allJoints = robot.TCFToAllJoint(curTcp, 0, 0, exPos)
        if rtn != 0:
            print(f"TCFToAllJoint failed, rtn:{rtn}")
            robot.CloseRPC()
            return

        # Verificar cada solución con cinemática directa
        for i in range(8):
            joint = allJoints[i]

            print(f"JOINT{i + 1}: j1={joint[0]:.3f}, j2={joint[1]:.3f}, j3={joint[2]:.3f}, "
                f"j4={joint[3]:.3f}, j5={joint[4]:.3f}, j6={joint[5]:.3f}")

            # Cinemática directa para obtener la pose cartesiana de la i-ésima solución
            rtn, pos = robot.GetForwardKin(joint)
            if rtn != 0:
                # Omitir esta solución si la cinemática directa falla
                continue

            print(f"POS{i + 1}: x={pos[0]:.3f}, y={pos[1]:.3f}, z={pos[2]:.3f}, "
                f"a={pos[3]:.3f}, b={pos[4]:.3f}, c={pos[5]:.3f}")

        # Cerrar conexión
        robot.CloseRPC()

    if __name__ == "__main__":
        main()
        
Solución de cinemática directa
+++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetForwardKin(joint_pos)``"
    "Descripción", "Cinemática directa，posición articular para resolver la pose de herramienta"
    "Parámetros obligatorios", "- ``joint_pos``:[j1,j2,j3,j4,j5,j6]:posición articular，unidad[°]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``desc_pos=[x,y,z,rx,ry,rz]``：solución de cinemática directa，posición articular para resolver la pose de herramienta"

Ejemplo de código de cálculo de cinemática directa e inversa del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    error, inverseRtn = robot.GetInverseKin(0, desc_pos=desc_pos1, config=-1)
    print(f"dcs1 GetInverseKin rtn is {inverseRtn[0]}, {inverseRtn[1]}, {inverseRtn[2]}, "
          f"{inverseRtn[3]}, {inverseRtn[4]}, {inverseRtn[5]}")
    error, inverseRtn = robot.GetInverseKinRef(0, desc_pos=desc_pos1, joint_pos_ref=j1)
    print(f"dcs1 GetInverseKinRef rtn is {inverseRtn[0]}, {inverseRtn[1]}, {inverseRtn[2]}, "
          f"{inverseRtn[3]}, {inverseRtn[4]}, {inverseRtn[5]}")
    error, hasResult = robot.GetInverseKinHasSolution(0, desc_pos=desc_pos1, joint_pos_ref=j1)
    print(f"dcs1 GetInverseKinRef result {hasResult}")
    error, forwordResult = robot.GetForwardKin(j1)
    print(f"jpos1 forwordResult rtn is {forwordResult[0]}, {forwordResult[1]}, {forwordResult[2]}, "
          f"{forwordResult[3]}, {forwordResult[4]}, {forwordResult[5]}")
    robot.CloseRPC()

Consultar los datos de los puntos de enseñanza del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotTeachingPoint(name)``"
    "Descripción", "Consultar los datos de los puntos de enseñanza del robot"
    "Parámetros obligatorios", "``name``：nombre del punto"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``[x,y,z,rx,ry,rz,j1,j2,j3,j4,j5,j6,tool,wobj,speed,acc,e1,e2,e3,e4]``：datos del punto"

Obtener los parámetros de compensación DH
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDHCompensation()``"
    "Descripción", "Obtener los parámetros de compensación DH"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``dhCompensation=[cmpstD1,cmpstA2,cmpstA3,cmpstD4,cmpstD5,cmpstD6]``：valores de compensación de los parámetros DH del robot(mm)"

Obtener el código SN de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotSN()``"
    "Descripción", "Obtener el código SN de la caja de control"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``SNCode``：código SN de la caja de control"

Ejemplo de código de consulta de los datos de los puntos de enseñanza del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    name = "P1"
    rtn, data = robot.GetRobotTeachingPoint(name)
    print(f"{rtn} name is: {name}")
    for i in range(20):
        print(f"data is: {data[i]}")
    rtn,que_len = robot.GetMotionQueueLength()
    print(f"GetMotionQueueLength rtn is: {rtn}, queue length is: {que_len}")
    retval,dh = robot.GetDHCompensation()
    print(f"retval is: {retval}")
    print(f"dh is: {dh[0]} {dh[1]} {dh[2]} {dh[3]} {dh[4]} {dh[5]}")
    error,sn = robot.GetRobotSN()
    print(f"robot SN is {sn[0]}")
    robot.CloseRPC()

Obtener el sistema de coordenadas de herramienta según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolCoordWithID(id)``"
    "Descripción", "Obtener el sistema de coordenadas de herramienta según el número"
    "Parámetros obligatorios", "- ``id``：número del sistema de coordenadas de herramienta"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "
    - Código de error éxito-0  fallo- errcode
    - ``coord``：valor del sistema de coordenadas
    - ``type``：tipo de herramienta (opcional) 0-herramienta；1-sensor
    - ``install``：posición de instalación (opcional) 0-extremo del robot；1-externo del robot
    - ``toolID``：ID de la herramienta
    - ``loadNo``：número de carga
    "

Obtener el sistema de coordenadas de pieza según el número
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWObjCoordWithID(id)``"
    "Descripción", "Obtener el sistema de coordenadas de pieza según el número"
    "Parámetros obligatorios", "- ``id``：número del sistema de coordenadas de pieza"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "
    - Código de error éxito-0  fallo- errcode
    - ``coord``：valor del sistema de coordenadas
    - ``refFrame``：sistema de coordenadas de referencia
    "

Obtener el sistema de coordenadas de herramienta externa según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetExToolCoordWithID(id)``"
    "Descripción", "Obtener el sistema de coordenadas de herramienta externa según el número"
    "Parámetros obligatorios", "- ``id``：número del sistema de coordenadas de herramienta externa"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "
    - Código de error éxito-0  fallo- errcode
    - ``coord``：valor del sistema de coordenadas
    - ``tcoord``：pose del sistema de coordenadas de pieza instalado en el extremo del robot (6 valores: [x, y, z, rx, ry, rz])
    "

Obtener el sistema de coordenadas del eje extendido según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetExAxisCoordWithID(id)``"
    "Descripción", "Obtener el sistema de coordenadas del eje extendido según el número"
    "Parámetros obligatorios", "- ``id``：número del sistema de coordenadas del eje extendido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "
    - Código de error éxito-0  fallo- errcode
    - ``coord``：valor del sistema de coordenadas
    - ``axisCoordNum``：número del eje extendido (opcional) bit0-bit3 corresponden al eje extendido 1-eje extendido 4；si el valor es 3, corresponde a los ejes extendidos aplicados [1,2]
    - ``calibFlag``：indicador de calibración (opcional) 0-no calibrado；1-calibrado
    "

Obtener la masa y el centro de gravedad de la carga según el número
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTargetPayloadWithID(id)``"
    "Descripción", "Obtener la masa y el centro de gravedad de la carga según el número"
    "Parámetros obligatorios", "- ``id``：número del sistema de coordenadas del eje extendido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``weight``：masa de la carga
    - ``cog``：centro de gravedad de la carga"

Obtener el sistema de coordenadas de herramienta actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetCurToolCoord()``"
    "Descripción", "Obtener el sistema de coordenadas de herramienta actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``coord``：valor del sistema de coordenadas"

Obtener el sistema de coordenadas de pieza actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetCurWObjCoord()``"
    "Descripción", "Obtener el sistema de coordenadas de pieza actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``coord``：valor del sistema de coordenadas"

Obtener el sistema de coordenadas de herramienta externa actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetCurExToolCoord()``"
    "Descripción", "Obtener el sistema de coordenadas de herramienta externa actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``coord``：valor del sistema de coordenadas"

Obtener el sistema de coordenadas del eje extendido actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetCurExAxisCoord()``"
    "Descripción", "Obtener el sistema de coordenadas del eje extendido actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``coord``：valor del sistema de coordenadas"

Ejemplo de código de sistemas de coordenadas y carga del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        time.sleep(2)

        id = 1
        rtn, toolCoord, type_val, install, toolID, loadNo = robot.GetToolCoordWithID(id)
        print(f"GetToolCoordWithID {id}, {toolCoord[0]:.6f} {toolCoord[1]:.6f} {toolCoord[2]:.6f} {toolCoord[3]:.6f} {toolCoord[4]:.6f} {toolCoord[5]:.6f},  type = {type_val}, install = {install}, toolID = {toolID}, loadNo = {loadNo}")
        rtn, wobjCoord, refFrame = robot.GetWObjCoordWithID(id)
        print(f"GetWObjCoordWithID {id}, {wobjCoord[0]:.6f} {wobjCoord[1]:.6f} {wobjCoord[2]:.6f} {wobjCoord[3]:.6f} {wobjCoord[4]:.6f} {wobjCoord[5]:.6f}, refFrame = {refFrame}")
        rtn, extoolCoord, exworkpieceCoord = robot.GetExToolCoordWithID(21)
        print(f"GetExToolCoordWithID {id}, {extoolCoord[0]:.6f} {extoolCoord[1]:.6f} {extoolCoord[2]:.6f} {extoolCoord[3]:.6f} {extoolCoord[4]:.6f} {extoolCoord[5]:.6f}, {exworkpieceCoord[0]:.6f} {exworkpieceCoord[1]:.6f} {exworkpieceCoord[2]:.6f} {exworkpieceCoord[3]:.6f} {exworkpieceCoord[4]:.6f} {exworkpieceCoord[5]:.6f}")
        rtn, exAxisCoord, axisCoordNum, calibFlag = robot.GetExAxisCoordWithID(id)
        print(f"GetExAxisCoordWithID {id}, {exAxisCoord[0]:.6f} {exAxisCoord[1]:.6f} {exAxisCoord[2]:.6f} {exAxisCoord[3]:.6f} {exAxisCoord[4]:.6f} {exAxisCoord[5]:.6f}, axisCoordNum = {axisCoordNum}, calibFlag = {calibFlag}")
        rtn, weight, cog = robot.GetTargetPayloadWithID(id)
        print(f"GetTargetPayloadWithID {id}, {weight:.6f} {cog[0]:.6f} {cog[1]:.6f} {cog[2]:.6f}")
        rtn, toolCoord = robot.GetCurToolCoord()
        print(f"GetCurToolCoord {toolCoord[0]:.6f} {toolCoord[1]:.6f} {toolCoord[2]:.6f} {toolCoord[3]:.6f} {toolCoord[4]:.6f} {toolCoord[5]:.6f}")
        rtn, wobjCoord = robot.GetCurWObjCoord()
        print(f"GetCurWObjCoord {wobjCoord[0]:.6f} {wobjCoord[1]:.6f} {wobjCoord[2]:.6f} {wobjCoord[3]:.6f} {wobjCoord[4]:.6f} {wobjCoord[5]:.6f}")
        rtn, extoolCoord = robot.GetCurExToolCoord()
        print(f"GetCurExToolCoord {extoolCoord[0]:.6f} {extoolCoord[1]:.6f} {extoolCoord[2]:.6f} {extoolCoord[3]:.6f} {extoolCoord[4]:.6f} {extoolCoord[5]:.6f}")

        rtn, exAxisCoord = robot.GetCurExAxisCoord()
        print(f"GetCurExAxisCoord {exAxisCoord[0]:.6f} {exAxisCoord[1]:.6f} {exAxisCoord[2]:.6f} {exAxisCoord[3]:.6f} {exAxisCoord[4]:.6f} {exAxisCoord[5]:.6f}")
        rtn, weightT = robot.GetTargetPayload(0)
        rtn, cogT = robot.GetTargetPayloadCog(0)
        print(f"GetTargetPayload {weightT:.6f} {cogT[0]:.6f} {cogT[1]:.6f} {cogT[2]:.6f}")
        coordSet = [0.0, 1.0, 2.0, 3.0, 4.0, 5.0]

        rtn = robot.SetToolCoord(1, coordSet, 0, 0, 1, 0)
        print(f"SetToolCoord rtn is {rtn}")

        rtn = robot.SetWObjCoord(1, coordSet, 0)
        print(f"SetWObjCoord rtn is {rtn}")

        rtn = robot.SetLoadWeight(1, 1.3)
        print(f"SetLoadWeight rtn is {rtn}")

        rtn = robot.SetLoadCoord(10.0, 20.0, 30.0,1)
        print(f"SetLoadCoord rtn is {rtn}")

        etcp = [0.0, 0.0, 100.0, 0.0, 0.0, 0.0]
        etool = [0.0, 0.0, 50.0, 0.0, 0.0, 0.0]
        rtn = robot.SetExToolCoord(21, etcp, etool)
        print(f"SetExToolCoord rtn is {rtn}")

        rtn = robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1)
        print(f"ExtAxisActiveECoordSys rtn is {rtn}")

        robot.CloseRPC()

    if __name__ == "__main__":
        main()