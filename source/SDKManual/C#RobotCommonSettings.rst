Configuraciones habituales del robot
=====================================

.. toctree:: 
    :maxdepth: 5

Establecer el punto de referencia de la herramienta - método de seis puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el punto de referencia de la herramienta - método de seis puntos 
    * @param [in] point_num Número de punto, rango [1~6] 
    * @return Código de error 
    */ 
    int SetToolPoint(int point_num); 

Calcular el sistema de coordenadas de herramienta - método de seis puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Calcular el sistema de coordenadas de herramienta
    * @param [out] tcp_pose Sistema de coordenadas de herramienta
    * @return Código de error 
    */ 
    int ComputeTool(ref DescPose tcp_pose); 

Establecer el punto de referencia de la herramienta - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el punto de referencia de la herramienta - método de cuatro puntos 
    * @param [in] point_num Número de punto, rango [1~4] 
    * @return Código de error 
    */ 
    int SetTcp4RefPoint(int point_num);

Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Calcular el sistema de coordenadas de herramienta
    * @param [out] tcp_pose Sistema de coordenadas de herramienta
    * @return Código de error 
    */ 
    int ComputeTcp4(ref DescPose tcp_pose);

Establecer el sistema de coordenadas de herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el sistema de coordenadas de herramienta
    * @param  [in] id Número del sistema de coordenadas, rango [0~14]
    * @param  [in] coord  Pose del centro de herramienta respecto al centro de la brida del extremo
    * @param  [in] type  0-sistema de coordenadas de herramienta, 1-sistema de coordenadas del sensor
    * @param  [in] install Posición de instalación, 0-extremo del robot, 1-exterior del robot
    * param   [in] toolID ID de la herramienta
    * @param  [in] loadNum Número de carga
    * @return  Código de error
    */
    int SetToolCoord(int id, DescPose coord, int type, int install,int toolID, int loadNum);

Calcular el sistema de coordenadas de herramienta a partir de la información de puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Calcular el sistema de coordenadas de herramienta a partir de la información de puntos
    * @param [in] method Método de cálculo; 0-método de cuatro puntos; 1-método de seis puntos
    * @param [in] pos Conjunto de posiciones articulares; en el método de cuatro puntos la longitud del array es 4, en el método de seis puntos la longitud es 6
    * @return Código de error
    */

    int ComputeToolCoordWithPoints(int method, JointPos[] pos, ref DescPose coordRtn)  

Establecer la lista de sistemas de coordenadas de herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer la lista de sistemas de coordenadas de herramienta
    * @param  [in] id Número del sistema de coordenadas, rango [0~14]
    * @param  [in] coord  Pose del centro de herramienta respecto al centro de la brida del extremo
    * @param  [in] type  0-sistema de coordenadas de herramienta, 1-sistema de coordenadas del sensor
    * @param  [in] install Posición de instalación, 0-extremo del robot, 1-exterior del robot
    * @param  [in] loadNum Número de carga
    * @return  Código de error
    */
    int SetToolList(int id, DescPose coord, int type, int install, int loadNum);  

Obtener el sistema de coordenadas de herramienta actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el sistema de coordenadas de herramienta actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] desc_pos Pose del sistema de coordenadas de herramienta
    * @return  Código de error
    */
    int GetTCPOffset(byte flag, ref DescPose desc_pos); 

Ejemplo de código de operación del sistema de coordenadas de herramienta del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button18_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(186.331f, 487.913f, 209.850f, 149.030f, 0.688f, -114.347f);
        JointPos p1Joint = new JointPos(-127.876f, -75.341f, 115.417f, -122.741f, -59.820f, 74.300f);

        DescPose p2Desc = new DescPose(69.721f, 535.073f, 202.882f, -144.406f, -14.775f, -89.012f);
        JointPos p2Joint = new JointPos(-101.780f, -69.828f, 110.917f, -125.740f, -127.841f, 74.300f);

        DescPose p3Desc = new DescPose(146.861f, 578.426f, 205.598f, 175.997f, -36.178f, -93.437f);
        JointPos p3Joint = new JointPos(-112.851f, -60.191f, 86.566f, -80.676f, -97.463f, 74.300f);

        DescPose p4Desc = new DescPose(136.284f, 509.876f, 225.613f, 178.987f, 1.372f, -100.696f);
        JointPos p4Joint = new JointPos(-116.397f, -76.281f, 113.845f, -128.611f, -88.654f, 74.299f);

        DescPose p5Desc = new DescPose(138.395f, 505.972f, 298.016f, 179.134f, 2.147f, -101.110f);
        JointPos p5Joint = new JointPos(-116.814f, -82.333f, 109.162f, -118.662f, -88.585f, 74.302f);

        DescPose p6Desc = new DescPose(105.553f, 454.325f, 232.017f, -179.426f, 0.444f, -99.952f);
        JointPos p6Joint = new JointPos(-115.649f, -84.367f, 122.447f, -128.663f, -90.432f, 74.303f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        JointPos[] posJ = new JointPos[] { p1Joint, p2Joint, p3Joint, p4Joint, p5Joint, p6Joint };
        DescPose coordRtn = new DescPose();
        int rtn = robot.ComputeToolCoordWithPoints(1, posJ, ref coordRtn);
        Console.WriteLine($"ComputeToolCoordWithPoints    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.MoveJ( p1Joint,  p1Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(3);
        robot.MoveJ( p4Joint,  p4Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(4);
        robot.MoveJ( p5Joint,  p5Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(5);
        robot.MoveJ( p6Joint,  p6Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(6);
        rtn = robot.ComputeTool(ref coordRtn);
        Console.WriteLine($"6 Point ComputeTool        {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");
        robot.SetToolList(1,  coordRtn, 0, 0, 0);

        robot.MoveJ( p1Joint,  p1Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ( p4Joint,  p4Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(4);
        rtn = robot.ComputeTcp4(ref coordRtn);
        Console.WriteLine($"4 Point ComputeTool        {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetToolCoord(2, coordRtn, 0, 0, 1, 0);

        DescPose getCoord = new DescPose();
        rtn = robot.GetTCPOffset(0, ref getCoord);
        Console.WriteLine($"GetTCPOffset    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");
    }

Establecer el punto de referencia de la herramienta externa - método de tres puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el punto de referencia de la herramienta externa - método de tres puntos 
    * @param [in] point_num Número de punto, rango [1~3] 
    * @return Código de error 
    */ 
    int SetExTCPPoint(int point_num); 

Calcular el sistema de coordenadas de herramienta externa - método de tres puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
    
    /** 
    * @brief Calcular el sistema de coordenadas de herramienta externa - método de tres puntos
    * @param [out] tcp_pose Sistema de coordenadas de herramienta externa
    * @return Código de error 
    */ 
    int ComputeExTCF(ref DescPose tcp_pose); 

Establecer el sistema de coordenadas de herramienta externa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el sistema de coordenadas de herramienta externa 
    * @param [in] id Número del sistema de coordenadas; 20-39 corresponden al sistema de coordenadas de herramienta externa 0-19
    * @param [in] etcp Pose del centro de herramienta respecto al centro de la brida del extremo 
    * @param [in] etool Pendiente de definir 
    * @return Código de error 
    */
    int SetExToolCoord(int id, DescPose etcp, DescPose etool); 

Establecer la lista de sistemas de coordenadas de herramienta externa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer la lista de sistemas de coordenadas de herramienta externa
    * @param  [in] Número del sistema de coordenadas; 20-39 corresponden al sistema de coordenadas de herramienta externa 0-19
    * @param  [in] etcp  Pose del centro de herramienta respecto al centro de la brida del extremo
    * @param  [in] etool  Pendiente de definir
    * @return  Código de error
    */
    int SetExToolList(int id, DescPose etcp, DescPose etool); 

Calcular el sistema de coordenadas de pieza a partir de la información de puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Calcular el sistema de coordenadas de pieza a partir de la información de puntos
    * @param [in] method Método de cálculo; 0: origen-eje x-eje z  1: origen-eje x-plano xy
    * @param [in] pos Conjunto de tres posiciones TCP
    * @param [in] refFrame Sistema de coordenadas de referencia
    * @return Código de error
    */
    int ComputeWObjCoordWithPoints(int method, DescPose[] pos, int refFrame, ref DescPose coordRtn)

Ejemplo de código de operación del sistema de coordenadas de herramienta externa del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button20_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(-89.606f, 779.517f, 193.516f, 178.000f, 0.476f, -92.484f);
        JointPos p1Joint = new JointPos(-108.145f, -50.137f, 85.818f, -125.599f, -87.946f, 74.329f);

        DescPose p2Desc = new DescPose(-24.656f, 850.384f, 191.361f, 177.079f, -2.058f, -95.355f);
        JointPos p2Joint = new JointPos(-111.024f, -41.538f, 69.222f, -114.913f, -87.743f, 74.329f);

        DescPose p3Desc = new DescPose(-99.813f, 766.661f, 241.878f, -176.817f, 1.917f, -91.604f);
        JointPos p3Joint = new JointPos(-107.266f, -56.116f, 85.971f, -122.560f, -92.548f, 74.331f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = new DescPose[] { p1Desc, p2Desc, p3Desc };
        DescPose coordRtn = new DescPose();

        robot.MoveJ( p1Joint,  p1Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(3);
        int rtn = robot.ComputeExTCF(ref coordRtn);
        Console.WriteLine($"ComputeExTCF                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetExToolCoord(1,  coordRtn,  offdese);
        robot.SetExToolList(1,  coordRtn,  offdese);
    }

Establecer el punto de referencia del sistema de coordenadas de pieza - método de tres puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el punto de referencia de la pieza - método de tres puntos 
    * @param [in] point_num Número de punto, rango [1~3]  
    * @return Código de error 
    */ 
    int SetWObjCoordPoint(int point_num); 

Calcular el sistema de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Calcular el sistema de coordenadas de pieza
    * @param [in] method Método de cálculo 0: origen-eje x-eje z  1: origen-eje x-plano xy
    * @param [in] refFrame Sistema de coordenadas de referencia
    * @param [out] wobj_pose Sistema de coordenadas de pieza
    * @return Código de error
    */
    int ComputeWObjCoord(int method, int refFrame, ref DescPose wobj_pose); 

Establecer el sistema de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el sistema de coordenadas de pieza
    * @param  [in] id Número del sistema de coordenadas, rango [1~15]
    * @param  [in] coord  Pose del sistema de coordenadas de pieza respecto al centro de la brida del extremo
    * @param  [in] refFrame Sistema de coordenadas de referencia
    * @return  Código de error
    */
    int SetWObjCoord(int id, DescPose coord, int refFrame);

Establecer la lista de sistemas de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer la lista de sistemas de coordenadas de pieza
    * @param  [in] id Número del sistema de coordenadas, rango [0~14] 
    * @param  [in] coord  Pose del sistema de coordenadas de pieza respecto al centro de la brida del extremo
    * @param  [in] refFrame Sistema de coordenadas de referencia
    * @return  Código de error
    */    
    int SetWObjList(int id, DescPose coord, int refFrame);

Obtener el sistema de coordenadas de pieza actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el sistema de coordenadas de pieza actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] desc_pos Pose del sistema de coordenadas de pieza
    * @return  Código de error
    */   
    int GetWObjOffset(byte flag, ref DescPose desc_pos); 

Ejemplo de código de operación del sistema de coordenadas de pieza del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button19_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint = new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc = new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint = new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc = new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint = new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,ref p1Desc);
        robot.GetForwardKin(p2Joint,ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = new DescPose[] { p1Desc, p2Desc, p3Desc };
        DescPose coordRtn = new DescPose();
        int rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, ref coordRtn);
        Console.WriteLine($"ComputeWObjCoordWithPoints    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.MoveJ( p1Joint,  p1Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(3);
        rtn = robot.ComputeWObjCoord(1, 0, ref coordRtn);
        Console.WriteLine($"ComputeWObjCoord                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetWObjCoord(1,  coordRtn, 0);
        robot.SetWObjList(1,  coordRtn, 0);

        DescPose getWobjDesc = new DescPose();
        rtn = robot.GetWObjOffset(0, ref getWobjDesc);
        Console.WriteLine($"GetWObjOffset                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");   
    } 

Establecer la velocidad global
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer la velocidad global
    * @param  [in]  vel  Porcentaje de velocidad, rango [0~100]
    * @return  Código de error
    */
    int SetSpeed(int vel); 

Establecer la aceleración del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la aceleración del robot
    * @param [in] acc Porcentaje de aceleración del robot
    * @return Código de error
    */
    int SetOaccScale(double acc)

Obtener la velocidad predeterminada del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la velocidad predeterminada del robot
    * @param  [out]  vel  Velocidad, unidad mm/s
    * @return  Código de error
    */   
    int GetDefaultTransVel(ref double vel); 

Establecer el peso de la carga del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el peso de la carga del extremo
    * @param  [in] loadNum Número de carga
    * @param  [in] weight  Peso de la carga, unidad kg
    * @return  Código de error
    */
    int SetLoadWeight(int loadNum, float weight)

Establecer las coordenadas del centro de gravedad de la carga del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer las coordenadas del centro de gravedad de la carga del extremo
    * @param  [in] coord Coordenadas del centro de gravedad, unidad mm
    * @return  Código de error
    */
    int SetLoadCoord(DescTran coord); 

Obtener el peso de la carga actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el peso de la carga actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] weight Peso de la carga, unidad kg
    * @return  Código de error
    */
    int GetTargetPayload(byte flag, ref double weight); 

Obtener el centro de gravedad de la carga actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el centro de gravedad de la carga actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] cog Centro de gravedad de la carga, unidad mm
    * @return  Código de error
    */   
    int GetTargetPayloadCog(byte flag, ref DescTran cog);

Establecer el modo de instalación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el modo de instalación del robot
    * @param  [in] install  Modo de instalación, 0-instalación vertical, 1-instalación lateral, 2-instalación invertida
    * @return  Código de error
    */
    int SetRobotInstallPos(byte install); 

Establecer el ángulo de instalación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el ángulo de instalación del robot, instalación libre
    * @param  [in] yangle  Ángulo de inclinación
    * @param  [in] zangle  Ángulo de rotación
    * @return  Código de error
    */
    int SetRobotInstallAngle(double yangle, double zangle); 

Obtener el ángulo de instalación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el ángulo de instalación del robot
    * @param  [out] yangle Ángulo de inclinación
    * @param  [out] zangle Ángulo de rotación
    * @return  Código de error
    */
    int GetRobotInstallAngle(ref double yangle, ref double zangle); 

Establecer el valor de una variable del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el valor de una variable del sistema
    * @param  [in]  id  Número de la variable, rango [1~20]
    * @param  [in]  value Valor de la variable
    * @return  Código de error
    */
    int SetSysVarValue(int id, double value); 

Obtener el valor de una variable del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el valor de una variable del sistema
    * @param  [in] id Número de la variable del sistema, rango [1~20]
    * @param  [out] value  Valor de la variable del sistema
    * @return  Código de error
    */
    int GetSysVarValue(int id, ref double value); 

Ejemplo de código de configuraciones habituales del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button21_Click(object sender, EventArgs e)
    {
        for (int i = 1; i < 100; i++)
        {
            robot.SetSpeed(i);
            robot.SetOaccScale(i);
            Thread.Sleep(30);
        }

        double defaultVel = 0.0f;
        robot.GetDefaultTransVel(ref defaultVel);
        Console.WriteLine($"GetDefaultTransVel is {defaultVel}");

        for (int i = 1; i < 21; i++)
        {
            robot.SetSysVarValue(i, i + 0.5f);
            Thread.Sleep(100);
        }

        for (int i = 1; i < 21; i++)
        {
            double value = 0;
            robot.GetSysVarValue(i, ref value);
            Console.WriteLine($"sys value  {i} is :{value}");
            Thread.Sleep(100);
        }

        robot.SetLoadWeight(0, 2.5f);

        DescTran loadCoord = new DescTran();
        loadCoord.x = 3.0f;
        loadCoord.y = 4.0f;
        loadCoord.z = 5.0f;
        robot.SetLoadCoord( loadCoord);

        Thread.Sleep(1000);

        double getLoad = 0.0f;
        robot.GetTargetPayload(0, ref getLoad);

        DescTran getLoadTran = new DescTran();
        robot.GetTargetPayloadCog(0, ref getLoadTran);
        Console.WriteLine($"get load is {getLoad}; get load cog is {getLoadTran.x} {getLoadTran.y} {getLoadTran.z}");

        robot.SetRobotInstallPos(0);
        robot.SetRobotInstallAngle(15.0f, 25.0f);

        double anglex = 0.0f;
        double angley = 0.0f;
        robot.GetRobotInstallAngle(ref anglex, ref angley);
        Console.WriteLine($"GetRobotInstallAngle x:  {anglex};  y:  {angley}");
    }

Interruptor de compensación de fricción de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Interruptor de compensación de fricción de las articulaciones 
    * @param [in] state 0-desactivado, 1-activado 
    * @return Código de error 
    */ 
    int FrictionCompensationOnOff(byte state); 

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación vertical
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación vertical
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    int SetFrictionValue_level(double[] coeff);

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación lateral
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación lateral
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    int SetFrictionValue_wall(double[] coeff); 

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación invertida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación invertida
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    int SetFrictionValue_ceiling(double[] coeff);

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación libre
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación libre
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    int SetFrictionValue_freedom(double[] coeff);
       
Ejemplo de código de configuración de compensación de fricción de las articulaciones del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        double[] lcoeff = { 0.9f, 0.9f, 0.9f, 0.9f, 0.9f, 0.9f };
        double[] wcoeff = { 0.4f, 0.4f, 0.4f, 0.4f, 0.4f, 0.4f };
        double[] ccoeff = { 0.6f, 0.6f, 0.6f, 0.6f, 0.6f, 0.6f };
        double[] fcoeff = { 0.5f, 0.5f, 0.5f, 0.5f, 0.5f, 0.5f };

        int rtn = robot.FrictionCompensationOnOff(1);
        Console.WriteLine($"FrictionCompensationOnOff rtn is{rtn}");

        rtn = robot.SetFrictionValue_level(lcoeff);
        Console.WriteLine($"SetFrictionValue_level rtn is {rtn}");

        rtn = robot.SetFrictionValue_wall(wcoeff);
        Console.WriteLine($"SetFrictionValue_wall rtn is{rtn}");

        rtn = robot.SetFrictionValue_ceiling(ccoeff);
        Console.WriteLine($"SetFrictionValue_ceiling rtn is {rtn}");

        rtn = robot.SetFrictionValue_freedom(fcoeff);
        Console.WriteLine($"SetFrictionValue_freedom rtn is {rtn}");
    }

Consultar el código de error del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Consultar el código de error del robot 
    * @param [out] maincode   Código de error principal
    * @param [out] subcode    Código de error secundario
    * @return Código de error 
    */ 
    int GetRobotErrorCode(ref int maincode, ref int subcode);

Borrado del estado de error
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Borrado del estado de error
    * @return  Código de error
    */
    int ResetAllError(); 

Ejemplo de código de obtención del estado de fallo y borrado de errores del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        int maincode=0, subcode=0;
        robot.GetRobotErrorCode(ref maincode, ref subcode);
        Console.WriteLine($"robot maincode is{maincode};  subcode is {subcode}" );

        robot.ResetAllError();

        Thread.Sleep(1000);

        robot.GetRobotErrorCode(ref maincode, ref subcode);
        Console.WriteLine($"robot maincode is{maincode};  subcode is{subcode}");
    }

Establecer los parámetros de monitorización de temperatura y velocidad del ventilador del armario de control de tensión amplia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer los parámetros de monitorización de temperatura y velocidad del ventilador del armario de control de tensión amplia
    * @param [in] enable 0-no habilitar la monitorización; 1-habilitar la monitorización
    * @param [in] period Período de monitorización (s), rango 1-100
    * @return Código de error
    */
    int SetWideBoxTempFanMonitorParam(int enable, int period);

Obtener los parámetros de monitorización de temperatura y velocidad del ventilador del armario de control de tensión amplia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener los parámetros de monitorización de temperatura y velocidad del ventilador del armario de control de tensión amplia
    * @param [out] enable 0-no habilitar la monitorización; 1-habilitar la monitorización
    * @param [out] period Período de monitorización (s), rango 1-100
    * @return Código de error
    */
    int GetWideBoxTempFanMonitorParam(ref int enable, ref int period);

Ejemplo de código
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    private void button46_Click(object sender, EventArgs e)
    {
        var pkg = new ROBOT_STATE_PKG(); 
        robot.SetWideBoxTempFanMonitorParam(1, 2);    
        int enable = 0;
        int period = 0;
        robot.GetWideBoxTempFanMonitorParam(ref enable, ref period);
        Console.WriteLine($"GetWideBoxTempFanMonitorParam enable is {enable}   period is {period}");  
        for (int i = 0; i < 100; i++)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($"robot ctrl box temp is {pkg.wideVoltageCtrlBoxTemp}, fan current is {pkg.wideVoltageCtrlBoxFanVel}");
            Thread.Sleep(100);
        }       
        int rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);
        Console.WriteLine($"SetWideBoxTempFanMonitorParam rtn is {rtn}");       
        enable = 0;
        period = 0;
        robot.GetWideBoxTempFanMonitorParam(ref enable, ref period);
        Console.WriteLine($"GetWideBoxTempFanMonitorParam enable is {enable}   period is {period}");  
        for (int i = 0; i < 100; i++)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($" robot ctrl box temp is {pkg.wideVoltageCtrlBoxTemp}, fan current is {pkg.wideVoltageCtrlBoxFanVel}");
            Thread.Sleep(100);
        }
    }

Establecer el punto de calibración de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el punto de calibración de foco
    * @param [in] pointNum Número del punto de calibración de foco 1-8
    * @param [in] point Coordenadas del punto de calibración
    * @return Código de error
    */
    int SetFocusCalibPoint(int pointNum, DescPose point);

Establecer las coordenadas de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer las coordenadas de foco
    * @param [in] pos Coordenadas XYZ del foco
    * @return Código de error
    */
    int SetFocusPosition(DescTran pos);

Activar el seguimiento de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Activar el seguimiento de foco
    * @param [in] kp Parámetro proporcional, por defecto 50.0
    * @param [in] kpredict Parámetro de prealimentación, por defecto 19.0
    * @param [in] aMax Límite de aceleración angular máxima, por defecto 1440°/s^2
    * @param [in] vMax Límite de velocidad angular máxima, por defecto 180°/s
    * @param [in] type Bloqueo de la dirección del eje X (0-vector de referencia de entrada; 1-horizontal; 2-vertical)
    * @return Código de error
    */
    int FocusStart(double kp, double kpredict, double aMax, double vMax, int type);

Detener el seguimiento de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Detener el seguimiento de foco
    * @return Código de error
    */
    int FocusEnd();

Ejemplo de código de seguimiento de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    private void button81_Click(object sender, EventArgs e)
    {
        DescPose p1Desc=new DescPose(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
        JointPos p1Joint = new JointPos(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);
        DescPose p2Desc = new DescPose(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
        JointPos p2Joint = new JointPos(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);
        DescPose p3Desc = new DescPose(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
        JointPos p3Joint = new JointPos(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);
        DescPose p4Desc = new DescPose(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
        JointPos p4Joint = new JointPos(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);
        DescPose p5Desc = new DescPose(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
        JointPos p5Joint = new JointPos(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);
        DescPose p6Desc = new DescPose(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
        JointPos p6Joint = new JointPos(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);
        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 100, 0, 0, 0);
        robot.GetForwardKin(p1Joint,ref p1Desc);
        robot.GetForwardKin(p2Joint, ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);
        robot.GetForwardKin(p4Joint, ref p4Desc);
        robot.GetForwardKin(p5Joint, ref p5Desc);
        robot.GetForwardKin(p6Joint, ref p6Desc);
        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);
        DescPose coordRtn = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.ComputeTcp4(ref coordRtn);
        Console.WriteLine($"4 Point ComputeTool      {rtn} coord is {coordRtn.tran.x} ,{coordRtn.tran.y} ,{coordRtn.tran.z} ,{coordRtn.rpy.rx} ,{coordRtn.rpy.ry} ,{coordRtn.rpy.rz} ");
        robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0);
        robot.GetForwardKin(p1Joint, ref p1Desc);
        robot.GetForwardKin(p2Joint, ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);
        robot.SetFocusCalibPoint(1, p1Desc);
        robot.SetFocusCalibPoint(2, p2Desc);
        robot.SetFocusCalibPoint(3, p3Desc);
        DescTran resultPos = new DescTran(0.0, 0.0, 0.0);
        double accuracy = 0.0;
        rtn = robot.ComputeFocusCalib(3, ref resultPos, ref accuracy);
        Console.WriteLine($"ComputeFocusCalib coord is  {rtn},{ resultPos.x} ,{ resultPos.y}, { resultPos.z}, accuracy is {accuracy} ");
        rtn = robot.SetFocusPosition(resultPos);
        robot.GetForwardKin(p5Joint, ref p5Desc);
        robot.GetForwardKin(p6Joint, ref p6Desc);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.FocusStart(50, 19, 710, 90, 0);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.FocusEnd();
    }

Activación de la función de calibración de sensibilidad del sensor de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Activación de la función de calibración de sensibilidad del sensor de par de las articulaciones
    * @param [in] status 0-desactivar; 1-activar
    * @return  Código de error
    */
    public int JointSensitivityEnable(int status);

Adquisición de datos de sensibilidad del sensor de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Adquisición de datos de sensibilidad del sensor de par de las articulaciones
    * @return Código de error
    */
    public int JointSensitivityCollect();

Obtener el resultado de la calibración de sensibilidad del sensor de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el resultado de la calibración de sensibilidad del sensor de par de las articulaciones
    * @param [out] calibResult Sensibilidad de las articulaciones j1~j6 [0-1]
    * @param [out] linearityn Linealidad de las articulaciones j1~j6 [0-1]
    * @return Código de error
    */
    public int JointSensitivityCalibration(double calibResult[6], double linearity[6]);

Obtener el error de histéresis del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el error de histéresis del sensor de par de las articulaciones
    * @param [out] hysteresisError Error de histéresis de las articulaciones j1~j6
    * @return Código de error
    */
    public int JointHysteresisError(ref double[] hysteresisError);
    
Obtener la repetibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:
    
    /**
    * @brief Obtener la repetibilidad del sensor de par de las articulaciones
    * @param [out] repeatability Repetibilidad del sensor de par de las articulaciones j1~j6
    * @return Código de error
    */
    public int JointRepeatability(ref double[] repeatability);
    
Establecer los parámetros del sensor de fuerza de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer los parámetros del sensor de fuerza de las articulaciones
    * @param [in] M Coeficiente de masa J1-J6 [0.001 ~ 10]
    * @param [in] B Coeficiente de amortiguación J1-J6 [0.001 ~ 10]
    * @param [in] K Coeficiente de rigidez J1-J6 [0.001 ~ 10]
    * @param [in] threshold Umbral de control de fuerza, Nm
    * @param [in] sensitivity Sensibilidad, Nm/V, [0 ~ 10]
    * @param [in] setZeroFlag Indicador de activación de la función; 0-desactivar; 1-activar; 2-posición 1 registrar cero; 3-posición 2 registrar cero
    * @return Código de error
    */
    public int SetAdmittanceParams(double[] M, double[] B, double[] K, double[] threshold, double[] sensitivity, int setZeroFlag);

Ejemplo de código de calibración automática de sensibilidad del sensor de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    public int TestSensitivityCalib()
    {
        int rtn; 
        rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        Console.WriteLine($"JointSensitivityEnable rtn is {rtn}");

        JointPos curJPos = new JointPos(0, 0, 0, 0, 0, 0);
        robot.GetActualJointPosDegree(0, ref curJPos);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        JointPos[] jointPoses = new JointPos[]
        {
            new JointPos(curJPos.jPos[0], 0, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -30, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -60, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -90, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -120, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -150, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -180, 0, -90, 0.02, curJPos.jPos[5])
        };
        for (int i = 0; i < jointPoses.Length; i++)
        {
            DescPose descPos = new DescPose(0, 0, 0, 0, 0, 0);
            robot.GetForwardKin(jointPoses[i], ref descPos);
            robot.MoveJ(jointPoses[i], descPos, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            Thread.Sleep(i == 0 ? 200 : 100);
            rtn = robot.JointSensitivityCollect();
            Console.WriteLine($"JointSensitivityCollect {i + 1} rtn is {rtn}");
            Thread.Sleep(100);
        }

        for (int i = jointPoses.Length - 2; i >= 0; i--)
        {
            DescPose descPos = new DescPose();
            robot.GetForwardKin(jointPoses[i], ref descPos);
            robot.MoveJ(jointPoses[i], descPos, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
            Thread.Sleep(100);
            rtn = robot.JointSensitivityCollect();
            Console.WriteLine($"JointSensitivityCollect {jointPoses.Length + (jointPoses.Length - 1 - i)} rtn is {rtn}");
            Thread.Sleep(100);
        }
        double[] calibResult = new double[6];
        double[] linearity = new double[6];
        rtn = robot.JointSensitivityCalibration(ref calibResult, ref linearity);
        Console.WriteLine($"JointSensitivityCalibration rtn is {rtn}");
        rtn = robot.JointSensitivityEnable(0);
        Console.WriteLine($"JointSensitivityEnable rtn is {rtn}");
        Console.WriteLine($"jointSensor Calib result is {calibResult[0]:F6} {calibResult[1]:F6} {calibResult[2]:F6} {calibResult[3]:F6} {calibResult[4]:F6} {calibResult[5]:F6}");
        Console.WriteLine($"jointSensor linearity is {linearity[0]:F6} {linearity[1]:F6} {linearity[2]:F6} {linearity[3]:F6} {linearity[4]:F6} {linearity[5]:F6}"); 
        double[] hysteresisError = new double[6];
        rtn = robot.JointHysteresisError(ref hysteresisError);
        Console.WriteLine($"JointHysteresisError result is {hysteresisError[0]:F6} {hysteresisError[1]:F6} {hysteresisError[2]:F6} {hysteresisError[3]:F6} {hysteresisError[4]:F6} {hysteresisError[5]:F6}");   
        double[] repeatability = new double[6];
        rtn = robot.JointRepeatability(ref repeatability);
        Console.WriteLine($"JointRepeatability result is {repeatability[0]:F6} {repeatability[1]:F6} {repeatability[2]:F6} {repeatability[3]:F6} {repeatability[4]:F6} {repeatability[5]:F6}");
        double[] M = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double[] B = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double[] K = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double[] threshold = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        Console.WriteLine($"SetAdmittanceParams rtn is {rtn}");
        robot.CloseRPC();
        return 0;
    }

Obtener el número de tramas de error de los 8 puertos esclavos del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el número de tramas de error de los 8 puertos esclavos del robot
    * @param [out] inRecvErr Número de tramas de error de recepción de entrada 
    * @param [out] inCRCErr Número de tramas de error CRC de entrada 
    * @param [out] inTransmitErr Número de tramas de error de reenvío de entrada 
    * @param [out] inLinkErr Número de tramas de error de enlace de entrada 
    * @param [out] outRecvErr Número de tramas de error de recepción de salida
    * @param [out] outCRCErr Número de tramas de error CRC de salida
    * @param [out] outTransmitErr Número de tramas de error de reenvío de salida
    * @param [out] outLinkErr Número de tramas de error de enlace de salida
    * @return Código de error
    */
    public int GetSlavePortErrCounter(ref int[] inRecvErr,ref int[] inCRCErr,ref int[] inTransmitErr,ref int[] inLinkErr,ref int[] outRecvErr,ref int[] outCRCErr,ref int[] outTransmitErr,ref int[] outLinkErr);

Poner a cero las tramas de error del puerto esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Poner a cero las tramas de error del puerto esclavo
    * @param [in] slaveID Número de esclavo 0~7
    * @return Código de error
    */
    public int SlavePortErrCounterClear(int slaveID);

Ejemplo de código de obtención de tramas de error del puerto esclavo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    public void TestSlavePortErr()
    {
        int[] inRecvErr = new int[8];
        int[] inCRCErr = new int[8];
        int[] inTransmitErr = new int[8];
        int[] inLinkErr = new int[8];
        int[] outRecvErr = new int[8];
        int[] outCRCErr = new int[8];
        int[] outTransmitErr = new int[8];
        int[] outLinkErr = new int[8];

        robot.GetSlavePortErrCounter(ref inRecvErr, ref inCRCErr, ref inTransmitErr, ref inLinkErr,
            ref outRecvErr, ref outCRCErr, ref outTransmitErr, ref outLinkErr);

        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                Console.WriteLine($"inRecvErr {i} is {inRecvErr[i]}");
            }

            if (inCRCErr[i] != 0)
            {
                Console.WriteLine($"inCRCErr {i} is {inCRCErr[i]}");
            }

            if (inTransmitErr[i] != 0)
            {
                Console.WriteLine($"inTransmitErr {i} is {inTransmitErr[i]}");
            }

            if (inLinkErr[i] != 0)
            {
                Console.WriteLine($"inLinkErr {i} is {inLinkErr[i]}");
            }

            if (outRecvErr[i] != 0)
            {
                Console.WriteLine($"outRecvErr {i} is {outRecvErr[i]}");
            }

            if (outCRCErr[i] != 0)
            {
                Console.WriteLine($"outCRCErr {i} is {outCRCErr[i]}");
            }

            if (outTransmitErr[i] != 0)
            {
                Console.WriteLine($"outTransmitErr {i} is {outTransmitErr[i]}");
            }

            if (outLinkErr[i] != 0)
            {
                Console.WriteLine($"outLinkErr {i} is {outLinkErr[i]}");
            }
        }
        Console.WriteLine("others has no err!");

        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }

        robot.CloseRPC();
    }

Establecer el coeficiente de prealimentación de velocidad de cada eje
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el coeficiente de prealimentación de velocidad de cada eje
    * @param [in] radio Coeficiente de prealimentación de velocidad de cada eje
    * @return Código de error
    */
    public int SetVelFeedForwardRatio(double radio[6]);

Obtener el coeficiente de prealimentación de velocidad de cada eje
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el coeficiente de prealimentación de velocidad de cada eje
    * @param [out] radio Coeficiente de prealimentación de velocidad de cada eje
    * @return Código de error
    */
    public int GetVelFeedForwardRatio(ref double radio[6]);

Ejemplo de código de configuración de prealimentación de velocidad del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public void TestVelFeedForwardRatio()
    {

        double[] setRadio = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double[] getRadio = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        robot.GetVelFeedForwardRatio(ref getRadio);
        Console.WriteLine($" {getRadio[0]:F6} {getRadio[1]:F6} {getRadio[2]:F6} {getRadio[3]:F6} {getRadio[4]:F6} {getRadio[5]:F6}");
    }

Calibración TCP con sensor fotoeléctrico - cálculo del RPY de la herramienta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibración TCP con sensor fotoeléctrico - cálculo del RPY de la herramienta
    * @param [in] Btool Posición cartesiana del robot
    * @param [in] Etool Valor del sistema de coordenadas de herramienta actual
    * @param [in] senser Valor del sistema de coordenadas del sensor actual (aún no disponible)
    * @param [in] radius Radio del movimiento circular mm (aún no disponible)
    * @param [in] dz Distancia de movimiento a lo largo de la dirección negativa del eje z del sistema de coordenadas base; cuando dz = 10000, la función devuelve directamente el RPY de la herramienta
    * @param [out] TCPRPY Valor del RPY de la herramienta
    * @return Código de error
    */
    public int TCPComputeRPY(DescPose Btool, DescPose Etool, DescPose sensor, double radius, double dz, out Rpy TCPRPY);

Calibración TCP con sensor fotoeléctrico - cálculo del XYZ de la herramienta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibración TCP con sensor fotoeléctrico - cálculo del XYZ de la herramienta
    * @param [in] select 0-calcular el TCP de la herramienta; 1-calcular el origen del sensor; 2-calcular la orientación del sensor; 3-devolver directamente el TCP de la herramienta; 4-registrar el sistema de coordenadas de pieza y el sistema de coordenadas de herramienta actuales
    * @param [in] originDirection 0-dirección X; 1-dirección Y; 2-dirección Z
    * @param [in] pos1 Posición cartesiana del robot 1
    * @param [in] pos2 Posición cartesiana del robot 2
    * @param [in] pos3 Posición cartesiana del robot 3
    * @param [in] pos4 Posición cartesiana del robot 4
    * @param [out] TCP Valor XYZ de la herramienta
    * @return Código de error
    */
    public int TCPComputeXYZ(int select, double originDirection, DescTran pos1, DescTran pos2,DescTran pos3, DescTran pos4, out DescTran TCP);

Calibración TCP con sensor fotoeléctrico - iniciar el registro de la posición del centro de la brida del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibración TCP con sensor fotoeléctrico - iniciar el registro de la posición del centro de la brida del extremo
    * @return Código de error
    */
    errno_t TCPRecordFlangePosStart();

Calibración TCP con sensor fotoeléctrico - detener el registro de la posición del centro de la brida del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibración TCP con sensor fotoeléctrico - detener el registro de la posición del centro de la brida del extremo
    * @return Código de error
    */
    public int TCPRecordFlangePosEnd();

Calibración TCP con sensor fotoeléctrico - obtener la posición del centro de herramienta del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibración TCP con sensor fotoeléctrico - obtener la posición del centro de herramienta del extremo
    * @param [out] TCP Posición del centro de herramienta (x,y,z)
    * @return Código de error
    */
    public int TCPGetRecordFlangePos(out DescTran TCP);

Calibración TCP con sensor fotoeléctrico
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibración TCP con sensor fotoeléctrico
    * @param [in] luaPath Ruta del programa lua de calibración automática: "FR_CalibrateTheToolTcp.lua"
    * @param [in] offsetX Desplazamiento del punto de enseñanza (x,y,z) mm
    * @param [out] TCP Sistema de coordenadas de herramienta tras la calibración (x,y,z,rx,ry,rz)
    * @return Código de error
    */
    public int PhotoelectricSensorTCPCalibration(string luaPath, DescTran offset, out DescPose TCP);

Ejemplo de código de calibración TCP con sensor fotoeléctrico
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    public void TestPhotoelectricSensorTCPCalib()
    {
        ROBOT_STATE_PKG pkg =new ROBOT_STATE_PKG();
        DescTran offset = new DescTran( 10.0, 10.0, 3.0 );
        DescPose TCP = new DescPose();
        int rtn = robot.PhotoelectricSensorTCPCalibration("FR_CalibrateTheToolTcp.lua", offset, out TCP);
        Console.WriteLine($"PhotoelectricSensorTCPCalibration : {rtn}");
        Console.WriteLine($"工具TCP坐标: X={TCP.tran.x:F3}, Y={TCP.tran.y:F3}, Z={TCP.tran.z:F3}");
        Console.WriteLine($"工具RPY姿态: RX={TCP.rpy.rx:F3}, RY={TCP.rpy.ry:F3}, RZ={TCP.rpy.rz:F3}");
    }

Establecer la velocidad de forma instantánea
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la velocidad (trama de instrucción, baja latencia)
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @return Código de error
    */
    public int SetWeaveOffsetRT(DescPose offset)

Establecer la velocidad física de forma instantánea
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la velocidad física de forma instantánea
    * @param [in] speed Valor de velocidad física, mm/s
    * @return  Código de error
    */
    public int SetPhySpeedInstant(double speed)

Ejemplo de código de configuración instantánea de la velocidad física
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    void SetPhySpeedInstantInput(double speed)
    {
        int rtn = robot.SetPhySpeedInstant(speed);
        Console.WriteLine($"SetPhySpeedInstant({speed}) : {rtn}");
    }