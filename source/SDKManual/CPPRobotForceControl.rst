Control de fuerza del robot
============================

.. toctree:: 
    :maxdepth: 5

Configuración del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
	 * @brief  Configurar el sensor de fuerza
	 * @param  [in] company  Fabricante del sensor de fuerza, 17-Kunwei Technology, 19-Instituto 11 de Aeroespacial, 20-sensor ATI, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xinjingcheng (XJC), 26-NSR
	 * @param  [in] device  Número de dispositivo, Kunwei (0-KWR75B), Instituto 11 de Aeroespacial (0-MCS6A-200-4), ATI (0-AXIA80-M8), Zhongke Midian (0-MST2010), Weihang Minxin (0-WHC6L-YB-10A), NBIT (0-XLH93003ACS), Xinjingcheng XJC (0-XJC-6F-D82), NSR (0-NSR-FTSensorA)
	 * @param  [in] softvesion  Número de versión del software, no se utiliza por ahora, por defecto 0
	 * @param  [in] bus Posición del bus del extremo donde está conectado el dispositivo, no se utiliza por ahora, por defecto 0
	 * @return  Código de error
	 */
    errno_t FT_SetConfig(int company, int device, int softvesion, int bus);

Obtener la configuración del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener la configuración del sensor de fuerza
    * @param  [in] company  Fabricante del sensor de fuerza, pendiente de definir
    * @param  [in] device  Número de dispositivo, no se utiliza por ahora, por defecto 0
    * @param  [in] softvesion  Número de versión del software, no se utiliza por ahora, por defecto 0
    * @param  [in] bus Posición del bus del extremo donde está conectado el dispositivo, no se utiliza por ahora, por defecto 0
    * @return  Código de error
    */
    errno_t  FT_GetConfig(int *company, int *device, int *softvesion, int *bus);

Activación del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Activación del sensor de fuerza
    * @param  [in] act  0-restablecer, 1-activar
    * @return  Código de error
    */
    errno_t  FT_Activate(uint8_t act);

Puesta a cero del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Puesta a cero del sensor de fuerza
    * @param  [in] act  0-eliminar el cero, 1-corrección del cero
    * @return  Código de error
    */
    errno_t  FT_SetZero(uint8_t act);   

Establecer el sistema de coordenadas de referencia del sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer el sistema de coordenadas de referencia del sensor de fuerza
    * @param  [in] ref  0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    * @return  Código de error
    */
    errno_t  FT_SetRCS(uint8_t ref); 

Establecer el peso de la carga bajo el sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Establecer el peso de la carga bajo el sensor de fuerza
     * @param [in] weight Peso de la carga kg
     * @return Código de error
     */
    errno_t SetForceSensorPayload(double weight);

Establecer el centro de gravedad de la carga bajo el sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Establecer el centro de gravedad de la carga bajo el sensor de fuerza
     * @param [in] x Centro de gravedad de la carga x mm
     * @param [in] y Centro de gravedad de la carga y mm
     * @param [in] z Centro de gravedad de la carga z mm
     * @return Código de error
     */
    errno_t SetForceSensorPayloadCog(double x, double y, double z);

Obtener el peso de la carga bajo el sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:
    
    /**
     * @brief Obtener el peso de la carga bajo el sensor de fuerza
     * @param [in] weight Peso de la carga kg
     * @return Código de error
     */
    errno_t GetForceSensorPayload(double& weight);

Obtener el centro de gravedad de la carga bajo el sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Obtener el centro de gravedad de la carga bajo el sensor de fuerza
     * @param [out] x Centro de gravedad de la carga x mm
     * @param [out] y Centro de gravedad de la carga y mm
     * @param [out] z Centro de gravedad de la carga z mm
     * @return Código de error
     */
    errno_t GetForceSensorPayloadCog(double& x, double& y, double& z);

Puesta a cero automática del sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Puesta a cero automática del sensor de fuerza
     * @param [out] weight Masa del sensor kg
     * @param [out] pos Centro de gravedad del sensor mm
     * @return Código de error
     */
    errno_t ForceSensorAutoComputeLoad(double& weight, DescTran& pos);

Obtener los datos de fuerza/par en el sistema de coordenadas de referencia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener los datos de fuerza/par en el sistema de coordenadas de referencia
    * @param  [out] ft  Fuerza/par, fx,fy,fz,tx,ty,tz
    * @return  Código de error
    */   
    errno_t  FT_GetForceTorqueRCS(ForceTorque *ft); 

Obtener los datos brutos de fuerza/par del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener los datos brutos de fuerza/par del sensor de fuerza
    * @param  [out] ft  Fuerza/par, fx,fy,fz,tx,ty,tz
    * @return  Código de error
    */   
    errno_t  FT_GetForceTorqueOrigin(ForceTorque *ft); 

Ejemplo de código de configuración y puesta a cero automática del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTInit(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      robot.FT_GetForceTorqueOrigin(0, &ft);
      printf("ft origin:%f,%f,%f,%f,%f,%f\n", ft.fx, ft.fy, ft.fz, ft.tx, ft.ty, ft.tz);
      robot.FT_SetZero(1);
      robot.Sleep(1000);
      DescPose ftCoord = {};
      robot.FT_SetRCS(0, ftCoord);
      robot.SetForceSensorPayload(0.824);
      robot.SetForceSensorPayloadCog(0.778, 2.554, 48.765);
      double weight = 0;
      double x = 0, y = 0, z = 0;
      robot.GetForceSensorPayload(weight);
      robot.GetForceSensorPayloadCog(x, y, z);
      printf("the FT load is %lf, %lf %lf %lf\n", weight, x, y, z);
      robot.SetForceSensorPayload(0);
      robot.SetForceSensorPayloadCog(0, 0, 0);
      double computeWeight = 0;
      DescTran tran = {};
      robot.ForceSensorAutoComputeLoad(weight, tran);
      cout << "the result is weight " << weight << " pos is " << tran.x << " " << tran.y << " " << tran.z << endl;
      robot.CloseRPC();
      return 0;
    }


Registro de identificación del peso de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Registro de identificación del peso de la carga
    * @param  [in] id  Número del sistema de coordenadas del sensor, rango [1~14]
    * @return  Código de error
    */
    errno_t  FT_PdIdenRecord(int id);   

Cálculo de identificación del peso de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Cálculo de identificación del peso de la carga
    * @param  [out] weight  Peso de la carga, unidad kg
    * @return  Código de error
    */   
    errno_t  FT_PdIdenCompute(float *weight);

Registro de identificación del centro de gravedad de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Registro de identificación del centro de gravedad de la carga
    * @param  [in] id  Número del sistema de coordenadas del sensor, rango [1~14]
    * @param  [in] index Número de punto, rango [1~3]
    * @return  Código de error
    */
    errno_t  FT_PdCogIdenRecord(int id, int index);    

Cálculo de identificación del centro de gravedad de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Cálculo de identificación del centro de gravedad de la carga
    * @param  [out] cog  Centro de gravedad de la carga, unidad mm
    * @return  Código de error
    */   
    errno_t  FT_PdCogIdenCompute(DescTran *cog); 

Ejemplo de código de identificación de carga del sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTLoadCompute(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      robot.FT_GetForceTorqueOrigin(0, &ft);
      printf("ft origin:%f,%f,%f,%f,%f,%f\n", ft.fx, ft.fy, ft.fz, ft.tx, ft.ty, ft.tz);
      robot.FT_SetZero(1);
      robot.Sleep(1000);
      DescPose tcoord = {};
      tcoord.tran.z = 35.0;
      robot.SetToolCoord(10, &tcoord, 1, 0, 0, 0);
      robot.FT_PdIdenRecord(10);
      robot.Sleep(1000);
      float weight = 0.0;
      robot.FT_PdIdenCompute(&weight);
      printf("payload weight:%f\n", weight);
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_p3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      robot.MoveCart(&desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 1);
      robot.MoveCart(&desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 2);
      robot.MoveCart(&desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 3);
      robot.Sleep(1000);
      DescTran cog;
      memset(&cog, 0, sizeof(DescTran));
      robot.FT_PdCogIdenCompute(&cog);
      printf("cog:%f,%f,%f\n", cog.x, cog.y, cog.z);
      robot.CloseRPC();
      return 0;
    }

Protección contra colisiones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Protección contra colisiones
    * @param  [in] flag 0-desactivar la protección contra colisiones, 1-activar la protección contra colisiones
    * @param  [in] sensor_id Número del sensor de fuerza
    * @param  [in] select  Seleccionar si se detectan colisiones en los seis grados de libertad, 0-no detectar, 1-detectar
    * @param  [in] ft  Fuerza/par de colisión, fx,fy,fz,tx,ty,tz
    * @param  [in] max_threshold Umbral máximo
    * @param  [in] min_threshold Umbral mínimo
    * @note   Rango de detección de fuerza/par: (ft-min_threshold, ft+max_threshold)
    * @return  Código de error
    */   
    errno_t  FT_Guard(uint8_t flag, int sensor_id, uint8_t select[6], ForceTorque *ft, float max_threshold[6], float min_threshold[6]); 

Ejemplo de código de protección contra colisiones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTGuard(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t sensor_id = 1;
      uint8_t select[6] = { 1,1,1,1,1,1 };
      float max_threshold[6] = { 10.0,10.0,10.0,10.0,10.0,10.0 };
      float min_threshold[6] = { 5.0,5.0,5.0,5.0,5.0,5.0 };
      ForceTorque ft;
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_p3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      robot.FT_Guard(1, sensor_id, select, &ft, max_threshold, min_threshold);
      robot.MoveCart(&desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.MoveCart(&desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.MoveCart(&desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.FT_Guard(0, sensor_id, select, &ft, max_threshold, min_threshold);
      robot.CloseRPC();
      return 0;
    }

Control de fuerza constante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Control de fuerza constante
    * @param [in] flag 0-desactivar el control de fuerza constante, 1-activar el control de fuerza constante
    * @param [in] sensor_id Número del sensor de fuerza
    * @param [in] select Seleccionar si se detectan colisiones en los seis grados de libertad, 0-no detectar, 1-detectar
    * @param [in] ft Fuerza/par de colisión, fx,fy,fz,tx,ty,tz
    * @param [in] ft_pid Parámetros pid de fuerza, parámetros pid de par
    * @param [in] adj_sign Control de inicio/parada adaptativo, 0-desactivar, 1-activar
    * @param [in] ILC_sign Control de inicio/parada ILC, 0-detener, 1-entrenamiento, 2-operación real
    * @param [in] max_dis Distancia máxima de ajuste, unidad mm
    * @param [in] max_ang Ángulo máximo de ajuste, unidad deg
    * @param [in] M Parámetros de masa rx, ry [0.1-10], por defecto 2
    * @param [in] B Parámetros de amortiguación rx, ry [0.1-50], por defecto 8
    * @param [in] threshold Umbral de activación rx, ry [0-10], por defecto 0.2
    * @param [in] adjustCoeff Coeficiente de ajuste de par rx, ry [0-1], por defecto 1
    * @param [in] polishRadio Radio de pulido, unidad mm
    * @param [in] filter_Sign Indicador de activación del filtro 0-desactivado; 1-activado, desactivado por defecto
    * @param [in] posAdapt_sign Indicador de activación de adaptación de orientación 0-desactivado; 1-activado, desactivado por defecto
    * @param [in] isNoBlock Indicador de bloqueo, 0-bloqueante; 1-no bloqueante
    * @return Código de error
    */
    errno_t FT_Control(uint8_t flag, int sensor_id, uint8_t select[6], ForceTorque* ft, float ft_pid[6], uint8_t adj_sign, 
    uint8_t ILC_sign, float max_dis, float max_ang, double M[2], double B[2], double threshold[2], double adjustCoeff[2], double polishRadio = 0.0, int filter_Sign = 0, int posAdapt_sign = 0, int isNoBlock = 0);

Ejemplo de código de control de fuerza constante con amortiguación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTControlWithAdjustCoeff(void)
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
      uint8_t sensor_id = 10;
      uint8_t select[6] = { 0,0,1,0,0,0 };
      float ft_pid[6] = { 0.0008, 0.0, 0.0, 0.0, 0.0, 0.0 };
      uint8_t adj_sign = 0;
      uint8_t ILC_sign = 0;
      float max_dis = 1000.0;
      float max_ang = 20;
      ForceTorque ft = {0.0};
      ExaxisPos epos(0, 0, 0, 0);
      JointPos j1(80.765, -98.795, 106.548, -97.734, -89.999, 94.842);
      JointPos j2(43.067, -84.429, 92.620, -98.175, -90.011, 57.144);
      DescPose desc_p1(5.009, -547.463, 262.053, -179.999, -0.019, 75.923);
      DescPose desc_p2(-347.966, -547.463, 262.048, -180.000, -0.019, 75.923);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      double M[2] = { 2.0, 2.0 };
      double B[2] = { 15.0, 15.0 };
      double threshold[2] = {1.0, 1.0};
      double adjustCoeff[2] = {1.0, 0.8};
      double polishRadio = 0.0;
      int filter_Sign = 0;
      int posAdapt_sign = 1;
      int isNoBlock;
      ft.fz = -10.0;
      while(true)
      { 
        rtn = robot.FT_Control(1, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
        printf("FT_Control start rtn is %d\n", rtn);
        robot.MoveL(&j1, &desc_p1, 1, 0, 100, 100, 100, -1, 0, &epos, 0, 0, &offset_pos, 200.0, 0);
        robot.MoveL(&j2, &desc_p2, 1, 0, 100, 100, 100, -1, 0, &epos, 0, 0, &offset_pos, 200.0, 0);
        rtn = robot.FT_Control(0, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
        printf("FT_Control end rtn is %d\n", rtn);
      }
      robot.CloseRPC();
      return 0;
    }

Exploración helicoidal
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Exploración helicoidal
    * @param  [in] rcs Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    * @param  [in] dr Avance de radio por vuelta
    * @param  [in] ft Umbral de fuerza/par, fx,fy,fz,tx,ty,tz, rango [0~100]
    * @param  [in] max_t_ms Tiempo máximo de exploración, unidad ms
    * @param  [in] max_vel Velocidad lineal máxima, unidad mm/s
    * @param  [in] strategy Estrategia de tratamiento cuando no se detecta fuerza/par, 0-error; 1-advertencia, continuar el movimiento
    * @return  Código de error
    */   
    errno_t  FT_SpiralSearch(int rcs, float dr, float ft, float max_t_ms, float max_vel, int strategy = 0);  

Inserción rotativa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inserción rotativa
    * @param [in] rcs Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    * @param [in] angVelRot Velocidad angular de rotación, unidad deg/s
    * @param [in] ft  Umbral de fuerza/par, fx,fy,fz,tx,ty,tz, rango [0~100]
    * @param [in] max_angle Ángulo máximo de rotación, unidad deg
    * @param [in] orn Dirección de fuerza/par, 1-a lo largo del eje z, 2-alrededor del eje z
    * @param [in] max_angAcc Aceleración angular máxima de rotación, unidad deg/s^2, no se utiliza por ahora, por defecto 0
    * @param [in] rotorn  Dirección de rotación, 1-horario, 2-antihorario
    * @param [in] strategy Estrategia de tratamiento cuando no se detecta fuerza/par, 0-error; 1-advertencia, continuar el movimiento
    * @return Código de error
    */
    errno_t FT_RotInsertion(int rcs, float angVelRot, float ft, float max_angle, uint8_t orn, float max_angAcc, uint8_t rotorn, int strategy = 0);

Ejemplo de código de inserción rotativa del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestMove(void)
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
        JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0;
        float acc = 100.0;
        float ovl = 100.0;
        float oacc = 100.0;
        float blendT = 0.0;
        float blendR = 0.0;
        uint8_t flag = 0;
        uint8_t search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&j2, &desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, oacc, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&j3, &desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &j4, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, oacc, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&j3, &desc_pos3, tool, user, vel, acc, &epos, &j1, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        rtn = robot.MoveCart(&desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        printf("MoveCart errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, -1, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, -1, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&desc_pos3, tool, user, vel, acc, &epos, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, blendR, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        robot.CloseRPC();
        return 0;
    }

Inserción lineal
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Inserción lineal
    * @param  [in] rcs Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    * @param  [in] ft  Umbral de fuerza/par, fx,fy,fz,tx,ty,tz, rango [0~100]
    * @param  [in] lin_v Velocidad lineal, unidad mm/s
    * @param  [in] lin_a Aceleración lineal, unidad mm/s^2, no se utiliza por ahora
    * @param  [in] max_dis Distancia máxima de inserción, unidad mm
    * @param  [in] linorn  Dirección de inserción, 0-dirección negativa, 1-dirección positiva
    * @param  [in] strategy Estrategia de tratamiento cuando no se detecta fuerza/par, 0-error; 1-advertencia, continuar el movimiento
    * @return  Código de error
    */   
    errno_t  FT_LinInsertion(int rcs, float ft, float lin_v, float lin_a, float max_dis, uint8_t linorn, int strategy=0);    

Ejemplo de código de instrucciones como exploración helicoidal e inserción lineal
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTSearch(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t status = 1; 
      int sensor_num = 1; 
      float gain[6] = { 0.0001,0.0,0.0,0.0,0.0,0.0 }; 
      uint8_t adj_sign = 0; 
      uint8_t ILC_sign = 0; 
      float max_dis = 100.0; 
      float max_ang = 5.0; 
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      int rcs = 0; 
      float dr = 0.7; 
      float fFinish = 1.0; 
      float t = 60000.0;
      float vmax = 3.0;
      float force_goal = 20.0; 
      float lin_v = 0.0;
      float lin_a = 0.0;
      float disMax = 100.0;
      uint8_t linorn = 1; 
      float angVelRot = 2.0; 
      float forceInsertion = 1.0; 
      int angleMax = 45; 
      uint8_t orn = 1;
      float angAccmax = 0.0; 
      uint8_t rotorn = 1; 
      uint8_t select1[6] = { 0,0,1,1,1,0 }; 
      ft.fz = -10.0;
      robot.FT_Control(status, sensor_num, select1, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_SpiralSearch(rcs, dr, fFinish, t, vmax);
      printf("FT_SpiralSearch rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select1, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select2[6] = { 1,1,1,0,0,0 }; 
      gain[0] = 0.00005;
      ft.fz = -30.0;
      status = 1;
      robot.FT_Control(status, sensor_num, select2, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn);
      printf("FT_LinInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select2, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select3[6] = { 0,0,1,1,1,0 }; 
      ft.fz = -10.0;
      gain[0] = 0.0001;
      status = 1;
      robot.FT_Control(status, sensor_num, select3, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_RotInsertion(rcs, angVelRot, forceInsertion, angleMax, orn, angAccmax, rotorn);
      printf("FT_RotInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select3, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select4[6] = { 1,1,1,0,0,0 }; 
      ft.fz = -30.0;
      status = 1;
      robot.FT_Control(status, sensor_num, select4, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn);
      printf("FT_LinInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select4, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      robot.CloseRPC();
      return 0;
    }

Localización de superficie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Localización de superficie
    * @param  [in] rcs Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    * @param  [in] dir  Dirección de movimiento, 1-dirección positiva, 2-dirección negativa 
    * @param  [in] axis Eje de movimiento, 1-eje x, 2-eje y, 3-eje z
    * @param  [in] lin_v Velocidad lineal de exploración, unidad mm/s
    * @param  [in] lin_a Aceleración lineal de exploración, unidad mm/s^2, no se utiliza por ahora, por defecto 0
    * @param  [in] max_dis Distancia máxima de exploración, unidad mm
    * @param  [in] ft  Umbral de fuerza/par de finalización de la acción, fx,fy,fz,tx,ty,tz  
    * @param  [in] strategy Estrategia de tratamiento cuando no se detecta fuerza/par, 0-error; 1-advertencia, continuar el movimiento
    * @return  Código de error
    */   
    errno_t  FT_FindSurface(int rcs, uint8_t dir, uint8_t axis, float lin_v, float lin_a, float max_dis, float ft, int stragety = 0);   

Inicio del cálculo de la posición del plano intermedio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Inicio del cálculo de la posición del plano intermedio
    * @return  Código de error
    */   
    errno_t  FT_CalCenterStart();

Fin del cálculo de la posición del plano intermedio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Fin del cálculo de la posición del plano intermedio
    * @param  [out] pos Pose del plano intermedio
    * @return  Código de error
    */      
    errno_t  FT_CalCenterEnd(DescPose *pos);

Ejemplo de código de localización de superficie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSurface(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      int rcs = 0;
      uint8_t dir = 1;
      uint8_t axis = 1;
      float lin_v = 3.0;
      float lin_a = 0.0;
      float maxdis = 50.0;
      float ft_goal = 2.0;
      DescPose desc_pos(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose xcenter(0, 0, 0, 0, 0, 0);
      DescPose ycenter(0, 0, 0, 0, 0, 0);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      ft.fx = -2.0;
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.FT_CalCenterStart();
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.WaitMs(1000);
      dir = 2;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.FT_CalCenterEnd(&xcenter);
      printf("xcenter:%f,%f,%f,%f,%f,%f\n", xcenter.tran.x, xcenter.tran.y, xcenter.tran.z, xcenter.rpy.rx, xcenter.rpy.ry, xcenter.rpy.rz);
      robot.MoveCart(&xcenter, 9, 0, 60.0, 50.0, 50.0, -1.0, -1);
      robot.FT_CalCenterStart();
      dir = 1;
      axis = 2;
      lin_v = 6.0;
      maxdis = 150.0;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.WaitMs(1000);
      dir = 2;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.FT_CalCenterEnd(&ycenter);
      printf("ycenter:%f,%f,%f,%f,%f,%f\n", ycenter.tran.x, ycenter.tran.y, ycenter.tran.z, ycenter.rpy.rx, ycenter.rpy.ry, ycenter.rpy.rz);
      robot.MoveCart(&ycenter, 9, 0, 60.0, 50.0, 50.0, 0.0, -1);
      robot.CloseRPC();
      return 0;
    }

Inicio del control de compliance
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Inicio del control de compliance
    * @param  [in] p Coeficiente de ajuste de posición o coeficiente de compliance
    * @param  [in] force Umbral de fuerza de activación del compliance, unidad N
    * @return  Código de error
    */   
    errno_t  FT_ComplianceStart(float p, float force); 

Fin del control de compliance
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Fin del control de compliance
    * @return  Código de error
    */   
    errno_t  FT_ComplianceStop(); 

Ejemplo de código de control de compliance
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestCompliance(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t flag = 1;
      int sensor_id = 1;
      uint8_t select[6] = { 1,1,1,0,0,0 };
      float ft_pid[6] = { 0.0005,0.0,0.0,0.0,0.0,0.0 };
      uint8_t adj_sign = 0;
      uint8_t ILC_sign = 0;
      float max_dis = 100.0;
      float max_ang = 0.0;
      ForceTorque ft;
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      memset(&ft, 0, sizeof(ForceTorque));
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      ft.fx = -10.0;
      ft.fy = -10.0;
      ft.fz = -10.0;
      robot.FT_Control(flag, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      float p = 0.00005;
      float force = 30.0;
      rtn = robot.FT_ComplianceStart(p, force);
      printf("FT_ComplianceStart rtn is %d\n", rtn);
      int count = 15;
      while (count)
      {
        robot.MoveL(&j1, &desc_p1, 0, 0, 100.0, 180.0, 100.0, -1.0, &epos, 0, 1, &offset_pos);
        robot.MoveL(&j2, &desc_p2, 0, 0, 100.0, 180.0, 100.0, -1.0, &epos, 0, 0, &offset_pos);
        count -= 1;
      }
      robot.FT_ComplianceStop();
      printf("FT_ComplianceStop rtn is %d\n", rtn);
      flag = 0;
      robot.FT_Control(flag, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      robot.CloseRPC();
      return 0;
    }

Inicialización de la identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicialización de la identificación de carga
    * @return Código de error
    */
    errno_t LoadIdentifyDynFilterInit();

Inicialización de la identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicialización de la identificación de carga
    * @return Código de error
    */
    errno_t LoadIdentifyDynVarInit();

Programa principal de identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Programa principal de identificación de carga
    * @param [in] joint_torque Par de las articulaciones
    * @param [in] joint_pos Posición de las articulaciones
    * @param [in] t Período de muestreo
    * @return Código de error
    */
    errno_t LoadIdentifyMain(double joint_torque[6], double joint_pos[6], double t);

Obtener el resultado de la identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el resultado de la identificación de carga
    * @param [in] gain 
    * @param [out] weight Peso de la carga
    * @param [out] cog Centro de gravedad de la carga
    * @return Código de error
    */
    errno_t LoadIdentifyGetResult(double gain[12], double *weight, DescTran *cog);

Ejemplo de código de identificación de carga del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestIdentify(void)
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
      int retval = 0;
      retval = robot.LoadIdentifyDynFilterInit();
      printf("LoadIdentifyDynFilterInit retval is: %d \n", retval);
      retval = robot.LoadIdentifyDynVarInit();
      printf("LoadIdentifyDynVarInit retval is: %d \n", retval);
      JointPos posJ = {};
      DescPose posDec = {};
      float joint_toq[6] = { 0.0 };
      robot.GetActualJointPosDegree(0, &posJ);
      posJ.jPos[1] = posJ.jPos[1] + 10;
      robot.GetJointTorques(0, joint_toq);
      joint_toq[1] = joint_toq[1] + 2;
      double tmpTorque[6] = { 0.0 };
      for (int i = 0; i < 6; i++)
      {
        tmpTorque[i] = joint_toq[i];
      }
      retval = robot.LoadIdentifyMain(tmpTorque, posJ.jPos, 1);
      printf("LoadIdentifyMain retval is: %d \n", retval);
      double gain[12] = { 0,0.05,0,0,0,0,0,0.02,0,0,0,0 };
      double weight = 0;
      DescTran load_pos;
      memset(&load_pos, 0, sizeof(DescTran));
      retval = robot.LoadIdentifyGetResult(gain, &weight, &load_pos);
      printf("LoadIdentifyGetResult retval is: %d ; weight is %f cog is %f %f %f \n", retval, weight, load_pos.x, load_pos.y, load_pos.z);
      robot.CloseRPC();
      return 0;
    }

Arrastre asistido por sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.0-3.8.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief  Arrastre asistido por sensor de fuerza
    * @param  [in] status Estado de control, 0-desactivar; 1-activar
    * @param  [in] asaptiveFlag Indicador de activación adaptativa, 0-desactivar; 1-activar
    * @param  [in] interfereDragFlag Indicador de arrastre en zona de interferencia, 0-desactivar; 1-activar
    * @param  [in] ingularityConstraintsFlag Estrategia de singularidad, 0-evitar; 1-atravesar
    * @param  [in] forceCollisionFlag Indicador de detección de colisiones del robot durante el arrastre asistido; 0-desactivar; 1-activar
    * @param  [in] M Coeficiente de inercia
    * @param  [in] B Coeficiente de amortiguación
    * @param  [in] K Coeficiente de rigidez
    * @param  [in] F Umbral de fuerza de arrastre de seis dimensiones
    * @param  [in] Fmax Límite máximo de fuerza de arrastre
    * @param  [in] Vmax Límite máximo de velocidad articular
    * @return  Código de error
    */
    errno_t EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag, int ingularityConstraintsFlag, int forceCollisionFlag, std::vector<double> M, std::vector<double> B, std::vector<double> K, std::vector<double> F, double Fmax, double Vmax);

Obtener el estado del interruptor de arrastre del sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Obtener el estado del interruptor de arrastre del sensor de fuerza
     * @param [out] dragState Estado de control del arrastre asistido por sensor de fuerza, 0-desactivar; 1-activar
     * @param [out] sixDimensionalDragState Estado de control del arrastre asistido por fuerza de seis dimensiones, 0-desactivar; 1-activar
     * @return Código de error
     */
    errno_t GetForceAndTorqueDragState(int& dragState, int& sixDimensionalDragState);

Activación automática del sensor de fuerza tras el borrado de errores
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Activación automática del sensor de fuerza tras el borrado de errores
     * @param [in] status Estado de control, 0-desactivar; 1-activar
     * @return Código de error
     */
    errno_t SetForceSensorDragAutoFlag(int status);

Ejemplo de código de arrastre asistido por sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestEndForceDragCtrl(void)
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
         robot.SetForceSensorDragAutoFlag(1);
         vector <double> M = { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
         vector <double> B = { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
         vector <double> K = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
         vector <double> F = { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };
         robot.EndForceDragControl(1, 0, 0, 0, 1, M, B, K, F, 50, 100);
         robot.Sleep(5000);
         int dragState = 0;
         int sixDimensionalDragState = 0;
         robot.GetForceAndTorqueDragState(dragState, sixDimensionalDragState);
         printf("the drag state is %d %d \n", dragState, sixDimensionalDragState);
         robot.EndForceDragControl(0, 0, 0, 0, 1, M, B, K, F, 50, 100);
         robot.CloseRPC();
         return 0;
     }

Establecer el interruptor y los parámetros del arrastre mixto de fuerza de seis dimensiones e impedancia articular
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Establecer el interruptor y los parámetros del arrastre mixto de fuerza de seis dimensiones e impedancia articular
     * @param [in] status Estado de control, 0-desactivar; 1-activar
     * @param [in] impedanceFlag Indicador de activación de la impedancia, 0-desactivar; 1-activar
     * @param [in] lamdeDain Ganancia de arrastre
     * @param [in] KGain Ganancia de rigidez
     * @param [in] BGain Ganancia de amortiguación
     * @param [in] dragMaxTcpVel Límite máximo de velocidad lineal del extremo durante el arrastre
     * @param [in] dragMaxTcpOriVel Límite máximo de velocidad angular del extremo durante el arrastre
     * @return Código de error
     */
    errno_t ForceAndJointImpedanceStartStop(int status, int impedanceFlag, std::vector<double> lamdeDain, std::vector<double> KGain, std::vector<double> BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Ejemplo de código de arrastre mixto de fuerza de seis dimensiones e impedancia articular
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    int TestForceAndJointImpedance(void)
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
      robot.DragTeachSwitch(1);
      vector <double> lamdeDain = { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
      vector <double> KGain = { 0, 0, 0, 0, 0, 0 };
      vector <double> BGain = { 150, 150, 150, 5.0, 5.0, 1.0 };
      rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lamdeDain, KGain, BGain, 1000, 180);
      printf("ForceAndJointImpedanceStartStop rtn is %d\n", rtn);
      robot.Sleep(5000);
      robot.DragTeachSwitch(0);
      rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lamdeDain, KGain, BGain, 1000, 180);
      printf("ForceAndJointImpedanceStartStop rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Control de inicio/parada de la impedancia
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Control de inicio/parada de la impedancia
    * @param [in] status 0: desactivar; 1-activar
    * @param [in] workSpace 0-espacio de articulaciones; 1-espacio cartesiano
    * @param [in] forceThreshold Umbral de fuerza de activación (N)
    * @param [in] m Parámetros de masa
    * @param [in] b Parámetros de amortiguación
    * @param [in] k Parámetros de rigidez
    * @param [in] maxV Velocidad lineal máxima (mm/s)
    * @param [in] maxVA Aceleración lineal máxima (mm/s2)
    * @param [in] maxW Velocidad angular máxima (°/s)
    * @param [in] maxWA Aceleración angular máxima (°/s2)
    * @return Código de error
    */
    errno_t ImpedanceControlStartStop(int status, int workSpace, double forceThreshold[6], double m[6], double b[6], double k[6], double maxV, double maxVA, double maxW, double maxWA);

Ejemplo de código de control de inicio/parada de la impedancia del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    int TestImpedanceControl()
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      uint8_t ctrl[20];
      uint8_t state;
      int pressVlaue;
      int error;
      robot.CloseRPC();
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return 0;
      }
      robot.SetReConnectParam(true, 30000, 500);
      JointPos j1(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
      JointPos j2(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
      DescPose desc_pos1(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
      DescPose desc_pos2(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 200.0;
      float ovl = 100.0;
      float blendT = -1.0;
      float blendR = -1.0;
      uint8_t flag = 0;
      uint8_t search = 0;
      robot.SetSpeed(20);
      int company = 17;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      robot.FT_SetZero(1);
      robot.Sleep(1000);
      double forceThreshold[6] = { 30,30,30,5,5,5 };
      double m[6] = { 0.1,0.1,0.1,0.02,0.02,0.02 };
      double b[6] = { 1,1,1,0.08,0.08,0.08 };
      double k[6] = { 0,0,0,0,0,0 };
      rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
      printf("ImpedanceControlStartStop errcode:%d\n", rtn);
      rtn = robot.MoveL(&desc_pos1, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos1, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      printf("movel errcode:%d\n", rtn);
      robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);    
      robot.CloseRPC();
      return 0;
    }

Activar la función de compensación de par y el coeficiente de compensación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Activar la función de compensación de par y el coeficiente de compensación
    * @param [in] status Interruptor, 0-desactivar; 1-activar
    * @param [in] torqueCoeff Coeficiente de compensación de par J1-J6 [0-1]
    * @return Código de error
    */
    errno_t SetCoderCompenParams(int status, double torqueCoeff[6]);