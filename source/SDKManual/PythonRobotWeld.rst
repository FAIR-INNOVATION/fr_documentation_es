Soldadura
======================

.. toctree:: 
    :maxdepth: 5
    
Establecer los parámetros de la curva de proceso de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetProcessParam(id, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime)``"
    "Descripción", "Establecer los parámetros de la curva de proceso de soldadura"
    "Parámetros obligatorios", "
    - ``id``： número del proceso de soldadura(1-99)
    - ``startCurrent``： corriente de cebado del arco(A)
    - ``startVoltage``：startVoltage voltaje de cebado del arco(V)
    - ``startTime``：startTime tiempo de cebado del arco(ms)
    - ``weldCurrent``：weldCurrent corriente de soldadura(A)
    - ``weldVoltage``：weldVoltage voltaje de soldadura(V)
    - ``endCurrent``：endCurrent corriente de extinción del arco(A)
    - ``endVoltage``：endVoltage voltaje de extinción del arco(V)
    - ``endTime``：endTime tiempo de extinción del arco(ms)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Obtener los parámetros de la curva de proceso de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingGetProcessParam(id)``"
    "Descripción", "Obtener los parámetros de la curva de proceso de soldadura"
    "Parámetros obligatorios", "
    - ``id``： número del proceso de soldadura(1-99)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``startCurrent``：corriente de cebado del arco(A)
    - ``startVoltage``： voltaje de cebado del arco(V)
    - ``startTime``：tiempo de cebado del arco(ms)
    - ``weldCurrent``：corriente de soldadura(A)
    - ``weldVoltage``：voltaje de soldadura(V)
    - ``endCurrent``：corriente de extinción del arco(A)
    - ``endVoltage``：voltaje de extinción del arco(V)
    - ``endTime``：tiempo de extinción del arco(ms)
    " 

Establecer la relación entre la corriente de soldadura y la salida analógica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetCurrentRelation(currentMin, currentMax, outputVoltageMin, outputVoltageMax)``"
    "Descripción", "Establecer la relación entre la corriente de soldadura y la salida analógica"
    "Parámetros obligatorios", "- ``currentMin``： valor de corriente del punto izquierdo de la relación lineal corriente de soldadura-salida analógica(A)
    - ``currentMax``：  valor de corriente del punto derecho de la relación lineal corriente de soldadura-salida analógica(A)
    - ``outputVoltageMin``： valor de voltaje de salida analógica del punto izquierdo de la relación lineal corriente de soldadura-salida analógica(V)
    - ``outputVoltageMax``：valor de voltaje de salida analógica del punto derecho de la relación lineal corriente de soldadura-salida analógica(V)
    - ``AOIndex``：puerto de salida analógica de corriente de soldadura"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la relación entre el voltaje de soldadura y la salida analógica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetVoltageRelation(weldVoltageMin, weldVoltageMax, outputVoltageMin, outputVoltageMax)``"
    "Descripción", "Establecer la relación entre el voltaje de soldadura y la salida analógica"
    "Parámetros obligatorios", "- ``weldVoltageMin``： valor de voltaje de soldadura del punto izquierdo de la relación lineal voltaje de soldadura-salida analógica(A)
    - ``weldVoltageMax``：  valor de voltaje de soldadura del punto derecho de la relación lineal voltaje de soldadura-salida analógica(A)
    - ``outputVoltageMin``： valor de voltaje de salida analógica del punto izquierdo de la relación lineal voltaje de soldadura-salida analógica(V)
    - ``outputVoltageMax``：valor de voltaje de salida analógica del punto derecho de la relación lineal voltaje de soldadura-salida analógica(V)
    - ``AOIndex``：puerto de salida analógica de voltaje de soldadura"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener la relación entre la corriente de soldadura y la salida analógica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingGetCurrentRelation()``"
    "Descripción", "Obtener la relación entre la corriente de soldadura y la salida analógica"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``currentMin``：valor de corriente del punto izquierdo de la relación lineal corriente de soldadura-salida analógica(A)
    - ``currentMax``：valor de corriente del punto derecho de la relación lineal corriente de soldadura-salida analógica(A)
    - ``outputVoltageMin``：valor de voltaje de salida analógica del punto izquierdo de la relación lineal corriente de soldadura-salida analógica(V)
    - ``outputVoltageMax``：valor de voltaje de salida analógica del punto derecho de la relación lineal corriente de soldadura-salida analógica(V)
    - ``AOIndex``：puerto de salida analógica de voltaje de soldadura"

Obtener la relación entre el voltaje de soldadura y la salida analógica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingGetVoltageRelation()``"
    "Descripción", "Obtener la relación entre el voltaje de soldadura y la salida analógica"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``weldVoltageMin``: valor de voltaje de soldadura del punto izquierdo de la relación lineal voltaje de soldadura-salida analógica(V)
    - ``weldVoltageMax``: valor de voltaje de soldadura del punto derecho de la relación lineal voltaje de soldadura-salida analógica(V)
    - ``outputVoltageMin``: valor de voltaje de salida analógica del punto izquierdo de la relación lineal voltaje de soldadura-salida analógica(V)
    - ``outputVoltageMax``: valor de voltaje de salida analógica del punto derecho de la relación lineal corriente de soldadura-salida analógica(V)
    - ``AOIndex``：puerto de salida analógica de voltaje de soldadura"

Establecer la corriente de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetCurrent(ioType, current, AOIndex, blend)``"
    "Descripción", "Establecer la corriente de soldadura"
    "Parámetros obligatorios", "- ``ioType``： tipo 0-IO del controlador； 1-IO extendido
    - ``current``： valor de corriente de soldadura(A)
    - ``AOIndex``： puerto de salida analógica de la caja de control de corriente de soldadura(0-1)
    - ``blend``：si suavizar 0-no suavizar，1-suavizar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el voltaje de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetVoltage(ioType, voltage, AOIndex, blend)``"
    "Descripción", "Establecer el voltaje de soldadura"
    "Parámetros obligatorios", "- ``ioType``： tipo 0-IO del controlador； 1-IO extendido
    - ``voltage``： valor de voltaje de soldadura(V)
    - ``AOIndex``： puerto de salida analógica de la caja de control de corriente de soldadura(0-1)
    - ``blend``：si suavizar 0-no suavizar，1-suavizar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer los parámetros de oscilación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.1.2
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveSetPara(weaveNum, weaveType, weaveFrequency, weaveIncStayTime, weaveRange, weaveLeftRange, weaveRightRange, additionalStayTime, weaveLeftStayTime, weaveRightStayTime, weaveCircleRadio, weaveStationary, weaveYawAngle, weaveRotAngle)``"
    "Descripción", "Establecer los parámetros de oscilación"
    "Parámetros obligatorios", "- ``weaveNum``： número de configuración de parámetros de soldadura oscilante
    - ``weaveType``： tipo de oscilación 0-oscilación triangular plana；1-oscilación triangular en L vertical；2-oscilación circular en sentido horario；3-oscilación circular en sentido antihorario；4-oscilación sinusoidal plana；5-oscilación sinusoidal en L vertical；6-oscilación triangular vertical；7-oscilación sinusoidal vertical
    - ``weaveFrequency``： frecuencia de oscilación(Hz)
    - ``weaveIncStayTime``： modo de espera 0-el ciclo no incluye tiempo de espera；1-el ciclo incluye tiempo de espera parámetro obligatorio
    - ``weaveRange``： amplitud de oscilación(mm)
    - ``weaveLeftRange``： longitud de la cuerda izquierda de la oscilación triangular vertical(mm)
    - ``weaveRightRange``： longitud de la cuerda derecha de la oscilación triangular vertical(mm)
    - ``additionalStayTime``： tiempo de permanencia en el punto del triángulo vertical de la oscilación triangular vertical(mm)
    - ``weaveLeftStayTime``： tiempo de permanencia izquierdo de la oscilación(ms)
    - ``weaveRightStayTime``：  tiempo de permanencia derecho de la oscilación(ms)
    - ``weaveCircleRadio``： oscilación circular-proporción de retorno(0-100%)
    - ``weaveStationary``： espera en la posición de oscilación，0-la posición continúa moviéndose durante el tiempo de espera；1-la posición permanece estática durante el tiempo de espera"
    "Parámetros predeterminados", "- ``weaveYawAngle``： ángulo de orientación de la dirección de oscilación (rotación alrededor del eje Z de oscilación)，unidad°,predeterminado0
    - ``weaveRotAngle``： ángulo de orientación de la dirección de oscilación (rotación alrededor del eje X de oscilación)，unidad°,predeterminado0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código para establecer los parámetros de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.WeldingSetProcessParam(1, 177, 27, 1000, 178, 28, 176, 26, 1000)
    robot.WeldingSetProcessParam(2, 188, 28, 555, 199, 29, 133, 23, 333)
    start_current = 0
    start_voltage = 0
    start_time = 0
    weld_current = 0
    weld_voltage = 0
    end_current = 0
    end_voltage = 0
    end_time = 0
    error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(1)
    print(f"the Num 1 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")
    error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(2)
    print(f"the Num 2 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")
    rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0)
    print(f"WeldingSetCurrentRelation rtn is: {rtn}")
    rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1)
    print(f"WeldingSetVoltageRelation rtn is: {rtn}")
    current_min = 0
    current_max = 0
    vol_min = 0
    vol_max = 0
    output_vmin = 0
    output_vmax = 0
    cur_index = 0
    vol_index = 0
    rtn,current_min, current_max, output_vmin, output_vmax, cur_index = robot.WeldingGetCurrentRelation()
    print(f"WeldingGetCurrentRelation rtn is: {rtn}")
    print(f"current min {current_min} current max {current_max} output vol min {output_vmin} output vol max {output_vmax}")
    rtn,vol_min, vol_max, output_vmin, output_vmax, vol_index = robot.WeldingGetVoltageRelation()
    print(f"WeldingGetVoltageRelation rtn is: {rtn}")
    print(f"vol min {vol_min} vol max {vol_max} output vol min {output_vmin} output vol max {output_vmax}")
    rtn = robot.WeldingSetCurrent(1, 100, 0, 0)
    print(f"WeldingSetCurrent rtn is: {rtn}")
    time.sleep(3)
    rtn = robot.WeldingSetVoltage(1, 10, 0, 0)
    print(f"WeldingSetVoltage rtn is: {rtn}")
    rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0,0.0, 60.000000)
    print(f"rtn is: {rtn}")
    robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0)
    rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200)
    print(f"WeldingSetCheckArcInterruptionParam {rtn}")
    rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0)
    print(f"WeldingSetReWeldAfterBreakOffParam {rtn}")
    enable = 0
    length = 0
    velocity = 0
    move_type = 0
    check_enable = 0
    arc_interrupt_time_length = 0
    rtn,check_enable, arc_interrupt_time_length = robot.WeldingGetCheckArcInterruptionParam()
    print(f"WeldingGetCheckArcInterruptionParam checkEnable {check_enable} arcInterruptTimeLength {arc_interrupt_time_length}")
    rtn,enable, length, velocity, move_type = robot.WeldingGetReWeldAfterBreakOffParam()
    print(f"WeldingGetReWeldAfterBreakOffParam enable = {enable}, length = {length}, velocity = {velocity}, moveType = {move_type}")
    robot.SetWeldMachineCtrlModeExtDoNum(17)
    for i in range(5):
        robot.SetWeldMachineCtrlMode(0)
        time.sleep(1)
        robot.SetWeldMachineCtrlMode(1)
        time.sleep(1)
    robot.CloseRPC()

Establecer los parámetros de oscilación en tiempo real
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveOnlineSetPara (weaveNum, weaveType, weaveFrequency, weaveIncStayTime, weaveRange, weaveLeftStayTime, weaveRightStayTime, weaveCircleRadio, weaveStationary)``"
    "Descripción", "Establecer los parámetros de oscilación en tiempo real"
    "Parámetros obligatorios", "- ``weaveNum``： número de configuración de parámetros de soldadura oscilante
    - ``weaveType``： tipo de oscilación 0-oscilación triangular plana；1-oscilación triangular en L vertical；2-oscilación circular en sentido horario；3-oscilación circular en sentido antihorario；4-oscilación sinusoidal plana；5-oscilación sinusoidal en L vertical；6-oscilación triangular vertical；7-oscilación sinusoidal vertical
    - ``weaveFrequency``： frecuencia de oscilación(Hz)
    - ``weaveIncStayTime``： modo de espera 0-el ciclo no incluye tiempo de espera；1-el ciclo incluye tiempo de espera parámetro obligatorio
    - ``weaveRange``： amplitud de oscilación(mm)
    - ``weaveLeftStayTime``： tiempo de permanencia izquierdo de la oscilación(ms)
    - ``weaveRightStayTime``：  tiempo de permanencia derecho de la oscilación(ms)
    - ``weaveCircleRadio``： oscilación circular-proporción de retorno(0-100%)
    - ``weaveStationary``： espera en la posición de oscilación，0-la posición continúa moviéndose durante el tiempo de espera；1-la posición permanece estática durante el tiempo de espera"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener los parámetros de detección de interrupción accidental del arco de soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingGetCheckArcInterruptionParam()``"
    "Descripción", "Obtener los parámetros de detección de interrupción accidental del arco de soldadura del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``checkEnable``：si habilitar la detección；0-no habilitar；1-habilitar
    - ``arcInterruptTimeLength``：duración de confirmación de interrupción del arco(ms)"

Establecer los parámetros de detección de interrupción accidental del arco de soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetCheckArcInterruptionParam(checkEnable, arcInterruptTimeLength)``"
    "Descripción", "Establecer los parámetros de detección de interrupción accidental del arco de soldadura del robot"
    "Parámetros obligatorios", "- ``checkEnable``：si habilitar la detección；0-no habilitar；1-habilitar
    - ``arcInterruptTimeLength``：duración de confirmación de interrupción del arco(ms)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Obtener los parámetros de recuperación de interrupción de soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingGetReWeldAfterBreakOffParam()``"
    "Descripción", "Obtener los parámetros de recuperación de interrupción de soldadura del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``enable``：si habilitar la recuperación de interrupción de soldadura
    - ``length``：distancia de solapamiento del cordón de soldadura(mm)
    - ``velocity``：porcentaje de velocidad del robot para volver al punto de reencendido del arco(0-100)
    - ``moveType``：modo de movimiento del robot al punto de reencendido del arco；0-LIN；1-PTP"

Establecer los parámetros de recuperación de interrupción de soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetReWeldAfterBreakOffParam(enable, length, velocity, moveType)``"
    "Descripción", "Establecer los parámetros de recuperación de interrupción de soldadura del robot"
    "Parámetros obligatorios", "- ``enable``：si habilitar la recuperación de interrupción de soldadura
    - ``length``：distancia de solapamiento del cordón de soldadura(mm)
    - ``velocity``：porcentaje de velocidad del robot para volver al punto de reencendido del arco(0-100)
    - ``moveType``：modo de movimiento del robot al punto de reencendido del arco；0-LIN；1-PTP"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Establecer el puerto DO extendido del modo de control de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWeldMachineCtrlModeExtDoNum(DONum)``"
    "Descripción", "Establecer el puerto DO extendido del modo de control de la soldadora"
    "Parámetros obligatorios", "- ``DONum``：puerto DO del modo de control de la soldadora(0-127)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Establecer el modo de control de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWeldMachineCtrlMode(mode, ioType)``"
    "Descripción", "Establecer el modo de control de la soldadora"
    "Parámetros obligatorios", "
    - ``ioType``：tipo de control；0-IO de la caja de control；1-protocolo de comunicación digital(UDP);2-protocolo de comunicación digital(ModbusTCP)
    - ``mode``：modo de control de la soldadora;modo de control de la soldadora;0-modo unificado de corriente continua；1-modo unificado de pulso；2-modo JOB；3-modo de control cercano；4-modo separado；5-modo CC/CV；6-TIG；7-CMT,8-Panasonic-con modo de pulso，9-Panasonic-sin modo de pulso"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Obtener el modo de control de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWeldMachineCtrlMode(self)``"
    "Descripción", "Obtener el modo de control de la soldadora"
    "Parámetros obligatorios", "
    - ``mode``：mode modo de control de la soldadora;0-modo unificado de corriente continua；1-modo unificado de pulso；2-modo JOB；3-modo de control cercano；4-modo separado；5-modo CC/CV；6-TIG；7-CMT
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Ejemplo de código para obtener el modo de control de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v3.9.8

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        robot.WeldingSetProcessParam(1, 177, 27, 1000, 178, 28, 176, 26, 1000)
        robot.WeldingSetProcessParam(2, 188, 28, 555, 199, 29, 133, 23, 333)

        start_current = 0
        start_voltage = 0
        start_time = 0
        weld_current = 0
        weld_voltage = 0
        end_current = 0
        end_voltage = 0
        end_time = 0

        error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(1)
        print(f"the Num 1 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")

        error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(2)
        print(f"the Num 2 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")

        rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0)
        print(f"WeldingSetCurrentRelation rtn is: {rtn}")

        rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1)
        print(f"WeldingSetVoltageRelation rtn is: {rtn}")

        current_min = 0
        current_max = 0
        vol_min = 0
        vol_max = 0
        output_vmin = 0
        output_vmax = 0
        cur_index = 0
        vol_index = 0

        rtn,current_min, current_max, output_vmin, output_vmax, cur_index = robot.WeldingGetCurrentRelation()
        print(f"WeldingGetCurrentRelation rtn is: {rtn}")
        print(
            f"current min {current_min} current max {current_max} output vol min {output_vmin} output vol max {output_vmax}")

        rtn,vol_min, vol_max, output_vmin, output_vmax, vol_index = robot.WeldingGetVoltageRelation()
        print(f"WeldingGetVoltageRelation rtn is: {rtn}")
        print(f"vol min {vol_min} vol max {vol_max} output vol min {output_vmin} output vol max {output_vmax}")

        rtn = robot.WeldingSetCurrent(1, 100, 0, 0)
        print(f"WeldingSetCurrent rtn is: {rtn}")

        time.sleep(3)

        rtn = robot.WeldingSetVoltage(1, 10, 0, 0)
        print(f"WeldingSetVoltage rtn is: {rtn}")

        rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0,0.0, 60.000000)
        print(f"rtn is: {rtn}")

        robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0)

        rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200)
        print(f"WeldingSetCheckArcInterruptionParam {rtn}")

        rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0)
        print(f"WeldingSetReWeldAfterBreakOffParam {rtn}")

        enable = 0
        length = 0
        velocity = 0
        move_type = 0
        check_enable = 0
        arc_interrupt_time_length = 0

        rtn,check_enable, arc_interrupt_time_length = robot.WeldingGetCheckArcInterruptionParam()
        print(
            f"WeldingGetCheckArcInterruptionParam checkEnable {check_enable} arcInterruptTimeLength {arc_interrupt_time_length}")

        rtn,enable, length, velocity, move_type = robot.WeldingGetReWeldAfterBreakOffParam()
        print(
            f"WeldingGetReWeldAfterBreakOffParam enable = {enable}, length = {length}, velocity = {velocity}, moveType = {move_type}")

        robot.SetWeldMachineCtrlModeExtDoNum(17)
        for i in range(5):
            robot.SetWeldMachineCtrlMode(0,1)
            error,getCtrlMode=robot.GetWeldMachineCtrlMode
            print(f"GetWeldMachineCtrlMode = {getCtrlMode}")
            time.sleep(1)
            robot.SetWeldMachineCtrlMode(1,1)
            error, getCtrlMode = robot.GetWeldMachineCtrlMode
            print(f"GetWeldMachineCtrlMode = {getCtrlMode}")
            time.sleep(1)

        robot.CloseRPC()

Inicio de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ARCStart(ioType, arcNum, timeout)``"
    "Descripción", "Inicio de soldadura"
    "Parámetros obligatorios", "- ``ioType``：tipo de io 0-IO del controlador； 1-IO extendido
    - ``arcNum``： número de archivo de configuración de la soldadora
    - ``timeout``： tiempo de espera de cebado del arco"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ARCEnd(ioType, arcNum, timeout)``"
    "Descripción", "Fin de soldadura"
    "Parámetros obligatorios", "- ``ioType``： tipo 0-IO del controlador； 1-IO extendido
    - ``arcNum``： número de archivo de configuración de la soldadora
    - ``timeout``： tiempo de espera de cebado del arco"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Inicio de oscilación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveStart(weaveNum)``"
    "Descripción", "Inicio de oscilación"
    "Parámetros obligatorios", "- ``weaveNum``： tipo 0-IO del controlador； 1-IO extendido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin de oscilación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveEnd(weaveNum)``"
    "Descripción", "Fin de oscilación"
    "Parámetros obligatorios", "- ``weaveNum``： número de configuración de parámetros de soldadura oscilante"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Alimentación de alambre hacia adelante
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetForwardWireFeed(ioType, wireFeed)``"
    "Descripción", "Alimentación de alambre hacia adelante"
    "Parámetros obligatorios", "- ``ioType``： 0-IO del controlador；1-IO extendido
    - ``wireFeed``： control de alimentación de alambre  0-detener alimentación；1-alimentar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Alimentación de alambre inversa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetReverseWireFeed(ioType, wireFeed)``"
    "Descripción", "Alimentación de alambre inversa"
    "Parámetros obligatorios", "- ``ioType``： 0-IO del controlador；1-IO extendido
    - ``wireFeed``： control de alimentación de alambre  0-detener alimentación；1-alimentar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Suministro de gas
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAspirated(ioType, airControl)``"
    "Descripción", "Suministro de gas"
    "Parámetros obligatorios", "- ``ioType``： 0-IO del controlador；1-IO extendido
    - ``airControl``： control de suministro de gas  0-detener suministro；1-suministrar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la recuperación de soldadura tras interrupción de la soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingStartReWeldAfterBreakOff()``"
    "Descripción", "Establecer la recuperación de soldadura tras interrupción de la soldadura del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Establecer la salida de soldadura tras interrupción de la soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingAbortWeldAfterBreakOff()``"
    "Descripción", "Establecer la salida de soldadura tras interrupción de la soldadura del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Ejemplo de código de control de soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.SetForwardWireFeed(0, 1)
    time.sleep(1)
    robot.SetForwardWireFeed(0, 0)
    robot.SetReverseWireFeed(0, 1)
    time.sleep(1)
    robot.SetReverseWireFeed(0, 0)
    robot.SetAspirated(0, 1)
    time.sleep(1)
    robot.SetAspirated(0, 0)
    robot.WeldingSetCurrent(1, 230, 0, 0)
    robot.WeldingSetVoltage(1, 24, 0, 1)
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=p1Joint, tool=13, user=0)
    robot.ARCStart(1, 0, 10000)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=p2Desc, tool=13, user=0)
    robot.ARCEnd(1, 0, 10000)
    robot.WeaveEnd(0)
    robot.WeldingStartReWeldAfterBreakOff()
    robot.WeldingAbortWeldAfterBreakOff()
    robot.CloseRPC()

Inicio de soldadura por segmentos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SegmentWeldStart(startDesePos,  endDesePos, startJPos, endJPos, weldLength, noWeldLength, weldIOType, arcNum, weldTimeout, isWeave,weaveNum,tool,user,vel=20.0, acc=0.0, ovl=100.0, blendR=-1.0,exaxis_pos=[0.0, 0.0, 0.0, 0.0],  search=0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0])``"
    "Descripción", "Inicio de soldadura por segmentos"
    "Parámetros obligatorios", "- ``startDesePos``： pose cartesiana inicial，unidad [mm][°]
    - ``endDesePos``： pose cartesiana objetivo，unidad [mm][°]
    - ``startJPos``：posición articular inicial，unidad [°] 
    - ``endJPos``：posición articular objetivo，unidad [°]  
    - ``weldLength``：longitud de soldadura，unidad [mm] 
    - ``noWeldLength``：longitud sin soldadura，unidad [mm] 
    - ``weldIOType``：tipo de IO de soldadura(0-IO de la caja de control；1-IO extendido) arcNum número de archivo de configuración de la soldadora 
    - ``timeout``：tiempo de espera de extinción del arco 
    - ``isWeave``：soldadura False-no soldar 
    - ``weaveNum``：número de configuración de parámetros de soldadura oscilante 
    - ``tool``：número de herramienta，[0~14]
    - ``user``：número de pieza，[0~14]"
    "Parámetros predeterminados", "- ``vel``：porcentaje de velocidad，[0~100] predeterminado20.0
    - ``acc``：aceleración[0~100] no disponible por ahora predeterminado0.0
    - ``ovl``：factor de escala de velocidad，[0~100] predeterminado100.0
    - ``blendR``：[-1.0]-movimiento preciso (bloqueante)，[0~1000]-radio de suavizado (no bloqueante)，unidad [mm] predeterminado-1.0
    - ``exaxis_pos``：posición del eje externo 1 ~ posición del eje externo 4 predeterminado[0.0,0.0,0.0,0.0]
    - ``search``：[0]-sin búsqueda de alambre，[1]-búsqueda de alambre
    - ``offset_flag``：[0]-sin desplazamiento，[1]-desplazamiento en el sistema de coordenadas de pieza/base，[2]-desplazamiento en el sistema de coordenadas de herramienta predeterminado 0
    - ``offset_pos``：cantidad de desplazamiento de pose，unidad [mm][°] predeterminado[0.0,0.0,0.0,0.0,0.0,0.0]"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Ejemplo de código de soldadura por segmentos del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.WeldingSetCurrent(1, 230, 0, 0)
    robot.WeldingSetVoltage(1, 24, 0, 1)
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    rtn = robot.SegmentWeldStart(p1Desc, p2Desc, p1Joint, p2Joint, 20, 20, 0, 0, 5000, 0, 0, 0, 0)
    print(f"SegmentWeldStart rtn is {rtn}")
    robot.CloseRPC()

Inicio de oscilación simulada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveStartSim(weaveNum)``"
    "Descripción", "Inicio de oscilación simulada"
    "Parámetros obligatorios", "- ``weaveNum``：número de parámetros de oscilación"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Fin de oscilación simulada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveEndSim(weaveNum)``"
    "Descripción", "Fin de oscilación simulada"
    "Parámetros obligatorios", "- ``weaveNum``：número de parámetros de oscilación"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Iniciar alerta de detección de trayectoria (sin movimiento)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveInspectStart(weaveNum)``"
    "Descripción", "Iniciar alerta de detección de trayectoria (sin movimiento)"
    "Parámetros obligatorios", "- ``weaveNum``：número de parámetros de oscilación"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Finalizar alerta de detección de trayectoria (sin movimiento)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveInspectEnd(weaveNum)``"
    "Descripción", "Finalizar alerta de detección de trayectoria (sin movimiento)"
    "Parámetros obligatorios", "- ``weaveNum``：número de parámetros de oscilación"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Inicio de cambio gradual de oscilación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveChangeStart(weaveChangeFlag, weaveNum, velStart, velEnd)``"
    "Descripción", "Inicio de cambio gradual de oscilación"
    "Parámetros obligatorios", "- ``weaveChangeFlag``：número de oscilación 1-cambiar parámetros de oscilación；2-cambiar parámetros de oscilación + velocidad de soldadura
    - ``weaveNum``：número de oscilación
    - ``velStart``：velocidad de inicio de soldadura，(cm/min)
    - ``velEnd``：velocidad de fin de soldadura，(cm/min)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Ejemplo de código de soldadura con cambio gradual de oscilación del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos= p1Joint,tool= 13,user= 0)
    robot.WeaveStartSim(0)
    robot.MoveL(desc_pos= p2Desc,tool= 13,user= 0)
    robot.WeaveEndSim(0)
    robot.MoveJ(joint_pos= p1Joint,tool= 13,user= 0)
    robot.WeaveInspectStart(0)
    robot.MoveL(desc_pos= p2Desc,tool= 13,user= 0,)
    robot.WeaveInspectEnd(0)
    robot.WeldingSetVoltage(1, 19, 0, 0)
    robot.WeldingSetCurrent(1, 190, 0, 0)
    robot.MoveL(desc_pos= p1Desc,tool= 1,user= 1,vel= 100,acc= 100,ovl= 50)
    robot.ARCStart(1, 0, 10000)
    robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0)
    robot.WeaveStart(0)
    robot.WeaveChangeStart(1, 0, 50, 30)
    robot.MoveL(desc_pos= p2Desc,tool= 1,user= 1,vel= 100)
    robot.WeaveChangeEnd()
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0)
    robot.ARCEnd(1, 0, 10000)
    robot.CloseRPC()

Fin de cambio gradual de oscilación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.9-3.7.9

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveChangeEnd()``"
    "Descripción", "Fin de cambio gradual de oscilación"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

IO extendido-configurar señal de detección de gas de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAirControlExtDoNum(DONum)``"
    "Descripción", "IO extendido-configurar señal de detección de gas de la soldadora"
    "Parámetros obligatorios", "
    - ``DONum``：número DO extendido de la señal de detección de gas
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

IO extendido-configurar señal de cebado del arco de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetArcStartExtDoNum(DONum)``"
    "Descripción", "IO extendido-configurar señal de cebado del arco de la soldadora"
    "Parámetros obligatorios", "
    - ``DONum``：número DO extendido de la señal de detección de gas
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 
        
IO extendido-configurar señal de alimentación de alambre inversa de la soldadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWireReverseFeedExtDoNum(DONum)``"
    "Descripción", "IO extendido-configurar señal de alimentación de alambre inversa de la soldadora"
    "Parámetros obligatorios", "
    - ``DONum``：número DO extendido de la señal de detección de gas
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 
        
IO extendido-configurar señal de alimentación de alambre hacia adelante de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWireForwardFeedExtDoNum(DONum)``"
    "Descripción", "IO extendido-configurar señal de alimentación de alambre hacia adelante de la soldadora"
    "Parámetros obligatorios", "
    - ``DONum``：número DO extendido de la señal de detección de gas
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 
        
IO extendido-configurar señal de éxito de cebado del arco de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetArcDoneExtDiNum(DINum)``"
    "Descripción", "IO extendido-configurar señal de éxito de cebado del arco de la soldadora"
    "Parámetros obligatorios", "
    - ``DINum``：número DI extendido de la señal de preparación de la soldadora
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 
        
IO extendido-configurar señal de preparación de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetArcDoneExtDiNum(DINum)``"
    "Descripción", "IO extendido-configurar señal de preparación de la soldadora"
    "Parámetros obligatorios", "
    - ``DINum``：número DI extendido de la señal de preparación de la soldadora
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 
        
IO extendido-configurar señal de recuperación de interrupción de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExtDIWeldBreakOffRecover(reWeldDINum, abortWeldDINum)``"
    "Descripción", "IO extendido-configurar señal de recuperación de interrupción de soldadura"
    "Parámetros obligatorios", "
    - ``reWeldDINum``：número DI extendido de la señal de recuperación de soldadura tras interrupción de soldadura
    - ``abortWeldDINum``：número DI extendido de la señal de salida de soldadura tras interrupción de soldadura
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Ejemplo de código para establecer señales de soldadura de IO extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.SetArcStartExtDoNum(10)
    print(f"SetArcStartExtDoNum rtn is {rtn}")
    rtn = robot.SetAirControlExtDoNum(20)
    print(f"SetAirControlExtDoNum rtn is {rtn}")
    rtn = robot.SetWireForwardFeedExtDoNum(30)
    print(f"SetWireForwardFeedExtDoNum rtn is {rtn}")
    rtn = robot.SetWireReverseFeedExtDoNum(40)
    rtn = robot.SetWeldReadyExtDiNum(50)
    print(f"SetWeldReadyExtDiNum rtn is {rtn}")
    rtn = robot.SetArcDoneExtDiNum(60)
    print(f"SetArcDoneExtDiNum rtn is {rtn}")
    rtn = robot.SetExtDIWeldBreakOffRecover(70, 80)
    print(f"SetExtDIWeldBreakOffRecover rtn is {rtn}")
    rtn = robot.SetWireSearchExtDIONum(0, 1)
    print(f"SetWireSearchExtDIONum rtn is {rtn}")
    robot.CloseRPC()

Obtener la configuración de funciones de DI extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetExtDIConfig(self)``"
    "Descripción", "Obtener la configuración de funciones de DI extendido"
    "Parámetros obligatorios", "
    - ``DIConfig``：configuración de entrada DI extendida；DIConfig[0]-puerto DI extendido de preparación de la soldadora
    - ``DIConfig[1]``：puerto DI extendido de éxito de cebado del arco
    - ``DIConfig[2]``：puerto DI extendido de recuperación de interrupción de soldadura
    - ``DIConfig[3]``：puerto DI extendido de salida de interrupción de soldadura
    - ``DIConfig[4]``：puerto DI extendido de éxito de búsqueda de alambre
    - ``DIConfig[5]``：puerto DI extendido de estado de funcionamiento de la soldadora láser
    - ``DIConfig[6]``：puerto DI extendido de estado de fallo de la soldadora láser
    - ``DIConfig[7-15]``：reservado
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Obtener la configuración de funciones de DO extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetExtDOConfig(self)``"
    "Descripción", "Obtener la configuración de funciones de DO extendido"
    "Parámetros obligatorios", "
    - ``DOConfig``：configuración de salida DO extendida；DOConfig[0]-puerto DO extendido de cebado del arco de la soldadora
    - ``DOConfig[1]``：puerto DO extendido de detección de gas
    - ``DOConfig[2]``：puerto DO extendido de alimentación de alambre hacia adelante
    - ``DOConfig[3]``：puerto DO extendido de alimentación de alambre inversa
    - ``DOConfig[4]``：puerto DO extendido de búsqueda de alambre
    - ``DOConfig[5]``：puerto DO extendido del modo de control de la soldadora
    - ``DOConfig[6]``：puerto DO extendido de habilitación de la soldadora láser
    - ``DOConfig[7]``：puerto DO extendido de inicio (emisión de luz) de la soldadora láser
    - ``DOConfig[8]``：puerto DO extendido de restablecimiento de la soldadora láser
    - ``DOConfig[9-15]``：reservado
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Ejemplo de código para obtener DI/DO extendidos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

    rtn = robot.SetArcStartExtDoNum(10)
        print(f"SetArcStartExtDoNum rtn is {rtn}")

        rtn = robot.SetAirControlExtDoNum(20)
        print(f"SetAirControlExtDoNum rtn is {rtn}")

        rtn = robot.SetWireForwardFeedExtDoNum(30)
        print(f"SetWireForwardFeedExtDoNum rtn is {rtn}")

        rtn = robot.SetWireReverseFeedExtDoNum(40)
        print(f"SetWireReverseFeedExtDoNum rtn is {rtn}")

        rtn = robot.SetWeldReadyExtDiNum(50)
        print(f"SetWeldReadyExtDiNum rtn is {rtn}")

        rtn = robot.SetArcDoneExtDiNum(60)
        print(f"SetArcDoneExtDiNum rtn is {rtn}")

        rtn = robot.SetExtDIWeldBreakOffRecover(70, 80)
        print(f"SetExtDIWeldBreakOffRecover rtn is {rtn}")

        rtn = robot.SetWireSearchExtDIONum(0, 1)
        print(f"SetWireSearchExtDIONum rtn is {rtn}")

        rtn, DIConfig = robot.GetExtDIConfig()
        print(f"GetExtDIConfig rtn is {rtn}")
        print(f"welder ready {DIConfig[0]}")
        print(f"arc done {DIConfig[1]}")
        print(f"reweld start {DIConfig[2]}")
        print(f"abort reweld {DIConfig[3]}")
        print(f"wiresearch done {DIConfig[4]}")
        print(f"Laser welding State {DIConfig[5]}")
        print(f"laser welding error state {DIConfig[6]}")

        rtn, DOConfig = robot.GetExtDOConfig()
        print(f"GetExtDOConfig rtn is {rtn}")
        print(f"Arc Start {DOConfig[0]}")
        print(f"Air Test {DOConfig[1]}")
        print(f"Wire forward {DOConfig[2]}")
        print(f"Wire Inverse {DOConfig[3]}")
        print(f"wiresearch {DOConfig[4]}")
        print(f"Weld Mode {DOConfig[5]}")
        print(f"laser Enable {DOConfig[6]}")
        print(f"Laser On {DOConfig[7]}")
        print(f"Laser Reset Error {DOConfig[8]}")

        robot.CloseRPC()
    
Control de seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.9-3.7.9

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceControl(flag,delaytime, isLeftRight, klr, tStartLr, stepMaxLr, sumMaxLr, isUpLow, kud, tStartUd, stepMaxUd, sumMaxUd, axisSelect, referenceType, referSampleStartUd, referSampleCountUd, referenceCurrent, offsetType, offsetParameter)``"
    "Descripción", "Control de seguimiento de arco"
    "Parámetros obligatorios", "- ``flag``： interruptor，0-desactivado；1-activado
    - ``delayTime``： tiempo de retardo，unidadms
    - ``isLeftRight``： compensación de desviación izquierda-derecha 0-desactivado，1-activado
    - ``klr``： coeficiente de ajuste izquierda-derecha (sensibilidad)
    - ``tStartLr``： tiempo de inicio de compensación izquierda-derecha cyc
    - ``stepMaxLr``： cantidad máxima de compensación izquierda-derecha por vez mm
    - ``sumMaxLr``： cantidad máxima total de compensación izquierda-derecha mm
    - ``isUpLow``： compensación de desviación arriba-abajo 0-desactivado，1-activado
    - ``kud``： coeficiente de ajuste arriba-abajo (sensibilidad)
    - ``tStartUd``： tiempo de inicio de compensación arriba-abajo cyc
    - ``stepMaxUd``： cantidad máxima de compensación arriba-abajo por vez mm
    - ``sumMaxUd``： cantidad máxima total de compensación arriba-abajo
    - ``axisSelect``： selección del sistema de coordenadas arriba-abajo，0-oscilación；1-herramienta；2-base
    - ``referenceType``： modo de configuración de la corriente de referencia arriba-abajo，0-retroalimentación；1-constante
    - ``referSampleStartUd``： inicio de conteo de muestreo de la corriente de referencia arriba-abajo (retroalimentación)，cyc
    - ``referSampleCountUd``： conteo de ciclos de muestreo de la corriente de referencia arriba-abajo (retroalimentación)，cyc
    - ``referenceCurrent``： corriente de referencia arriba-abajo mA
    - ``offsetType``： tipo de seguimiento con desplazamiento，0-sin desplazamiento；1-muestreo；2-porcentaje
    - ``offsetParameter``： parámetro de desplazamiento；muestreo (tiempo de inicio de muestreo de desplazamiento, por defecto se muestrea un ciclo)；porcentaje (porcentaje de desplazamiento (-100 ~ 100))"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Selección de canal AI de seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceExtAIChannelConfig(channel)``"
    "Descripción", "Selección de canal AI de seguimiento de arco"
    "Parámetros obligatorios", "- ``channel``：selección de canal AI de seguimiento de arco,[0-3]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Seguimiento de arco + activación de compensación multicapa y multipasada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceReplayStart()``"
    "Descripción", "Seguimiento de arco + activación de compensación multicapa y multipasada"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Seguimiento de arco + desactivación de compensación multicapa y multipasada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceReplayEnd()``"
    "Descripción", "Seguimiento de arco + desactivación de compensación multicapa y multipasada"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Transformación de coordenadas de desplazamiento-soldadura multicapa y multipasada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MultilayerOffsetTrsfToBase(pointo, pointX, pointZ, dx, dy, db)``"
    "Descripción", "Transformación de coordenadas de desplazamiento-soldadura multicapa y multipasada"
    "Parámetros obligatorios", "- ``pointo``：pose cartesiana del punto de referencia
    - ``pointX``：pose cartesiana del punto de dirección de desplazamiento X del punto de referencia
    - ``pointZ``：pose cartesiana del punto de dirección de desplazamiento Z del punto de referencia
    - ``dx``：cantidad de desplazamiento en dirección x(mm)
    - ``dz``：cantidad de desplazamiento en dirección z(mm)
    - ``dry``：cantidad de desplazamiento alrededor del eje y(°)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``offset``：cantidad de desplazamiento calculada"

Ejemplo de código de seguimiento de arco de soldadura multicapa y multipasada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    mulitilineorigin1_joint = [-24.090, -63.501, 84.288, -111.940, -93.426, 57.669]
    mulitilineorigin1_desc = [-677.559, 190.951, -1.205, 1.144, -41.482, -82.577]
    mulitilineX1_desc = [-677.556, 211.949, -1.206]
    mulitilineZ1_desc = [-677.564, 190.956, 19.817]
    mulitilinesafe_joint = [-25.734, -63.778, 81.502, -108.975, -93.392, 56.021]
    mulitilinesafe_desc = [-677.561, 211.950, 19.812, 1.144, -41.482, -82.577]
    mulitilineorigin2_joint = [-29.743, -75.623, 101.241, -116.354, -94.928, 55.735]
    mulitilineorigin2_desc = [-563.961, 215.359, -0.681, 2.845, -40.476, -87.443]
    mulitilineX2_desc = [-563.965, 220.355, -0.680]
    mulitilineZ2_desc = [-563.968, 215.362, 4.331]
    epos = [0, 0, 0, 0]
    offset = [0, 0, 0, 0, 0, 0]
    time.sleep(0.01)
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error = robot.WeaveStart(0)
    print(f"WeaveStart return: {error}")
    error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0)
    print(f"ArcWeldTraceControl return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 1,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0)
    print(f"ArcWeldTraceControl return: {error}")
    error = robot.WeaveEnd(0)
    print(f"WeaveEnd return: {error}")
    error = robot.ARCEnd(1, 0, 10000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error,offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc[:3], mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc[:3], mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.ArcWeldTraceReplayStart()
    print(f"ArcWeldTraceReplayStart return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 2,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceReplayEnd()
    print(f"ArcWeldTraceReplayEnd return: {error}")
    error = robot.ARCEnd(1, 0, 10000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc[:3], mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc[:3], mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0)
    error = robot.ArcWeldTraceReplayStart()
    print(f"ArcWeldTraceReplayStart return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 2,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceReplayEnd()
    print(f"ArcWeldTraceReplayEnd return: {error}")
    error = robot.ARCEnd(1, 0, 3000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    robot.CloseRPC()

Selección de canal AI de retroalimentación de corriente de la soldadora de seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceAIChannelCurrent(channel)``"
    "Descripción", "Selección de canal AI de retroalimentación de corriente de la soldadora de seguimiento de arco"
    "Parámetros obligatorios", "- ``channel``：canal；0-AI0 extendido；1-AI1 extendido；2-AI2 extendido；3-AI3 extendido；4-AI0 de la caja de control；5-AI1 de la caja de control"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Selección de canal AI de retroalimentación de voltaje de la soldadora de seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceAIChannelVoltage(channel)``"
    "Descripción", "Selección de canal AI de retroalimentación de voltaje de la soldadora de seguimiento de arco"
    "Parámetros obligatorios", "- ``channel``：canal；0-AI0 extendido；1-AI1 extendido；2-AI2 extendido；3-AI3 extendido；4-AI0 de la caja de control；5-AI1 de la caja de control"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Parámetros de conversión de retroalimentación de corriente de la soldadora de seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceCurrentPara(AILow, AIHigh, currentLow, currentHigh)``"
    "Descripción", "Parámetros de conversión de retroalimentación de corriente de la soldadora de seguimiento de arco"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``AILow``：límite inferior del canal AI，valor predeterminado0V，rango[0-10V]
    - ``AIHigh``：límite superior del canal AI，valor predeterminado10V，rango[0-10V]
    - ``currentLow``：valor de corriente de la soldadora correspondiente al límite inferior del canal AI，valor predeterminado0V，rango[0-200V]
    - ``currentHigh``：valor de corriente de la soldadora correspondiente al límite superior del canal AI，valor predeterminado100V，rango[0-200V]"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Parámetros de conversión de retroalimentación de voltaje de la soldadora de seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceVoltagePara(AILow, AIHigh, voltageLow, voltageHigh)``"
    "Descripción", "Parámetros de conversión de retroalimentación de voltaje de la soldadora de seguimiento de arco"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``AILow``：límite inferior del canal AI，valor predeterminado0V，rango[0-10V]
    - ``AIHigh``：límite superior del canal AI，valor predeterminado10V，rango[0-10V]
    - ``voltageLow``：valor de voltaje de la soldadora correspondiente al límite inferior del canal AI，valor predeterminado0V，rango[0-200V]
    - ``voltageHigh``：valor de voltaje de la soldadora correspondiente al límite superior del canal AI，valor predeterminado100V，rango[0-200V]"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')

    safetydescPose = [-504.043,275.181,40.908,-28.002,-42.025,-14.044]
    safetyjointPos = [-39.078,-76.732,87.227,-99.47,-94.301,18.714]
    startdescPose = [-473.86,257.879,-20.849,-37.317,-42.021,2.543]
    startjointPos = [-43.487,-76.526,95.568,-104.445,-89.356,3.72]
    enddescPose = [-499.844,141.225,7.72,-34.856,-40.17,13.13]
    endjointPos = [-31.305,-82.998,99.401,-104.426,-89.35,3.696]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=safetyjointPos, tool=1, user=0, vel=20, acc=100)
    robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0)
    robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1)
    robot.WeldingSetVoltage(0, 25, 1, 0)  # ----establecer voltaje
    robot.WeldingSetCurrent(0, 260, 0, 0)  # ----establecer corriente
    rtn = robot.ArcWeldTraceAIChannelCurrent(4)
    print("ArcWeldTraceAIChannelCurrent rtn is", rtn)
    rtn = robot.ArcWeldTraceAIChannelVoltage(5)
    print("ArcWeldTraceAIChannelVoltage rtn is", rtn)
    rtn = robot.ArcWeldTraceCurrentPara(0, 5, 0, 500)
    print("ArcWeldTraceCurrentPara rtn is", rtn)
    rtn = robot.ArcWeldTraceVoltagePara(1.018, 10, 0, 50)
    print("ArcWeldTraceVoltagePara rtn is", rtn)
    robot.MoveJ(joint_pos=startjointPos, tool=1, user=0, vel=20, acc=100)
    robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.ARCStart(0, 0, 10000)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=enddescPose, tool=1, user=0, vel=100, ovl= 2, acc=100)
    robot.ARCEnd(0, 0, 10000)
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.MoveJ(joint_pos=safetyjointPos, tool=1, user=0, vel=20, acc=100)

Establecer el puerto IO extendido de búsqueda de alambre
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWireSearchExtDIONum(searchDoneDINum, searchStartDONum)``"
    "Descripción", "Establecer el puerto IO extendido de búsqueda de alambre"
    "Parámetros obligatorios", "- ``searchDoneDINum``：puerto DO de éxito de búsqueda de alambre(0-127)
    - ``searchStartDONum``：puerto DO de control de inicio/parada de búsqueda de alambre(0-127)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Ejemplo de código
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    toolCoord = [0, 0, 200, 0, 0, 0]
    robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0)
    wobjCoord = [0, 0, 0, 0, 0, 0]
    robot.SetWObjCoord(1, wobjCoord, 0)
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 50, 5, 50, 1, 50, 10)
    robot.ExtDevLoadUDPDriver()
    robot.SetWireSearchExtDIONum(0, 0)
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    descStart = [216.543, 445.175, 93.465, 179.683, 1.757, -112.641]
    jointStart = [-128.345, -86.660, 114.679, -119.625, -89.219, 74.303]
    descEnd = [111.143, 523.384, 87.659, 179.703, 1.835, -97.750]
    jointEnd = [-113.454, -81.060, 109.328, -119.954, -89.218, 74.302]
    error = robot.MoveL(desc_pos=descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descEnd,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    descREF0A = [142.135, 367.604, 86.523, 179.728, 1.922, -111.089]
    jointREF0A = [-126.794, -100.834, 128.922, -119.864, -89.218, 74.302]
    descREF0B = [254.633, 463.125, 72.604, 179.845, 2.341, -114.704]
    jointREF0B = [-130.413, -81.093, 112.044, -123.163, -89.217, 74.303]
    descREF1A = [92.556, 485.259, 47.476, -179.932, 3.130, -97.512]
    jointREF1A = [-113.231, -83.815, 119.877, -129.092, -89.217, 74.303]
    descREF1B = [203.103, 583.836, 63.909, 179.991, 2.854, -103.372]
    jointREF1B = [-119.088, -69.676, 98.692, -121.761, -89.219, 74.303]
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos=descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    varNameRef = ["REF0", "REF1", "#", "#", "#", "#"]
    varNameRes = ["RES0", "RES1", "#", "#", "#", "#"]
    offectFlag = 0
    offectPos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    error, offectFlag, offectPos = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes)
    print(f"GetWireSearchOffset return: {error}")
    error = robot.PointsOffsetEnable(0, offectPos)
    print(f"PointsOffsetEnable return: {error}")
    error = robot.MoveL(desc_pos= descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descEnd,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.PointsOffsetDisable()
    robot.CloseRPC()

Inicio de búsqueda de alambre
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WireSearchStart(refPos,searchVel,searchDis,autoBackFlag,autoBackVel,autoBackDis,offectFlag)``"
    "Descripción", "Inicio de búsqueda de alambre"
    "Parámetros obligatorios", "- ``refPos``： 1-punto de referencia 0-punto de contacto
    - ``searchVel``： velocidad de búsqueda %
    - ``searchDis``： distancia de búsqueda mm
    - ``autoBackFlag``： indicador de retorno automático，0-no automático；-automático
    - ``autoBackVel``： velocidad de retorno automático %
    - ``autoBackDis``： distancia de retorno automático mm
    - ``offectFlag``： 1-búsqueda con desplazamiento；0-búsqueda de punto de enseñanza"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Fin de búsqueda de alambre
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WireSearchEnd(refPos,searchVel,searchDis,autoBackFlag,autoBackVel,autoBackDis,offectFlag)``"
    "Descripción", "Fin de búsqueda de alambre"
    "Parámetros obligatorios", "- ``refPos``： 1-punto de referencia 2-punto de contacto
    - ``searchVel``： velocidad de búsqueda %
    - ``searchDis``： distancia de búsqueda mm
    - ``autoBackFlag``： indicador de retorno automático，0-no automático；-automático
    - ``autoBackVel``： velocidad de retorno automático %
    - ``autoBackDis``： distancia de retorno automático mm
    - ``offectFlag``： 1-búsqueda con desplazamiento；2-búsqueda de punto de enseñanza"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Calcular el desplazamiento de búsqueda de alambre
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWireSearchOffset(seamType, method,varNameRef,varNameRes)``"
    "Descripción", "Calcular el desplazamiento de búsqueda de alambre"
    "Parámetros obligatorios", "- ``seamType``： tipo de cordón de soldadura
    - ``method``： método de cálculo
    - ``varNameRef``： punto de referencia1-6，“#”indica variable sin punto
    - ``varNameRes``： punto de contacto1-6，“#”indica variable sin punto"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``offsetFlag``： 0-el desplazamiento se superpone directamente al punto de instrucción；1-el desplazamiento requiere transformación de coordenadas del punto de instrucción
    - ``offset``： pose de desplazamiento[x, y, z, a, b, c]"

Esperar a que finalice la búsqueda de alambre
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WireSearchWait(varname)``"
    "Descripción", "Esperar a que finalice la búsqueda de alambre"
    "Parámetros obligatorios", "- ``varName``： nombre del punto de contacto “RES0” ~ “RES99”"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Escritura del punto de contacto de búsqueda de alambre en la base de datos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetPointToDatabase(varName,pos)``"
    "Descripción", "Escritura del punto de contacto de búsqueda de alambre en la base de datos"
    "Parámetros obligatorios", "- ``varName``： nombre del punto de contacto “RES0” ~ “RES99”
    - ``pos``：datos del punto de contacto[x, y, x, a, b, c]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode" 

Ejemplo de código de búsqueda de alambre del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    toolCoord = [0, 0, 200, 0, 0, 0]
    robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0)
    wobjCoord = [0, 0, 0, 0, 0, 0]
    robot.SetWObjCoord(1, wobjCoord, 0)
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    descStart = [216.543, 445.175, 93.465, 179.683, 1.757, -112.641]
    jointStart = [-128.345, -86.660, 114.679, -119.625, -89.219, 74.303]
    descEnd = [111.143, 523.384, 87.659, 179.703, 1.835, -97.750]
    jointEnd = [-113.454, -81.060, 109.328, -119.954, -89.218, 74.302]
    error = robot.MoveL(desc_pos=descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descEnd,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    descREF0A = [142.135, 367.604, 86.523, 179.728, 1.922, -111.089]
    jointREF0A = [-126.794, -100.834, 128.922, -119.864, -89.218, 74.302]
    descREF0B = [254.633, 463.125, 72.604, 179.845, 2.341, -114.704]
    jointREF0B = [-130.413, -81.093, 112.044, -123.163, -89.217, 74.303]
    descREF1A = [92.556, 485.259, 47.476, -179.932, 3.130, -97.512]
    jointREF1A = [-113.231, -83.815, 119.877, -129.092, -89.217, 74.303]
    descREF1B = [203.103, 583.836, 63.909, 179.991, 2.854, -103.372]
    jointREF1B = [-119.088, -69.676, 98.692, -121.761, -89.219, 74.303]
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos=descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    varNameRef = ["REF0", "REF1", "#", "#", "#", "#"]
    varNameRes = ["RES0", "RES1", "#", "#", "#", "#"]
    offectFlag = 0
    offectPos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    error, offectFlag, offectPos = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes)
    print(f"GetWireSearchOffset return: {error}")
    error = robot.PointsOffsetEnable(0, offectPos)
    print(f"PointsOffsetEnable return: {error}")
    error = robot.MoveL(desc_pos= descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descEnd,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.PointsOffsetDisable()
    robot.CloseRPC()

Establecer el inicio del cambio gradual del voltaje de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetVoltageGradualChangeStart(IOType, voltageStart, voltageEnd, AOIndex, blend)``"
    "Descripción", "Establecer el inicio del cambio gradual del voltaje de soldadura"
    "Parámetros obligatorios", "- ``IOType``：tipo de control；0-IO de la caja de control；1-protocolo de comunicación digital(UDP);2-protocolo de comunicación digital(ModbusTCP)
    - ``voltageStart``：voltaje de soldadura inicial(V)
    - ``voltageEnd``：voltaje de soldadura final(V)
    - ``AOIndex``：número de puerto AO de la caja de control(0-1)
    - ``blend``：si suavizar 0-no suavizar；1-suavizar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el fin del cambio gradual del voltaje de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetVoltageGradualChangeEnd()``"
    "Descripción", "Establecer el fin del cambio gradual del voltaje de soldadura"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el inicio del cambio gradual de la corriente de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetCurrentGradualChangeStart(IOType, currentStart, currentEnd, AOIndex, blend)``"
    "Descripción", "Establecer el inicio del cambio gradual de la corriente de soldadura"
    "Parámetros obligatorios", "- ``IOType``：tipo de control；0-IO de la caja de control；1-protocolo de comunicación digital(UDP);2-protocolo de comunicación digital(ModbusTCP)
    - ``currentStart``：corriente de soldadura inicial(A)
    - ``currentEnd``：corriente de soldadura final(A)
    - ``AOIndex``：número de puerto AO de la caja de control(0-1)
    - ``blend``：si suavizar 0-no suavizar；1-suavizar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el fin del cambio gradual de la corriente de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetCurrentGradualChangeEnd()``"
    "Descripción", "Establecer el fin del cambio gradual de la corriente de soldadura"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de cambio gradual de corriente y voltaje de soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    startdescPose = [-484.707, 276.996, -14.013, -37.657, -40.508, -1.548]
    startjointPos = [-45.421, -75.673, 93.627, -104.302, -87.938, 6.005]
    enddescPose = [-508.767, 137.109, -13.966, -37.639, -40.508, -1.559]
    endjointPos = [-32.768, -80.947, 100.254, -106.201, -87.201, 18.648]
    safedescPose = [-484.709, 294.436, 13.621, -37.660, -40.508, -1.545]
    safejointPos = [-46.604, -75.410, 89.109, -100.003, -88.012, 4.823]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0)
    robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1)
    robot.WeldingSetVoltage(0, 25, 1, 0)  # ----establecer voltaje
    robot.WeldingSetCurrent(0, 260, 0, 0)  # ----establecer corriente
    robot.MoveJ(joint_pos=safejointPos, tool=1, user=0, vel=5, acc=100)
    rtn = robot.WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0)
    print("WeldingSetCurrentGradualChangeStart rtn is", rtn)
    rtn = robot.WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0)
    print("WeldingSetVoltageGradualChangeStart rtn is", rtn)
    rtn = robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    print("ArcWeldTraceControl rtn is", rtn)
    robot.MoveJ(joint_pos=startjointPos, tool=1, user=0, vel=5, acc=100)
    robot.ARCStart(0, 0, 10000)
    robot.WeaveStart(0)
    robot.WeaveChangeStart(2, 1, 24, 36)
    robot.MoveL(desc_pos=enddescPose, tool=1, user=0, vel=100, ovl=2, acc=100)
    robot.ARCEnd(0, 0, 10000)
    robot.WeaveChangeEnd()
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.WeldingSetCurrentGradualChangeEnd()
    robot.WeldingSetVoltageGradualChangeEnd()

Establecer parámetros de oscilación personalizados
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CustomWeaveSetPara(id, pointNum, point, stayTime, frequency, incStayType, stationary)``"
    "Descripción", "Establecer parámetros de oscilación personalizados"
    "Parámetros obligatorios", "- ``id``：número de oscilación personalizada：0-2
    - ``pointNum``：número de puntos de oscilación 0-10
    - ``point``：datos de puntos finales de movimiento x,y,z
    - ``stayTime``：tiempo de permanencia de oscilación ms
    - ``frequency``：frecuencia de oscilación Hz
    - ``incStayType``：modo de espera：0-el ciclo no incluye tiempo de espera；1-el ciclo incluye tiempo de espera
    - ``stationary``：espera en la posición de oscilación：0-continuar moviéndose durante el tiempo de espera；1-permanecer estático durante el tiempo de espera"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener parámetros de oscilación personalizados
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CustomWeaveGetPara(id)``"
    "Descripción", "Obtener parámetros de oscilación personalizados"
    "Parámetros obligatorios", "- ``id``：número de oscilación personalizada：0-2"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``pointNum``：número de puntos de oscilación 0-10
    - ``point``：datos de puntos finales de movimiento x,y,z
    - ``stayTime``：tiempo de permanencia de oscilación ms
    - ``frequency``：frecuencia de oscilación Hz
    - ``incStayType``：modo de espera：0-el ciclo no incluye tiempo de espera；1-el ciclo incluye tiempo de espera
    - ``stationary``：espera en la posición de oscilación：0-continuar moviéndose durante el tiempo de espera；1-permanecer estático durante el tiempo de espera"

Ejemplo de código de parámetros de oscilación personalizados
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    point = [0.0] * 30
    point[0] = -3.0
    point[1] = -3.0
    point[2] = 0.0
    point[3] = -6.0
    point[4] = 0.0
    point[5] = 0.0
    point[6] = -3.0
    point[7] = 3.0
    point[8] = 0.0
    point[9] = 0.0
    point[10] = 0.0
    point[11] = 0.0
    stayTime = [0.0] * 10
    rtn = robot.CustomWeaveSetPara(2, 4, point, stayTime, 1.000, 0, 0)
    print(f"CustomWeaveSetPara rtn is {rtn}")
    time.sleep(1)
    pointNum = 0
    frequency = 0.0
    incStayType = 0
    stationary = 0
    rtn, pointNum, point, stayTime, frequency, incStayType, stationary = robot.CustomWeaveGetPara(2)
    print(f"pointNum is {pointNum}")
    for i in range(pointNum):
        print(f"point {i}, point x y z {point[i * 3 + 0]},{point[i * 3 + 1]},{point[i * 3 + 2]}")
    print(f"fre is {frequency}, stay is {incStayType},{stationary}")
    robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000)
    desc_p1 = [-288.650, 367.807, 288.404, 0.000, -0.001, 0.001]
    desc_p2 = [-431.714, 367.815, 288.415, 0.001, 0.001, 0.000]
    desc_p3 = [-348.666, 427.798, 288.404, -0.000, -0.000, 0.001]
    j1 = [140.656, -84.560, -91.707, -93.734, 90.000, 50.655]
    j2 = [149.873, -98.298, -77.599, -94.103, 90.000, 59.873]
    j3 = [139.773, -96.173, -80.014, -93.814, 90.000, 49.772]
    epos = [0.0] * 4
    offset_pos = [0.0] * 6
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.Circle(desc_pos_p=desc_p3, tool_p=3, user_p=0, vel_p=50, desc_pos_t=desc_p2, tool_t=3, user_t=0, vel_t=50, oacc=10)
    robot.WeaveEnd(0)
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.MoveC(desc_pos_p=desc_p3, tool_p=3, user_p=0, vel_p=50, desc_pos_t=desc_p2, tool_t=3, user_t=0, vel_t=50)
    robot.WeaveEnd(0)
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=desc_p2, tool=3, user=0, vel=100, ovl=10, speedPercent=100)
    robot.WeaveEnd(0)
    robot.CloseRPC()

Configuración de parámetros de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingParam(self, num, scanSpeed, scanWidth, peakPower, dutyCycle, Freq, io_type=1)``"
    "Descripción", "Escribir los parámetros de configuración de uno de los 10 grupos de procesos de la soldadora láser y configurarlos en la soldadora"
    "Parámetros obligatorios", "
    - ``io_type``:tipo de comunicación 0-IO 1-UDP
    - ``Num``:número de grupo a configurar(1~10)
    - ``scanSpeed``:velocidad de escaneo
    - ``scanWidth``:ancho de escaneo
    - ``peakPower``:potencia pico
    - ``dutyCycle``:ciclo de trabajo
    - ``Freq``:frecuencia
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer inicio y parada de soldadura láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingStartEnd(self, status, io_type=1, max_waittime=10000)``"
    "Descripción", "Establecer encendido y apagado de la soldadora láser"
    "Parámetros obligatorios", "
    - ``io_type``:tipo de comunicación 0-IO 1-UDP
    - ``status``:palabra de control 0-recepción de luz 1-emisión de luz
    - ``max_waittime``:tiempo máximo de espera
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Habilitación y deshabilitación de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingEnable(self, status, io_type=1)``"
    "Descripción", "Habilitación y deshabilitación de la soldadora láser"
    "Parámetros obligatorios", "
    - ``io_type``:tipo de comunicación 0-IO 1-UDP
    - ``status``:0-deshabilitar 1-habilitar
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Restablecimiento de fallos de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ResetLaserWeldingErr(self,status, io_type=1)``"
    "Descripción", "Restablecimiento de fallos de la soldadora láser"
    "Parámetros obligatorios", "
    - ``io_type``:tipo de comunicación 0-IO 1-UDP
    - ``status``:palabra de control 0-inválido 1-restablecimiento de fallos
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el estado de funcionamiento de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLaserWeldingRunningState(self, io_type=1)``"
    "Descripción", "Obtener el estado de funcionamiento de la soldadora láser"
    "Parámetros obligatorios", "
    - ``io_type``:tipo de comunicación 0-IO 1-UDP
    - ``status``:palabra de control 0-parada 1-funcionamiento
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el estado de fallo de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLaserWeldingErrState(self, io_type=1)``"
    "Descripción", "Obtener el estado de fallo de la soldadora láser"
    "Parámetros obligatorios", "
    - ``io_type``:tipo de comunicación 0-IO 1-UDP
    - ``status``:0-sin fallo 1-con fallo
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener los parámetros de configuración de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLaserWeldingParamTarget(self, num)``"
    "Descripción", "Obtener los parámetros de configuración de uno de los 10 grupos de procesos de la soldadora láser"
    "Parámetros obligatorios", "
    - ``Num``:número de grupo a configurar(1~10)
    - ``scanSpeed``:velocidad de escaneo
    - ``scanWidth``:ancho de escaneo
    - ``peakPower``:potencia pico
    - ``dutyCycle``:ciclo de trabajo
    - ``Freq``:frecuencia
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener los parámetros de configuración vigentes actualmente de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLaserWeldingParamActual(self, io_type=1)``"
    "Descripción", "Obtener los parámetros de configuración vigentes actualmente de la soldadora láser"
    "Parámetros obligatorios", "
    - ``io_type``:tipo de comunicación 0-IO 1-UDP
    - ``scanSpeed``:velocidad de escaneo
    - ``scanWidth``:ancho de escaneo
    - ``peakPower``:potencia pico
    - ``dutyCycle``:ciclo de trabajo
    - ``Freq``:frecuencia
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Configurar el puerto DO extendido de habilitación de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingEnableExtDoNum(self, ctrlModeDONum)``"
    "Descripción", "Configurar el puerto DO extendido de habilitación de la soldadora láser"
    "Parámetros obligatorios", "
    - ``ctrlModeDONum``:número de puerto DO extendido de habilitación de la soldadora láser
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Configurar el puerto DO extendido de inicio de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingStartExtDoNum(self, ctrlModeDONum)``"
    "Descripción", "Configurar el IO extendido de la soldadora láser, puerto DO de inicio"
    "Parámetros obligatorios", "
    - ``ctrlModeDONum``:número de puerto DO extendido de inicio (emisión/recepción de luz) de la soldadora láser
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Configurar el puerto DO extendido de restablecimiento de fallos de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingErrResetExtDoNum(self, ctrlModeDONum)``"
    "Descripción", "Configurar el IO extendido de la soldadora láser, puerto DO de restablecimiento de fallos"
    "Parámetros obligatorios", "
    - ``ctrlModeDONum``:número de puerto DO extendido de restablecimiento de fallos de la soldadora láser
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Configurar el puerto DI extendido del estado de funcionamiento (estado de emisión de luz) de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingRunningStateExtDiNum(self, diNum)``"
    "Descripción", "Configurar el puerto DI extendido del estado de funcionamiento (estado de emisión de luz) de la soldadora láser"
    "Parámetros obligatorios", "
    - ``diNum``:configurar el puerto DI extendido del estado de funcionamiento (estado de emisión de luz) de la soldadora láser
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Configurar el puerto DI extendido del estado de fallo de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingErrStateExtDiNum(self, diNum)``"
    "Descripción", "Configurar el puerto DI extendido del estado de fallo de la soldadora láser"
    "Parámetros obligatorios", "
    - ``diNum``:configurar el puerto DI extendido del estado de fallo de la soldadora láser
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de soldadura láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from time import sleep
    from fairino import Robot
    import time

    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')

    def testLsaerWeld():
        robot.ExtDevLoadUDPDriver()
        time.sleep(1)

        robot.SetLaserWeldingParam(num = 3, scanSpeed = 2000, scanWidth = 3, peakPower = 1500, dutyCycle = 100, Freq = 1000, io_type=1)
        robot.SetLaserWeldingStartExtDoNum(ctrlModeDONum=1)

        robot.Mode(0)
        time.sleep(1)

        desc_pos1 = [-303.721, -206.960, 297.105, 152.209, 19.857, 109.166]
        desc_pos2 = [-301.575, -254.888, 284.786, 155.919, 26.946, 111.629]
        desc_safe = [-344.386, -280.830, 435.073, 173.835, 15.333, 124.931]
        jointPos1 = [9.827, -99.740, 120.088, -78.900, -77.241, -17.904]
        jointPos2 = [15.251, -96.456, 120.138, -84.664, -68.542, -17.843]
        jointSafe = [19.142, -98.078, 101.493, -83.078, -77.070, -17.794]

        error = robot.MoveL(desc_pos=desc_pos1,joint_pos=jointPos1, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)
        robot.SetLaserWeldingStartEnd(1, io_type=1, max_waittime=10000)

        error = robot.MoveL(desc_pos=desc_pos2, joint_pos=jointPos2, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)
        robot.SetLaserWeldingStartEnd(0, io_type=1, max_waittime=10000)

        error = robot.MoveL(desc_pos=desc_safe, joint_pos=jointSafe, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)

        robot.Mode(1)
        time.sleep(1)

        # Cerrar conexión
        robot.CloseRPC()
        time.sleep(1)

    # Llamar a la función de prueba
    testLsaerWeld()

Establecer el retorno al punto cero del ciclo al final de la oscilación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWeaveBackCenterConfig(self, flag)``"
    "Descripción", "Establecer el retorno al punto cero del ciclo al final de la oscilación"
    "Parámetros obligatorios", "
    - ``flag``: si volver al punto cero del ciclo al final de la oscilación；0-no volver al punto cero del ciclo；1-volver al punto cero del ciclo
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"    

Obtener los parámetros de retorno al punto cero del ciclo al final de la oscilación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWeaveBackCenterConfig(self)``"
    "Descripción", "Obtener los parámetros de retorno al punto cero del ciclo al final de la oscilación"
    "Parámetros obligatorios", "
    - ``flag``: si volver al punto cero del ciclo al final de la oscilación；0-no volver al punto cero del ciclo；1-volver al punto cero del ciclo
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"   

Ejemplo de código de retorno al punto cero del ciclo al final de la oscilación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        def callback(src_type, count, cmd_id, data_len, content):
            print(" cmd_id={} count={} data_len={} content={}".format(cmd_id, count, data_len, content))
            return 0

        robot.SetUDPCmdRpyCallback(callback)

        j1 = [9.000, -66.067, 67.706, -103.217, -90.151, 100.669]
        j2 = [-4.660, -107.973, 103.734, -76.214, -89.999, 90.886]
        j3 = [-36.762, -77.380, 91.364, -127.159, -90.024, 54.833]
        j4 = [-62.875, -89.460, 86.437, -77.030, -90.012, 31.539]

    
        desc_pos1 = [-654.129, -235.344, 246.543, 6.010, -11.535, -176.787]
        desc_pos2 = [-273.710, -100.871, 280.935, 5.692, 9.522, 179.512]
        desc_pos3 = [-566.093, 311.278, 215.008, -10.453, -17.486, -174.209]
        desc_pos4 = [-246.558, 328.240, 292.173, 13.912, 4.437, -179.067]

        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
        epos = [0.0, 0.0, 0.0, 0.0]

        tool = 2
        user = 0
        vel = 100.0
        acc = 100.0
        ovl = 20.0
        oacc = 100.0
        blendT = 0.0
        blendR = 0.0
        flag = 0
        search = 0
        blendMode = 0
        velAccMode = 0

        robot.SetSpeed(1)

        robot.WeaveEnd(0)

        rtn = robot.SetWeaveBackCenterConfig(1)
        print(f"SetWeaveBackCenterConfig rtn is {rtn}")

        rtn, weaveBackConfig = robot.GetWeaveBackCenterConfig()
        print(f"GetWeavebackCenterConfig {weaveBackConfig}")

        rtn = robot.MoveJ(joint_pos=j1, desc_pos=desc_pos1, tool=tool, user=user,
                        vel=vel, acc=acc, ovl=100.0, exaxis_pos=epos,
                        blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
        print(f"MoveJ rtn is {rtn}")

        robot.WeaveStart(0)

        robot.NewSplineStart(0, 6000)

        rtn = robot.NewSplinePoint(joint_pos=j1, desc_pos=desc_pos1, tool=tool, user=user,lastFlag=0,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=0)
        print(f"NewSplinePoint 1 rtn is {rtn}")

        rtn = robot.NewSplinePoint(joint_pos=j2, desc_pos=desc_pos2, tool=tool, user=user,lastFlag=0,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=0)
        print(f"NewSplinePoint 2 rtn is {rtn}")

        rtn = robot.NewSplinePoint(joint_pos=j3, desc_pos=desc_pos3, tool=tool, user=user,lastFlag=0,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=0)
        print(f"NewSplinePoint 3 rtn is {rtn}")

        rtn = robot.NewSplinePoint(joint_pos=j4, desc_pos=desc_pos4, tool=tool, user=user,lastFlag=1,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=1)
        print(f"NewSplinePoint 4 rtn is {rtn}")

        robot.NewSplineEnd()

        robot.CloseRPC()


    if __name__ == "__main__":
        main()