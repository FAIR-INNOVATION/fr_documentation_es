Configuraciones habituales del robot
===============================================

.. toctree:: 
    :maxdepth: 5

Establecer el punto de referencia de la herramienta - método de seis puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el punto de referencia de la herramienta - método de seis puntos
    * @param [in] point_num Número de punto, rango [1~6]
    * @return Código de error 
    */ 
    int SetToolPoint(int point_num);

Calcular el sistema de coordenadas de herramienta - método de seis puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcular el sistema de coordenadas de herramienta
    * @param [out] tcp_pose Sistema de coordenadas de herramienta
    * @return Código de error 
    */ 
    int ComputeTool(DescPose tcp_pose);

Establecer el punto de referencia de la herramienta - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el punto de referencia de la herramienta - método de cuatro puntos
    * @param [in] point_num Número de punto, rango [1~4]
    * @return Código de error 
    */ 
    int SetTcp4RefPoint(int point_num);

Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcular el sistema de coordenadas de herramienta
    * @param [out] tcp_pose Sistema de coordenadas de herramienta
    * @return Código de error 
    */ 
    int ComputeTcp4(DescPose tcp_pose);

Calcular el sistema de coordenadas de herramienta a partir de la información de los puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcular el sistema de coordenadas de herramienta a partir de la información de los puntos
    * @param [in] method Método de cálculo; 0-método de cuatro puntos; 1-método de seis puntos
    * @param [in] pos Grupo de posiciones de articulaciones; en el método de cuatro puntos la longitud del arreglo es 4, en el método de seis puntos la longitud del arreglo es 6
    * @param [out] tool_pose Sistema de coordenadas de herramienta de salida
    * @return Código de error 
    */ 
    int ComputeToolCoordWithPoints(int method, JointPos[] pos,DescPose tool_pose);

Establecer el sistema de coordenadas de herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el sistema de coordenadas de herramienta 
    * @param [in] id Número del sistema de coordenadas, rango [0~14]
    * @param [in] coord  Pose del centro de la herramienta respecto al centro de la brida del extremo
    * @param [in] type  0-sistema de coordenadas de herramienta, 1-sistema de coordenadas de sensor
    * @param [in] install Posición de instalación, 0-extremo del robot, 1-exterior del robot
    * @param [in] toolID  ID de la herramienta
    * @param [in] loadNum  Número de carga
    * @return Código de error 
    */ 
    int SetToolCoord(int id, DescPose coord, int type, int install, int toolID, int loadNum);  

Establecer la lista de sistemas de coordenadas de herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer la lista de sistemas de coordenadas de herramienta
    * @param  [in] id Número del sistema de coordenadas, rango [0~14]
    * @param  [in] coord  Pose del centro de la herramienta respecto al centro de la brida del extremo
    * @param  [in] type  0-sistema de coordenadas de herramienta, 1-sistema de coordenadas de sensor
    * @param  [in] install Posición de instalación, 0-extremo del robot, 1-exterior del robot
    * @param  [in] loadNum Número de carga
    * @return  Código de error
    */
    int SetToolList(int id, DescPose coord, int type, int install, int loadNum);  

Obtener el sistema de coordenadas de herramienta actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el sistema de coordenadas de herramienta actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] desc_pos Pose del sistema de coordenadas de herramienta
    * @return  Código de error
    */
    int GetTCPOffset(int flag, DescPose desc_pos); 

Ejemplo de código de operación del sistema de coordenadas de herramienta del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestTCPCompute(Robot robot)
    {
        DescPose p1Desc=new DescPose(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
        JointPos p1Joint=new JointPos(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);

        DescPose p2Desc=new DescPose(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
        JointPos p2Joint=new JointPos(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);

        DescPose p3Desc=new DescPose(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
        JointPos p3Joint=new JointPos(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);

        DescPose p4Desc=new DescPose(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
        JointPos p4Joint=new JointPos(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);

        DescPose p5Desc=new DescPose(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
        JointPos p5Joint=new JointPos(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);

        DescPose p6Desc=new DescPose(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
        JointPos p6Joint=new JointPos(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        JointPos[] posJ = { p1Joint , p2Joint , p3Joint , p4Joint , p5Joint , p6Joint };
        DescPose coordRtn =new DescPose() {};
        int rtn = robot.ComputeToolCoordWithPoints(1, posJ, coordRtn);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(4);
        robot.MoveJ(p5Joint, p5Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(5);
        robot.MoveJ(p6Joint, p6Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(6);
        rtn = robot.ComputeTool(coordRtn);
        robot.SetToolList(3, coordRtn, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);
        rtn = robot.ComputeTcp4(coordRtn);

        robot.SetToolCoord(4, coordRtn, 0, 0, 1, 0);

        DescPose getCoord = new DescPose(){};
        rtn = robot.GetTCPOffset(0, getCoord);
        return 0;
    }

Establecer el punto de referencia de la herramienta externa - método de seis puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el punto de referencia de la herramienta externa - método de tres puntos 
    * @param [in] point_num Número de punto, rango [1~3]
    * @return Código de error 
    */ 
    int SetExTCPPoint(int point_num); 

Calcular el sistema de coordenadas de herramienta externa - método de seis puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:
    
    /** 
    * @brief Calcular el sistema de coordenadas de herramienta externa - método de tres puntos
    * @param [out] tcp_pose Sistema de coordenadas de herramienta externa
    * @return Código de error 
    */ 
    int ComputeExTCF(DescPose tcp_pose); 

Establecer el sistema de coordenadas de herramienta externa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el sistema de coordenadas de herramienta externa 
    * @param [in] id Número del sistema de coordenadas, 20-39 corresponden a los sistemas de coordenadas de herramienta externa 0-19
    * @param [in] etcp  Pose del centro de la herramienta respecto al centro de la brida del extremo
    * @param [in] etool  Pendiente
    * @return Código de error 
    */
    int SetExToolCoord(int id, DescPose etcp, DescPose etool); 

Establecer la lista de sistemas de coordenadas de herramienta externa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer la lista de sistemas de coordenadas de herramienta externa
    * @param  [in] id Número del sistema de coordenadas, 20-39 corresponden a los sistemas de coordenadas de herramienta externa 0-19
    * @param  [in] etcp  Pose del centro de la herramienta respecto al centro de la brida del extremo
    * @param  [in] etool  Pendiente
    * @return  Código de error
    */
    int SetExToolList(int id, DescPose etcp, DescPose etool); 

Ejemplo de código de operación del sistema de coordenadas de herramienta externa del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestExtCoord(Robot robot)
    {
        DescPose p1Desc=new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint=new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc=new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint=new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc=new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint=new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,p1Desc);
        robot.GetForwardKin(p2Joint,p2Desc);
        robot.GetForwardKin(p3Joint,p3Desc);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = { p1Desc , p2Desc , p3Desc };
        DescPose coordRtn = new DescPose();

        robot.MoveJ(p1Joint, p1Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(3);
        int rtn = robot.ComputeExTCF(coordRtn);

        robot.SetExToolCoord(1, coordRtn, offdese);
        robot.SetExToolList(1, coordRtn, offdese);
        return 0;
    }
    
Establecer el punto de referencia del sistema de coordenadas de la pieza - método de tres puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el punto de referencia de la pieza - método de tres puntos 
    * @param [in] point_num Número de punto, rango [1~3]
    * @return Código de error 
    */ 
    int SetWObjCoordPoint(int point_num);


Calcular el sistema de coordenadas de la pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcular el sistema de coordenadas de la pieza
    * @param [in]  method Método de cálculo 0: origen-eje x-eje z  1: origen-eje x-plano xy
    * @param [in]  refFrame Sistema de coordenadas de referencia
    * @param [out]  wobj_pose Sistema de coordenadas de la pieza
    * @return Código de error 
    */ 
    int ComputeWObjCoord(int method, int refFrame, DescPose wobj_pose); 

Establecer el sistema de coordenadas de la pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el sistema de coordenadas de la pieza
    * @param  [in] id Número del sistema de coordenadas, rango [1~15]
    * @param  [in] coord  Pose del sistema de coordenadas de la pieza respecto al centro de la brida del extremo
    * @param  [in] refFrame Sistema de coordenadas de referencia
    * @return  Código de error
    */    
    int SetWObjCoord(int id, DescPose coord, int refFrame);

Establecer la lista de sistemas de coordenadas de la pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer la lista de sistemas de coordenadas de la pieza
    * @param  [in] id Número del sistema de coordenadas, rango [1~15]
    * @param  [in] coord  Pose del sistema de coordenadas de la pieza respecto al centro de la brida del extremo
    * @param  [in] refFrame Sistema de coordenadas de referencia
    * @return  Código de error
    */    
    int SetWObjList(int id, DescPose coord, int refFrame);

Calcular el sistema de coordenadas de la pieza a partir de la información de los puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcular el sistema de coordenadas de la pieza a partir de la información de los puntos
    * @param [in] method Método de cálculo; 0: origen-eje x-eje z  1: origen-eje x-plano xy
    * @param [in] pos Tres grupos de posiciones del TCP
    * @param [in] refFrame Sistema de coordenadas de referencia
    * @param [in] tcp_pose Sistema de coordenadas de la pieza de salida
    * @return Código de error 
    */ 
    int ComputeWObjCoordWithPoints(int method, DescPose[] pos, int refFrame,DescPose tcp_pose);

Obtener el sistema de coordenadas de la pieza actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el sistema de coordenadas de la pieza actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] desc_pos Pose del sistema de coordenadas de la pieza
    * @return  Código de error
    */   
    int GetWObjOffset(int flag, DescPose desc_pos);

Ejemplo de código de operación del sistema de coordenadas de la pieza del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestWobjCoord(Robot robot)
    {
        DescPose p1Desc=new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint=new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc=new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint=new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc=new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint=new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,p1Desc);
        robot.GetForwardKin(p2Joint,p2Desc);
        robot.GetForwardKin(p3Joint,p3Desc);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP =new DescPose[]{p1Desc , p2Desc , p3Desc };
        DescPose coordRtn =new DescPose();
        int rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, coordRtn);

        robot.MoveJ(p1Joint, p1Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(3);
        rtn = robot.ComputeWObjCoord(1, 0, coordRtn);

        robot.SetWObjCoord(1, coordRtn, 0);
        robot.SetWObjList(1, coordRtn, 0);

        DescPose getWobjDesc = new DescPose();
        rtn = robot.GetWObjOffset(0, getWobjDesc);
        return 0;
    }
    
Establecer la velocidad global
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer la velocidad global
    * @param  [in]  vel  Porcentaje de velocidad, rango [0~100]
    * @return  Código de error
    */
    int SetSpeed(int vel); 

Establecer la aceleración del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la aceleración del robot
    * @param [in] acc Porcentaje de aceleración del robot
    * @return Código de error
    */
    int SetOaccScale(double acc);

Obtener la velocidad predeterminada del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la velocidad predeterminada del robot
    * @return  List[0]:int código de error; List[1]: double vel velocidad, unidad mm/s
    */   
    List<Number> GetDefaultTransVel(); 

Establecer el peso de la carga del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el peso de la carga del extremo
    * @param  [in] loadNum Número de carga
    * @param  [in] weight  Peso de la carga, unidad kg
    * @return  Código de error
    */
    int SetLoadWeight(int loadNum,double weight);

Establecer las coordenadas del centro de masa de la carga del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer las coordenadas del centro de masa de la carga del extremo
    * @param  [in] coord Coordenadas del centro de masa, unidad mm
    * @return  Código de error
    */
    int SetLoadCoord(DescTran coord); 

Establecer las coordenadas del centro de masa de la carga del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief  Establecer las coordenadas del centro de masa de la carga del extremo
     * @param  [in] loadNum Número de carga
     * @param  [in] coord Coordenadas del centro de masa, unidad mm
     * @return  Código de error
     */
    public int SetLoadCoord(int loadNum, DescTran coord)

Obtener el peso de la carga actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el peso de la carga actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @return  List[0]:int código de error; List[1]: double weight  peso de la carga, unidad kg
    */
    List<Number> GetTargetPayload(int flag); 

Obtener el centro de masa de la carga actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el centro de masa de la carga actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] cog Centro de masa de la carga, unidad mm
    * @return  Código de error
    */   
    int GetTargetPayloadCog(int flag, DescTran cog);

Establecer el modo de instalación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el modo de instalación del robot
    * @param  [in]  install  Modo de instalación, 0-instalación normal, 1-instalación lateral, 2-instalación invertida
    * @return  Código de error
    */
    int SetRobotInstallPos(int install); 

Establecer el ángulo de instalación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el ángulo de instalación del robot, instalación libre
    * @param  [in] yangle  Ángulo de inclinación
    * @param  [in] zangle  Ángulo de rotación
    * @return  Código de error
    */
    int SetRobotInstallAngle(double yangle, double zangle); 

Obtener el ángulo de instalación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el ángulo de instalación del robot
    * @return  List[0]:código de error; List[1]:double yangle ángulo de inclinación; List[2]:double zangle ángulo de rotación
    */
    public List<Number> GetRobotInstallAngle()

Establecer el valor de una variable del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el valor de una variable del sistema
    * @param  [in]  id  Número de variable, rango [1~20]
    * @param  [in]  value Valor de la variable
    * @return  Código de error
    */
    int SetSysVarValue(int id, double value); 

Obtener el valor de una variable del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el valor de una variable del sistema
    * @param  [in] id Número de variable del sistema, rango [1~20]
    * @return  List[0]:código de error; List[1]:double value valor de la variable del sistema
    */
    List<Number> GetSysVarValue(int id); 

Ejemplo de código de configuraciones habituales del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLoadInstall(Robot robot)
    {
        for (int i = 1; i < 100; i++)
        {
            robot.SetSpeed(i);
            robot.SetOaccScale(i);
            robot.Sleep(30);
        }

        List<Number> defaultVel=new ArrayList<>();

        defaultVel=robot.GetDefaultTransVel();
        System.out.println("GetDefaultTransVel is:"+ defaultVel.get(1));

        for (int i = 1; i < 21; i++)
        {
            robot.SetSysVarValue(i, i + 0.5);
            robot.Sleep(100);
        }

        for (int i = 1; i < 21; i++)
        {
            float value = 0;
            defaultVel=robot.GetSysVarValue(i);
            System.out.println("sys value :"+i+", is :"+defaultVel.get(1));
            robot.Sleep(100);
        }

        robot.SetLoadWeight(0, 2.5);

        DescTran loadCoord = new DescTran();
        loadCoord.x = 3.0;
        loadCoord.y = 4.0;
        loadCoord.z = 5.0;
        robot.SetLoadCoord(loadCoord);

        robot.Sleep(1000);

        List<Number> getLoad = new ArrayList<>();

        getLoad=robot.GetTargetPayload(0);

        DescTran getLoadTran =new DescTran();
        robot.GetTargetPayloadCog(0, getLoadTran);
        System.out.println("get load is:"+getLoad.get(1)+", get load cog is: "+getLoadTran.x+","+getLoadTran.y+","+getLoadTran.z);

        robot.SetRobotInstallPos(0);
        robot.SetRobotInstallAngle(15.0, 25.0);

        List<Number> angle=new ArrayList<>();
        angle=robot.GetRobotInstallAngle();
        System.out.println("GetRobotInstallAngle x:"+angle.get(1)+";  y:"+angle.get(2));

        robot.CloseRPC();
        return 0;
    }

Interruptor de compensación de fricción de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Interruptor de compensación de fricción de las articulaciones 
    * @param [in] state  0-desactivado, 1-activado
    * @return Código de error 
    */ 
    int FrictionCompensationOnOff(int state); 

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación normal
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación normal
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    int SetFrictionValue_level(Object[] coeff);

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación lateral
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación lateral
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    int SetFrictionValue_wall(Object[] coeff); 

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación invertida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación invertida
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    int SetFrictionValue_ceiling(Object[] coeff);

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación libre
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación libre
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    int SetFrictionValue_freedom(Object[] coeff);

Ejemplo de código de configuración de la compensación de fricción de las articulaciones del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFriction(Robot robot)
    {

        Object[] lcoeff = { 0.9,0.9,0.9,0.9,0.9,0.9 };
        Object[] wcoeff = { 0.4,0.4,0.4,0.4,0.4,0.4 };
        Object[] ccoeff = { 0.6,0.6,0.6,0.6,0.6,0.6 };
        Object[] fcoeff = { 0.5,0.5,0.5,0.5,0.5,0.5 };

        int rtn = robot.FrictionCompensationOnOff(1);
        System.out.println("FrictionCompensationOnOff rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_level(lcoeff);
        System.out.println("SetFrictionValue_level rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_wall(wcoeff);
        System.out.println("SetFrictionValue_wall rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_ceiling(ccoeff);
        System.out.println("SetFrictionValue_ceiling rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_freedom(fcoeff);
        System.out.println("SetFrictionValue_freedom rtn is:"+ rtn);

        robot.CloseRPC();
        return 0;
    }

Consultar el código de error del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief  Consultar el código de error del robot
     * @param  [out]  maincode  Código de error principal
     * @param  [out]  subcode   Código de error secundario
     * @return  Código de error
     */ 
    int GetRobotErrorCode(int[] maincode, int[] subcode);

Borrar el estado de error
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Borrar el estado de error
    * @return  Código de error
    */
    int ResetAllError(); 

Ejemplo de código de obtención y borrado del estado de fallo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetError(Robot robot)
    {
        int[] maincode={0}, subcode={0};
        robot.GetRobotErrorCode(maincode, subcode);

        robot.ResetAllError();

        robot.Sleep(1000);

        robot.GetRobotErrorCode(maincode, subcode);
        return 0;
    }

Establecer los parámetros de monitorización de temperatura y velocidad del ventilador de la caja de control de voltaje amplio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer los parámetros de monitorización de temperatura y velocidad del ventilador de la caja de control de voltaje amplio
    * @param [in] enable 0-no habilitar la monitorización; 1-habilitar la monitorización
    * @param [in] period Período de monitorización (s), rango 1-100
    * @return Código de error
    */
    int SetWideBoxTempFanMonitorParam(int enable, int period);

Obtener los parámetros de monitorización de temperatura y velocidad del ventilador de la caja de control de voltaje amplio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener los parámetros de monitorización de temperatura y velocidad del ventilador de la caja de control de voltaje amplio
    * @return List[0]-código de error,List[1]-enable 0-no habilitar la monitorización; 1-habilitar la monitorización,List[2]-period período de monitorización (s), rango 1-100
    */
    List<Number> GetWideBoxTempFanMonitorParam()

Ejemplo de código de obtención del estado de temperatura y corriente del ventilador de la caja de control de voltaje amplio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestWideVoltageCtrlBoxtemp(Robot robot)
    {
        robot.SetWideBoxTempFanMonitorParam(1, 2);
        List<Number> list=robot.GetWideBoxTempFanMonitorParam();
        System.out.println("GetWideBoxTempFanMonitorParam enable is:"+list.get(1)+", period is:"+list.get(2));
        ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
        for (int i = 0; i < 100; i++)
        {
            pkg=robot.GetRobotRealTimeState();
            System.out.println("robot ctrl box temp is:"+pkg.wideVoltageCtrlBoxTemp+",fan current is:"+pkg.wideVoltageCtrlBoxFanCurrent);
            robot.Sleep(100);
        }

        int rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);

        list=robot.GetWideBoxTempFanMonitorParam();
        for (int i = 0; i < 100; i++)
        {
            pkg=robot.GetRobotRealTimeState();
            System.out.println("robot ctrl box temp is:"+pkg.wideVoltageCtrlBoxTemp+" ,fan current is:"+pkg.wideVoltageCtrlBoxFanCurrent);
            robot.Sleep(100);
        }

        robot.CloseRPC();
        robot.Sleep(2000);
        return 0;
    }

Establecer el punto de calibración de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el punto de calibración de foco
    * @param [in] pointNum Número del punto de calibración de foco 1-8
    * @param [in] point    Coordenadas del punto de calibración
    * @return Código de error
    */
    int SetFocusCalibPoint(int pointNum, DescPose point)

Calcular el resultado de la calibración de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Calcular el resultado de la calibración de foco
    * @param [in] pointNum  Número de puntos de calibración
    * @param [in] resultPos XYZ del resultado de la calibración
    * @param [out] accuracy   Error de precisión de la calibración
    * @return Código de error
    */
    int ComputeFocusCalib(int pointNum, DescTran resultPos, double[] accuracy)

Activar el seguimiento de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Activar el seguimiento de foco
    * @param [in] kp       Parámetro proporcional, por defecto 50.0
    * @param [in] kpredict Parámetro de prealimentación, por defecto 19.0
    * @param [in] aMax     Límite máximo de aceleración angular, por defecto 1440°/s^2
    * @param [in] vMax     Límite máximo de velocidad angular, por defecto 180°/s
    * @param [in] type     Bloqueo de la dirección del eje X (0-vector de entrada de referencia; 1-horizontal; 2-vertical)
    * @return Código de error
    */
    int FocusStart(double kp, double kpredict, double aMax, double vMax, int type)

Detener el seguimiento de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Detener el seguimiento de foco
    * @return Código de error
    */
    int FocusEnd()

Establecer las coordenadas del foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:
    
    /**
    * @brief Establecer las coordenadas del foco
    * @param pos Coordenadas XYZ del foco
    * @return Código de error
    */
    public int SetFocusPosition(DescTran pos)

Ejemplo de código de seguimiento de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestFocus(Robot robot){
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

        robot.GetForwardKin(p1Joint, p1Desc);
        robot.GetForwardKin(p2Joint,  p2Desc);
        robot.GetForwardKin(p3Joint,  p3Desc);
        robot.GetForwardKin(p4Joint,  p4Desc);
        robot.GetForwardKin(p5Joint,  p5Desc);
        robot.GetForwardKin(p6Joint,  p6Desc);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);

        DescPose coordRtn = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.ComputeTcp4( coordRtn);

        robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0);

        robot.GetForwardKin(p1Joint, p1Desc);
        robot.GetForwardKin(p2Joint, p2Desc);
        robot.GetForwardKin(p3Joint, p3Desc);

        robot.SetFocusCalibPoint(1, p1Desc);
        robot.SetFocusCalibPoint(2, p2Desc);
        robot.SetFocusCalibPoint(3, p3Desc);

        DescTran resultPos = new DescTran(0.0, 0.0, 0.0);
        double[] accuracy = {0.0};
        rtn = robot.ComputeFocusCalib(3,  resultPos,  accuracy);
        rtn = robot.SetFocusPosition(resultPos);

        robot.GetForwardKin(p5Joint,  p5Desc);
        robot.GetForwardKin(p6Joint,  p6Desc);

        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);

        robot.FocusStart(50, 19, 710, 90, 0);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.FocusEnd();
    }

Activar la función de calibración de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Activar la función de calibración de sensibilidad del sensor de par de las articulaciones
    * @param status 0-desactivar; 1-activar
    * @return Código de error
    */
    public int JointSensitivityEnable(int status)

Recogida de datos de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Recogida de datos de sensibilidad del sensor de par de las articulaciones
    * @return Código de error
    */
    public int JointSensitivityCollect()

Obtener el resultado de la calibración de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el resultado de la calibración de sensibilidad del sensor de par de las articulaciones
    * @param calibResult Sensibilidad de las articulaciones j1~j6 [0-1]
    * @param linearityn Linealidad de las articulaciones j1~j6 [0-1]
    * @return Código de error
    */
    public int JointSensitivityCalibration(double calibResult[6], double linearity[6])

Obtener el error de histéresis del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el error de histéresis del sensor de par de las articulaciones
    * @param hysteresisError Error de histéresis de las articulaciones j1~j6
    * @return Código de error
    */
    public int JointHysteresisError(double[] hysteresisError);
    
Obtener la repetibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:
    
    /**
    * @brief Obtener la repetibilidad del sensor de par de las articulaciones
    * @param repeatability Repetibilidad del sensor de par de las articulaciones j1~j6
    * @return Código de error
    */
    public int JointRepeatability(double[] repeatability);
    
Establecer los parámetros del sensor de fuerza de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer los parámetros del sensor de fuerza de las articulaciones
    * @param Parámetro obligatorio M Coeficientes de masa J1-J6[]
    * @param Parámetro obligatorio B Coeficientes de amortiguación J1-J6[]
    * @param Parámetro obligatorio K Coeficientes de rigidez J1-J6[]
    * @param Parámetro predeterminado threshold Umbral de control de fuerza, Nm
    * @param Parámetro predeterminado sensitivity Sensibilidad, Nm/V, []
    * @param Parámetro predeterminado setZeroFlag Indicador de activación de la función; 0-desactivar; 1-activar; 2-posición 1 registrar punto cero; 3-posición 2 registrar punto cero
    * @return Código de error
    */
    public int SetAdmittanceParams(double[] M, double[] B, double[] K, double[] threshold, double[] sensitivity, int setZeroFlag);

Ejemplo de código de calibración automática de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestSensitivityCalib(Robot robot)
    {
        int rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        System.out.printf("JointSensitivityEnable rtn is %d\n", rtn);
        JointPos curJPos = new JointPos();
        robot.GetActualJointPosDegree(curJPos);
        ExaxisPos epos = new ExaxisPos(0,0,0,0);
        DescPose offset_pos =new DescPose(0,0,0,0,0,0 );
        JointPos jointPos1 = new JointPos(curJPos.J1, 0, 0, -90, 0.02, curJPos.J6);
        DescPose descPos1 = new DescPose();
        robot.GetForwardKin(jointPos1, descPos1);
        robot.MoveJ(jointPos1, descPos1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 1 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos2 =new JointPos( curJPos.J1, -30, 0, -90, 0.02, curJPos.J6 );
        DescPose descPos2 =new DescPose();
        robot.GetForwardKin(jointPos2, descPos2);
        robot.MoveJ(jointPos2, descPos2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 2 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos3 = new JointPos( curJPos.J1, -60, 0, -90, 0.02, curJPos.J6 );
        DescPose descPos3 =new DescPose();
        robot.GetForwardKin(jointPos3, descPos3);
        robot.MoveJ(jointPos3, descPos3, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 3 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos4 = new JointPos(curJPos.J1, -90, 0, -90, 0.02, curJPos.J6);
        DescPose descPos4 = new DescPose();
        robot.GetForwardKin(jointPos4, descPos4);
        robot.MoveJ(jointPos4, descPos4, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 4 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos5 = new JointPos(curJPos.J1, -120, 0, -90, 0.02, curJPos.J6);
        DescPose descPos5 = new DescPose();
        robot.GetForwardKin(jointPos5, descPos5);
        robot.MoveJ(jointPos5, descPos5, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 5 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos6 = new JointPos(curJPos.J1, -150, 0, -90, 0.02, curJPos.J6);
        DescPose descPos6 = new DescPose();
        robot.GetForwardKin(jointPos6, descPos6);
        robot.MoveJ(jointPos6, descPos6, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 6 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos7 = new JointPos(curJPos.J1, -180, 0, -90, 0.02, curJPos.J6);
        DescPose descPos7 = new DescPose();
        robot.GetForwardKin(jointPos7, descPos7);
        robot.MoveJ(jointPos7, descPos7, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 7 rtn is %d\n", rtn);
        robot.Sleep(100);
        //Recorrido inverso
        robot.MoveJ(jointPos6, descPos6, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 8 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos5, descPos5, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 9 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos4, descPos4, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 10 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos3, descPos3, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 11 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos2, descPos2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 12 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos1, descPos1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 13 rtn is %d\n", rtn);
        robot.Sleep(100);
        double[] calibResult =new double[6];
        double[] linearity = new double[6];
        rtn = robot.JointSensitivityCalibration(calibResult, linearity);
        System.out.printf("JointSensitivityCalibration rtn is %d\n", rtn);
        rtn = robot.JointSensitivityEnable(0);
        System.out.printf("JointSensitivityEnable rtn is %d\n", rtn);
        System.out.printf("jointSensor Calib result is %f %f %f %f %f %f\njointSensor linearity is %f %f %f %f %f %f\n",
                calibResult[0], calibResult[1], calibResult[2],
                calibResult[3], calibResult[4], calibResult[5],
                linearity[0], linearity[1], linearity[2],
                linearity[3], linearity[4], linearity[5]);
        double[] hysteresisError = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        rtn = robot.JointHysteresisError(hysteresisError);
        System.out.printf("JointHysteresisError result is %f %f %f %f %f %f\n",
                hysteresisError[0], hysteresisError[1], hysteresisError[2],
                hysteresisError[3], hysteresisError[4], hysteresisError[5]);
        double[] repeatability = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        rtn = robot.JointRepeatability(repeatability);
        System.out.printf("JointRepeatability result is %f %f %f %f %f %f\n",
                repeatability[0], repeatability[1], repeatability[2],
                repeatability[3], repeatability[4], repeatability[5]);
        double[] M = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        double[] B = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        double[] K = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        double[] threshold = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        System.out.printf("SetAdmittanceParams rtn is %d\n", rtn);
    }

Obtener el número de tramas de error de los 8 puertos esclavos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el número de tramas de error de los 8 puertos esclavos del robot
    * @param  inRecvErr Número de tramas de error de recepción de entrada
    * @param  inCRCErr Número de tramas de error CRC de entrada
    * @param  inTransmitErr Número de tramas de error de reenvío de entrada
    * @param  inLinkErr Número de tramas de error de enlace de entrada
    * @param  outRecvErr Número de tramas de error de recepción de salida
    * @param  outCRCErr Número de tramas de error CRC de salida
    * @param  outTransmitErr Número de tramas de error de reenvío de salida
    * @param  outLinkErr Número de tramas de error de enlace de salida
    * @return Código de error
    */
    public int GetSlavePortErrCounter(int[] inRecvErr, int[] inCRCErr, int[] inTransmitErr, int[] inLinkErr, int[] outRecvErr, int[] outCRCErr, int[] outTransmitErr, int[] outLinkErr)

Puesta a cero de las tramas de error del puerto esclavo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Puesta a cero de las tramas de error del puerto esclavo
    * @param slaveID Número de esclavo 0~7
    * @return Código de error
    */
    public int SlavePortErrCounterClear(int slaveID)

Ejemplo de código de obtención de tramas de error del puerto esclavo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestSlavePortErr(Robot robot)
    {
        ROBOT_STATE_PKG pkg =new ROBOT_STATE_PKG();
        int[] inRecvErr =new int[8];
        int[] inCRCErr =new int[8];
        int[] inTransmitErr =new int[8];
        int[] inLinkErr =new int[8];
        int[] outRecvErr =new int[8];
        int[] outCRCErr =new int[8];
        int[] outTransmitErr =new int[8];
        int[] outLinkErr =new int[8];
        robot.GetSlavePortErrCounter(inRecvErr,  inCRCErr, inTransmitErr, inLinkErr,
                outRecvErr, outCRCErr, outTransmitErr, outLinkErr);
        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inRecvErr[i]);
            }
            if (inCRCErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inCRCErr[i]);
            }
            if (inTransmitErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inTransmitErr[i]);
            }
            if (inLinkErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inLinkErr[i]);
            }
            if (outRecvErr[i] != 0)
            {
                System.out.printf("outRecvErr %d is %d\n", i, outRecvErr[i]);
            }
            if (outCRCErr[i] != 0)
            {
                System.out.printf("outCRCErr %d is %d\n", i, outCRCErr[i]);
            }
            if (outTransmitErr[i] != 0)
            {
                System.out.printf("outTransmitErr %d is %d\n", i, outTransmitErr[i]);
            }
            if (outLinkErr[i] != 0)
            {
                System.out.printf("outLinkErr %d is %d\n", i, outLinkErr[i]);
            }
        }
        System.out.printf("others has no err!\n");
        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }
        robot.CloseRPC();
    }

Establecer el coeficiente de prealimentación de velocidad de cada eje
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el coeficiente de prealimentación de velocidad de cada eje
    * @param  radio Coeficiente de prealimentación de velocidad de cada eje
    * @return Código de error
    */
    public int SetVelFeedForwardRatio(double[] radio)

Obtener el coeficiente de prealimentación de velocidad de cada eje
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el coeficiente de prealimentación de velocidad de cada eje
    * @param  radio Coeficiente de prealimentación de velocidad de cada eje
    * @return Código de error
    */
    public int GetVelFeedForwardRatio(double[] radio)

Ejemplo de código del coeficiente de prealimentación de velocidad del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestVelFeedForwardRatio(Robot robot)
    {
        double[] setRadio =new double[] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double[] getRadio = new double[]{ 0.0 };
        robot.GetVelFeedForwardRatio(getRadio);
        System.out.printf(" %f %f %f %f %f %f\n", getRadio[0], getRadio[1], getRadio[2], getRadio[3], getRadio[4], getRadio[5]);
        robot.CloseRPC();
    }

Calibración TCP del sensor fotoeléctrico - calcular RPY de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibración TCP del sensor fotoeléctrico - calcular RPY de la herramienta
    * @param  Btool Posición cartesiana del robot
    * @param  Etool Valor actual del sistema de coordenadas de herramienta
    * @param  sensor Valor actual del sistema de coordenadas del sensor (aún no disponible)
    * @param  radius Radio del movimiento circular mm (aún no disponible)
    * @param  dz Distancia de movimiento a lo largo de la dirección negativa del eje z del sistema de coordenadas base; cuando dz = 10000, la función devuelve directamente el RPY de la herramienta
    * @param  TCPRPY Valor del RPY de la herramienta
    * @return Código de error
    */
    public int TCPComputeRPY(DescPose Btool, DescPose Etool, DescPose sensor, double radius, double dz, Rpy TCPRPY)

Calibración TCP del sensor fotoeléctrico - calcular XYZ de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibración TCP del sensor fotoeléctrico - calcular XYZ de la herramienta
    * @param  select 0-calcular TCP de la herramienta; 1-calcular el origen del sensor; 2-calcular la orientación del sensor; 3-devolver directamente el TCP de la herramienta; 4-registrar el sistema de coordenadas de la pieza y el sistema de coordenadas de herramienta actuales
    * @param  originDirection 0-dirección X; 1-dirección Y; 2-dirección Z
    * @param  pos1 Posición cartesiana 1 del robot
    * @param  pos2 Posición cartesiana 2 del robot
    * @param  pos3 Posición cartesiana 3 del robot
    * @param  pos4 Posición cartesiana 4 del robot
    * @param  TCP Valor XYZ de la herramienta
    * @return Código de error
    */
    public int TCPComputeXYZ(int select, double originDirection, DescTran pos1, DescTran pos2, DescTran pos3, DescTran pos4, DescTran TCP)

Calibración TCP del sensor fotoeléctrico - iniciar el registro de la posición del centro de la brida del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibración TCP del sensor fotoeléctrico - iniciar el registro de la posición del centro de la brida del extremo
    * @return Código de error
    */
    public int TCPRecordFlangePosStart()

Calibración TCP del sensor fotoeléctrico - detener el registro de la posición del centro de la brida del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibración TCP del sensor fotoeléctrico - detener el registro de la posición del centro de la brida del extremo
    * @return Código de error
    */
    public int TCPRecordFlangePosEnd()

Calibración TCP del sensor fotoeléctrico - obtener la posición del centro de la herramienta del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibración TCP del sensor fotoeléctrico - obtener la posición del centro de la herramienta del extremo
    * @param  TCP Posición del centro de la herramienta (x,y,z)
    * @return Código de error
    */
    public int TCPGetRecordFlangePos(DescTran TCP)

Calibración TCP del sensor fotoeléctrico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibración TCP del sensor fotoeléctrico
    * @param luaPath Ruta del programa lua de calibración automática: "FR_CalibrateTheToolTcp.lua"
    * @param offset Desplazamiento del punto de enseñanza (x,y,z) mm
    * @param TCP Sistema de coordenadas de herramienta tras la calibración (x,y,z,rx,ry,rz)
    * @return Código de error
    */
    public int PhotoelectricSensorTCPCalibration(String luaPath, DescTran offset, DescPose TCP)

Ejemplo de código de calibración TCP del sensor fotoeléctrico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestPhotoelectricSensorTCPCalib(Robot robot)
    {
        DescTran offset = new DescTran(10.0, 10.0, 3.0 );
        DescPose TCP = new DescPose();
        int rtn = robot.PhotoelectricSensorTCPCalibration("FR_CalibrateTheToolTcp.lua", offset, TCP);
        System.out.printf("PhotoelectricSensorTCPCalibration rtn is %d %f %f %f %f %f %f \n", rtn, TCP.tran.x, TCP.tran.y, TCP.tran.z, TCP.rpy.rx, TCP.rpy.ry, TCP.rpy.rz);
        robot.CloseRPC();
        robot.Sleep(9999999);
    }
    
Establecer la velocidad física en tiempo real
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la velocidad física en tiempo real
    * @param [in] speed Valor de la velocidad física, mm/s
    * @return Código de error
    */
    public int SetPhySpeedInstant(double speed)
        
Ejemplo de código de establecimiento de la velocidad física en tiempo real
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static class RobotThread implements Runnable {
        private final Robot robot;
        private volatile boolean running = true;

        public RobotThread(Robot robot) {
            this.robot = robot;
        }

        public void stop() {
            running = false;
        }

        @Override
        public void run() {
            BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));

            while (running) {
                try {
                    System.out.print("Please input speed value (0~100, q to quit): ");
                    System.out.flush();

                    String line = reader.readLine();

                    // 1. Fin del flujo (Ctrl+D / Ctrl+Z / cierre de tubería)
                    if (line == null) {
                        System.out.println("\nInput stream closed, exit speed input thread.");
                        break;
                    }

                    // 2. Eliminar espacios en blanco al inicio y al final
                    line = line.trim();

                    // 3. Línea vacía: omitir, no imprimir nada
                    if (line.isEmpty()) {
                        continue;
                    }

                    // 4. Comando de salida
                    if ("q".equalsIgnoreCase(line)) {
                        System.out.println("Quit speed input thread.");
                        break;
                    }

                    // 5. Analizar el número
                    int speed;
                    try {
                        speed = Integer.parseInt(line);
                    } catch (NumberFormatException e) {
                        System.out.println("Invalid number: [" + line + "]");
                        continue;
                    }

                    // 7. Enviar la velocidad
                    robot.SetPhySpeedInstant(speed);
                    System.out.println("SetSpeed -> " + speed + "%");

                } catch (IOException e) {
                    System.out.println("Input error: " + e.getMessage());
                    break;
                }
            }
        }

        public static int TestSetPhySpeed(Robot robot) {
            // 1. Cambiar al modo de posición (equivalente a Python robot.Mode(0))
            robot.Mode(0);

            // 2. Habilitar la alimentación (equivalente a Python robot.RobotEnable(1))
            robot.RobotEnable(1);

            // 3. Dos puntos objetivo
            JointPos j1 = new JointPos(-60.206, -49.449, 79.476, -124.322, -88.416, -45.209);
            DescPose d1 = new DescPose(-412.929, 510.912, 94.557, -175.850, -1.933, 74.992);
            JointPos j2 = new JointPos(-141.282, -40.962, 62.359, -110.496, -85.512, -126.379);
            DescPose d2 = new DescPose(586.847, 510.915, 94.560, -175.851, -1.934, 74.991);

            ExaxisPos ex = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
            DescPose zeroOff = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);

            // 4. Iniciar el hilo de entrada (hilo daemon)
            RobotThread speedInput = new RobotThread(robot);
            Thread th = new Thread(speedInput, "SpeedInputThread");
            th.setDaemon(true);
            th.start();

            // 5. Bucle MoveL, durante el cual se puede introducir la velocidad en tiempo real
            try {
                while (true) {
                    int rtn = robot.MoveL(j1, d1, 1, 0, 100, 100, 100,
                            -1, 0, ex, 0, 0, zeroOff, 100, 0, 0, 10);
                    if (rtn != 0) {
                        System.out.println("MoveL j1->d1 failed, rtn=" + rtn);
                        break;
                    }

                    rtn = robot.MoveL(j2, d2, 1, 0, 100, 100, 100,
                            -1, 0, ex, 0, 0, zeroOff, 100, 0, 0, 10);
                    if (rtn != 0) {
                        System.out.println("MoveL j2->d2 failed, rtn=" + rtn);
                        break;
                    }

                    // Ceder la CPU para evitar que el bucle principal deje sin recursos al hilo de entrada
                    Thread.sleep(10);
                }
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            } finally {
                speedInput.stop();
            }

            return 0;
        }
    }