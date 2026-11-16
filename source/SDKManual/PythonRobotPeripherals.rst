Periféricos del robot
=====================

.. toctree:: 
    :maxdepth: 5

Configurar pinza
++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetGripperConfig(company,device,softversion=0,bus=0)``"
    "Descripción", "Configurar pinza"
    "Parámetros obligatorios", "- ``company``：fabricante de la pinza，1-Robotiq，2-Huiling，3-Tianji，4-DaHuan，5-Zhixing；
    - ``device``：número de dispositivo，Robotiq(serie 0-2F-85)，Huiling(serie 0-NK,1-Z-EFG-100)，Tianji(0-TEG-110)，DaHuan(0-PGI-140)，Zhixing(0-CTPM2F20)"
    "Parámetros predeterminados", "- ``softversion``：número de versión de software，no se utiliza por ahora，valor predeterminado 0；
    - ``bus``：posición del bus del extremo donde está montado el dispositivo，no se utiliza por ahora，valor predeterminado 0；"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Obtener configuración de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperConfig()``"
    "Descripción", "Obtener configuración de la pinza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``[number,company,device,softversion]``： number，número de pinza;company，fabricante de la pinza，1-Robotiq，2-Huiling，3-Tianji，4-DaHuan，5-Zhixing ;device，número de dispositivo，Robotiq(serie 0-2F-85)，Huiling(serie 0-NK,1-Z-EFG-100)，Tianji(0-TEG-110)，DaHuan(0-PGI-140)，Zhixing(0-CTPM2F20);softvesion，número de versión de software，no se utiliza por ahora，valor predeterminado 0。"

Activar pinza
++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ActGripper(index,action)``"
    "Descripción", "Activar pinza"
    "Parámetros obligatorios", "- ``index``:número de pinza；
    - ``action``:0-restablecer，1-activar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Controlar pinza
++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveGripper(index,pos,vel,force,maxtime,block,type,rotNum,rotVel,rotTorque)``"
    "Descripción", "Controlar pinza"
    "Parámetros obligatorios", "- ``index``:número de pinza；
    - ``pos``:porcentaje de posición，rango[0~100]；
    - ``vel``:porcentaje de velocidad，rango[0~100];
    - ``force``:porcentaje de torque，rango[0~100]；
    - ``maxtime``:tiempo máximo de espera，rango[0~30000]，unidad[ms]；
    - ``block``:0-bloqueante，1-no bloqueante；
    - ``type``:tipo de pinza，0-pinza paralela；1-pinza rotativa；
    - ``rotNum``:rotNum número de revoluciones；
    - ``rotVel``:porcentaje de velocidad de rotación[0-100]；
    - ``rotTorque``:porcentaje de torque de rotación[0-100]。"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Obtener estado de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperMotionDone()``"
    "Descripción", "Obtener estado de movimiento de la pinza(a partir de la versión 401，la definición de retroalimentación del estado de movimiento de la pinza del protocolo del extremo y los dispositivos adaptados está unificada)"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``[fault,status]``：estado de movimiento de la pinza，fault:0-sin error，otros-con error；status:0-movimiento no completado，1-movimiento completado sin detección de objeto 2-movimiento completado con detección de objeto 3-movimiento completado con detección de caída del objeto"

Obtener estado de activación de la pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperActivateStatus()``"
    "Descripción", "Obtener estado de activación de la pinza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``fault``：0-sin error，1-con error
    - ``gripper_active``：bit0~bit15 corresponden a los números de pinza 0~15，bit=0 no activada，bit=1 activada"

Obtener posición de la pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperCurPosition()``"
    "Descripción", "Obtener posición de la pinza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``fault``：0-sin error，1-con error
    - ``position``：porcentaje de posición，rango0~100%"

Obtener velocidad de la pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperCurSpeed()``"
    "Descripción", "Obtener velocidad de la pinza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``fault``：0-sin error，1-con error
    - ``speed``：porcentaje de velocidad，rango0~100%"

Obtener corriente de la pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperCurCurrent()``"
    "Descripción", "Obtener corriente de la pinza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``fault``：0-sin error，1-con error
    - ``current``：porcentaje de corriente，rango0~100%"

Obtener voltaje de la pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperVoltage()``"
    "Descripción", "Obtener voltaje de la pinza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``fault``：0-sin error，1-con error
    - ``voltage``：voltaje,unidad0.1V"

Obtener temperatura de la pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperTemp()``"
    "Descripción", "Obtener temperatura de la pinza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``fault``：0-sin error，1-con error
    - ``temp``：temperatura，unidad℃"

Calcular punto de preagarre-visión
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputePrePick(desc_pos, zlength, zangle)``"
    "Descripción", "Calcular punto de preagarre-visión"
    "Parámetros obligatorios", "- ``desc_pos``：pose cartesiana del punto de agarre;
    - ``zlength``：desplazamiento del eje z;
    - ``zangle``：desplazamiento de rotación alrededor del eje z"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``pre_pos``：pose cartesiana del punto de preagarre"

Calcular punto de retirada-visión
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputePostPick(desc_pos, zlength, zangle)``"
    "Descripción", "Calcular punto de retirada-visión"
    "Parámetros obligatorios", "- ``desc_pos``：pose cartesiana del punto de agarre;
    - ``zlength``：desplazamiento del eje z;
    - ``zangle``：desplazamiento de rotación alrededor del eje z"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``post_pos``：pose cartesiana del punto de retirada"

Ejemplo de código de operación de la pinza del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    company = 4
    device = 0
    softversion = 0
    bus = 2
    index = 2
    act = 0
    max_time = 30000
    block = 0
    status = 0
    fault = 0
    active_status = 0
    current_pos = 0
    current = 0
    voltage = 0
    temp = 0
    speed = 0
    robot.SetGripperConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.GetGripperConfig()
    print(f"gripper config:{company},{device},{softversion},{bus}")
    robot.ActGripper(index, act)
    time.sleep(1)
    act = 1
    robot.ActGripper(index, act)
    time.sleep(1)
    error = robot.MoveGripper(index, 90, 50, 50, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{error}")
    time.sleep(1)
    error = robot.MoveGripper(index, 30, 50, 0, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{error}")
    error, [fault, status] = robot.GetGripperMotionDone()
    print(f"motion status:{fault},{status}")
    error, [fault, active_status] = robot.GetGripperActivateStatus()
    print(f"gripper active fault is:{fault},status is:{active_status}")
    error, [fault, current_pos] = robot.GetGripperCurPosition()
    print(f"fault is:{fault},current position is:{current_pos}")
    error, [fault, current] = robot.GetGripperCurCurrent()
    print(f"fault is:{fault},current current is:{current}")
    error, [fault, voltage] = robot.GetGripperVoltage()
    print(f"fault is:{fault},current voltage is:{voltage}")
    error, [fault, temp] = robot.GetGripperTemp()
    print(f"fault is:{fault},current temperature is:{temp}")
    error, [fault, speed] = robot.GetGripperCurSpeed()
    print(f"fault is:{fault},current speed is:{speed}")
    retval = 0
    prepick_pose = [0.0]*6
    postpick_pose = [0.0]*6
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    retval, prepick_pose = robot.ComputePrePick(p1Desc, 10, 0)
    print(f"ComputePrePick retval is:{retval}")
    print(f"xyz is:{prepick_pose[0]},{prepick_pose[1]},{prepick_pose[2]};rpy is:{prepick_pose[3]},{prepick_pose[4]},{prepick_pose[5]}")
    retval, postpick_pose = robot.ComputePostPick(p2Desc, -10, 0)
    print(f"ComputePostPick retval is:{retval}")
    print(f"xyz is:{postpick_pose[0]},{postpick_pose[1]},{postpick_pose[2]};rpy is:{postpick_pose[3]},{postpick_pose[4]},{postpick_pose[5]}")
    robot.CloseRPC()

Obtener el número de revoluciones de la pinza rotativa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperRotNum()``"
    "Descripción", "Obtener el número de revoluciones de la pinza rotativa"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``fault``：0-sin error，1-con error
    - ``num``：número de revoluciones"

Obtener el porcentaje de velocidad de rotación de la pinza rotativa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperRotSpeed()``"
    "Descripción", "Obtener el porcentaje de velocidad de rotación de la pinza rotativa"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``fault``：0-sin error，1-con error
    - ``speed``：porcentaje de velocidad de rotación"

Obtener el porcentaje de torque de rotación de la pinza rotativa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperRotTorque()``"
    "Descripción", "Obtener el porcentaje de torque de rotación de la pinza rotativa"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``fault``：0-sin error，1-con error
    - ``torque``：porcentaje de torque de rotación"

Ejemplo de código para obtener el estado de la pinza rotativa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    fault = 0
    rotNum = 0.0
    rotSpeed = 0
    rotTorque = 0
    error,fault, rotNum = robot.GetGripperRotNum()
    error,fault, rotSpeed = robot.GetGripperRotSpeed()
    error,fault, rotTorque = robot.GetGripperRotTorque()
    print(f"gripper rot num:{rotNum},gripper rotSpeed:{rotSpeed},gripper rotTorque:{rotTorque}")
    robot.CloseRPC()

Inicio y parada de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorStartEnd(status)``"
    "Descripción", "Inicio y parada de la cinta transportadora"
    "Parámetros obligatorios", "- ``status``： estado de la cinta transportadora，1-iniciar，0-detener"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Registrar punto de detección IO
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorPointIORecord()``"
    "Descripción", "Registrar punto de detección IO"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Registrar punto A
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorPointARecord()``"
    "Descripción", "Registrar punto A"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Registrar punto de referencia
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorRefPointRecord()``"
    "Descripción", "Registrar punto de referencia"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Registrar punto B
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorPointBRecord()``"
    "Descripción", "Registrar punto B"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Detección IO de pieza en cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorIODetect(max_t)``"
    "Descripción", "Detección IO de pieza en cinta transportadora"
    "Parámetros obligatorios", "- ``max_t``： tiempo máximo de detección，unidad ms"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener posición actual del objeto
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorGetTrackData(mode)``"
    "Descripción", "Obtener posición actual del objeto"
    "Parámetros obligatorios", "- ``mode``： 1-seguimiento y agarre 2-seguimiento en movimiento 3-seguimiento TPD"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Inicio del seguimiento de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorTrackStart(status)``"
    "Descripción", "Inicio del seguimiento de la cinta transportadora"
    "Parámetros obligatorios", "- ``status``： estado，1-iniciar，0-detener"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Parada del seguimiento de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorTrackEnd()``"
    "Descripción", "Parada del seguimiento de la cinta transportadora"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Configuración de parámetros de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorSetParam(param, followType, startDis, endDis)``"
    "Descripción", "Configuración de parámetros de la cinta transportadora"
    "Parámetros obligatorios", "- ``param``： = [encChannel,resolution,lead,wpAxis,vision,speedRadio] 
                    - ``encChannel``: canal del codificador 1-2
                    - ``resolution``: resolución del codificador número de pulsos por revolución del codificador
                    - ``lead``: relación de transmisión mecánica distancia recorrida por la cinta por cada revolución del codificador
                    - ``wpAxis``: número del sistema de coordenadas de la pieza para la función de seguimiento en movimiento，seguimiento y agarre、seguimiento TPD se establece en 0
                    - ``vision``: si tiene visión  0-sin 1-con,
                    - ``speedRadio``: relación de velocidad  para el seguimiento y agarre de la cinta el rango de velocidad es (1-100)  seguimiento en movimiento、seguimiento TPD se establece en 1"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Compensación del punto de agarre de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorCatchPointComp(cmp)``"
    "Descripción", "Compensación del punto de agarre de la cinta transportadora"
    "Parámetros obligatorios", "- ``cmp``： posición de compensación [x,y,z]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Movimiento lineal
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorTrackMoveL(name,tool,wobj,vel=20,acc=100,ovl=100,blendR=-1.0)``"
    "Descripción", "Movimiento lineal"
    "Parámetros obligatorios", "- ``name``：cvrCatchPoint o cvrRaisePoint
    - ``tool``: número de herramienta
    - ``wobj``:  número de pieza"
    "Parámetros predeterminados", "- ``vel``: velocidad predeterminada20
    - ``acc``: aceleración predeterminada100
    - ``ovl``: factor de escala de velocidad predeterminado100
    - ``blendR``: [-1.0]-movimiento preciso (bloqueante)，[0~1000]-radio de suavizado (no bloqueante)，unidad [mm] predeterminado-1.0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Detección de entrada de comunicación de la cinta transportadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorComDetect(timeout)``"
    "Descripción", "Detección de entrada de comunicación de la cinta transportadora"
    "Parámetros obligatorios", "- ``timeout``：tiempo de espera máximo ms"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Disparo de detección de entrada de comunicación de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorComDetectTrigger()``"
    "Descripción", "Disparo de detección de entrada de comunicación de la cinta transportadora"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de operación de la cinta transportadora del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    retval = robot.ConveyorStartEnd(1)
    print(f"ConveyorStartEnd retval is:{retval}")
    retval = robot.ConveyorPointIORecord()
    print(f"ConveyorPointIORecord retval is:{retval}")
    retval = robot.ConveyorPointARecord()
    print(f"ConveyorPointARecord retval is:{retval}")
    retval = robot.ConveyorRefPointRecord()
    print(f"ConveyorRefPointRecord retval is:{retval}")
    retval = robot.ConveyorPointBRecord()
    print(f"ConveyorPointBRecord retval is:{retval}")
    retval = robot.ConveyorStartEnd(0)
    print(f"ConveyorStartEnd retval is:{retval}")
    param = [1.0, 10000.0, 200.0, 0.0, 0.0, 20.0]
    retval = robot.ConveyorSetParam(param,0)
    print(f"ConveyorSetParam retval is:{retval}")
    cmp = [0.0, 0.0, 0.0]
    retval = robot.ConveyorCatchPointComp(cmp)
    print(f"ConveyorCatchPointComp retval is:{retval}")
    index = 1
    max_time = 30000
    block = 0
    retval = 0
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    retval = robot.MoveCart(p1Desc, 1, 0, 100.0)
    print(f"MoveCart retval is:{retval}")
    retval = robot.WaitMs(1)
    print(f"WaitMs retval is:{retval}")
    retval = robot.ConveyorIODetect(10000)
    print(f"ConveyorIODetect retval is:{retval}")
    retval = robot.ConveyorGetTrackData(1)
    print(f"ConveyorGetTrackData retval is:{retval}")
    retval = robot.ConveyorTrackStart(1)
    print(f"ConveyorTrackStart retval is:{retval}")
    retval = robot.ConveyorTrackMoveL("cvrCatchPoint", 1, 0, 100)
    print(f"TrackMoveL retval is:{retval}")
    retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{retval}")
    retval = robot.ConveyorTrackMoveL("cvrRaisePoint", 1, 0, 100)
    print(f"TrackMoveL retval is:{retval}")
    retval = robot.ConveyorTrackEnd()
    print(f"ConveyorTrackEnd retval is:{retval}")
    robot.MoveCart(p2Desc, 1, 0, 100.0, 100.0)
    retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{retval}")
    robot.CloseRPC()

Configuración de parámetros de seguimiento en el lugar de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetStationaryTrackPara(self, trackMode, trackTime, trackDis)``"
    "Descripción", "Configuración de parámetros de seguimiento en el lugar de la cinta transportadora"
    "Parámetros obligatorios", "
    - ``trackMode``: 0-tiempo；1-distancia；2-tiempo y distancia cualquiera que se cumpla
    - ``trackTime``: tiempo de seguimiento，unidad s
    - ``trackDis``: distancia de seguimiento
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Esperar a que finalice el movimiento en vacío en el lugar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitStationaryMotionDone(self)``"
    "Descripción", "Esperar a que finalice el movimiento en vacío en el lugar"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de movimiento de seguimiento en el lugar de la cinta transportadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time


    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5) 
        j1 = [-35.146, -102.684, 120.805, -100.401, -90.295, 150.105]
        d1 = [-121.814, -348.341, 209.978, -173.152, -3.585, -5.446]

        ex = [0.0, 0.0, 0.0, 0.0]
        zeroOff = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        tool = 1
        workpiece = 1

        para = [0, 10000, 200, 0, 0, 10]
    
        rtn = robot.ConveyorSetParam(para= para)
        print(f"ConveyorSetParam rtn is {rtn}")

        robot.MoveJ(joint_pos=j1, desc_pos=d1, tool=tool, user=workpiece,
                    vel=100, acc=100, ovl=100, exaxis_pos=ex,
                    blendT=-1, offset_flag=0, offset_pos=zeroOff)

        print("--- Paso 1: SetDO(6,1) ---")
        rtn = robot.SetDO(6, 1, 0, 0)
        print(f"  SetDO(6,1) rtn={rtn}")

        print("--- Paso 2: ConveyorTrackStart(2) ---")
        rtn = robot.ConveyorTrackStart(2)
        print(f"  ConveyorTrackStart(2) rtn={rtn}")

        print("--- Paso 3: ConveyorIODetect(10000) ---")
        rtn = robot.ConveyorIODetect(10000)
        print(f"  ConveyorIODetect(10000) rtn={rtn}")

        print("--- Paso 4: ConveyorGetTrackData(2) ---")
        rtn = robot.ConveyorGetTrackData(2)
        print(f"  ConveyorGetTrackData(2) rtn={rtn}")

        print("--- Paso 5: SetStationaryTrackPara(0,5,5) ---")
        rtn = robot.SetStationaryTrackPara(0, 5, 5)
        print(f"  SetStationaryTrackPara(0,5,5) rtn={rtn}")

        print("--- Paso 6: MoveStationary() ---")
        rtn = robot.MoveStationary()
        print(f"  MoveStationary() rtn={rtn}")

        rtn = robot.WaitStationaryMotionDone()
        print(f"  WaitStationaryMotionDone() rtn={rtn}")

        print("--- Paso 7: ConveyorTrackEnd() ---")
        rtn = robot.ConveyorTrackEnd()
        print(f"  ConveyorTrackEnd() rtn={rtn}")

        print("--- Paso 8: SetDO(6,0) ---")
        rtn = robot.SetDO(6, 0, 0, 0)
        print(f"  SetDO(6,0) rtn={rtn}")

        robot.CloseRPC()


    if __name__ == "__main__":
        main()    

Configuración de sensor del extremo
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AxleSensorConfig(idCompany, idDevice, idSoftware, idBus)``"
    "Descripción", "Configuración de sensor del extremo"
    "Parámetros obligatorios", "
    - ``idCompany``: fabricante，18-JUNKONG；25-HUIDE
    - ``idDevice``: tipo，0-JUNKONG/RYR6T.V1.0
    - ``idSoftware``: versión de software，0-J1.0/HuiDe1.0(aún no disponible)
    - ``idBus``: posición de montaje，1-puerto 1 del extremo；2-puerto 2 del extremo...8-puerto 8 del extremo(aún no disponible)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener configuración del sensor del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AxleSensorConfigGet()``"
    "Descripción", "Obtener configuración del sensor del extremo"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``idCompany``: fabricante，18-JUNKONG；25-HUIDE
    - ``idDevice``: tipo，0-JUNKONG/RYR6T.V1.0"
        
Activación del sensor del extremo
+++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AxleSensorActivate(actFlag)``"
    "Descripción", "Activación del sensor del extremo"
    "Parámetros obligatorios", "``actFlag``： 0-restablecer；1-activar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``coord``: valor del sistema de coordenadas[x,y,z,rx,ry,rz]"

Escritura de registro del sensor del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AxleSensorRegWrite(devAddr, regHAddr, regLAddr, regNum, data1, data2, isNoBlock)``"
    "Descripción", "Escritura de registro del sensor del extremo"
    "Parámetros obligatorios", "- ``devAddr``：número de dirección del dispositivo 0-255
    - ``regHAddr``：dirección de registro bits altos 8
    - ``regLAddr``：dirección de registro bits bajos 8
    - ``regNum``：número de registros 0-255
    - ``data1``：valor 1 a escribir en el registro
    - ``data2``：valor 2 a escribir en el registro
    - ``isNoBlock``：si es bloqueante 0-bloqueante；1-no bloqueante"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Ejemplo de código del sensor del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.AxleSensorConfig(18, 0, 0, 1)
    error, company, type = robot.AxleSensorConfigGet()
    print(f"company is:{company},type is:{type}")
    rtn = robot.AxleSensorActivate(1)
    print(f"AxleSensorActivate rtn is:{rtn}")
    time.sleep(1)
    rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0)
    print(f"AxleSensorRegWrite rtn is:{rtn}")
    robot.CloseRPC()

Obtener protocolo de periféricos del robot
++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetExDevProtocol()``"
    "Descripción", "Obtener protocolo de periféricos del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode; 
    - ``protocol``: número de protocolo de periféricos del robot 4096-tarjeta de control de eje extendido；4097-ModbusSlave；4098-ModbusMaster"

Establecer protocolo de periféricos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExDevProtocol(protocol)``"
    "Descripción", "Establecer protocolo de periféricos del robot"
    "Parámetros obligatorios", "- ``protocol``：número de protocolo de periféricos del robot 4096-tarjeta de control de eje extendido；4097-ModbusSlave；4098-ModbusMaster"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código para establecer el protocolo de periféricos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    protocol = 4096
    rtn = robot.SetExDevProtocol(protocol)
    print(f"SetExDevProtocol rtn:{rtn}")
    rtn, protocol = robot.GetExDevProtocol()
    print(f"GetExDevProtocol rtn:{rtn},protocol is:{protocol}")
    robot.CloseRPC()


Obtener parámetros de comunicación del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxleCommunicationParam()``"
    "Descripción", "Obtener parámetros de comunicación del extremo"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``baudRate``：velocidad en baudios:soporta1-9600，2-14400，3-19200，4-38400，5-56000，6-67600，7-115200，8-128000
    - ``dataBit``：bits de datos:soporta（8,9），actualmente comúnmente utilizado 8
    - ``stopBit``：bit de parada:1-1，2-0.5，3-2，4-1.5，actualmente comúnmente utilizado 1
    - ``verify``：bit de verificación:0-None，1-Odd，2-Even,actualmente comúnmente utilizado 0
    - ``timeout``：tiempo de espera:1~1000ms，este valor debe combinarse con la configuración del periférico para establecer un parámetro de tiempo razonable
    - ``timeoutTimes``：número de tiempos de espera:1~10，principalmente para reenvío por tiempo de espera，reducir excepciones ocasionales y mejorar la experiencia del usuario
    - ``period``：intervalo de tiempo de comando periódico:1~1000ms，principalmente utilizado para el intervalo de tiempo de cada envío de comandos periódicos"

Establecer parámetros de comunicación del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleCommunicationParam(baudRate, dataBit, stopBit, verify, timeout, timeoutTimes, period)``"
    "Descripción", "Establecer parámetros de comunicación del extremo"
    "Parámetros obligatorios", "- ``baudRate``：velocidad en baudios:soporta1-9600，2-14400，3-19200，4-38400，5-56000，6-67600，7-115200，8-128000
    - ``dataBit``：bits de datos:soporta（8,9），actualmente comúnmente utilizado 8
    - ``stopBit``：bit de parada:1-1，2-0.5，3-2，4-1.5，actualmente comúnmente utilizado 1
    - ``verify``：bit de verificación:0-None，1-Odd，2-Even,actualmente comúnmente utilizado 0
    - ``timeout``：tiempo de espera:1~1000ms，este valor debe combinarse con la configuración del periférico para establecer un parámetro de tiempo razonable
    - ``timeoutTimes``：número de tiempos de espera:1~10，principalmente para reenvío por tiempo de espera，reducir excepciones ocasionales y mejorar la experiencia del usuario
    - ``period``：intervalo de tiempo de comando periódico:1~1000ms，principalmente utilizado para el intervalo de tiempo de cada envío de comandos periódicos"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Establecer tipo de transferencia de archivo del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleFileType(type)``"
    "Descripción", "Establecer tipo de transferencia de archivo del extremo"
    "Parámetros obligatorios", "- ``type``：1-archivo de actualización MCU,2-archivo LUA"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Establecer habilitación de ejecución LUA del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleLuaEnable(enable)``"
    "Descripción", "Establecer habilitación de ejecución LUA del extremo"
    "Parámetros obligatorios", "- ``enable``：0-no habilitar；1-habilitar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Recuperación de errores de archivo LUA del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRecoverAxleLuaErr(enable)``"
    "Descripción", "Recuperación de errores de archivo LUA del extremo"
    "Parámetros obligatorios", "- ``status``：0-no recuperar；1-recuperar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Obtener estado de habilitación de ejecución LUA del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxleLuaEnableStatus()``"
    "Descripción", "Obtener estado de habilitación de ejecución LUA del extremo"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``enable``：0-no habilitar；1-habilitar"

Establecer tipo de habilitación de dispositivo del extremo LUA del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleLuaEnableDeviceType(self, forceSensorEnable, gripperEnable, IOEnable, dexhandEnable)``"
    "Descripción", "Establecer tipo de habilitación de dispositivo del extremo LUA del extremo"
    "Parámetros obligatorios", "
    - ``forceSensorEnable``：estado de habilitación del sensor de fuerza，0-no habilitar；1-habilitar
    - ``gripperEnable``：estado de habilitación de la pinza，0-no habilitar；1-habilitar
    - ``IOEnable``：estado de habilitación del dispositivo IO，0-no habilitar；1-habilitar
    - ``dexhandEnable``：estado de habilitación de la mano diestra，0-no habilitar；1-habilitar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Obtener tipo de habilitación de dispositivo del extremo LUA del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxleLuaEnableDeviceType()``"
    "Descripción", "Obtener tipo de habilitación de dispositivo del extremo LUA del extremo"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``forceSensorEnable``：estado de habilitación del sensor de fuerza，0-no habilitar；1-habilitar
    - ``gripperEnable``：estado de habilitación de la pinza，0-no habilitar；1-habilitar
    - ``IOEnable``：estado de habilitación del dispositivo IO，0-no habilitar；1-habilitar
    - ``dexhandEnable``：estado de habilitación de la mano diestra，0-no habilitar；1-habilitar"

Obtener dispositivo del extremo configurado actualmente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxleLuaEnableDevice()``"
    "Descripción", "Obtener dispositivo del extremo configurado actualmente"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``forceSensorEnable[8]``：estado de habilitación del sensor de fuerza，0-no habilitar；1-habilitar
    - ``gripperEnable[8]``：estado de habilitación de la pinza，0-no habilitar；1-habilitar
    - ``IOEnable[8]``：estado de habilitación del dispositivo IO，0-no habilitar；1-habilitar
    - ``dexhandEnable``：estado de habilitación de la mano diestra，0-no habilitar；1-habilitar"

Establecer habilitación de la función de control de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleLuaGripperFunc(id, func)``"
    "Descripción", "Establecer habilitación de la función de control de movimiento de la pinza"
    "Parámetros obligatorios", "
    - ``id``：número de dispositivo de la pinza
    - ``func``：0-habilitación de la pinza；1-inicialización de la pinza；2-configuración de posición；3-configuración de velocidad；4-configuración de torque；6-leer estado de la pinza；7-leer estado de inicialización；8-leer código de fallo；9-leer posición；10-leer velocidad；11-leer torque,12-configuración del número de revoluciones de la pinza rotativa； 13-configuración de la velocidad de rotación de la pinza rotativa； 14-configuración del torque de rotación de la pinza rotativa； 15-leer estado de la pinza rotativa；16-leer estado de inicialización de la pinza rotativa；17-leer número de revoluciones de la pinza rotativa；18-leer velocidad de la pinza rotativa；19-leer torque de la pinza rotativa；20-configuración de movimiento sincronizado multieje；21-comando de borrado de fallos；22-estado de funcionamiento de un solo eje；23-estado de funcionamiento de todos los ejes；"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Obtener habilitación de la función de control de movimiento de la pinza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxleLuaGripperFunc(id)``"
    "Descripción", "Obtener habilitación de la función de control de movimiento de la pinza"
    "Parámetros obligatorios", "- ``id``：número de dispositivo de la pinza"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``func``：0-habilitación de la pinza；1-inicialización de la pinza；2-configuración de posición；3-configuración de velocidad；4-configuración de torque；6-leer estado de la pinza；7-leer estado de inicialización；8-leer código de fallo；9-leer posición；10-leer velocidad；11-leer torque,12-configuración del número de revoluciones de la pinza rotativa； 13-configuración de la velocidad de rotación de la pinza rotativa； 14-configuración del torque de rotación de la pinza rotativa； 15-leer estado de la pinza rotativa；16-leer estado de inicialización de la pinza rotativa；17-leer número de revoluciones de la pinza rotativa；18-leer velocidad de la pinza rotativa；19-leer torque de la pinza rotativa；20-configuración de movimiento sincronizado multieje；21-comando de borrado de fallos；22-estado de funcionamiento de un solo eje；23-estado de funcionamiento de todos los ejes；"

Escritura de archivo de esclavo Ethercat del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SlaveFileWrite(type,slaveID,fileName)``"
    "Descripción", "Escritura de archivo de esclavo Ethercat del robot"
    "Parámetros obligatorios", "- ``type``：tipo de archivo de esclavo，1-actualizar archivo de esclavo；2-actualizar archivo de configuración de esclavo
    - ``slaveID``：número de esclavo
    - ``fileName``：nombre del archivo a subir"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Subir archivo de protocolo abierto LUA del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AxleLuaUpload(filePath)``"
    "Descripción", "Subir archivo de protocolo abierto LUA del extremo"
    "Parámetros obligatorios", "- ``filePath``：ruta local del archivo lua .../AXLE_LUA_End_DaHuan.lua"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Entrada del esclavo Ethercat del robot en modo boot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSysServoBootMode(filePath)``"
    "Descripción", "Entrada del esclavo Ethercat del robot en modo boot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de operación de archivo LUA del extremo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua")
    param = [7, 8, 1, 0, 5, 3, 1]  # Parámetros correspondientes a AxleComParam
    robot.SetAxleCommunicationParam(7, 8, 1, 0, 5, 3, 1)
    error,getParam0,getParam1,getParam2,getParam3,getParam4,getParam5,getParam6 = robot.GetAxleCommunicationParam()
    print(f"GetAxleCommunicationParam param is:{getParam0} {getParam1} {getParam2} {getParam3} {getParam4} {getParam5} {getParam6}")
    robot.SetAxleLuaEnable(1)
    error,luaEnableStatus = robot.GetAxleLuaEnableStatus()
    robot.SetAxleLuaEnableDeviceType(0, 1, 0)
    error,forceEnable, gripperEnable, ioEnable = robot.GetAxleLuaEnableDeviceType()
    print(f"GetAxleLuaEnableDeviceType param is:{forceEnable} {gripperEnable} {ioEnable}")
    func = [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1]
    robot.SetAxleLuaGripperFunc(1, func)
    error,getFunc = robot.GetAxleLuaGripperFunc(1)
    error,getforceEnable, getgripperEnable, getioEnable = robot.GetAxleLuaEnableDevice()
    print("\ngetforceEnable status:", end=" ")
    for i in range(8):
        print(f"{getforceEnable[i]},", end="")
    print("\ngetgripperEnable status:", end=" ")
    for i in range(8):
        print(f"{getgripperEnable[i]},", end="")
    print("\ngetioEnable status:", end=" ")
    for i in range(8):
        print(f"{getioEnable[i]},", end="")
    print()
    robot.ActGripper(1, 0)
    time.sleep(2)
    robot.ActGripper(1, 1)
    time.sleep(2)
    robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0)
    while True:
        error,pkg = robot.GetRobotRealTimeState()
        print(f"gripper pos is:{pkg.gripper_position}")
        time.sleep(0.1)
    robot.CloseRPC()

    
Obtener estado del botón SmartTool
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSmarttoolBtnState()``"
    "Descripción", "Obtener estado del botón SmartTool"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``state``：estado de los botones del mango SmartTool;(bit0:0-comunicación normal；1-comunicación desconectada；bit1-deshacer operación；bit2-borrar programa；bit3-tecla A；bit4-tecla B；bit5-tecla C；bit6-tecla D；bit7-tecla E；bit8-tecla IO；bit9-manual/automático；bit10-inicio)"

Ejemplo de código del botón SmartTool
+++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    while True:
        error,state = robot.GetSmarttoolBtnState()
        print(f"{state:016b}")
        time.sleep(0.1)

Establecer detección de fuerza de carga antes de habilitar el arrastre
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTorqueDetectionSwitch(flag)``"
    "Descripción", "Establecer detección de fuerza de carga antes de habilitar el arrastre"
    "Parámetros obligatorios", "- ``flag``：0-desactivar；1-activar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Función de encendido y apagado del periférico láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingLaserOnOff(OnOff, weldId)``"
    "Descripción", "Función de encendido y apagado del periférico láser"
    "Parámetros obligatorios", "- ``OnOff``：0-apagar；1-encender"
    "Parámetros predeterminados", "- ``weldId``：ID de soldadura predeterminado0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Función de inicio y fin del seguimiento láser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingTrackOnOff(OnOff, coordId)``"
    "Descripción", "Función de inicio y fin del seguimiento láser"
    "Parámetros obligatorios", "- ``OnOff``：0-apagar；1-encender
    - ``coordId``：número del sistema de coordenadas de la herramienta del periférico láser"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Búsqueda láser-dirección fija
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingSearchStart_xyz(direction, vel, distance, timeout, posSensorNum)``"
    "Descripción", "Búsqueda láser-dirección fija"
    "Parámetros obligatorios", "- ``direction``：0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
    - ``vel``：velocidad unidad%
    - ``distance``：distancia máxima de búsqueda unidadmm
    - ``timeout``：tiempo de espera de búsqueda unidadms
    - ``posSensorNum``：número del sistema de coordenadas de la herramienta calibrada por láser"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Búsqueda láser-dirección arbitraria
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingSearchStart_point(directionPoint, vel, distance, timeout, posSensorNum)``"
    "Descripción", "Búsqueda láser-dirección arbitraria"
    "Parámetros obligatorios", "- ``directionPoint``：coordenadas xyz del punto de entrada de búsqueda,[x,y,z]
    - ``vel``：velocidad unidad%
    - ``distance``：distancia máxima de búsqueda unidadmm
    - ``timeout``：tiempo de espera de búsqueda unidadms
    - ``posSensorNum``：número del sistema de coordenadas de la herramienta calibrada por láser"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Configuración IP del láser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingSensorConfig(ip, port)``"
    "Descripción", "Configuración IP del láser"
    "Parámetros obligatorios", "- ``ip``：dirección ip del periférico láser
    - ``port``：número de puerto del periférico láser"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Configuración del período de muestreo del periférico láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingSensorSamplePeriod(period)``"
    "Descripción", "Configuración del período de muestreo del periférico láser"
    "Parámetros obligatorios", "- ``period``：período de muestreo del periférico láser unidadms"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Carga del controlador del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadPosSensorDriver(type)``"
    "Descripción", "Carga del controlador del periférico láser"
    "Parámetros obligatorios", "- ``type``：tipo de protocolo del controlador del periférico láser 101-Ruiniu 102-Chuangxiang 103-Quanshi 104-Tongzhou 105-Aotai"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Descarga del controlador del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``UnLoadPosSensorDriver()``"
    "Descripción", "Descarga del controlador del periférico láser"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Registro de trayectoria de soldadura por láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserSensorRecord1(status, delayTime)``"
    "Descripción", "Registro de trayectoria de soldadura por láser"
    "Parámetros obligatorios", "- ``status``：0-detener registro 1-seguimiento en tiempo real  2-iniciar registro
    - ``delayTime``：tiempo de retardo unidadms"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Reproducción de trayectoria de soldadura por láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserSensorReplay(delayTime, speed)``"
    "Descripción", "Reproducción de trayectoria de soldadura por láser"
    "Parámetros obligatorios", "- ``delayTime``：tiempo de retardo unidadms
    - ``speed``：velocidad unidad%"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Reproducción de seguimiento láser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveLTR()``"
    "Descripción", "Reproducción de seguimiento láser"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Reproducción de trayectoria de soldadura por láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserSensorRecordandReplay(delayMode, delayTime, delayDisExAxisNum, delayDis, sensitivePara, int trackMode, int triggerMode, double runTime, speed)``"
    "Descripción", "Reproducción de trayectoria de soldadura por láser"
    "Parámetros obligatorios", "- ``delayMode``：modo 0-tiempo de retardo 1-distancia de retardo
    - ``delayTime``：tiempo de retardo unidadms
    - ``delayDisExAxisNum``：número del eje extendido
    - ``delayDis``：distancia de retardo unidadmm
    - ``sensitivePara``：coeficiente de sensibilidad de compensación
    - ``trackMode``：tipo de seguimiento en punto fijo。0-movimiento asíncrono del eje extendido；1-robot
    - ``triggerMode``：modo de disparo del seguimiento en punto fijo。0-duración del seguimiento；1-IO
    - ``runTime``：duración del seguimiento en punto fijo del robot(s)
    - ``speed``：velocidad unidad%"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Movimiento al punto de inicio del registro de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveToLaserRecordStart(moveType, ovl)``"
    "Descripción", "Movimiento al punto de inicio del registro de soldadura"
    "Parámetros obligatorios", "- ``moveType``：0-PTP 1-LIN
    - ``ovl``：velocidad unidad%"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Movimiento al punto final del registro de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveToLaserRecordEnd(moveType, ovl)``"
    "Descripción", "Movimiento al punto final del registro de soldadura"
    "Parámetros obligatorios", "- ``moveType``：0-PTP 1-LIN
    - ``ovl``：velocidad unidad%"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Movimiento al punto de búsqueda del sensor láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveToLaserSeamPos(moveFlag, ovl, dataFlag, plateType, trackOffectType, offset)``"
    "Descripción", "Movimiento al punto de búsqueda del sensor láser"
    "Parámetros obligatorios", "- ``moveFlag``：tipo de movimiento：0-PTP；1-LIN
    - ``ovl``：factor de escala de velocidad，0-100
    - ``dataFlag``：selección de datos de caché de soldadura：0-ejecutar datos de planificación；1-ejecutar datos de registro
    - ``plateType``：tipo de placa：0-placa corrugada；1-placa ondulada；2-placa de valla；3-barril de aceite；4-acero corrugado con concha
    - ``trackOffectType``：tipo de desplazamiento del sensor láser：0-sin desplazamiento；1-desplazamiento del sistema de coordenadas base；2-desplazamiento del sistema de coordenadas de la herramienta；3-desplazamiento de datos originales del sensor láser
    - ``offset``：cantidad de desplazamiento"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener información de coordenadas del punto de búsqueda del sensor láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLaserSeamPos(trackOffectType, offset)``"
    "Descripción", "Obtener información de coordenadas del punto de búsqueda del sensor láser"
    "Parámetros obligatorios", "- ``trackOffectType``：tipo de desplazamiento del sensor láser：0-sin desplazamiento；1-desplazamiento del sistema de coordenadas base；2-desplazamiento del sistema de coordenadas de la herramienta；3-desplazamiento de datos originales del sensor láser
    - ``offset``：cantidad de desplazamiento"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``jPos``：posición articular[°]
    - ``descPos``：posición cartesiana[mm]
    - ``tool``：sistema de coordenadas de la herramienta
    - ``user``：sistema de coordenadas de la pieza
    - ``exaxis``：posición del eje extendido[mm]"

Ejemplo de código de configuración y depuración de parámetros del sensor del periférico láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.LaserTrackingSensorConfig("192.168.58.20", 5020)
    robot.LaserTrackingSensorSamplePeriod(20)
    robot.LoadPosSensorDriver(101)
    robot.LaserTrackingLaserOnOff(0, 0)
    time.sleep(3)
    robot.LaserTrackingLaserOnOff(1, 0)
    robot.CloseRPC()

Ejemplo de código de escaneo de trayectoria láser y reproducción de trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua")
    robot.UnloadCtrlOpenLUA(0)
    robot.LoadCtrlOpenLUA(0)
    time.sleep(8)
    i = 0
    while i<10:
        startjointPos = [56.205, -117.951, 141.872, -118.149, -94.217, -122.176]
        startdescPose = [-97.552, -282.855, 26.675, 174.182, -1.338, -91.707]
        exaxisPos = [0.0] * 4
        offdese = [0.0] * 6
        robot.MoveL(desc_pos=startdescPose,tool= 1,user= 0,vel= 100,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserSensorRecord1(2, 10)
        endjointPos = [68.809, -87.100, 121.120, -127.233, -95.038, -109.555]
        enddescPose = [-103.555, -464.234, 13.076, 174.179, -1.344, -91.709]
        robot.MoveL(desc_pos=enddescPose,tool= 1,user= 0,vel= 50,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserSensorRecord1(0, 10)
        robot.MoveToLaserRecordStart(1, 30)
        robot.LaserSensorReplay(10, 100)
        robot.MoveLTR()
        robot.LaserSensorRecord1(0, 10)
        i = i+1
    robot.CloseRPC()

Ejemplo de código de búsqueda láser y seguimiento en tiempo real
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua")
    robot.UnloadCtrlOpenLUA(0)
    robot.LoadCtrlOpenLUA(0)
    time.sleep(8)
    time.sleep(8)
    i = 0
    while i < 10:
        startjointPos = [56.205, -117.951, 141.872, -118.149, -94.217, -122.176]
        startdescPose = [-97.552, -282.855, 26.675, 174.182, -1.338, -91.707]
        exaxisPos = [0.0] * 4
        offdese = [0.0] * 6
        directionPoint = [0.0] * 3
        robot.MoveL(desc_pos=startdescPose,tool= 1,user= 0,vel= 100,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3)
        robot.LaserTrackingSearchStop()
        robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese)
        robot.LaserTrackingTrackOnOff(1, 3)
        endjointPos = [68.809, -87.100, 121.120, -127.233, -95.038, -109.555]
        enddescPose = [-103.555, -464.234, 13.076, 174.179, -1.344, -91.709]
        robot.MoveL(desc_pos=enddescPose,tool= 1,user= 0,vel= 20,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserTrackingTrackOnOff(0, 3)
        i = i + 1
        print(i)
    robot.CloseRPC()

Ejemplo de código de seguimiento láser sincronizado entre eje extendido y robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    startexaxisPos = [0.0, 0.0, 0.0, 0.0]
    seamexaxisPos = [-10.0, 0.0, 0.0, 0.0]
    endexaxisPos = [-30.0, 0.0, 0.0, 0.0]
    offdese = [0.0] * 6
    seamjointPos = [0.0] * 6
    seamdescPose = [0.0] * 6
    i=0
    while i < 10:
        startjointPos = [58.337, -119.628, 146.037, -116.358, -92.224, -117.654]
        startdescPose = [-53.375, -255.363, 0.919, 178.054, 1.077, -94.026]
        robot.ExtAxisSyncMoveJ(joint_pos=startjointPos, tool=1,user= 0,vel= 100,acc= 100, ovl=100,exaxis_pos= startexaxisPos,blendT= -1,offset_flag= 0,offset_pos= offdese)
        ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2)
        robot.LaserTrackingSearchStop()
        tool = 0
        user = 0
        rnte, seamjointPos, seamdescPose, tool, user, startexaxisPos = robot.GetLaserSeamPos(0, offdese)
        print(f"{seamjointPos[0]},{seamjointPos[1]},{seamjointPos[2]},{seamjointPos[3]},{seamjointPos[4]},{seamjointPos[5]},{seamdescPose[0]},{seamdescPose[1]},{seamdescPose[2]},{seamdescPose[3]},{seamdescPose[4]},{seamdescPose[5]}")
        if ret == 0:
            robot.ExtAxisSyncMoveJ(joint_pos=seamjointPos, tool=1,user= 0,vel= 100,acc= 100, ovl=100,exaxis_pos= seamexaxisPos,blendT= -1,offset_flag= 0,offset_pos= offdese)
            robot.LaserTrackingTrackOnOff(1, 2)
            endjointPos = [70.580, -90.918, 126.593, -125.154, -92.162, -105.403]
            enddescPose = [-53.375, -419.020, 0.920, 178.054, 1.076, -94.026]
            robot.ExtAxisSyncMoveL(desc_pos=enddescPose, tool=1,user= 0,vel= 20,acc= 100, ovl=100,blendR= -1,exaxis_pos= endexaxisPos,offset_pos= offdese)
            robot.LaserTrackingTrackOnOff(0, 2)
        i = i+1
        print(i)
    robot.CloseRPC()

Controlar ventosa en matriz
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSuckerCtrl(slaveID, len, ctrlValue)``"
    "Descripción", "Controlar ventosa en matriz"
    "Parámetros obligatorios", "- ``slaveID``：número de esclavo
    - ``len``：longitud
    - ``ctrlValue``：valor de control 1-aspirar según el vacío máximo 2-aspirar según el vacío establecido 3-detener la aspiración"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener estado de la ventosa en matriz
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSuckerState(slaveID)``"
    "Descripción", "Obtener estado de la ventosa en matriz"
    "Parámetros obligatorios", "- ``slaveID``：número de esclavo"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``state``：estado de aspiración 0-liberar objeto 1-detección de pieza aspirada con éxito 2-no se ha aspirado ningún objeto 3-objeto desprendido
    - ``pressValue``：vacío actual unidadkpa
    - ``error``：código de error actual de la ventosa"

Esperar estado de la ventosa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitSuckerState(slaveID, state, ms)``"
    "Descripción", "Esperar estado de la ventosa"
    "Parámetros obligatorios", "- ``slaveID``：número de esclavo
    - ``state``：estado de aspiración 0-liberar objeto 1-detección de pieza aspirada con éxito 2-no se ha aspirado ningún objeto 3-objeto desprendido
    - ``ms``：tiempo máximo de espera"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de comando de control de ventosa en matriz
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("C://项目/外设SDK/CtrlDev_sucker.lua")
    time.sleep(2)
    robot.UnloadCtrlOpenLUA(1)
    robot.LoadCtrlOpenLUA(1)
    time.sleep(1)
    ctrl = bytearray(20)
    ctrl[0] = 1
    robot.SetSuckerCtrl(0, 1, ctrl)
    for i in range(100):
        rtn, state, press_value, error = robot.GetSuckerState(1)
        print(f"sucker1 state is {state}, pressValue is {press_value}, error num is {error}")
        rtn, state, press_value, error = robot.GetSuckerState(12)
        print(f"sucker12 state is {state}, pressValue is {press_value}, error num is {error}")
        time.sleep(0.1)
    ret = robot.WaitSuckerState(1, 1, 100)
    print(f"WaitSuckerState result is {ret}")
    ctrl[0] = 3
    robot.SetSuckerCtrl(1, 1, ctrl)
    robot.SetSuckerCtrl(12, 1, ctrl)
    robot.CloseRPC()

Subir archivo Lua de protocolo abierto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``OpenLuaUpload(filePath)``"
    "Descripción", "Subir archivo Lua de protocolo abierto"
    "Parámetros obligatorios", "- ``filePath``：ruta local del archivo lua de protocolo abierto"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener parámetros de la placa esclava
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetFieldBusConfig()``"
    "Descripción", "Obtener parámetros de la placa esclava"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``type``：0-Ethercat，1-CClink, 3-Ethercat, 4-EIP
    - ``version``：versión del protocolo
    - ``connState``：0-no conectado 1-conectado"

Escribir DO del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveWriteDO(DOIndex, wirteNum, status)``"
    "Descripción", "Escribir DO del esclavo"
    "Parámetros obligatorios", "- ``DOIndex``：número DO
    - ``wirteNum``：cantidad a escribir
    - ``status``：valor a escribir，máximo 8"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Escribir AO del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveWriteAO(AOIndex, wirteNum, status)``"
    "Descripción", "Escribir AO del esclavo"
    "Parámetros obligatorios", "- ``AOIndex``：número AO
    - ``wirteNum``：cantidad a escribir
    - ``status``：valor a escribir，máximo 8"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Leer DI del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveReadDI(DOIndex, readeNum)``"
    "Descripción", "Leer DI del esclavo"
    "Parámetros obligatorios", "- ``DOIndex``：número DI
    - ``readeNum``：cantidad a leer"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``status[8]``：valores leídos，máximo 8"

Leer AI del esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveReadAI(AOIndex, readeNum)``"
    "Descripción", "Leer AI del esclavo"
    "Parámetros obligatorios", "- ``AOIndex``：número AI
    - ``readeNum``：cantidad a leer"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``status[8]``：valores leídos，máximo 8"

Esperar entrada DI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveWaitDI(DIIndex, status, waitMs)``"
    "Descripción", "Esperar entrada DI extendida"
    "Parámetros obligatorios", "- ``DIIndex``：número DI
    - ``status``：0-nivel bajo；1-nivel alto
    - ``waitMs``：tiempo máximo de espera(ms)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Esperar entrada AI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveWaitAI(AIIndex, waitType, value, waitMs)``"
    "Descripción", "Esperar entrada AI extendida"
    "Parámetros obligatorios", "- ``AIIndex``：número AI
    - ``waitType``：0-mayor que；1-menor que
    - ``value``：valor AI
    - ``waitMs``：tiempo máximo de espera(ms)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de instrucciones relacionadas con la interfaz del modo esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/外设/CtrlDev_field.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(3,"CtrlDev_field.lua")
    robot.UnloadCtrlOpenLUA(3)
    robot.LoadCtrlOpenLUA(3)
    time.sleep(8)
    rtn,type, version, conn_state = robot.GetFieldBusConfig()
    print(f"type is {type}, version is {version}, connState is {conn_state}")
    # Write digital outputs
    ctrl = [1, 0, 1]  # DO0=1, DO1=0, DO2=1
    robot.FieldBusSlaveWriteDO(0, 3, ctrl)
    # Write analog output
    ctrl_ao = [0x1000]  # AO2 = 0x1000
    robot.FieldBusSlaveWriteAO(2, 1, ctrl_ao)
    for i in range(100):
        rtn,di = robot.FieldBusSlaveReadDI(0, 4)
        print(f"DI0 is {di[0]}, DI1 is {di[1]}, DI2 is {di[2]}, DI3 is {di[3]}")
        rtn, ai = robot.FieldBusSlaveReadAI(0, 3)
        print(f"AI0 is {ai[0]}, AI1 is {ai[1]}, AI2 is {ai[2]}")
        time.sleep(0.01)
    ret = robot.FieldBusSlaveWaitDI(0, 1, 100)
    print(f"FieldBusSlaveWaitDI result is {ret}")
    ret = robot.FieldBusSlaveWaitAI(0, 0, 400.00, 100)
    print(f"FieldBusSlaveWaitAI result is {ret}")
    robot.CloseRPC()

Interfaz SDK de apertura y cierre de la función de transmisión transparente del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleGenComEnable(mode)``"
    "Descripción", "Activar la función de transmisión transparente general del extremo"
    "Parámetros obligatorios", "- ``mode``：habilitación，0-desactivar，1-activar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Interfaz SDK de envío y recepción de datos no periódicos de la función de transmisión transparente del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SndRcvAxleGenComCmdData( len_snd, sndBuff, len_rcv)``"
    "Descripción", "Enviar datos no periódicos desde el extremo y esperar respuesta"
    "Parámetros obligatorios", "
    - ``len_snd``：longitud de envío;
    - ``sndBuff[]``：datos de envío;
    - ``len_rcv``：longitud de recepción seleccionada;
    - ``rcvBuff[]``：datos de respuesta;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de comunicación de datos no periódicos del cabezal de moxibustión Beiyikang basado en la función de transmisión transparente del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from time import sleep
    from fairino import Robot
    from ctypes import sizeof
    # A connection is established with the robot controller. A successful connection returns a robot object
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')

    import time


    def testAxleGenCom(self):

        led_on = [0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79]
        led_off = [0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78]
        version = [0xAB, 0xBA, 0x11, 0x00, 0x76]
        state = [0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B]
        cycleState = [0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78]
        cnt = 1

        p1Joint = [88.708, -86.178, 140.989, -141.825, -89.162, -49.879]
        p1Desc = [188.007, -377.850, 260.207, 178.715, 2.823, -131.466]
        p2Joint = [112.131, -75.554, 126.989, -139.027, -88.044, -26.477]
        p2Desc = [368.003, -377.848, 260.211, 178.715, 2.823, -131.465]

        exaxisPos = [0, 0, 0, 0]
        offdese = [0, 0, 0, 0, 0, 0]

        #开启末端透传功能
        robot.SetAxleGenComEnable(1)
        robot.SetAxleLuaEnable(1)

        while cnt <= 10000:
            #读取版本号
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(len_snd=5, sndBuff=version, len_rcv=10)
            print(ret)
            print(rcvdata)
            print(f"hard version : {rcvdata[4]},hard code:{rcvdata[5]}, soft version:{rcvdata[6]} {rcvdata[7]}, soft code:{rcvdata[8]}")
            if ret != 0:
                break
            time.sleep(1)
            # 读取艾灸头在位状态
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(6, state, 6)
            print(f"state : {rcvdata[4]} ")
            time.sleep(1)
            # 开启艾灸头激光
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(6, led_on, 6)
            print(f"led on rcv data is: {rcvdata[0]}, {rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}")
            robot.MoveJ(joint_pos=p1Joint, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=exaxisPos, blendT=-1,
                            offset_flag=0, offset_pos=offdese)
            time.sleep(4)
            # 关闭艾灸头激光
            ret, rcvdata = robot.SndRcvAxleGenComCmdData(6, led_off, 6)
            print(f"led off rcv data is: {rcvdata[0]}, {rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}")
            robot.MoveJ(joint_pos=p2Joint, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=exaxisPos, blendT=-1,offset_flag=0, offset_pos=offdese)
            time.sleep(1)
            print(f"***********************complate No. {cnt} SDK test*****************************")
            cnt = cnt + 1

        robot.CloseRPC()
        return 0

    testAxleGenCom(robot)
    
Descargar archivo Lua de protocolo abierto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``OpenLuaDownload(fileName, savePath)``"
    "Descripción", "Descargar archivo Lua de protocolo abierto"
    "Parámetros obligatorios", "
    - ``fileName``：nombre del archivo de protocolo abierto CtrlDev_XXX.lua;
    - ``savePath``: ruta de guardado del protocolo abierto;
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Eliminar archivo Lua de protocolo abierto especificado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``OpenLuaDelete(fileName)``"
    "Descripción", "Eliminar archivo Lua de protocolo abierto especificado"
    "Parámetros obligatorios", "
    - ``fileName``：nombre del archivo lua de protocolo abierto a eliminar CtrlDev_XXX.lua
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Eliminar todos los archivos Lua de protocolo abierto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AllOpenLuaDelete()``"
    "Descripción", "Eliminar todos los archivos Lua de protocolo abierto"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código SDK de operación de archivo lua de protocolo abierto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from time import sleep
    import time
    from fairino import Robot

    # Establecer conexión con el controlador del robot
    robot = Robot.RPC('192.168.58.2')


    def TestCtrlOpenLuaOperate(self):
        # Subir archivo Lua al robot
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua")
        print(f"OpenLuaUpload rtn is {rtn}")
        
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua")
        print(f"OpenLuaUpload rtn is {rtn}")
        
        # Descargar archivo Lua desde el robot
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/")
        print(f"OpenLuaDownload rtn is {rtn}")
        
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/")
        print(f"OpenLuaDownload rtn is {rtn}")
        
        # Establecer el nombre del archivo Lua de control abierto
        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua")
        print(f"SetCtrlOpenLUAName rtn is {rtn}")
        
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua")
        print(f"SetCtrlOpenLUAName rtn is {rtn}")
        
        # Obtener el nombre del archivo Lua de control abierto
        rtn, name = robot.GetCtrlOpenLUAName()
        print(f"ctrl open lua names : {name[0]}, {name[1]}, {name[2]}, {name[3]}")
        
        # Cargar el Lua de control abierto
        rtn = robot.LoadCtrlOpenLUA(1)
        print(f"LoadCtrlOpenLUA rtn is {rtn}")
        time.sleep(2)
        
        # Descargar el Lua de control abierto
        rtn = robot.UnloadCtrlOpenLUA(1)
        print(f"UnloadCtrlOpenLUA rtn is {rtn}")
        
        # Eliminar el archivo Lua especificado
        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua")
        print(f"OpenLuaDelete rtn is {rtn}")
        
        # Eliminar todos los archivos Lua
        rtn = robot.AllOpenLuaDelete()
        print(f"AllOpenLuaDelete rtn is {rtn}")
        
        # Cerrar la conexión
        robot.CloseRPC()
        time.sleep(1)


    # Llamar a la función de prueba
    TestCtrlOpenLuaOperate(robot)
        
Controlar el movimiento de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDexterousHandsMove(self, idstart, slaveNum, pos, speed, force, max_time)``"
    "Descripción", "Controlar el movimiento de la mano diestra"
    "Parámetros obligatorios", "
    - ``idstart``：número de esclavo inicial;
    - ``slaveNum``：cantidad;
    - ``pos[16]``：posición(-360~360);
    - ``speed[16]``：porcentaje de velocidad，rango[0~100];
    - ``force[16]``：porcentaje de torque，rango[0~100];
    - ``max_time``：tiempo máximo de espera，rango[0~30000]，unidadms;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
        
Controlar restablecimiento y activación de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDexterousHandsAct(self, id, act)``"
    "Descripción", "Controlar restablecimiento y activación de la mano diestra"
    "Parámetros obligatorios", "
    - ``id``：número de esclavo;
    - ``act``：0-restablecer 1-activar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
        
Borrar error de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ClearDexterousHandsError(self)``"
    "Descripción", "Borrar error de la mano diestra"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Establecer habilitación de la función de control de movimiento de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDexterousHandsFunc(self, id, func)``"
    "Descripción", "Establecer habilitación de la función de control de movimiento de la mano diestra"
    "Parámetros obligatorios", "
    - ``id``：número de esclavo de la mano diestra;
    - ``func``：matriz de funciones，32 elementos
        0-disparo de agarre、1-inicialización de la pinza、2-configuración de posición、3-configuración de velocidad、4-configuración de torque、
        6-leer estado de la pinza、7-leer estado de inicialización、8-leer código de fallo、9-leer posición、10-leer velocidad、
        11-leer torque、12-configuración del número de revoluciones、13-configuración de la velocidad de rotación、14-configuración del torque de rotación、
        15-leer estado de la pinza rotativa、16-leer estado de inicialización de la pinza rotativa、17-leer número de revoluciones de la pinza rotativa、18-leer velocidad de la pinza rotativa、
        19-leer torque de la pinza rotativa、20-configuración de movimiento sincronizado multieje、21-comando de borrado de fallos、22-estado de funcionamiento de un solo eje、
        23-estado de funcionamiento de todos los ejes"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Obtener habilitación de la función de control de movimiento de la mano diestra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDexterousHandsFunc(self, id)``"
    "Descripción", "Obtener habilitación de la función de control de movimiento de la mano diestra"
    "Parámetros obligatorios", "
    - ``id``：número de esclavo de la mano diestra;
    - ``func``：matriz de funciones，32 elementos
        0-disparo de agarre、1-inicialización de la pinza、2-configuración de posición、3-configuración de velocidad、4-configuración de torque、
        6-leer estado de la pinza、7-leer estado de inicialización、8-leer código de fallo、9-leer posición、10-leer velocidad、
        11-leer torque、12-configuración del número de revoluciones、13-configuración de la velocidad de rotación、14-configuración del torque de rotación、
        15-leer estado de la pinza rotativa、16-leer estado de inicialización de la pinza rotativa、17-leer número de revoluciones de la pinza rotativa、18-leer velocidad de la pinza rotativa、
        19-leer torque de la pinza rotativa、20-configuración de movimiento sincronizado multieje、21-comando de borrado de fallos、22-estado de funcionamiento de un solo eje、
        23-estado de funcionamiento de todos los ejes"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de configuración y movimiento de la mano diestra del extremo  
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:  
     
    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')

    def main(self):

        id = 1                 
        slaveNum = 4         
        max_time = 8000      
        speed = [0] * 16     
        force = [0] * 16     

        for i in range(16):
            force[i] = 50 if i < 4 else 0

        def set_positions(v1, v2, v3, v4):
            pos = [0.0] * 16
            pos[0] = v1
            pos[1] = v2
            pos[2] = v3
            pos[3] = v4
            return pos

        j1 = [-53.426,-85.916,109.280,-86.236,-96.663,-28.560]
        j2 = [-91.877,-85.917,109.281,-86.236,-96.663,-28.560]
        epos = [0, 0, 0, 0]
        offset_pos = [0, 0, 0, 0, 0, 0]

        ret = robot.ClearDexterousHandsError()
        print(f"ClearDexterousHandsError -> {ret}")

        setFunc = [0] * 32
        setFunc[2] = 1   
        setFunc[4] = 1   
        setFunc[9] = 1   
        setFunc[10] = 1  
        setFunc[11] = 1  
        setFunc[22] = 1  

        ret = robot.SetDexterousHandsFunc(id, setFunc)
        print(f"SetDexterousHandsFunc(habilitación+inicialización+posición/velocidad/torque habilitados) -> {ret}")

        ret, getFunc = robot.GetDexterousHandsFunc(id)
        print(f"GetDexterousHandsFunc -> {ret}")
        if ret == 0:
            print("GetDexterousHandsFunc :")
            for i in range(len(getFunc)):
                print(f"  [{i}]={getFunc[i]}", end="")
                if (i + 1) % 8 == 0:
                    print()  
                elif i < len(getFunc) - 1:
                    print(", ", end="")
            if len(getFunc) % 8 != 0:

        ret = robot.SetDexterousHandsAct(id, 1)
        print(f"SetDexterousHandsAct() -> {ret}")
        if ret != 0:
            return
            pos = set_positions(20, 20, 20, 20)
        ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time)
        print(f"ret: {ret}")
        time.sleep(5)

        for iteration in range(1, 11):
            robot.MoveJ(joint_pos=j1, tool=1, user=0, vel=100, acc=100, ovl=100,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

            pos = set_positions(10, 10, 10, 10)
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time)
            time.sleep(1)

            robot.MoveJ(joint_pos=j2, tool=1, user=0, vel=100, acc=100, ovl=100,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

            pos = set_positions(50, 50, 50, 50)
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time)
            time.sleep(1)

    main(robot)

Esperar estado de movimiento de la pinza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GripperWaitMotionDone(self, status, timeout, strategy, type)``"
    "Descripción", "Esperar estado de movimiento de la pinza"
    "Parámetros obligatorios", "
    - ``status``：0-movimiento no completado，1-movimiento completado sin detección de objeto，2-movimiento completado con detección de objeto，3-movimiento completado con detección de caída del objeto
    - ``timeout``：tiempo de espera（ms），-1 espera permanente
    - ``strategy``：0-detener con error，1-continuar ejecutando
    - ``type``：0-pinza paralela，1-pinza rotativa
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"    

Ejemplo de código de espera del estado de movimiento de la pinza    
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:  

    from fairino import Robot
    import time

    def main():
        # Establecer conexión con el controlador del robot
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        print("========== Prueba de movimiento completado de la pinza ==========")

        # Abrir la pinza
        rtn = robot.MoveGripper(2, 50, 50, 100, 30000, 0, 0, 0, 0, 0)
        print(f"MoveGripper(open) ret={rtn}")
        time.sleep(2)
        rtn, pkg = robot.GetRobotRealTimeState()
        print(f"gripper_motiondone {pkg.gripper_motiondone}")

        # Cerrar la pinza
        rtn = robot.MoveGripper(2, 90, 100, 100, 30000, 0, 0, 0, 0, 0)
        print(f"MoveGripper(close) ret={rtn}")
        time.sleep(2)
        rtn, pkg = robot.GetRobotRealTimeState()
        print(f"gripper_motiondone {pkg.gripper_motiondone}")

        # Esperar movimiento completado, sin objeto detectado, tiempo de espera 5s, detener con error
        rtn = robot.GripperWaitMotionDone(2, 5000, 0, 0)
        print(f"GripperWaitMotionDone(no object detected) ret={rtn}")

        # Bucle y consulta del estado de movimiento de la pinza
        while True:
            rtn, status = robot.GetGripperMotionDone()
            print(f"motion status:{status[0]},{status[1]}\n")

            rtn, pkg = robot.GetRobotRealTimeState()
            print(f"error code {pkg.main_code},{pkg.sub_code}")

            time.sleep(0.5)

        # Cerrar conexión (nunca alcanzado debido al bucle infinito)
        robot.CloseRPC()

    if __name__ == "__main__":
        main()

Ejemplo de código de registro y reproducción láser + movimiento asíncrono del eje extendido + oscilación en punto fijo    
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:         

    def test_laser_record_replay_exaxis_with_wave():
    print("\n========== Registro y reproducción láser + movimiento asíncrono del eje extendido + oscilación en punto fijo ==========")

    startjointPos = [105.600,-65.393,-93.638,-79.687,79.175,134.046]
    startdescPose = [42.376,533.597,362.564,-34.957,-0.564,169.063]
    endjointPos = [105.600,-65.393,-93.638,-79.687,79.175,134.046]
    enddescPose = [42.376,533.597,362.564,-34.957,-0.564,169.063]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

    # MoveJ al punto seguro(eje extendido 0,134.296,0,0)
    rtn = robot.MoveJ(joint_pos=startjointPos, desc_pos=startdescPose, tool=5, user=0,
                        vel=100, acc=100, ovl=50, exaxis_pos=[0, 134.296, 0, 0],
                        blendT=-1, offset_flag=0, offset_pos=offdese)
    print(f"MoveJ start: {rtn}")

    # Movimiento asíncrono del eje extendido a 74.335 punto de inicio
    rtn = robot.ExtAxisMove([0, 74.335, 0, 0], 50, -1)
    print(f"ExtAxisMove 74.335: {rtn}")
    time.sleep(3)

    # MoveL al punto de inicio
    rtn = robot.MoveL(joint_pos=endjointPos, desc_pos=enddescPose, tool=5, user=0,
                        vel=100, acc=100, ovl=50, blendR=-1, offset_flag=0,
                        exaxis_pos=[0, 74.335, 0, 0], search=0,
                        offset_pos=offdese)
    print(f"MoveL end: {rtn}")

    # Iniciar registro láser
    rtn = robot.LaserSensorRecord1(2, 10)
    print(f"LaserSensorRecord start: {rtn}")

    # Durante el registro, el eje extendido se mueve a 134.296
    rtn = robot.ExtAxisMove([0, 134.296, 0, 0], 50, -1)
    print(f"ExtAxisMove 134.296: {rtn}")
    time.sleep(3)

    # Detener registro láser
    rtn = robot.LaserSensorRecord1(0, 10)
    print(f"LaserSensorRecord stop: {rtn}")

    # El eje extendido vuelve a 74.335, MoveL de vuelta al punto de inicio
    rtn = robot.ExtAxisMove([0, 74.335, 0, 0], 50, -1)
    print(f"ExtAxisMove back: {rtn}")

    # MoveL al punto de inicio
    rtn = robot.MoveL(joint_pos=endjointPos, desc_pos=enddescPose, tool=5, user=0,
                        vel=100, acc=100, ovl=50, blendR=-1, offset_flag=0,
                        exaxis_pos=[0, 74.335, 0, 0], search=0,
                        offset_pos=offdese)
    print(f"MoveL back: {rtn}")

    # Movimiento PTP al punto de inicio del registro de soldadura
    rtn = robot.MoveToLaserRecordStart(0, 30)
    print(f"MoveToLaserRecordStart: {rtn}")

    # Iniciar reproducción
    rtn = robot.LaserSensorRecord1(3, 10)
    print(f"LaserSensorRecord replay: {rtn}")

    # Inicio de oscilación en punto fijo
    refPoint = [49.381,533.608,362.556,-34.961,-0.564,169.062]
    rtn = robot.OriginPointWeaveStart(0, 1, refPoint, 5)
    print(f"OriginPointWeaveStart: {rtn}")

    # Durante la oscilación, el eje extendido se mueve a 134.296
    rtn = robot.ExtAxisMove([0, 134.296, 0, 0], 50, -1)
    print(f"ExtAxisMove replay: {rtn}")

    # Fin de la oscilación
    rtn = robot.OriginPointWeaveEnd()
    print(f"OriginPointWeaveEnd: {rtn}")

    # Detener reproducción
    rtn = robot.LaserSensorRecord1(0, 10)
    print(f"LaserSensorRecord stop: {rtn}") 

Ejemplo de código de registro y reproducción láser + oscilación normal   
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:   

    def test_laser_reproduce_normal_weave():
    print("\n========== Registro y reproducción láser + oscilación normal ==========")

    startjointPos = [68.930,-70.217,-121.821,-75.522,91.216,137.289]
    startdescPose = [216.097,304.517,34.164,-3.871,0.792,132.864]
    endjointPos = [58.092,-78.843,-115.569,-73.420,91.662,126.457]
    enddescPose = [296.276,307.453,34.803,-3.868,0.783,132.864]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

    time.sleep(1)

    # MoveL a la posición inicial(eje extendido 0,174.957,0,0)
    rtn = robot.MoveL(joint_pos=startjointPos, desc_pos=startdescPose, tool=5, user=0,
                        vel=100, acc=100, ovl=100, blendR=-1, offset_flag=0,
                        exaxis_pos=[0, 174.957, 0, 0], search=0,
                        offset_pos=offdese)
    print(f"MoveL start: {rtn}")

    # Iniciar registro láser
    rtn = robot.LaserSensorRecord1(2, 10)
    print(f"LaserSensorRecord start: {rtn}")

    # MoveL a la posición final
    rtn = robot.MoveL(joint_pos=endjointPos, desc_pos=enddescPose, tool=5, user=0,
                        vel=100, acc=100, ovl=100, blendR=-1, offset_flag=0,
                        exaxis_pos=[0, 174.957, 0, 0], search=0,
                        offset_pos=offdese)
    print(f"MoveL end: {rtn}")

    # Detener registro láser
    rtn = robot.LaserSensorRecord1(0, 10)
    print(f"LaserSensorRecord stop: {rtn}")

    # MoveL de vuelta a la posición inicial
    rtn = robot.MoveL(joint_pos=startjointPos, desc_pos=startdescPose, tool=5, user=0,
                        vel=100, acc=100, ovl=100, blendR=-1, offset_flag=0,
                        exaxis_pos=[0, 174.957, 0, 0], search=0,
                        offset_pos=offdese)
    print(f"MoveL back: {rtn}")

    # Movimiento LIN al punto de inicio del registro de soldadura
    rtn = robot.MoveToLaserRecordStart(1, 30)
    print(f"MoveToLaserRecordStart: {rtn}")

    # Inicio de oscilación normal
    rtn = robot.WeaveStart(0)
    print(f"WeaveStart: {rtn}")

    # Iniciar reproducción del registro
    rtn = robot.LaserSensorRecord1(3, 10)
    print(f"LaserSensorRecord replay: {rtn}")

    # Movimiento de reproducción del seguimiento láser
    rtn = robot.MoveLTR()
    print(f"MoveLTR: {rtn}")
    time.sleep(3)

    # Detener reproducción del registro
    rtn = robot.LaserSensorRecord1(0, 10)
    print(f"LaserSensorRecord stop: {rtn}")

    # Fin de la oscilación normal
    rtn = robot.WeaveEnd(0)
    print(f"WeaveEnd: {rtn}")