Otras interfaces
=================

.. toctree:: 
    :maxdepth: 5

Obtener la clave pública SSH
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSSHKeygen()``"
    "Descripción", "Obtener la clave pública SSH"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``keygen``：Clave pública"

Enviar comando SCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSSHScpCmd(mode, sshname, sship, usr_file_url, robot_file_url)``"
    "Descripción", "Enviar comando SCP"
    "Parámetros obligatorios", "- ``mode``：0-carga (PC anfitrión->controlador), 1-descarga (controlador->PC anfitrión)
    - ``sshname``：Nombre de usuario del PC anfitrión
    - ``sship``：Dirección IP del PC anfitrión
    - ``usr_file_url``：Ruta del archivo en el PC anfitrión
    - ``robot_file_url``：Ruta del archivo en el controlador del robot"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Calcular el valor MD5 del archivo en la ruta especificada
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeFileMD5(file_path)``"
    "Descripción", "Calcular el valor MD5 del archivo en la ruta especificada"
    "Parámetros obligatorios", "- ``file_path``：Ruta del archivo incluido el nombre del archivo; la ruta predeterminada de la carpeta Traj es: /fruser/traj/, por ejemplo /fruser/traj/trajHelix_aima_1.txt"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``md5``：Valor MD5 del archivo"

Ejemplo de código de las instrucciones SSH y MD5 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    file_path = "/fruser/airlab.lua"
    md5 = ""
    emerg_state = 0
    si0_state = 0
    si1_state = 0
    sdk_com_state = 0
    ssh_keygen = ""
    retval,ssh_keygen = robot.GetSSHKeygen()
    print(f"GetSSHKeygen retval is: {retval}")
    print(f"ssh key is: {ssh_keygen}")
    ssh_name = "fr"
    ssh_ip = "192.168.58.45"
    ssh_route = "/home/fr"
    ssh_robot_url = "/root/robot/dhpara.config"
    retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url)
    print(f"SetSSHScpCmd retval is: {retval}")
    print(f"robot url is: {ssh_robot_url}")
    error, md5 = robot.ComputeFileMD5(file_path)
    print(f"md5 is: {md5}")
    robot.CloseRPC()

Establecer el período de retroalimentación del puerto 20004 del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotRealtimeStateSamplePeriod(period)``"
    "Descripción", "Establecer el período de retroalimentación del puerto 20004 del robot"
    "Parámetros obligatorios", "- ``period``：Período de retroalimentación del puerto 20004 del robot (ms)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Obtener el período de retroalimentación del puerto 20004 del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotRealtimeStateSamplePeriod()``"
    "Descripción", "Obtener el período de retroalimentación del puerto 20004 del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``period``：Período de retroalimentación del puerto 20004 del robot (ms)"

Ejemplo de código de configuración del período de retroalimentación de estado del puerto 20004 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.SetRobotRealtimeStateSamplePeriod(10)
    error,getPeriod = robot.GetRobotRealtimeStateSamplePeriod()
    print(f"period is {getPeriod}")
    time.sleep(1)
    robot.CloseRPC()

Actualización del software del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SoftwareUpgrade(filePath, block)``"
    "Descripción", "Actualización del software del robot"
    "Parámetros obligatorios", "- ``filePath``：Ruta completa del paquete de actualización de software
    - ``block``：Si se bloquea hasta completar la actualización true:bloquear; false:no bloquear"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode "

Obtener el estado de actualización del software del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSoftwareUpgradeState()``"
    "Descripción", "Obtener el estado de actualización del software del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``state``：Estado de actualización del paquete de software del robot, 0: inactivo o subiendo paquete de actualización, 1~100: porcentaje completado de la actualización, -1: fallo al actualizar el software, -2: fallo de verificación, -3: fallo de verificación de versión, -4: fallo de descompresión, -5: fallo de actualización de la configuración de usuario, -6: fallo de actualización de la configuración de periféricos, -7: fallo de actualización de la configuración del eje extendido, -8: fallo de actualización de la configuración del robot, -9: fallo de actualización de la configuración de parámetros DH"

Ejemplo de código de actualización del software del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    error = robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", False)
    print(f"SoftwareUpgrade error is {error}")
    while True:
        curState = robot.GetSoftwareUpgradeState()
        print(f"upgrade state is {curState}")
        time.sleep(3)
    robot.CloseRPC()

Descargar la base de datos de la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PointTableDownLoad(point_table_name, save_file_path)``"
    "Descripción", "Descargar la base de datos de la tabla de puntos"
    "Parámetros obligatorios", "- ``point_table_name``：Nombre de la tabla de puntos a descargar    pointTable1.db;
    - ``save_file_path``:Ruta de guardado de la tabla de puntos a descargar   C://test/;"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Subir la base de datos de la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PointTableUpLoad(point_table_file_path)``"
    "Descripción", "Subir la base de datos de la tabla de puntos"
    "Parámetros obligatorios", "- ``point_table_file_path``：Nombre de ruta completo de la tabla de puntos a subir   C://test/pointTable1.db"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Actualizar el archivo lua de la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PointTableUpdateLua(point_table_name, lua_file_name)``"
    "Descripción", "Actualizar el archivo lua de la tabla de puntos"
    "Parámetros obligatorios", "- ``point_table_name``：Nombre de la tabla de puntos a cambiar pointTable1.db, cuando la tabla de puntos está vacía, es decir "" , indica que el programa lua se actualiza al programa inicial sin aplicar la tabla de puntos
    - ``lua_file_name``: Nombre del archivo lua a actualizar testPointTable.lua"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Cambio y aplicación de la tabla de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PointTableSwitch(self, point_table_name)``"
    "Descripción", "Cambio de la tabla de puntos"
    "Parámetros obligatorios", "
    - ``point_table_name``：Nombre de la tabla de puntos a cambiar `pointTable1.db`, cuando la tabla de puntos está vacía, es decir `` , indica que el programa lua se actualiza al programa inicial sin aplicar la tabla de puntos
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de operación de la tabla de puntos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    save_path = "D://zDOWN/"
    point_table_name = "point_table_FR5.db"
    rtn = robot.PointTableDownLoad(point_table_name, save_path)
    print(f"download : {point_table_name} fail: {rtn}")
    upload_path = "D://zDOWN/point_table_FR5.db"
    rtn = robot.PointTableUpLoad(upload_path)
    print(f"retval is: {rtn}")
    point_tablename = "point_table_FR5.db"
    lua_name = "test0610.lua"
    rtn,error = robot.PointTableUpdateLua(point_tablename, lua_name)
    print(f"retval is: {rtn}")
    robot.CloseRPC()

Descarga del registro del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``RbLogDownload(savePath)``"
    "Descripción", "Descarga del registro del controlador"
    "Parámetros obligatorios", "- ``savePath``：Ruta de guardado del archivo D://zDown/"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Descarga de todas las fuentes de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AllDataSourceDownload(savePath)``"
    "Descripción", "Descarga de todas las fuentes de datos"
    "Parámetros obligatorios", "- ``savePath``：Ruta de guardado del archivo D://zDown/"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Descarga del paquete de copia de seguridad de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``DataPackageDownload(savePath)``"
    "Descripción", "Descarga del paquete de copia de seguridad de datos"
    "Parámetros obligatorios", "- ``savePath``：Ruta de guardado del archivo D://zDown/"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de descarga de datos del controlador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.RbLogDownload("D://zDOWN/")
    print(f"RbLogDownload rtn is {rtn}")
    rtn = robot.AllDataSourceDownload("D://zDOWN/")
    print(f"AllDataSourceDownload rtn is {rtn}")
    rtn = robot.DataPackageDownload("D://zDOWN/")
    print(f"DataPackageDownload rtn is {rtn}")
    robot.CloseRPC()

Establecer la actualización del codificador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetEncoderUpgrade(path)``"
    "Descripción", "Establecer la actualización del codificador"
    "Parámetros obligatorios", "- ``path``：Ruta completa local del paquete de actualización (D://zUP/XXXXX.bin)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Establecer la actualización del firmware de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetJointFirmwareUpgrade(type, path)``"
    "Descripción", "Establecer la actualización del firmware de las articulaciones"
    "Parámetros obligatorios", "- ``type``：Tipo de archivo de actualización; 1-actualizar firmware; 2-actualizar archivo de configuración de esclavo
    - ``path``：Ruta completa local del paquete de actualización (D://zUP/XXXXX.bin)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la actualización del firmware de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetCtrlFirmwareUpgrade(type, path)``"
    "Descripción", "Establecer la actualización del firmware de la caja de control"
    "Parámetros obligatorios", "- ``type``：Tipo de archivo de actualización; 1-actualizar firmware; 2-actualizar archivo de configuración de esclavo
    - ``path``：Ruta completa local del paquete de actualización (D://zUP/XXXXX.bin)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Establecer la actualización del firmware del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetEndFirmwareUpgrade(type, path)``"
    "Descripción", "Establecer la actualización del firmware del extremo"
    "Parámetros obligatorios", "- ``type``：Tipo de archivo de actualización; 1-actualizar firmware; 2-actualizar archivo de configuración de esclavo
    - ``path``：Ruta completa local del paquete de actualización (D://zUP/XXXXX.bin)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
       
Actualización del archivo de configuración de todos los parámetros de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointAllParamUpgrade(path)``"
    "Descripción", "Actualización del archivo de configuración de todos los parámetros de las articulaciones"
    "Parámetros obligatorios", "- ``path``：Ruta completa local del paquete de actualización (D://zUP/XXXXX.bin)"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de actualización del firmware del esclavo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.RobotEnable(0)
    time.sleep(0.2)
    rtn = robot.JointAllParamUpgrade("D://zUP/MT/joint0603/jointallparameters.db")
    print(f"robot JointAllParamUpgrade rtn is {rtn}")
    rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/MT/FAIR_Cobot_Cbd_Asix_V2.0.bin")
    print(f"robot SetCtrlFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/MT/FAIR_Cobot_Axle_Asix_V2.4.bin")
    print(f"robot SetEndFirmwareUpgrade rtn is {rtn}")
    robot.SetSysServoBootMode()
    time.sleep(0.2)
    rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/MT/FR_CTRL_PRIMCU_FV201412_MAIN_U4_T01_20250630(MT).bin")
    print(f"robot SetCtrlFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/MT/FR_END_FV2010010_MAIN_U1_T01_20250603.bin")
    print(f"robot SetEndFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/MT/FR_SERVO_FV504215_MAIN_U7_T07_20250603.bin")
    print(f"robot SetJointFirmwareUpgrade rtn is {rtn}")
    robot.CloseRPC()
       
Actualización del sistema operativo del robot (caja de control LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``KernelUpgrade(filePath)``"
    "Descripción", "Actualización del sistema operativo del robot (caja de control LA)"
    "Parámetros obligatorios", "- ``filePath``：Ruta completa del paquete de actualización del sistema operativo"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
       
Obtener el resultado de la actualización del sistema operativo del robot (caja de control LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetKernelUpgradeResult()``"
    "Descripción", "Obtener el resultado de la actualización del sistema operativo del robot (caja de control LA)"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
       
Generación del registro MCU del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``RobotMCULogCollect()``"
    "Descripción", "Generación del registro MCU del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
           
Establecer la detención del robot al desconectarse la comunicación del puerto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotStopOnComDisc(portID, enable, confirmTime)``"
    "Descripción", "Establecer la detención del robot al desconectarse la comunicación del puerto"
    "Parámetros obligatorios", "
    - ``portID``：Número de puerto 0-8080; 1-8083; 2-20002; 3-20004
    - ``enable``：0-desactivar; 1-activar
    - ``confirmTime``：Duración de confirmación de interrupción de comunicación (ms) [0-5000]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
           
Obtener los parámetros de detención del robot al desconectarse la comunicación del puerto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotStopOnComDisc(portID)``"
    "Descripción", "Obtener los parámetros de detención del robot al desconectarse la comunicación del puerto"
    "Parámetros obligatorios", "
    - ``portID``：Número de puerto 0-8080; 1-8083; 2-20002; 3-20004
    - ``enable``：0-desactivar; 1-activar
    - ``confirmTime``：Duración de confirmación de interrupción de comunicación (ms) [0-5000]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de los parámetros de detención del robot al desconectarse la comunicación del puerto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot
    # Establecer comunicación con el controlador del robot
    robot = Robot.RPC('192.168.58.2')

    def test_robot_stop_on_com_disc(self):
        # Inicializar parámetros
        enable = False
        confirm_time = 0

        # Establecer la función de detención del robot al desconectarse la comunicación
        rtn = robot.SetRobotStopOnComDisc(0, True, 330)
        print(f"SetRobotStopOnComDisc index0: {rtn}")

        rtn = robot.SetRobotStopOnComDisc(1, True, 550)
        print(f"SetRobotStopOnComDisc index1: {rtn}")

        rtn = robot.SetRobotStopOnComDisc(2, True, 110)
        print(f"SetRobotStopOnComDisc index2: {rtn}")

        rtn = robot.SetRobotStopOnComDisc(3, True, 220)
        print(f"SetRobotStopOnComDisc index3: {rtn}")

        # Obtener la configuración de detención del robot al desconectarse la comunicación
        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(0)
        print(f"GetRobotStopOnComDisc 8080 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(1)
        print(f"GetRobotStopOnComDisc 80803 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(2)
        print(f"GetRobotStopOnComDisc 20002 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        rtn, enable, confirm_time = robot.GetRobotStopOnComDisc(3)
        print(f"GetRobotStopOnComDisc 20004 rtn {rtn}; enable is {enable}; confirm time is {confirm_time}")

        # Cerrar la conexión RPC
        robot.CloseRPC()
        return 0

    test_robot_stop_on_com_disc(robot)

Envío de trama de instrucciones por UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SendUDPFrame(frame)``"
    "Descripción", "Envío de trama de instrucciones por UDP"
    "Parámetros obligatorios", "
    - ``frame``：Datos UDP a enviar, transmisión transparente, sin encapsulación"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código SDK basado en comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Establecer comunicación con el controlador del robot
    robot = Robot.RPC('192.168.58.2')

    def TestSendUDPFrame(self):
        # Establecer la función de devolución de llamada
        def callback(src_type, count, cmd_id, data_len, content):
            print("Respuesta recibida: cmd_id={} count={} data_len={} content={}".format(cmd_id, count, data_len, content))
            return 0
        robot.SetUDPCmdRpyCallback(callback)

        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f")
        print(f"SendUDPFrame Mode(0) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame("/f/bIII21III303III7IIIMode(1)III/b/f")
        print(f"SendUDPFrame Mode(1) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame(
            "/f/bIII49III201III184IIIMoveJ(-15.625, -82.680, 101.654, -110.950, -88.290, 0.017, -383.012, -2.325, 242.655, -178.024, 1.710, 74.416, 0, 0, 100, 100, 100, 0.000, 0.000, 0.000, 0.000, -1, 0, 0, 0, 0, 0, 0, 0)III/b/f")
        print(f"SendUDPFrame MoveJ(-15.625) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame(
            "/f/bIII48III203III199IIIMoveL(-75.622, -82.680, 101.654, -110.950, -88.290, 0.017, -193.537, 330.525, 242.657, -178.024, 1.710, 14.420, 0, 0, 100, 100, 100, -1, 0, 0.000, 0.000, 0.000, 0.000, 0, 0, 0, 0, 0, 0, 0, 0, 100, 0)III/b/f")
        print(f"SendUDPFrame MoveL(-75.622) rtn is {rtn}")
        time.sleep(1)

        rtn = robot.SendUDPFrame("/f/bIII4III905III20IIIGetSoftwareVersion()III/b/f")
        print(f"SendUDPFrame GetSoftwareVersion() rtn is {rtn}")

        time.sleep(1)

        # Prueba de verificación de datos de trama UDP enviada
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("III20III303III7IIIMode(0)III/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/bIII20III303III6IIIMode(0)III/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/b|||20|||303|||7|||Mode(0)|||/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        rtn = robot.SendUDPFrame("/f/bII20II303II7IIMode(0)II/b/f")
        print(f"SendUDPFrame rtn is {rtn}")

        robot.CloseRPC()
        time.sleep(1)

    TestSendUDPFrame(robot)
    
Establecer el color de la luz del extremo del robot personalizado por el usuario
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetUserLEDColor(r, g, b)``"
    "Descripción", "Establecer el color de la luz del extremo del robot personalizado por el usuario"
    "Parámetros obligatorios", "
    - ``r``：Control de la luz roja del extremo; 0-apagada; 1-encendida
    - ``g``：Control de la luz verde del extremo; 0-apagada; 1-encendida
    - ``b``：Control de la luz azul del extremo; 0-apagada; 1-encendida
    - "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código SDK de establecimiento del color de la luz del extremo del robot personalizado por el usuario
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Establecer comunicación con el controlador del robot
    robot = Robot.RPC('192.168.58.2')


    def testled(self):
        # Establecer el color de la luz LED personalizada del usuario
        # Orden de parámetros: R, G, B (rojo, verde, azul)

        # Blanco (rojo, verde y azul encendidos)
        robot.SetUserLEDColor(True, True, True)
        time.sleep(1)

        # Apagar todas las luces
        robot.SetUserLEDColor(False, False, False)
        time.sleep(1)

        # Rojo (solo luz roja encendida)
        robot.SetUserLEDColor(True, False, False)
        time.sleep(1)

        # Verde (solo luz verde encendida)
        robot.SetUserLEDColor(False, True, False)
        time.sleep(1)

        # Azul (solo luz azul encendida)
        robot.SetUserLEDColor(False, False, True)

        # Cerrar la conexión
        robot.CloseRPC()

    testled(robot)

Enviar trama de instrucciones personalizada a través de TCP 8080
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SendTCPFrame(self, frame):``"
    "Descripción", "Enviar trama de instrucciones personalizada a través de TCP 8080 (en modo mTLS se realiza automáticamente a través del canal cifrado)"
    "Parámetros obligatorios", "
    - ``frame``：Trama de instrucciones completa, como /f/bIII52III236III7IIIMode(0)III/b/f"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de envío de trama de instrucciones personalizada a través de TCP 8080
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        # Establecer comunicación con el controlador del robot (TLS habilitado)
        robot = Robot.RPC(
            '192.168.58.2',
            tls_enable=True,
            tls_cert_path=r"E:\certs"
        )
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        # Establecer una función de devolución de llamada simple de respuesta de comandos UDP
        def callback(src_type, count, cmd_id, data_len, content):
            print("Callback: cmd_id={} count={} data_len={} content={}".format(cmd_id, count, data_len, content))
            return 0

        robot.SetUDPCmdRpyCallback(callback)

        # Nombre del programa a cargar
        program_name = "mtls.lua"
        state = 0
        line = 0

        mode0 = "/f/bIII52III236III7IIIMode(0)III/b/f"
        mode1 = "/f/bIII52III236III7IIIMode(1)III/b/f"

        print(f"[SEND] {mode0}")
        robot.SendTCPFrame(mode0)
        time.sleep(1)

        print(f"[SEND] {mode1}")
        robot.SendTCPFrame(mode1)
        time.sleep(1)

        print(f"[SEND] {mode0}")
        robot.SendTCPFrame(mode0)

        # Establecer modo automático y cargar el programa
        robot.Mode(0)
        robot.LoadDefaultProgConfig(0, program_name)
        robot.ProgramLoad(program_name)
        robot.SetSpeedInstant(50)
        robot.ProgramRun()
        time.sleep(5)

        # Pausar y consultar el estado del programa
        robot.PauseMotion()
        rtn, state = robot.GetProgramState()
        print(f"program state:{state}\n")

        rtn, line = robot.GetCurrentLine()
        print(f"current line:{line}\n")

        rtn, loaded_name = robot.GetLoadedProgram()
        print(f"program name:{loaded_name}\n")

        # Reanudar y pausar de nuevo
        robot.ResumeMotion()
        time.sleep(2)
        robot.PauseMotion()
        time.sleep(2)

        # Cerrar la conexión
        robot.CloseRPC()
        time.sleep(1)

    if __name__ == "__main__":
        main()
        
Actualización por carga del paquete de copia de seguridad de datos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``DataPackageUpgrade(self, filePath)``"
    "Descripción", "Actualización por carga del paquete de copia de seguridad de datos"
    "Parámetros obligatorios", "
    - ``filePath``：Ruta del archivo del paquete de copia de seguridad de datos a subir; D://zUP/fr_user_data.tar.gz"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el porcentaje de progreso de la actualización del paquete de copia de seguridad de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDataPackageUpgradeProgress(self)``"
    "Descripción", "Obtener el porcentaje de progreso de la actualización del paquete de copia de seguridad de datos"
    "Parámetros obligatorios", "
    - ``progress``：Porcentaje de progreso de la actualización [0-100], -1:fallo de la actualización"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el porcentaje de progreso de la actualización de todos los parámetros de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetJointAllParamUpgradeProgress(self)``"
    "Descripción", "Obtener el porcentaje de progreso de la actualización de todos los parámetros de las articulaciones"
    "Parámetros obligatorios", "
    - ``progress``：Porcentaje de progreso de la actualización [0-100], -1:fallo de la actualización"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de actualización por carga del paquete de copia de seguridad de datos y consulta del progreso de la actualización
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    def test_data_package_upgrade(robot):
    """Prueba de actualización del paquete de datos"""
    print("\n========== Prueba de actualización del paquete de datos ==========")

    time.sleep(0.2)  # 200ms

    # Actualización del paquete de datos
    rtn = robot.DataPackageUpgrade("D://zUP/upgrade/FR5/fr_user_data.tar.gz")
    print(f"robot DataPackageUpgrade rtn is {rtn}")

    # Consultar el progreso de la actualización hasta el 100%
    upgradeProgress = 0
    while upgradeProgress < 100:
        rtn, upgradeProgress = robot.GetDataPackageUpgradeProgress()
        print(f"robot data package upgrade progress : {upgradeProgress}")
        time.sleep(0.2)  # 200ms
        
Ejemplo de código de actualización de todos los parámetros de las articulaciones y consulta del progreso de la actualización
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    def test_joint_all_param_upgrade(robot):
    """Prueba de actualización de todos los parámetros de las articulaciones"""
    print("\n========== Prueba de actualización de todos los parámetros de las articulaciones ==========")

    # Deshabilitar el robot antes de actualizar los parámetros
    robot.RobotEnable(0)
    time.sleep(0.2)  # 200ms

    # Actualización de todos los parámetros de las articulaciones
    rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/FR3WMS/jointallparameters.db")
    print(f"robot JointAllParamUpgrade rtn is {rtn}")

    # Consultar el progreso de la actualización hasta el 100%
    upgradeProgress = 0
    while upgradeProgress < 100:
        rtn, upgradeProgress = robot.GetJointAllParamUpgradeProgress()
        print(f"robot joint all param upgrade progress : {upgradeProgress}")
        time.sleep(0.2)  # 200ms