Eje extendido
================

.. toctree:: 
    :maxdepth: 5

Establecer los parámetros del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetParam(servoId,servoCompany,servoModel,servoSoftVersion, servoResolution,axisMechTransRatio)``"
    "Descripción", "Establecer los parámetros del eje extendido 485"
    "Parámetros obligatorios", "- ``servoId``：ID del servoaccionamiento, rango [1-15], corresponde al ID de esclavo;
    - ``servoCompany``：Fabricante del servoaccionamiento, 1-Dynatec;
    - ``servoModel``：Modelo del servoaccionamiento, 1-FD100-750C;
    - ``servoSoftVersion``：Versión de software del servoaccionamiento, 1-V1.0;
    - ``servoResolution``：Resolución del codificador;
    - ``axisMechTransRatio``：Relación de transmisión mecánica;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener los parámetros de configuración del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoGetParam(servoId)``"
    "Descripción", "Obtener los parámetros de configuración del eje extendido 485"
    "Parámetros obligatorios", "- ``servoId``：ID del servoaccionamiento, rango [1-15], corresponde al ID de esclavo;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode;
    - ``servoCompany``：Fabricante del servoaccionamiento, 1-Dynatec;
    - ``servoModel``：Modelo del servoaccionamiento, 1-FD100-750C;
    - ``servoSoftVersion``：Versión de software del servoaccionamiento, 1-V1.0;
    - ``servoResolution``：Resolución del codificador;
    - ``axisMechTransRatio``：Relación de transmisión mecánica;"

Establecer la habilitación/deshabilitación del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoEnable(servoId,status)``"
    "Descripción", "Establecer la habilitación/deshabilitación del eje extendido 485"
    "Parámetros obligatorios", "- ``servoId``：ID del servoaccionamiento, rango [1-15], corresponde al ID de esclavo;
    - ``status``：Estado de habilitación, 0-deshabilitar, 1-habilitar;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el modo de control del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetControlMode(servoId,mode)``"
    "Descripción", "Establecer el modo de control del eje extendido 485"
    "Parámetros obligatorios", "- ``servoId``：ID del servoaccionamiento, rango [1-15], corresponde al ID de esclavo;
    - ``mode``：Modo de control, 0-modo de posición, 1-modo de velocidad;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la posición objetivo del eje extendido 485 (modo de posición)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetTargetPos(servoId,pos,speed)``"
    "Descripción", "Establecer la posición objetivo del eje extendido 485 (modo de posición)"
    "Parámetros obligatorios", "- ``servoId``：ID del servoaccionamiento, rango [1-15], corresponde al ID de esclavo;
    - ``pos``：Posición objetivo, mm o °;
    - ``speed``：Velocidad objetivo, mm/s o °/s;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el par objetivo del eje extendido 485 (modo de par) - aún no disponible
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetTargetTorque(servoId,torque)``"
    "Descripción", "Establecer el par objetivo del eje extendido 485 (modo de par)"
    "Parámetros obligatorios", "- ``servoId``：ID del servoaccionamiento, rango [1-15], corresponde al ID de esclavo;
    - ``torque``：Par objetivo, Nm;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el retorno a cero del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoHoming(servoId,mode,searchVel,latchVel)``"
    "Descripción", "Establecer el retorno a cero del eje extendido 485"
    "Parámetros obligatorios", "- ``servoId``：ID del servoaccionamiento, rango [1-15], corresponde al ID de esclavo;
    - ``mode``：Modo de retorno a cero, 1-retorno a cero en la posición actual; 2-retorno a cero en el límite negativo; 3-retorno a cero en el límite positivo;
    - ``searchVel``： Velocidad de retorno a cero, mm/s o °/s;
    - ``latchVel``：Velocidad de enganche, mm/s o °/s;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Borrar la información de error del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoClearError(servoId)``"
    "Descripción", "Borrar la información de error del eje extendido 485"
    "Parámetros obligatorios", "- ``servoId``：ID del servoaccionamiento, rango [1-15], corresponde al ID de esclavo;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el estado del servo del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoGetStatus(servoId)``"
    "Descripción", "Obtener el estado del servo del eje extendido 485"
    "Parámetros obligatorios", "- ``servoId``：ID del servoaccionamiento, rango [1-15], corresponde al ID de esclavo;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode;
    - ``servoErrCode``：Código de fallo del servoaccionamiento
    - ``servoState``：Estado del servoaccionamiento bit0:0-no habilitado；1-habilitado;  bit1:0-sin movimiento；1-en movimiento;  bit2 0-límite positivo no activado；1-límite positivo activado；bit3 0-límite negativo no activado；1-límite negativo activado；bit4 0-posicionamiento no completado；1-posicionamiento completado；  bit5：0-sin retorno a cero；1-retorno a cero completado；
    - ``servoPos``：Posición actual del servo mm o °;
    - ``servoSpeed``：Velocidad actual del servo mm/s o °/s;
    - ``servoTorque``：Par actual del servo Nm;"

Establecer la velocidad objetivo del eje extendido 485 (modo de velocidad)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetTargetSpeed(servoId,speed)``"
    "Descripción", "Establecer la velocidad objetivo del eje extendido 485 (modo de velocidad)"
    "Parámetros obligatorios", "- ``servoId``：ID del servoaccionamiento, rango [1-15], corresponde al ID de esclavo;
    - ``speed``：Velocidad objetivo, mm/s o °/s;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el número de eje de los datos del eje extendido 485 en la retroalimentación de estado
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServosetStatusID(servoId)``"
    "Descripción", "Establecer el número de eje de los datos del eje extendido 485 en la retroalimentación de estado"
    "Parámetros obligatorios", "- ``servoId``：ID del servoaccionamiento, rango [1-15], corresponde al ID de esclavo;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la aceleración y desaceleración de movimiento del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetAcc(acc, dec)``"
    "Descripción", "Establecer la aceleración y desaceleración de movimiento del eje extendido 485"
    "Parámetros obligatorios", "- ``acc``：Aceleración de movimiento del eje extendido 485
    - ``dec``：Desaceleración de movimiento del eje extendido 485"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la aceleración y desaceleración de parada de emergencia del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetEmergencyStopAcc(acc, dec)``"
    "Descripción", "Establecer la aceleración y desaceleración de parada de emergencia del eje extendido 485"
    "Parámetros obligatorios", "- ``acc``：Aceleración de parada de emergencia del eje extendido 485
    - ``dec``：Desaceleración de parada de emergencia del eje extendido 485"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener la aceleración y desaceleración de movimiento del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoGetAcc()``"
    "Descripción", "Obtener la aceleración y desaceleración de movimiento del eje extendido 485"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``acc``：Aceleración de movimiento del eje extendido 485
    - ``dec``：Desaceleración de movimiento del eje extendido 485"

Obtener la aceleración y desaceleración de parada de emergencia del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoGetEmergencyStopAcc()``"
    "Descripción", "Obtener la aceleración y desaceleración de parada de emergencia del eje extendido 485"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``acc``：Aceleración de parada de emergencia del eje extendido 485
    - ``dec``：Desaceleración de parada de emergencia del eje extendido 485"

Ejemplo de código de control del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45)
    print(f"AuxServoSetParam is: {retval}")
    servoCompany = 0
    servoModel = 0
    servoSoftVersion = 0
    servoResolution = 0
    axisMechTransRatio = 0.0
    retval, servoCompany, servoModel, servoSoftVersion, servoResolution, axisMechTransRatio = robot.AuxServoGetParam(1)
    print(f"servoCompany {servoCompany}\n"
          f"servoModel {servoModel}\n"
          f"servoSoftVersion {servoSoftVersion}\n"
          f"servoResolution {servoResolution}\n"
          f"axisMechTransRatio {axisMechTransRatio}\n")
    retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14)
    print(f"AuxServoSetParam is: {retval}")
    retval, servoCompany, servoModel, servoSoftVersion, servoResolution, axisMechTransRatio = robot.AuxServoGetParam(1)
    print(f"servoCompany {servoCompany}\n"
          f"servoModel {servoModel}\n"
          f"servoSoftVersion {servoSoftVersion}\n"
          f"servoResolution {servoResolution}\n"
          f"axisMechTransRatio {axisMechTransRatio}\n")
    retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36)
    print(f"AuxServoSetParam is: {retval}")
    time.sleep(3)
    robot.AuxServoSetAcc(3000, 3000)
    robot.AuxServoSetEmergencyStopAcc(5000, 5000)
    time.sleep(1)
    emagacc = 0.0
    emagdec = 0.0
    acc = 0.0
    dec = 0.0
    error,emagacc, emagdec = robot.AuxServoGetEmergencyStopAcc()
    print(f"emergency acc is {emagacc}  dec is {emagdec}")
    error,acc, dec = robot.AuxServoGetAcc()
    print(f"acc is {acc}  dec is {dec}")
    robot.AuxServoSetControlMode(1, 0)
    time.sleep(2)
    retval = robot.AuxServoEnable(1, 0)
    print(f"AuxServoEnable disenable {retval}")
    time.sleep(1)
    servoErrCode = 0
    servoState = 0
    servoPos = 0.0
    servoSpeed = 0.0
    servoTorque = 0.0
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoState {servoState}")
    time.sleep(1)
    retval = robot.AuxServoEnable(1, 1)
    print(f"AuxServoEnable enable {retval}")
    time.sleep(1)
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoState {servoState}")
    time.sleep(1)
    retval = robot.AuxServoHoming(1, 1, 5, 1,100)
    print(f"AuxServoHoming {retval}")
    time.sleep(3)
    retval = robot.AuxServoSetTargetPos(1, 200, 30,100)
    print(f"AuxServoSetTargetPos {retval}")
    time.sleep(1)
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoSpeed {servoSpeed}")
    time.sleep(8)
    robot.AuxServoSetControlMode(1, 1)
    time.sleep(2)
    robot.AuxServoEnable(1, 0)
    time.sleep(1)
    robot.AuxServoEnable(1, 1)
    time.sleep(1)
    robot.AuxServoSetTargetSpeed(1, 100, 80)
    time.sleep(5)
    robot.AuxServoSetTargetSpeed(1, 0, 80)
    robot.CloseRPC()

Configuración de los parámetros de comunicación del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevSetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum, selfConnect)``"
    "Descripción", "Configuración de los parámetros de comunicación del eje extendido UDP"
    "Parámetros obligatorios", "
    - ``ip``：Dirección IP del PLC;
    - ``port``：Número de puerto;
    - ``period``：Período de comunicación (ms, aún no disponible);
    - ``lossPkgTime``：Tiempo de detección de pérdida de paquetes (ms);
    - ``lossPkgNum``：Número de pérdidas de paquetes;
    - ``disconnectTime``：Duración de confirmación de desconexión de comunicación;
    - ``reconnectEnable``：Habilitación de reconexión automática tras desconexión de comunicación 0-no habilitar 1-habilitar;
    - ``reconnectPeriod``：Intervalo del período de reconexión (ms);
    - ``reconnectNum``：Número de reconexiones
    - ``selfConnect``：Si se establece automáticamente la conexión tras reinicio por corte de energía; 0-no establecer conexión; 1-establecer conexión"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener los parámetros de comunicación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevGetUDPComParam()``"
    "Descripción", "Obtener los parámetros de comunicación del eje extendido UDP"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "
    - Código de error éxito-0  fallo- errcode;
    - ``ip``：Dirección IP del PLC;
    - ``port``：Número de puerto;
    - ``period``：Período de comunicación (ms, aún no disponible);
    - ``lossPkgTime``：Tiempo de detección de pérdida de paquetes (ms);
    - ``lossPkgNum``：Número de pérdidas de paquetes;
    - ``disconnectTime``：Duración de confirmación de desconexión de comunicación;
    - ``reconnectEnable``：Habilitación de reconexión automática tras desconexión de comunicación 0-no habilitar 1-habilitar;
    - ``reconnectPeriod``：Intervalo del período de reconexión (ms);
    - ``reconnectNum``：Número de reconexiones
    - ``selfConnect``：Si se reconecta automáticamente tras reiniciar la caja de control; 0-no reconectar; 1-reconectar"
 
Cargar la comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevLoadUDPDriver()``"
    "Descripción", "Cargar la comunicación UDP"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Descargar la comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevUnloadUDPDriver()``"
    "Descripción", "Descargar la comunicación UDP"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Restablecer la conexión tras una desconexión anómala de la comunicación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevUDPClientComReset()``"
    "Descripción", "Restablecer la conexión tras una desconexión anómala de la comunicación del eje extendido UDP"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Cerrar la comunicación tras una desconexión anómala de la comunicación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevUDPClientComClose()``"
    "Descripción", "Cerrar la comunicación tras una desconexión anómala de la comunicación del eje extendido UDP"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Configuración de los parámetros del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisParamConfig(axisId, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc,axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType)``"
    "Descripción", "Configuración de los parámetros del eje extendido UDP"
    "Parámetros obligatorios", "
    - ``axisId``：Número de eje [1-4];
    - ``axisType``：Tipo de eje extendido 0-traslación; 1-rotación;
    - ``axisDirection``：Dirección del eje extendido 0-positiva; 1-negativa;
    - ``axisMax``：Posición máxima del eje extendido mm;
    - ``axisMin``：Posición mínima del eje extendido mm;
    - ``axisVel``：Velocidad mm/s;
    - ``axisAcc``：Aceleración mm/s2;
    - ``axisLead``：Paso mm;
    - ``encResolution``：Resolución del codificador;
    - ``axisOffect``：Desplazamiento del eje extendido en el punto inicial de la soldadura;
    - ``axisCompany``：Fabricante del accionamiento 1-Huichuan; 2-Inovance; 3-Panasonic;
    - ``axisModel``：Modelo del accionamiento 1-Huichuan-SV-XD3EA040L-E, 2-Huichuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG;
    - ``axisEncType``：Tipo de codificador 0-incremental; 1-absoluto;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtención de los parámetros del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisGetParamConfig(self, axisID)``"
    "Descripción", "Obtención de los parámetros del eje extendido UDP"
    "Parámetros obligatorios", "
    - ``axisID``：Número de eje extendido [1-4]
    - ``axisType``：Tipo de eje extendido 0-traslación; 1-rotación
    - ``axisDirection``：Dirección del eje extendido 0-positiva; 1-negativa
    - ``axisMax``：Posición máxima del eje extendido mm
    - ``axisMin``：Posición mínima del eje extendido mm
    - ``axisVel``：Velocidad mm/s
    - ``axisAcc``：Aceleración mm/s2
    - ``axisLead``：Paso mm
    - ``encResolution``：Resolución del codificador
    - ``axisOffect``：Desplazamiento del eje extendido en el punto inicial de la soldadura
    - ``axisCompany``：Fabricante del accionamiento 1-Huichuan; 2-Inovance; 3-Panasonic
    - ``axisModel``：Modelo del accionamiento 1-Huichuan-SV-XD3EA040L-E, 2-Huichuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    - ``axisEncType``：Tipo de codificador 0-incremental; 1-absoluto
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la posición relativa del robot extendido respecto al eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotPosToAxis(installType)``"
    "Descripción", "Establecer la posición relativa del robot extendido respecto al eje extendido"
    "Parámetros obligatorios", "- ``installType``：0-robot instalado sobre el eje externo, 1-robot instalado fuera del eje externo;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la configuración de los parámetros DH del sistema del eje extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxisDHParaConfig(axisConfig,axisDHd1,axisDHd2,axisDHd3,axisDHd4,axisDHa1, axisDHa2,axisDHa3,axisDHa4)``"
    "Descripción", "Establecer la configuración de los parámetros DH del sistema del eje extendido"
    "Parámetros obligatorios", "
    - ``axisConfig``：Configuración del eje externo, 0-guía lineal de un solo grado de libertad, 1-posicionador tipo L de dos grados de libertad, 2-tres grados de libertad, 3-cuatro grados de libertad, 4-posicionador de un solo grado de libertad;
    - ``axisDHd1``：Parámetro DH d1 del eje externo mm;
    - ``axisDHd2``：Parámetro DH d2 del eje externo mm;
    - ``axisDHd3``：Parámetro DH d3 del eje externo mm;
    - ``axisDHd4``：Parámetro DH d4 del eje externo mm;
    - ``axisDHa1``：Parámetro DH a1 del eje externo mm;
    - ``axisDHa2``：Parámetro DH a2 del eje externo mm;
    - ``axisDHa3``：Parámetro DH a3 del eje externo mm;
    - ``axisDHa4``：Parámetro DH a4 del eje externo mm;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
                          
Habilitación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisServoOn(axisID, status)``"
    "Descripción", "Habilitación del eje extendido UDP"
    "Parámetros obligatorios", "- ``axisID``：Número de eje [1-4];
    - ``status``：0-deshabilitar; 1-habilitar;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Retorno a cero del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisSetHoming(axisID, mode, searchVel, latchVel)``"
    "Descripción", "Retorno a cero del eje extendido UDP"
    "Parámetros obligatorios", "
    - ``axisID``：Número de eje [1-4];
    - ``mode``：Modo de retorno a cero 0 retorno a cero en la posición actual, 1 retorno a cero en el límite negativo, 2-retorno a cero en el límite positivo;
    - ``searchVel``：Velocidad de búsqueda de cero (mm/s);
    - ``latchVel``：Velocidad de enganche de búsqueda de cero (mm/s);"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Inicio del jog del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisStartJog( axisID, direction, vel, acc, maxDistance)``"
    "Descripción", "Inicio del jog del eje extendido UDP"
    "Parámetros obligatorios", "
    - ``axisID``：Número de eje [1-4];
    - ``direction``：Dirección de giro 0-inversa; 1-positiva;
    - ``vel``：Velocidad (mm/s);
    - ``acc``：Aceleración (mm/s);
    - ``maxDistance``：Distancia máxima de jog;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Parada del jog del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisStopJog(axisID)``"
    "Descripción", "Parada del jog del eje extendido UDP"
    "Parámetros obligatorios", "- ``axisID``：Número de eje [1-4];"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de configuración y jog del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    from fairino.Robot import RobotState
    import time

    def main():
        # Añadir los datos de estado en tiempo real que se desean obtener (si es necesario)
        # rtn = AddRobotRealtimeState([RobotState.ExaxisCoordID])
        # if rtn != 0:
        #     print(f"✗ Error al añadir el campo, código de error: {rtn}")
        #     return None
        # print("✓ Campo añadido correctamente")

        # Establecer comunicación con el controlador del robot
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        # Configurar los parámetros de comunicación UDP
        rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1)
        print(f"ExtDevSetUDPComParam rtn is {rtn}")

        # Obtener los parámetros de comunicación UDP
        error, param = robot.ExtDevGetUDPComParam()
        print("ExtDevGetUDPComParam return ", error)
        print("Parámetros de comunicación del eje extendido UDP: ", param)

        # Cargar el controlador UDP
        robot.ExtDevLoadUDPDriver()

        # Establecer el tiempo de finalización del comando del eje extendido
        rtn = robot.SetExAxisCmdDoneTime(5000.0)
        print(f"SetExAxisCmdDoneTime rtn is {rtn}")

        # Habilitar el servo del eje extendido
        rtn = robot.ExtAxisServoOn(1, 1)
        print(f"ExtAxisServoOn axis id 1 rtn is {rtn}")
        rtn = robot.ExtAxisServoOn(2, 1)
        print(f"ExtAxisServoOn axis id 2 rtn is {rtn}")
        time.sleep(2)

        # Retorno a cero del eje extendido
        robot.ExtAxisSetHoming(1, 0, 10, 2)
        time.sleep(2)
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
        print(f"ExtAxisSetHoming rtn is {rtn}")

        time.sleep(4)

        # Establecer la posición relativa del robot respecto al eje extendido
        rtn = robot.SetRobotPosToAxis(1)
        print(f"SetRobotPosToAxis rtn is {rtn}")

        # Establecer la configuración de los parámetros DH del eje extendido
        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0)
        print(f"SetAxisDHParaConfig rtn is {rtn}")

        # Configurar los parámetros del eje extendido 1
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0)
        print(f"ExtAxisParamConfig axis 1 rtn is {rtn}")

        # Obtener la configuración de los parámetros del eje extendido 1
        rtn, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType = robot.ExtAxisGetParamConfig(1)
        print(f"axis id 1 ExtAxisGetParamConfig : axisType {axisType}, axisDirection {axisDirection}, axisMax {axisMax}, axisMin {axisMin}, axisVel {axisVel}, axisAcc {axisAcc}, axisLead {axisLead}, encResolution {encResolution}, axisOffect {axisOffect}, axisCompany {axisCompany}, axisModel {axisModel}, axisEncType {axisEncType}")

        # Configurar los parámetros del eje extendido 2
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0)
        print(f"ExtAxisParamConfig axis 2 rtn is {rtn}")

        # Obtener la configuración de los parámetros del eje extendido 2
        rtn, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType = robot.ExtAxisGetParamConfig(2)
        print(f"axis id 2 ExtAxisGetParamConfig : axisType {axisType}, axisDirection {axisDirection}, axisMax {axisMax}, axisMin {axisMin}, axisVel {axisVel}, axisAcc {axisAcc}, axisLead {axisLead}, encResolution {encResolution}, axisOffect {axisOffect}, axisCompany {axisCompany}, axisModel {axisModel}, axisEncType {axisEncType}")

        time.sleep(3)

        # Prueba de jog del eje extendido 1
        robot.ExtAxisStartJog(1, 0, 10, 10, 30)
        time.sleep(1)
        robot.ExtAxisStopJog(1)
        time.sleep(3)
        robot.ExtAxisServoOn(1, 0)

        time.sleep(3)

        # Prueba de jog del eje extendido 2
        robot.ExtAxisStartJog(2, 0, 10, 10, 30)
        time.sleep(1)
        robot.ExtAxisStopJog(2)
        time.sleep(3)
        robot.ExtAxisServoOn(2, 0)

        # Descargar el controlador UDP
        robot.ExtDevUnloadUDPDriver()

        # Cerrar la conexión
        robot.CloseRPC()


    # Llamar a la función de prueba
    main()

Establecer el punto de referencia del sistema de coordenadas del eje extendido - método de cuatro puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisSetRefPoint(pointNum)``"
    "Descripción", "Establecer el punto de referencia del sistema de coordenadas del eje extendido - método de cuatro puntos"
    "Parámetros obligatorios", "- ``pointNum``：Número de punto [1-4];"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
        
Calcular el sistema de coordenadas del eje extendido - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisComputeECoordSys()``"
    "Descripción", "Calcular el sistema de coordenadas del eje extendido - método de cuatro puntos"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode;
    - ``coord``：Valor del sistema de coordenadas del eje extendido [x,y,z,rx,ry,rz];"
                 
Configuración del punto de referencia del sistema de coordenadas del posicionador - método de cuatro puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PositionorSetRefPoint(pointNum)``"
    "Descripción", "Configuración del punto de referencia del sistema de coordenadas del posicionador - método de cuatro puntos"
    "Parámetros obligatorios", "- ``pointNum``：Número de punto [1-4];"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Cálculo del sistema de coordenadas del posicionador - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PositionorComputeECoordSys()``"
    "Descripción", "Cálculo del sistema de coordenadas del posicionador - método de cuatro puntos"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode;
    - ``coord``：Valor del sistema de coordenadas del posicionador [x,y,z,rx,ry,rz];"
             
Establecer la pose del punto de referencia de calibración en el sistema de coordenadas del extremo del posicionador
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRefPointInExAxisEnd(pos)``"
    "Descripción", "Establecer la pose del punto de referencia de calibración en el sistema de coordenadas del extremo del posicionador"
    "Parámetros obligatorios", "- ``pos``：Valor de la pose [x,y,z,rx,ry,rz];"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Aplicar el sistema de coordenadas del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisActiveECoordSys(applyAxisId,axisCoordNum,coord,calibFlag)``"
    "Descripción", "Aplicar el sistema de coordenadas del eje extendido"
    "Parámetros obligatorios", "
    - ``applyAxisId``:Número de eje extendido bit0-bit3 corresponden a los números de eje extendido 1-4, por ejemplo, para aplicar los ejes extendidos 1 y 3, sería 0b 0000 0101, es decir, 5;
    - ``axisCoordNum``：Número del sistema de coordenadas del eje extendido;
    - ``coord``：Valor del sistema de coordenadas [x,y,z,rx,ry,rz];
    - ``calibFlag``：Indicador de calibración 0-no, 1-sí;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el sistema de coordenadas del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisGetCoord()``"
    "Descripción", "Obtener el sistema de coordenadas del eje extendido"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``coord``：Sistema de coordenadas del eje extendido"

Ejemplo de código de calibración del sistema de coordenadas del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1)
    print(f"ExtDevSetUDPComParam rtn is {rtn}")
    rtn,udp_params = robot.ExtDevGetUDPComParam()
    ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum = udp_params
    patam = (
        f"\nip {ip}\nport {port}\nperiod {period}\nlossPkgTime {lossPkgTime}\n"
        f"lossPkgNum {lossPkgNum}\ndisConntime {disconnectTime}\nreconnecable {reconnectEnable}\n"
        f"reconnperiod {reconnectPeriod}\nreconnnun {reconnectNum}"
    )
    print(f"ExtDevGetUDPComParam rtn is {rtn}{patam}")
    robot.ExtDevLoadUDPDriver()
    rtn = robot.ExtAxisServoOn(1, 1)
    print(f"ExtAxisServoOn axis id 1 rtn is {rtn}")
    rtn = robot.ExtAxisServoOn(2, 1)
    print(f"ExtAxisServoOn axis id 2 rtn is {rtn}")
    time.sleep(2)
    robot.ExtAxisSetHoming(1, 0, 10, 2)
    time.sleep(2)
    rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
    print(f"ExtAxisSetHoming rtn is {rtn}")
    time.sleep(4)
    rtn = robot.SetRobotPosToAxis(1)
    print(f"SetRobotPosToAxis rtn is {rtn}")
    rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4, 0, 0, 0, 0, 0, 0)
    print(f"SetAxisDHParaConfig rtn is {rtn}")
    rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig axis 1 rtn is {rtn}")
    rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig axis 2 rtn is {rtn}")
    toolCoord = [0, 0, 210, 0, 0, 0]
    robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0)
    jSafe = [115.193, -96.149, 92.489, -87.068, -89.15, -83.488]
    j1 = [117.559, -92.624, 100.329, -96.909, -94.057, -83.488]
    j2 = [112.239, -90.096, 99.282, -95.909, -89.824, -83.488]
    j3 = [110.839, -83.473, 93.166, -89.22, -90.499, -83.487]
    j4 = [107.935, -83.572, 95.424, -92.873, -87.933, -83.488]
    descSafe = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc1 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc2 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc3 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc4 = [0.0,0.0,0.0,0.0,0.0,0.0]
    exaxisPos = [0.0,0.0,0.0,0.0]
    offdese = [0.0,0.0,0.0,0.0,0.0,0.0]
    error, descSafe = robot.GetForwardKin(jSafe)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    time.sleep(2)
    error, desc1 = robot.GetForwardKin(j1)
    robot.MoveJ(joint_pos=j1,tool= 1,user= 0,vel= 100)
    time.sleep(2)
    actualTCPPos = [0.0,0.0,0.0,0.0,0.0,0.0]
    error, actualTCPPos = robot.GetActualTCPPose(0)
    robot.SetRefPointInExAxisEnd(actualTCPPos)
    rtn = robot.PositionorSetRefPoint(1)
    print(f"PositionorSetRefPoint 1 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc2 = robot.GetForwardKin(j2)
    rtn = robot.MoveJ(joint_pos=j2,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(2)
    print(f"PositionorSetRefPoint 2 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc3 = robot.GetForwardKin(j3)
    robot.MoveJ(joint_pos=j3,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(3)
    print(f"PositionorSetRefPoint 3 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc4 = robot.GetForwardKin(j4)
    robot.MoveJ(joint_pos=j4,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(4)
    print(f"PositionorSetRefPoint 4 rtn is {rtn}")
    time.sleep(2)
    axisCoord = [0.0,0.0,0.0,0.0,0.0,0.0]
    error,axisCoord = robot.PositionorComputeECoordSys()
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    print(f"PositionorComputeECoordSys rtn is {axisCoord[0]} {axisCoord[1]} {axisCoord[2]} {axisCoord[3]} {axisCoord[4]} {axisCoord[5]}")
    rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1)
    print(f"ExtAxisActiveECoordSys rtn is {rtn}")
    robot.CloseRPC()
          
Movimiento del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisMove(pos,ovl,blend=-1)``"
    "Descripción", "Movimiento del eje extendido UDP"
    "Parámetros obligatorios", "- ``pos=[exaxis[0],exaxis[1],exaxis[2],exaxis[3]]``：Posición objetivo, posición del eje 1~posición del eje 4;
    - ``ovl``：Porcentaje de velocidad"
    "Parámetros predeterminados", "- ``blend``：Parámetro de suavizado (mm o ms), -1, esperar a que finalice el movimiento, valor predeterminado -1"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
                                        
Ejemplo de código de movimiento del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    axisPos = [20,0,0,0]
    robot.ExtAxisMove(axisPos, 50, -1)
    robot.CloseRPC()
    return 0

Movimiento sincronizado del eje extendido UDP con el movimiento de las articulaciones del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisSyncMoveJ(joint_pos,tool,user,exaxis_pos, desc_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel=20.0, acc=0.0, ovl= 100.0,  blendT=-1.0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0])``"
    "Descripción", "Movimiento sincronizado del eje extendido UDP con el movimiento de las articulaciones del robot"
    "Parámetros obligatorios", "
    - ``joint_pos``：Posición objetivo de las articulaciones, unidad [°];
    - ``desc_pos``：Pose cartesiana objetivo, unidad [mm][°]
    - ``tool``：Número de herramienta, [0~14]
    - ``user``：Número de pieza, [0~14]
    - ``exaxis_pos``：Posición del eje externo 1 ~ posición del eje externo 4"
    "Parámetros predeterminados", "
    - ``desc_pos``:Pose cartesiana objetivo, unidad [mm][°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática directa;
    - ``vel``： Porcentaje de velocidad, [0~100]; valor predeterminado 20.0;
    - ``acc``：Porcentaje de aceleración, [0~100]; aún no disponible, valor predeterminado 0.0;
    - ``ovl``：Factor de escala de velocidad, [0~100]; valor predeterminado 100.0;
    - ``blendT``：[-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad [ms]; valor predeterminado -1.0;
    - ``offset_flag``：[0]-sin desplazamiento, [1]-desplazamiento en el sistema de coordenadas de pieza/base, [2]-desplazamiento en el sistema de coordenadas de herramienta; valor predeterminado 0;
    - ``offset_pos``：Cantidad de desplazamiento de la pose, unidad [mm][°]; valor predeterminado [0.0,0.0,0.0,0.0,0.0,0.0];"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode;"
                                        
Ejemplo de código de movimiento sincronizado del eje extendido UDP con el movimiento de las articulaciones del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    # Establecer los parámetros de comunicación UDP y cargar
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Establecer los parámetros del eje extendido
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Habilitar y poner a cero el eje extendido
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Calibración del sistema de coordenadas del eje extendido
    pos = []  # Introduzca aquí las coordenadas del punto de calibración
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Esta operación debe repetirse 4 veces (con 4 puntos)
    error,coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Punto inicial y final del movimiento sincronizado
    startdescPose = []  # Introduzca las coordenadas específicas
    startjointPos = []  # Introduzca las coordenadas específicas
    startexaxisPos = []  # Introduzca las coordenadas específicas
    enddescPose = []  # Introduzca las coordenadas específicas
    endjointPos = []  # Introduzca las coordenadas específicas
    endexaxisPos = []  # Introduzca las coordenadas específicas
    # Moverse al punto inicial
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos,tool= 1,user= 1,vel= 100,acc= 100,ovl= 100,exaxis_pos= startexaxisPos,blendT= 0,offset_flag= 0,offset_pos= offdese)
    robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, endexaxisPos, 100, 100, 100, -1, 0, offdese)
    robot.CloseRPC()
                  
Movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisSyncMoveL(desc_pos, tool, user, exaxis_pos, joint_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel=20.0, acc=0.0, ovl=100.0, blendR=-1.0, search=0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],config=-1)``"
    "Descripción", "Movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot"
    "Parámetros obligatorios", "
    - ``desc_pos``：Pose cartesiana objetivo, unidad [mm][°];
    - ``tool``：Número de herramienta, [0~14];
    - ``user``：Número de pieza, [0~14];
    - ``exaxis_pos``：Posición del eje externo 1 ~ posición del eje externo 4;"
    "Parámetros predeterminados", "
    - ``joint_pos``:Posición objetivo de las articulaciones, unidad [°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática inversa;
    - ``vel``： Porcentaje de velocidad, [0~100]; valor predeterminado 20.0;
    - ``acc``：Porcentaje de aceleración, [0~100]; aún no disponible, valor predeterminado 0.0;
    - ``ovl``：Factor de escala de velocidad, [0~100]; valor predeterminado 100.0;
    - ``blendR``：[-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad [ms]; valor predeterminado -1.0;
    - ``search``：[0]-sin búsqueda de posición de alambre de soldadura, [1]-búsqueda de posición de alambre de soldadura;
    - ``offset_flag``：[0]-sin desplazamiento, [1]-desplazamiento en el sistema de coordenadas de pieza/base, [2]-desplazamiento en el sistema de coordenadas de herramienta; valor predeterminado 0;
    - ``offset_pos``：Cantidad de desplazamiento de la pose, unidad [mm][°]; valor predeterminado [0.0,0.0,0.0,0.0,0.0,0.0];
    - ``config``:Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones, valor predeterminado -1"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode;"
                                            
Ejemplo de código de movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    # Establecer los parámetros de comunicación UDP y cargar
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Establecer los parámetros del eje extendido
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Habilitar y poner a cero el eje extendido
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Calibración del sistema de coordenadas del eje extendido
    pos = []  # Introduzca las coordenadas del punto de calibración
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Debe llamarse 4 veces para la calibración
    error,coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Punto inicial y final del movimiento sincronizado
    startdescPose = []  # Introduzca las coordenadas
    startjointPos = []  # Introduzca las coordenadas
    startexaxisPos = []  # Introduzca las coordenadas
    enddescPose = []  # Introduzca las coordenadas
    endjointPos = []  # Introduzca las coordenadas
    endexaxisPos = []  # Introduzca las coordenadas
    # Moverse al punto inicial
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos, tool= 1,user= 1,vel= 100,acc= 100,ovl= 100,exaxis_pos= startexaxisPos,blendT= 0)
    # Ejecutar el movimiento lineal sincronizado
    robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, endexaxisPos, 100, 100, 100, 0, 0, offdese)
    robot.CloseRPC()
                      
Movimiento sincronizado del eje extendido UDP con el movimiento circular del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisSyncMoveC(desc_pos_p, tool_p, user_p,exaxis_pos_p, desc_pos_t, tool_t, user_t,exaxis_pos_t,joint_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], joint_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],vel_p=20.0, acc_p=100.0, offset_flag_p=0, offset_pos_p =[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel_t=20.0, acc_t=100.0, offset_flag_t=0, offset_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], ovl=100.0, blendR=-1.0, config=-1)``"
    "Descripción", " Movimiento sincronizado del eje extendido UDP con el movimiento circular del robot"
    "Parámetros obligatorios", "
    - ``desc_pos_p``：Pose cartesiana del punto de trayectoria, unidad [mm][°];
    - ``tool_p``：Número de herramienta del punto de trayectoria, [0~14];
    - ``user_p``：Número de pieza del punto de trayectoria, [0~14];
    - ``exaxis_pos_p``：Posición del eje externo 1 ~ posición del eje externo 4 del punto de trayectoria; valor predeterminado [0.0,0.0,0.0,0.0];
    - ``desc_pos_t``：Pose cartesiana del punto objetivo, unidad [mm][°];
    - ``tool_t``：Número de herramienta, [0~14];
    - ``user_t``：Número de pieza, [0~14];
    - ``exaxis_pos_t``：Posición del eje externo 1 ~ posición del eje externo 4 del punto objetivo; valor predeterminado [0.0,0.0,0.0,0.0];"
    "Parámetros predeterminados", "
    - ``joint_pos_p``:Posición objetivo de las articulaciones, unidad [°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática inversa;
    - ``joint_pos_t``:Posición objetivo de las articulaciones, unidad [°]; valor inicial predeterminado [0.0,0.0,0.0,0.0,0.0,0.0], el valor predeterminado utiliza el valor de retorno de la solución de cinemática inversa;
    - ``vel_p``: Porcentaje de velocidad del punto de trayectoria, [0~100]; valor predeterminado 20.0;
    - ``acc_p``: Porcentaje de aceleración del punto de trayectoria, [0~100]; aún no disponible, valor predeterminado 0.0;
    - ``offset_flag_p``: Si el punto de trayectoria está desplazado[0]-sin desplazamiento, [1]-desplazamiento en el sistema de coordenadas de pieza/base, [2]-desplazamiento en el sistema de coordenadas de herramienta; valor predeterminado 0;
    - ``offset_pos_p``: Cantidad de desplazamiento de la pose del punto de trayectoria, unidad [mm][°]; valor predeterminado [0.0,0.0,0.0,0.0,0.0,0.0];
    - ``vel_t``: Porcentaje de velocidad del punto objetivo, [0~100]; valor predeterminado 20.0;
    - ``acc_t``: Porcentaje de aceleración del punto objetivo, [0~100]; aún no disponible; valor predeterminado 0.0;
    - ``offset_flag_t``: Si el punto objetivo está desplazado[0]-sin desplazamiento, [1]-desplazamiento en el sistema de coordenadas de pieza/base, [2]-desplazamiento en el sistema de coordenadas de herramienta; valor predeterminado 0;
    - ``offset_pos_t``: Cantidad de desplazamiento de la pose del punto objetivo, unidad [mm][°]; valor predeterminado [0.0,0.0,0.0,0.0,0.0,0.0];
    - ``ovl``: Factor de escala de velocidad, [0~100]; valor predeterminado 100.0;
    - ``blendR``：[-1.0]-movimiento en posición (bloqueante), [0~1000]-radio de suavizado (no bloqueante), unidad [mm]; valor predeterminado -1.0;
    - ``config``:Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones, valor predeterminado -1"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode;"
                                                
Ejemplo de código de movimiento sincronizado del eje extendido UDP con el movimiento circular del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    # Establecer los parámetros de comunicación UDP y cargar
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Establecer los parámetros del eje extendido
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Habilitar y poner a cero el eje extendido
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Calibración del sistema de coordenadas del eje extendido
    pos = []  # Introduzca las coordenadas del punto de calibración
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Llamar 4 veces para completar la calibración
    coord = []
    error,coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Punto inicial, intermedio y final del arco sincronizado
    startdescPose = []# Introduzca las coordenadas
    startjointPos = []# Introduzca las coordenadas
    startexaxisPos =[]  # Introduzca las coordenadas del eje extendido
    middescPose = []# Introduzca el punto intermedio
    midjointPos = []
    midexaxisPos =[]
    enddescPose = []
    endjointPos = []
    endexaxisPos =[]
    # Moverse al punto inicial
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos,tool= 1,user= 1,vel= 100,acc= 100,ovl= 100,exaxis_pos= startexaxisPos,blendT= 0,offset_flag= 0,offset_pos= offdese)
    # Iniciar el movimiento circular sincronizado
    robot.ExtAxisSyncMoveC(midjointPos,middescPose,1,1,midexaxisPos,
                           endjointPos,enddescPose,1,1,endexaxisPos,
                           100,100,0,offdese,
                           100,100,0,offdese,
                           100,0)
    robot.CloseRPC()

Establecer DO extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAuxDO(DONum,bOpen,smooth,block)``"
    "Descripción", "Establecer DO extendida"
    "Parámetros obligatorios", "
    - ``DONum``： Número de DO;
    - ``bOpen``：Interruptor True-abrir,False-cerrar;
    - ``smooth``：Si se suaviza True -sí, False -no;
    - ``block``：Si es bloqueante True -sí, False -no;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer AO extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAuxAO(AONum,value,block)``"
    "Descripción", "Establecer AO extendida"
    "Parámetros obligatorios", "
    - ``AONum``： Número de AO;
    - ``value``：Valor analógico [0-4095];
    - ``block``：Si es bloqueante True -sí, False -no;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
        
Establecer el tiempo de filtrado de entrada DI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAuxDIFilterTime(filterTime)``"
    "Descripción", "Establecer el tiempo de filtrado de entrada DI extendida"
    "Parámetros obligatorios", "- ``filterTime``： Tiempo de filtrado (ms);"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
        
Establecer el tiempo de filtrado de entrada AI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAuxAIFilterTime(AINum,filterTime)``"
    "Descripción", "Establecer el tiempo de filtrado de entrada AI extendida"
    "Parámetros obligatorios", "
    - ``AINum``： Número de AI;
    - ``filterTime``： Tiempo de filtrado (ms);"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
        
Esperar la entrada DI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitAuxDI(DINum,bOpen,time,errorAlarm)``"
    "Descripción", "Esperar la entrada DI extendida"
    "Parámetros obligatorios", "
    - ``DINum``： Número de DI;
    - ``bOpen``：Interruptor True-abrir,False-cerrar;
    - ``time``：Tiempo máximo de espera (ms);
    - ``errorAlarm``：Si se continúa el movimiento True-sí,False-no"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
        
Esperar la entrada AI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitAuxAI(,AINum,sign,value,time,errorAlarm)``"
    "Descripción", "Esperar la entrada AI extendida"
    "Parámetros obligatorios", "
    - ``AINum``： Número de AI;
    - ``sign``：0-mayor que; 1-menor que;
    - ``value``：Valor de AI;
    - ``time``：Tiempo máximo de espera (ms);
    - ``errorAlarm``：Si se continúa el movimiento True-sí,False-no"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
        
Obtener el valor de DI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAuxDI(DINum,isNoBlock)``"
    "Descripción", "Obtener el valor de DI extendida"
    "Parámetros obligatorios", "
    - ``DINum``： Número de DI;
    - ``isNoBlock``：Si es bloqueante True-bloqueante false-no bloqueante;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode;
    - ``isOpen``： 0-cerrado; 1-abierto;"
          
Obtener el valor de AI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAuxAI(AINum,isNoBlock)``"
    "Descripción", "Obtener el valor de AI extendida"
    "Parámetros obligatorios", "
    - ``AINum``： Número de AI;
    - ``isNoBlock``：Si es bloqueante True-bloqueante False-no bloqueante"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode;
    - ``value``：Valor de entrada;"

Ejemplo de código de IO extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    for i in range(128):
        robot.SetAuxDO(i, True, False, True)
        time.sleep(0.1)
    for i in range(128):
        robot.SetAuxDO(i, False, False, True)
        time.sleep(0.1)
    for i in range(409):
        value1 = i * 10
        value2 = 4095 - i * 10
        robot.SetAuxAO(0, value1, True)
        robot.SetAuxAO(1, value2, True)
        robot.SetAuxAO(2, value1, True)
        robot.SetAuxAO(3, value2, True)
        time.sleep(0.01)
    robot.SetAuxDIFilterTime(10)
    robot.SetAuxAIFilterTime(0, 10)
    for i in range(20):
        curValue = False
        error, curValue = robot.GetAuxDI(i, False)  # Nota: si la biblioteca requiere paso por referencia internamente, modificar aquí
        print(f"DI{i}   {curValue}")
    curValue = -1
    for i in range(4):
        error, curValue = robot.GetAuxAI(i, True)  # Igualmente, tener en cuenta el paso por referencia
        print(f"AI{i}   {curValue}")
    robot.WaitAuxDI(1, False, 1000, False)
    robot.WaitAuxAI(1, 1, 132, 1000, False)
    robot.CloseRPC()

Habilitación del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TractorEnable(enable)``"
    "Descripción", "Habilitación del dispositivo móvil"
    "Parámetros obligatorios", "- ``enable``：Estado de habilitación, 0-deshabilitar, 1-habilitar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Retorno a cero del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TractorHoming()``"
    "Descripción", "Retorno a cero del dispositivo móvil"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Movimiento lineal del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TractorMoveL(distance, vel)``"
    "Descripción", "Movimiento lineal del dispositivo móvil"
    "Parámetros obligatorios", "- ``distance``：Distancia del movimiento lineal (mm)
    - ``vel``：Porcentaje de velocidad del movimiento lineal (0-100)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Movimiento circular del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TractorMoveC(radio, angle, vel)``"
    "Descripción", "Movimiento circular del dispositivo móvil"
    "Parámetros obligatorios", "- ``radio``：Radio del movimiento circular (mm)
    - ``angle``：Ángulo del movimiento circular (°)
    - ``vel``：Porcentaje de velocidad del movimiento circular (0-100)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Detención del movimiento del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramStop()``"
    "Descripción", "Detención del movimiento del dispositivo móvil"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10, 1)
    robot.ExtDevLoadUDPDriver()
    rtn = robot.ExtAxisServoOn(1, 1)
    rtn = robot.ExtAxisServoOn(2, 1)
    time.sleep(2)
    robot.ExtAxisSetHoming(1, 0, 10, 2)
    time.sleep(2)
    rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
    time.sleep(4)
    robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0)
    robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0)
    robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0)
    robot.TractorEnable(False)
    time.sleep(2)
    robot.TractorEnable(True)
    time.sleep(2)
    robot.TractorHoming()
    time.sleep(2)
    robot.TractorMoveL(100, 2)
    time.sleep(5)
    robot.TractorStop()
    robot.TractorMoveL(-100, 20)
    time.sleep(5)
    robot.TractorMoveC(300, 90, 20)
    time.sleep(10)
    robot.TractorMoveC(300, -90, 20)
    time.sleep(1)
    robot.CloseRPC()

Registro de puntos del sensor láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserRecordPoint(coordID)``"
    "Descripción", "Registro de puntos del sensor láser"
    "Parámetros obligatorios", "- ``coordID``：Sistema de coordenadas del sensor láser"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``joint``：Posición de articulaciones del punto identificado por el sensor láser
    - ``desc``：Posición cartesiana del punto identificado por el sensor láser
    - ``exaxis``：Posición del eje extendido del punto identificado por el sensor láser"

Ejemplo de código de registro de puntos del sensor láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    direction_point = [0, 0, 0]
    rtn = robot.LaserTrackingSearchStart(2, direction_point, 10, 100, 10000, 2)
    print(f"LaserTrackingSearchStart rtn is {rtn}")
    robot.LaserTrackingSearchStop()
    coord_id = 2
    rtn, joint, desc, exaxis = robot.LaserRecordPoint(coord_id)
    print(f"rtn is {rtn}")
    print(f"desc_pos:{desc[0]},{desc[1]},{desc[2]},"
          f"{desc[3]},{desc[4]},{desc[5]}")
    print(f"joint_pos:{joint[0]},{joint[1]},{joint[2]},{joint[3]},{joint[4]},{joint[5]}")
    print(f"exaxis pos is {exaxis[0]} {exaxis[1]} {exaxis[2]} {exaxis[3]}")
    off = [0] * 6
    robot.MoveJ(joint,tool=1,user=0,vel=100,acc=100,ovl=50,exaxis_pos=exaxis,blendT=-1,offset_flag=0,offset_pos=off)
    robot.CloseRPC()

Establecer la estrategia de movimiento sincronizado del eje extendido y el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExAxisRobotPlan(strategy)``"
    "Descripción", "Establecer la estrategia de movimiento sincronizado del eje extendido y el robot"
    "Parámetros obligatorios", "- ``strategy``：Estrategia; 0-con el robot como referencia; 1-sincronizado entre eje extendido y robot"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de establecimiento de la estrategia de movimiento sincronizado del eje extendido y el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    joint_pos1 = [-22.016, -49.217, 124.714, -161.100, -85.108, -0.333]
    joint_pos2 = [-21.083, -46.613, 110.079, -147.796, -80.757, -0.330]
    joint_pos3 = [-25.572, -60.090, 135.397, -163.889, -82.489, -0.345]
    desc_pos1 = [2.637, -0.001, 30.673, 178.786, -4.134, 68.326]
    desc_pos2 = [213.812, -1.440, 47.311, 177.410, 0.166, 68.946]
    desc_pos3 = [444.342, -12.723, 82.470, -177.701, -1.325, 65.151]
    epos1 = [0.001, 0.000, 0.000, 0.000]
    epos2 = [299.977, 0.000, 0.000, 0.000]
    epos3 = [399.969, 0.000, 0.000, 0.000]
    offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.SetExAxisRobotPlan(0)
    print(f"SetExAxisRobotPlan rtn is {rtn}")
    time.sleep(1)
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos1,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos1,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 1 rtn is {rtn}")
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos2,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos2,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 2 rtn is {rtn}")
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos3,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos3,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 3 rtn is {rtn}")
    time.sleep(8)
    robot.CloseRPC()

Configuración del tiempo de finalización del posicionamiento del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExAxisCmdDoneTime(time)``"
    "Descripción", "Configuración del tiempo de finalización del posicionamiento del eje extendido UDP"
    "Parámetros obligatorios", "- ``time``：Tiempo de finalización del posicionamiento [ms]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"