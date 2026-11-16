Uso del programa WebAPP del robot
==================================

.. toctree:: 
    :maxdepth: 5

Establecer la carga automática del programa de trabajo predeterminado al arrancar
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadDefaultProgConfig(flag,program_name)``"
    "Descripción", "Establecer la carga automática del programa de trabajo predeterminado al arrancar"
    "Parámetros obligatorios", "
    - ``flag``：1-cargar automáticamente el programa predeterminado al arrancar，0-no cargar automáticamente el programa predeterminado
    - ``program_name``：nombre y ruta del programa de trabajo，como movej.lua"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Cargar el programa de trabajo especificado
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramLoad(program_name)``"
    "Descripción", "Cargar el programa de trabajo especificado"
    "Parámetros obligatorios", "- ``program_name``：nombre y ruta del programa de trabajo，como movej.lua"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el nombre del programa de trabajo cargado
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLoadedProgram()``"
    "Descripción", "Obtener el nombre del programa de trabajo cargado"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``program_name``：nombre del programa de trabajo cargado"

Obtener el número de línea de ejecución del programa de trabajo actual del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetCurrentLine()``"
    "Descripción", "Obtener el número de línea de ejecución del programa de trabajo actual del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``line_num``：número de línea de ejecución del programa de trabajo actual del robot"

Ejecutar el programa de trabajo cargado actualmente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramRun()``"
    "Descripción", "Ejecutar el programa de trabajo cargado actualmente"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Pausar el programa de trabajo en ejecución actual
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramPause()``"
    "Descripción", "Pausar el programa de trabajo en ejecución actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Reanudar el programa de trabajo pausado actual
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramResume()``"
    "Descripción", "Reanudar el programa de trabajo pausado actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Terminar el programa de trabajo en ejecución actual
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramStop()``"
    "Descripción", "Terminar el programa de trabajo en ejecución actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el estado de ejecución del programa de trabajo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetProgramState()``"
    "Descripción", "Obtener el estado de ejecución del programa de trabajo del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``state``:estado de ejecución del programa de trabajo del robot，1-programa detenido o sin programa en ejecución，2-programa en ejecución，3-programa en pausa"

Ejemplo de código de operación del programa LUA del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    program_name = "test0610.lua"
    loaded_name = ""
    state = 0
    line = 0
    robot.Mode(0)
    robot.LoadDefaultProgConfig(0, program_name)
    robot.ProgramLoad(program_name)
    robot.ProgramRun()
    time.sleep(1)
    robot.ProgramPause()
    error,state = robot.GetProgramState()
    print(f"program state:{state}")
    error,line = robot.GetCurrentLine()
    print(f"current line:{line}")
    error,loaded_name = robot.GetLoadedProgram()
    print(f"program name:{loaded_name}")
    time.sleep(1)
    robot.ProgramResume()
    time.sleep(1)
    robot.ProgramStop()
    time.sleep(1)
    robot.CloseRPC()

Descargar archivo Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``LuaDownLoad(fileName, savePath)``"
    "Descripción", "Descargar archivo Lua"
    "Parámetros obligatorios", "- ``fileName``：nombre del archivo lua a descargar，como “test.lua”
    - ``savePath``：ruta local de guardado del archivo，como “D://Down/”"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Eliminar archivo Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LuaDelete(fileName)``"
    "Descripción", "Eliminar archivo Lua"
    "Parámetros obligatorios", "- ``fileName``：nombre del archivo lua a eliminar “test.lua”"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el nombre de todos los archivos lua actuales
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLuaList()``"
    "Descripción", "Obtener el nombre de todos los archivos lua actuales"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``lua_num``：cantidad de archivos lua
    - ``luaNames``：lista de nombres de archivos lua"

Subir archivo Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LuaUpload(filePath)``"
    "Descripción", "Subir archivo Lua"
    "Parámetros obligatorios", "- ``filePath``：nombre de ruta completo del archivo a subir  como D://test/test.lua"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - errorStr(devuelto si el archivo lua contiene errores)"

Ejemplo de código de carga y descarga de archivos LUA del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    rtn,lua_num,luaNames = robot.GetLuaList()
    print(f"res is:{rtn}")
    print(f"size is:{lua_num}")
    for name in luaNames:
        print(name)
    rtn = robot.LuaDownLoad("test0610.lua", "D://zDOWN/")
    print(f"LuaDownLoad rtn is:{rtn}")
    rtn = robot.LuaUpload("D://zDOWN/test0610.lua")
    print(f"LuaUpload rtn is:{rtn}")
    rtn = robot.LuaDelete("test0610.lua")
    print(f"LuaDelete rtn is:{rtn}")
    robot.CloseRPC()