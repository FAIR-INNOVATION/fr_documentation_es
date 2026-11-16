Reproducción de trayectoria del robot
============================================

.. toctree:: 
    :maxdepth: 5

Establecer los parámetros de registro de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer los parámetros de registro de trayectoria TPD
    * @param  [in] type  Tipo de dato de registro, 1-posición de articulaciones
    * @param  [in] name  Nombre del archivo de trayectoria
    * @param  [in] period_ms  Período de muestreo de datos, valor fijo 2ms o 4ms u 8ms
    * @param  [in] di_choose  Selección de DI, bit0~bit7 corresponden a DI0~DI7 de la caja de control, bit8~bit9 corresponden a DI0~DI1 del extremo, 0-no seleccionar, 1-seleccionar
    * @param  [in] do_choose  Selección de DO, bit0~bit7 corresponden a DO0~DO7 de la caja de control, bit8~bit9 corresponden a DO0~DO1 del extremo, 0-no seleccionar, 1-seleccionar
    * @return  Código de error
    */
    errno_t  SetTPDParam(int type, char name[30], int period_ms, uint16_t di_choose, uint16_t do_choose);

Iniciar el registro de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Iniciar el registro de trayectoria TPD
    * @param  [in] type  Tipo de dato de registro, 1-posición de articulaciones
    * @param  [in] name  Nombre del archivo de trayectoria
    * @param  [in] period_ms  Período de muestreo de datos, valor fijo 2ms o 4ms u 8ms
    * @param  [in] di_choose  Selección de DI, bit0~bit7 corresponden a DI0~DI7 de la caja de control, bit8~bit9 corresponden a DI0~DI1 del extremo, 0-no seleccionar, 1-seleccionar
    * @param  [in] do_choose  Selección de DO, bit0~bit7 corresponden a DO0~DO7 de la caja de control, bit8~bit9 corresponden a DO0~DO1 del extremo, 0-no seleccionar, 1-seleccionar
    * @return  Código de error
    */
    errno_t  SetTPDStart(int type, char name[30], int period_ms, uint16_t di_choose, uint16_t do_choose); 

Detener el registro de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Detener el registro de trayectoria TPD
    * @return  Código de error
    */
    errno_t  SetWebTPDStop();

Eliminar el registro de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Eliminar el registro de trayectoria TPD
    * @param  [in] name  Nombre del archivo de trayectoria
    * @return  Código de error
    */   
    errno_t  SetTPDDelete(char name[30]);

Precarga de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Precarga de trayectoria TPD
    * @param  [in] name  Nombre del archivo de trayectoria
    * @return  Código de error
    */      
    errno_t  LoadTPD(char name[30]);

Reproducción de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Reproducción de trayectoria TPD
    * @param  [in] name  Nombre del archivo de trayectoria
    * @param  [in] blend 0-sin suavizado, 1-suavizado
    * @param  [in] ovl  Porcentaje de escala de velocidad, rango [0~100]
    * @return  Código de error
    */
    errno_t  MoveTPD(char name[30], uint8_t blend, float ovl);

Obtener la pose inicial de TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la pose inicial de TPD
    * @param [in] name Nombre del archivo TPD, sin sufijo de archivo
    * @return Código de error
    */   
    errno_t GetTPDStartPose(char name[30], DescPose *desc_pose);

Moverse al punto de inicio del registro de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Moverse al punto de inicio del registro de trayectoria TPD
    * @param [in] name Nombre del archivo de trayectoria
    * @param [in] moveType Tipo de movimiento; 0-PTP; 1-LIN
    * @param [in] ovl Porcentaje de escala de velocidad, rango [0~100]
    * @return Código de error
    */
    errno_t MoveToTPDStart(char name[30], uint8_t moveType, float ovl);
    
Ejemplo de código de registro de trayectoria TPD del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestTPD(void)
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
    int type = 1;
    char name[30] = "tpd2025";
    int period_ms = 4;
    uint16_t di_choose = 0;
    uint16_t do_choose = 0;
    robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);
    robot.Mode(1);
    robot.Sleep(1000);
    robot.DragTeachSwitch(1);
    robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
    robot.Sleep(3000);
    robot.SetWebTPDStop();
    robot.DragTeachSwitch(0);
    robot.Sleep(1000);
    float ovl = 100.0;
    uint8_t blend = 0;
    DescPose start_pose = {};
    rtn = robot.LoadTPD(name);
    printf("LoadTPD rtn is: %d\n", rtn);
    robot.GetTPDStartPose(name, &start_pose);
    printf("start pose, xyz is: %f %f %f. rpy is: %f %f %f \n", start_pose.tran.x, start_pose.tran.y, start_pose.tran.z, start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
    rtn = robot.MoveToTPDStart(name, 0, 100);
    printf("MoveToTPDStart rtn is: %d\n", rtn);
    rtn = robot.MoveTPD(name, blend, ovl);
    printf("MoveTPD rtn is: %d\n", rtn);
    std::this_thread::sleep_for(std::chrono::milliseconds(5000));
    robot.SetTPDDelete(name);
    robot.CloseRPC();
    return 0;
    }

Preprocesamiento de trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Preprocesamiento de trayectoria
    * @param [in] name Nombre del archivo de trayectoria
    * @param [in] ovl Porcentaje de escala de velocidad, rango [0~100]
    * @param [in] opt 1-punto de control, por defecto 1
    * @return Código de error
    */   
    errno_t LoadTrajectoryJ(char name[30], float ovl, int opt);

Reproducción de trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Reproducción de trayectoria
    * @return Código de error
    */   
    errno_t MoveTrajectoryJ();

Obtener la pose inicial de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la pose inicial de la trayectoria
    * @param [in] name Nombre del archivo de trayectoria
    * @return Código de error
    */   
    errno_t GetTrajectoryStartPose(char name[30], DescPose *desc_pose);

Obtener el número de puntos de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el número de puntos de la trayectoria
    * @return Código de error
    */   
    errno_t GetTrajectoryPointNum(int *pnum);

Establecer la velocidad durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la velocidad durante la ejecución de la trayectoria
    * @param [in] ovl Porcentaje de velocidad [0-100.0]
    * @param [in] mode Modo; 0-modo de reducción de velocidad; 1-cambio directo
    * @return Código de error
    */
    errno_t SetTrajectoryJSpeed(float ovl, int mode = 0);

Ejemplo de código para establecer la velocidad durante la ejecución de la trayectoria del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSetTrajectoryJSpeed() 
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
        
        rtn = robot.TrajectoryJUpLoad("D://zUP/horse.txt");
        printf("Upload TrajectoryJ A %d\n", rtn);
        char traj_file_name[90] = "horse.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        printf("LoadTrajectoryJ %s, rtn is: %d\n", traj_file_name, rtn);
        DescPose traj_start_pose;
        memset(&traj_start_pose, 0, sizeof(DescPose));
        rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
        printf("GetTrajectoryStartPose is: %d\n", rtn);
        printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
        std::this_thread::sleep_for(std::chrono::seconds(1));
        robot.SetSpeed(50);
        robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(&traj_num);
        printf("GetTrajectoryStartPose rtn is: %d, traj num is: %d\n", rtn, traj_num);
        rtn = robot.MoveTrajectoryJ();
        printf("MoveTrajectoryJ rtn is: %d\n", rtn);
        robot.Sleep(1000);
        robot.GetRobotRealTimeState(&pkg);
        int trajspeedMode = 1;
        while (pkg.motion_done == 0)
        {
            robot.GetRobotRealTimeState(&pkg);
            rtn = robot.SetTrajectoryJSpeed(10.0, trajspeedMode);
            printf("SetTrajectoryJSpeed is: %d\n", rtn);
            robot.Sleep(1000);
            rtn = robot.SetTrajectoryJSpeed(80.0, trajspeedMode);
            printf("SetTrajectoryJSpeed is: %d\n", rtn);
            robot.Sleep(1000);
        }
        robot.CloseRPC();
        robot.Sleep(1000000);
        return 0;
    }

Establecer la fuerza y el par durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la fuerza y el par durante la ejecución de la trayectoria
    * @param [in] ft Fuerza y par en tres direcciones, unidades N y Nm
    * @return Código de error
    */   
    errno_t SetTrajectoryJForceTorque(ForceTorque *ft);

Establecer la fuerza en la dirección x durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la fuerza en la dirección x durante la ejecución de la trayectoria
    * @param [in] fx Fuerza en la dirección x, unidad N
    * @return Código de error
    */   
    errno_t SetTrajectoryJForceFx(double fx);

Establecer la fuerza en la dirección y durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la fuerza en la dirección y durante la ejecución de la trayectoria
    * @param [in] fy Fuerza en la dirección y, unidad N
    * @return Código de error
    */   
    errno_t SetTrajectoryJForceFy(double fy);

Establecer la fuerza en la dirección z durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la fuerza en la dirección z durante la ejecución de la trayectoria
    * @param [in] fz Fuerza en la dirección z, unidad N
    * @return Código de error
    */   
    errno_t SetTrajectoryJForceFz(double fz);

Establecer el par alrededor del eje x durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el par alrededor del eje x durante la ejecución de la trayectoria
    * @param [in] tx Par alrededor del eje x, unidad Nm
    * @return Código de error
    */   
    errno_t SetTrajectoryJTorqueTx(double tx);

Establecer el par alrededor del eje y durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el par alrededor del eje y durante la ejecución de la trayectoria
    * @param [in] ty Par alrededor del eje y, unidad Nm
    * @return Código de error
    */   
    errno_t SetTrajectoryJTorqueTy(double ty);

Establecer el par alrededor del eje z durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el par alrededor del eje z durante la ejecución de la trayectoria
    * @param [in] tz Par alrededor del eje z, unidad Nm
    * @return Código de error
    */   
    errno_t SetTrajectoryJTorqueTz(double tz);

Subir el archivo de trayectoria J
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
	 * @brief Subir el archivo de trayectoria J
	 * @param [in] filePath Nombre de ruta completo del archivo de trayectoria a subir   C://test/testJ.txt
	 * @return Código de error
	 */
	errno_t TrajectoryJUpLoad(const std::string& filePath);

Eliminar el archivo de trayectoria J
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
	 * @brief Eliminar el archivo de trayectoria J
	 * @param [in] fileName Nombre del archivo testJ.txt
	 * @return Código de error
	 */
	errno_t TrajectoryJDelete(const std::string& fileName);

Ejemplo de código de reproducción del archivo de trayectoria J del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestTraj(void)
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
      rtn = robot.TrajectoryJUpLoad("D://zUP/traj1.txt");
      printf("Upload TrajectoryJ A %d\n", rtn);
      char traj_file_name[30] = "/fruser/traj/traj1.txt";
      rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
      printf("LoadTrajectoryJ %s, rtn is: %d\n", traj_file_name, rtn);
      DescPose traj_start_pose;
      memset(&traj_start_pose, 0, sizeof(DescPose));
      rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
      printf("GetTrajectoryStartPose is: %d\n", rtn);
      printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
      std::this_thread::sleep_for(std::chrono::seconds(1));
      robot.SetSpeed(50);
      robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
      int traj_num = 0;
      rtn = robot.GetTrajectoryPointNum(&traj_num);
      printf("GetTrajectoryStartPose rtn is: %d, traj num is: %d\n", rtn, traj_num);
      rtn = robot.SetTrajectoryJSpeed(50.0);
      printf("SetTrajectoryJSpeed is: %d\n", rtn);
      ForceTorque traj_force;
      memset(&traj_force, 0, sizeof(ForceTorque));
      traj_force.fx = 10;
      rtn = robot.SetTrajectoryJForceTorque(&traj_force);
      printf("SetTrajectoryJForceTorque rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFx(10.0);
      printf("SetTrajectoryJForceFx rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFy(0.0);
      printf("SetTrajectoryJForceFy rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFz(0.0);
      printf("SetTrajectoryJForceFz rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTx(10.0);
      printf("SetTrajectoryJTorqueTx rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTy(10.0);
      printf("SetTrajectoryJTorqueTy rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTz(10.0);
      printf("SetTrajectoryJTorqueTz rtn is: %d\n", rtn);
      rtn = robot.MoveTrajectoryJ();
      printf("MoveTrajectoryJ rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Preprocesamiento de trayectoria (previsión de trayectoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Preprocesamiento de trayectoria (previsión de trayectoria)
    * @param [in] name Nombre del archivo de trayectoria
    * @param [in] mode Modo de muestreo, 0-no realizar muestreo; 1-muestreo con intervalo de datos igual; 2-muestreo con límite de error igual
    * @param [in] errorLim Límite de error, efectivo al usar ajuste de línea recta
    * @param [in] type Modo de suavizado, 0-suavizado de Bézier
    * @param [in] precision Precisión de suavizado, efectiva al usar suavizado de Bézier
    * @param [in] vamx Velocidad máxima configurada, mm/s
    * @param [in] amax Aceleración máxima configurada, mm/s2
    * @param [in] jmax Sobreaceleración (jerk) máxima configurada, mm/s3
    * @param [in] flag Interruptor de activación de previsión de velocidad constante, 0-no activar; 1-activar
    * @return Código de error
    */
    errno_t LoadTrajectoryLA(char name[30], int mode, double errorLim, int type, double precision, double vamx, double amax, double jmax, int flag = 0);

Reproducción de trayectoria (previsión de trayectoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Reproducción de trayectoria (previsión de trayectoria)
    * @return  Código de error
    */
    errno_t MoveTrajectoryLA();

Ejemplo de código de reproducción de trayectoria (previsión de trayectoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestLoadTrajLA(void)
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
      rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt");
      printf("Upload TrajectoryJ A %d\n", rtn);
      char traj_file_name[30] = "/fruser/traj/traj.txt";
      rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 100, 200, 1000);
      printf("LoadTrajectoryLA %s, rtn is: %d\n", traj_file_name, rtn);
      DescPose traj_start_pose;
      memset(&traj_start_pose, 0, sizeof(DescPose));
      rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
      printf("GetTrajectoryStartPose is: %d\n", rtn);
      printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
      std::this_thread::sleep_for(std::chrono::seconds(1));
      robot.SetSpeed(50);
      robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
      rtn = robot.MoveTrajectoryLA();
      printf("MoveTrajectoryLA rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }