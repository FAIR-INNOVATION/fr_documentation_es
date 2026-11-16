Control de fuerza del robot
===========================

.. toctree:: 
    :maxdepth: 5

Configuración del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_SetConfig(company,device,softversion=0,bus=0)``"
    "Descripción", "Configuración del sensor de fuerza"
    "Parámetros obligatorios", "- ``company``：Fabricante del sensor, 17-Kunwei Technology, 19-11º Instituto de Aeroespacial, 20-Sensor ATI, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xinjingcheng (XJC), 26-NSR;
    - ``device``：Número de dispositivo, Kunwei(0-KWR75B), 11º Instituto de Aeroespacial(0-MCS6A-200-4), ATI(0-AXIA80-M8), Zhongke Midian(0-MST2010), Weihang Minxin(0-WHC6L-YB-10A), NBIT(0-XLH93003ACS), Xinjingcheng XJC(0-XJC-6F-D82), NSR(0-NSR-FTSensorA);"
    "Parámetros predeterminados", "- ``softversion``：Número de versión de software, aún no utilizado, valor predeterminado 0;
    - ``bus``：Posición del bus del extremo donde está montado el dispositivo, aún no utilizado, valor predeterminado 0;"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener la configuración del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_GetConfig()``"
    "Descripción", "Obtener la configuración del sensor de fuerza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``[number,company,device,softversion,bus]``：number número del sensor; company fabricante del sensor de fuerza, 17-Kunwei Technology, 19-11º Instituto de Aeroespacial, 20-Sensor ATI, 21-Zhongke Midian, 22-Weihang Minxin; device número de dispositivo, Kunwei (0-KWR75B), 11º Instituto de Aeroespacial (0-MCS6A-200-4), ATI(0-AXIA80-M8), Zhongke Midian (0-MST2010), Weihang Minxin (0-WHC6L-YB10A); softvesion número de versión de software, aún no utilizado, valor predeterminado 0" 

Activación del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_Activate(state)``"
    "Descripción", "Activación del sensor de fuerza"
    "Parámetros obligatorios", "- ``state``：0-reiniciar, 1-activar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Puesta a cero del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_SetZero(state)``"
    "Descripción", "Puesta a cero del sensor de fuerza"
    "Parámetros obligatorios", "- ``state``：0-eliminar el punto cero, 1-corrección del punto cero"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el sistema de coordenadas de referencia del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_SetRCS(ref,coord=[0,0,0,0,0,0])``"
    "Descripción", "Establecer el sistema de coordenadas de referencia del sensor de fuerza"
    "Parámetros obligatorios", "- ``ref``：0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base"
    "Parámetros predeterminados", "- ``coord``：[x,y,z,rx,ry,rz] valor del sistema de coordenadas personalizado, valor predeterminado [0,0,0,0,0,0]"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

        
Establecer el peso de la carga bajo el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetForceSensorPayload(weight)``"
    "Descripción", "Establecer el peso de la carga bajo el sensor de fuerza"
    "Parámetros obligatorios", " - ``weight``：Peso de la carga kg"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
  
Establecer el centro de masa de la carga bajo el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetForceSensorPayloadCog(x,y,z)``"
    "Descripción", "Establecer el centro de masa de la carga bajo el sensor de fuerza"
    "Parámetros obligatorios", "
    - ``x``：centro de masa de la carga x mm
    - ``y``：centro de masa de la carga y mm
    - ``z``：centro de masa de la carga z mm
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
            
Obtener el peso de la carga bajo el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetForceSensorPayload()``"
    "Descripción", "Obtener el peso de la carga bajo el sensor de fuerza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``weight``：Peso de la carga kg"
            
Obtener el centro de masa de la carga bajo el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetForceSensorPayloadCog()``"
    "Descripción", "Obtener el centro de masa de la carga bajo el sensor de fuerza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``x``：centro de masa de la carga x mm 
    - ``y``：centro de masa de la carga y mm 
    - ``z``：centro de masa de la carga z mm"

Puesta a cero automática del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ForceSensorAutoComputeLoad()``"
    "Descripción", "Puesta a cero automática del sensor de fuerza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``weight``：Masa del sensor kg
    - ``pos=[x,y,z]``：Centro de masa del sensor mm"

Obtener los datos de fuerza/par en el sistema de coordenadas de referencia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_GetForceTorqueRCS()``"
    "Descripción", "Obtener los datos de fuerza/par en el sistema de coordenadas de referencia"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``data=[fx,fy,fz,tx,ty,tz]``：Datos de fuerza/par en el sistema de coordenadas de referencia"

Obtener los datos brutos de fuerza/par del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_GetForceTorqueOrigin()``"
    "Descripción", "Obtener los datos brutos de fuerza/par del sensor de fuerza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode  
    - ``data=[fx,fy,fz,tx,ty,tz]``：Datos brutos de fuerza/par del sensor de fuerza "

Ejemplo de código de configuración del sensor de fuerza y puesta a cero automática
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot 
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    error,ft = robot.FT_GetForceTorqueOrigin()
    print(f"ft origin:{ft[0]},{ft[1]},{ft[2]},{ft[3]},{ft[4]},{ft[5]}")
    robot.FT_SetZero(1)
    time.sleep(1)
    ftCoord = [0, 0, 0, 0, 0, 0]
    robot.FT_SetRCS(0, ftCoord)
    robot.SetForceSensorPayload(0.824)
    robot.SetForceSensorPayloadCog(0.778, 2.554, 48.765)
    error,weight = robot.GetForceSensorPayload()
    error,x, y, z = robot.GetForceSensorPayloadCog()
    print(f"the FT load is  {weight}, {x} {y} {z}")
    robot.SetForceSensorPayload(0)
    robot.SetForceSensorPayloadCog(0, 0, 0)
    error,computeWeight, tran = robot.ForceSensorAutoComputeLoad()
    print(f"the result is weight {computeWeight} pos is {tran[0]} {tran[1]} {tran[2]}")
    robot.CloseRPC()

Registro de identificación del peso de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_PdIdenRecord(tool_id)``"
    "Descripción", "Registro de identificación del peso de la carga"
    "Parámetros obligatorios", "- ``tool_id``：Número del sistema de coordenadas del sensor, rango [0~14]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode  "

Cálculo de identificación del peso de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_PdIdenCompute()``"
    "Descripción", "Cálculo de identificación del peso de la carga"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode   
    - ``weight``：Peso de la carga, unidad kg  "

Registro de identificación del centro de masa de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_PdCogIdenRecord(tool_id,index)``"
    "Descripción", "Registro de identificación del centro de masa de la carga"
    "Parámetros obligatorios", "- ``tool_id``：Número del sistema de coordenadas del sensor, rango [0~14];
    - ``index``：Número de punto [1~3]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Cálculo de identificación del centro de masa de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_PdCogIdenCompute()``"
    "Descripción", "Cálculo de identificación del centro de masa de la carga"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode  
    - ``cog=[cogx,cogy,cogz]``：Centro de masa de la carga, unidad mm  "

Ejemplo de código de identificación de carga del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot 
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    error,ft = robot.FT_GetForceTorqueOrigin()
    print(f"ft origin:{ft[0]},{ft[1]},{ft[2]},{ft[3]},{ft[4]},{ft[5]}")
    robot.FT_SetZero(1)
    time.sleep(1)
    tcoord = [0, 0, 35.0, 0, 0, 0]
    robot.SetToolCoord(10, tcoord, 1, 0, 0, 0)
    robot.FT_PdIdenRecord(10)
    time.sleep(1)
    error,weight = robot.FT_PdIdenCompute()
    print(f"payload weight:{weight}")
    desc_p1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_p2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_p3 = [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207]
    robot.MoveCart(desc_p1, 0, 0, 100.0)
    time.sleep(1)
    robot.FT_PdCogIdenRecord(10, 1)
    robot.MoveCart(desc_p2, 0, 0, 100.0)
    time.sleep(1)
    robot.FT_PdCogIdenRecord(10, 2)
    robot.MoveCart(desc_p3, 0, 0, 100.0)
    time.sleep(1)
    robot.FT_PdCogIdenRecord(10, 3)
    time.sleep(1)
    error,cog = robot.FT_PdCogIdenCompute()
    print(f"FT_PdCogIdenCompute return {error}")
    print(f"cog:{cog[0]},{cog[1]},{cog[2]}")
    robot.CloseRPC()

Protección de colisión
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_Guard(flag,sensor_num,select,force_torque,max_threshold,min_threshold)``"
    "Descripción", "Protección de colisión"
    "Parámetros obligatorios", "- ``flag``：0-desactivar la protección de colisión, 1-activar la protección de colisión;
    - ``sensor_num``：Número del sensor de fuerza;
    - ``select``：Si se detecta colisión en los seis grados de libertad [fx,fy,fz,mx,my,mz], 0-no efectivo, 1-efectivo;
    - ``force_torque``：Fuerza/par de detección de colisión, unidad N o Nm;
    - ``max_threshold``：Umbral máximo;
    - ``min_threshold``：Umbral mínimo;
    - Rango de detección de fuerza/par: (force_torque-min_threshold, force_torque+max_threshold)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Ejemplo de código de protección de colisión
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    sensor_id = 1
    select = [1, 1, 1, 1, 1, 1]
    max_threshold = [10.0, 10.0, 10.0, 10.0, 10.0, 10.0]
    min_threshold = [5.0, 5.0, 5.0, 5.0, 5.0, 5.0]
    ft = None 
    desc_p1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_p2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_p3 = [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207]
    error = robot.FT_Guard(1, sensor_id, select,[0.0,0.0,0.0,0.0,0.0,0.0], max_threshold, min_threshold)
    robot.MoveCart(desc_p1, 0, 0, 100.0)
    robot.MoveCart(desc_p2, 0, 0, 100.0)
    robot.MoveCart(desc_p3, 0, 0, 100.0)
    robot.FT_Guard(0, sensor_id, select,[0.0,0.0,0.0,0.0,0.0,0.0], max_threshold, min_threshold)
    robot.CloseRPC()

Control de fuerza constante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M=None, B=None, threshold=[0.2,0.2], adjustCoeff=[1.0,1.0], polishRadio=0, filter_Sign=0, posAdapt_sign=0, isNoBlock=0)``"
    "Descripción", "Control de fuerza constante"
    "Parámetros obligatorios", "- ``flag``：Indicador de activación del control de fuerza constante, 0-desactivado, 1-activado;
    - ``sensor_id``：Número del sensor de fuerza;
    - ``select``：Si se detecta en los seis grados de libertad [fx,fy,fz,mx,my,mz], 0-no efectivo, 1-efectivo;
    - ``ft``：Fuerza/par de detección, unidad N o Nm;
    - ``ft_pid``：[f_p,f_i,f_d,m_p,m_i,m_d], parámetros PID de fuerza, parámetros PID de par;
    - ``adj_sign``：Estado de inicio/parada adaptativo, 0-desactivado, 1-activado;
    - ``ILC_sign``: Estado de inicio/parada del control ILC, 0-detener, 1-entrenamiento, 2-operación práctica;
    - ``max_dis``：Distancia máxima de ajuste;
    - ``max_ang``：Ángulo máximo de ajuste;"
    "Parámetros predeterminados", "- ``M``：Parámetros de masa;
    - ``B``：Parámetros de amortiguación;
    - ``threshold``：Umbral de activación rx, ry [0-10], valor predeterminado 0.2;
    - ``adjustCoeff``：Coeficiente de ajuste del par rx, ry [0-1], valor predeterminado 1;
    - ``polishRadio``：Radio del disco de pulido, unidad mm;
    - ``filter_Sign``：Indicador de activación del filtrado 0-desactivado; 1-activado, valor predeterminado 0-desactivado;
    - ``posAdapt_sign``：Indicador de activación de adaptación de orientación 0-desactivado; 1-activado, valor predeterminado 0-desactivado;
    - ``isNoBlock``：Indicador de bloqueo, 0-bloqueante; 1-no bloqueante, valor predeterminado 0-bloqueante;"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Ejemplo de código de control de fuerza constante con amortiguación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    sensor_id = 10
    select = [0, 0, 1, 0, 0, 0]
    ft_pid = [0.0008, 0.0, 0.0, 0.0, 0.0, 0.0]
    adj_sign = 0
    ILC_sign = 0
    max_dis = 1000.0
    max_ang = 20.0
    ft = [0.0] * 6 
    epos = [0.0] * 4
    j1 = [80.765, -98.795, 106.548, -97.734, -89.999, 94.842]
    j2 = [43.067, -84.429, 92.620, -98.175, -90.011, 57.144]
    desc_p1 = [5.009, -547.463, 262.053, -179.999, -0.019, 75.923]
    desc_p2 = [-347.966, -547.463, 262.048, -180.000, -0.019, 75.923]
    offset_pos = [0.0] * 6
    M = [2.0, 2.0]
    B = [15.0, 15.0]
    threshold = [1.0, 1.0]
    adjustCoeff = [1.0, 0.8]
    polishRadio = 0.0
    filter_Sign = 0
    posAdapt_sign = 1
    isNoBlock = 0
    ft[2] = -10.0 
    while True:
        rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold,adjustCoeff, 0, 0, 1, 0)
        print(f"FT_Control start rtn is {rtn}")
        rtn = robot.MoveL(desc_pos=desc_p1, tool=1, user=0, vel=100, acc=100, ovl=100, blendR=-1, blendMode = 0, exaxis_pos=epos, search=0, offset_flag=0, offset_pos=offset_pos)
        rtn = robot.MoveL(desc_pos=desc_p2, tool=1, user=0, vel=100, acc=100, ovl=100, blendR=-1, blendMode = 0, exaxis_pos=epos, search=0, offset_flag=0, offset_pos=offset_pos)
        rtn = robot.FT_Control(0, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold,adjustCoeff, 0, 0, 1, 0)
        print(f"FT_Control end rtn is {rtn}")
    robot.CloseRPC()
    return 0

Exploración en hélice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_SpiralSearch(rcs, ft, dr=0.7, max_t_ms=60000, max_vel=5, strategy=0)``"
    "Descripción", "Exploración en hélice"
    "Parámetros obligatorios", "- ``rcs``：Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    - ``ft``：Umbral de fuerza o par (0~100), unidad N o Nm;"
    "Parámetros predeterminados", "- ``dr``：Avance de radio por vuelta, unidad mm, valor predeterminado 0.7;
    - ``max_t_ms``：Tiempo máximo de exploración, unidad ms, valor predeterminado 60000;
    - ``max_vel``：Velocidad lineal máxima, unidad mm/s, valor predeterminado 5;
    - ``strategy``：Estrategia de tratamiento cuando no se detecta fuerza/par, 0-error; 1-advertencia, continuar el movimiento;"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Inserción giratoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_RotInsertion(rcs, ft, orn, angVelRot=3, angleMax=45, angAccmax=0, rotorn=1, strategy=0)``"
    "Descripción", "Inserción giratoria"
    "Parámetros obligatorios", "- ``rcs``：Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base;
    - ``ft``：Umbral de fuerza o par (0~100), unidad N o Nm;
    - ``orn``：Dirección de fuerza/par, 1-a lo largo del eje z, 2-alrededor del eje z;"
    "Parámetros predeterminados", "- ``angVelRot``：Velocidad angular de rotación, unidad °/s, valor predeterminado 3;
    - ``angleMax``：Ángulo máximo de rotación, unidad °, valor predeterminado 45;
    - ``angAccmax``：Aceleración angular máxima de rotación, unidad °/s^2, aún no utilizada, valor predeterminado 0;
    - ``rotorn``：Dirección de rotación, 1-sentido horario, 2-sentido antihorario, valor predeterminado 1;
    - ``strategy``：Estrategia de tratamiento cuando no se detecta fuerza/par, 0-error; 1-advertencia, continuar el movimiento"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Ejemplo de código de instrucciones como exploración en hélice, inserción recta, etc.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    j1=[-11.904,-99.669,117.473,-108.616,-91.726,74.256]
    j2=[-45.615,-106.172,124.296,-107.151,-91.282,74.255]
    j3=[-29.777,-84.536,109.275,-114.075,-86.655,74.257]
    j4=[-31.154,-95.317,94.276,-88.079,-89.740,74.256]
    desc_pos1=[-419.524,-13.000,351.569,-178.118,0.314,3.833]
    desc_pos2=[-321.222,185.189,335.520,-179.030,-1.284,-29.869]
    desc_pos3=[-487.434,154.362,308.576,176.600,0.268,-14.061]
    desc_pos4=[-443.165,147.881,480.951,179.511,-0.775,-15.409]
    offset_pos=[0.0]*6
    epos=[0.0]*4
    tool=0
    user=0
    vel=100.0
    acc=100.0
    ovl=100.0
    oacc=100.0
    blendT=0.0
    blendR=0.0
    flag=0
    search=0
    blendMode=0
    velAccMode=0
    robot.SetSpeed(20)
    rtn=robot.MoveJ(joint_pos=j1,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.MoveL(desc_pos=desc_pos2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,blendR=blendR,blendMode=blendMode,exaxis_pos=epos,search=search,offset_flag=flag,offset_pos=offset_pos,oacc=oacc,velAccParamMode=velAccMode)
    print(f"movelerrcode:{rtn}")
    rtn=robot.MoveC(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,offset_flag_p=flag,offset_pos_p=offset_pos,desc_pos_t=desc_pos4,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,offset_flag_t=flag,offset_pos_t=offset_pos,ovl=ovl,blendR=blendR,oacc=oacc,velAccParamMode=velAccMode)
    print(f"movecerrcode:{rtn}")
    rtn=robot.MoveJ(joint_pos=j2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.Circle(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,desc_pos_t=desc_pos1,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,ovl=ovl,offset_flag=flag,offset_pos=offset_pos,oacc=oacc,blendR=-1,velAccParamMode=velAccMode)
    print(f"circleerrcode:{rtn}")
    rtn=robot.MoveCart(desc_pos=desc_pos4,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,blendT=blendT,config=-1)
    print(f"MoveCarterrcode:{rtn}")
    rtn=robot.MoveJ(joint_pos=j1,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.MoveL(desc_pos=desc_pos2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,blendR=blendR,blendMode=blendMode,exaxis_pos=epos,search=search,offset_flag=flag,offset_pos=offset_pos,config=-1,velAccParamMode=velAccMode)
    print(f"movelerrcode:{rtn}")
    rtn=robot.MoveC(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,offset_flag_p=flag,offset_pos_p=offset_pos,desc_pos_t=desc_pos4,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,offset_flag_t=flag,offset_pos_t=offset_pos,ovl=ovl,blendR=blendR,config=-1,velAccParamMode=velAccMode)
    print(f"movecerrcode:{rtn}")
    rtn=robot.MoveJ(joint_pos=j2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.Circle(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,desc_pos_t=desc_pos1,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,ovl=ovl,offset_flag=flag,offset_pos=offset_pos,oacc=oacc,blendR=-1,velAccParamMode=velAccMode)
    print(f"circleerrcode:{rtn}")
    robot.CloseRPC()
    return0

Inserción recta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_LinInsertion(rcs, ft, disMax, linorn, lin_v=1.0, lin_a=1.0, strategy=0)``"
    "Descripción", "Inserción recta"
    "Parámetros obligatorios", "- ``rcs``：Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base;
    - ``ft``：Umbral de fuerza o par (0~100), unidad N o Nm;
    - ``disMax``：Distancia máxima de inserción, unidad mm;
    - ``linorn``：Dirección de inserción: 0-dirección negativa, 1-dirección positiva"
    "Parámetros predeterminados", "
    - ``lin_v``：Velocidad lineal, unidad mm/s, valor predeterminado 1;
    - ``lin_a``：Aceleración lineal, unidad mm/s^2, aún no utilizada, valor predeterminado 1;
    - ``strategy``：Estrategia de tratamiento cuando no se detecta fuerza/par, 0-error; 1-advertencia, continuar el movimiento;"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Ejemplo de código de instrucciones como exploración en hélice, inserción recta, etc.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:
    
    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    status = 1
    sensor_num = 1
    gain = [0.0001, 0.0, 0.0, 0.0, 0.0, 0.0]
    adj_sign = 0
    ILC_sign = 0
    max_dis = 100.0
    max_ang = 5.0
    ft = [0.0,0.0,-10.0,0.0,0.0,0.0]
    rcs = 0
    dr = 0.7
    fFinish = 1.0
    t = 60000.0
    vmax = 3.0
    force_goal = 20.0
    lin_v = 0.0
    lin_a = 0.0
    disMax = 100.0
    linorn = 1
    angVelRot = 2.0
    forceInsertion = 1.0
    angleMax = 45
    orn = 1
    angAccmax = 0.0
    rotorn = 1
    select1 = [0, 0, 1, 1, 1, 0]
    robot.FT_Control(status, sensor_num, select1, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_SpiralSearch(rcs, dr, fFinish, t, vmax)
    print(f"FT_SpiralSearch rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select1, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    select2 = [1, 1, 1, 0, 0, 0]
    gain[0] = 0.00005
    ft[2] = -30.0
    robot.FT_Control(1, sensor_num, select2, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn)
    print(f"FT_LinInsertion rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select2, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    select3 = [0, 0, 1, 1, 1, 0]
    ft[2] = -10.0
    gain[0] = 0.0001
    robot.FT_Control(1, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_RotInsertion(rcs, angVelRot, forceInsertion, angleMax, orn, angAccmax, rotorn)
    print(f"FT_RotInsertion rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    select4 = [1, 1, 1, 0, 0, 0]
    ft[2] = -30.0
    robot.FT_Control(1, sensor_num, select4, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn)
    print(f"FT_LinInsertion rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select4, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    robot.CloseRPC()

Localización de superficie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_FindSurface (rcs, dir, axis, disMax, ft, lin_v=3.0, lin_a=0.0, stragety = 0)``"
    "Descripción", "Localización de superficie"
    "Parámetros obligatorios", "- ``rcs``： Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base;
    - ``dir``：Dirección de movimiento, 1-dirección positiva, 2-dirección negativa;
    - ``axis``：Eje de movimiento, 1-x, 2-y, 3-z;
    - ``disMax``：Distancia máxima de exploración, unidad mm;
    - ``ft``：Umbral de fuerza de terminación de la acción, unidad N;"
    "Parámetros predeterminados", "- ``lin_v``：Velocidad lineal de exploración, unidad mm/s, valor predeterminado 3;
    - ``lin_a``：Aceleración lineal de exploración, unidad mm/s^2, valor predeterminado 0;
    - ``strategy``：Estrategia de tratamiento cuando no se detecta fuerza/par, 0-error; 1-advertencia, continuar el movimiento;"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Inicio del cálculo de la posición del plano intermedio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_CalCenterStart()``"
    "Descripción", "Inicio del cálculo de la posición del plano intermedio"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin del cálculo de la posición del plano intermedio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_CalCenterEnd()``"
    "Descripción", "Fin del cálculo de la posición del plano intermedio"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode
    - ``pos=[x,y,z,rx,ry,rz]``：Posición del plano intermedio"

Ejemplo de código de localización de superficie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    rcs = 0
    dir = 1
    axis = 1
    lin_v = 3.0
    lin_a = 0.0
    maxdis = 50.0
    ft_goal = 2.0
    desc_pos = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    xcenter = [0, 0, 0, 0, 0, 0]
    ycenter = [0, 0, 0, 0, 0, 0]
    ft = [-2.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    robot.MoveCart(desc_pos, 9, 0, 100.0)
    robot.FT_CalCenterStart()
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    robot.MoveCart(desc_pos, 9, 0)
    robot.WaitMs(1000)
    dir = 2
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    error,xcenter = robot.FT_CalCenterEnd()
    print(f"xcenter:{xcenter[0]},{xcenter[1]},{xcenter[2]},{xcenter[3]},{xcenter[4]},{xcenter[5]}")
    robot.MoveCart(xcenter, 9, 0, 60.0)
    robot.FT_CalCenterStart()
    dir = 1
    axis = 2
    lin_v = 6.0
    maxdis = 150.0
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    robot.MoveCart(desc_pos, 9, 0, 100.0)
    robot.WaitMs(1000)
    dir = 2
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    error,ycenter = robot.FT_CalCenterEnd()
    print(f"ycenter:{ycenter[0]},{ycenter[1]},{ycenter[2]},{ycenter[3]},{ycenter[4]},{ycenter[5]}")
    robot.MoveCart(ycenter, 9, 0, 60.0)
    robot.CloseRPC()

Ejemplo de código de estrategia de fallo de exploración de control de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        # Establecer comunicación con el controlador del robot
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        print("========== Inicio de la prueba de estrategia de control de fuerza FT ==========")

        # ========== FT_SpiralSearch: strategy 0 / 1 ==========
        print("=== FT_SpiralSearch strategy=0 ===")
        rtn = robot.FT_SpiralSearch(0, 5, 5.0, 3000.0, 3.0, 0)
        print(f"FT_SpiralSearch(0) rtn is {rtn}")
        time.sleep(5)
        robot.ResetAllError()
        time.sleep(2)

        print("=== FT_SpiralSearch strategy=1 ===")
        rtn = robot.FT_SpiralSearch(0, 5, 1.0, 3000.0, 3.0, 1)
        print(f"FT_SpiralSearch(1) rtn is {rtn}")
        time.sleep(5)
        robot.ResetAllError()
        time.sleep(2)

        # ========== FT_LinInsertion: strategy 0/1 ==========
        print("=== FT_LinInsertion strategy=0 ===")
        rtn = robot.FT_LinInsertion(0, 20.0, 15.0, 1.0, 10.0, 1, 0)
        print(f"FT_LinInsertion(0) rtn is {rtn}")
        time.sleep(5)
        robot.ResetAllError()
        time.sleep(2)

        print("=== FT_LinInsertion strategy=1 ===")
        rtn = robot.FT_LinInsertion(0, 20.0, 15.0, 1.0, 10.0, 1, 1)
        print(f"FT_LinInsertion(1) rtn is {rtn}")
        time.sleep(5)
        robot.ResetAllError()
        time.sleep(2)

        # ========== FT_FindSurface: strategy 0/1 ==========
        print("=== FT_FindSurface strategy=0 ===")
        rtn = robot.FT_FindSurface(0, 1, 1, 15.0, 5, 50.0, 20.0, 0)
        print(f"FT_FindSurface(0) rtn is {rtn}")
        time.sleep(10)
        robot.ResetAllError()
        time.sleep(5)

        print("=== FT_FindSurface strategy=1 ===")
        rtn = robot.FT_FindSurface(0, 1, 1, 15.0, 5, 50.0, 20.0, 1)
        print(f"FT_FindSurface(1) rtn is {rtn}")
        time.sleep(10)
        robot.ResetAllError()

        print("finish")

        # Cerrar la conexión
        robot.CloseRPC()

    if __name__ == "__main__":
        main()

Activación del control de cumplimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_ComplianceStart(p, force)``"
    "Descripción", "Activación del control de cumplimiento"
    "Parámetros obligatorios", "- ``p``: Coeficiente de ajuste de posición o coeficiente de cumplimiento
    - ``force``：Umbral de fuerza de activación del cumplimiento, unidad N"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode  "

Desactivación del control de cumplimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_ComplianceStop()``"
    "Descripción", "Desactivación del control de cumplimiento"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de control de cumplimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    flag = 1
    sensor_id = 1
    select = [1, 1, 1, 0, 0, 0]
    ft_pid = [0.0005, 0.0, 0.0, 0.0, 0.0, 0.0]
    adj_sign = 0
    ILC_sign = 0
    max_dis = 100.0
    max_ang = 0.0
    ft = [-10.0, -10.0, -10.0, 0.0, 0.0, 0.0]
    offset_pos = [0.0,0.0,0.0,0.0,0.0,0.0]  # Sustituye a DescPose(0, 0, 0, 0, 0, 0)
    epos = [0.0,0.0,0.0,0.0]  # Sustituye a ExaxisPos(0, 0, 0, 0)
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]  # JointPos
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    desc_p1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]  # DescPose
    desc_p2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    p = 0.00005
    force = 30.0
    rtn = robot.FT_ComplianceStart(p, force)
    print(f"FT_ComplianceStart rtn is {rtn}")
    count = 3
    while count > 0:
        robot.MoveL(desc_pos=desc_p1,tool= 0,user= 0,vel= 100.0)
        robot.MoveL(desc_pos=desc_p2,tool= 0,user= 0,vel= 100.0)
        count -= 1
    robot.FT_ComplianceStop()
    print(f"FT_ComplianceStop rtn is {rtn}")
    flag = 0
    robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    robot.CloseRPC()

Inicialización del filtro de identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadIdentifyDynFilterInit()``"
    "Descripción", "Inicialización del filtro de identificación de carga"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode  "

Inicialización de variables de identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadIdentifyDynVarInit()``"
    "Descripción", "Inicialización de variables de identificación de carga"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode  "

Programa principal de identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadIdentifyMain(joint_torque, joint_pos, t)``"
    "Descripción", "Programa principal de identificación de carga"
    "Parámetros obligatorios", "- ``joint_torque``： Par de las articulaciones j1-j6;
    - ``joint_pos``：Posición de las articulaciones j1-j6
    - ``t``：Período de muestreo"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el resultado de la identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadIdentifyGetResult(gain)``"
    "Descripción", "Obtener el resultado de la identificación de carga"
    "Parámetros obligatorios", "- ``gain``：Coeficiente del término de gravedad double[6], coeficiente del término centrífugo double[6]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``weight``：Peso de la carga
    - ``cog=[x,y,z]``：Coordenadas del centro de masa de la carga"

Ejemplo de código de identificación de carga del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    retval = robot.LoadIdentifyDynFilterInit()
    print(f"LoadIdentifyDynFilterInit retval is: {retval}")
    retval = robot.LoadIdentifyDynVarInit()
    print(f"LoadIdentifyDynVarInit retval is: {retval}")
    error, posJ = robot.GetActualJointPosDegree(0)
    posJ[1] += 10  # Modificar la articulación 2
    error, joint_toq = robot.GetJointTorques(0)
    joint_toq[1] += 2  # Modificar el par en la articulación 2
    tmpTorque = joint_toq.copy()
    retval = robot.LoadIdentifyMain(tmpTorque, posJ, 1)
    print(f"LoadIdentifyMain retval is: {retval}")
    gain = [0, 0.05, 0, 0, 0, 0, 0, 0.02, 0, 0, 0, 0]
    weight = [0.0]
    load_pos = [0.0, 0.0, 0.0]
    retval, weight, load_pos = robot.LoadIdentifyGetResult(gain)
    print(f"LoadIdentifyGetResult retval is: {retval} ; weight is {weight}  cog is {load_pos[0]} {load_pos[1]} {load_pos[2]}")
    robot.CloseRPC()

Arrastre asistido por sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``EndForceDragControl(status, asaptiveFlag, interfereDragFlag, ingularityConstraintsFlag, M, B, K, F, Fmax, Vmax, forceCollisionFlag=0)``"
    "Descripción", "Arrastre asistido por sensor de fuerza"
    "Parámetros obligatorios", "- ``status``：Estado de control, 0-desactivar; 1-activar
    - ``asaptiveFlag``：Indicador de activación adaptativa, 0-desactivar; 1-activar
    - ``interfereDragFlag``：Indicador de arrastre en zona de interferencia, 0-desactivar; 1-activar
    - ``ingularityConstraintsFlag``：Estrategia de puntos singulares, 0-evitar; 1-atravesar
    - ``forceCollisionFlag``：Indicador de detección de colisión del robot durante el arrastre asistido; 0-desactivar; 1-activar
    - ``M=[m1,m2,m3,m4,m5,m6]``：Coeficientes de inercia
    - ``B=[b1,b2,b3,b4,b5,b6]``：Coeficientes de amortiguación
    - ``K=[k1,k2,k3,k4,k5,k6]``：Coeficientes de rigidez
    - ``F=[f1,f2,f3,f4,f5,f6]``：Umbral de fuerza de seis dimensiones para el arrastre
    - ``Fmax``：Límite máximo de fuerza de arrastre
    - ``Vmax``：Límite máximo de velocidad de las articulaciones"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
        
Obtener el estado del interruptor de arrastre del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetForceAndTorqueDragState()``"
    "Descripción", "Obtener el estado del interruptor de arrastre del sensor de fuerza"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``dragState``：Estado de control del arrastre asistido por sensor de fuerza, 0-desactivar; 1-activar
    - ``sixDimensionalDragState``：Estado de control del arrastre asistido de fuerza de seis dimensiones, 0-desactivar; 1-activar"
    
Apertura automática del sensor de fuerza tras el borrado de errores
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetForceSensorDragAutoFlag(status)``"
    "Descripción", "Apertura automática del sensor de fuerza tras el borrado de errores"
    "Parámetros obligatorios", "- ``status``：Estado de control, 0-desactivar; 1-activar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Ejemplo de código de arrastre asistido por sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.SetForceSensorDragAutoFlag(1)
    M = [15.0, 15.0, 15.0, 0.5, 0.5, 0.1]
    B = [150.0, 150.0, 150.0, 5.0, 5.0, 1.0]
    K = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    F = [10.0, 10.0, 10.0, 1.0, 1.0, 1.0]
    robot.EndForceDragControl(1, 0, 0, 0, M, B, K, F, 50, 100)
    time.sleep(5)
    drag_state = 0
    six_dimensional_drag_state = 0
    error,drag_state, six_dimensional_drag_state = robot.GetForceAndTorqueDragState()
    print(f"the drag state is {drag_state} {six_dimensional_drag_state}")
    robot.EndForceDragControl(0, 0, 0, 0, M, B, K, F, 50, 100)
    robot.CloseRPC()
    
Establecer el interruptor y los parámetros del arrastre mixto de fuerza de seis dimensiones e impedancia de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ForceAndJointImpedanceStartStop(status, impedanceFlag, lamdeDain, KGain, BGain, dragMaxTcpVel, dragMaxTcpOriVel)``"
    "Descripción", "Establecer el interruptor y los parámetros del arrastre mixto de fuerza de seis dimensiones e impedancia de articulaciones"
    "Parámetros obligatorios", "- ``status``：Estado de control, 0-desactivar; 1-activar
    - ``impedanceFlag``：Indicador de activación de impedancia, 0-desactivar; 1-activar
    - ``lamdeDain``：[D1,D2,D3,D4,D5, D6] ganancia de arrastre
    - ``KGain``：[K1,K2,K3,K4,K5,K6] ganancia de rigidez
    - ``BGain``：[B1,B2,B3,B4,B5,B] ganancia de amortiguación
    - ``dragMaxTcpVel``：Límite máximo de velocidad lineal del extremo durante el arrastre
    - ``dragMaxTcpOriVel``：Límite máximo de velocidad angular del extremo durante el arrastre"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de arrastre mixto de fuerza de seis dimensiones e impedancia de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.DragTeachSwitch(1)
    lamde_dain = [3.0, 2.0, 2.0, 2.0, 2.0, 3.0]
    k_gain = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    b_gain = [150.0, 150.0, 150.0, 5.0, 5.0, 1.0]
    rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lamde_dain, k_gain, b_gain, 1000, 180)
    print(f"ForceAndJointImpedanceStartStop rtn is {rtn}")
    time.sleep(5)
    robot.DragTeachSwitch(0)
    rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lamde_dain, k_gain, b_gain, 1000, 180)
    print(f"ForceAndJointImpedanceStartStop rtn is {rtn}")
    robot.CloseRPC()

Control de inicio/parada de impedancia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ImpedanceControlStartStop(status, workSpace, forceThreshold, m, b, k, maxV, maxVA, maxW, maxWA)``"
    "Descripción", "Control de inicio/parada de impedancia"
    "Parámetros obligatorios", "- ``status``：0-desactivar; 1-activar
    - ``workSpace``：0-espacio de articulaciones; 1-espacio cartesiano
    - ``forceThreshold``：Umbral de fuerza de activación (N)
    - ``m``：Parámetros de masa
    - ``b``：Parámetros de amortiguación
    - ``k``：Parámetros de rigidez
    - ``maxV``：Velocidad lineal máxima (mm/s)
    - ``maxVA``：Aceleración lineal máxima (mm/s2)
    - ``maxW``：Velocidad angular máxima (°/s)
    - ``maxWA``：Aceleración angular máxima (°/s2)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de control de inicio/parada de impedancia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    j1 = [102.622, -135.990, 120.769, -73.950, -90.848, 35.507]
    j2 = [93.674, -80.062, 82.947, -92.199, -90.967, 26.559]
    desc_pos1 = [136.552, -149.799, 449.532, 179.817, -1.172, 157.123]
    desc_pos2 = [136.540, -561.048, 449.542, 179.819, -1.172, 157.122]
    offset_pos = [0.0] * 6
    epos = [0.0] * 4
    tool = 0
    user = 0
    vel = 100.0
    acc = 200.0
    ovl = 100.0
    blendT = -1.0
    blendR = -1.0
    flag = 0
    search = 0
    robot.SetSpeed(20)
    company = 17
    device = 0
    softversion = 0
    bus = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    rnt,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    robot.FT_SetZero(1)
    time.sleep(1)
    forceThreshold = [30.0, 30.0, 30.0, 5.0, 5.0, 5.0]
    m = [0.1, 0.1, 0.1, 0.02, 0.02, 0.02]
    b = [1.0, 1.0, 1.0, 0.08, 0.08, 0.08]
    k = [0.0] * 6
    rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100)
    print(f"ImpedanceControlStartStop errcode:{rtn}")
    rtn = robot.MoveL(desc_pos=desc_pos1,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos2,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos1,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos2,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos1,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos2,tool= tool,user= user,vel= vel,speedPercent=1)
    print(f"movel errcode:{rtn}")
    robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100)
    robot.CloseRPC()

Activar la función de compensación de par y los coeficientes de compensación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetCoderCompenParams(status, torqueCoeff)``"
    "Descripción", "Activar la función de compensación de par y los coeficientes de compensación"
    "Parámetros obligatorios", "- ``status``：Interruptor, 0-desactivar; 1-activar
    - ``torqueCoeff``：Coeficientes de compensación de par J1-J6 [0-1]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"