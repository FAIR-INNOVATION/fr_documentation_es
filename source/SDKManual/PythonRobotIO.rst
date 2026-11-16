IO del robot
============

.. toctree:: 
    :maxdepth: 5

Establecer la salida digital de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDO(id, status, smooth=0, block=0)``"
    "Descripción", "Establecer la salida digital de la caja de control"
    "Parámetros obligatorios", "-  ``id``:número de io, rango [0~15];
    - ``status``:0-desactivado, 1-activado;"
    "Parámetros predeterminados", "- ``smooth``:0-sin suavizado, 1-suavizado, valor predeterminado 0;
    - ``block``:0-bloqueante, 1-no bloqueante, valor predeterminado 0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la salida digital de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolDO (id, status, smooth=0, block=0)``"
    "Descripción", "Establecer la salida digital de la herramienta"
    "Parámetros obligatorios", "-  ``id``:número de io, rango [0~1];
    - ``status``:0-desactivado, 1-activado;"
    "Parámetros predeterminados", "- ``smooth``:0-sin suavizado, 1-suavizado;
    - ``block``:0-bloqueante, 1-no bloqueante."
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la salida analógica de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAO(id,value,block=0)``"
    "Descripción", "Establecer la salida analógica de la caja de control"
    "Parámetros obligatorios", "- ``id``:número de io, rango [0~1];
    - ``value``:porcentaje del valor de corriente o voltaje, rango [0~100%] corresponde al valor de corriente [0~20mA] o voltaje [0~10V];"
    "Parámetros predeterminados", "- ``block``:[0]-bloqueante, [1]-no bloqueante, valor predeterminado 0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la salida analógica de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolAO(id,value,block=0)``"
    "Descripción", "Establecer la salida analógica de la herramienta"
    "Parámetros obligatorios", "- ``id``:número de io, rango [0];
    - ``value``:porcentaje del valor de corriente o voltaje, rango [0~100%] corresponde al valor de corriente [0~20mA] o voltaje [0~10V];"
    "Parámetros predeterminados", "- ``block``:[0]-bloqueante, [1]-no bloqueante, valor predeterminado 0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de establecimiento de salidas digitales y analógicas
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    status = 1
    smooth = 0  
    block = 0 
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3) 
    status = 0 
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 1
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1) 
    status = 0 
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    for i in range(100):
        robot.SetAO(0, i, block)
        time.sleep(0.03)
    for i in range(100):
        robot.SetToolAO(0, i, block)
        time.sleep(0.03)
    robot.CloseRPC()

Obtener la entrada digital de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDI(id, block=0)``"
    "Descripción", "Obtener la entrada digital de la caja de control"
    "Parámetros obligatorios", "- ``id``:número de io, rango [0~15];"
    "Parámetros predeterminados", "- ``block``:0-bloqueante, 1-no bloqueante, valor predeterminado 0"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``di``: 0-nivel bajo, 1-nivel alto"

Obtener la entrada digital de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolDI(id, block=0)``"
    "Descripción", "Obtener la entrada digital de la herramienta"
    "Parámetros obligatorios", "- ``id``:número de io, rango [0~1];"
    "Parámetros predeterminados", "- ``block``:0-bloqueante, 1-no bloqueante, valor predeterminado 0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode
    - ``di``: 0-nivel bajo, 1-nivel alto"

Obtener la entrada analógica de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAI(id, block = 0)``"
    "Descripción", "Obtener la entrada analógica de la caja de control"
    "Parámetros obligatorios", "- ``id``:número de io, rango [0~1];"
    "Parámetros predeterminados", "- ``block``:0-bloqueante, 1-no bloqueante, valor predeterminado 0 "
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``value``: porcentaje del valor de corriente o voltaje de entrada, rango [0~100] corresponde al valor de corriente [0~20mA] o voltaje [0~10V]"

Obtener la entrada analógica de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolAI(id, block = 0)``"
    "Descripción", "Obtener la entrada analógica del extremo"
    "Parámetros obligatorios", "- ``id``:número de io, rango [0];"
    "Parámetros predeterminados", "- ``block``:0-bloqueante, 1-no bloqueante, valor predeterminado 0"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``value``: porcentaje del valor de corriente o voltaje de entrada, rango [0~100] corresponde al valor de corriente [0~20mA] o voltaje [0~10V]"

Obtener el estado del botón de registro de puntos del extremo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxlePointRecordBtnState()``"
    "Descripción", "Obtener el estado del botón de registro de puntos del extremo del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``buttonstatus``: Estado del botón, 0-pulsado, 1-liberado"

Obtener el estado de salida DO del extremo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolDO()``"
    "Descripción", "Obtener el estado de salida DO del extremo del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``do_state``: Estado de salida DO, do0~do1 corresponden a bit1~bit2, comenzando desde bit0"

Obtener el estado de salida DO del controlador del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDO()``"
    "Descripción", "Obtener el estado de salida DO del controlador del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``do_state_h``: Estado de salida DO, co0~co7 corresponden a bit0~bit7; do_state_l Estado de salida DO, do0~do7 corresponden a bit0~bit7"

Ejemplo de código de obtención del estado DI y DO del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    block = 0 
    error,di = robot.GetDI(0, block)
    print(f"di0: {di}")
    error,tool_di = robot.GetToolDI(1, block)
    print(f"tool_di1: {tool_di}")
    error,ai = robot.GetAI(0, block)
    print(f"ai0: {ai:.2f}") 
    error,tool_ai = robot.GetToolAI(0, block)
    print(f"tool_ai0: {tool_ai:.2f}")
    error,button_state = robot.GetAxlePointRecordBtnState()
    print(f"_button_state is: {button_state}")
    error,tool_do_state = robot.GetToolDO()
    print(f"tool DO state: {tool_do_state}")
    error,[do_state_h, do_state_l] = robot.GetDO()
    print(f"DO state hight  : {do_state_h}")
    print(f"DO state low : {do_state_l}")
    robot.CloseRPC()

Esperar la entrada digital de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitDI(id,status,maxtime,opt)``"
    "Descripción", "Esperar la entrada digital de la caja de control"
    "Parámetros obligatorios", "- ``id``:número de io, rango [0~15];
    - ``status``:0-desactivado, 1-activado;
    - ``maxtime``:tiempo máximo de espera, unidad [ms];
    - ``opt``:estrategia tras el tiempo de espera, 0-el programa se detiene y muestra el tiempo de espera agotado, 1-ignorar el tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Esperar múltiples entradas digitales de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitMultiDI(mode,id,status,maxtime,opt)``"
    "Descripción", "Esperar múltiples entradas digitales de la caja de control"
    "Parámetros obligatorios", "- ``mode``:[0]-múltiples en AND, [1]-múltiples en OR;
    - ``id``:número de io, bit0~bit7 corresponden a DI0~DI7, bit8~bit15 corresponden a CI0~CI7;
    - ``status``:bit0~bit7 corresponden al estado de DI0~DI7, bit8~bit15 corresponden al estado de los bits de estado de CI0~CI7, [0]-desactivado, [1]-activado;
    - ``maxtime``:tiempo máximo de espera, unidad [ms];
    - ``opt``:estrategia tras el tiempo de espera, 0-el programa se detiene y muestra el tiempo de espera agotado, 1-ignorar el tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre."
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Esperar la entrada digital de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitToolDI(id,status,maxtime,opt)``"
    "Descripción", "Esperar la entrada digital del extremo"
    "Parámetros obligatorios", "- ``id``:número de io, rango [0~1];
    - ``status``:0-desactivado, 1-activado;
    - ``maxtime``:tiempo máximo de espera, unidad [ms];
    - ``opt``:estrategia tras el tiempo de espera, 0-el programa se detiene y muestra el tiempo de espera agotado, 1-ignorar el tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Esperar la entrada analógica de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitAI(id,sign,value,maxtime,opt)``"
    "Descripción", "Esperar la entrada analógica de la caja de control"
    "Parámetros obligatorios", "- ``id``:número de io, rango [0~1];
    - ``sign``:0-mayor que, 1-menor que
    - ``value``:porcentaje del valor de corriente o voltaje de entrada, rango [0~100] corresponde al valor de corriente [0~20mA] o voltaje [0~10V];
    - ``maxtime``:tiempo máximo de espera, unidad [ms];
    - ``opt``:estrategia tras el tiempo de espera, 0-el programa se detiene y muestra el tiempo de espera agotado, 1-ignorar el tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Esperar la entrada analógica de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitToolAI(id,sign,value,maxtime,opt)``"
    "Descripción", "Esperar la entrada analógica del extremo"
    "Parámetros obligatorios", "- ``id``:número de io, rango [0];
    - ``sign``:0-mayor que, 1-menor que
    - ``value``:porcentaje del valor de corriente o voltaje de entrada, rango [0~100] corresponde al valor de corriente [0~20mA] o voltaje [0~10V];
    - ``maxtime``:tiempo máximo de espera, unidad [ms];
    - ``opt``:estrategia tras el tiempo de espera, 0-el programa se detiene y muestra el tiempo de espera agotado, 1-ignorar el tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de espera de señales de entrada digitales y analógicas de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    status = 1
    smooth = 0
    block = 0
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 0
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 1
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    status = 0
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    for i in range(100):
        robot.SetAO(0, i, block)
        time.sleep(0.03)
    for i in range(100):
        robot.SetToolAO(0, i, block)
        time.sleep(0.03)
    block = 0
    error,di = robot.GetDI(0, block)
    print(f"di0: {di}")
    error,tool_di = robot.GetToolDI(1, block)
    print(f"tool_di1: {tool_di}")
    error,ai = robot.GetAI(0, block)
    print(f"ai0: {ai:.2f}")
    error,tool_ai = robot.GetToolAI(0, block)
    print(f"tool_ai0: {tool_ai:.2f}")
    error,button_state = robot.GetAxlePointRecordBtnState()
    print(f"_button_state is: {button_state}")
    error,tool_do_state = robot.GetToolDO()
    print(f"tool DO state: {tool_do_state}")
    error,[do_state_h, do_state_l] = robot.GetDO()
    print(f"DO state hight  : {do_state_h}")
    print(f"DO state low : {do_state_l}")
    rtn = robot.WaitDI(0, 1, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitMultiDI(1, 3, 3, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitToolDI(1, 1, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitAI(0, 0, 50, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitToolAI(0, 0, 50, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    robot.CloseRPC()

Establecer si la salida DO de la caja de control se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetCtlBoxDO(resetFlag,reloadFlag)``"
    "Descripción", "Establecer si la salida DO de la caja de control se reinicia tras detener/pausar"
    "Parámetros obligatorios", "
    - ``resetFlag``：0-no reiniciar; 1-reiniciar
    - ``reloadFlag``：Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer si la salida AO de la caja de control se reinicia tras detener/pausar
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetCtlBoxDO(resetFlag,reloadFlag)``"
    "Descripción", "Establecer si la salida AO de la caja de control se reinicia tras detener/pausar"
    "Parámetros obligatorios", "
    - ``resetFlag``：0-no reiniciar; 1-reiniciar
    - ``reloadFlag``：Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer si la salida DO de la herramienta del extremo se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetAxleDO(resetFlag,reloadFlag)``"
    "Descripción", "Establecer si la salida DO de la herramienta del extremo se reinicia tras detener/pausar"
    "Parámetros obligatorios", "
    - ``resetFlag``：0-no reiniciar; 1-reiniciar
    - ``reloadFlag``：Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer si la salida AO de la herramienta del extremo se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetAxleAO(resetFlag,reloadFlag)``"
    "Descripción", "Establecer si la salida AO de la herramienta del extremo se reinicia tras detener/pausar"
    "Parámetros obligatorios", "
    - ``resetFlag``：0-no reiniciar; 1-reiniciar
    - ``reloadFlag``：Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer si la DO extendida se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetExtDO (resetFlag,reloadFlag)``"
    "Descripción", "Establecer si la DO extendida se reinicia tras detener/pausar"
    "Parámetros obligatorios", "
    - ``resetFlag``：0-no reiniciar; 1-reiniciar
    - ``reloadFlag``：Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer si la AO extendida se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetExtAO (resetFlag,reloadFlag)``"
    "Descripción", "Establecer si la AO extendida se reinicia tras detener/pausar"
    "Parámetros obligatorios", "
    - ``resetFlag``：0-no reiniciar; 1-reiniciar
    - ``reloadFlag``：Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer si la salida de SmartTool se reinicia tras detener/pausar
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetSmartToolDO(resetFlag,reloadFlag)``"
    "Descripción", "Establecer si la salida de SmartTool se reinicia tras detener/pausar"
    "Parámetros obligatorios", "
    - ``resetFlag``：0-no reiniciar; 1-reiniciar
    - ``reloadFlag``：Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Ejemplo de código de reinicio de salida tras detener/pausar el programa LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    for i in range(16):
        robot.SetDO(i, 1, 0, 0)
        time.sleep(0.2)
    resetFlag = 0
    resumeReloadFlag = 0
    rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetCtlBoxAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetAxleDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetAxleAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetExtDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetExtAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetSmartToolDO(resetFlag, resumeReloadFlag)
    robot.ProgramLoad("test.lua")
    robot.ProgramRun()
    time.sleep(2)
    robot.PauseMotion()
    time.sleep(2)
    robot.ResumeMotion()
    time.sleep(2)
    robot.CloseRPC()
    return 0
    
Establecer la función del puerto CI configurable
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDIConfig(config)``"
    "Descripción", "Establecer la función del puerto CI configurable"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de códigos de función CI0-CI7, 0-ninguna;1-inicio de arco exitoso;2-máquina de soldar preparada;3-detección de cinta transportadora;4-pausa;5-reanudar;6-inicio;7-parada;
      8-pausa/reanudar;9-inicio/parada;10-arrastre con pedal;11-moverse al origen de trabajo;12-conmutación manual/automático;
      13-búsqueda de posición de alambre de soldadura exitosa;14-interrupción de movimiento;15-iniciar programa principal;16-iniciar rebobinado;17-confirmación de inicio;
      18-señal de detección fotoeléctrica X;19-señal de detección fotoeléctrica Y;20-señal de entrada de parada de emergencia externa 1;21-señal de entrada de parada de emergencia externa 2;
      22-modo de reducción de nivel uno;23-modo de reducción de nivel dos;24-modo de reducción de nivel tres (parada);25-reanudar soldadura;26-terminar soldadura;
      27-activar arrastre asistido;28-desactivar arrastre asistido;29-activar/desactivar arrastre asistido;30-borrar todos los errores;
      31-conmutación manual/automático (nivel alto/bajo);32-habilitar;33-deshabilitar;34-habilitar/deshabilitar (flanco de subida/bajada);35-inicio/fin de seguimiento de punto fijo;
      36-entrar en movimiento de velocidad de seguridad;37-bloqueo de arrastre del bucle de corriente;38-bloqueo asistido por sensor de fuerza"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "
    
Obtener la función del puerto CI configurable de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDIConfig()``"
    "Descripción", "Obtener la función del puerto CI configurable de la caja de control"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de códigos de función CI0-CI7, 0-ninguna;1-inicio de arco exitoso;2-máquina de soldar preparada;3-detección de cinta transportadora;4-pausa;5-reanudar;6-inicio;7-parada;
      8-pausa/reanudar;9-inicio/parada;10-arrastre con pedal;11-moverse al origen de trabajo;12-conmutación manual/automático;
      13-búsqueda de posición de alambre de soldadura exitosa;14-interrupción de movimiento;15-iniciar programa principal;16-iniciar rebobinado;17-confirmación de inicio;
      18-señal de detección fotoeléctrica X;19-señal de detección fotoeléctrica Y;20-señal de entrada de parada de emergencia externa 1;21-señal de entrada de parada de emergencia externa 2;
      22-modo de reducción de nivel uno;23-modo de reducción de nivel dos;24-modo de reducción de nivel tres (parada);25-reanudar soldadura;26-terminar soldadura;
      27-activar arrastre asistido;28-desactivar arrastre asistido;29-activar/desactivar arrastre asistido;30-borrar todos los errores;
      31-conmutación manual/automático (nivel alto/bajo);32-habilitar;33-deshabilitar;34-habilitar/deshabilitar (flanco de subida/bajada);35-inicio/fin de seguimiento de punto fijo
      36-entrar en movimiento de velocidad de seguridad;37-bloqueo de arrastre del bucle de corriente;38-bloqueo asistido por sensor de fuerza
      201-señal de entrada de parada de emergencia externa 1-doble canal; 202-señal de entrada de parada de emergencia externa 2-doble canal; 203-modo de reducción de nivel uno-doble canal;
      204-modo de reducción de nivel dos-doble canal; 205-modo de reducción de nivel tres-doble canal; 206-parada normal-doble canal; 207-muro de seguridad 1-doble canal; 208-muro de seguridad 2-doble canal;
      209-muro de seguridad 3-doble canal; 210-muro de seguridad 4-doble canal; 211-muro de seguridad 5-doble canal; 212-muro de seguridad 6-doble canal; 213-muro de seguridad 7-doble canal;
      214-muro de seguridad 8-doble canal; 215-reinicio de parada de seguridad-doble canal;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "
    
Establecer la función del puerto CO configurable
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDOConfig(config)``"
    "Descripción", "Establecer la función del puerto CO configurable"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de códigos de función CO0-CO7,0-ninguna;1-error del robot;2-robot en movimiento;3-inicio/parada de pulverización;4-limpieza de pistola de pulverización;5-señal de suministro de gas;6-señal de inicio de arco;7-alimentación de alambre por impulsos;
      8-alimentación de alambre inversa;9-entrada JOB 1;10-entrada JOB 2;11-entrada JOB 3;12-control de inicio/parada de cinta transportadora;13-robot en pausa;14-llegada al origen de trabajo;
      15-llegada a la zona de interferencia;16-control de inicio/parada de búsqueda de posición de alambre de soldadura;17-inicio del robot completado;18-inicio/parada del programa;19-modo automático/manual;20-señal de salida de parada de emergencia 1-seguridad;
      21-señal de salida de parada de emergencia 2-seguridad;22-ejecución/parada del programa de script LUA;23-salida de estado de seguridad-seguridad;24-salida de estado de parada protectora-seguridad;
      25-robot en movimiento-seguridad;26-modo de reducción del robot-seguridad;27-modo no reducido del robot-seguridad;28-robot no detenido;29-error del robot-error de punto de instrucción;
      30-error del robot-error del accionamiento;31-error del robot-error de fuera del límite suave;32-error del robot-error de colisión;33-error del robot-error del número de esclavos activos;
      34-error del robot-error de esclavo;35-error del robot-error de IO;36-error del robot-error de pinza;37-error del robot-error de archivo;38-error del robot-error de pose singular;
      39-error del robot-error de comunicación del accionamiento;40-error del robot-error de parámetro;41-error del robot-error de eje externo fuera del límite suave;42-advertencia del robot-advertencia;
      43-advertencia del robot-advertencia de puerta de seguridad;44-advertencia del robot-advertencia de movimiento;45-advertencia del robot-advertencia de zona de interferencia;46-advertencia del robot-advertencia de muro de seguridad;
      47-estado de habilitación;48-elevación automática en curso tras desconexión;49-advertencia de interferencia del cubo 1;50-advertencia de interferencia del cubo 2;51-advertencia de interferencia del cubo 3;52-advertencia de interferencia del cubo 4;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "
    
Obtener la función del puerto CO configurable
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDOConfig()``"
    "Descripción", "Obtener la función del puerto CO configurable"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de códigos de función CO0-CO7,0-ninguna;1-error del robot;2-robot en movimiento;3-inicio/parada de pulverización;4-limpieza de pistola de pulverización;5-señal de suministro de gas;6-señal de inicio de arco;7-alimentación de alambre por impulsos;
      8-alimentación de alambre inversa;9-entrada JOB 1;10-entrada JOB 2;11-entrada JOB 3;12-control de inicio/parada de cinta transportadora;13-robot en pausa;14-llegada al origen de trabajo;
      15-llegada a la zona de interferencia;16-control de inicio/parada de búsqueda de posición de alambre de soldadura;17-inicio del robot completado;18-inicio/parada del programa;19-modo automático/manual;20-señal de salida de parada de emergencia 1-seguridad;
      21-señal de salida de parada de emergencia 2-seguridad;22-ejecución/parada del programa de script LUA;23-salida de estado de seguridad-seguridad;24-salida de estado de parada protectora-seguridad;
      25-robot en movimiento-seguridad;26-modo de reducción del robot-seguridad;27-modo no reducido del robot-seguridad;28-robot no detenido;29-error del robot-error de punto de instrucción;
      30-error del robot-error del accionamiento;31-error del robot-error de fuera del límite suave;32-error del robot-error de colisión;33-error del robot-error del número de esclavos activos;
      34-error del robot-error de esclavo;35-error del robot-error de IO;36-error del robot-error de pinza;37-error del robot-error de archivo;38-error del robot-error de pose singular;
      39-error del robot-error de comunicación del accionamiento;40-error del robot-error de parámetro;41-error del robot-error de eje externo fuera del límite suave;42-advertencia del robot-advertencia;
      43-advertencia del robot-advertencia de puerta de seguridad;44-advertencia del robot-advertencia de movimiento;45-advertencia del robot-advertencia de zona de interferencia;46-advertencia del robot-advertencia de muro de seguridad;
      47-estado de habilitación;48-elevación automática en curso tras desconexión;49-advertencia de interferencia del cubo 1;50-advertencia de interferencia del cubo 2;51-advertencia de interferencia del cubo 3;52-advertencia de interferencia del cubo 4;
      201-señal de salida de parada de emergencia 1-doble canal; 202-señal de salida de parada de emergencia 2-doble canal; 203-salida de estado de seguridad-doble canal; 204-salida de estado de parada protectora-doble canal; 205-robot en movimiento-doble canal;
      206-modo de reducción del robot-doble canal; 207-modo no reducido del robot-doble canal;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "
    
Establecer la función del puerto End-CI configurable del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolDIConfig(config)``"
    "Descripción", "Establecer la función del puerto End-CI configurable del extremo"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de códigos de función End CI0-CI1,0-ninguna;1-interruptor de la herramienta de enseñanza por arrastre;2-señal de registro de punto;3-conmutación manual/automático (señal de pulso);4-inicio/parada del registro TPD;5-pausar movimiento;
      6-reanudar movimiento;7-inicio;8-parada;9-pausa/reanudar;10-inicio/parada;11-activar arrastre asistido por sensor de fuerza;12-desactivar arrastre asistido por sensor de fuerza;
      13-activar/desactivar arrastre asistido por sensor de fuerza;14-señal de detección láser X;15-señal de detección láser Y;16-movimiento PTP al origen de trabajo;17-interrupción de movimiento, detener el movimiento actual según la señal;
      18-iniciar programa principal;19-iniciar rebobinado;20-confirmación de inicio;21-reanudar soldadura;22-terminar soldadura;23-borrar errores;24-conmutación manual/automático (nivel alto/bajo)
      25-habilitar;26-deshabilitar;27-habilitar/deshabilitar;28-señal de inicio/parada del seguimiento servo láser;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "
    
Obtener la función del puerto End-CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolDIConfig()``"
    "Descripción", "Obtener la función del puerto End-CI configurable del extremo"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de códigos de función End CI0-CI1,0-ninguna;1-interruptor de la herramienta de enseñanza por arrastre;2-señal de registro de punto;3-conmutación manual/automático (señal de pulso);4-inicio/parada del registro TPD;5-pausar movimiento;
      6-reanudar movimiento;7-inicio;8-parada;9-pausa/reanudar;10-inicio/parada;11-activar arrastre asistido por sensor de fuerza;12-desactivar arrastre asistido por sensor de fuerza;
      13-activar/desactivar arrastre asistido por sensor de fuerza;14-señal de detección láser X;15-señal de detección láser Y;16-movimiento PTP al origen de trabajo;17-interrupción de movimiento, detener el movimiento actual según la señal;
      18-iniciar programa principal;19-iniciar rebobinado;20-confirmación de inicio;21-reanudar soldadura;22-terminar soldadura;23-borrar errores;24-conmutación manual/automático (nivel alto/bajo)
      25-habilitar;26-deshabilitar;27-habilitar/deshabilitar;28-señal de inicio/parada del seguimiento servo láser;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "
    
Establecer el estado válido del CI configurable de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDIConfigLevel(config)``"
    "Descripción", "Establecer el estado válido del CI configurable de la caja de control"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de estados válidos de los puertos CI0-CI7; 0-nivel alto válido; 1-nivel bajo válido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Obtener el estado válido del CI configurable de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDIConfigLevel()``"
    "Descripción", "Obtener el estado válido del CI configurable de la caja de control"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de estados válidos de los puertos CI0-CI7; 0-nivel alto válido; 1-nivel bajo válido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Establecer el estado válido del CO configurable de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDOConfigLevel(config)``"
    "Descripción", "Establecer el estado válido del CO configurable de la caja de control"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de estados válidos de los puertos CO0-CO7; 0-nivel alto válido; 1-nivel bajo válido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Obtener el estado válido del CO configurable de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDOConfigLevel()``"
    "Descripción", "Obtener el estado válido del CO configurable de la caja de control"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de estados válidos de los puertos CO0-CO7; 0-nivel alto válido; 1-nivel bajo válido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Establecer el estado válido del CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolDIConfigLevel(config)``"
    "Descripción", "Establecer el estado válido del CI configurable del extremo"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de estados válidos de los puertos CI0-CI7; 0-nivel alto válido; 1-nivel bajo válido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Obtener el estado válido del CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolDIConfigLevel()``"
    "Descripción", "Obtener el estado válido del CI configurable del extremo"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de estados válidos de los puertos CI0-CI7; 0-nivel alto válido; 1-nivel bajo válido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Establecer el estado válido del DI estándar de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetStandardDILevel(config)``"
    "Descripción", "Establecer el estado válido del DI estándar de la caja de control"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de estados válidos de los puertos DI0-DI7; 0-nivel alto válido; 1-nivel bajo válido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Obtener el estado válido del DI estándar de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetStandardDILevel()``"
    "Descripción", "Obtener el estado válido del DI estándar de la caja de control"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de estados válidos de los puertos DI0-DI7; 0-nivel alto válido; 1-nivel bajo válido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Establecer el estado válido del DO estándar de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetStandardDOLevel(config)``"
    "Descripción", "Establecer el estado válido del DO estándar de la caja de control"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de estados válidos de los puertos DO0-DO7; 0-nivel alto válido; 1-nivel bajo válido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Obtener el estado válido del DO estándar de la caja de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetStandardDOLevel()``"
    "Descripción", "Obtener el estado válido del DO estándar de la caja de control"
    "Parámetros obligatorios", "
    - ``config``：Arreglo de estados válidos de los puertos DO0-DO7; 0-nivel alto válido; 1-nivel bajo válido"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Ejemplo de código SDK relacionado con la configuración de IO
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Establecer comunicación con el controlador del robot
    robot = Robot.RPC('192.168.58.2')


    def TestIOConfig(self):
        # Establecer y obtener la configuración de DI
        setDIConfig = [1, 2, 3, 4, 5, 6, 7, 8]
        getDIConfig = [0] * 8
        rtn = robot.SetDIConfig(setDIConfig)
        print(f"SetDIConfig rtn is {rtn}")
        rtn, getDIConfig = robot.GetDIConfig()
        print(f"GetDIConfig rtn is {rtn}, value is {getDIConfig[0]} {getDIConfig[1]} {getDIConfig[2]} {getDIConfig[3]} {getDIConfig[4]} {getDIConfig[5]} {getDIConfig[6]} {getDIConfig[7]}")

        # Establecer y obtener la configuración de DO
        setDOConfig = [9, 10, 11, 12, 13, 14, 15, 16]
        getDOConfig = [0] * 8
        rtn = robot.SetDOConfig(setDOConfig)
        print(f"SetDOConfig rtn is {rtn}")
        rtn, getDOConfig = robot.GetDOConfig()
        print(f"GetDOConfig rtn is {rtn}, value is {getDOConfig[0]} {getDOConfig[1]} {getDOConfig[2]} {getDOConfig[3]} {getDOConfig[4]} {getDOConfig[5]} {getDOConfig[6]} {getDOConfig[7]}")

        # Establecer y obtener la configuración de DI de la herramienta
        setToolDIConfig = [17, 18]
        getToolDIConfig = [0] * 2
        rtn = robot.SetToolDIConfig(setToolDIConfig)
        print(f"SetToolDIConfig rtn is {rtn}")
        rtn, getToolDIConfig = robot.GetToolDIConfig()
        print(f"GetToolDIConfig rtn is {rtn}, value is {getToolDIConfig[0]} {getToolDIConfig[1]}")

        # Establecer y obtener la configuración de nivel de DI (0: nivel bajo válido, 1: nivel alto válido)
        setDIConfigLevel = [1, 1, 1, 1, 0, 0, 0, 0]
        getDIConfigLevel = [0] * 8
        rtn = robot.SetDIConfigLevel(setDIConfigLevel)
        print(f"SetDIConfigLevel rtn is {rtn}")
        rtn, getDIConfigLevel = robot.GetDIConfigLevel()
        print(f"GetDIConfigLevel rtn is {rtn}, value is {getDIConfigLevel[0]} {getDIConfigLevel[1]} {getDIConfigLevel[2]} {getDIConfigLevel[3]} {getDIConfigLevel[4]} {getDIConfigLevel[5]} {getDIConfigLevel[6]} {getDIConfigLevel[7]}")

        # Establecer y obtener la configuración de nivel de DO (0: nivel bajo válido, 1: nivel alto válido)
        setDOConfigLevel = [0, 0, 0, 0, 1, 1, 1, 1]
        getDOConfigLevel = [0] * 8
        rtn = robot.SetDOConfigLevel(setDOConfigLevel)
        print(f"SetDOConfigLevel rtn is {rtn}")
        rtn, getDOConfigLevel = robot.GetDOConfigLevel()
        print(f"GetDOConfigLevel rtn is {rtn}, value is {getDOConfigLevel[0]} {getDOConfigLevel[1]} {getDOConfigLevel[2]} {getDOConfigLevel[3]} {getDOConfigLevel[4]} {getDOConfigLevel[5]} {getDOConfigLevel[6]} {getDOConfigLevel[7]}")

        # Establecer y obtener la configuración de nivel de DI de la herramienta
        setToolDIConfigLevel = [1, 0]
        getToolDIConfigLevel = [0] * 2
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel)
        print(f"SetToolDIConfigLevel rtn is {rtn}")
        rtn, getToolDIConfigLevel = robot.GetToolDIConfigLevel()
        print(f"GetToolDIConfigLevel rtn is {rtn}, value is {getToolDIConfigLevel[0]} {getToolDIConfigLevel[1]}")

        # Establecer y obtener la configuración de nivel de DI estándar
        setStandardDILevel = [1, 1, 1, 1, 0, 0, 0, 0]
        getStandardDILevel = [0] * 8
        rtn = robot.SetStandardDILevel(setStandardDILevel)
        print(f"SetStandardDILevel rtn is {rtn}")
        rtn, getStandardDILevel = robot.GetStandardDILevel()
        print(f"GetStandardDILevel rtn is {rtn}, value is {getStandardDILevel[0]} {getStandardDILevel[1]} {getStandardDILevel[2]} {getStandardDILevel[3]} {getStandardDILevel[4]} {getStandardDILevel[5]} {getStandardDILevel[6]} {getStandardDILevel[7]}")

        # Establecer y obtener la configuración de nivel de DO estándar
        setStandardDOLevel = [0, 0, 0, 0, 1, 1, 1, 1]
        getStandardDOLevel = [0] * 8
        rtn = robot.SetStandardDOLevel(setStandardDOLevel)
        print(f"SetStandardDOLevel rtn is {rtn}")
        rtn, getStandardDOLevel = robot.GetStandardDOLevel()
        print(f"GetStandsrdDOLevel rtn is {rtn}, value is {getStandardDOLevel[0]} {getStandardDOLevel[1]} {getStandardDOLevel[2]} {getStandardDOLevel[3]} {getStandardDOLevel[4]} {getStandardDOLevel[5]} {getStandardDOLevel[6]} {getStandardDOLevel[7]}")

        # Esperar 2 segundos
        time.sleep(2)

        # Cerrar la conexión
        robot.CloseRPC()
        time.sleep(1)

    # Llamar a la función de prueba
    TestIOConfig(robot)

Configuración de la función CI de doble canal de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSafetyDIConfig(self, ID, config)``"
    "Descripción", "Configuración de la función CI de doble canal de seguridad"
    "Parámetros obligatorios", "
    - ``ID``：ID de doble canal; [0-3]
    - ``config``：Configuración de función; 0-sin configuración; 201-señal de entrada de parada de emergencia externa 1; 202-señal de entrada de parada de emergencia externa 2; 203-modo de reducción de nivel uno; 204-modo de reducción de nivel dos; 205-modo de reducción de nivel tres;
                           206-parada normal; 207-muro de seguridad 1; 208-muro de seguridad 2; 209-muro de seguridad 3; 210-muro de seguridad 4; 211-muro de seguridad 5; 212-muro de seguridad 6; 213-muro de seguridad 7;
                           214-muro de seguridad 8; 215-reinicio de parada de seguridad;
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Configuración de la función CO de doble canal de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSafetyDOConfig(self, ID, config)``"
    "Descripción", "Configuración de la función CO de doble canal de seguridad"
    "Parámetros obligatorios", "
    - ``ID``：ID de doble canal; [0-3]
    - ``config``： Configuración de función; 0-sin configuración; 201-señal de salida de parada de emergencia 1; 202-señal de salida de parada de emergencia 2; 203-salida de estado de seguridad; 204-salida de estado de parada protectora; 205-robot en movimiento; 206-modo de reducción del robot; 207-modo no reducido del robot;
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de configuración de la función IO de doble canal de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        # Establecer comunicación con el controlador del robot
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        print("========== Prueba de configuración de IO de seguridad ==========")

        # ========== Establecer la configuración de DI de seguridad ==========
        print("\n--- Establecer la configuración de DI de seguridad ---")
        rtn = robot.SetSafetyDIConfig(0, 201)
        print(f"SetSafetyDIConfig(0, 201) rtn is {rtn}")

        rtn = robot.SetSafetyDIConfig(1, 202)
        print(f"SetSafetyDIConfig(1, 202) rtn is {rtn}")

        rtn = robot.SetSafetyDIConfig(2, 203)
        print(f"SetSafetyDIConfig(2, 203) rtn is {rtn}")

        rtn = robot.SetSafetyDIConfig(3, 204)
        print(f"SetSafetyDIConfig(3, 204) rtn is {rtn}")

        # Obtener la configuración de DI
        rtn, getDIConfig = robot.GetDIConfig()
        print(f"GetDIConfig rtn is {rtn}, value is {getDIConfig[0]} {getDIConfig[1]} {getDIConfig[2]} {getDIConfig[3]} {getDIConfig[4]} {getDIConfig[5]} {getDIConfig[6]} {getDIConfig[7]}")

        # ========== Borrar la configuración de DI de seguridad ==========
        print("\n--- Borrar la configuración de DI de seguridad ---")
        rtn = robot.SetSafetyDIConfig(0, 0)
        print(f"SetSafetyDIConfig(0, 0) rtn is {rtn}")

        rtn = robot.SetSafetyDIConfig(1, 0)
        print(f"SetSafetyDIConfig(1, 0) rtn is {rtn}")

        rtn = robot.SetSafetyDIConfig(2, 0)
        print(f"SetSafetyDIConfig(2, 0) rtn is {rtn}")

        rtn = robot.SetSafetyDIConfig(3, 0)
        print(f"SetSafetyDIConfig(3, 0) rtn is {rtn}")

        # Obtener la configuración de DI para verificar el borrado
        rtn, getDIConfig = robot.GetDIConfig()
        print(f"GetDIConfig rtn is {rtn}, value is {getDIConfig[0]} {getDIConfig[1]} {getDIConfig[2]} {getDIConfig[3]} {getDIConfig[4]} {getDIConfig[5]} {getDIConfig[6]} {getDIConfig[7]}")

        # ========== Establecer la configuración de DO de seguridad ==========
        print("\n--- Establecer la configuración de DO de seguridad ---")
        rtn = robot.SetSafetyDOConfig(0, 204)
        print(f"SetSafetyDOConfig(0, 204) rtn is {rtn}")

        rtn = robot.SetSafetyDOConfig(1, 205)
        print(f"SetSafetyDOConfig(1, 205) rtn is {rtn}")

        rtn = robot.SetSafetyDOConfig(2, 206)
        print(f"SetSafetyDOConfig(2, 206) rtn is {rtn}")

        rtn = robot.SetSafetyDOConfig(3, 207)
        print(f"SetSafetyDOConfig(3, 207) rtn is {rtn}")

        # Obtener la configuración de DO
        rtn, getDOConfig = robot.GetDOConfig()
        print(f"GetDOConfig rtn is {rtn}, value is {getDOConfig[0]} {getDOConfig[1]} {getDOConfig[2]} {getDOConfig[3]} {getDOConfig[4]} {getDOConfig[5]} {getDOConfig[6]} {getDOConfig[7]}")

        # ========== Borrar la configuración de DO de seguridad ==========
        print("\n--- Borrar la configuración de DO de seguridad ---")
        rtn = robot.SetSafetyDOConfig(0, 0)
        print(f"SetSafetyDOConfig(0, 0) rtn is {rtn}")

        rtn = robot.SetSafetyDOConfig(1, 0)
        print(f"SetSafetyDOConfig(1, 0) rtn is {rtn}")

        rtn = robot.SetSafetyDOConfig(2, 0)
        print(f"SetSafetyDOConfig(2, 0) rtn is {rtn}")

        rtn = robot.SetSafetyDOConfig(3, 0)
        print(f"SetSafetyDOConfig(3, 0) rtn is {rtn}")

        # Obtener la configuración de DO para verificar el borrado
        rtn, getDOConfig = robot.GetDOConfig()
        print(f"GetDOConfig rtn is {rtn}, value is {getDOConfig[0]} {getDOConfig[1]} {getDOConfig[2]} {getDOConfig[3]} {getDOConfig[4]} {getDOConfig[5]} {getDOConfig[6]} {getDOConfig[7]}")

        time.sleep(2)

        # Cerrar la conexión
        robot.CloseRPC()
        time.sleep(1)

        print("\n========== Prueba completada ==========")


    if __name__ == "__main__":
        main()