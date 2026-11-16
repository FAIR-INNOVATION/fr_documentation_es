Configuraciones habituales del robot
====================================

.. toctree:: 
    :maxdepth: 5

Establecer el punto de referencia de la herramienta - método de seis puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolPoint(point_num)``"
    "Descripción", "Establecer el punto de referencia de la herramienta - método de seis puntos"
    "Parámetros obligatorios", "- ``point_num``：Número de punto, rango [1~6]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Calcular el sistema de coordenadas de herramienta - método de seis puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeTool()``"
    "Descripción", "Calcular el sistema de coordenadas de herramienta - método de seis puntos (calcular después de establecer los seis puntos de referencia de la herramienta)"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``：Sistema de coordenadas de herramienta"

Establecer el punto de referencia de la herramienta - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTcp4RefPoint(point_num)``"
    "Descripción", "Establecer el punto de referencia de la herramienta - método de cuatro puntos"
    "Parámetros obligatorios", "``point_num``：Número de punto, rango [1~4]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``：Sistema de coordenadas de herramienta"

Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeTcp4()``"
    "Descripción", "Calcular el sistema de coordenadas de herramienta - método de cuatro puntos (calcular después de establecer los cuatro puntos de referencia de la herramienta)"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``：Sistema de coordenadas de herramienta"

Calcular el sistema de coordenadas de herramienta a partir de la información de los puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeToolCoordWithPoints(method, pos)``"
    "Descripción", "Calcular el sistema de coordenadas de herramienta a partir de la información de los puntos"
    "Parámetros obligatorios", "- ``method``：Método de cálculo; 0-método de cuatro puntos; 1-método de seis puntos
    - ``pos``：Grupo de posiciones de articulaciones; en el método de cuatro puntos la longitud del arreglo es 4, en el método de seis puntos la longitud del arreglo es 6"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``tcp_offset=[x,y,z,rx,ry,rz]``：Sistema de coordenadas de herramienta calculado a partir de la información de los puntos, unidad [mm][°]"

Establecer el sistema de coordenadas de herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolCoord(id,t_coord,type,install,toolID,loadNum)``"
    "Descripción", "Establecer el sistema de coordenadas de herramienta"
    "Parámetros obligatorios", "- ``id``:Número del sistema de coordenadas, rango [1~15];
    - ``t_coord``:Pose del centro de la herramienta respecto al centro de la brida del extremo, unidad [mm][°];
    - ``type``:0-sistema de coordenadas de herramienta, 1-sistema de coordenadas de sensor;
    - ``install``:Posición de instalación, 0-extremo del robot, 1-exterior del robot
    - ``toolID``:ID de la herramienta
    - ``loadNum``:Número de carga"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Establecer la lista de sistemas de coordenadas de herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolList(id,t_coord ,type, install, loadNum)``"
    "Descripción", "Establecer la lista de sistemas de coordenadas de herramienta"
    "Parámetros obligatorios", "- ``id``:Número del sistema de coordenadas, rango [1~15];
    - ``t_coord``:[x,y,z,rx,ry,rz] Pose del centro de la herramienta respecto al centro de la brida del extremo, unidad [mm][°];
    - ``type``:0-sistema de coordenadas de herramienta, 1-sistema de coordenadas de sensor;
    - ``install``:Posición de instalación, 0-extremo del robot, 1-exterior del robot
    - ``loadNum``:Número de carga"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Obtener el sistema de coordenadas de herramienta actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTCPOffset(flag=1)``"
    "Descripción", "Obtener el sistema de coordenadas de herramienta actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "``flag``：0-bloqueante, 1-no bloqueante; valor predeterminado 1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``tcp_offset=[x,y,z,rx,ry,rz]``: Pose relativa del sistema de coordenadas de herramienta actual, unidad [mm][°]"

Ejemplo de código de operación del sistema de coordenadas de herramienta del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [186.331, 487.913, 209.850, 149.030, 0.688, -114.347]
    p2Desc = [69.721, 535.073, 202.882, -144.406, -14.775, -89.012]
    p3Desc = [146.861, 578.426, 205.598, 175.997, -36.178, -93.437]
    p4Desc = [136.284, 509.876, 225.613, 178.987, 1.372, -100.696]
    p5Desc = [138.395, 505.972, 298.016, 179.134, 2.147, -101.110]
    p6Desc = [105.553, 454.325, 232.017, -179.426, 0.444, -99.952]
    p1Joint = [-127.876, -75.341, 115.417, -122.741, -59.820, 74.300]
    p2Joint = [-101.780, -69.828, 110.917, -125.740, -127.841, 74.300]
    p3Joint = [-112.851, -60.191, 86.566, -80.676, -97.463, 74.300]
    p4Joint = [-116.397, -76.281, 113.845, -128.611, -88.654, 74.299]
    p5Joint = [-116.814, -82.333, 109.162, -118.662, -88.585, 74.302]
    p6Joint = [-115.649, -84.367, 122.447, -128.663, -90.432, 74.303]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    posJ = [p1Joint, p2Joint, p3Joint, p4Joint, p5Joint, p6Joint]
    rtn,coordRtn = robot.ComputeToolCoordWithPoints(1, posJ)
    print(f"ComputeToolCoordWithPoints    {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.MoveJ(joint_pos=p1Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(3)
    robot.MoveJ(joint_pos=p4Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(4)
    robot.MoveJ(joint_pos=p5Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(5)
    robot.MoveJ(joint_pos=p6Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(6)
    rtn,coordRtn = robot.ComputeTool()
    print(f"6 Point ComputeTool        {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolList(1, coordRtn, 0, 0, 0)
    robot.MoveJ(joint_pos=p1Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(3)
    robot.MoveJ(joint_pos=p4Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(4)
    rtn,coordRtn = robot.ComputeTcp4()
    print(f"4 Point ComputeTool        {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolCoord(2, coordRtn, 0, 0, 1, 0)
    rtn,getCoord = robot.GetTCPOffset(0)
    print(f"GetTCPOffset    {rtn}  coord is {getCoord[0]} {getCoord[1]} {getCoord[2]} {getCoord[3]} {getCoord[4]} {getCoord[5]}")
    robot.CloseRPC()

Establecer el punto de referencia de la herramienta externa - método de seis puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExTCPPoint(point_num)``"
    "Descripción", "Establecer el punto de referencia de la herramienta externa - método de tres puntos"
    "Parámetros obligatorios", "- ``point_num``：Número de punto, rango [1~3]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Calcular el sistema de coordenadas de herramienta externa - método de seis puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeExTCF(point_num)``"
    "Descripción", "Calcular el sistema de coordenadas de herramienta externa - método de tres puntos (calcular después de establecer los tres puntos de referencia)"
    "Parámetros obligatorios", "``point_num``：Número de punto, rango [1~3]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``etcp=[x,y,z,rx,ry,rz]``：Sistema de coordenadas de herramienta externa"

Establecer el sistema de coordenadas de herramienta externa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExToolCoord(id,etcp,etool)``"
    "Descripción", "Establecer el sistema de coordenadas de herramienta externa"
    "Parámetros obligatorios", "- ``id``:Número del sistema de coordenadas, 20-39 corresponden a los sistemas de coordenadas de herramienta externa 0-19;
    - ``etcp``:[x,y,z,rx,ry,rz] Sistema de coordenadas de herramienta externa, unidad [mm][°];
    - ``etool``:[x,y,z,rx,ry,rz] Sistema de coordenadas de la herramienta del extremo, unidad [mm][°];"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la lista de sistemas de coordenadas de herramienta externa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExToolList(id,etcp ,etool)``"
    "Descripción", "Establecer la lista de sistemas de coordenadas de herramienta externa"
    "Parámetros obligatorios", "- ``id``:Número del sistema de coordenadas, 20-39 corresponden a los sistemas de coordenadas de herramienta externa 0-19;
    - ``etcp``:[x,y,z,rx,ry,rz] Sistema de coordenadas de herramienta externa, unidad [mm][°];
    - ``etool``:[x,y,z,rx,ry,rz] Sistema de coordenadas de la herramienta del extremo, unidad [mm][°];"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Ejemplo de código de operación del sistema de coordenadas de herramienta externa del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    robot = Robot.RPC('192.168.58.2')

    def TestExtCoord(self):
        p1Desc = [-89.606, 779.517, 193.516, 178.000, 0.476, -92.484]
        p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]

        p2Desc = [-24.656, 850.384, 191.361, 177.079, -2.058, -95.355]
        p2Joint = [-111.024, -41.538, 69.222, -114.913, -87.743, 74.329]

        p3Desc = [-99.813, 766.661, 241.878, -176.817, 1.917, -91.604]
        p3Joint = [-107.266, -56.116, 85.971, -122.560, -92.548, 74.331]

        exaxisPos = [0, 0, 0, 0]
        offdese = [0, 0, 0, 0, 0, 0]

        posTCP = [p1Desc, p2Desc, p3Desc]
        # coordRtn = DescPose()

        robot.MoveJ(joint_pos=p1Joint,tool=1, user=0, vel=50)
        robot.SetExTCPPoint(1)
        robot.MoveJ(joint_pos=p2Joint,tool=1, user=0, vel=50)
        robot.SetExTCPPoint(2)
        robot.MoveJ(joint_pos=p3Joint,tool=1, user=0, vel=50)
        robot.SetExTCPPoint(3)
        rtn,coordRtn = robot.ComputeExTCF()
        print(f"ComputeExTCF {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")

        robot.SetExToolCoord(21, coordRtn, offdese)
        robot.SetExToolList(21, coordRtn, offdese)

        robot.CloseRPC()
    TestExtCoord(robot)

Establecer el punto de referencia de la pieza - método de tres puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWObjCoordPoint(point_num)``"
    "Descripción", "Establecer el punto de referencia de la pieza - método de tres puntos"
    "Parámetros obligatorios", "``point_num``:Número de punto, rango [1~3]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Calcular el sistema de coordenadas de la pieza - método de tres puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeWObjCoord(method, refFrame)``"
    "Descripción", "Calcular el sistema de coordenadas de la pieza - método de tres puntos (calcular después de establecer los tres puntos de referencia);"
    "Parámetros obligatorios", "- ``method``：Método de cálculo 0: origen-eje x-eje z, 1: origen-eje x-plano xy
    - ``refFrame``：Sistema de coordenadas de referencia"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``wobj_pose=[x,y,z,rx,ry,rz]``：Sistema de coordenadas de la pieza"

Establecer el sistema de coordenadas de la pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWObjCoord(id, coord, refFrame)``"
    "Descripción", "Establecer el sistema de coordenadas de la pieza"
    "Parámetros obligatorios", "- ``id``:Número del sistema de coordenadas, rango [0~14];
    - ``coord``:Pose del sistema de coordenadas de la pieza respecto al centro de la brida del extremo, unidad [mm][°]
    - ``refFrame``:Sistema de coordenadas de referencia"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la lista de sistemas de coordenadas de la pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWObjList(id, coord, refFrame)``"
    "Descripción", "Establecer la lista de sistemas de coordenadas de la pieza"
    "Parámetros obligatorios", "- ``id``:Número del sistema de coordenadas, rango [0~14];
    - ``coord``:Pose del sistema de coordenadas de la pieza respecto al centro de la brida del extremo, unidad [mm][°]
    - ``refFrame``:Sistema de coordenadas de referencia"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Calcular el sistema de coordenadas de la pieza a partir de la información de los puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeWObjCoordWithPoints(method, pos, refFrame)``"
    "Descripción", "Calcular el sistema de coordenadas de la pieza a partir de la información de los puntos"
    "Parámetros obligatorios", "- ``method``：Método de cálculo; 0: origen-eje x-eje z  1: origen-eje x-plano xy
    - ``pos``：Tres grupos de posiciones del TCP
    - ``refFrame``：Sistema de coordenadas de referencia"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode 
    - ``wobj_offset=[x,y,z,rx,ry,rz]``：Sistema de coordenadas de la pieza calculado a partir de la información de los puntos, unidad [mm][°]"

Obtener el sistema de coordenadas de la pieza actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWObjOffset(flag=1)``"
    "Descripción", "Obtener el sistema de coordenadas de la pieza actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "``flag``：0-bloqueante, 1-no bloqueante; valor predeterminado 1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``wobj_offset=[x,y,z,rx,ry,rz]``: Pose relativa del sistema de coordenadas de la pieza actual, unidad [mm][°]"

Ejemplo de código de operación del sistema de coordenadas de la pieza del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [-89.606, 779.517, 193.516, 178.000, 0.476, -92.484]
    p2Desc = [-24.656, 850.384, 191.361, 177.079, -2.058, -95.355]
    p3Desc = [-99.813, 766.661, 241.878, -176.817, 1.917, -91.604]
    p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]
    p2Joint = [-111.024, -41.538, 69.222, -114.913, -87.743, 74.329]
    p3Joint = [-107.266, -56.116, 85.971, -122.560, -92.548, 74.331]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    posTCP = [p1Desc, p2Desc, p3Desc]
    rtn,coordRtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0)
    print(f"ComputeWObjCoordWithPoints    {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.MoveJ(joint_pos=p1Joint,tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(3)
    rtn,coordRtn = robot.ComputeWObjCoord(1, 0)
    print(f"ComputeWObjCoord   {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetWObjCoord(1, coordRtn, 0)
    robot.SetWObjList(1, coordRtn, 0)
    rtn,getWobjDesc = robot.GetWObjOffset(0)
    print(f"GetWObjOffset    {rtn}  coord is {getWobjDesc[0]} {getWobjDesc[1]} {getWobjDesc[2]} {getWobjDesc[3]} {getWobjDesc[4]} {getWobjDesc[5]}")
    robot.CloseRPC()

Establecer la velocidad global
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSpeed(vel)``"
    "Descripción", "Establecer la velocidad global"
    "Parámetros obligatorios", "- ``vel``:Porcentaje de velocidad, rango [0~100]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer la aceleración del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOaccScale(acc)``"
    "Descripción", "Establecer la aceleración del robot"
    "Parámetros obligatorios", "- ``acc``:Porcentaje de aceleración del robot"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Obtener la velocidad predeterminada
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDefaultTransVel()``"
    "Descripción", "Obtener la velocidad predeterminada"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``vel``: Velocidad predeterminada, unidad [mm/s]"

Establecer el peso de la carga del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLoadWeight(loadNum, weight)``"
    "Descripción", "Establecer el peso de la carga del extremo; una configuración incorrecta del peso de la carga puede provocar que el robot pierda el control en modo de arrastre"
    "Parámetros obligatorios", "- ``loadNum``:Número de carga
    - ``weight``:Unidad [kg]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Establecer las coordenadas del centro de masa de la carga del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLoadCoord(x,y,z,loadNum = 0)``"
    "Descripción", "Establecer las coordenadas del centro de masa de la carga del extremo; una configuración incorrecta del centro de masa de la carga puede provocar que el robot pierda el control en modo de arrastre"
    "Parámetros obligatorios", "- ``x``: Coordenada del centro de masa, unidad [mm]
    - ``y``: Coordenada del centro de masa, unidad [mm]
    - ``z``: Coordenada del centro de masa, unidad [mm]"
    "Parámetros predeterminados", "- ``loadNum``: Número de carga, valor predeterminado 0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Obtener el peso de la carga actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTargetPayload(flag=1)``"
    "Descripción", "Obtener la masa de la carga actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "``flag``：0-bloqueante, 1-no bloqueante; valor predeterminado 1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``weight``：Peso de la carga actual, unidad [kg]"

Obtener el centro de masa de la carga actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTargetPayloadCog(flag=1)``"
    "Descripción", "Obtener el centro de masa de la carga actual"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "``flag``：0-bloqueante, 1-no bloqueante; valor predeterminado 1"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``cog=[x,y,z]``: Coordenadas del centro de masa actual, unidad [mm]"

Establecer el modo de instalación del robot - instalación fija
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotInstallPos(method)``"
    "Descripción", "Establecer el modo de instalación del robot - instalación fija; una configuración incorrecta del modo de instalación puede provocar que el robot pierda el control en modo de arrastre"
    "Parámetros obligatorios", "- ``method``:0-instalación normal, 1-instalación lateral, 2-instalación invertida"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode "

Establecer el ángulo de instalación del robot - instalación libre
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotInstallAngle(yangle,zangle)``"
    "Descripción", "Establecer el ángulo de instalación del robot - instalación libre; una configuración incorrecta del ángulo de instalación puede provocar que el robot pierda el control en modo de arrastre"
    "Parámetros obligatorios", "- ``yangle``：Ángulo de inclinación
    - ``zangle``：Ángulo de rotación"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el ángulo de instalación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotInstallAngle()``"
    "Descripción", "Obtener el ángulo de instalación del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``[yangle,zangle]``：yangle-ángulo de inclinación, zangle-ángulo de rotación"

Establecer el valor de una variable del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSysVarValue(id,value)``"
    "Descripción", "Establecer una variable del sistema"
    "Parámetros obligatorios", "- ``id``：Número de variable, rango [1~20];
    - ``value``：Valor de la variable"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el valor de una variable del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSysVarValue(id)``"
    "Descripción", "Obtener el valor de una variable del sistema"
    "Parámetros obligatorios", "- ``id``：Número de variable del sistema, rango [1~20]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``var_value``：Valor de la variable del sistema"

Ejemplo de código de configuraciones habituales del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    for i in range(1, 100):
        robot.SetSpeed(i)
        robot.SetOaccScale(i)
        time.sleep(0.03)
    error,defaultVel = robot.GetDefaultTransVel()
    print(f"GetDefaultTransVel is {defaultVel}")
    for i in range(1, 21):
        robot.SetSysVarValue(i, i + 0.5)
        time.sleep(0.1)
    for i in range(1, 21):
        value = robot.GetSysVarValue(i)
        print(f"sys value {i} is: {value}")
        time.sleep(0.1)
    robot.SetLoadWeight(0, 2.5)
    robot.SetLoadCoord(3.0,4.0,5.0)
    time.sleep(1)
    error,getLoad = robot.GetTargetPayload(0)
    error,getLoadTran = robot.GetTargetPayloadCog(0)
    print(f"get load is {getLoad}; get load cog is {getLoadTran[0]} {getLoadTran[1]} {getLoadTran[2]}")
    robot.SetRobotInstallPos(0)
    robot.SetRobotInstallAngle(15.0, 25.0)
    error,[anglex, angley] = robot.GetRobotInstallAngle()
    print(f"GetRobotInstallAngle x: {anglex}; y: {angley}")
    robot.CloseRPC()

Interruptor de compensación de fricción de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FrictionCompensationOnOff(state)``"
    "Descripción", "Interruptor de compensación de fricción de las articulaciones"
    "Parámetros obligatorios", "- ``state``：0-desactivado, 1-activado"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación normal
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFrictionValue_level(coeff)``"
    "Descripción", "Establecer el coeficiente de compensación de fricción de las articulaciones - instalación fija - instalación normal"
    "Parámetros obligatorios", "- ``coeff=[j1,j2,j3,j4,j5,j6]``：Coeficientes de compensación de las seis articulaciones"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación lateral
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFrictionValue_wall(coeff)``"
    "Descripción", "Establecer el coeficiente de compensación de fricción de las articulaciones - instalación fija - instalación lateral"
    "Parámetros obligatorios", "- ``coeff=[j1,j2,j3,j4,j5,j6]``：Coeficientes de compensación de las seis articulaciones"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación invertida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFrictionValue_ceiling(coeff)``"
    "Descripción", "Establecer el coeficiente de compensación de fricción de las articulaciones - instalación fija - instalación invertida"
    "Parámetros obligatorios", "- ``coeff=[j1,j2,j3,j4,j5,j6]``：Coeficientes de compensación de las seis articulaciones"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación libre
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFrictionValue_freedom(coeff)``"
    "Descripción", "Establecer el coeficiente de compensación de fricción de las articulaciones - instalación libre"
    "Parámetros obligatorios", "- ``coeff=[j1,j2,j3,j4,j5,j6]``：Coeficientes de compensación de las seis articulaciones"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de configuración de la compensación de fricción de las articulaciones del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    lcoeff = [0.9, 0.9, 0.9, 0.9, 0.9, 0.9]
    wcoeff = [0.4, 0.4, 0.4, 0.4, 0.4, 0.4]
    ccoeff = [0.6, 0.6, 0.6, 0.6, 0.6, 0.6]
    fcoeff = [0.5, 0.5, 0.5, 0.5, 0.5, 0.5]
    rtn = robot.FrictionCompensationOnOff(1)
    print(f"FrictionCompensationOnOff rtn is {rtn}")
    rtn = robot.SetFrictionValue_level(lcoeff)
    print(f"SetFrictionValue_level rtn is {rtn}")
    rtn = robot.SetFrictionValue_wall(wcoeff)
    print(f"SetFrictionValue_wall rtn is {rtn}")
    rtn = robot.SetFrictionValue_ceiling(ccoeff)
    print(f"SetFrictionValue_ceiling rtn is {rtn}")
    rtn = robot.SetFrictionValue_freedom(fcoeff)
    print(f"SetFrictionValue_freedom rtn is {rtn}")
    robot.CloseRPC()

Consultar el código de error del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotErrorCode()``"
    "Descripción", "Consultar el código de error del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``[maincode subcode]``：Código de error del robot, maincode-código de error principal, subcode-código de error secundario"

Borrar el estado de error
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ResetAllError()``"
    "Descripción", "Borrar el estado de error; solo se pueden borrar los errores reiniciables"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de obtención del estado de fallo y borrado de errores del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]
    robot.MoveJ(joint_pos=p1Joint, tool=5, user=2, vel=50)
    time.sleep(1)
    error,[maincode, subcode] = robot.GetRobotErrorCode()
    print(f"robot maincode is {maincode}; subcode is {subcode}")
    time.sleep(1)
    robot.ResetAllError()
    time.sleep(1)
    error,[maincode, subcode] = robot.GetRobotErrorCode()
    print(f"robot maincode is {maincode}; subcode is {subcode}")
    robot.CloseRPC()

Establecer los parámetros de monitorización de temperatura y velocidad del ventilador de la caja de control de voltaje amplio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWideBoxTempFanMonitorParam(enable, period)``"
    "Descripción", "Establecer los parámetros de monitorización de temperatura y velocidad del ventilador de la caja de control de voltaje amplio"
    "Parámetros obligatorios", "- ``enable``：0-no habilitar la monitorización; 1-habilitar la monitorización
    - ``period``：Período de monitorización (s), rango 1-100"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener los parámetros de monitorización de temperatura y velocidad del ventilador de la caja de control de voltaje amplio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWideBoxTempFanMonitorParam()``"
    "Descripción", "Obtener los parámetros de monitorización de temperatura y velocidad del ventilador de la caja de control de voltaje amplio"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``enable``：0-no habilitar la monitorización; 1-habilitar la monitorización
    - ``period``：Período de monitorización (s), rango 1-100"

Ejemplo de código de obtención del estado de temperatura y corriente del ventilador de la caja de control de voltaje amplio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    robot.SetWideBoxTempFanMonitorParam(1, 2)
    error, enable, period = robot.GetWideBoxTempFanMonitorParam()
    print(f"GetWideBoxTempFanMonitorParam enable is:{enable},period is:{period}")
    for i in range(100):
        error, pkg = robot.GetRobotRealTimeState()
        print(f"robot ctrl box temp is:{pkg.wideVoltageCtrlBoxTemp},fan current is:{pkg.wideVoltageCtrlBoxFanCurrent}")
        time.sleep(0.1)
    rtn = robot.SetWideBoxTempFanMonitorParam(0, 2)
    print(f"SetWideBoxTempFanMonitorParam rtn is:{rtn}")
    error, enable, period = robot.GetWideBoxTempFanMonitorParam()
    print(f"GetWideBoxTempFanMonitorParam enable is:{enable},period is:{period}")
    for i in range(100):
        error, pkg = robot.GetRobotRealTimeState()
        print(f"robot ctrl box temp is:{pkg.wideVoltageCtrlBoxTemp},fan current is:{pkg.wideVoltageCtrlBoxFanCurrent}")
        time.sleep(0.1)
    robot.CloseRPC()

Establecer el punto de calibración de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFocusCalibPoint(pointNum, point)``"
    "Descripción", "Establecer el punto de calibración de foco"
    "Parámetros obligatorios", "- ``pointNum``：Número del punto de calibración de foco 1-8
    - ``point``：Coordenadas del punto de calibración"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Calcular el resultado de la calibración de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeFocusCalib(pointNum)``"
    "Descripción", "Calcular el resultado de la calibración de foco"
    "Parámetros obligatorios", "- ``pointNum``：Número de puntos de calibración"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``resultPos``：XYZ del resultado de la calibración
    - ``accuracy``：Error de precisión de la calibración"

Activar el seguimiento de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FocusStart(kp=50.0, kpredic=19.0, aMax=1440, vMax=180, type=0)``"
    "Descripción", "Activar el seguimiento de foco"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "- ``kp``：Parámetro proporcional, valor predeterminado 50.0
    - ``kpredic``：Parámetro de prealimentación, valor predeterminado 19.0
    - ``aMax``：Límite máximo de aceleración angular, valor predeterminado 1440°/s^2
    - ``vMax``：Límite máximo de velocidad angular, valor predeterminado 180°/s
    - ``type``：Bloqueo de la dirección del eje X (0-vector de entrada de referencia; 1-horizontal; 2-vertical), valor predeterminado 0"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Detener el seguimiento de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FocusEnd()``"
    "Descripción", "Detener el seguimiento de foco"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Establecer las coordenadas del foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFocusPosition(pos)``"
    "Descripción", "Establecer las coordenadas del foco"
    "Parámetros obligatorios", "- ``pos``：Coordenadas XYZ del foco"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de seguimiento de foco del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [186.331, 487.913, 209.850, 149.030, 0.688, -114.347]
    p1Joint = [-127.876, -75.341, 115.417, -122.741, -59.820, 74.300]
    p2Desc = [69.721, 535.073, 202.882, -144.406, -14.775, -89.012]
    p2Joint = [-101.780, -69.828, 110.917, -125.740, -127.841, 74.300]
    p3Desc = [146.861, 578.426, 205.598, 175.997, -36.178, -93.437]
    p3Joint = [-112.851, -60.191, 86.566, -80.676, -97.463, 74.300]
    p4Desc = [136.284, 509.876, 225.613, 178.987, 1.372, -100.696]
    p4Joint = [-116.397, -76.281, 113.845, -128.611, -88.654, 74.299]
    p5Desc = [138.395, 505.972, 298.016, 179.134, 2.147, -101.110]
    p5Joint = [-116.814, -82.333, 109.162, -118.662, -88.585, 74.302]
    p6Desc = [105.553, 454.325, 232.017, -179.426, 0.444, -99.952]
    p6Joint = [-115.649, -84.367, 122.447, -128.663, -90.432, 74.303]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 100, 0, 0, 0]
    robot.MoveJ(joint_pos=p1Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(3)
    robot.MoveJ(joint_pos=p4Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(4)
    rtn,coordRtn = robot.ComputeTcp4()
    print(f"4 Point ComputeTool {rtn} coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} "
          f"{coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0)
    error, p1Desc = robot.GetForwardKin(p1Joint)
    error, p2Desc = robot.GetForwardKin(p2Joint)
    error, p3Desc = robot.GetForwardKin(p3Joint)
    robot.SetFocusCalibPoint(1, p1Desc)
    robot.SetFocusCalibPoint(2, p2Desc)
    robot.SetFocusCalibPoint(3, p3Desc)
    rtn, resultPos, accuracy = robot.ComputeFocusCalib(pointNum=3)
    print(f"ComputeFocusCalib coord is {rtn} {resultPos[0]} {resultPos[1]} {resultPos[2]} accuracy is {accuracy}")
    rtn = robot.SetFocusPosition(resultPos)
    error, p5Desc = robot.GetForwardKin(p5Joint)
    error, p6Desc = robot.GetForwardKin(p6Joint)
    robot.MoveL(desc_pos=p5Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.MoveL(desc_pos=p6Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.FocusStart(50, 19, 710, 90, 0)
    robot.MoveL(desc_pos=p5Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.MoveL(desc_pos=p6Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.FocusEnd()
    robot.CloseRPC()

Activación de la función de calibración de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointSensitivityEnable(status)``"
    "Descripción", "Activación de la función de calibración de sensibilidad del sensor de par de las articulaciones"
    "Parámetros obligatorios", "- ``status``：0-desactivar; 1-activar"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Recogida de datos de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointSensitivityCollect()``"
    "Descripción", "Recogida de datos de sensibilidad del sensor de par de las articulaciones"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"
    
Obtener el resultado de la calibración de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointSensitivityCalibration()``"
    "Descripción", "Obtener el resultado de la calibración de sensibilidad del sensor de par de las articulaciones"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``calibResult``：Sensibilidad de las articulaciones j1~j6 [0-1]
    - ``linearityn``：Linealidad de las articulaciones j1~j6 [0-1]"

Obtener el error de histéresis del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointHysteresisError()``"
    "Descripción", "Obtener el error de histéresis del sensor de par de las articulaciones"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``hysteresisError``：Error de histéresis de las articulaciones j1~j6"

Obtener la repetibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointRepeatability()``"
    "Descripción", "Obtener la repetibilidad del sensor de par de las articulaciones"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``repeatability``：Repetibilidad de las articulaciones j1~j6"

Establecer los parámetros del sensor de fuerza de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAdmittanceParams(M, B, K, threshold, sensitivity, setZeroFlag)``"
    "Descripción", "Establecer los parámetros del sensor de fuerza de las articulaciones"
    "Parámetros obligatorios", "
    - ``M``：Coeficientes de masa J1-J6 [0.001 ~ 10]
    - ``B``：Coeficientes de amortiguación J1-J6 [0.001 ~ 10]
    - ``K``：Coeficientes de rigidez J1-J6 [0.001 ~ 10]
    - ``threshold``：Umbral de control de fuerza, Nm
    - ``sensitivity``：Sensibilidad, Nm/V, [0 ~ 10]
    - ``setZeroFlag``：Indicador de activación de la función; 0-desactivar; 1-activar; 2-posición 1 registrar punto cero; 3-posición 2 registrar punto cero"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Ejemplo de código de calibración automática de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.JointSensitivityEnable(0)
    rtn = robot.JointSensitivityEnable(1)
    print(f"JointSensitivityEnable rtn is {rtn}")
    curJPos = [0.0] * 6
    rtn, curJPos = robot.GetActualJointPosDegree(0)
    epos = [0.0] * 4
    offset_pos = [0.0] * 6
    jointPos1 = [curJPos[0], 0.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos1 = [0.0] * 6
    rtn, descPos1 = robot.GetForwardKin(jointPos1)
    robot.MoveJ(joint_pos=jointPos1, desc_pos=descPos1, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.2)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 1 rtn is {rtn}")
    time.sleep(0.1)
    jointPos2 = [curJPos[0], -30.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos2 = [0.0] * 6
    rtn, descPos2 = robot.GetForwardKin(jointPos2)
    robot.MoveJ(joint_pos=jointPos2, desc_pos=descPos2, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 2 rtn is {rtn}")
    time.sleep(0.1)
    jointPos3 = [curJPos[0], -60.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos3 = [0.0] * 6
    rtn, descPos3 = robot.GetForwardKin(jointPos3)
    robot.MoveJ(joint_pos=jointPos3, desc_pos=descPos3, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 3 rtn is {rtn}")
    time.sleep(0.1)
    jointPos4 = [curJPos[0], -90.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos4 = [0.0] * 6
    rtn, descPos4 = robot.GetForwardKin(jointPos4)
    robot.MoveJ(joint_pos=jointPos4, desc_pos=descPos4, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 4 rtn is {rtn}")
    time.sleep(0.1)
    jointPos5 = [curJPos[0], -120.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos5 = [0.0] * 6
    rtn, descPos5 = robot.GetForwardKin(jointPos5)
    robot.MoveJ(joint_pos=jointPos5, desc_pos=descPos5, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 5 rtn is {rtn}")
    time.sleep(0.1)
    jointPos6 = [curJPos[0], -150.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos6 = [0.0] * 6
    rtn, descPos6 = robot.GetForwardKin(jointPos6)
    robot.MoveJ(joint_pos=jointPos6, desc_pos=descPos6, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 6 rtn is {rtn}")
    time.sleep(0.1)
    jointPos7 = [curJPos[0], -180.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos7 = [0.0] * 6
    rtn, descPos7 = robot.GetForwardKin(jointPos7)
    robot.MoveJ(joint_pos=jointPos7, desc_pos=descPos7, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 7 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos6, desc_pos=descPos6, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 8 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos5, desc_pos=descPos5, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 9 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos4, desc_pos=descPos4, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 10 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos3, desc_pos=descPos3, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 11 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos2, desc_pos=descPos2, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 12 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos1, desc_pos=descPos1, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.2)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 13 rtn is {rtn}")
    time.sleep(0.1)
    calibResult = [0.0] * 6
    linearity = [0.0] * 6
    rtn,calibResult, linearity = robot.JointSensitivityCalibration()
    print(f"JointSensitivityCalibration rtn is {rtn}")
    rtn = robot.JointSensitivityEnable(0)
    print(f"JointSensitivityEnable rtn is {rtn}")
    print(f"jointSensor Calib result is {calibResult[0]},{calibResult[1]},{calibResult[2]},{calibResult[3]},{calibResult[4]},{calibResult[5]}")
    print( f"jointSensor linearity is {linearity[0]},{linearity[1]},{linearity[2]},{linearity[3]},{linearity[4]},{linearity[5]}")
    hysteresisError = [0.0] * 6
    rtn,hysteresisError = robot.JointHysteresisError()
    print(f"JointHysteresisError result is {hysteresisError[0]},{hysteresisError[1]},{hysteresisError[2]},{hysteresisError[3]},{hysteresisError[4]},{hysteresisError[5]}")
    repeatability = [0.0] * 6
    rtn,repeatability = robot.JointRepeatability()
    print(f"JointRepeatability result is {repeatability[0]},{repeatability[1]},{repeatability[2]},{repeatability[3]},{repeatability[4]},{repeatability[5]}")
    M = [1.0] * 6
    B = [1.0] * 6
    K = [0.0] * 6
    threshold = [1.0] * 6
    setZeroFlag = 1
    rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag)
    print(f"SetAdmittanceParams rtn is {rtn}")
    robot.CloseRPC()

Obtener el número de tramas de error de los 8 puertos esclavos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSlavePortErrCounter()``"
    "Descripción", "Obtener el número de tramas de error de los 8 puertos esclavos del robot"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``inRecvErr``：Número de tramas de error de recepción de entrada
    - ``inCRCErr``：Número de tramas de error CRC de entrada
    - ``inTransmitErr``：Número de tramas de error de reenvío de entrada
    - ``inLinkErr``：Número de tramas de error de enlace de entrada
    - ``outRecvErr``：Número de tramas de error de recepción de salida
    - ``outCRCErr``：Número de tramas de error CRC de salida
    - ``outTransmitErr``：Número de tramas de error de reenvío de salida
    - ``outLinkErr``：Número de tramas de error de enlace de salida"

Puesta a cero de las tramas de error del puerto esclavo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointSensitivityEnable(slaveID)``"
    "Descripción", "Puesta a cero de las tramas de error del puerto esclavo"
    "Parámetros obligatorios", "- ``slaveID``：Número de esclavo 0~7"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Ejemplo de código de obtención de tramas de error del puerto esclavo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    inRecvErr = [0] * 8
    inCRCErr = [0] * 8
    inTransmitErr = [0] * 8
    inLinkErr = [0] * 8
    outRecvErr = [0] * 8
    outCRCErr = [0] * 8
    outTransmitErr = [0] * 8
    outLinkErr = [0] * 8
    rtn,inRecvErr, inCRCErr, inTransmitErr, inLinkErr, outRecvErr, outCRCErr, outTransmitErr, outLinkErr = robot.GetSlavePortErrCounter()
    for i in range(8):
        if inRecvErr[i] != 0:
            print(f"inRecvErr {i} is {inRecvErr[i]}")
        if inCRCErr[i] != 0:
            print(f"inCRCErr {i} is {inCRCErr[i]}")
        if inTransmitErr[i] != 0:
            print(f"inTransmitErr {i} is {inTransmitErr[i]}")
        if inLinkErr[i] != 0:
            print(f"inLinkErr {i} is {inLinkErr[i]}")
        if outRecvErr[i] != 0:
            print(f"outRecvErr {i} is {outRecvErr[i]}")
        if outCRCErr[i] != 0:
            print(f"outCRCErr {i} is {outCRCErr[i]}")
        if outTransmitErr[i] != 0:
            print(f"outTransmitErr {i} is {outTransmitErr[i]}")
        if outLinkErr[i] != 0:
            print(f"outLinkErr {i} is {outLinkErr[i]}")
    print("others has no err!")
    for i in range(8):
        robot.SlavePortErrCounterClear(i)
    robot.CloseRPC()

Establecer el coeficiente de prealimentación de velocidad de cada eje
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetVelFeedForwardRatio(radio)``"
    "Descripción", "Establecer el coeficiente de prealimentación de velocidad de cada eje"
    "Parámetros obligatorios", "- ``radio``：Coeficiente de prealimentación de velocidad de cada eje"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "Código de error éxito-0  fallo- errcode"

Obtener el coeficiente de prealimentación de velocidad de cada eje
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetVelFeedForwardRatio()``"
    "Descripción", "Obtener el coeficiente de prealimentación de velocidad de cada eje"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode
    - ``radio``：Coeficiente de prealimentación de velocidad de cada eje"

Ejemplo de código del coeficiente de prealimentación de velocidad del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Establecer comunicación con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    setRadio = [1.0, 1.0, 1.0, 1.0, 1.0, 1.0]
    robot.SetVelFeedForwardRatio(setRadio)
    getRadio = [0.0] * 6
    rtn,getRadio = robot.GetVelFeedForwardRatio()
    print(f"{getRadio[0]},{getRadio[1]},{getRadio[2]},{getRadio[3]},{getRadio[4]},{getRadio[5]}")
    robot.CloseRPC()

Calibración TCP del sensor fotoeléctrico - calcular RPY de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TCPComputeRPY(Btool, Etool, sensor, radius, dz)``"
    "Descripción", "Calibración TCP del sensor fotoeléctrico - calcular RPY de la herramienta"
    "Parámetros obligatorios", "
    - ``Btool``：Posición cartesiana del robot
    - ``Etool``：Valor actual del sistema de coordenadas de herramienta
    - ``Btsenserool``：Valor actual del sistema de coordenadas del sensor (aún no disponible)
    - ``radius``：Radio del movimiento circular mm (aún no disponible)
    - ``dz``：Distancia de movimiento a lo largo de la dirección negativa del eje z del sistema de coordenadas base; cuando dz = 10000, la función devuelve directamente el RPY de la herramienta"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Calibración TCP del sensor fotoeléctrico - calcular XYZ de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TCPComputeXYZ(select, originDirection, pos1, pos2, pos3, pos4)``"
    "Descripción", "Calibración TCP del sensor fotoeléctrico - calcular XYZ de la herramienta"
    "Parámetros obligatorios", "
    - ``select``：0-calcular TCP de la herramienta; 1-calcular el origen del sensor; 2-calcular la orientación del sensor; 3-devolver directamente el TCP de la herramienta; 4-registrar el sistema de coordenadas de la pieza y el sistema de coordenadas de herramienta actuales
    - ``originDirection``：0-dirección X; 1-dirección Y; 2-dirección Z
    - ``pos1``：Posición cartesiana 1 del robot
    - ``pos2``：Posición cartesiana 2 del robot
    - ``pos3``：Posición cartesiana 3 del robot
    - ``pos4``：Posición cartesiana 4 del robot"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "
    - Código de error éxito-0  fallo- errcode
    - Valor de retorno (devuelto al llamar con éxito) Valor XYZ de la herramienta TCP"

Calibración TCP del sensor fotoeléctrico - iniciar el registro de la posición del centro de la brida del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TCPRecordFlangePosStart()``"
    "Descripción", "Calibración TCP del sensor fotoeléctrico - iniciar el registro de la posición del centro de la brida del extremo"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Calibración TCP del sensor fotoeléctrico - detener el registro de la posición del centro de la brida del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TCPRecordFlangePosEnd()``"
    "Descripción", "Calibración TCP del sensor fotoeléctrico - detener el registro de la posición del centro de la brida del extremo"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo- errcode"

Calibración TCP del sensor fotoeléctrico - obtener la posición del centro de la herramienta del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TCPGetRecordFlangePos()``"
    "Descripción", "Calibración TCP del sensor fotoeléctrico - obtener la posición del centro de la herramienta del extremo"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "
    - Código de error éxito-0  fallo- errcode
    - Valor de retorno (devuelto al llamar con éxito) Posición del centro de la herramienta TCP (x,y,z)"

Calibración TCP del sensor fotoeléctrico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PhotoelectricSensorTCPCalibration(self, luaFile, offsetX)``"
    "Descripción", "Calibración TCP del sensor fotoeléctrico"
    "Parámetros obligatorios", "
    - ``luaFile``：Nombre del programa lua de calibración automática: como `FR_CalibrateTheToolTcp.lua`
    - ``offsetX``：Desplazamiento del punto de enseñanza (x,y,z) mm"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "
    - Código de error éxito-0  fallo- errcode
    - Valor de retorno (devuelto al llamar con éxito) Valor XYZ de la herramienta TCP"

Ejemplo de código de calibración TCP del sensor fotoeléctrico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    offset = [10.0, 10.0, 3.0]
    TCP = [0.0] * 6
    rtn, TCP = robot.PhotoelectricSensorTCPCalibration("FR_CalibrateTheToolTcp.lua", offset)
    print(f"PhotoelectricSensorTCPCalibration rtn is {rtn},{TCP[0]},{TCP[1]},{TCP[2]},{TCP[3]},{TCP[4]},{TCP[5]}")
    robot.CloseRPC()
    return 0

Establecer la velocidad en tiempo real (trama de instrucción, baja latencia)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSpeedInstant(self, vel)``"
    "Descripción", "Establecer la velocidad en tiempo real (trama de instrucción, baja latencia)"
    "Parámetros obligatorios", "
    - ``vel``：Porcentaje de velocidad, rango [0~100]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "
    - Código de error éxito-0  fallo- errcode"

Establecer el desplazamiento en tiempo real de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWeaveOffsetRT(self, offset)``"
    "Descripción", "Establecer el desplazamiento en tiempo real de la oscilación"
    "Parámetros obligatorios", "
    - ``offset``：Desplazamiento en tiempo real [x,y,z,rx,ry,rz], unidad [mm, °]"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "
    - Código de error éxito-0  fallo- errcode"

Ejemplo de código de prueba de regulación de velocidad y desplazamiento en tiempo real de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    import threading


    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        epos = [0.0, 0.0, 0.0, 0.0]
        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        j1 = [5.027, -84.331, -75.139, -103.690, 86.379, 20.794]
        d1 = [324.752, -83.339, 366.314, -172.321, -0.936, -106.047]

        j2 = [-35.335, -117.598, -57.174, -95.234, 90.001, -19.560]
        d2 = [324.999, -355.439, 260.000, 179.995, 0.003, -105.775]

        j3 = [59.787, -117.594, -57.183, -95.222, 90.006, 75.562]
        d3 = [324.998, 355.441, 260.002, 179.995, 0.003, -105.775]

        rtn = 0

        print("\nStep 1: MoveJ to start point")
        rtn = robot.MoveJ(joint_pos=j1, desc_pos=d1, tool=1, user=0, vel=100, acc=100, ovl=50,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        print(f"  MoveJ(j1) rtn={rtn}")
        time.sleep(0.5)

        print("\nStep 2: MoveJ to weave entry point")
        rtn = robot.MoveJ(joint_pos=j2, desc_pos=d2, tool=1, user=0, vel=100, acc=100, ovl=50,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        print(f"  MoveJ(j2) rtn={rtn}")
        time.sleep(0.5)

        print("\nStep 3: WeaveStart + MoveL in background thread")
        robot.WeaveStart(0)

        weave_running = True
        move_rtn = [0]  

        def weave_move_thread():
            rtn_val = robot.MoveL(joint_pos=j3, desc_pos=d3, tool=1, user=0, vel=100, acc=100, ovl=5,
                                blendR=-1, offset_flag=0, exaxis_pos=epos, search=0,
                                offset_pos=offset_pos, config=5, velAccParamMode=0, overSpeedStrategy=0, speedPercent=10)
            print(f"  MoveL(weave) thread finished, rtn={rtn_val}")
            move_rtn[0] = rtn_val
            nonlocal weave_running
            weave_running = False

        weave_thread = threading.Thread(target=weave_move_thread)
        weave_thread.daemon = True
        weave_thread.start()
        time.sleep(0.5)  

        print("\nStep 4: SetSpeed test during weaving")
        speed_values = [20, 50, 80, 30, 60, 10]
        for speed in speed_values:
            if not weave_running:
                break
            rtn = robot.SetSpeedInstant(speed)
            print(f"  SetSpeed({speed}) -> rtn={rtn}")
            # rtn, pkg = robot.GetRobotRealTimeState()
            # print(f"target_TCP_CmpSpeed: [{', '.join([f'{x:.3f}' for x in pkg.target_TCP_CmpSpeed])}]")
            time.sleep(5)

        time.sleep(5)

        print("\nStep 5: SetWeaveOffsetRT test (50 iterations, delta=0.1)")
        accum_offset = 0.0
        for i in range(50):
            if not weave_running:
                break
            accum_offset += 1
            weave_offset = [0.0, 0.0, accum_offset, 0.0, 0.0, 0.0]
            rtn = robot.SetWeaveOffsetRT(weave_offset)
            rtn, pkg = robot.GetRobotRealTimeState()
            print(f"  [{i+1}/50] SetWeaveOffsetRT(x={accum_offset:.1f}) -> rtn={rtn}, "
                f"TCP_pos=({pkg.tl_cur_pos[0]:.2f},{pkg.tl_cur_pos[1]:.2f},{pkg.tl_cur_pos[2]:.2f})")
            time.sleep(0.1)

        print("\nStep 6: Wait for weave MoveL, then WeaveEnd")
        weave_thread.join()
        robot.WeaveEnd(0)
        time.sleep(0.5)

        print("\nStep 7: MoveL back to start")
        rtn = robot.MoveL(joint_pos=j1, desc_pos=d1, tool=1, user=0, vel=100, acc=100, ovl=50,
                        blendR=-1, offset_flag=0, exaxis_pos=epos, search=0,
                        offset_pos=offset_pos, config=50, velAccParamMode=0, overSpeedStrategy=0, speedPercent=10)
        print(f"  MoveL(back) rtn={rtn}")

        rtn, pkg = robot.GetRobotRealTimeState()
        print(f"\n  Final robot state: main_code={pkg.main_code}, sub_code={pkg.sub_code}")
        
        robot.CloseRPC()


    if __name__ == "__main__":
        main()  
        
Establecer la velocidad física en tiempo real
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetPhySpeedInstant(self, speed)``"
    "Descripción", "Establecer la velocidad física en tiempo real"
    "Parámetros obligatorios", "
    - ``speed``：Valor de la velocidad física, mm/s"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "
    - Código de error éxito-0  fallo- errcode"

Ejemplo de código de establecimiento de la velocidad física en tiempo real
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    import threading


    def robot_thread_func(robot):
    """Hilo en segundo plano: leer la entrada del usuario y establecer la velocidad en tiempo real"""
    while True:
        try:
            input_val = input("Please input speed value: ")
            input_val = float(input_val)
            rtn = robot.SetPhySpeedInstant(input_val)
            print(f"SetPhySpeedInstant({input_val}) rtn is {rtn}")
        except ValueError:
            print("Invalid number!")


    def main():
        # Establecer comunicación con el controlador del robot
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        # Iniciar el hilo en segundo plano para la entrada de velocidad
        th = threading.Thread(target=robot_thread_func, args=(robot,))
        th.daemon = True
        th.start()

        # Definir los puntos de movimiento
        j1 = [-60.206, -49.449, 79.476, -124.322, -88.416, -45.209]
        d1 = [-412.929, 510.912, 94.557, -175.850, -1.933, 74.992]
        j2 = [-141.282, -40.962, 62.359, -110.496, -85.512, -126.379]
        d2 = [586.847, 510.915, 94.560, -175.851, -1.934, 74.991]

        ex = [0.0, 0.0, 0.0, 0.0]
        zeroOff = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        # Bucle infinito: MoveL de ida y vuelta entre dos puntos
        while True:
            rtn = robot.MoveL(desc_pos=d1, tool=1, user=0, joint_pos=j1,
                            vel=100, acc=100, ovl=100, blendR=-1, blendMode=0,
                            exaxis_pos=ex, search=0, offset_flag=0, offset_pos=zeroOff,
                            oacc=100, config=0, velAccParamMode=0, overSpeedStrategy=0, speedPercent=10)
            print(f"MoveL j1->d1 rtn: {rtn}")

            rtn = robot.MoveL(desc_pos=d2, tool=1, user=0, joint_pos=j2,
                            vel=100, acc=100, ovl=100, blendR=-1, blendMode=0,
                            exaxis_pos=ex, search=0, offset_flag=0, offset_pos=zeroOff,
                            oacc=100, config=0, velAccParamMode=0, overSpeedStrategy=0, speedPercent=10)
            print(f"MoveL j2->d2 rtn: {rtn}")

        # Cerrar la conexión (nunca se alcanza debido al bucle infinito)
        robot.CloseRPC()

    if __name__ == "__main__":
        main()