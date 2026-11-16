Movimiento del robot
=======================

.. toctree:: 
    :maxdepth: 5

Jog punto a punto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``StartJOG(ref,nb,dir,max_dis,vel=20.0,acc=100.0)``"
    "Descripción", "Jog punto a punto"
    "Parámetros obligatorios", "- ``ref``：0-jog de articulaciones,2-jog en el sistema de coordenadas base,4-jog en el sistema de coordenadas de herramienta,8-jog en el sistema de coordenadas de pieza;
    - ``nb``：1-articulación 1 (eje x),2-articulación 2 (eje y),3-articulación 3 (eje z),4-articulación 4 (rx),5-articulación 5 (ry),6-articulación 6 (rz);
    - ``dir``：0-dirección negativa, 1-dirección positiva;
    - ``max_dis``：Ángulo/distancia máximo de un solo jog, unidad ° o mm;"
    "Parámetros predeterminados", "- ``vel``：Porcentaje de velocidad, [0~100], valor predeterminado 20;
    - ``acc``：Porcentaje de aceleración, [0~100], valor predeterminado 100;"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Parada con desaceleración del jog punto a punto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``StopJOG(ref)``"
    "Descripción", "Parada con desaceleración del jog punto a punto"
    "Parámetros obligatorios", "- ``ref``：1-parada del jog de articulaciones,3-parada del jog en el sistema de coordenadas base,5-parada del jog en el sistema de coordenadas de herramienta,9-parada del jog en el sistema de coordenadas de pieza"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Parada inmediata del jog punto a punto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ImmStopJOG()``"
    "Descripción", "Parada inmediata del jog punto a punto"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de control del jog punto a punto del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    for i in range(6):
        robot.StartJOG(0, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.ImmStopJOG()
        time.sleep(1)
    for i in range(6):
        robot.StartJOG(2, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.ImmStopJOG()
        time.sleep(1)
    for i in range(6):
        robot.StartJOG(4, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.StopJOG(5)
        time.sleep(1)
    for i in range(6):
        robot.StartJOG(8, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.StopJOG(9)
        time.sleep(1)
    robot.CloseRPC()

Movimiento en el espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveJ(joint_pos, tool, user, desc_pos = [0.0,0.0,0.0,0.0,0.0,0.0], vel = 20.0, acc = 0.0, ovl = 100.0, exaxis_pos = [0.0,0.0,0.0,0.0], blendT = -1.0, offset_flag = 0, offset_pos = [0.0,0.0,0.0,0.0,0.0,0.0])``"
    "Descripción", "Movimiento en el espacio de articulaciones"
    "Parámetros obligatorios", "- ``joint_pos``:Posición objetivo de las articulaciones, unidad [°];
    - ``tool``:Número de herramienta, [0~14];
    - ``user``:Número de pieza, [0~14];"
    "Parámetros predeterminados", "- ``desc_pos``:Pose cartesiana objetivo, unidad [mm][°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática directa;
    - ``vel``:Porcentaje de velocidad, [0~100], valor predeterminado 20.0;
    - ``acc``:Porcentaje de aceleración, [0~100], aún no disponible;
    - ``ovl``:Factor de escala de velocidad, [0~100], valor predeterminado 100.0;
    - ``exaxis_pos``:Posición del eje externo 1 ~ posición del eje externo 4, valor predeterminado [0.0,0.0,0.0,0.0];
    - ``blendT``:[-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad [ms], valor predeterminado -1.0;
    - ``offset_flag``:[0]-sin desplazamiento, [1]-desplazamiento en el sistema de coordenadas de pieza/base, [2]-desplazamiento en el sistema de coordenadas de herramienta, valor predeterminado 0;
    - ``offset_pos``:Cantidad de desplazamiento de la pose, unidad [mm][°], valor predeterminado [0.0,0.0,0.0,0.0,0.0,0.0];"
    "Valor de retorno", "Código de error  éxito-0  fallo- errcode"

Movimiento lineal en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveL(desc_pos, tool, user, joint_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel=20.0, acc=0.0, ovl=100.0,blendR=-1.0, blendMode = 0,exaxis_pos=[0.0, 0.0, 0.0, 0.0], search=0, offset_flag=0,offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],oacc = 100.0,config=-1,velAccParamMode=0,overSpeedStrategy=0,speedPercent=10)``"
    "Descripción", "Movimiento lineal en el espacio cartesiano"
    "Parámetros obligatorios", "- ``desc_pos``:Pose cartesiana objetivo, unidad [mm][°];
    - ``tool``:Número de herramienta, [0~14];
    - ``user``:Número de pieza, [0~14];"
    "Parámetros predeterminados", "- ``joint_pos``:Posición objetivo de las articulaciones, unidad [°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática inversa;
    - ``vel``:Porcentaje de velocidad, [0~100], valor predeterminado 20.0;
    - ``acc``:Porcentaje de aceleración, [0~100], aún no disponible, valor predeterminado 0.0;
    - ``ovl``:Factor de escala de velocidad, [0~100], valor predeterminado 100.0;
    - ``blendR``:[-1.0]-movimiento en posición (bloqueante), [0~1000]-radio de suavizado (no bloqueante), unidad [mm], valor predeterminado -1.0;
    - ``blendMode``:Modo de transición; 0-transición tangente interna; 1-transición en esquina, valor predeterminado 0;
    - ``exaxis_pos``:Posición del eje externo 1 ~ posición del eje externo 4, valor predeterminado [0.0,0.0,0.0,0.0];
    - ``search``:[0]-sin búsqueda de posición de alambre de soldadura, [1]-búsqueda de posición de alambre de soldadura;
    - ``offset_flag``:[0]-sin desplazamiento, [1]-desplazamiento en el sistema de coordenadas de pieza/base, [2]-desplazamiento en el sistema de coordenadas de herramienta, valor predeterminado 0;
    - ``offset_pos``:Cantidad de desplazamiento de la pose, unidad [mm][°], valor predeterminado [0.0,0.0,0.0,0.0,0.0,0.0];
    - ``oacc``:Factor de escala de aceleración [0-100]/aceleración física (mm/s2), valor predeterminado 100;
    - ``config``:Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones, valor predeterminado -1
    - ``velAccParamMode``:Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2), valor predeterminado 0
    - ``overSpeedStrategy``:Estrategia de tratamiento de exceso de velocidad, 0-estrategia desactivada; 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, valor predeterminado 0
    - ``speedPercent``:Porcentaje de umbral de reducción de velocidad permitido [0-100], valor predeterminado 10%
    "
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Movimiento circular en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveC(desc_pos_p, tool_p, user_p, desc_pos_t, tool_t, user_t, joint_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], joint_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],vel_p=20.0, acc_p=100.0, exaxis_pos_p=[0.0, 0.0, 0.0, 0.0], offset_flag_p=0,offset_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],vel_t=20.0, acc_t=100.0, exaxis_pos_t=[0.0, 0.0, 0.0, 0.0], offset_flag_t=0,offset_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],ovl=100.0, blendR=-1.0,oacc=100.0,config=-1,velAccParamMode=0)``"
    "Descripción", "Movimiento circular en el espacio cartesiano"
    "Parámetros obligatorios", "- ``desc_pos_p``:Pose cartesiana del punto de trayectoria, unidad [mm][°];
    - ``tool_p``:Número de herramienta del punto de trayectoria, [0~14];
    - ``user_p``:Número de pieza del punto de trayectoria, [0~14];
    - ``desc_pos_t``:Pose cartesiana del punto objetivo, unidad [mm][°];
    - ``tool_t``:Número de herramienta, [0~14];
    - ``user_t``:Número de pieza, [0~14];"
    "Parámetros predeterminados", "- ``joint_pos_p``:Posición de las articulaciones del punto de trayectoria, unidad [°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática inversa;
    - ``joint_pos_t``:Posición de las articulaciones del punto objetivo, unidad [°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática inversa;
    - ``vel_p``:Porcentaje de velocidad del punto de trayectoria, [0~100], valor predeterminado 20.0;
    - ``acc_p``:Porcentaje de aceleración del punto de trayectoria, [0~100], aún no disponible, valor predeterminado 0.0;
    - ``exaxis_pos_p``:Posición del eje externo 1 ~ posición del eje externo 4 del punto de trayectoria, valor predeterminado [0.0,0.0,0.0,0.0];
    - ``offset_flag_p``:Si el punto de trayectoria está desplazado [0]-sin desplazamiento, [1]-desplazamiento en el sistema de coordenadas de pieza/base, [2]-desplazamiento en el sistema de coordenadas de herramienta, valor predeterminado 0;
    - ``vel_t``:Porcentaje de velocidad del punto objetivo, [0~100], valor predeterminado 20.0;
    - ``acc_t``:Porcentaje de aceleración del punto objetivo, [0~100], aún no disponible, valor predeterminado 0.0;
    - ``exaxis_pos_t``:Posición del eje externo 1 ~ posición del eje externo 4 del punto objetivo, valor predeterminado [0.0,0.0,0.0,0.0];
    - ``offset_flag_t``:Si el punto objetivo está desplazado [0]-sin desplazamiento, [1]-desplazamiento en el sistema de coordenadas de pieza/base, [2]-desplazamiento en el sistema de coordenadas de herramienta, valor predeterminado 0;
    - ``offset_pos_t``:Cantidad de desplazamiento de la pose del punto objetivo, unidad [mm][°], valor predeterminado [0.0,0.0,0.0,0.0,0.0,0.0];
    - ``ovl:``:Factor de escala de velocidad, [0~100], valor predeterminado 100.0;
    - ``blendR``:[-1.0]-movimiento en posición (bloqueante), [0~1000]-radio de suavizado (no bloqueante), unidad [mm], valor predeterminado -1.0;
    - ``oacc``:Factor de escala de aceleración [0-100]/aceleración física (mm/s2), valor predeterminado 100;
    - ``config``:Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones, valor predeterminado -1;
    - ``velAccParamMode``:Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2), valor predeterminado 0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Movimiento circular completo en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``Circle(desc_pos_p, tool_p, user_p, desc_pos_t, tool_t, user_t, joint_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],joint_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],vel_p=20.0, acc_p=0.0, exaxis_pos_p=[0.0, 0.0, 0.0, 0.0], vel_t=20.0, acc_t=0.0,exaxis_pos_t=[0.0, 0.0, 0.0, 0.0],ovl=100.0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], oacc=100.0, blendR=-1,config=-1,velAccParamMode=0)``"
    "Descripción", "Movimiento circular completo en el espacio cartesiano"
    "Parámetros obligatorios", "- ``desc_pos_p``:Pose cartesiana del punto de trayectoria, unidad [mm][°];
    - ``tool_p``:Número de herramienta, [0~14];
    - ``user_p``:Número de pieza, [0~14];
    - ``desc_pos_t``:Pose cartesiana del punto objetivo, unidad [mm][°];
    - ``tool_t``:Número de herramienta, [0~14];
    - ``user_t``:Número de pieza, [0~14];"
    "Parámetros predeterminados", "- ``joint_pos_p``:Posición de las articulaciones del punto de trayectoria, unidad [°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática inversa;
    - ``joint_pos_t``:Posición de las articulaciones del punto objetivo, unidad [°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática inversa;
    - ``vel_p``:Porcentaje de velocidad, [0~100], valor predeterminado 20.0;
    - ``acc_p``:Porcentaje de aceleración del punto de trayectoria, [0~100], aún no disponible, valor predeterminado 0.0;
    - ``exaxis_pos_p``:Posición del eje externo 1 ~ posición del eje externo 4 del punto de trayectoria, valor predeterminado [0.0,0.0,0.0,0.0];
    - ``vel_t``:Porcentaje de velocidad del punto objetivo, [0~100], valor predeterminado 20.0;
    - ``acc_t``:Porcentaje de aceleración del punto objetivo, [0~100], aún no disponible, valor predeterminado 0.0;
    - ``exaxis_pos_t``:Posición del eje externo 1 ~ posición del eje externo 4 del punto objetivo, valor predeterminado [0.0,0.0,0.0,0.0]
    - ``ovl``:Factor de escala de velocidad, [0~100], valor predeterminado 100.0;
    - ``offset_flag``:Si está desplazado [0]-sin desplazamiento, [1]-desplazamiento en el sistema de coordenadas de pieza/base, [2]-desplazamiento en el sistema de coordenadas de herramienta, valor predeterminado 0;
    - ``offset_pos``:Cantidad de desplazamiento de la pose, unidad [mm][°], valor predeterminado [0.0,0.0,0.0,0.0,0.0,0.0]
    - ``oacc``:Factor de escala de aceleración [0-100]/aceleración física (mm/s2), valor predeterminado: 100;
    - ``blendR``:-1: bloqueante; 0~1000: radio de suavizado, valor predeterminado: -1;
    - ``config``:Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones, valor predeterminado -1;
    - ``velAccParamMode``:Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2), valor predeterminado 0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Movimiento punto a punto en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveCart(desc_pos, tool, user, vel = 20.0, acc = 0.0, ovl = 100.0, blendT = -1.0, config = -1)``"
    "Descripción", "Movimiento punto a punto en el espacio cartesiano"
    "Parámetros obligatorios", "- ``desc_pos``:Posición cartesiana objetivo;
    - ``tool``:Número de herramienta, [0~14];
    - ``user``:Número de pieza, [0~14];"
    "Parámetros predeterminados", "- ``vel``:Velocidad, rango [0~100], valor predeterminado 20.0;
    - ``acc``:Aceleración, rango [0~100], aún no disponible, valor predeterminado 0.0;
    - ``ovl``:Factor de escala de velocidad, [0~100], valor predeterminado 100.0;
    - ``blendT``:[-1.0]-movimiento en posición (bloqueante), [0~500]-tiempo de suavizado (no bloqueante), unidad [ms], valor predeterminado -1.0;
    - ``config``:Configuración de articulaciones, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según la configuración de articulaciones, valor predeterminado -1"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de instrucciones de movimiento básico del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    j3 = [-29.777, -84.536, 109.275, -114.075, -86.655, 74.257]
    j4 = [-31.154, -95.317, 94.276, -88.079, -89.740, 74.256]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_pos3 = [-487.434, 154.362, 308.576, 176.600, 0.268, -14.061]
    desc_pos4 = [-443.165, 147.881, 480.951, 179.511, -0.775, -15.409]
    offset_pos = [0.0] * 6
    epos = [0.0] * 4
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    oacc = 100.0
    blendT = 0.0
    blendR = 0.0
    flag = 0
    search = 0
    blendMode = 0
    velAccMode = 0
    robot.SetSpeed(20)
    rtn = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.MoveL(desc_pos=desc_pos2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, blendR=blendR, blendMode=blendMode, exaxis_pos=epos, search=search, offset_flag=flag, offset_pos=offset_pos,oacc=oacc, velAccParamMode=velAccMode)
    print(f"movel errcode:{rtn}")
    rtn = robot.MoveC(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, offset_flag_p=flag, offset_pos_p=offset_pos, desc_pos_t=desc_pos4, tool_t=tool, user_t=user, vel_t=vel,acc_t=acc, exaxis_pos_t=epos, offset_flag_t=flag, offset_pos_t=offset_pos, ovl=ovl, blendR=blendR, oacc=oacc, velAccParamMode=velAccMode)
    print(f"movec errcode:{rtn}")
    rtn = robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.Circle(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, desc_pos_t=desc_pos1, tool_t=tool, user_t=user, vel_t=vel, acc_t=acc, exaxis_pos_t=epos, ovl=ovl,offset_flag=flag, offset_pos=offset_pos, oacc=oacc, blendR=-1, velAccParamMode=velAccMode)
    print(f"circle errcode:{rtn}")
    rtn = robot.MoveCart(desc_pos=desc_pos4, tool=tool, user=user, vel=vel, acc=acc,ovl=ovl, blendT=blendT, config=-1)
    print(f"MoveCart errcode:{rtn}")
    rtn = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.MoveL(desc_pos=desc_pos2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, blendR=blendR, blendMode=blendMode, exaxis_pos=epos, search=search, offset_flag=flag, offset_pos=offset_pos, config=-1,velAccParamMode=velAccMode)
    print(f"movel errcode:{rtn}")
    rtn = robot.MoveC(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, offset_flag_p=flag, offset_pos_p=offset_pos, desc_pos_t=desc_pos4, tool_t=tool, user_t=user, vel_t=vel, acc_t=acc,exaxis_pos_t=epos, offset_flag_t=flag, offset_pos_t=offset_pos, ovl=ovl, blendR=blendR, config=-1, velAccParamMode=velAccMode)
    print(f"movec errcode:{rtn}")
    rtn = robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.Circle(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, desc_pos_t=desc_pos1, tool_t=tool, user_t=user, vel_t=vel, acc_t=acc, exaxis_pos_t=epos, ovl=ovl, offset_flag=flag,offset_pos=offset_pos, oacc=oacc, blendR=-1, velAccParamMode=velAccMode)
    print(f"circle errcode:{rtn}")
    robot.CloseRPC()
    return 0

Movimiento en hélice en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``NewSpiral(desc_pos, tool, user, param, joint_pos = [0.0,0.0,0.0,0.0,0.0,0.0], vel = 20.0, acc = 0.0, exaxis_pos = [0.0,0.0,0.0,0.0], ovl = 100.0, offset_flag = 0, offset_pos = [0.0,0.0,0.0,0.0,0.0,0.0], config = -1)``"
    "Descripción", "Movimiento en hélice en el espacio cartesiano"
    "Parámetros obligatorios", "- ``desc_pos``:Pose cartesiana objetivo, unidad [mm][°];
    - ``tool``:Número de herramienta, [0~14];
    - ``user``:Número de pieza, [0~14];
    - ``param=[circle_num, circle_angle, rad_init, rad_add, rotaxis_add, rot_direction, velAccMode]``：circle_num: número de vueltas de la hélice; circle_angle: ángulo de inclinación de la hélice; rad_init: radio inicial de la hélice; rad_add: incremento de radio; rotaxis_add: incremento de dirección del eje de rotación; rot_direction: dirección de rotación, 0-sentido horario, 1-sentido antihorario; velAccMode modo de parámetros de velocidad y aceleración: 0-velocidad angular constante, 1-velocidad lineal constante;"
    "Parámetros predeterminados", "- ``joint_pos``:Posición objetivo de las articulaciones, unidad [°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática inversa;
    - ``vel``:Porcentaje de velocidad, [0~100], valor predeterminado 20.0;
    - ``acc``:Porcentaje de aceleración, [0~100], valor predeterminado 100.0;
    - ``exaxis_pos``:Posición del eje externo 1 ~ posición del eje externo 4, valor predeterminado [0.0,0.0,0.0,0.0];
    - ``ovl``:Factor de escala de velocidad, [0~100], valor predeterminado 100.0;
    - ``offset_flag``:[0]-sin desplazamiento, [1]-desplazamiento en el sistema de coordenadas de pieza/base, [2]-desplazamiento en el sistema de coordenadas de herramienta, valor predeterminado 0;
    - ``offset_pos``:Cantidad de desplazamiento de la pose, unidad [mm][°], valor predeterminado [0.0,0.0,0.0,0.0,0.0,0.0]
    - ``config``:Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones, valor predeterminado -1"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    j = [67.957, -81.482, 87.595, -95.691, -94.899, -9.727]
    desc_pos = [-123.142, -551.735, 430.549, 178.753, -4.757, 167.754]
    offset_pos1 = [50.0, 0.0, 0.0, -30.0, 0.0, 0.0]
    offset_pos2 = [50.0, 0.0, 0.0, -30.0, 0.0, 0.0]
    epos = [0.0] * 4
    sp = [2, 30.0, 50.0, 10.0, 10.0, 0, 1]  # [circle_num, circle_angle, rad_init, rad_add, rotaxis_add, rot_direction, velAccMode]
    tool = 0
    user = 0
    vel = 30.0
    acc = 60.0
    ovl = 100.0
    blendT = -1.0
    flag = 2
    robot.SetSpeed(20)
    rtn = robot.MoveJ(joint_pos=j, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos1)
    print(f"movej errcode:{rtn}")
    rtn = robot.NewSpiral(desc_pos=desc_pos, tool=tool, user=user, vel=vel, acc=acc, exaxis_pos=epos, ovl=ovl, offset_flag=flag, offset_pos=offset_pos2, param=sp)
    print(f"newspiral errcode:{rtn}")
    robot.CloseRPC()
    return 0

Inicio del movimiento servo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoMoveStart(self, cmdType=0, filtertime=0, gain=[-1.0, -1.0, -1.0, -1.0, -1.0, -1.0])``"
    "Descripción", "Inicio del movimiento servo, se utiliza junto con las instrucciones ServoJ y ServoCart"
    "Parámetros obligatorios", "
    - ``cmdType``: Tipo de transmisión de comandos, 0=XML-RPC, 1=UDP transparente
    - ``filtertime``: Tiempo de filtrado, unidad ms, valor predeterminado 0
    - ``gain``: Arreglo de ganancia del lazo de posición, la longitud debe ser 6, correspondiendo sucesivamente a la ganancia del lazo de posición de las articulaciones J1~J6; al pasar None se usan los valores predeterminados [-1.0, -1.0, -1.0, -1.0, -1.0, -1.0]
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin del movimiento servo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoMoveEnd(cmdType=0)``"
    "Descripción", "Fin del movimiento servo, se utiliza junto con las instrucciones ServoJ y ServoCart"
    "Parámetros obligatorios", "- ``cmdType``: Tipo de transmisión de comandos, 0=XML-RPC, 1=UDP transparente"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Movimiento en modo servo del espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoJ(joint_pos, axisPos, acc = 0.0, vel = 0.0, cmdT = 0.008, filterT = 0.0, gain = 0.0, id=0, cmdType=0)``"
    "Descripción", "Movimiento en modo servo del espacio de articulaciones"
    "Parámetros obligatorios", "- ``joint_pos``:Posición objetivo de las articulaciones, unidad [°];
    - ``axisPos``:Posición del eje externo, unidad mm;"
    "Parámetros predeterminados", "- ``acc``:Aceleración, rango [0~100], aún no disponible, valor predeterminado 0.0;
    - ``vel``:Velocidad, rango [0~100], aún no disponible, valor predeterminado 0.0;
    - ``cmdT``:Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016], valor predeterminado 0.008;
    - ``filterT``:Tiempo de filtrado, unidad [s], aún no disponible, valor predeterminado 0.0;
    - ``gain``:Amplificador proporcional de la posición objetivo, aún no disponible, valor predeterminado 0.0;
    - ``id``:ID de la instrucción servoJ, valor predeterminado 0;
    - ``cmdType``:Tipo de transmisión de comandos, 0=XML-RPC, 1=UDP transparente;"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de inicio del movimiento servo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def udp_frame_callback(src_type, count, cmd_id, data_len, content):
        """Función de devolución de llamada de recepción de tramas UDP"""
        print("Callback: cmd_id={} count={} data_len={} content={}".format(cmd_id, count, data_len, content))
        return 0


    def test_servo_j_with_filtertime(robot):
        """Prueba de ServoJ con tiempo de filtrado y ganancia del servo"""
        print("\n========== Prueba de ServoJ con tiempo de filtrado ==========")

        j = [70.000000, -49.000000, -109.000000, -81.000000, 76.000000, 93.000000]
        epos = [0.0, 0.0, 0.0, 0.0]
        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        # Moverse a la posición inicial de las articulaciones
        robot.MoveJ(joint_pos=j, tool=1, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        vel = 0.0
        acc = 0.0
        cmdT = 0.008
        filterT = 0.0
        gain = 0.0
        cmdID = 0
        comType = 0
        filtertime = 0
        ServoGain = [22.0, 22.0, 22.0, 22.0, 22.0, 22.0]

        # Obtener la posición actual de las articulaciones
        rtn, j = robot.GetActualJointPosDegree(0)
        if rtn != 0:
            print(f"GetActualJointPosDegree errcode:{rtn}")

        # Iniciar el movimiento servo con tiempo de filtrado y ganancia
        rtn = robot.ServoMoveStart(comType, filtertime, ServoGain)
        print(f"ServoMoveStart rtn is {rtn}")

        # Leer el archivo de trayectoria y enviar comandos ServoJ
        file_path = "D://zUP/6RPTPpath.txt"
        try:
            with open(file_path, 'r') as fin:
                for line in fin:
                    line = line.strip()
                    if not line:
                        continue
                    # Formato de análisis de línea: ServoJ(j1,j2,j3,j4,j5,j6,...
                    if line.startswith("ServoJ("):
                        values_str = line[len("ServoJ("):]
                        parts = values_str.split(',')
                        if len(parts) >= 6:
                            p = [float(parts[i]) for i in range(6)]
                            rtn = robot.ServoJ(joint_pos=p, axisPos=epos, acc=acc, vel=vel,
                                            cmdT=cmdT, filterT=filterT, gain=gain,
                                            id=cmdID, cmdType=comType)
                            print(f"ServoJ rtn is {rtn}")
        except FileNotFoundError:
            print(f"File not found: {file_path}")

        # Finalizar el movimiento servo
        rtn = robot.ServoMoveEnd(comType)
        print(f"ServoMoveEnd rtn is {rtn}")

        time.sleep(4)


    def test_servo_cart_with_filtertime(robot):
        """Prueba de ServoCart con tiempo de filtrado y ganancia del servo"""
        print("\n========== Prueba de ServoCart con tiempo de filtrado ==========")

        desc_pos_dt = [542.1690, 34.7990, 114.4800, 169.808000, -3.600000, -133.152000]
        exaxis = [0.0, 0.0, 0.0, 0.0]
        pos_gain = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
        mode = 0
        vel = 0.0
        acc = 0.0
        cmdT = 0.008
        filterT = 0.0
        gain = 0.0
        filtertime = 80
        ServoGain = [20.0, 20.0, 20.0, 20.0, 20.0, 20.0]

        # Establecer la velocidad y moverse al punto de inicio
        robot.SetSpeed(20)
        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
        robot.MoveL(desc_pos=desc_pos_dt, tool=1, user=0, vel=100, acc=100, ovl=100,
                    blendR=-1, blendMode=0, exaxis_pos=exaxis, search=0,
                    offset_flag=0, offset_pos=offset_pos)

        # Iniciar el movimiento servo con tiempo de filtrado y ganancia
        rtn = robot.ServoMoveStart(0, filtertime, ServoGain)
        print(f"ServoMoveStart rtn is {rtn}")

        # Leer el archivo de trayectoria y enviar comandos ServoCart
        file_path = "D://zUP/6RCARpath.txt"
        try:
            with open(file_path, 'r') as fin:
                for line in fin:
                    line = line.strip()
                    if not line:
                        continue
                    # Formato de análisis de línea: ServoCart(0,x,y,z,rx,ry,rz,...
                    if line.startswith("ServoCart("):
                        values_str = line[len("ServoCart("):]
                        parts = values_str.split(',')
                        # Omitir el primer elemento (mode=0), tomar los siguientes 6 valores
                        if len(parts) >= 7:
                            desc_pos_dt = [float(parts[i]) for i in range(1, 7)]
                            rtn = robot.ServoCart(mode=mode, desc_pos=desc_pos_dt, exaxis=exaxis,
                                                pos_gain=pos_gain, acc=acc, vel=vel,
                                                cmdT=cmdT, filterT=filterT, gain=gain)
                            print(f"ServoCart rtn is {rtn}")
        except FileNotFoundError:
            print(f"File not found: {file_path}")

        # Finalizar el movimiento servo
        robot.ServoMoveEnd()


    def main():
        # Establecer comunicación con el controlador del robot
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        # Establecer la función de devolución de llamada de respuesta de comandos UDP
        robot.SetUDPCmdRpyCallback(udp_frame_callback)

        # Ejecutar la prueba deseada (descomentar una a la vez)
        # test_servo_j_with_filtertime(robot)
        test_servo_cart_with_filtertime(robot)

        # Cerrar la conexión
        robot.CloseRPC()


    if __name__ == "__main__":
        main()

Ejemplo de código de movimiento en modo servo del espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    j = [0.0] * 6
    epos = [0.0] * 4
    vel = 0.0
    acc = 0.0
    cmdT = 0.008
    filterT = 0.0
    gain = 0.0
    flag = 0
    count = 500
    dt = 0.1
    cmdID = 0
    ret, j = robot.GetActualJointPosDegree(flag)
    if ret == 0:
        cmdID += 1
        robot.ServoMoveStart()
        while count:
            robot.ServoJ(joint_pos=j,axisPos= epos,acc= acc,vel= vel, cmdT=cmdT, filterT=filterT, gain=gain, id=cmdID)
            j[4] += dt
            count -= 1
            time.sleep(cmdT)
            rtn,pkg = robot.GetRobotRealTimeState()
            print(f"Servoj Count {pkg.servoJCmdNum}; last pos is {pkg.lastServoTarget[0]},{pkg.lastServoTarget[1]},{pkg.lastServoTarget[2]},{pkg.lastServoTarget[3]},{pkg.lastServoTarget[4]},{pkg.lastServoTarget[5]}")

            if count < 50:
                robot.MotionQueueClear()
                print(f"After queue clear, Servoj Count {pkg.servoJCmdNum}; last pos is {pkg.lastServoTarget[0]},{pkg.lastServoTarget[1]},{pkg.lastServoTarget[2]},{pkg.lastServoTarget[3]},{pkg.lastServoTarget[4]},{pkg.lastServoTarget[5]}")
                break
        robot.ServoMoveEnd()
    else:
        print(f"GetActualJointPosDegree errcode:{ret}")
    robot.CloseRPC()

Inicio del control de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoJTStart(cmdType=0)``"
    "Descripción", "Inicio del control de par de las articulaciones"
    "Parámetros obligatorios", "- ``cmdType``: Tipo de transmisión de comandos, 0=XML-RPC, 1=UDP transparente"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Control de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoJT(torque, interval, checkFlag=0, jPowerLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],jVelLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], cmdType=0)``"
    "Descripción", "Control de par de las articulaciones"
    "Parámetros obligatorios", "- ``torque``:par de las articulaciones j1~j6, unidad Nm
                - ``interval``:período de instrucción, unidad s, rango [0.001~0.008]
                - ``checkFlag``:estrategia de detección 0-sin límite; 1-limitar potencia; 2-limitar velocidad; 3-limitar potencia y velocidad simultáneamente, valor predeterminado 0
                - ``jPowerLimit``:parámetro predeterminado jPowerLimit límite máximo de potencia de las articulaciones (W), valor predeterminado [0.0,0.0,0.0,0.0,0.0,0.0]
                - ``jVelLimit``:velocidad máxima de las articulaciones (°/s), valor predeterminado [0.0,0.0,0.0,0.0,0.0,0.0]
                - ``cmdType``:tipo de transmisión de comandos, 0=XML-RPC, 1=UDP transparente"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin del control de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoJTEnd(cmdType=0)``"
    "Descripción", "Fin del control de par de las articulaciones"
    "Parámetros obligatorios", "- ``cmdType``: Tipo de transmisión de comandos, 0=XML-RPC, 1=UDP transparente"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código SDK de ServoJT, ServoJTStart y ServoJTEnd basado en comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Establecer comunicación con el controlador del robot
    robot = Robot.RPC('192.168.58.2')

    def TestServoJTUDP(self):
        # Establecer la función de devolución de llamada
        def callback(src_type, count, cmd_id, data_len, content):
            print("Función de devolución de llamada: cmd_id={} count={} data_len={} content={}".format(cmd_id, count, data_len, content))
            return 0

        robot.SetUDPCmdRpyCallback(callback)
        while True:
            # Inicializar la posición de las articulaciones y la posición del eje externo
            j = [0, -90, 90, 0, 0, 0]
            epos = [0, 0, 0, 0]
            offset_pos = [0, 0, 0, 0, 0, 0]

            # Moverse a la posición inicial
            robot.MoveJ(joint_pos=j, tool=0, user=0, vel=100, acc=100, ovl=100,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
            time.sleep(3)
            # Activar la enseñanza por arrastre
            result=robot.DragTeachSwitch(1)
            print("Resultado devuelto por DragTeachSwitch: {}".format(result))
            torques = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

            # Obtener el par de las articulaciones
            ret, torques = robot.GetJointTorques(flag=1)
            if ret != 0:
                print(f"GetJointTorques errcode:{ret}")

            count = 100
            result = robot.ServoJTStart(cmdType=1)
            print("Resultado devuelto por ServoJTStart: {}".format(result))
            # Control de par positivo
            while True:
                torques[0] = 0.03
                result = robot.ServoJT(
                    torque=torques,
                    interval=0.001,
                    checkFlag=0,
                    jPowerLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
                    jVelLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
                    cmdType=1
                )
                print("Resultado devuelto: {}".format(result))
                time.sleep(1)

                ret, pkg = robot.GetRobotRealTimeState()
                if pkg.jt_cur_pos[0] > 30:
                    break

            # Control de par negativo
            while True:
                torques[0] = -0.03
                result = robot.ServoJT(
                        torque=torques,
                        interval=0.001,
                        checkFlag=0,
                        jPowerLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
                        jVelLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
                        cmdType=1
                    )
                print("Resultado devuelto: {}".format(result))
                time.sleep(1)

                ret, pkg = robot.GetRobotRealTimeState()
                if pkg.jt_cur_pos[0] < 0:
                    break

            # Finalizar el control de par y desactivar la enseñanza por arrastre
            result = robot.ServoJTEnd(cmdType=1)
            print("Resultado devuelto por ServoJTEnd: {}".format(result))
            result = robot.DragTeachSwitch(0)
            print("Resultado devuelto por DragTeachSwitch: {}".format(result))

        robot.CloseRPC()
        return 0
    TestServoJTUDP(robot)

Ejemplo de código de control de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.DragTeachSwitch(1)
    # torques = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    error,torques = robot.GetJointTorques(1)
    robot.ServoJTStart()
    count = 100
    while count > 0:
        error = robot.ServoJT(torques, 0.001)
        count -= 1
        time.sleep(0.001)
    error = robot.ServoJTEnd()
    robot.DragTeachSwitch(0)
    robot.CloseRPC()

Movimiento en modo servo del espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoCart(mode, desc_pos, exaxis, pos_gain=[1.0, 1.0, 1.0, 1.0, 1.0, 1.0], acc=0.0, vel=0.0, cmdT=0.008,filterT=0.0, gain=0.0)``"
    "Descripción", "Movimiento en modo servo del espacio cartesiano"
    "Parámetros obligatorios", "- ``mode``:[0]-movimiento absoluto (sistema de coordenadas base), [1]-movimiento incremental (sistema de coordenadas base), [2]-movimiento incremental (sistema de coordenadas de herramienta);
    - ``exaxis``:Posición del eje extendido;
    - ``desc_pos``:Posición cartesiana objetivo / incremento de posición cartesiana objetivo;"
    "Parámetros predeterminados", "- ``pos_gain``:Coeficiente proporcional del incremento de pose, solo efectivo en movimiento incremental, rango [0~1], valor predeterminado [1.0, 1.0, 1.0, 1.0, 1.0, 1.0];
    - ``acc``:Aceleración, rango [0~100], aún no disponible, valor predeterminado 0.0;
    - ``vel``:Velocidad, rango [0~100], aún no disponible, valor predeterminado 0.0;
    - ``cmdT``:Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016], valor predeterminado 0.008;
    - ``filterT``:Tiempo de filtrado, unidad [s], aún no disponible, valor predeterminado 0.0;
    - ``gain``:Amplificador proporcional de la posición objetivo, aún no disponible, valor predeterminado 0.0;"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de movimiento en modo servo del espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    desc_pos_dt = [83.00800, 50.525000, 29.246, 179.629, -7.138, -166.975]
    exaxis = [100.0, 0.0, 0.0, 0.0]
    pos_gain = [0.0] * 6
    mode = 0
    vel = 0.0
    acc = 0.0
    cmdT = 0.001
    filterT = 0.0
    gain = 0.0
    flag = 0
    count = 5000
    robot.SetSpeed(20)
    while count:
        rtn = robot.ServoCart(mode, desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain)
        print(f"ServoCart rtn is {rtn}")
        count -= 1
        desc_pos_dt[0] += 0.01
        exaxis[0] += 0.01
    robot.CloseRPC()
    return 0

Inicio del movimiento por spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SplineStart()``"
    "Descripción", "Inicio del movimiento por spline"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Movimiento por spline PTP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SplinePTP(joint_pos, tool, user, desc_pos = [0.0,0.0,0.0,0.0,0.0,0.0],  vel = 20.0,  acc = 100.0, ovl = 100.0)``"
    "Descripción", "Movimiento por spline PTP"
    "Parámetros obligatorios", "- ``joint_pos``:Posición objetivo de las articulaciones, unidad [°];
    - ``tool``:Número de herramienta, [0~14];
    - ``user``:Número de pieza, [0~14];"
    "Parámetros predeterminados", "- ``desc_pos``:Pose cartesiana objetivo, unidad [mm][°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática directa;
    - ``vel``:Velocidad, rango [0~100], valor predeterminado 20.0;
    - ``acc``:Aceleración, rango [0~100], valor predeterminado 100.0;
    - ``ovl``:Factor de escala de velocidad, [0~100], valor predeterminado 100.0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin del movimiento por spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SplineEnd()``"
    "Descripción", "Fin del movimiento por spline"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Ejemplo de código de movimiento por spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    joint_points = [
        [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256],  # j1
        [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255],  # j2
        [-61.954, -84.409, 108.153, -116.316, -91.283, 74.260],  # j3
        [-89.575, -80.276, 102.713, -116.302, -91.284, 74.267]  # j4
    ]
    cart_points = [
        [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833],  # desc_pos1
        [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869],  # desc_pos2
        [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207],  # desc_pos3
        [-104.066, 544.321, 327.023, -177.715, 3.371, -73.818]  # desc_pos4
    ]
    offset_pos = [0] * 6 
    epos = [0] * 4 
    tool = user = 0
    vel = acc = ovl = 100.0 
    blendT = -1.0  
    flag = 0 
    robot.SetSpeed(20)
    err1 = robot.MoveJ(joint_pos=joint_points[0],tool=tool, user=user,vel=vel)
    print(f"Código de error de MoveJ: {err1}")
    robot.SplineStart()
    robot.SplinePTP(joint_pos=joint_points[0],tool=tool, user=user)
    robot.SplinePTP(joint_pos=joint_points[1],tool=tool, user=user)
    robot.SplinePTP(joint_pos=joint_points[2],tool=tool, user=user)
    robot.SplinePTP(joint_pos=joint_points[3],tool=tool, user=user)
    robot.SplineEnd()
    robot.CloseRPC()

Inicio del nuevo movimiento por spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``NewSplineStart(type,averageTime=2000)``"
    "Descripción", "Inicio del nuevo movimiento por spline"
    "Parámetros obligatorios", "- ``type``:0-transición de arco, 1-los puntos dados son puntos de trayectoria"
    "Parámetros predeterminados", "- ``averageTime``:Tiempo medio global de conexión (ms), valor predeterminado 2000"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Punto de instrucción del nuevo spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``NewSplinePoint(desc_pos,tool,user,lastFlag,joint_pos=[0.0,0.0,0.0,0.0,0.0,0.0], vel = 0.0, acc = 0.0, ovl = 100.0 ,blendR = 0.0 )``"
    "Descripción", "Punto de instrucción del nuevo spline"
    "Parámetros obligatorios", "- ``desc_pos``:Pose cartesiana objetivo, unidad [mm][°];
    - ``tool``:Número de herramienta, [0~14];
    - ``user``:Número de pieza, [0~14];
    - ``lastFlag``:Si es el último punto, 0-no, 1-sí;"
    "Parámetros predeterminados", "- ``joint_pos``:Posición objetivo de las articulaciones, unidad [°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática inversa;
    - ``vel``:Velocidad, rango [0~100], aún no disponible, valor predeterminado 0.0;
    - ``acc``:Aceleración, rango [0~100], aún no disponible, valor predeterminado 0.0;
    - ``ovl``:Factor de escala de velocidad, [0~100], valor predeterminado 100.0;
    - ``blendR``: [0~1000]-radio de suavizado, unidad [mm], valor predeterminado 0.0;"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin del nuevo movimiento por spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``NewSplineEnd()``"
    "Descripción", "Fin del nuevo movimiento por spline"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código del nuevo movimiento por spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    j3 = [-61.954, -84.409, 108.153, -116.316, -91.283, 74.260]
    j4 = [-89.575, -80.276, 102.713, -116.302, -91.284, 74.267]
    j5 = [-95.228, -54.621, 73.691, -112.245, -91.280, 74.268]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_pos3 = [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207]
    desc_pos4 = [-104.066, 544.321, 327.023, -177.715, 3.371, -73.818]
    desc_pos5 = [-33.421, 732.572, 275.103, -177.907, 2.709, -79.482]
    offset_pos = [0, 0, 0, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    err1 = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel)
    print(f"movej errcode:{err1}")
    robot.NewSplineStart(1, 2000)
    robot.NewSplinePoint(desc_pos=desc_pos1, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos2, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos3, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos4, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos5, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplineEnd()
    robot.CloseRPC()

Terminación del movimiento del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``StopMotion()``"
    "Descripción", "Terminación del movimiento; para usar la terminación del movimiento la instrucción de movimiento debe estar en estado no bloqueante"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Pausa del movimiento del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``PauseMotion()``"
    "Descripción", "Pausa del movimiento; para usar la pausa del movimiento la instrucción de movimiento debe estar en estado no bloqueante"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Reanudación del movimiento del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``ResumeMotion()``"
    "Descripción", "Reanudación del movimiento; para usar la reanudación del movimiento la instrucción de movimiento debe estar en estado no bloqueante"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de pausa, reanudación y detención del movimiento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    j1 =[-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j5 =[-95.228, -54.621, 73.691, -112.245, -91.280, 74.268]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos5 = [-33.421, 732.572, 275.103, -177.907, 2.709, -79.482]
    offset_pos = [0, 0, 0, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    rtn = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel)
    rtn = robot.MoveJ(joint_pos=j5, tool=tool, user=user, vel=vel, blendT=1)
    time.sleep(1)
    robot.PauseMotion()
    time.sleep(1)
    robot.ResumeMotion()
    time.sleep(1)
    robot.StopMotion()
    time.sleep(1)
    robot.CloseRPC()

Inicio del desplazamiento global de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``PointsOffsetEnable(flag,offset_pos)``"
    "Descripción", "Inicio del desplazamiento global de puntos"
    "Parámetros obligatorios", "- ``flag``:0-desplazamiento en el sistema de coordenadas base o de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta;
    - ``offset_pos``:Cantidad de desplazamiento, unidad [mm][°]."
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin del desplazamiento global de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``PointsOffsetDisable()``"
    "Descripción", "Fin del desplazamiento global de puntos"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de desplazamiento de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    offset_pos = [0, 0, 0, 0, 0, 0]
    offset_pos1 = [0, 0, 50, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    robot.MoveJ(joint_pos=j1,tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    time.sleep(1)
    robot.PointsOffsetEnable(flag=0, offset_pos=offset_pos1)
    robot.MoveJ(joint_pos=j1,tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    robot.PointsOffsetDisable()
    robot.CloseRPC()

Inicio de la AO sincronizada con el movimiento de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``MoveAOStart(AONum,maxTCPSpeed=1000,maxAOPercent=100,zeroZoneCmp=20)``"
    "Descripción", "Inicio de la AO sincronizada con el movimiento de la caja de control"
    "Parámetros obligatorios", "- ``AONum``:Número de AO de la caja de control"
    "Parámetros predeterminados", "
    - ``maxTCPSpeed``:Valor máximo de velocidad TCP [1-5000mm/s], valor predeterminado 1000;
    - ``maxAOPercent``:Porcentaje de AO correspondiente al valor máximo de velocidad TCP, valor predeterminado 100%;
    - ``zeroZoneCmp``:Valor de compensación de zona muerta, porcentaje de AO, entero, valor predeterminado 20%, rango [0-100]."
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin de la AO sincronizada con el movimiento de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``MoveAOStop()``"
    "Descripción", "Fin de la AO sincronizada con el movimiento de la caja de control"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Inicio de la AO sincronizada con el movimiento del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``MoveToolAOStart(AONum,maxTCPSpeed=1000,maxAOPercent=100,zeroZoneCmp =20)``"
    "Descripción", "Inicio de la AO sincronizada con el movimiento del extremo"
    "Parámetros obligatorios", "- ``AONum``:Número de AO del extremo"
    "Parámetros predeterminados", "
    - ``maxTCPSpeed``:Valor máximo de velocidad TCP [1-5000mm/s], valor predeterminado 1000;
    - ``maxAOPercent``:Porcentaje de AO correspondiente al valor máximo de velocidad TCP, valor predeterminado 100%;
    - ``zeroZoneCmp``:Valor de compensación de zona muerta, porcentaje de AO, entero, valor predeterminado 20%, rango [0-100]."
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin de la AO sincronizada con el movimiento del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``MoveToolAOStop()``"
    "Descripción", "Fin de la AO sincronizada con el movimiento del extremo"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
      
Ejemplo de código de AO sincronizada con el movimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    offset_pos = [0, 0, 0, 0, 0, 0]
    offset_pos1 = [0, 0, 50, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 20.0
    acc = 20.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    robot.MoveAOStart(0, 100, 100, 20)
    robot.MoveJ(joint_pos=j1,tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    robot.MoveAOStop()
    time.sleep(1)
    robot.MoveToolAOStart(0, 100, 100, 20)
    robot.MoveJ(joint_pos=j1,tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    robot.MoveToolAOStop()
    robot.CloseRPC()

Inicio del filtrado FIR del movimiento Ptp
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``PtpFIRPlanningStart(maxAcc, maxJek)``"
    "Descripción", "Inicio del filtrado FIR del movimiento Ptp"
    "Parámetros obligatorios", "- ``maxAcc``:Valor extremo máximo de aceleración (deg/s2)
    - ``maxJek``:Valor extremo unificado de jerk (sobreaceleración) de las articulaciones (deg/s3)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Cierre del filtrado FIR del movimiento Ptp
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``PtpFIRPlanningEnd()``"
    "Descripción", "Cierre del filtrado FIR del movimiento Ptp"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Inicio del filtrado FIR del movimiento LIN y ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``LinArcFIRPlanningStart(maxAccLin,maxAccDeg,maxJerkLin,maxJerkDeg)``"
    "Descripción", "Inicio del filtrado FIR del movimiento LIN y ARC"
    "Parámetros obligatorios", "- ``maxAccLin``:Valor extremo de aceleración lineal (mm/s2)
    - ``maxAccDeg``:Valor extremo de aceleración angular (deg/s2)
    - ``maxJerkLin``:Valor extremo de jerk lineal (mm/s3)
    - ``maxJerkDeg``:Valor extremo de jerk angular (deg/s3)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Cierre del filtrado FIR del movimiento LIN y ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``LinArcFIRPlanningEnd()``"
    "Descripción", "Cierre del filtrado FIR del movimiento LIN y ARC"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"   

Ejemplo de código de filtrado FIR
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    midjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    endjointPos = [-29.777, -84.536, 109.275, -114.075, -86.655, 74.257]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    middescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    enddescPose = [-487.434, 154.362, 308.576, 176.600, 0.268, -14.061]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.PtpFIRPlanningStart(1000.0, 1000.0)
    print(f"PtpFIRPlanningStart rtn is {rtn}")
    error = robot.MoveJ(joint_pos=startjointPos,tool= 0,user= 0,desc_pos=startdescPose,vel= 100,acc=100,ovl=100, blendT=-1.0, offset_flag=0)
    print(f"MoveJ rtn is {rtn}")
    error = robot.MoveJ(joint_pos=endjointPos,tool= 0,user= 0,desc_pos=enddescPose,vel= 100,acc=100,ovl=100, blendT=-1.0, offset_flag=0)
    print(f"MoveJ rtn is {rtn}")
    robot.PtpFIRPlanningEnd()
    print(f"PtpFIRPlanningEnd rtn is {rtn}")
    rtn = robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000)
    print(f"LinArcFIRPlanningStart rtn is {rtn}")
    error = robot.MoveL(desc_pos=startdescPose,tool= 0,user= 0, joint_pos=startjointPos,vel= 100,overSpeedStrategy=1,speedPercent=1)
    print(f"MoveL rtn is {rtn}")
    error = robot.MoveC(desc_pos_p=middescPose,tool_p= 0,user_p= 0, joint_pos_p=midjointPos,vel_p= 100,desc_pos_t=enddescPose,tool_t= 0,user_t= 0,joint_pos_t=endjointPos,vel_t= 100)
    print(f"MoveC rtn is {rtn}")
    robot.LinArcFIRPlanningEnd()
    print(f"LinArcFIRPlanningEnd rtn is {rtn}")
    robot.CloseRPC()

Activación del suavizado de aceleración
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AccSmoothStart(saveFlag_flag)``"
    "Descripción", "Activación del suavizado de aceleración"
    "Parámetros obligatorios", "- ``saveFlag_flag``：Si se guarda tras un corte de energía"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Desactivación del suavizado de aceleración
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AccSmoothEnd(saveFlag_flag)``"
    "Descripción", "Desactivación del suavizado de aceleración"
    "Parámetros obligatorios", "- ``saveFlag_flag``：Si se guarda tras un corte de energía"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de suavizado de aceleración
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    endjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    enddescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.AccSmoothStart(0)
    print(f"AccSmoothStart rtn is {rtn}")
    robot.MoveJ(joint_pos=startjointPos,tool= 0,user= 0,vel= 100)
    robot.MoveJ(joint_pos=endjointPos,tool= 0,user= 0,vel= 100)
    rtn = robot.AccSmoothEnd(0)
    print(f"AccSmoothEnd rtn is {rtn}")

Activación de la velocidad de orientación especificada del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AngularSpeedStart(ratio)``"
    "Descripción", "Activación de la velocidad de orientación especificada"
    "Parámetros obligatorios", "- ``ratio``:Porcentaje de velocidad de orientación [0-300]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Desactivación de la velocidad de orientación especificada
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AngularSpeedEnd()``"
    "Descripción", "Desactivación de la velocidad de orientación especificada"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Ejemplo de código de velocidad de orientación especificada del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    endjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    enddescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.AngularSpeedStart(50)
    print(f"AngularSpeedStart rtn is {rtn}")
    robot.MoveJ(joint_pos=startjointPos, tool=0,user= 0,vel= 100)
    robot.MoveJ(joint_pos=endjointPos, tool=0,user= 0,vel= 100)
    rtn = robot.AngularSpeedEnd()
    print(f"AngularSpeedEnd rtn is {rtn}")
    robot.CloseRPC()

Activación de la protección de pose singular
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SingularAvoidStart(protectMode, minShoulderPos=100, minElbowPos=50, minWristPos=10)``"
    "Descripción", "Activación de la protección de pose singular"
    "Parámetros obligatorios", "
    - ``protectMode``：Modo de protección de pose singular: 0-modo de articulaciones; 1-modo cartesiano
    "
    "Parámetros predeterminados", "- ``minShoulderPos``：Rango de ajuste de singularidad de hombro (mm), valor predeterminado 100.0
    - ``minElbowPos``：Rango de ajuste de singularidad de codo (mm), valor predeterminado 50.0
    - ``minWristPos``：Rango de ajuste de singularidad de muñeca (°), valor predeterminado 10.0"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Desactivación de la protección de pose singular
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SingularAvoidEnd()``"
    "Descripción", "Desactivación de la protección de pose singular"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Ejemplo de código de protección de pose singular del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    endjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    enddescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.SingularAvoidStart(2, 10, 5, 5)
    print(f"SingularAvoidStart rtn is {rtn}")
    robot.MoveJ(joint_pos=startjointPos, tool=0,user= 0,vel= 100)
    robot.MoveJ(joint_pos=endjointPos, tool=0,user= 0,vel= 100)
    rtn = robot.SingularAvoidEnd()
    print(f"SingularAvoidEnd rtn is {rtn}")
    robot.CloseRPC()

Vaciar la cola de instrucciones de movimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MotionQueueClear()``"
    "Descripción", "Vaciar la cola de instrucciones de movimiento"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Vaciar la cola de instrucciones de movimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveToIntersectLineStart(mainPoint, piecePoint, tool, wobj, vel, acc, ovl, oacc, moveType,mainExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]],pieceExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]],extAxisFlag=0,exaxisPos=[0.0,0.0,0.0,0.0],moveDirection=0,offset=[0.0,0.0,0.0,0.0,0.0,0.0])``"
    "Descripción", "Moverse al punto inicial de la línea de intersección"
    "Parámetros obligatorios", "
    - ``mainPoint``：Pose cartesiana de los 6 puntos de enseñanza del tubo principal
    - ``piecePoint``：Pose cartesiana de los 6 puntos de enseñanza del tubo auxiliar
    - ``tool``：Número del sistema de coordenadas de herramienta
    - ``wobj``：Número del sistema de coordenadas de pieza
    - ``vel``：Porcentaje de velocidad
    - ``acc``：Porcentaje de aceleración
    - ``ovl``：Factor de escala de velocidad
    - ``oacc``：Factor de escala de aceleración
    - ``moveType``：Tipo de movimiento; 0-PTP; 1-LIN
    - ``mainExaxisPos``：Posición del eje extendido de los 6 puntos de enseñanza del tubo principal, valor predeterminado [[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]]
    - ``pieceExaxisPos``：Posición del eje extendido de los 6 puntos de enseñanza del tubo de empalme, valor predeterminado [[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]]
    - ``extAxisFlag``：Si se habilita el eje extendido; 0-no habilitar; 1-habilitar
    - ``exaxisPos``：Posición del eje extendido del punto inicial [0.0,0.0,0.0,0.0]
    - ``moveDirection``：Dirección de movimiento; 0-sentido horario; 1-sentido antihorario
    - ``offset``：Cantidad de desplazamiento
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Movimiento de línea de intersección
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveIntersectLine(mainPoint, piecePoint, tool, wobj, vel, acc, ovl, oacc, moveDirection,mainExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]],pieceExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]],extAxisFlag=0,exaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]],offset=[0.0,0.0,0.0,0.0,0.0,0.0])``"
    "Descripción", "Movimiento de línea de intersección"
    "Parámetros obligatorios", "
    - ``mainPoint``：Pose cartesiana de los 6 puntos de enseñanza del tubo principal
    - ``piecePoint``：Pose cartesiana de los 6 puntos de enseñanza del tubo auxiliar
    - ``tool``：Número del sistema de coordenadas de herramienta
    - ``wobj``：Número del sistema de coordenadas de pieza
    - ``vel``：Porcentaje de velocidad
    - ``acc``：Porcentaje de aceleración
    - ``ovl``：Factor de escala de velocidad
    - ``oacc``：Factor de escala de aceleración
    - ``moveDirection``：Dirección de movimiento; 0-sentido horario; 1-sentido antihorario
    - ``mainExaxisPos``：Posición del eje extendido de los 6 puntos de enseñanza del tubo principal, valor predeterminado [[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]]
    - ``pieceExaxisPos``：Posición del eje extendido de los 6 puntos de enseñanza del tubo de empalme, valor predeterminado [[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]]
    - ``extAxisFlag``：Si se habilita el eje extendido; 0-no habilitar; 1-habilitar
    - ``exaxisPos``：Posición del eje extendido del punto inicial [0.0,0.0,0.0,0.0]
    - ``offset``：Cantidad de desplazamiento
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Ejemplo de código de movimiento de línea de intersección del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    mainPoint = [[0.0] * 6 for _ in range(6)]
    piecePoint = [[0.0] * 6 for _ in range(6)]
    mainExaxisPos = [[0.0] * 4 for _ in range(6)]
    pieceExaxisPos = [[0.0] * 4 for _ in range(6)]
    extAxisFlag = 1
    exaxisPos = [[0.0] * 4 for _ in range(4)]
    offset = [0.0, 2.0, 30.0, -2.0, 0.0, 0.0]
    mainPoint[0] = [490.004, -383.194, 402.735, -9.332, -1.528, 69.594]
    mainPoint[1] = [444.950, -407.117, 389.011, -5.546, -2.196, 65.279]
    mainPoint[2] = [445.168, -463.605, 355.759, -1.544, -10.886, 57.104]
    mainPoint[3] = [507.529, -485.385, 343.013, -0.786, -4.834, 61.799]
    mainPoint[4] = [554.390, -442.647, 367.701, -4.761, -10.181, 64.925]
    mainPoint[5] = [532.552, -394.003, 396.467, -13.732, -13.592, 67.411]
    mainExaxisPos[0] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[1] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[2] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[3] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[4] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[5] = [-29.996, 0.000, 0.000, 0.000]
    piecePoint[0] = [505.571, -192.408, 316.759, 38.098, 37.051, 139.447]
    piecePoint[1] = [533.837, -201.558, 332.340, 34.644, 42.339, 137.748]
    piecePoint[2] = [530.386, -225.085, 373.808, 35.431, 45.111, 137.560]
    piecePoint[3] = [485.646, -229.195, 383.778, 33.870, 45.173, 137.064]
    piecePoint[4] = [460.551, -212.161, 354.256, 28.856, 45.602, 135.930]
    piecePoint[5] = [474.217, -197.124, 324.611, 42.469, 41.133, 148.167]
    pieceExaxisPos[0] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[1] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[2] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[3] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[4] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[5] = [-29.996, -0.000, 0.000, 0.000]
    exaxisPos[0] = [-29.996, -0.000, 0.000, 0.000]
    exaxisPos[1] = [-44.994, 90.000, 0.000, 0.000]
    exaxisPos[2] = [-59.992, 0.002, 0.000, 0.000]
    exaxisPos[3] = [-44.994, -89.997, 0.000, 0.000]
    tool = 2
    wobj = 0
    vel = 100.0
    acc = 100.0
    ovl = 12.0
    oacc = 12.0
    moveType = 1
    moveDirection = 1
    rtn = robot.MoveToIntersectLineStart(mainPoint=mainPoint, mainExaxisPos=mainExaxisPos, piecePoint=piecePoint, pieceExaxisPos=pieceExaxisPos, extAxisFlag=extAxisFlag,exaxisPos=exaxisPos[0], tool=tool, wobj=wobj, vel=vel, acc=acc, ovl=ovl, oacc=oacc, moveType=moveType, moveDirection=moveDirection, offset=offset)
    print(f"MoveToIntersectLineStart rtn is {rtn}")
    rtn = robot.MoveIntersectLine(mainPoint=mainPoint, mainExaxisPos=mainExaxisPos, piecePoint=piecePoint, pieceExaxisPos=pieceExaxisPos, extAxisFlag=extAxisFlag, exaxisPos=exaxisPos, tool=tool,wobj=wobj, vel=vel, acc=acc, ovl=5.0, oacc=5.0, moveDirection=moveDirection, offset=offset)
    print(f"MoveIntersectLine rtn is {rtn}")
    robot.CloseRPC()

Movimiento en vacío en el lugar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveStationary()``"
    "Descripción", "Movimiento en vacío en el lugar"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"
 
Ejemplo de código de movimiento en vacío en el lugar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 0, 10, 100)
    print(f"LaserSensorRecordandReplay rtn is {rtn}")
    rtn = robot.MoveStationary()
    print(f"MoveStationary rtn is {rtn}")
    rtn = robot.LaserSensorRecord1(0, 10)
    print(f"LaserSensorRecordandReplay rtn is {rtn}")
    robot.CloseRPC()
    return 0

Inicio de la oscilación de punto fijo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``OriginPointWeaveStart(weaveNum, mode, refPoint, weaveTime)``"
    "Descripción", "Inicio de la oscilación de punto fijo"
    "Parámetros obligatorios", "
    - ``weaveNum``:Número de oscilación [0-7]
    - ``mode``:0-sistema de coordenadas de herramienta; 1-punto de referencia
    - ``refPoint``:Coordenadas cartesianas del punto de referencia [x,y,z,a,b,c]
    - ``weaveTime``:Tiempo de oscilación [s]
    - "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Fin de la oscilación de punto fijo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``OriginPointWeaveEnd()``"
    "Descripción", "Fin de la oscilación de punto fijo"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Ejemplo de código SDK de oscilación de punto fijo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from time import sleep
    import time
    from fairino import Robot

    # Establecer comunicación con el controlador del robot
    robot = Robot.RPC('192.168.58.2')

    def TestOriginPointWeave(self):
        time.sleep(2)
        # Inicializar posición de articulaciones, eje externo y desplazamiento
        j = [39.886, -98.580, -124.032, -47.393, 90.000, 40.842]
        epos = [0, 0, 0, 0]
        offset_pos = [0, 0, 0, 0, 0, 0]

        # Posición del punto de referencia [x, y, z, rx, ry, rz]
        refPoint = [400.021, 300.022, 299.996, 179.997, -0.003, -90.956]

        # Moverse a la posición inicial
        robot.MoveJ(joint_pos=j, tool=1, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        # Primera oscilación: sistema de coordenadas absoluto (tool=0), modo 0
        robot.OriginPointWeaveStart(0, 0, refPoint, 3)
        robot.MoveStationary()
        robot.OriginPointWeaveEnd()

        time.sleep(2)

        # Moverse de nuevo a la posición inicial
        robot.MoveJ(joint_pos=j, tool=1, user=0, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        # Segunda oscilación: sistema de coordenadas absoluto (tool=0), modo 1
        robot.OriginPointWeaveStart(0, 1, refPoint, 3)
        robot.MoveStationary()
        robot.OriginPointWeaveEnd()

        # Cerrar la conexión
        robot.CloseRPC()
        time.sleep(1)

    TestOriginPointWeave(robot)

Ejemplo de código SDK de oscilación de punto fijo (incluye láser y eje extendido)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from time import sleep
    import time
    from fairino import Robot

    # Establecer comunicación con el controlador del robot
    robot = Robot.RPC('192.168.58.2')

    def TestOriginPointWeave(self):
        time.sleep(2)
        # Inicializar posición de articulaciones, eje externo y desplazamiento
        j = [39.886, -98.580, -124.032, -47.393, 90.000, 40.842]
        epos1 = [0, 0, 0, 0]
        offset_pos = [0, 0, 0, 0, 0, 0]
        epos2 = [5, 0.000, 0.000, 0.000]
        # Posición del punto de referencia [x, y, z, rx, ry, rz]
        refPoint = [400.021, 300.022, 299.996, 179.997, -0.003, -90.956]

        rtn = 0
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020)
        robot.LaserTrackingSensorSamplePeriod(20)
        robot.LoadPosSensorDriver(101)

        # Cargar el controlador UDP
        robot.ExtDevLoadUDPDriver()

        # Establecer el tiempo de finalización del comando del eje externo
        rtn = robot.SetExAxisCmdDoneTime(5000.0)
        print(f"SetExAxisCmdDoneTime rtn is {rtn}")

        # Habilitar los ejes externos 1 y 2
        rtn = robot.ExtAxisServoOn(1, 1)
        print(f"ExtAxisServoOn axis id 1 rtn is {rtn}")
        rtn = robot.ExtAxisServoOn(2, 1)
        print(f"ExtAxisServoOn axis id 2 rtn is {rtn}")
        time.sleep(2)

        # Establecer el retorno a cero del eje externo
        robot.ExtAxisSetHoming(1, 0, 10, 2)
        robot.LaserTrackingLaserOnOff(1)

        # 1---sin eje extendido
        robot.LaserTrackingTrackOnOff(1, 4)
        time.sleep(0.2)
        # Iniciar la oscilación de punto fijo
        robot.OriginPointWeaveStart(0, 0, refPoint, 10)
        robot.MoveStationary()  # Ejecutar el movimiento fijo (se asume que el método existe)
        robot.OriginPointWeaveEnd()
        robot.LaserTrackingTrackOnOff(0, 4)

        time.sleep(2)  # Esperar 2 segundos

        # 2----con eje extendido
        robot.ExtAxisMove(epos1, 100, -1)
        robot.LaserTrackingTrackOnOff(1, 4)
        # Iniciar la oscilación de punto fijo
        robot.OriginPointWeaveStart(0, 0, refPoint, 20)
        robot.ExtAxisMove(epos2, 100, -1)
        robot.OriginPointWeaveEnd()
        robot.LaserTrackingTrackOnOff(0, 4)

        # Cerrar la conexión
        robot.CloseRPC()
        time.sleep(1)

    TestOriginPointWeave(robot)

Movimiento en modo servo de velocidad del espacio de articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoJV(self, joint_vel, exis_vel, acc=0.0, vel=0.0, cmdT=0.008, filterT=0.0, gain=0.0, id=0, comType=0)``"
    "Descripción", "Movimiento en modo servo de velocidad del espacio de articulaciones"
    "Parámetros obligatorios", "
    - ``joint_vel``:Velocidad objetivo de las 6 articulaciones, unidad deg/s
    - ``exis_vel``:Velocidad de los 4 ejes externos, unidad deg/s
    - ``acc``: Porcentaje de aceleración, rango [0~100], aún no disponible, valor predeterminado 0
    - ``vel``:Porcentaje de velocidad, rango [0~100], aún no disponible, valor predeterminado 0
    - ``cmdT``:Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016]
    - ``filterT``:Tiempo de filtrado, unidad s, aún no disponible, valor predeterminado 0
    - ``gain``:Amplificador proporcional de la posición objetivo, aún no disponible, valor predeterminado 0
    - ``id``:ID de la instrucción servoJ, valor predeterminado 0
    - ``comType``:Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de movimiento en modo servo de velocidad del espacio de articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time

    def main():
        # Establecer comunicación con el controlador del robot
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        # Inicializar el arreglo de velocidades de las articulaciones y el arreglo de velocidades de los ejes extendidos
        joint_vel = [10.0, 0.0, 0.0, 0.0, 0.0, 0.0]
        exis_vel = [0.0, 0.0, 0.0, 0.0]
        acc = 0.0
        vel = 0.0
        cmdT = 0.008
        filterT = 0.0
        gain = 0.0
        cnt = 0

        # Llamar cíclicamente a ServoJV, 200 veces en total
        while cnt < 200:
            rtn = robot.ServoJV(joint_vel=joint_vel, exis_vel=exis_vel, acc=acc, vel=vel,
                                cmdT=cmdT, filterT=filterT, gain=gain)
            print(f"ServoJV rtn is {rtn}")
            cnt += 1

        # Cerrar la conexión
        robot.CloseRPC()


    # Llamar a la función de prueba
    main()

Inicio del control MIT de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoMITStart(self, comType=0)``"
    "Descripción", "Inicio del control MIT de las articulaciones"
    "Parámetros obligatorios", "
    - ``comType``:Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin del control MIT de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoMITEnd(self, comType=0)``"
    "Descripción", "Fin del control MIT de las articulaciones"
    "Parámetros obligatorios", "
    - ``comType``:Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Control MIT de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoMIT(self, posGain, desPos, velGain, desVel, torque_ff, interval, comType=0)``"
    "Descripción", "Control MIT de las articulaciones"
    "Parámetros obligatorios", "
    - ``posGain``:Ganancia de posición de las articulaciones j1~j6
    - ``desPos``:Posición deseada de las articulaciones j1~j6, unidad: deg
    - ``velGain``:Ganancia de velocidad de las articulaciones j1~j6
    - ``desVel``:Velocidad deseada de las articulaciones j1~j6, unidad: deg/s
    - ``torque_ff``:Par de prealimentación de las articulaciones j1~j6, unidad: Nm
    - ``interval``:Período de instrucción, unidad s, rango [0.001~0.008]
    - ``comType``:Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de control MIT de las articulaciones del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from time import sleep
    import time
    from fairino import Robot

    # Establecer comunicación con el controlador del robot
    robot = Robot.RPC('192.168.58.2')

    # Definir la función de devolución de llamada
    def udp_frame_callback(src_type, count, cmd_id, data_len, content):
        """Función de devolución de llamada de respuesta de comandos UDP"""
        print(f"Función de devolución de llamada: cmd_id={cmd_id} count={count} data_len={data_len} content={content}")
        return 0

    def ServoMITtest(self):
        # Establecer la función de devolución de llamada de respuesta de comandos UDP
        robot.SetUDPCmdRpyCallback(udp_frame_callback)

        while True:
            # Restablecer todos los errores
            robot.ResetAllError()
            time.sleep(0.5)

            # Inicializar arreglos de parámetros
            posGain = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
            desPos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
            velGain = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
            desVel = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
            torques = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

            # Obtener el par de las articulaciones
            rtn, torques = robot.GetJointTorques(flag=1)
            print(f"GetJointTorques rtn: {rtn}")
            print("111111")

            # Iniciar el modo Servo MIT
            rtn = robot.ServoMITStart(0)
            print(f"ServoMITStart rtn: {rtn}")

            # Activar la enseñanza por arrastre
            rtn = robot.DragTeachSwitch(1)
            print(f"DragTeachSwitch rtn: {rtn}")

            intev = 0.008

            # Movimiento positivo: par positivo en la articulación 6 hasta que el ángulo supere 30 grados
            while True:
                torques[5] = 0.03
                rtn = robot.ServoMIT(posGain, desPos, velGain,
                                    desVel, torques, intev, comType=0)
                print(f"ServoMIT call rtn is {rtn}")
                time.sleep(0.001)  # 1ms

                rtn, pkg = robot.GetRobotRealTimeState()
                print(f"pkg.jt_cur_pos[5]: {pkg.jt_cur_pos[5]}")

                if pkg.jt_cur_pos[5] > 30:
                    break

            # Movimiento negativo: par negativo en la articulación 6 hasta que el ángulo sea menor que 0 grados
            while True:
                torques[5] = -0.03
                rtn = robot.ServoMIT(posGain, desPos, velGain,
                                    desVel, torques, intev, comType=0)
                print(f"ServoMIT call rtn is {rtn}")
                time.sleep(0.001)  # 1ms

                rtn, pkg = robot.GetRobotRealTimeState()
                print(f"pkg.jt_cur_pos[5]: {pkg.jt_cur_pos[5]}")

                if pkg.jt_cur_pos[5] < 0:
                    break

            # Desactivar la enseñanza por arrastre
            rtn = robot.DragTeachSwitch(0)
            print(f"DragTeachSwitch off rtn: {rtn}")

            # Finalizar el modo Servo MIT
            rtn = robot.ServoMITEnd(0)
            print(f"ServoMITEnd rtn: {rtn}")

    # Llamar a la función de prueba
    ServoMITtest(robot)

Inicio de la conversión de puntos del sistema de coordenadas de pieza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded::python SDK-v3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WorkPieceTrsfStart(self, workpieceID)``"
    "Descripción", "Inicio de la conversión de puntos del sistema de coordenadas de pieza"
    "Parámetros obligatorios", "
    - ``workpieceID``: Número de pieza [0-14]
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"    

Fin de la conversión de puntos del sistema de coordenadas de pieza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded::python SDK-v3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WorkPieceTrsfEnd((self)``"
    "Descripción", "Fin de la conversión de puntos del sistema de coordenadas de pieza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"    

Ejemplo de código de conversión de puntos del sistema de coordenadas de pieza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded::python SDK-v3.9.8

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        j1 = [-11.188, -64.165, -107.299, -76.706, 89.590, 92.983]
        j2 = [-38.148, -97.408, -133.704, -30.999, 89.584, 92.986]
        j3 = [-25.561, -123.131, -85.736, -94.911, 89.582, 93.006]
        j4 = [-8.013, -125.881, -79.196, -84.440, 89.564, 93.005]
        j5 = [-2.722, -94.518, -119.965, -54.518, 89.563, 93.005]
        j6 = [-2.671, -56.234, -138.914, -25.099, 95.355, 92.967]
        j7 = [-1.229, -121.184, -63.201, -122.331, 93.045, 93.019]

        desc1 = [225.986, 190.694, 394.238, -6.230, -23.797, -98.972]
        desc2 = [52.741, 262.917, 30.824, -5.696, -9.864, -126.092]
        desc3 = [70.455, 88.410, 45.299, -4.101, 31.775, -113.199]
        desc4 = [209.453, -73.895, 56.416, -4.727, 17.523, -95.906]
        desc5 = [274.800, 81.106, 102.977, -5.467, -2.980, -90.711]
        desc6 = [300.392, 177.281, 300.926, -1.909, -51.894, -89.703]
        desc7 = [296.856, -31.294, 215.698, -0.589, 34.594, -88.954]

        exaxis = [0.0, 0.0, 0.0, 0.0]
        offset = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        tool = 1
        workpiece = 1
        blend = 5.0

        robot.MoveJ(joint_pos=j1, desc_pos=desc1, tool=tool, user=workpiece,
                    vel=100, acc=100, ovl=100, exaxis_pos=exaxis,
                    blendT=-1, offset_flag=0, offset_pos=offset)

        robot.MoveJ(joint_pos=j2, desc_pos=desc2, tool=tool, user=workpiece,
                    vel=100, acc=100, ovl=100, exaxis_pos=exaxis,
                    blendT=blend, offset_flag=0, offset_pos=offset)

        robot.MoveL(joint_pos=j3, desc_pos=desc3, tool=tool, user=workpiece,
                    vel=10, acc=100, ovl=100, blendR=blend, blendMode=0,
                    exaxis_pos=exaxis, search=0, offset_flag=1, offset_pos=offset)

        robot.MoveC(desc_pos_p=desc4, tool_p=tool, user_p=workpiece,
                    desc_pos_t=desc5, tool_t=tool, user_t=workpiece,
                    joint_pos_p=j4, joint_pos_t=j5,
                    vel_p=100, acc_p=100, exaxis_pos_p=exaxis, offset_flag_p=0, offset_pos_p=offset,
                    vel_t=100, acc_t=100, exaxis_pos_t=exaxis, offset_flag_t=0, offset_pos_t=offset,
                    ovl=10, blendR=blend)

        robot.Circle(desc_pos_p=desc6, tool_p=tool, user_p=workpiece,
                    desc_pos_t=desc7, tool_t=tool, user_t=workpiece,
                    joint_pos_p=j6, joint_pos_t=j7,
                    vel_p=100, acc_p=100, exaxis_pos_p=exaxis,
                    vel_t=100, acc_t=100, exaxis_pos_t=exaxis,
                    ovl=10, offset_flag=0, offset_pos=offset, blendR=blend)
        rtn = robot.WorkPieceTrsfStart(2)
        print(f"WorkPieceTrsfStart rtn is {rtn}")

        robot.MoveJ(joint_pos=j1, desc_pos=desc1, tool=tool, user=workpiece,
                    vel=100, acc=100, ovl=100, exaxis_pos=exaxis,
                    blendT=-1, offset_flag=0, offset_pos=offset)

        robot.MoveJ(joint_pos=j2, desc_pos=desc2, tool=tool, user=workpiece,
                    vel=100, acc=100, ovl=100, exaxis_pos=exaxis,
                    blendT=blend, offset_flag=0, offset_pos=offset)

        robot.MoveL(joint_pos=j3, desc_pos=desc3, tool=tool, user=workpiece,
                    vel=10, acc=100, ovl=100, blendR=blend, blendMode=0,
                    exaxis_pos=exaxis, search=0, offset_flag=1, offset_pos=offset)

        robot.MoveC(desc_pos_p=desc4, tool_p=tool, user_p=workpiece,
                    desc_pos_t=desc5, tool_t=tool, user_t=workpiece,
                    joint_pos_p=j4, joint_pos_t=j5,
                    vel_p=100, acc_p=100, exaxis_pos_p=exaxis, offset_flag_p=0, offset_pos_p=offset,
                    vel_t=100, acc_t=100, exaxis_pos_t=exaxis, offset_flag_t=0, offset_pos_t=offset,
                    ovl=10, blendR=blend)

        robot.Circle(desc_pos_p=desc6, tool_p=tool, user_p=workpiece,
                    desc_pos_t=desc7, tool_t=tool, user_t=workpiece,
                    joint_pos_p=j6, joint_pos_t=j7,
                    vel_p=100, acc_p=100, exaxis_pos_p=exaxis,
                    vel_t=100, acc_t=100, exaxis_pos_t=exaxis,
                    ovl=10, offset_flag=0, offset_pos=offset, blendR=blend)
        rtn = robot.WorkPieceTrsfEnd()
        print(f"WorkPieceTrsfEnd rtn is {rtn}")

        robot.CloseRPC()
        time.sleep(2)


    if __name__ == "__main__":
        main()
        
Movimiento en modo servo del espacio de articulaciones (admite la entrada de múltiples puntos a la vez)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoJMultiPos(self, joint_pos, axisPos, acc=0.0, vel=0.0, cmdT=0.008, filterT=0.0, gain=0.0, id=0, cmdType=0)``"
    "Descripción", "Movimiento en modo servo del espacio de articulaciones (admite la entrada de múltiples puntos a la vez)"
    "Parámetros obligatorios", "
    - ``joint_pos``: Conjunto de posiciones objetivo de las articulaciones (admite hasta 10 grupos), unidad deg, lista bidimensional, cada elemento son 6 posiciones de articulaciones
    - ``axisPos``: Posición del eje externo, unidad mm, 4 elementos
    - ``acc``: Porcentaje de aceleración, rango [0~100], aún no disponible, valor predeterminado 0.0
    - ``vel``: Porcentaje de velocidad, rango [0~100], aún no disponible, valor predeterminado 0.0
    - ``cmdT``: Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016], valor predeterminado 0.008
    - ``filterT``: Tiempo de filtrado, unidad s, aún no disponible, valor predeterminado 0.0
    - ``gain``: Amplificador proporcional de la posición objetivo, aún no disponible, valor predeterminado 0.0
    - ``id``: ID de la instrucción servoJ, valor predeterminado 0
    - ``cmdType``: Tipo de transmisión de comandos, 0=XML-RPC, 1=UDP transparente
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode
    - ``servoJCmdCount``: Contador de puntos de la instrucción ServoJ [0-10000] (solo devuelto en modo XML-RPC)"   
        
Ejemplo de código de movimiento en modo servo del espacio de articulaciones (entrada de múltiples puntos)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:     

    from fairino import Robot
    import time

    def main():
        # Establecer comunicación con el controlador del robot
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        # ========== Leer el archivo de trayectoria de articulaciones ==========
        file_path = "C://Users/lenovo/Desktop/ServoJPath.txt"
        all_joint_data = []

        try:
            with open(file_path, 'r') as fin:
                for line in fin:
                    parts = line.strip().split()
                    if len(parts) >= 6:
                        # Omitir la primera columna (columna de índice), tomar las columnas 2~7 (índices 1~6)
                        one_pose = [float(parts[i]) for i in range(1, 7)]
                        all_joint_data.append(one_pose)
        except FileNotFoundError:
            print("无法打开文件 ServoJPath.txt")
            return

        print(f"Se leyeron en total {len(all_joint_data)} conjuntos de posiciones de articulaciones")

        # ========== Construir la trayectoria de ida y vuelta (directo + inverso, eliminando los extremos duplicados) ==========
        back_forth_path = all_joint_data.copy()
        # Añadir en orden inverso desde el penúltimo (eliminando el punto final duplicado)
        for i in range(len(all_joint_data) - 2, -1, -1):
            back_forth_path.append(all_joint_data[i])

        print(f"Total de puntos de la trayectoria de ida y vuelta: {len(back_forth_path)}")

        epos = [0.0, 0.0, 0.0, 0.0]
        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        # Moverse a la posición inicial
        robot.MoveJ(joint_pos=all_joint_data[0], tool=0, user=0,
                    vel=100, acc=100, ovl=100, exaxis_pos=epos,
                    blendT=-1, offset_flag=0, offset_pos=offset_pos)

        time.sleep(1)

        # ========== Bucle principal ==========
        while True:
            # Restablecer todos los errores
            robot.ResetAllError()

            # Moverse a la posición inicial
            robot.MoveJ(joint_pos=all_joint_data[0], tool=0, user=0,
                        vel=100, acc=100, ovl=100, exaxis_pos=epos,
                        blendT=-1, offset_flag=0, offset_pos=offset_pos)

            move_count = 0
            total_points = len(back_forth_path)

            while move_count < total_points - 10:
                # Obtener el estado en tiempo real del robot
                rtn, pkg = robot.GetRobotRealTimeState()

                # Calcular la cantidad de comandos ServoJ que se pueden enviar en una sola vez
                single_servo_j_count = 50 - pkg.mc_queue_len
                if single_servo_j_count <= 0:
                    time.sleep(0.1)
                    continue

                if single_servo_j_count > 10:
                    single_servo_j_count = 10

                # Construir la lista de posiciones de articulaciones a enviar (lista bidimensional, cada elemento contiene 6 ángulos de articulaciones)
                joint_pos_list = []
                for j in range(single_servo_j_count):
                    if move_count < total_points:
                        joint_pos_list.append(back_forth_path[move_count])
                        move_count += 1
                    else:
                        break

                # Enviar el comando ServoJ de múltiples puntos
                axis_pos = [0.0, 0.0, 0.0, 0.0]
                # Nota sobre el orden de los parámetros: joint_pos, axisPos, acc, vel, cmdT, filterT, gain, id, cmdType
                # acc=100.0 corresponde al 100.0 de C++, vel=100.0 corresponde al 100.0 de C++
                rtn, servo_j_cmd_count = robot.ServoJMultiPos(joint_pos_list, axis_pos,
                                                            acc=100.0, vel=100.0,
                                                            cmdT=0.008, filterT=0.008,
                                                            gain=1.0, id=0, cmdType=0)
                if rtn != 0:
                    print(f"ServoJMultiPos falló, código de error: {rtn}")
                    break

                # Imprimir información de depuración
                print(f"Se enviaron {len(joint_pos_list)} puntos, contador de comandos ServoJ: {servo_j_cmd_count}")

            time.sleep(4)

        # Cerrar la conexión (normalmente no se llega aquí)
        robot.CloseRPC()


    if __name__ == "__main__":
        main()