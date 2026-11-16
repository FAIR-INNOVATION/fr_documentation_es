Fundamentos del robot
=========================

.. toctree:: 
    :maxdepth: 5

Instanciar el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``RPC(self, ip, tls_enable, tls_cert_path)``"
    "Descripción", "Instanciar un objeto robot"
    "Parámetros obligatorios", "
    - ``ip``：Dirección IP del robot; la IP de fábrica predeterminada es `192.168.58.2`
    - ``tls_enable``：Si se habilita la comunicación cifrada (mTLS + DTLS); valor predeterminado False
    - ``tls_cert_path``：Ruta de la carpeta de certificados; el directorio debe contener: ca.crt / client.crt / client.key; obligatorio cuando tls_enable=True
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Éxito: devuelve un objeto robot
    - Fallo: el objeto creado se destruye"

Ejemplo de código de instanciación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    robot = Robot.RPC(
        '192.168.58.2',
        tls_enable=True,
        tls_cert_path=r"E:\certs"
    )

Cerrar la conexión RPC
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CloseRPC()``"
    "Descripción", "Cerrar la conexión RPC"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Ninguno"

Consultar el número de versión del SDK
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSDKVersion()``"
    "Descripción", "Consultar el número de versión del SDK"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo-errcode
    - ``sdk``：Número de versión del SDK, número de versión del controlador"

Obtener la IP del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetControllerIP()``"
    "Descripción", "Consultar la IP del controlador"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``ip``：IP del controlador"

Controlar la entrada o salida del modo de enseñanza por arrastre del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``DragTeachSwitch(state)``"
    "Descripción", "Controlar la entrada o salida del modo de enseñanza por arrastre del robot"
    "Parámetros obligatorios", "- ``state``：1-entrar en el modo de enseñanza por arrastre, 0-salir del modo de enseñanza por arrastre"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Consultar si el robot está en modo de arrastre
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``IsInDragTeach()``"
    "Descripción", "Consultar si el robot está en modo de enseñanza por arrastre"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``state``：0-modo no de enseñanza por arrastre, 1-modo de enseñanza por arrastre"

Controlar la habilitación o deshabilitación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``RobotEnable(state)``"
    "Descripción", "Controlar la habilitación o deshabilitación del robot"
    "Parámetros obligatorios", "- ``state``：1-habilitar, 0-deshabilitar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "


Controlar el cambio de modo manual/automático del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``Mode(state)``"
    "Descripción", "Controlar el cambio de modo manual/automático del robot"
    "Parámetros obligatorios", "- ``state``：0-modo automático, 1-modo manual"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error  éxito-0  fallo- errcode"

Apagar el sistema operativo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ShutDownRobotOS()``"
    "Descripción", "Apagar el sistema operativo del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Cambiar al modo manual de alta velocidad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``HiSpeedManualSwitch(self, state)``"
    "Descripción", "Cambiar al modo manual de alta velocidad"
    "Parámetros obligatorios", "
    - ``state``：0-salir de la alta velocidad manual; 1-entrar en la alta velocidad manual
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Inicializar los parámetros del registro
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoggerInit(output_model=1, file_path="", file_num=5)``"
    "Descripción", "Inicializar los parámetros del registro"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``output_model``：Modo de salida, 0-salida directa; 1-salida con búfer; 2-salida asíncrona, valor predeterminado 1
    - ``file_path``：Ruta de guardado del archivo + nombre; el nombre debe tener la forma xxx.log, por ejemplo /home/fr/linux/fairino.log. Por defecto es la ruta donde se ejecuta el programa; el nombre predeterminado es: fairino_year+month+data.log (por ejemplo: fairino_2024_03_13.log);
    - ``file_num``：Número de archivos de almacenamiento rotativo, de 1 a 20, valor predeterminado 5. Límite por archivo 50M;"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el nivel de filtrado del registro
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLoggerLevel(lvl=1)``"
    "Descripción", "Establecer el nivel de filtrado del registro"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``lvl``：Valor del nivel de filtrado; cuanto menor sea el valor, menos registros se emiten: 1-error, 2-warning, 3-inform, 4-debug; el valor predeterminado es 1"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de control básico del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    time.sleep(1)
    error,version = robot.GetSDKVersion()
    print(f"SDK version: {version}")
    error,ip = robot.GetControllerIP()
    print(f"controller ip: {ip}")

    robot.Mode(1)
    time.sleep(1)
    robot.DragTeachSwitch(state=1)
    time.sleep(1)
    error,state = robot.IsInDragTeach()
    print(f"drag state: {state}")
    time.sleep(3)
    robot.DragTeachSwitch(state=0)
    time.sleep(1)
    error,state = robot.IsInDragTeach()
    print(f"drag state: {state}")
    time.sleep(3)
    robot.RobotEnable(0)
    time.sleep(3)
    robot.RobotEnable(1)
    robot.Mode(0)
    time.sleep(1)
    robot.Mode(1)
    time.sleep(1)
    rtn = robot.HiSpeedManualSwitch(1)
    print(f"change high speed mode : {rtn}")
    time.sleep(1)
    rtn = robot.HiSpeedManualSwitch(0)
    print(f"change low speed mode : {rtn}")
    time.sleep(3)
    robot.ShutDownRobotOS()
  
    robot.CloseRPC()

Obtener la versión de software del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSoftwareVersion()``"
    "Descripción", "Obtener la versión de software del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``robotModel``：Modelo del robot
    - ``webVersion``：Versión web
    - ``controllerVersion``：Versión del controlador"

Obtener la información de la versión de hardware del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSlaveHardVersion()``"
    "Descripción", "Obtener la información de la versión de hardware del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``ctrlBoxBoardVersion``：Versión de la caja de control
    - ``driver1Version``
    - ``driver2Version``
    - ``driver3Version``
    - ``driver4Version``
    - ``driver5Version``
    - ``driver6Version``
    - ``endBoardVersion``"

Obtener la información de la versión de firmware del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSlaveFirmVersion()``"
    "Descripción", "Obtener la información de la versión de firmware del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``ctrlBoxBoardVersion``：Versión de la caja de control
    - ``driver1Version``
    - ``driver2Version``
    - ``driver3Version``
    - ``driver4Version``
    - ``driver5Version``
    - ``driver6Version``
    - ``endBoardVersion``"

Ejemplo de código para obtener las versiones de software y firmware del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    rtn,robotModel, webversion, controllerVersion = robot.GetSoftwareVersion()
    print(f"Getsoftwareversion rtn is: {rtn}")
    print(f"robotmodel is: {robotModel}, webversion is: {webversion}, controllerVersion is: {controllerVersion}\n")
    rtn,ctrlBoxBoardversion, driver1version, driver2version,driver3version, driver4version, driver5version,driver6version, endBoardversion = robot.GetHardwareversion()
    print(f"GetHardwareversion rtn is: {rtn}")
    print(f"GetHardwareversion get hardware version is: {ctrlBoxBoardversion}, {driver1version}, {driver2version}, "
          f"{driver3version}, {driver4version}, {driver5version}, {driver6version}, {endBoardversion}\n")
    rtn,ctrlBoxBoardversion, driver1version, driver2version,driver3version, driver4version, driver5version,driver6version, endBoardversion = robot.GetFirmwareVersion()
    print(f"GetFirmwareversion rtn is: {rtn}")
    print(f"GetFirmwareversion get firmware version is: {ctrlBoxBoardversion}, {driver1version}, {driver2version}, "
          f"{driver3version}, {driver4version}, {driver5version}, {driver6version}, {endBoardversion}\n")
    robot.CloseRPC()