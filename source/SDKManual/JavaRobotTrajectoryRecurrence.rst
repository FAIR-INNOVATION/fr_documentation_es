Reproducción de trayectoria del robot
=====================================

.. toctree:: 
    :maxdepth: 5

Establecer los parámetros de registro de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
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
    int SetTPDParam(int type, String name, int period_ms, int di_choose, int do_choose);

Iniciar el registro de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
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
    int SetTPDStart(int type, String name, int period_ms, int di_choose, int do_choose);

Detener el registro de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Detener el registro de trayectoria TPD
    * @return  Código de error
    */
    int SetWebTPDStop(); 

Eliminar el registro de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Eliminar el registro de trayectoria TPD
    * @param  [in] name  Nombre del archivo de trayectoria
    * @return  Código de error
    */   
    int SetTPDDelete(string name); 

Precarga de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Precarga de trayectoria
    * @param  [in] name  Nombre del archivo de trayectoria
    * @return  Código de error
    */      
    int LoadTPD(String name);

Reproducción de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Reproducción de trayectoria
    * @param  [in] name  Nombre del archivo de trayectoria
    * @param  [in] blend 0-sin suavizado, 1-suavizado
    * @param  [in] ovl  Porcentaje de escala de velocidad, rango [0~100]
    * @return  Código de error
    */
    int MoveTPD(String name, int blend, double ovl); 

Obtener la pose inicial de TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener la pose inicial de la trayectoria 
    * @param [in] name  Nombre del archivo de trayectoria, sin sufijo de archivo
    * @param [out] desc_pose Pose inicial de la trayectoria obtenida
    * @return Código de error 
    */ 
    int GetTPDStartPose(String name, DescPose desc_pose); 

Ejemplo de código de registro de trayectoria TPD del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestTPD(Robot robot)
    {
        int type = 1;
        String name = "tpd2025";
        int period_ms = 4;
        int di_choose = 0;
        int do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        robot.Sleep(10000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        double ovl = 100.0;
        int blend = 0;

        DescPose start_pose =new DescPose() {};

        int rtn = robot.LoadTPD(name);
        System.out.println("LoadTPD rtn is:"+ rtn);

        robot.GetTPDStartPose(name, start_pose);
        robot.MoveCart(start_pose, 0, 0, 100, 100, ovl, -1, -1);
        robot.Sleep(1000);

        rtn = robot.MoveTPD(name, blend, ovl);
        System.out.println("MoveTPD rtn is: "+ rtn);
        robot.Sleep(5000);

        robot.SetTPDDelete(name);
        return 0;
    }

Preprocesamiento de trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Preprocesamiento de archivo de trayectoria externo 
    * @param [in] name Nombre del archivo de trayectoria  
    * @param [in] ovl Porcentaje de escala de velocidad, rango [0~100]
    * @param [in] opt 1-punto de control, por defecto 1 
    * @return Código de error 
    */ 
    int LoadTrajectoryJ(String name, double ovl, int opt); 

Reproducción de trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Reproducción de archivo de trayectoria externo  
    * @return Código de error 
    */
    int MoveTrajectoryJ();

Obtener la pose inicial de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener la pose inicial de la trayectoria 
    * @param [in] name Nombre del archivo de trayectoria  
    * @param [out] desc_pose Pose inicial de la trayectoria obtenida
    * @return Código de error 
    */ 
    int GetTrajectoryStartPose(String name, DescPose desc_pose);

Obtener el número de puntos de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el número de puntos de la trayectoria
    * @return  Código de error
    */
    public int GetTrajectoryPointNum(int pnum)

Establecer la velocidad durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /*
    * @brief  Establecer la velocidad durante la ejecución de la trayectoria
    * @param  ovl Porcentaje de velocidad
    * @param  mode Modo; 0-modo de reducción de velocidad; 1-cambio directo
    * @return  Código de error
    */
    public int SetTrajectoryJSpeed(double ovl, int mode)

Establecer la fuerza y el par durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer la fuerza y el par durante la ejecución de la trayectoria
    * @param  [in] ft Fuerza y par en tres direcciones, unidades N y Nm
    * @return  Código de error
    */
    public int SetTrajectoryJForceTorque(ForceTorque ft)

Establecer la fuerza en la dirección x durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer la fuerza en la dirección x durante la ejecución de la trayectoria  
    * @param [in] fx Fuerza en la dirección x, unidad N
    * @return Código de error 
    */
    int SetTrajectoryJForceFx(double fx);

Establecer la fuerza en la dirección y durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer la fuerza en la dirección y durante la ejecución de la trayectoria
    * @param [in] fy Fuerza en la dirección y, unidad N
    * @return Código de error 
    */
    int SetTrajectoryJForceFy(double fy);

Establecer la fuerza en la dirección z durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer la fuerza en la dirección z durante la ejecución de la trayectoria  
    * @param [in] fz  Fuerza en la dirección z, unidad N
    * @return Código de error 
    */
    int SetTrajectoryJForceFz(double fz);

Establecer el par alrededor del eje x durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el par alrededor del eje x durante la ejecución de la trayectoria  
    * @param [in] tx Par alrededor del eje x, unidad Nm
    * @return Código de error 
    */
    int SetTrajectoryJTorqueTx(double tx);

Establecer el par alrededor del eje y durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el par alrededor del eje y durante la ejecución de la trayectoria  
    * @param [in] ty Par alrededor del eje y, unidad Nm
    * @return Código de error 
    */
    int SetTrajectoryJTorqueTy(double ty);

Establecer el par alrededor del eje z durante la ejecución de la trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el par alrededor del eje z durante la ejecución de la trayectoria  
    * @param [in] tz Par alrededor del eje z, unidad Nm
    * @return Código de error 
    */
    int SetTrajectoryJTorqueTz(double tz);

Subir archivo de trayectoria J
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Subir archivo de trayectoria J  
    * @param [in] filePath Nombre de ruta completo del archivo de trayectoria a subir   C://test/testJ.txt
    * @return Código de error 
    */
    int TrajectoryJUpLoad(String filePath);

Eliminar archivo de trayectoria J
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Eliminar archivo de trayectoria J  
    * @param [in] fileName Nombre del archivo testJ.txt
    * @return Código de error 
    */
    int TrajectoryJDelete(String fileName);

Ejemplo de código de reproducción del archivo de trayectoria J del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestTraj(Robot robot)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/horse.txt");
        System.out.println("Upload TrajectoryJ A :"+ rtn);

        String traj_file_name = "horse.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        System.out.println("LoadTrajectoryJ:"+traj_file_name+", rtn is:"+ rtn);

        DescPose traj_start_pose=new DescPose(0,0,0,0,0,0);
        rtn = robot.GetTrajectoryStartPose(traj_file_name, traj_start_pose);

        robot.Sleep(1000);


        ExaxisPos epos=new ExaxisPos(0,0,0,0);
        DescPose po=new DescPose(0,0,0,0,0,0);
        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(traj_num);

        rtn = robot.SetTrajectoryJSpeed(50.0);
        System.out.println("SetTrajectoryJSpeed is:"+ rtn);

        ForceTorque traj_force=new ForceTorque(0,0,0,0,0,0);
        traj_force.fx = 10;
        rtn = robot.SetTrajectoryJForceTorque(traj_force);
        System.out.println("SetTrajectoryJForceTorque rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJForceFx(10.0);
        System.out.println("SetTrajectoryJForceFx rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJForceFy(0.0);
        System.out.println("SetTrajectoryJForceFy rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJForceFz(0.0);
        System.out.println("SetTrajectoryJForceFz rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJTorqueTx(10.0);
        System.out.println("SetTrajectoryJTorqueTx rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJTorqueTy(10.0);
        System.out.println("SetTrajectoryJTorqueTy rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJTorqueTz(10.0);
        System.out.println("SetTrajectoryJTorqueTz rtn is:"+ rtn);

        rtn = robot.MoveTrajectoryJ();
        System.out.println("MoveTrajectoryJ rtn is: "+ rtn);

        return 0;
    }

Ejemplo de código de establecimiento de la velocidad durante la ejecución de la trayectoria del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public int TestSetTrajectoryJSpeed(Robot robot) {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        int rtn;

        robot.SetReconnectParam(true, 30000, 500);
        rtn = robot.TrajectoryJUpLoad("D://zUP/horse.txt");
        System.out.printf("Upload TrajectoryJ A %d%n", rtn);
        String trajFileName = "horse.txt";
        rtn = robot.LoadTrajectoryJ(trajFileName, 100, 1);
        System.out.printf("LoadTrajectoryJ %s, rtn is: %d%n", trajFileName, rtn);
        DescPose trajStartPose = new DescPose();
        rtn = robot.GetTrajectoryStartPose(trajFileName, trajStartPose);
        System.out.printf("GetTrajectoryStartPose is: %d%n", rtn);
        System.out.printf("desc_pos:%f,%f,%f,%f,%f,%f%n", trajStartPose.tran.x, trajStartPose.tran.y, trajStartPose.tran.z, trajStartPose.rpy.rx, trajStartPose.rpy.ry, trajStartPose.rpy.rz);
        robot.Sleep(1000);
        robot.SetSpeed(50);
        robot.MoveCart(trajStartPose, 0, 0, 100, 100, 100, -1, -1);
        rtn = robot.GetTrajectoryPointNum(0);
        pkg = robot.GetRobotRealTimeState();
        int trajNum = pkg.trajectory_pnum;
        System.out.printf("GetTrajectoryPointNum rtn is: %d, traj num is: %d%n", rtn, trajNum);

        rtn = robot.MoveTrajectoryJ();
        System.out.printf("MoveTrajectoryJ rtn is: %d%n", rtn);

        robot.Sleep(1000);

        pkg = robot.GetRobotRealTimeState();
        int trajspeedMode = 1;
        while (pkg.motion_done == 0)
        {
            pkg = robot.GetRobotRealTimeState();

            rtn = robot.SetTrajectoryJSpeed(10.0, trajspeedMode);
            System.out.printf("SetTrajectoryJSpeed is: %d%n", rtn);

            robot.Sleep(1000);

            rtn = robot.SetTrajectoryJSpeed(80.0, trajspeedMode);
            System.out.printf("SetTrajectoryJSpeed is: %d%n", rtn);

            robot.Sleep(1000);
        }

        return 0;
    }

Preprocesamiento de trayectoria (previsión de trayectoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /** 
    * @brief Preprocesamiento de trayectoria (previsión de trayectoria) 
    * @param [in] name  Nombre del archivo de trayectoria
    * @param [in] mode Modo de muestreo, 0-no realizar muestreo; 1-muestreo con intervalo de datos igual; 2-muestreo con límite de error igual
    * @param [in] errorLim Límite de error, efectivo al usar ajuste de línea recta
    * @param [in] type Modo de suavizado, 0-suavizado de Bézier
    * @param [in] precision Precisión de suavizado, efectiva al usar suavizado de Bézier
    * @param [in] vamx Velocidad máxima configurada, mm/s
    * @param [in] amax Aceleración máxima configurada, mm/s2
    * @param [in] jmax Sobreaceleración (jerk) máxima configurada, mm/s3
    * @return Código de error 
    */ 
    int LoadTrajectoryLA(String name, int mode, double errorLim, int type, double precision, double vamx, double amax, double jmax); 

Reproducción de trayectoria (previsión de trayectoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /** 
    * @brief Reproducción de trayectoria (previsión de trayectoria)  
    * @return Código de error 
    */
    int MoveTrajectoryLA();

Ejemplo de código de reproducción de trayectoria (previsión de trayectoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLoadTrajLA(Robot robot)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt");

        String traj_file_name = "/fruser/traj/traj.txt";
        rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 100, 200, 1000);

        DescPose traj_start_pose=new DescPose(0,0,0,0,0,0);
        rtn = robot.GetTrajectoryStartPose(traj_file_name, traj_start_pose);

        robot.Sleep(1000);
        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        rtn = robot.MoveTrajectoryLA();

        robot.CloseRPC();
        return 0;
    }

Moverse al punto de inicio del registro de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Moverse al punto de inicio del registro de trayectoria TPD
    * @param name Nombre del archivo de trayectoria
    * @param moveType Tipo de movimiento; 0-PTP; 1-LIN
    * @param ovl Porcentaje de escala de velocidad, rango [0~100]
    * @return Código de error
    */
    public int MoveToTPDStart(string name, int moveType, double ovl)

Ejemplo de código SDK de movimiento al punto de inicio del registro de trayectoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testTPDmove (Robot robot)
    {
        int rtn = 0;
        int type = 1;
        String name = "tpd2025";
        int period_ms = 4;
        int di_choose = 0;
        int do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        robot.Sleep(3000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        robot.Sleep(1000);
        double ovl = 100.0;
        int blend = 0;
        DescPose start_pose = new DescPose();
        rtn = robot.LoadTPD(name);
        System.out.printf("LoadTPD rtn is: %d\n", rtn);

        robot.GetTPDStartPose(name, start_pose);
        System.out.printf("start pose, xyz is: %f %f %f. rpy is: %f %f %f \n", start_pose.tran.x, start_pose.tran.y, start_pose.tran.z, start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
        //robot.MoveCart(&start_pose, 0, 0, 100, 100, ovl, -1, -1);
        //robot.Sleep(1000);

        rtn = robot.MoveToTPDStart(name, 0, 100);
        System.out.printf("MoveToTPDStart rtn is: %d\n", rtn);

        rtn = robot.MoveTPD(name, blend, ovl);
        System.out.printf("MoveTPD rtn is: %d\n", rtn);

        robot.Sleep(5000);

        robot.SetTPDDelete(name);

        return ;
    }