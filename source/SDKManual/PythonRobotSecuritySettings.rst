Configuración de seguridad del robot
=====================================

.. toctree:: 
    :maxdepth: 5

Establecer nivel de colisión
+++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAnticollision (mode,level,config)``"
    "Descripción", "Establecer nivel de colisión"
    "Parámetros obligatorios", "- ``mode``:0-nivel，1-porcentaje；
    - ``level=[j1,j2,j3,j4,j5,j6]``:umbral de colisión；
    - ``config``:0-no actualizar archivo de configuración，1-actualizar archivo de configuración"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer estrategia tras colisión
++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetCollisionStrategy(strategy,safeTime,safeDistance,safeVel,safetyMargin)``"
    "Descripción", "Establecer estrategia tras colisión"
    "Parámetros obligatorios", "- ``strategy``：0-pausar con error，1-continuar ejecutando，2-detener con error，3-modo de par de gravedad，4-modo de respuesta oscilante，5-modo de rebote tras colisión"
    "Parámetros predeterminados", "- ``safeTime``：tiempo de parada segura[1000-2000]ms，predeterminado：1000
    - ``safeDistance``：distancia de parada segura[1-150]mm，predeterminado：100
    - ``safeVel``：velocidad de parada segura[50-250]mm/s，predeterminado：250
    - ``safetyMargin[6]``：coeficiente de seguridad[1-10]，predeterminado：[10,10,10,10,10,10]"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Inicio de la función de umbral de detección de colisión personalizado, establecimiento de umbrales de detección de colisión del lado articular y del lado TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.0

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CustomCollisionDetectionStart(flag, jointDetectionThreshould, tcpDetectionThreshould, block)``"
    "Descripción", "Inicio de la función de umbral de detección de colisión personalizado, establecimiento de umbrales de detección de colisión del lado articular y del lado TCP"
    "Parámetros obligatorios", "- ``flag``： 1-solo detección articular activada；2-solo detección TCP activada；3-detección articular y TCP activadas simultáneamente
    - ``jointDetectionThreshould``： umbral de detección de colisión articular j1-j6
    - ``tcpDetectionThreshould``： umbral de detección de colisión TCP，xyzabc
    - ``block``： 0-no bloqueante；1-bloqueante"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Cierre de la función de umbral de detección de colisión personalizado
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.0

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CustomCollisionDetectionEnd()``"
    "Descripción", "Cierre de la función de umbral de detección de colisión personalizado"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Ejemplo de código de configuración del nivel de colisión del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    mode = 0
    config = 1
    level1 = [1.0, 2.0, 3.0, 4.0, 5.0, 6.0]
    level2 = [50.0, 20.0, 30.0, 40.0, 50.0, 60.0]
    rtn = robot.SetAnticollision(mode, level1, config)
    print(f"SetAnticollision mode 0 rtn is {rtn}")
    mode = 1
    rtn = robot.SetAnticollision(mode, level2, config)
    print(f"SetAnticollision mode 1 rtn is {rtn}")
    p1Joint = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    p2Joint = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    robot.MoveL(desc_pos=p2Desc, tool=0, user=0, vel=100, blendR=2)
    robot.ResetAllError()
    safety = [5, 5, 5, 5, 5, 5]
    rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety)
    print(f"SetCollisionStrategy rtn is {rtn}")
    jointDetectionThreshould = [0.1, 0.1, 0.1, 0.1, 0.1, 0.1]
    tcpDetectionThreshould = [60, 60, 60, 60, 60, 60]
    rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0)
    print(f"CustomCollisionDetectionStart rtn is {rtn}")
    robot.MoveL(desc_pos=p1Desc, tool=0, user=0, vel=100)
    robot.MoveL(desc_pos=p2Desc, tool=0, user=0, vel=100)
    rtn = robot.CustomCollisionDetectionEnd()
    print(f"CustomCollisionDetectionEnd rtn is {rtn}")
    robot.CloseRPC()

Establecer límite positivo
++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLimitPositive(p_limit)``"
    "Descripción", "Establecer límite positivo"
    "Parámetros obligatorios", "- ``p_limit=[j1,j2,j3,j4,j5,j6]``：seis posiciones articulares"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer límite negativo
++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLimitNegative(n_limit)``"
    "Descripción", "Establecer límite negativo"
    "Parámetros obligatorios", "- ``n_limit=[j1,j2,j3,j4,j5,j6]``：seis posiciones articulares"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener ángulo de límite suave articular
+++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetJointSoftLimitDeg(flag=1)``"
    "Descripción", "Obtener ángulo de límite suave articular"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "``flag``：0-bloqueante，1-no bloqueante  predeterminado1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``[j1min,j1max,j2min,j2max,j3min,j3max, j4min,j4max,j5min, j5max, j6min,j6max]``：eje1~eje6，límite negativo y límite positivo articular，unidad[mm]"

Ejemplo de código de configuración de límites del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    plimit = [170.0, 80.0, 150.0, 80.0, 170.0, 160.0]
    robot.SetLimitPositive(plimit)
    nlimit = [-170.0, -260.0, -150.0, -260.0, -170.0, -160.0]
    robot.SetLimitNegative(nlimit)
    error,neg_deg = robot.GetJointSoftLimitDeg(0)
    print(f"pos limit deg: {neg_deg[1]}, {neg_deg[3]}, {neg_deg[5]}, {neg_deg[7]}, {neg_deg[9]}, {neg_deg[11]}")
    print(f"neg limit deg: {neg_deg[0]}, {neg_deg[2]}, {neg_deg[4]}, {neg_deg[6]}, {neg_deg[8]}, {neg_deg[10]}")
    robot.CloseRPC()

Establecer método de detección de colisión del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetCollisionDetectionMethod(method, thresholdMode)``"
    "Descripción", "Establecer método de detección de colisión del robot"
    "Parámetros obligatorios", "
    - ``method``：método de detección de colisión：0-modo de corriente；1-doble codificador；2-corriente y doble codificador activados simultáneamente
    - ``thresholdMode``：modo de umbral del nivel de colisión；0-modo de umbral fijo por nivel de colisión；1-umbral de detección de colisión personalizado  
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Establecer inicio y cierre de la detección de colisión en estado estático
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetStaticCollisionOnOff(status)``"
    "Descripción", "Establecer inicio y cierre de la detección de colisión en estado estático"
    "Parámetros obligatorios", "
    - ``status``： 0-cerrar；1-abrir
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Ejemplo de código para establecer el método de detección de colisión del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.SetCollisionDetectionMethod(0,0)
    rtn = robot.SetStaticCollisionOnOff(1)
    print(f"SetStaticCollisionOnOff On rtn is {rtn}")
    time.sleep(5)
    rtn = robot.SetStaticCollisionOnOff(0)
    print(f"SetStaticCollisionOnOff Off rtn is {rtn}")
    robot.CloseRPC()

Detección de potencia de par articular
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetPowerLimit(status, power)``"
    "Descripción", "Detección de potencia de par articular"
    "Parámetros obligatorios", "
    - ``status``：0-cerrar；1-abrir
    - ``power``：establecer potencia máxima(W)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"
    
Ejemplo de código de detección de potencia de par articular
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.DragTeachSwitch(1)
    robot.SetPowerLimit(1, 200)
    error,torques = robot.GetJointTorques(1)
    count = 100
    robot.ServoJTStart()
    while count > 0:
        error = robot.ServoJT(torques, 0.001)
        count -= 1
        time.sleep(0.001)  # retardo de 1ms
    error = robot.ServoJTEnd()
    robot.DragTeachSwitch(0)
    robot.CloseRPC()

Establecer parámetros de velocidad de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetVelReducePara(enable, maxTCPVel, strategy, maxJointVel=[45.0, 45.0, 45.0, 45.0, 45.0, 45.0])``"
    "Descripción", "Establecer parámetros de velocidad de seguridad"
    "Parámetros obligatorios", "
    - ``enable``：0-desactivado；1-activado en modo manual；2-activado en todos los modos(no soporta limitación automática de velocidad)
    - ``maxTCPVel``：limitar la velocidad máxima TCP;[0-1000]mm/s
    - ``strategy``：estrategia tras exceso de velocidad；0-detener con alarma；1-limitación automática de velocidad；2-detener con alarma y deshabilitar
    - ``maxJointVel``：velocidad máxima de las 6 articulaciones(°/s) predeterminado[45.0, 45.0, 45.0, 45.0, 45.0, 45.0]
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Ejemplo de código SDK de configuración de parámetros de velocidad de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time


    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        j1 = [10.220, -11.121, -118.086, -46.739, 82.036, 131.503]
        j2 = [89.782, -11.122, -118.086, -46.740, 82.036, 131.504]

        epos = [0.0, 0.0, 0.0, 0.0]
        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        robot.SetSpeed(20)

        maxJointVel = [100.0, 100.0, 100.0, 100.0, 100.0, 100.0]

        rtn = robot.SetVelReducePara(0, 200, 0, maxJointVel)
        robot.MoveJ(joint_pos=j2, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel)
        print(f"SetVelReduceParaA param error rtn is {rtn}")

        robot.MoveJ(joint_pos=j1, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        robot.MoveJ(joint_pos=j2, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        maxJointVel = [20.0, 20.0, 20.0, 20.0, 20.0, 20.0]
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel)
        print(f"SetVelReduceParaB reduce vel rtn is {rtn}")

        robot.MoveJ(joint_pos=j1, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        robot.MoveJ(joint_pos=j2, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        robot.CloseRPC()

    if __name__ == "__main__":
        main()

Obtener suma de verificación de los parámetros de configuración de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSafetyParamsCheckSum(self)``"
    "Descripción", "Obtener suma de verificación de los parámetros de configuración de seguridad"
    "Parámetros obligatorios", "
    - ``status``：estado de verificación，0-válido，1-en verificación，2-verificación fallida
    - ``checksum``：suma de verificación 8 dígitos hexadecimales (la capa inferior devuelve uint32_t, requiere conversión manual)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Verificación de contraseña de operación de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SafetyOPPasswordCheck(self,status,password)``"
    "Descripción", "Verificación de contraseña de operación de seguridad"
    "Parámetros obligatorios", "
    - ``status``：verificación，0-abrir，1-cerrar
    - ``password``：contraseña
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Ejemplo de código de verificación de contraseña de los parámetros de configuración de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from time import sleep
    import time
    from fairino import Robot

    # Establecer conexión con el controlador del robot
    robot = Robot.RPC('192.168.58.2')


    def test(self):
        error, status, hex_code = robot.GetSafetyParamsCheckSum()
        print(f"GetSafetyParamsChecksum: error={error}, status={status}, hex_code={hex_code}")
        time.sleep(3)
        error = robot.SafetyOPPasswordCheck(0, "12345678")
        print(f"SafetyOPPasswordCheck: error={error}")

        if error == 0:
            error = robot.SetAnticollision(mode=0, level=[2.0, 2.0, 2.0, 2.0, 2.0, 2.0], config=1)
            print(f"SetAnticollision: error={error}")

            error = robot.SetCollisionStrategy(strategy=0, safeTime=1000, safeDistance=150,
                                            safetyMargin=[10, 10, 10, 10, 10, 10])
            print(f"SetCollisionStrategy: error={error}")

        time.sleep(1)

        error, status, hex_code = robot.GetSafetyParamsCheckSum()
        print(f"GetSafetyParamsChecksum(again): error={error}, status={status}, hex_code={hex_code}")


    test(robot)