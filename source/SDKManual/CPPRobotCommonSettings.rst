Configuraciones habituales del robot
=====================================

.. toctree:: 
    :maxdepth: 5

Establecer el punto de referencia de la herramienta - método de seis puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Establecer el punto de referencia de la herramienta - método de seis puntos
     * @param [in] point_num Número de punto, rango [1~6] 
     * @return Código de error
     */
    errno_t SetToolPoint(int point_num);

Calcular el sistema de coordenadas de herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Calcular el sistema de coordenadas de herramienta
     * @param [out] tcp_pose Sistema de coordenadas de herramienta
     * @return Código de error
     */
    errno_t ComputeTool(DescPose *tcp_pose);

Establecer el punto de referencia de la herramienta - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Establecer el punto de referencia de la herramienta - método de cuatro puntos
     * @param [in] point_num Número de punto, rango [1~4] 
     * @return Código de error
     */
    errno_t SetTcp4RefPoint(int point_num);

Calcular el sistema de coordenadas de herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Calcular el sistema de coordenadas de herramienta
     * @param [out] tcp_pose Sistema de coordenadas de herramienta
     * @return Código de error
     */
    errno_t ComputeTcp4(DescPose *tcp_pose);

Calcular el sistema de coordenadas de herramienta a partir de la información de puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
	 * @brief Calcular el sistema de coordenadas de herramienta a partir de la información de puntos
	 * @param [in] method Método de cálculo; 0-método de cuatro puntos; 1-método de seis puntos
	 * @param [in] pos Conjunto de posiciones articulares; en el método de cuatro puntos la longitud del array es 4, en el método de seis puntos la longitud es 6
	 * @param [out] coord Resultado del sistema de coordenadas de herramienta
	 * @return Código de error
    */
	errno_t ComputeToolCoordWithPoints(int method, JointPos pos[], DescPose& coord);

Establecer el sistema de coordenadas de herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

	/**
	 * @brief  Establecer el sistema de coordenadas de herramienta
	 * @param  [in] id Número del sistema de coordenadas, rango [0~14]
	 * @param  [in] coord  Pose del centro de herramienta respecto al centro de la brida del extremo
	 * @param  [in] type  0-sistema de coordenadas de herramienta, 1-sistema de coordenadas del sensor
	 * @param  [in] install Posición de instalación, 0-extremo del robot, 1-exterior del robot
	 * @param  [in] toolID ID de la herramienta
	 * @param  [in] loadNum Número de carga
	 * @return  Código de error
	 */
	errno_t SetToolCoord(int id, DescPose *coord, int type, int install, int toolID, int loadNum);

Establecer la lista de sistemas de coordenadas de herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
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
	errno_t SetToolList(int id, DescPose *coord, int type, int install, int loadNum);

Obtener el sistema de coordenadas de herramienta actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el sistema de coordenadas de herramienta actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] desc_pos Pose del sistema de coordenadas de herramienta
    * @return  Código de error
    */
    errno_t  GetTCPOffset(uint8_t flag, DescPose *desc_pos);

Ejemplo de código de operación del sistema de coordenadas de herramienta del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestTCPCompute(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         DescPose p1Desc(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
         JointPos p1Joint(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);
         DescPose p2Desc(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
         JointPos p2Joint(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);
         DescPose p3Desc(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
         JointPos p3Joint(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);
         DescPose p4Desc(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
         JointPos p4Joint(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);
         DescPose p5Desc(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
         JointPos p5Joint(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);
         DescPose p6Desc(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
         JointPos p6Joint(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         JointPos posJ[6] = { p1Joint , p2Joint , p3Joint , p4Joint , p5Joint , p6Joint };
         DescPose coordRtn = {};
         rtn = robot.ComputeToolCoordWithPoints(1, posJ, coordRtn);
         printf("ComputeToolCoordWithPoints    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(1);
         robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(2);
         robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(3);
         robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(4);
         robot.MoveJ(&p5Joint, &p5Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(5);
         robot.MoveJ(&p6Joint, &p6Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetToolPoint(6);
         rtn = robot.ComputeTool(&coordRtn);
         printf("6 Point ComputeTool        %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.SetToolList(1, &coordRtn, 0, 0, 0);
         robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(1);
         robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(2);
         robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(3);
         robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetTcp4RefPoint(4);
         rtn = robot.ComputeTcp4(&coordRtn);
         printf("4 Point ComputeTool        %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.SetToolCoord(2, &coordRtn, 0, 0, 1, 0);
         DescPose getCoord = {};
         rtn = robot.GetTCPOffset(0, &getCoord);
         printf("GetTCPOffset    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.CloseRPC();
         return 0;
     }

Establecer el punto de referencia de la herramienta externa - método de seis puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Establecer el punto de referencia de la herramienta externa - método de seis puntos
     * @param [in] point_num Número de punto, rango [1~4] 
     * @return Código de error
     */
    errno_t SetExTCPPoint(int point_num);

Calcular el sistema de coordenadas de herramienta externa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Calcular el sistema de coordenadas de herramienta externa
     * @param [out] tcp_pose Sistema de coordenadas de herramienta externa
     * @return Código de error
     */
    errno_t ComputeExTCF(DescPose *tcp_pose);  

Establecer el sistema de coordenadas de herramienta externa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8

.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer el sistema de coordenadas de herramienta externa
    * @param  [in] id Número del sistema de coordenadas; 20-39 corresponden al sistema de coordenadas de herramienta externa 0-19
    * @param  [in] etcp  Pose del centro de herramienta respecto al centro de la brida del extremo
    * @param  [in] etool  Pose del sistema de coordenadas de pieza instalado en el extremo del robot
    * @return  Código de error
    */
    errno_t  SetExToolCoord(int id, DescPose *etcp, DescPose *etool);

Establecer la lista de sistemas de coordenadas de herramienta externa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8

.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer la lista de sistemas de coordenadas de herramienta externa
    * @param  [in] id Número del sistema de coordenadas; 20-39 corresponden al sistema de coordenadas de herramienta externa 0-19
    * @param  [in] etcp  Pose del centro de herramienta respecto al centro de la brida del extremo
    * @param  [in] etool  Pose del sistema de coordenadas de pieza instalado en el extremo del robot
    * @return  Código de error
    */
    errno_t  SetExToolList(int id, DescPose *etcp, DescPose *etool);

Ejemplo de código de operación del sistema de coordenadas de herramienta externa del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8

.. code-block:: c++
    :linenos:

    int TestExtCoord(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        DescPose p1Desc(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);
        DescPose p2Desc(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);
        DescPose p3Desc(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);
        ExaxisPos exaxisPos(0, 0, 0, 0);
        DescPose offdese(0, 0, 0, 0, 0, 0);
        DescPose posTCP[3] = { p1Desc , p2Desc , p3Desc };
        DescPose coordRtn = {};
        robot.MoveJ(&p1Joint, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetExTCPPoint(1);
        robot.MoveJ(&p2Joint, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetExTCPPoint(2);
        robot.MoveJ(&p3Joint, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetExTCPPoint(3);
        rtn = robot.ComputeExTCF(&coordRtn);
        printf("ComputeExTCF          %d coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
        robot.SetExToolCoord(21, &coordRtn, &offdese);
        robot.SetExToolList(21, &coordRtn, &offdese);
        robot.CloseRPC();
        return 0;
    }

Establecer el punto de referencia de la pieza - método de tres puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Establecer el punto de referencia de la pieza - método de tres puntos
     * @param [in] point_num Número de punto, rango [1~3] 
     * @return Código de error
     */
    errno_t SetWObjCoordPoint(int point_num);

Calcular el sistema de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

	/**
	 * @brief  Calcular el sistema de coordenadas de pieza
	 * @param [in] method Método de cálculo 0: origen-eje x-eje z  1: origen-eje x-plano xy
	 * @param [in] refFrame Sistema de coordenadas de referencia
	 * @param [out] wobj_pose Sistema de coordenadas de pieza
	 * @return Código de error
	 */
	errno_t ComputeWObjCoord(int method, int refFrame, DescPose *wobj_pose);

Establecer el sistema de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
	 * @brief  Establecer el sistema de coordenadas de pieza
	 * @param  [in] id Número del sistema de coordenadas, rango [0~14]
	 * @param  [in] coord  Pose del sistema de coordenadas de pieza respecto al centro de la brida del extremo
	 * @param  [in] refFrame Sistema de coordenadas de referencia
	 * @return  Código de error
	 */
	errno_t SetWObjCoord(int id, DescPose *coord, int refFrame);

Establecer la lista de sistemas de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

	/**
	 * @brief  Establecer la lista de sistemas de coordenadas de pieza
	 * @param  [in] id Número del sistema de coordenadas, rango [0~14]
	 * @param  [in] coord  Pose del sistema de coordenadas de pieza respecto al centro de la brida del extremo
	 * @param  [in] refFrame Sistema de coordenadas de referencia
	 * @return  Código de error
	 */
	errno_t SetWObjList(int id, DescPose *coord, int refFrame);

Calcular el sistema de coordenadas de pieza a partir de la información de puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
	 * @brief Calcular el sistema de coordenadas de pieza a partir de la información de puntos
	 * @param [in] method Método de cálculo; 0: origen-eje x-eje z  1: origen-eje x-plano xy
	 * @param [in] pos Conjunto de tres posiciones TCP
	 * @param [in] refFrame Sistema de coordenadas de referencia
	 * @param [out] coord Resultado del sistema de coordenadas de herramienta
	 * @return Código de error
    */
	errno_t ComputeWObjCoordWithPoints(int method, DescPose pos[], int refFrame, DescPose& coord);

Obtener el sistema de coordenadas de pieza actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el sistema de coordenadas de pieza actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] desc_pos Pose del sistema de coordenadas de pieza
    * @return  Código de error
    */   
    errno_t  GetWObjOffset(uint8_t flag, DescPose *desc_pos);

Ejemplo de código de operación del sistema de coordenadas de pieza del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestWobjCoord(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         DescPose p1Desc(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
         JointPos p1Joint(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);
         DescPose p2Desc(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
         JointPos p2Joint(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);
         DescPose p3Desc(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
         JointPos p3Joint(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         DescPose posTCP[3] = { p1Desc , p2Desc , p3Desc };
         DescPose coordRtn = {};
         rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, coordRtn);
         printf("ComputeWObjCoordWithPoints    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.MoveJ(&p1Joint, &p1Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(1);
         robot.MoveJ(&p2Joint, &p2Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(2);
         robot.MoveJ(&p3Joint, &p3Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(3);
         rtn = robot.ComputeWObjCoord(1, 0, &coordRtn);
         printf("ComputeWObjCoord                   %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.SetWObjCoord(1, &coordRtn, 0);
         robot.SetWObjList(1, &coordRtn, 0);
         DescPose getWobjDesc = {};
         rtn = robot.GetWObjOffset(0, &getWobjDesc);
         printf("GetWObjOffset                   %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.CloseRPC();
         return 0;
     }

Establecer la velocidad global
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer la velocidad global
    * @param  [in]  vel  Porcentaje de velocidad, rango [0~100]
    * @return  Código de error
    */
    errno_t  SetSpeed(int vel);

Establecer la aceleración del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

	/**
	 * @brief Establecer la aceleración del robot
	 * @param [in] acc Porcentaje de aceleración del robot
	 * @return Código de error
	 */
	errno_t SetOaccScale(double acc);

Obtener la velocidad predeterminada del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener la velocidad predeterminada del robot
    * @param  [out]  vel  Velocidad, unidad mm/s
    * @return  Código de error
    */   
    errno_t  GetDefaultTransVel(float *vel);
    
Establecer el peso de la carga del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
	 * @brief  Establecer el peso de la carga del extremo
	 * @param  [in] loadNum Número de carga
	 * @param  [in] weight  Peso de la carga, unidad kg
	 * @return  Código de error
    */
    errno_t SetLoadWeight(int loadNum = 0, float weight);

Establecer las coordenadas del centro de gravedad de la carga del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer las coordenadas del centro de gravedad de la carga del extremo
    * @param [in] loadNum Número de carga
    * @param [in] coord Coordenadas del centro de gravedad, unidad mm
    * @return Código de error
    */
    errno_t SetLoadCoord(int loadNum, DescTran* coord);

Obtener el peso de la carga actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el peso de la carga actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] weight Peso de la carga, unidad kg
    * @return  Código de error
    */
    errno_t  GetTargetPayload(uint8_t flag, float *weight);

Obtener el centro de gravedad de la carga actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el centro de gravedad de la carga actual
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] cog Centro de gravedad de la carga, unidad mm
    * @return  Código de error
    */   
    errno_t  GetTargetPayloadCog(uint8_t flag, DescTran *cog);

Establecer el modo de instalación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer el modo de instalación del robot
    * @param  [in] install  Modo de instalación, 0-instalación vertical, 1-instalación lateral, 2-instalación invertida
    * @return  Código de error
    */
    errno_t  SetRobotInstallPos(uint8_t install);   

Establecer el ángulo de instalación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer el ángulo de instalación del robot, instalación libre
    * @param  [in] yangle  Ángulo de inclinación
    * @param  [in] zangle  Ángulo de rotación
    * @return  Código de error
    */
    errno_t  SetRobotInstallAngle(double yangle, double zangle);

Obtener el ángulo de instalación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el ángulo de instalación del robot
    * @param  [out] yangle Ángulo de inclinación
    * @param  [out] zangle Ángulo de rotación
    * @return  Código de error
    */
    errno_t  GetRobotInstallAngle(float *yangle, float *zangle);

Establecer el valor de una variable del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer el valor de una variable del sistema
    * @param  [in]  id  Número de la variable, rango [1~20]
    * @param  [in]  value Valor de la variable
    * @return  Código de error
    */
    errno_t  SetSysVarValue(int id, float value);

Obtener el valor de una variable del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el valor de una variable del sistema
    * @param  [in] id Número de la variable del sistema, rango [1~20]
    * @param  [out] value  Valor de la variable del sistema
    * @return  Código de error
    */
    errno_t  GetSysVarValue(int id, float *value);

Ejemplo de código de configuraciones habituales del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestLoadInstall(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         for (int i = 1; i < 100; i++)
         {
             robot.SetSpeed(i);
             robot.SetOaccScale(i);
             robot.Sleep(30);
         }
         float defaultVel = 0.0;
         robot.GetDefaultTransVel(&defaultVel);
         printf("GetDefaultTransVel is %f\n", defaultVel);
         for (int i = 1; i < 21; i++)
         {
             robot.SetSysVarValue(i, i + 0.5);
             robot.Sleep(100);
         }
         for (int i = 1; i < 21; i++)
         {
             float value = 0;
             robot.GetSysVarValue(i, &value);
             printf("sys value  %d is :%f\n", i, value);
             robot.Sleep(100);
         }
         robot.SetLoadWeight(0, 2.5);
         DescTran loadCoord = {};
         loadCoord.x = 3.0;
         loadCoord.y = 4.0;
         loadCoord.z = 5.0;
         robot.SetLoadCoord(&loadCoord);
         robot.Sleep(1000);
         float getLoad = 0.0;
         robot.GetTargetPayload(0, &getLoad);
         DescTran getLoadTran = {};
         robot.GetTargetPayloadCog(0, &getLoadTran);
         printf("get load is %f; get load cog is %f %f %f\n", getLoad, getLoadTran.x, getLoadTran.y, getLoadTran.z);
         robot.SetRobotInstallPos(0);
         robot.SetRobotInstallAngle(15.0, 25.0);
         float anglex = 0.0;
         float angley = 0.0;
         robot.GetRobotInstallAngle(&anglex, &angley);
         printf("GetRobotInstallAngle x:  %f;  y:  %f\n", anglex, angley);
         robot.CloseRPC();
         return 0;
     }

Interruptor de compensación de fricción de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Interruptor de compensación de fricción de las articulaciones
    * @param  [in]  state  0-desactivado, 1-activado
    * @return  Código de error
    */
    errno_t  FrictionCompensationOnOff(uint8_t state);

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación vertical
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación vertical
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    errno_t  SetFrictionValue_level(float coeff[6]);

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación lateral
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación lateral
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    errno_t  SetFrictionValue_wall(float coeff[6]);

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación invertida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación invertida
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    errno_t  SetFrictionValue_ceiling(float coeff[6]);

Establecer el coeficiente de compensación de fricción de las articulaciones - instalación libre
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer el coeficiente de compensación de fricción de las articulaciones - instalación libre
    * @param  [in]  coeff Coeficientes de compensación de las seis articulaciones, rango [0~1]
    * @return  Código de error
    */
    errno_t  SetFrictionValue_freedom(float coeff[6]);

Ejemplo de código de configuración de compensación de fricción de las articulaciones del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFriction(void)
    {
       ROBOT_STATE_PKG pkg = {};
       FRRobot robot;

       robot.LoggerInit();
       robot.SetLoggerLevel(1);
       int rtn = robot.RPC("192.168.58.2");
       if (rtn != 0)
       {
          return -1;
       }
       robot.SetReConnectParam(true, 30000, 500);
       float lcoeff[6] = { 0.9,0.9,0.9,0.9,0.9,0.9 };
       float wcoeff[6] = { 0.4,0.4,0.4,0.4,0.4,0.4 };
       float ccoeff[6] = { 0.6,0.6,0.6,0.6,0.6,0.6 };
       float fcoeff[6] = { 0.5,0.5,0.5,0.5,0.5,0.5 };
       rtn = robot.FrictionCompensationOnOff(1);
       printf("FrictionCompensationOnOff rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_level(lcoeff);
       printf("SetFrictionValue_level rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_wall(wcoeff);
       printf("SetFrictionValue_wall rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_ceiling(ccoeff);
       printf("SetFrictionValue_ceiling rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_freedom(fcoeff);
       printf("SetFrictionValue_freedom rtn is %d\n", rtn);
       robot.CloseRPC();
       return 0;
    }

Consultar el código de error del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Consultar el código de error del robot
     * @param  [out]  maincode  Código de error principal
     * @param  [out]  subcode   Código de error secundario
     * @return  Código de error
     */ 
    errno_t  GetRobotErrorCode(int *maincode, int *subcode);

Borrado del estado de error
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Borrado del estado de error
    * @return  Código de error
    */
    errno_t  ResetAllError();

Ejemplo de código de obtención del estado de fallo y borrado de errores del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetError(void)
    {
       ROBOT_STATE_PKG pkg = {};
       FRRobot robot;
       robot.LoggerInit();
       robot.SetLoggerLevel(1);
       int rtn = robot.RPC("192.168.58.2");
       if (rtn != 0)
       {
          return -1;
       }
       robot.SetReConnectParam(true, 30000, 500);
       int maincode, subcode;
       robot.GetRobotErrorCode(&maincode, &subcode);
       printf("robot maincode is %d; subcode is %d\n", maincode, subcode);
       robot.ResetAllError();
       robot.Sleep(1000);
       robot.GetRobotErrorCode(&maincode, &subcode);
       printf("robot maincode is %d; subcode is %d\n", maincode, subcode);
       robot.CloseRPC();
       return 0;
    }

Establecer los parámetros de monitorización de temperatura y corriente del ventilador del armario de control de tensión amplia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer los parámetros de monitorización de temperatura y corriente del ventilador del armario de control de tensión amplia
    * @param [in] enable 0-no habilitar la monitorización; 1-habilitar la monitorización
    * @param [in] period Período de monitorización (s), rango 1-100
    * @return Código de error
    */
    errno_t SetWideBoxTempFanMonitorParam(int enable, int period);
    
Obtener los parámetros de monitorización de temperatura y corriente del ventilador del armario de control de tensión amplia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener los parámetros de monitorización de temperatura y corriente del ventilador del armario de control de tensión amplia
    * @param [out] enable 0-no habilitar la monitorización; 1-habilitar la monitorización
    * @param [out] period Período de monitorización (s), rango 1-100
    * @return Código de error
    */
    errno_t GetWideBoxTempFanMonitorParam(int &enable, int &period);
    
Ejemplo de código de obtención de temperatura y corriente del ventilador del armario de control de tensión amplia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestWideVoltageCtrlBoxtemp(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         printf("robot rpc rtn is %d\n", rtn);
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         robot.SetWideBoxTempFanMonitorParam(1, 2);
         int enable = 0;
         int period = 0;
         robot.GetWideBoxTempFanMonitorParam(enable, period);
         printf("GetWideBoxTempFanMonitorParam enable is %d   period is %d\n", enable, period);
         for (int i = 0; i < 100; i++)
         {
             robot.GetRobotRealTimeState(&pkg);
             printf("robot ctrl box temp is %f,  fan current is %d\n", pkg.wideVoltageCtrlBoxTemp, pkg.wideVoltageCtrlBoxFanCurrent);
             robot.Sleep(100);
         }
         rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);
         printf("SetWideBoxTempFanMonitorParam rtn is %d\n", rtn);
         enable = 0;
         period = 0;
         robot.GetWideBoxTempFanMonitorParam(enable, period);
         printf("GetWideBoxTempFanMonitorParam enable is %d   period is %d\n", enable, period);
         for (int i = 0; i < 100; i++)
         {
             robot.GetRobotRealTimeState(&pkg);
             printf("robot ctrl box temp is %f,  fan current is %d\n", pkg.wideVoltageCtrlBoxTemp, pkg.wideVoltageCtrlBoxFanCurrent);
             robot.Sleep(100);
         }
         robot.CloseRPC();
         robot.Sleep(2000);
         return 0;
     }
         
Calcular el resultado de la calibración de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Calcular el resultado de la calibración de foco
    * @param [in] pointNum Número de puntos de calibración
    * @param [out] resultPos XYZ del resultado de la calibración
    * @param [out] accuracy Error de precisión de la calibración
    * @return Código de error
    */
    errno_t ComputeFocusCalib(int pointNum, DescTran& resultPos, float& accuracy);
         
Establecer las coordenadas de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer las coordenadas de foco
    * @param [in] pos Coordenadas XYZ del foco
    * @return Código de error
    */
    errno_t SetFocusPosition(DescTran pos);
         
Activar el seguimiento de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t FocusStart(double kp, double kpredict, double aMax, double vMax, int type);
         
Detener el seguimiento de foco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Detener el seguimiento de foco
    * @return Código de error
    */
    errno_t FocusEnd();

Ejemplo de código de seguimiento de foco del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFocus()
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      DescPose p1Desc(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
      JointPos p1Joint(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);
      DescPose p2Desc(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
      JointPos p2Joint(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);
      DescPose p3Desc(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
      JointPos p3Joint(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);
      DescPose p4Desc(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
      JointPos p4Joint(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);
      DescPose p5Desc(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
      JointPos p5Joint(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);
      DescPose p6Desc(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
      JointPos p6Joint(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 100, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(1);
      robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(2);
      robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(3);
      robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(4);
      DescPose coordRtn = {};
      rtn = robot.ComputeTcp4(&coordRtn);
      printf("4 Point ComputeTool    %d coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
      robot.SetToolCoord(1, &coordRtn, 0, 0, 1, 0);
      robot.GetForwardKin(&p1Joint, &p1Desc);
      robot.GetForwardKin(&p2Joint, &p2Desc);
      robot.GetForwardKin(&p3Joint, &p3Desc);
      robot.SetFocusCalibPoint(1, p1Desc);
      robot.SetFocusCalibPoint(2, p2Desc);
      robot.SetFocusCalibPoint(3, p3Desc);
      DescTran resultPos = {};
      float accuracy = 0.0;
      rtn = robot.ComputeFocusCalib(3, resultPos, accuracy);
      printf("ComputeFocusCalib coord is %d %f %f %f accuracy is %f\n", rtn, resultPos.x, resultPos.y, resultPos.z, accuracy);
      rtn = robot.SetFocusPosition(resultPos);
      robot.GetForwardKin(&p5Joint, &p5Desc);
      robot.GetForwardKin(&p6Joint, &p6Desc);
      robot.MoveL(&p5Joint, &p5Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.MoveL(&p6Joint, &p6Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.FocusStart(50, 19, 710, 90, 0);
      robot.MoveL(&p5Joint, &p5Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.MoveL(&p6Joint, &p6Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.FocusEnd();
      robot.CloseRPC();
      return 0;
    }

Activación de la función de calibración de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Activación de la función de calibración de sensibilidad del sensor de par de las articulaciones
    * @param [in] status 0-desactivar; 1-activar
    * @return  Código de error
    */
    errno_t JointSensitivityEnable(int status);

Adquisición de datos de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Adquisición de datos de sensibilidad del sensor de par de las articulaciones
    * @return Código de error
    */
    errno_t JointSensitivityCollect();
    

Obtener el resultado de la calibración de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el resultado de la calibración de sensibilidad del sensor de par de las articulaciones
    * @param [out] calibResult Sensibilidad de las articulaciones j1~j6 [0-1]
    * @param [out] linearityn Linealidad de las articulaciones j1~j6 [0-1]
    * @return Código de error
    */
    errno_t JointSensitivityCalibration(double calibResult[6], double linearity[6]);

Obtener el error de histéresis del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el error de histéresis del sensor de par de las articulaciones
    * @param [out] hysteresisError Error de histéresis de las articulaciones j1~j6
    * @return Código de error
    */
    errno_t JointHysteresisError(double hysteresisError[6]);
    
Obtener la repetibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:
    
    /**
    * @brief Obtener la repetibilidad del sensor de par de las articulaciones
    * @param [out] repeatability Repetibilidad del sensor de par de las articulaciones j1~j6
    * @return Código de error
    */
    errno_t JointRepeatability(double repeatability[6]);
    
Establecer los parámetros del sensor de fuerza de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t SetAdmittanceParams(double M[6], double B[6], double K[6], double threshold[6], double sensitivity[6], int setZeroFlag);

Ejemplo de código de calibración automática de sensibilidad del sensor de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSensitivityCalib()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        printf("JointSensitivityEnable rtn is %d\n", rtn);
        JointPos curJPos = {};
        robot.GetActualJointPosDegree(0, &curJPos);
        ExaxisPos epos = { 0,0,0,0 };
        DescPose offset_pos = { 0,0,0,0,0,0 };
        JointPos jointPos1 = { curJPos.jPos[0], 0, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos1 = {};
        robot.GetForwardKin(&jointPos1, &descPos1);
        robot.MoveJ(&jointPos1, &descPos1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 1 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos2 = { curJPos.jPos[0], -30, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos2 = {};
        robot.GetForwardKin(&jointPos2, &descPos2);
        robot.MoveJ(&jointPos2, &descPos2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 2 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos3 = { curJPos.jPos[0], -60, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos3 = {};
        robot.GetForwardKin(&jointPos3, &descPos3);
        robot.MoveJ(&jointPos3, &descPos3, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 3 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos4 = { curJPos.jPos[0], -90, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos4 = {};
        robot.GetForwardKin(&jointPos4, &descPos4);
        robot.MoveJ(&jointPos4, &descPos4, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 4 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos5 = { curJPos.jPos[0], -120, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos5 = {};
        robot.GetForwardKin(&jointPos5, &descPos5);
        robot.MoveJ(&jointPos5, &descPos5, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 5 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos6 = { curJPos.jPos[0], -150, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos6 = {};
        robot.GetForwardKin(&jointPos6, &descPos6);
        robot.MoveJ(&jointPos6, &descPos6, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 6 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos7 = { curJPos.jPos[0], -180, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos7 = {};
        robot.GetForwardKin(&jointPos7, &descPos7);
        robot.MoveJ(&jointPos7, &descPos7, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 7 rtn is %d\n", rtn);
        robot.Sleep(100);
        //-------------------
        robot.MoveJ(&jointPos6, &descPos6, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 8 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos5, &descPos5, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 9 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos4, &descPos4, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 10 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos3, &descPos3, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 11 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos2, &descPos2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 12 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos1, &descPos1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 13 rtn is %d\n", rtn);
        robot.Sleep(100);
        double calibResult[6] = { 0.0 };
        double linearity[6] = { 0.0 };
        rtn = robot.JointSensitivityCalibration(calibResult, linearity);
        printf("JointSensitivityCalibration rtn is %d\n", rtn);
        rtn = robot.JointSensitivityEnable(0);
        printf("JointSensitivityEnable rtn is %d\n", rtn);
        printf("jointSensor Calib result is %f %f %f %f %f %f\njointSensor linearity is %f %f %f %f %f %f\n", 
            calibResult[0], calibResult[1], calibResult[2], 
            calibResult[3], calibResult[4], calibResult[5], 
            linearity[0], linearity[1], linearity[2],
            linearity[3], linearity[4], linearity[5]);
        double hysteresisError[6] = { 0.0 };
        rtn = robot.JointHysteresisError(hysteresisError);
        printf("JointHysteresisError result is %f %f %f %f %f %f\n",
            hysteresisError[0], hysteresisError[1], hysteresisError[2],
            hysteresisError[3], hysteresisError[4], hysteresisError[5]);
        double repeatability[6] = { 0.0 };
        rtn = robot.JointRepeatability(repeatability);
        printf("JointRepeatability result is %f %f %f %f %f %f\n",
            repeatability[0], repeatability[1], repeatability[2],
            repeatability[3], repeatability[4], repeatability[5]);
        double M[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double B[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double K[6] = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double threshold[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        printf("SetAdmittanceParams rtn is %d\n", rtn);
        robot.CloseRPC();
    }
    
Obtener el número de tramas de error de los 8 puertos esclavos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t GetSlavePortErrCounter(int inRecvErr[8], int inCRCErr[8], int inTransmitErr[8], int inLinkErr[8], int outRecvErr[8], int outCRCErr[8], int outTransmitErr[8], int outLinkErr[8]);

Poner a cero las tramas de error del puerto esclavo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Poner a cero las tramas de error del puerto esclavo
    * @param [in] slaveID Número de esclavo 0~7
    * @return Código de error
    */
    errno_t SlavePortErrCounterClear(int slaveID);
    
Ejemplo de código de obtención de tramas de error del puerto esclavo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSlavePortErr()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        int inRecvErr[8] = {0.0}; 
        int inCRCErr[8] = { 0.0 };
        int inTransmitErr[8] = { 0.0 };
        int inLinkErr[8] = { 0.0 };
        int outRecvErr[8] = { 0.0 };
        int outCRCErr[8] = { 0.0 };
        int outTransmitErr[8] = { 0.0 };
        int outLinkErr[8] = { 0.0 };
        robot.GetSlavePortErrCounter(inRecvErr,  inCRCErr, inTransmitErr, inLinkErr,
            outRecvErr, outCRCErr, outTransmitErr, outLinkErr);
        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inRecvErr[i]);
            }
            if (inCRCErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inCRCErr[i]);
            }
            if (inTransmitErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inTransmitErr[i]);
            }
            if (inLinkErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inLinkErr[i]);
            }
            if (outRecvErr[i] != 0)
            {
                printf("outRecvErr %d is %d\n", i, outRecvErr[i]);
            }
            if (outCRCErr[i] != 0)
            {
                printf("outCRCErr %d is %d\n", i, outCRCErr[i]);
            }
            if (outTransmitErr[i] != 0)
            {
                printf("outTransmitErr %d is %d\n", i, outTransmitErr[i]);
            }
            if (outLinkErr[i] != 0)
            {
                printf("outLinkErr %d is %d\n", i, outLinkErr[i]);
            }
        }
        printf("others has no err!\n");
        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }
        robot.CloseRPC();
        return 0;
    }

Establecer el coeficiente de prealimentación de velocidad de cada eje
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el coeficiente de prealimentación de velocidad de cada eje
    * @param [in] radio Coeficiente de prealimentación de velocidad de cada eje
    * @return Código de error
    */
    errno_t SetVelFeedForwardRatio(double radio[6]);

Obtener el coeficiente de prealimentación de velocidad de cada eje
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el coeficiente de prealimentación de velocidad de cada eje
    * @param [out] radio Coeficiente de prealimentación de velocidad de cada eje
    * @return Código de error
    */
    errno_t GetVelFeedForwardRatio(double radio[6]);

Ejemplo de código del coeficiente de prealimentación de velocidad del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestVelFeedForwardRatio()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        double setRadio[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double getRadio[6] = { 0.0 };
        robot.GetVelFeedForwardRatio(getRadio);
        printf(" %f %f %f %f %f %f\n", getRadio[0], getRadio[1], getRadio[2], getRadio[3], getRadio[4], getRadio[5]);
        robot.CloseRPC();
        return 0;
    }

Calibración TCP con sensor fotoeléctrico - cálculo del RPY de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t TCPComputeRPY(DescPose Btool, DescPose Etool, DescPose sensor, double radius, double dz, Rpy& TCPRPY);

Calibración TCP con sensor fotoeléctrico - cálculo del XYZ de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t TCPComputeXYZ(int select, double originDirection, DescTran pos1, DescTran pos2, DescTran pos3, DescTran pos4, DescTran& TCP);

Calibración TCP con sensor fotoeléctrico - iniciar el registro de la posición del centro de la brida del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Calibración TCP con sensor fotoeléctrico - iniciar el registro de la posición del centro de la brida del extremo
    * @return Código de error
    */
    errno_t TCPRecordFlangePosStart();

Calibración TCP con sensor fotoeléctrico - detener el registro de la posición del centro de la brida del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Calibración TCP con sensor fotoeléctrico - detener el registro de la posición del centro de la brida del extremo
    * @return Código de error
    */
    errno_t TCPRecordFlangePosEnd();

Calibración TCP con sensor fotoeléctrico - obtener la posición del centro de herramienta del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Calibración TCP con sensor fotoeléctrico - obtener la posición del centro de herramienta del extremo
    * @param [out] TCP Posición del centro de herramienta (x,y,z)
    * @return Código de error
    */
    errno_t TCPGetRecordFlangePos(DescTran& TCP);

Calibración TCP con sensor fotoeléctrico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Calibración TCP con sensor fotoeléctrico
    * @param [in] luaPath Ruta del programa lua de calibración automática: "FR_CalibrateTheToolTcp.lua"
    * @param [in] offsetX Desplazamiento del punto de enseñanza (x,y,z) mm
    * @param [out] TCP Sistema de coordenadas de herramienta tras la calibración (x,y,z,rx,ry,rz)
    * @return Código de error
    */
    errno_t PhotoelectricSensorTCPCalibration(std::string luaPath, DescTran offset, DescPose& TCP);

Ejemplo de código de calibración TCP con sensor fotoeléctrico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestPhotoelectricSensorTCPCalib(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        DescTran offset = { 10.0, 10.0, 3.0 };
        DescPose TCP = {};
        rtn = robot.PhotoelectricSensorTCPCalibration("FR_CalibrateTheToolTcp.lua", offset, TCP);
        printf("PhotoelectricSensorTCPCalibration rtn is  %d %f %f %f %f %f %f \n", rtn, TCP.tran.x, TCP.tran.y, TCP.tran.z, TCP.rpy.rx, TCP.rpy.ry, TCP.rpy.rz);
        robot.CloseRPC();
        robot.Sleep(9999999);
        return 0;
    }

Establecer la velocidad global de forma instantánea
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la velocidad global de forma instantánea
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @return Código de error
    */
    errno_t SetSpeedInstant(int vel);

Establecer la velocidad física de forma instantánea
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la velocidad física de forma instantánea
    * @param [in] speed Valor de velocidad física, mm/s
    * @return Código de error
    */
    errno_t SetPhySpeedInstant(double speed);

Ejemplo de código de configuración instantánea de la velocidad física
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    int TestSetPhySpeedInstant()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        double inputVal = 0.0;
        while (true)
        {
            std::cout << "Please input speed value: ";
            if (std::cin >> inputVal)
            {
                robot.SetPhySpeedInstant(inputVal);
            }
            else
            {
                std::cin.clear();
                std::cin.ignore();
                std::cout << "Invalid number!" << std::endl;
            }
        }
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }