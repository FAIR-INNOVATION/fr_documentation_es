Reproducción de trayectorias del robot
======================================

.. toctree:: 
    :maxdepth: 5

Establecer los parámetros de registro de trayectoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer los parámetros de registro de trayectoria TPD
    * @param  [in] type  Tipo de datos de registro, 1-posición de articulaciones
    * @param  [in] name  Nombre del archivo de trayectoria
    * @param  [in] period_ms  Período de muestreo de datos, valor fijo 2 ms, 4 ms u 8 ms
    * @param  [in] di_choose  Selección de DI, bit0~bit7 corresponden a DI0~DI7 del armario de control, bit8~bit9 corresponden a DI0~DI1 del extremo; 0-no seleccionar, 1-seleccionar
    * @param  [in] do_choose  Selección de DO, bit0~bit7 corresponden a DO0~DO7 del armario de control, bit8~bit9 corresponden a DO0~DO1 del extremo; 0-no seleccionar, 1-seleccionar
    * @return  Código de error
    */
    int SetTPDParam(int type, string name, int period_ms, UInt16 di_choose, UInt16 do_choose);

Iniciar el registro de trayectoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Iniciar el registro de trayectoria TPD
    * @param  [in] type  Tipo de datos de registro, 1-posición de articulaciones
    * @param  [in] name  Nombre del archivo de trayectoria
    * @param  [in] period_ms  Período de muestreo de datos, valor fijo 2 ms, 4 ms u 8 ms
    * @param  [in] di_choose  Selección de DI, bit0~bit7 corresponden a DI0~DI7 del armario de control, bit8~bit9 corresponden a DI0~DI1 del extremo; 0-no seleccionar, 1-seleccionar
    * @param  [in] do_choose  Selección de DO, bit0~bit7 corresponden a DO0~DO7 del armario de control, bit8~bit9 corresponden a DO0~DO1 del extremo; 0-no seleccionar, 1-seleccionar
    * @return  Código de error
    */
    int SetTPDStart(int type, string name, int period_ms, UInt16 di_choose, UInt16 do_choose); 

Detener el registro de trayectoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Detener el registro de trayectoria TPD
    * @return  Código de error
    */
    int SetWebTPDStop(); 

Eliminar el registro de trayectoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Eliminar el registro de trayectoria TPD
    * @param  [in] name  Nombre del archivo de trayectoria
    * @return  Código de error
    */   
    int SetTPDDelete(string name); 

Precarga de trayectoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Precarga de trayectoria
    * @param  [in] name  Nombre del archivo de trayectoria
    * @return  Código de error
    */      
    int LoadTPD(string name);

Obtener la pose inicial de la trayectoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la pose inicial de la trayectoria 
    * @param [in] name  Nombre del archivo de trayectoria
    * @param [out] desc_pose Pose inicial de la trayectoria 
    * @return Código de error 
    */ 
    int GetTPDStartPose(string name, ref DescPose desc_pose); 

Reproducción de trayectoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Reproducción de trayectoria
    * @param  [in] name  Nombre del archivo de trayectoria
    * @param  [in] blend 0-sin suavizado, 1-suavizado
    * @param  [in] ovl  Porcentaje de escala de velocidad, rango [0~100]
    * @return  Código de error
    */
    int MoveTPD(string name, byte blend, float ovl); 

Ejemplo de código de registro de trayectoria TPD del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnTPDMove_Click(object sender, EventArgs e)
    {
        int type = 1;
        string name = "tpd2025";
        int period_ms = 4;
        ushort di_choose = 0;
        ushort do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        Thread.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        Thread.Sleep(10000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        float ovl = 100.0f;
        byte blend = 0;

        DescPose start_pose = new DescPose();

        int rtn = robot.LoadTPD(name);
        Console.WriteLine("LoadTPD rtn is: {0}\n", rtn);

        robot.GetTPDStartPose(name, ref start_pose);
        Console.WriteLine("start pose, xyz is: {0} {1} {2}. rpy is: {3} {4} {5} \n",
            start_pose.tran.x, start_pose.tran.y, start_pose.tran.z,
            start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
        robot.MoveCart(start_pose, 0, 0, 100, 100, ovl, -1, -1);
        Thread.Sleep(1000);

        rtn = robot.MoveTPD(name, blend, ovl);
        Console.WriteLine("MoveTPD rtn is: {0}\n", rtn);
        Thread.Sleep(5000);

        robot.SetTPDDelete(name);
    }

Preprocesamiento del archivo de trayectoria externo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Preprocesamiento del archivo de trayectoria externo 
    * @param [in] name Nombre del archivo de trayectoria  
    * @param [in] ovl Porcentaje de escala de velocidad, rango [0~100] 
    * @param [in] opt 1-punto de control, por defecto 1 
    * @return Código de error 
    */ 
    int LoadTrajectoryJ(string name, float ovl, int opt); 

Reproducción de trayectoria del archivo de trayectoria externo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Reproducción de trayectoria del archivo de trayectoria externo  
    * @return Código de error 
    */
    int MoveTrajectoryJ();

Obtener la posición inicial de la trayectoria del archivo de trayectoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la posición inicial de la trayectoria del archivo de trayectoria 
    * @param [in] name Nombre del archivo de trayectoria  
    * @param [out] desc_pose Pose inicial de la trayectoria  
    * @return Código de error 
    */ 
    int GetTrajectoryStartPose(string name, ref DescPose desc_pose); 

Obtener el número de puntos de trayectoria del archivo de trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener el número de puntos de trayectoria   
    * @param [out] pnum Número de puntos de trayectoria  
    * @return Código de error 
    */  
    int GetTrajectoryPointNum(ref int pnum);

Establecer la velocidad de ejecución de la trayectoria del archivo de trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer la velocidad durante la ejecución de la trayectoria
    * @param  [in] ovl Porcentaje de velocidad
    * @param  [in] mode 0-modo de reducción de velocidad, 1-conmutación directa
    * @return  Código de error
    */
    public int SetTrajectoryJSpeed(double ovl, int mode = 0)

Ejemplo de código de configuración de la velocidad durante la ejecución de la trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int RunTrajectoryJ(string localFilePath = "D://zUP/horse.txt", string remoteFilePath = "horse.txt",
    int initialSpeedPercent = 50, int trajSpeedMode = 1)
    {
        int rtn;

        // 1. Cargar el archivo de trayectoria J
        rtn = robot.TrajectoryJUpLoad(localFilePath);
        if (rtn != 0)
        {
            Console.WriteLine($"Upload TrajectoryJ failed: {rtn}");
            return rtn;
        }
        Console.WriteLine($"Upload TrajectoryJ success: {localFilePath}");

        // 2. Cargar el archivo de trayectoria
        rtn = robot.LoadTrajectoryJ(remoteFilePath, 100, 1);
        if (rtn != 0)
        {
            Console.WriteLine($"LoadTrajectoryJ failed: {rtn}");
            return rtn;
        }
        Console.WriteLine($"LoadTrajectoryJ success: {remoteFilePath}");

        // 3. Obtener la pose inicial de la trayectoria
        DescPose trajStartPose = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.GetTrajectoryStartPose(remoteFilePath, ref trajStartPose);
        if (rtn != 0)
        {
            Console.WriteLine($"GetTrajectoryStartPose failed: {rtn}");
            return rtn;
        }
        Console.WriteLine($"Trajectory start pose: ({trajStartPose.tran.x}, {trajStartPose.tran.y}, {trajStartPose.tran.z}, " +
                            $"{trajStartPose.rpy.rx}, {trajStartPose.rpy.ry}, {trajStartPose.rpy.rz})");

        // 4. Moverse al punto inicial de la trayectoria (PTP en el espacio cartesiano)
        robot.SetSpeed(initialSpeedPercent);
        rtn = robot.MoveCart(trajStartPose, 0, 0, 100, 100, 100, -1, -1);
        if (rtn != 0)
        {
            Console.WriteLine($"MoveCart to start pose failed: {rtn}");
            return rtn;
        }

        // 5. Obtener el número de puntos de trayectoria (opcional, solo para visualización)
        int trajPointNum = 0;
        rtn = robot.GetTrajectoryPointNum(ref trajPointNum);
        if (rtn != 0)
        {
            Console.WriteLine($"GetTrajectoryPointNum failed: {rtn}");
            // No retornar, continuar la ejecución
        }
        else
        {
            Console.WriteLine($"Trajectory points count: {trajPointNum}");
        }

        // 6. Iniciar la ejecución del movimiento de trayectoria (no bloqueante)
        rtn = robot.MoveTrajectoryJ();
        if (rtn != 0)
        {
            Console.WriteLine($"MoveTrajectoryJ failed: {rtn}");
            return rtn;
        }
        Console.WriteLine("MoveTrajectoryJ started.");

        // 7. Modificar dinámicamente la velocidad durante el movimiento (alternando 10% y 80%)
        // Usar GetRobotMotionDone para comprobar si el movimiento ha finalizado
        byte motionDone = 0;
        robot.GetRobotMotionDone(ref motionDone);

        while (motionDone == 0)
        {
            // Establecer velocidad al 10%
            rtn = robot.SetTrajectoryJSpeed(10.0, trajSpeedMode);
            Console.WriteLine($"SetTrajectoryJSpeed to 10% returned: {rtn}");
            robot.Sleep(1000);

            // Volver a comprobar el estado del movimiento
            robot.GetRobotMotionDone(ref motionDone);
            if (motionDone != 0) break;

            // Establecer velocidad al 80%
            rtn = robot.SetTrajectoryJSpeed(80.0, trajSpeedMode);
            Console.WriteLine($"SetTrajectoryJSpeed to 80% returned: {rtn}");
            robot.Sleep(1000);

            // Comprobar de nuevo el estado del movimiento
            robot.GetRobotMotionDone(ref motionDone);
        }

        Console.WriteLine("Trajectory J motion completed.");
        return 0;
    }

Establecer la fuerza y el par durante la ejecución de la trayectoria del archivo de trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer la fuerza y el par durante la ejecución de la trayectoria del archivo de trayectoria  
    * @param [in] ft Fuerza y par en las tres direcciones, unidad N y Nm
    * @return Código de error 
    */
    int SetTrajectoryJForceTorque(ForceTorque ft); 

Establecer la fuerza a lo largo de la dirección x durante la ejecución de la trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer la fuerza a lo largo de la dirección x durante la ejecución de la trayectoria  
    * @param [in] fx  Fuerza a lo largo de la dirección x, unidad N
    * @return Código de error 
    */
    int SetTrajectoryJForceFx(double fx);

Establecer la fuerza a lo largo de la dirección y durante la ejecución de la trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer la fuerza a lo largo de la dirección y durante la ejecución de la trayectoria  
    * @param [in] fy  Fuerza a lo largo de la dirección y, unidad N
    * @return Código de error 
    */
    int SetTrajectoryJForceFy(double fy);

Establecer la fuerza a lo largo de la dirección z durante la ejecución de la trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer la fuerza a lo largo de la dirección z durante la ejecución de la trayectoria  
    * @param [in] fz  Fuerza a lo largo de la dirección z, unidad N
    * @return Código de error 
    */
    int SetTrajectoryJForceFz(double fz);

Establecer el par alrededor del eje x durante la ejecución de la trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el par alrededor del eje x durante la ejecución de la trayectoria  
    * @param [in] tx  Par alrededor del eje x, unidad Nm
    * @return Código de error 
    */
    int SetTrajectoryJTorqueTx(double tx);

Establecer el par alrededor del eje y durante la ejecución de la trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el par alrededor del eje y durante la ejecución de la trayectoria  
    * @param [in] ty  Par alrededor del eje y, unidad Nm
    * @return Código de error 
    */
    int SetTrajectoryJTorqueTy(double ty);

Establecer el par alrededor del eje z durante la ejecución de la trayectoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el par alrededor del eje z durante la ejecución de la trayectoria  
    * @param [in] tz  Par alrededor del eje z, unidad Nm
    * @return Código de error 
    */
    int SetTrajectoryJTorqueTz(double tz);

Cargar el archivo de trayectoria J
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Cargar el archivo de trayectoria J
    * @param [in] filePath Ruta completa del archivo de trayectoria a cargar   C://test/testJ.txt
    * @return Código de error
    */
    int TrajectoryJUpLoad(string filePath);

Eliminar el archivo de trayectoria J
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Eliminar el archivo de trayectoria J
    * @param [in] fileName Nombre del archivo testJ.txt
    * @return Código de error
    */
    int TrajectoryJDelete(string fileName);

Ejemplo de código de reproducción del archivo de trayectoria J del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button33_Click(object sender, EventArgs e)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/spray_traj1.txt");
        Console.WriteLine("Upload TrajectoryJ A {0}\n", rtn);

        string traj_file_name = "/fruser/traj/spray_traj1.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        Console.WriteLine("LoadTrajectoryJ {0}, rtn is: {1}\n", traj_file_name, rtn);

        DescPose traj_start_pose = new DescPose();
        rtn = robot.GetTrajectoryStartPose(traj_file_name, ref traj_start_pose);
        Console.WriteLine("GetTrajectoryStartPose is: {0}\n", rtn);
        Console.WriteLine("desc_pos:{0},{1},{2},{3},{4},{5}\n",
            traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z,
            traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);

        Thread.Sleep(1000);

        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(ref traj_num);
        Console.WriteLine("GetTrajectoryStartPose rtn is: {0}, traj num is: {1}\n", rtn, traj_num);

        rtn = robot.SetTrajectoryJSpeed(50.0f);
        Console.WriteLine("SetTrajectoryJSpeed is: {0}\n", rtn);

        ForceTorque traj_force = new ForceTorque();
        traj_force.fx = 10;
        rtn = robot.SetTrajectoryJForceTorque(traj_force);
        Console.WriteLine("SetTrajectoryJForceTorque rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFx(10.0f);
        Console.WriteLine("SetTrajectoryJForceFx rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFy(0.0f);
        Console.WriteLine("SetTrajectoryJForceFy rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFz(0.0f);
        Console.WriteLine("SetTrajectoryJForceFz rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTx(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTx rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTy(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTy rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTz(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTz rtn is: {0}\n", rtn);

        rtn = robot.MoveTrajectoryJ();
        Console.WriteLine("MoveTrajectoryJ rtn is: {0}\n", rtn);
    }

Preprocesamiento de trayectoria (previsión de trayectoria)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Preprocesamiento de trayectoria (previsión de trayectoria)
    * @param  [in] name  Nombre del archivo de trayectoria
    * @param  [in] mode Modo de muestreo, 0-sin muestreo; 1-muestreo con intervalos de datos iguales; 2-muestreo con límite de error igual
    * @param  [in] errorLim Límite de error, efectivo al usar ajuste de línea recta
    * @param  [in] type Modo de suavizado, 0-suavizado de Bézier
    * @param  [in] precision Precisión de suavizado, efectiva al usar suavizado de Bézier
    * @param  [in] vamx Velocidad máxima establecida, mm/s
    * @param  [in] amax Aceleración máxima establecida, mm/s2
    * @param  [in] jmax Jerk máximo establecido, mm/s3
    * @return  Código de error   
    */
    int LoadTrajectoryLA(string name, int mode, double errorLim, int type, double precision, double vamx, double amax, double jmax);

Reproducción de trayectoria (previsión de trayectoria)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Reproducción de trayectoria (previsión de trayectoria)
    * @return  Código de error   
    */
    int MoveTrajectoryLA();

Ejemplo de código de reproducción de trayectoria (previsión de trayectoria)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button87_Click(object sender, EventArgs e)
    {
        // Cargar el archivo de trayectoria
        int rtn = robot.TrajectoryJUpLoad(@"D:\zUP\horse.txt");
        Console.WriteLine($"Upload TrajectoryJ A {rtn}");

        string trajFileName = "horse.txt";
        rtn = robot.LoadTrajectoryLA(trajFileName, 2, 0, 0, 1, 40, 100, 100, 1);
        Console.WriteLine($"LoadTrajectoryLA {trajFileName}, rtn is: {rtn}");

        DescPose trajStartPose = new DescPose();
        rtn = robot.GetTrajectoryStartPose(trajFileName, ref trajStartPose);
        Console.WriteLine($"GetTrajectoryStartPose is: {rtn}");
        Console.WriteLine($"desc_pos: {trajStartPose.tran.x},{trajStartPose.tran.y},{trajStartPose.tran.z},{trajStartPose.rpy.rx},{trajStartPose.rpy.ry},{trajStartPose.rpy.rz}");

        Thread.Sleep(1000);

        robot.SetSpeed(50);
        robot.MoveCart(trajStartPose, 0, 0, 100, 100, 100, -1, -1);

        rtn = robot.MoveTrajectoryLA();
        Console.WriteLine($"MoveTrajectoryLA rtn is: {rtn}");
    }

Moverse al punto inicial del registro de trayectoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Moverse al punto inicial del registro de trayectoria TPD
    * @param [in] name Nombre del archivo de trayectoria
    * @param [in] moveType Tipo de movimiento; 0-PTP; 1-LIN
    * @param [in] ovl Porcentaje de escala de velocidad, rango [0~100]
    * @return Código de error
    */
    public int MoveToTPDStart(string name, int moveType, double ovl)

Ejemplo de código SDK para moverse al punto inicial del registro de trayectoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void testTPDmove()
    {
        string name = "tpd2025";
        int type = 1;
        int period_ms = 4;
        int rtn = 0;
        UInt16 di_choose = 0;
        UInt16 do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        Thread.Sleep(3000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        Thread.Sleep(3000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        Thread.Sleep(1000);
        float ovl = 100.0f;
        byte blend = 0;
        DescPose start_pose = new DescPose();
        rtn = robot.LoadTPD(name);
        Console.WriteLine($"LoadTPD rtn is:{rtn}\n");

        robot.GetTPDStartPose(name, ref start_pose);
        Console.WriteLine($"start pose, xyz is: %f %f %f. rpy is: {start_pose.tran.x},{start_pose.tran.y}, {start_pose.tran.z}, {start_pose.rpy.rx}, {start_pose.rpy.ry}, {start_pose.rpy.rz}");

        rtn = robot.MoveToTPDStart(name, 0, 100.0);

        rtn = robot.MoveTPD(name, blend, ovl);
        Thread.Sleep(5000*5);

        robot.SetTPDDelete(name);
    }