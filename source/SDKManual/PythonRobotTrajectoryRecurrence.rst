Reproducción de trayectorias del robot
=======================================

.. toctree:: 
    :maxdepth: 5

Establecer parámetros de registro de trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTPDParam(name, period_ms, type=1,di_choose=0, do_choose=0)``"
    "Descripción", "Establecer parámetros de registro de trayectoria"
    "Parámetros obligatorios", "- ``name``：nombre de la trayectoria；
    - ``period_ms``：período de muestreo，valor fijo，2ms o 4ms o 8ms;"
    "Parámetros predeterminados", "- ``type``：tipo de dato，1-posición articular；
    - ``di_choose``：selección DI,bit0~bit7 corresponden a DI0~DI7 de la caja de control，bit8~bit9 corresponden a DI0~DI1 del extremo，0-no seleccionar，1-seleccionar predeterminado0;
    - ``do_choose``：selección DO,bit0~bit7 corresponden a DO0~DO7 de la caja de control，bit8~bit9 corresponden a DO0~DO1 del extremo，0-no seleccionar，1-seleccionar predeterminado0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Iniciar registro de trayectoria
++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTPDStart(name, period_ms, type=1,di_choose=0, do_choose=0)``"
    "Descripción", "Iniciar registro de trayectoria"
    "Parámetros obligatorios", "- ``name``：nombre de la trayectoria；
    - ``period_ms``：período de muestreo，valor fijo，2ms o 4ms o 8ms；"
    "Parámetros predeterminados", "- ``type``：tipo de dato，1-posición articular predeterminado1;
    - ``di_choose``：selección DI,bit0~bit7 corresponden a DI0~DI7 de la caja de control，bit8~bit9 corresponden a DI0~DI1 del extremo，0-no seleccionar，1-seleccionar predeterminado0;
    - ``do_choose``：selección DO,bit0~bit7 corresponden a DO0~DO7 de la caja de control，bit8~bit9 corresponden a DO0~DO1 del extremo，0-no seleccionar，1-seleccionar predeterminado0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Detener registro de trayectoria
++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWebTPDStop()``"
    "Descripción", "Detener registro de trayectoria"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Eliminar registro de trayectoria
+++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTPDDelete(name)``"
    "Descripción", "Eliminar registro de trayectoria"
    "Parámetros obligatorios", "- ``name``:nombre de la trayectoria"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código
+++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    type = 1
    name = "tpd2025"
    period_ms = 4
    di_choose = 0
    do_choose = 0
    robot.SetTPDParam(name, period_ms)
    robot.Mode(1)
    time.sleep(1)
    robot.DragTeachSwitch(1)
    robot.SetTPDStart(name, period_ms)
    print("SetTPDStart")
    time.sleep(10)
    robot.SetWebTPDStop()
    robot.DragTeachSwitch(0)
    robot.CloseRPC()

Precarga de trayectoria
+++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadTPD(name)``"
    "Descripción", "Precarga de trayectoria"
    "Parámetros obligatorios", "- ``name``:nombre de la trayectoria"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Reproducción de trayectoria
++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveTPD(name,blend,ovl)``"
    "Descripción", "Reproducción de trayectoria"
    "Parámetros obligatorios", "- ``name``:nombre de la trayectoria
    - ``blend``：si suavizar，0-no suavizar，1-suavizar
    - ``ovl``：factor de escala de velocidad，rango[0~100]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener pose inicial de la trayectoria
+++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTPDStartPose(name)``"
    "Descripción", "Obtener pose inicial de la trayectoria"
    "Parámetros obligatorios", "- ``name``:nombre de la trayectoria"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``desc_pose=[x,y,z,rx,ry,rz]``：pose inicial de la trayectoria"

Ejemplo de código de registro de trayectoria TPD del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    type = 1
    name = "tpd2025"
    period_ms = 4
    di_choose = 0
    do_choose = 0
    ovl = 100.0
    blend = 0
    rtn = robot.LoadTPD(name)
    print(f"LoadTPD rtn is: {rtn}")
    error,start_pose = robot.GetTPDStartPose(name)
    print(f"start pose, xyz is: {start_pose[0]},{start_pose[1]},{start_pose[2]}. "
          f"rpy is: {start_pose[3]},{start_pose[4]},{start_pose[5]}")
    robot.MoveCart(start_pose, 0, 0, 100, 100)
    time.sleep(1)
    rtn = robot.MoveTPD(name, blend, ovl)
    print(f"MoveTPD rtn is: {rtn}")
    time.sleep(5)
    robot.SetTPDDelete(name)
    robot.CloseRPC()

Preprocesamiento de trayectoria
++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadTrajectoryJ(name,ovl,opt=1)``"
    "Descripción", "Preprocesamiento de trayectoria"
    "Parámetros obligatorios", "
    - ``name``:nombre de la trayectoria como trajHelix_aima_1.txt,también compatible con nombres de archivo de ruta completa，como /fruser/traj/trajHelix_aima_1.txt;
    - ``ovl``：porcentaje de escala de velocidad，rango[0~100];"
    "Parámetros predeterminados", "- ``opt``：1-punto de control，predeterminado1"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Reproducción de trayectoria
++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveTrajectoryJ()``"
    "Descripción", "Reproducción de trayectoria"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener pose inicial de la trayectoria
++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTrajectoryStartPose(name)``"
    "Descripción", "Obtener pose inicial de la trayectoria"
    "Parámetros obligatorios", "``name``:nombre de la trayectoria"
    "Parámetros predeterminados", "Ninguno"       
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``desc_pose=[x,y,z,rx,ry,rz]``：pose inicial de la trayectoria"

Obtener número de punto de trayectoria
++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTrajectoryPointNum()``"
    "Descripción", "Obtener número de punto de trayectoria"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``pnum``：número de punto de trayectoria"

Establecer la velocidad durante la ejecución de la trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJSpeed(ovl,mode)``"
    "Descripción", "Establecer la velocidad durante la ejecución de la trayectoria"
    "Parámetros obligatorios", "
    - ``ovl``:porcentaje de escala de velocidad，rango[0~100]
    - ``mode``:0-modo de reducción de velocidad；1-cambio directo"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código para establecer la velocidad durante la ejecución de la trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Establecer conexión con el controlador del robot
    robot = Robot.RPC('192.168.58.2')


    def TestSetTrajectoryJSpeed(self):
        # Subir archivo de trayectoria
        rtn = robot.TrajectoryJUpLoad("C://Users/lenovo/Desktop/trajHelix_aima_1.txt")
        print(f"Upload TrajectoryJ A {rtn}")

        traj_file_name = "trajHelix_aima_1.txt"
        # Cargar archivo de trayectoria，parámetros：nombre de archivo，porcentaje de velocidad，si es cíclico (1:cíclico)
        rtn = robot.LoadTrajectoryJ(name=traj_file_name, ovl=100, opt=1)
        print(f"LoadTrajectoryJ {traj_file_name}, rtn is: {rtn}")

        # Obtener la pose del punto inicial de la trayectoria
        rtn, traj_start_pose = robot.GetTrajectoryStartPose(name=traj_file_name)
        print(f"GetTrajectoryStartPose is: {rtn}")
        print(
            f"desc_pos:{traj_start_pose[0]},{traj_start_pose[1]},{traj_start_pose[2]},{traj_start_pose[3]},{traj_start_pose[4]},{traj_start_pose[5]}")

        time.sleep(1)

        # Establecer la velocidad base y moverse al punto inicial de la trayectoria
        robot.SetSpeed(50)
        robot.MoveCart(desc_pos=traj_start_pose, tool=0, user=0, vel=100, acc=100, ovl=100, blendT=-1, config=-1)

        # Obtener el número de puntos de la trayectoria
        rtn, traj_num = robot.GetTrajectoryPointNum()
        print(f"GetTrajectoryStartPose rtn is: {rtn}, traj num is: {traj_num}")

        # Iniciar la ejecución del movimiento de trayectoria
        rtn = robot.MoveTrajectoryJ()
        print(f"MoveTrajectoryJ rtn is: {rtn}")

        time.sleep(1)

        # Obtener el estado en tiempo real del robot
        trajspeedMode = 0
        while True:
            rtn, pkg = robot.GetRobotRealTimeState()
            if pkg.motion_done != 0:
                break

            # Establecer la velocidad de la trayectoria al 10%
            rtn = robot.SetTrajectoryJSpeed(ovl=10.0, mode=trajspeedMode)
            print(f"SetTrajectoryJSpeed is: {rtn}")

            time.sleep(1)

            # Establecer la velocidad de la trayectoria al 80%
            rtn = robot.SetTrajectoryJSpeed(ovl=80.0, mode=trajspeedMode)
            print(f"SetTrajectoryJSpeed is: {rtn}")

            time.sleep(1)

        # Cerrar conexión
        robot.CloseRPC()
        time.sleep(1)


    # Llamar a la función de prueba
    TestSetTrajectoryJSpeed(robot)

Establecer la fuerza y el par durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJForceTorque(ft)``"
    "Descripción", "Establecer la fuerza y el par durante la ejecución de la trayectoria"
    "Parámetros obligatorios", "``ft=[fx,fy,fz,tx,ty,tz]``:unidad N y Nm"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la fuerza en la dirección x durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJForceFx(fx)``"
    "Descripción", "Establecer la fuerza en la dirección x durante la ejecución de la trayectoria"
    "Parámetros obligatorios", "``ft``:fuerza en la dirección x，unidad N"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la fuerza en la dirección y durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJForceFx(fy)``"
    "Descripción", "Establecer la fuerza en la dirección y durante la ejecución de la trayectoria"
    "Parámetros obligatorios", "``fy``:fuerza en la dirección y，unidad N"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la fuerza en la dirección z durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJForceFx(fz)``"
    "Descripción", "Establecer la fuerza en la dirección z durante la ejecución de la trayectoria"
    "Parámetros obligatorios", "``fz``:fuerza en la dirección z，unidad N"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el par alrededor del eje x durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJTorqueTx(tx)``"
    "Descripción", "Establecer el par alrededor del eje x durante la ejecución de la trayectoria"
    "Parámetros obligatorios", "``tx``:par alrededor del eje x，unidad Nm"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el par alrededor del eje y durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJTorqueTx(ty)``"
    "Descripción", "Establecer el par alrededor del eje y durante la ejecución de la trayectoria"
    "Parámetros obligatorios", "``ty``:par alrededor del eje y，unidad Nm"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el par alrededor del eje z durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJTorqueTx(tz)``"
    "Descripción", "Establecer el par alrededor del eje z durante la ejecución de la trayectoria"
    "Parámetros obligatorios", "- ``tz``:par alrededor del eje z，unidad Nm"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Subir archivo de trayectoria J
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TrajectoryJUpLoad(filePath)``"
    "Descripción", "Subir archivo de trayectoria J"
    "Parámetros obligatorios", "- ``filePath``:nombre de ruta completo del archivo de trayectoria a subir，C://test/testJ.txt"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Eliminar archivo de trayectoria J
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TrajectoryJDelete(filePath)``"
    "Descripción", "Eliminar archivo de trayectoria J"
    "Parámetros obligatorios", "- ``filePath``:nombre de ruta completo del archivo de trayectoria a eliminar，C://test/testJ.txt"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de reproducción de archivo de trayectoria J del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt")
    print(f"Upload TrajectoryJ A {rtn}")
    traj_file_name = "traj.txt"
    rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1)
    print(f"LoadTrajectoryJ {traj_file_name}, rtn is: {rtn}")
    rtn,traj_start_pose = robot.GetTrajectoryStartPose(traj_file_name)
    print(f"GetTrajectoryStartPose is: {rtn}")
    print(f"desc_pos:{traj_start_pose[0]},{traj_start_pose[1]},{traj_start_pose[2]},"
          f"{traj_start_pose[3]},{traj_start_pose[4]},{traj_start_pose[5]}")
    time.sleep(1)
    robot.SetSpeed(50)
    robot.MoveCart(traj_start_pose, 0, 0, 50, 100, 100)
    rtn,traj_num = robot.GetTrajectoryPointNum()
    print(f"GetTrajectoryStartPose rtn is: {rtn}, traj num is: {traj_num}")
    rtn = robot.SetTrajectoryJSpeed(50.0)
    print(f"SetTrajectoryJSpeed is: {rtn}")
    traj_force = [0.0,0.0,0.0,0.0,0.0,0.0]
    traj_force[0] = 10  # fx = 10
    rtn = robot.SetTrajectoryJForceTorque(traj_force)
    print(f"SetTrajectoryJForceTorque rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFx(10.0)
    print(f"SetTrajectoryJForceFx rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFy(0.0)
    print(f"SetTrajectoryJForceFy rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFz(0.0)
    print(f"SetTrajectoryJForceFz rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTx(10.0)
    print(f"SetTrajectoryJTorqueTx rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTy(10.0)
    print(f"SetTrajectoryJTorqueTy rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTz(10.0)
    print(f"SetTrajectoryJTorqueTz rtn is: {rtn}")
    rtn = robot.MoveTrajectoryJ()
    print(f"MoveTrajectoryJ rtn is: {rtn}")
    robot.CloseRPC()

Preprocesamiento de trayectoria (previsión de trayectoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadTrajectoryLA(name, mode, errorLim, type, precision, vamx, amax, jmax, flag)``"
    "Descripción", "Preprocesamiento de trayectoria (previsión de trayectoria)"
    "Parámetros obligatorios", "- ``name``:nombre del archivo de trayectoria
    - ``mode``：modo de muestreo，0-no muestrear；1-muestreo con intervalo de datos igual；2-muestreo con límite de error igual
    - ``errorLim``:límite de error，efectivo al usar ajuste lineal
    - ``type``:modo de suavizado，0-suavizado de Bézier
    - ``precision``:precisión de suavizado，efectivo al usar suavizado de Bézier
    - ``vamx``:velocidad máxima establecida，mm/s
    - ``amax``:aceleración máxima establecida，mm/s2
    - ``jmax``:sobreaceleración máxima establecida，mm/s3
    - ``flag``:interruptor de activación de previsión a velocidad constante 0-no activar；1-activar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Reproducción de trayectoria (previsión de trayectoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.0

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveTrajectoryLA()``"
    "Descripción", "Reproducción de trayectoria (previsión de trayectoria)"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de reproducción de trayectoria (previsión de trayectoria)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt")
    print(f"Upload TrajectoryJ A {rtn}")
    traj_file_name = "traj.txt"
    rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 50, 200, 1000, 0)
    print(f"LoadTrajectoryLA {traj_file_name}, rtn is: {rtn}")
    rtn, traj_start_pose = robot.GetTrajectoryStartPose(traj_file_name)
    print(f"GetTrajectoryStartPose is: {rtn}")
    print(f"desc_pos: {traj_start_pose[0]},{traj_start_pose[1]},{traj_start_pose[2]},{traj_start_pose[3]},{traj_start_pose[4]},{traj_start_pose[5]}")
    time.sleep(1)
    robot.SetSpeed(50)
    robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100)
    rtn = robot.MoveTrajectoryLA()
    print(f"MoveTrajectoryLA rtn is: {rtn}")
    robot.CloseRPC()

Moverse al punto inicial del registro de trayectoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveToTPDStart(name, moveType, ovl)``"
    "Descripción", "Moverse al punto inicial del registro de trayectoria TPD"
    "Parámetros obligatorios", "
    - ``name``:nombre del archivo de trayectoria
    - ``moveType``：tipo de movimiento；0-PTP; 1-LIN
    - ``ovl``:porcentaje de escala de velocidad，rango[0~100]
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código SDK para moverse al punto inicial del registro de trayectoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    from fairino import Robot
    from ctypes import sizeof
    # A connection is established with the robot controller. A successful connection returns a robot object
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    import time

    def TestTPD(self):
        type = 1
        name = "tpd2025"
        period_ms = 4
        di_choose = 0
        do_choose = 0

        robot.SetTPDParam(type=type, name=name, period_ms=period_ms, di_choose=di_choose, do_choose=do_choose)

        robot.Mode(1)
        time.sleep(1)
        robot.DragTeachSwitch(1)
        robot.SetTPDStart(type=type, name=name, period_ms=period_ms, di_choose=di_choose, do_choose=do_choose)
        time.sleep(3)
        robot.SetWebTPDStop()
        robot.DragTeachSwitch(0)

        time.sleep(1)
        ovl = 100.0
        blend = 0
        start_pose = [0.0] * 6
        rtn = robot.LoadTPD(name)
        print(f"LoadTPD rtn is: {rtn}")

        rtn, start_pose = robot.GetTPDStartPose(name)
        print(f"start pose, xyz is: {start_pose[0]},{start_pose[1]},{start_pose[2]}. rpy is: {start_pose[3]},{start_pose[4]},{start_pose[5]}")
        # robot.MoveCart(desc_pos=start_pose, tool=0, user=0, vel=100, acc=100, ovl=ovl, blendT=-1, config=-1)
        #time.sleep(1)

        rtn = robot.MoveToTPDStart(name, 0, 100)
        print(f"MoveToTPDStart rtn is: {rtn}")

        rtn = robot.MoveTPD(name, blend, ovl)
        print(f"MoveTPD rtn is: {rtn}")
        time.sleep(5)

        robot.SetTPDDelete(name)

        robot.CloseRPC()
        return 0

    TestTPD(robot)