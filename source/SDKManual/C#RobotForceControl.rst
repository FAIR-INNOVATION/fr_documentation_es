Control de fuerza del robot
============================

.. toctree:: 
    :maxdepth: 5

Configuración del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Configurar el sensor de fuerza
    * @param  [in] company  Fabricante del sensor de fuerza, 17-Kunwei Technology
    * @param  [in] device  Número de dispositivo, no se utiliza por ahora, por defecto 0
    * @param  [in] softvesion  Número de versión del software, no se utiliza por ahora, por defecto 0
    * @param  [in] bus Posición del bus del extremo donde está conectado el dispositivo, no se utiliza por ahora, por defecto 0
    * @return  Código de error
    */
    int FT_SetConfig(int company, int device, int softvesion, int bus); 

Obtener la configuración del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener la configuración del sensor de fuerza 
    * @param [out] deviceID Número del sensor de fuerza 
    * @param [out] company Fabricante del sensor de fuerza, fabricante del sensor de fuerza, 17-Kunwei Technology, 19-Instituto 11 de Aeroespacial, 20-sensor ATI, 21-Zhongke Midian, 22-Weihang Minxin
    * @param [out] device  Número de dispositivo, Kunwei (0-KWR75B), Instituto 11 de Aeroespacial (0-MCS6A-200-4), ATI (0-AXIA80 -M8), Zhongke Midian (0-MST2010), Weihang Minxin (0-WHC6L-YB-10A) 
    * @param [out] softvesion Número de versión del software, no se utiliza por ahora, por defecto 0 
    * @return Código de error 
    */ 
    int FT_GetConfig(ref int deviceID, ref int company, ref int device, ref int softvesion); 

Activación del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Activación del sensor de fuerza
    * @param  [in] act  0-restablecer, 1-activar
    * @return  Código de error
    */
    int FT_Activate(byte act); 

Puesta a cero del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Puesta a cero del sensor de fuerza
    * @param  [in] act  0-eliminar el cero, 1-corrección del cero
    * @return  Código de error
    */
    int FT_SetZero(byte act); 

Establecer el sistema de coordenadas de referencia del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el sistema de coordenadas de referencia del sensor de fuerza
    * @param  [in] ref  0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    * @return  Código de error
    */
    int FT_SetRCS(byte type); 

Establecer el peso de la carga bajo el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el peso de la carga bajo el sensor de fuerza
    * @param  [in] weight Peso de la carga kg
    * @return  Código de error
    */
    int SetForceSensorPayLoad(double weight);

Establecer el centro de gravedad de la carga bajo el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el centro de gravedad de la carga bajo el sensor de fuerza
    * @param  [in] x Centro de gravedad de la carga x mm 
    * @param  [in] y Centro de gravedad de la carga y mm
    * @param  [in] z Centro de gravedad de la carga z mm
    * @return  Código de error
    */
    int SetForceSensorPayLoadCog(double x, double y, double z);

Obtener el peso de la carga bajo el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el peso de la carga bajo el sensor de fuerza
    * @param  [in] weight Peso de la carga kg
    * @return  Código de error
    */
    int GetForceSensorPayLoad(ref double weight);

Obtener el centro de gravedad de la carga bajo el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el centro de gravedad de la carga bajo el sensor de fuerza
    * @param  [out] x Centro de gravedad de la carga x mm 
    * @param  [out] y Centro de gravedad de la carga y mm
    * @param  [out] z Centro de gravedad de la carga z mm
    * @return  Código de error
    */
    int GetForceSensorPayLoadCog(ref double x, ref double y, ref double z);

Puesta a cero automática del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Puesta a cero automática del sensor de fuerza
    * @param  [out] weight Masa del sensor kg 
    * @param  [out] pos Centro de gravedad del sensor mm
    * @return  Código de error
    */
    int ForceSensorAutoComputeLoad(ref double weight, ref DescTran pos);

Obtener los datos de fuerza/par en el sistema de coordenadas de referencia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener los datos de fuerza/par en el sistema de coordenadas de referencia
    * @param  [out] ft  Fuerza/par, fx,fy,fz,tx,ty,tz
    * @return  Código de error
    */   
    int FT_GetForceTorqueRCS(byte flag, ref ForceTorque ft); 

Obtener los datos brutos de fuerza/par del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener los datos brutos de fuerza/par del sensor de fuerza
    * @param  [out] ft  Fuerza/par, fx,fy,fz,tx,ty,tz
    * @return  Código de error
    */   
    int FT_GetForceTorqueOrigin(byte flag, ref ForceTorque ft); 

Ejemplo de código de configuración y puesta a cero automática del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button54_Click(object sender, EventArgs e)
    {
        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config:{company},{device},{softversion},{bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        ForceTorque ft = new ForceTorque(0, 0, 0, 0, 0, 0);
        robot.FT_GetForceTorqueOrigin(0, ref ft);
        Console.WriteLine($"ft origin:{ft.fx},{ft.fy},{ft.fz},{ft.tx},{ft.ty},{ft.tz}");
        robot.FT_SetZero(1);
        Thread.Sleep(1000);

        DescPose ftCoord = new DescPose(0, 0, 0, 0, 0, 0);
        robot.FT_SetRCS(0, ftCoord);

        robot.SetForceSensorPayLoad(0.824);
        robot.SetForceSensorPayLoadCog(0.778, 2.554, 48.765);
        double weight = 0;
        double x = 0, y = 0, z = 0;
        robot.GetForceSensorPayLoad(ref weight);
        robot.GetForceSensorPayLoadCog(ref x, ref y, ref z);
        Console.WriteLine($"the FT load is {weight}, {x} {y} {z}");

        robot.SetForceSensorPayLoad(0);
        robot.SetForceSensorPayLoadCog(0, 0, 0);

        double computeWeight = 0;
        DescTran tran = new DescTran(0, 0, 0);
        robot.ForceSensorAutoComputeLoad(ref weight, ref tran);
        Console.WriteLine($"the result is weight {weight} pos is {tran.x} {tran.y} {tran.z}");

    } 

Registro de identificación del peso de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Registro de identificación del peso de la carga
    * @param  [in] id  Número del sistema de coordenadas del sensor, rango [1~14]
    * @return  Código de error
    */
    int FT_PdIdenRecord(int id);

Cálculo de identificación del peso de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Cálculo de identificación del peso de la carga
    * @param  [out] weight  Peso de la carga, unidad kg
    * @return  Código de error
    */   
    int FT_PdIdenCompute(ref double weight);

Registro de identificación del centro de gravedad de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Registro de identificación del centro de gravedad de la carga
    * @param  [in] id  Número del sistema de coordenadas del sensor, rango [1~14]
    * @param  [in] index Número de punto, rango [1~3]
    * @return  Código de error
    */
    int FT_PdCogIdenRecord(int id, int index); 

Cálculo de identificación del centro de gravedad de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Cálculo de identificación del centro de gravedad de la carga
    * @param  [out] cog  Centro de gravedad de la carga, unidad mm
    * @return  Código de error
    */   
    int FT_PdCogIdenCompute(ref DescTran cog);

Ejemplo de código de identificación de carga del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnFTPdCog_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        ForceTorque ft = new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ref ft);
        Console.WriteLine($"ft origin: {ft.fx}, {ft.fy}, {ft.fz}, {ft.tx}, {ft.ty}, {ft.tz}");
        robot.FT_SetZero(1);
        Thread.Sleep(1000);

        DescPose tcoord = new DescPose(0, 0, 35.0, 0, 0, 0);
        robot.SetToolCoord(10, tcoord, 1, 0, 0, 0);

        robot.FT_PdIdenRecord(10);
        Thread.Sleep(1000);

        double weight = 0.0f;
        robot.FT_PdIdenCompute(ref weight);
        Console.WriteLine($"payload weight: {weight}");

        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.MoveCart( desc_p1, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 1);
        robot.MoveCart( desc_p2, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 2);
        robot.MoveCart( desc_p3, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 3);

        DescTran cog = new DescTran(0,0,0);
        robot.FT_PdCogIdenCompute(ref cog);
        Console.WriteLine($"cog: {cog.x}, {cog.y}, {cog.z}");
    }

Protección contra colisiones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
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
    int FT_Guard(int flag, int sensor_id, int[] select, ForceTorque ft, double[] max_threshold, double[] min_threshold); 

Ejemplo de código de protección contra colisiones
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnFTGuard_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        byte sensor_id = 1;
        int[] select = { 1, 1, 1, 1, 1, 1 };
        double[] max_threshold = { 10.0f, 10.0f, 10.0f, 10.0f, 10.0f, 10.0f };
        double[] min_threshold = { 5.0f, 5.0f, 5.0f, 5.0f, 5.0f, 5.0f };

        ForceTorque ft = new ForceTorque();
        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.FT_Guard(1, sensor_id, select,  ft, max_threshold, min_threshold);
        robot.MoveCart( desc_p1, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart( desc_p2, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart( desc_p3, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);

        robot.FT_Guard(0, sensor_id, select, ft, max_threshold, min_threshold);
    }

Control de fuerza constante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Control de fuerza constante
    * @param  [in] flag 0-desactivar el control de fuerza constante, 1-activar el control de fuerza constante
    * @param  [in] sensor_id Número del sensor de fuerza
    * @param  [in] select  Seleccionar si se detectan colisiones en los seis grados de libertad, 0-no detectar, 1-detectar
    * @param  [in] ft  Fuerza/par de colisión, fx,fy,fz,tx,ty,tz
    * @param  [in] ft_pid Parámetros pid de fuerza, parámetros pid de par
    * @param  [in] adj_sign Control de inicio/parada adaptativo, 0-desactivar, 1-activar
    * @param  [in] ILC_sign Control de inicio/parada ILC, 0-detener, 1-entrenamiento, 2-operación real
    * @param  [in] max_dis Distancia máxima de ajuste, unidad mm
    * @param  [in] max_ang Ángulo máximo de ajuste, unidad deg
    * @param  [in] M Parámetros de masa rx, ry [0.1-10], por defecto 2
    * @param  [in] B Parámetros de amortiguación rx, ry [0.1-50], por defecto 8
    * @param  [in] threshold Umbral de activación rx, ry [0-10], por defecto 0.2
    * @param  [in] adjustCoeff Coeficiente de ajuste de par rx, ry [0-1], por defecto 1
    * @param  [in] polishRadio Radio de pulido, unidad mm
    * @param  [in] filter_Sign Indicador de activación del filtro 0-desactivado; 1-activado, desactivado por defecto
    * @param  [in] posAdapt_sign Indicador de activación de adaptación de orientación 0-desactivado; 1-activado, desactivado por defecto
    * @param  [in] isNoBlock Indicador de bloqueo, 0-bloqueante; 1-no bloqueante
    * @return  Código de error
    */
    public int FT_Control(byte flag, int sensor_id, byte[] select, ForceTorque ft, float[] ft_pid,byte adj_sign, byte ILC_sign, float max_dis, float max_ang,double[] M, double[] B, double[] threshold, double[] adjustCoeff,double polishRadio, int filter_Sign, int posAdapt_sign, int isNoBlock)

Ejemplo de código de control de fuerza constante con amortiguación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    public void TestFTControlWithAdjustCoeff()
    {
        int rtn;
        int sensor_id = 10;
        byte[] select = new byte[6] { 0, 0, 1, 0, 0, 0 };
        float[] ft_pid = new float[6] { 0.0008f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        byte adj_sign = 0;
        byte ILC_sign = 0;
        float max_dis = 1000.0f;
        float max_ang = 20.0f;
        ForceTorque ft = new ForceTorque();
        ft.fz = -10.0f;
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        JointPos j1 = new JointPos(80.765f, -98.795f, 106.548f, -97.734f, -89.999f, 94.842f);
        JointPos j2 = new JointPos(43.067f, -84.429f, 92.620f, -98.175f, -90.011f, 57.144f);
        DescPose desc_p1 = new DescPose(5.009f, -547.463f, 262.053f, -179.999f, -0.019f, 75.923f);
        DescPose desc_p2 = new DescPose(-347.966f, -547.463f, 262.048f, -180.000f, -0.019f, 75.923f);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        double[] M = new double[2] { 2.0, 2.0 };
        double[] B = new double[2] { 15.0, 15.0 };
        double[] threshold = new double[2] { 1.0, 1.0 };
        double[] adjustCoeff = new double[2] { 1.0, 0.8 };
        double polishRadio = 0.0;
        int filter_Sign = 0;
        int posAdapt_sign = 1;
        int isNoBlock = 0;
        while (true)
        {
            rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            Console.WriteLine($"FT_Control start rtn is {rtn}");
            robot.MoveL(j1, desc_p1, 1, 0, 100, 100, 100, -1, 0, epos, 0, 0, offset_pos, 0, 0, 10);
            robot.MoveL(j2, desc_p2, 1, 0, 100, 100, 100, -1, 0, epos, 0, 0, offset_pos, 0, 0, 10);
            rtn = robot.FT_Control(0, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            Console.WriteLine($"FT_Control end rtn is {rtn}");
        }
    }

Inserción rotativa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Inserción rotativa
    * @param [in] rcs Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    * @param [in] angVelRot Velocidad angular de rotación, unidad deg/s
    * @param [in] ft Umbral de fuerza/par, fx,fy,fz,tx,ty,tz, rango [0~100]
    * @param [in] max_angle Ángulo máximo de rotación, unidad deg
    * @param [in] orn Dirección de fuerza/par, 1-a lo largo del eje z, 2-alrededor del eje z
    * @param [in] max_angAcc Aceleración angular máxima de rotación, unidad deg/s^2, no se utiliza por ahora, por defecto 0
    * @param [in] rotorn Dirección de rotación, 1-horario, 2-antihorario
    * @param [in] strategy Estrategia de tratamiento cuando no se detecta fuerza/par, 0-error; 1-advertencia, continuar el movimiento
    * @return Código de error
    */
    public int FT_RotInsertion(int rcs, double angVelRot, double ft, double max_angle, int orn, double max_angAcc, int rotorn, int strategy)

Exploración helicoidal
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
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
    public int FT_SpiralSearch(int rcs, float dr, float ft, float max_t_ms, float max_vel, int strategy = 0)

Inserción lineal
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
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
    public int FT_LinInsertion(int rcs, float ft, float lin_v, float lin_a, float max_dis, byte linorn, int strategy=0)

Ejemplo de código de inserción rotativa del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public void TestRotInsert()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        int rtn;

        float forceInsertion = 5.0f; // Umbral de fuerza o par (0~100), unidad N o Nm
        int angleMax = 300; // Ángulo máximo de rotación, unidad °
        byte orn = 1; // Dirección de fuerza, 1-fz, 2-mz
        float angAccmax = 0; // Aceleración angular máxima de rotación, unidad °/s^2, no se utiliza por ahora
        byte status = 1;  // Indicador de activación del control de fuerza constante, 0-desactivado, 1-activado
        int sensor_num = 11; // Número del sensor de fuerza
        float[] gain = { 0.0001f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };  // Umbral máximo
        byte adj_sign = 0;  // Estado de inicio/parada adaptativo, 0-desactivado, 1-activado
        byte ILC_sign = 0;  // Estado de inicio/parada del control ILC, 0-detener, 1-entrenamiento, 2-operación real
        float max_dis = 1000.0f;  // Distancia máxima de ajuste
        float max_ang = 20.0f;  // Ángulo máximo de ajuste
        ForceTorque ft = new ForceTorque();
        int rcs = 0;  // Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
        float angVelRot = 1.0f;  // Velocidad angular de rotación, unidad °/s
        byte rotorn = 1; // Dirección de rotación, 1-horario, 2-antihorario
        JointPos j1 = new JointPos(100.968, -108.678, 126.166, -106.630, -93.253, 19.584);
        DescPose desc_p1 = new DescPose(159.473, -316.570, 334.560, -179.718, -3.352, 171.400);
        ExaxisPos epos = new ExaxisPos(0.0f, 0.0f, 0.0f, 0.0f);
        DescPose offset_pos = new DescPose(0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f);

        robot.MoveL(j1, desc_p1, 2, 0, 100.0f, 180.0f, 100.0f, -1.0f, 0, epos, (byte)0, (byte)1, offset_pos);

        byte[] select3 = { 0, 0, 1, 0, 0, 0 };
        ft.fz = -5.0f;
        gain[0] = 0.0001f;
        status = 1;
        robot.FT_Control(status, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
        rtn = robot.FT_LinInsertion(rcs, 10, 1, 1, 100, 1);
        Console.WriteLine("FT_LinInsertion rtn is " + rtn);
        robot.FT_Control(0, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);

        ft.fz = -30.0f;
        robot.FT_Control(1, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
        rtn = robot.FT_RotInsertion(rcs, angVelRot, forceInsertion, angleMax, orn, angAccmax, rotorn, 0);
        Console.WriteLine("FT_RotInsertion rtn is " + rtn);
        robot.FT_Control(0, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);

        rtn = robot.FT_LinInsertion(0, 40, 3, 0, 100, 1);
        Console.WriteLine("FT_LinInsertion retract rtn is " + rtn);

        Thread.Sleep(1000);
        robot.GetRobotRealTimeState(ref pkg);
        Console.WriteLine("robot errcode " + pkg.main_code + "  " + pkg.sub_code);
    }

Localización de superficie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
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
    public int FT_FindSurface(int rcs, byte dir, byte axis, float lin_v, float lin_a, float max_dis, float ft, int stragety = 0)

Inicio del cálculo de la posición del plano intermedio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inicio del cálculo de la posición del plano intermedio
    * @return  Código de error
    */
    public int FT_CalCenterStart()

Fin del cálculo de la posición del plano intermedio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Fin del cálculo de la posición del plano intermedio
    * @param  [out] pos Pose del plano intermedio
    * @return  Código de error
    */
    public int FT_CalCenterEnd(ref DescPose pos)

Ejemplo de código de punto de superficie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    private void button59_Click(object sender, EventArgs e)
    {
        int company = 22;
        int device = 0;
        int softversion = 0;
        int bus = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine("FT config:" + company + "," + device + "," + softversion + "," + bus);
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        int rcs = 0;
        byte dir = 1;
        byte axis = 1;
        float lin_v = 15.0f;
        float lin_a = 0.0f;
        float maxdis = 500.0f;
        float ft_goal = 2.0f;
        DescPose desc_pos = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose xcenter = new DescPose(0, 0, 0, 0, 0, 0);
        DescPose ycenter = new DescPose(0, 0, 0, 0, 0, 0);

        ForceTorque ft = new ForceTorque();

        ft.fx = -2.0f;

        robot.MoveCart(desc_pos, 1, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);

        robot.FT_CalCenterStart();
        robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
        robot.MoveCart(desc_pos, 1, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.WaitMs(1000);

        dir = 2;
        robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
        robot.FT_CalCenterEnd(ref xcenter);
        Console.WriteLine("xcenter:" + xcenter.tran.x + "," + xcenter.tran.y + "," + xcenter.tran.z + "," + xcenter.rpy.rx + "," + xcenter.rpy.ry + "," + xcenter.rpy.rz);
        robot.MoveCart(xcenter, 1, 0, 60.0f, 50.0f, 50.0f, -1.0f, -1);

        robot.FT_CalCenterStart();
        dir = 1;
        axis = 2;
        lin_v = 6.0f;
        maxdis = 150.0f;
        robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
        robot.MoveCart(desc_pos, 1, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.WaitMs(1000);

        dir = 2;
        robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
        robot.FT_CalCenterEnd(ref ycenter);
        Console.WriteLine("ycenter:" + ycenter.tran.x + "," + ycenter.tran.y + "," + ycenter.tran.z + "," + ycenter.rpy.rx + "," + ycenter.rpy.ry + "," + ycenter.rpy.rz);
        robot.MoveCart(ycenter, 1, 0, 60.0f, 50.0f, 50.0f, 0.0f, -1);

    }

Establecer el desplazamiento en tiempo real de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el desplazamiento en tiempo real de la oscilación
    * @param [in] offset Desplazamiento en tiempo real [mm、°]
    * @return  Código de error
    */
    public int SetWeaveOffsetRT(DescPose offset)

Ejemplo de código de ajuste de velocidad y desplazamiento en tiempo real de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:   

    public void TestWeaveSpeedAndOffset()
    {
        Console.WriteLine("============================================================");
        Console.WriteLine("  Weave Speed and Offset Test");
        Console.WriteLine("============================================================");

        if (robot == null)
        {
            Console.WriteLine("ERROR: Robot not connected!");
            return;
        }

        int rtn;
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        JointPos j1 = new JointPos(5.027, -84.331, -75.139, -103.690, 86.379, 20.794);
        DescPose d1 = new DescPose(324.752, -83.339, 366.314, -172.321, -0.936, -106.047);

        JointPos j2 = new JointPos(-35.335, -117.598, -57.174, -95.234, 90.001, -19.560);
        DescPose d2 = new DescPose(324.999, -355.439, 260.000, 179.995, 0.003, -105.775);

        JointPos j3 = new JointPos(59.787, -117.594, -57.183, -95.222, 90.006, 75.562);
        DescPose d3 = new DescPose(324.998, 355.441, 260.002, 179.995, 0.003, -105.775);

        // ---- Paso 1: MoveJ al punto de inicio ----
        Console.WriteLine("\nPaso 1: MoveJ al punto de inicio");
        rtn = robot.MoveJ(j1, d1, 1, 0, 100, 100, 50, epos, -1, 0, offset_pos);
        Console.WriteLine("  MoveJ(j1) rtn={0}", rtn);
        Thread.Sleep(500);

        // ---- Paso 2: MoveJ a la entrada de oscilación ----
        Console.WriteLine("\nPaso 2: MoveJ al punto de entrada de oscilación");
        rtn = robot.MoveJ(j2, d2, 1, 0, 100, 100, 50, epos, -1, 0, offset_pos);
        Console.WriteLine("  MoveJ(j2) rtn={0}", rtn);
        Thread.Sleep(500);

        // ---- Paso 3: WeaveStart, lanzar el hilo de MoveL de oscilación ----
        Console.WriteLine("\nPaso 3: WeaveStart + MoveL en hilo en segundo plano");
        robot.WeaveStart(0);

        bool weaveRunning = true;
        Thread weaveThread = new Thread(() =>
        {
            rtn = robot.MoveL(j3, d3, 1, 0, 100, 100, 5, -1, 0, epos, 0, 0, offset_pos, 5, 0, 0, 10);
            Console.WriteLine("  Hilo MoveL(weave) finalizado, rtn={0}", rtn);
            weaveRunning = false;
        });
        weaveThread.IsBackground = true;
        weaveThread.Start();
        Thread.Sleep(500);  // Esperar a que comience el movimiento

        // ---- Paso 4: Prueba de velocidad (hilo principal, MoveL de oscilación en segundo plano) ----
        Console.WriteLine("\nPaso 4: Prueba de SetSpeed durante la oscilación");
        int[] speedValues = { 20, 50, 80, 30, 60, 10 };
        foreach (int speed in speedValues)
        {
            if (!weaveRunning) break;
            rtn = robot.SetSpeedInstant(speed);
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine("  SetSpeed({0}) -> rtn={1}, TCP_CmpSpeed={2}", speed, rtn, pkg.target_TCP_CmpSpeed);
            Thread.Sleep(5000);
        }


        Thread.Sleep(5000);
        // ---- Paso 5: Prueba de desplazamiento SetWeaveOffsetRT (hilo principal, MoveL de oscilación en segundo plano) ----
        Console.WriteLine("\nPaso 5: Prueba de SetWeaveOffsetRT (50 iteraciones, delta=0.1)");
        double accumOffset = 0.0;
        for (int i = 0; i < 50 && weaveRunning; i++)
        {
            accumOffset += 0.1;
            DescPose weaveOffset = new DescPose(0, 0, accumOffset, 0, 0, 0);
            rtn = robot.SetWeaveOffsetRT(weaveOffset);
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine("  [{0}/50] SetWeaveOffsetRT(x={1:F1}) -> rtn={2}, TCP_pos=({3:F2},{4:F2},{5:F2})",
                i + 1, accumOffset, rtn,
                pkg.tl_cur_pos[0], pkg.tl_cur_pos[1], pkg.tl_cur_pos[2]);
            Thread.Sleep(100);
        }

        // ---- Paso 6: Esperar el MoveL de oscilación y luego WeaveEnd ----
        Console.WriteLine("\nPaso 6: Esperar el MoveL de oscilación y luego WeaveEnd");
        weaveThread.Join();
        robot.WeaveEnd(0);
        Thread.Sleep(500);

        // ---- Paso 7: MoveL de vuelta al inicio ----
        Console.WriteLine("\nPaso 7: MoveL de vuelta al inicio");
        rtn = robot.MoveL(j1, d1, 1, 0, 100, 100, 50, -1, 0, epos, 0, 0, offset_pos, 50, 0, 0, 10);
        Console.WriteLine("  MoveL(back) rtn={0}", rtn);

        robot.GetRobotRealTimeState(ref pkg);
        Console.WriteLine("\n  Estado final del robot: main_code={0}, sub_code={1}", pkg.main_code, pkg.sub_code);
        Console.WriteLine("============================================================");
        Console.WriteLine("  Weave Speed and Offset Test Complete");
        Console.WriteLine("============================================================");
    } 

Inicio del control de compliance
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inicio del control de compliance
    * @param  [in] p Coeficiente de ajuste de posición o coeficiente de compliance
    * @param  [in] force Umbral de fuerza de activación del compliance, unidad N
    * @return  Código de error
    */   
    int FT_ComplianceStart(float p, float force);

Fin del control de compliance
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Fin del control de compliance
    * @return  Código de error
    */   
    int FT_ComplianceStop(); 

Ejemplo de código de control de compliance
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnComplience_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;
        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        byte flag = 1;
        int sensor_id = 1;
        int[] select = { 1, 1, 1, 0, 0, 0 };
        double[] ft_pid = { 0.0005f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        byte adj_sign = 0, ILC_sign = 0;
        float max_dis = 100.0f, max_ang = 0.0f;

        ForceTorque ft = new ForceTorque { fx = -10.0, fy = -10.0, fz = -10.0 };
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        robot.FT_Control(flag, (byte)sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang);
        float p = 0.00005f;
        float force = 30.0f;
        int rtn = robot.FT_ComplianceStart(p, force);
        Console.WriteLine($"FT_ComplianceStart rtn is {rtn}");

        int count = 5;
        while (count-- > 0)
        {
        robot.MoveL(j1, desc_p1, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, epos, 0, 1, offset_pos);
        robot.MoveL(j2, desc_p2, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, epos, 0, 0, offset_pos);
        }

        robot.FT_ComplianceStop();
        Console.WriteLine($"FT_ComplianceStop rtn is {rtn}");

        flag = 0;
        robot.FT_Control(flag, (byte)sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang);
    }

Inicialización de la identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Inicialización de la identificación de carga
    * @return Código de error
    */
    int LoadIdentifyDynFilterInit();

Inicialización de las variables de identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Inicialización de las variables de identificación de carga
    * @return Código de error
    */
    int LoadIdentifyDynVarInit();

Programa principal de identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Programa principal de identificación de carga
    * @param [in] joint_torque Par de las articulaciones
    * @param [in] joint_pos Posición de las articulaciones
    * @param [in] t Período de muestreo
    * @return Código de error
    */
    int LoadIdentifyMain(double[] joint_torque, double[] joint_pos, double t);

Obtener el resultado de la identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el resultado de la identificación de carga
    * @param [in] gain  Coeficiente del término de gravedad double[6], coeficiente del término centrífugo double[6]
    * @param [out] weight Peso de la carga
    * @param [out] cog Centro de gravedad de la carga
    * @return Código de error
    */
    int LoadIdentifyGetResult(double[] gain, ref double weight, ref DescTran cog);

Ejemplo de código de identificación de carga del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button74_Click(object sender, EventArgs e)
    {
        int rtn;
        int retval = 0;

        retval = robot.LoadIdentifyDynFilterInit();
        Console.WriteLine("LoadIdentifyDynFilterInit retval is: " + retval);

        retval = robot.LoadIdentifyDynVarInit();
        Console.WriteLine("LoadIdentifyDynVarInit retval is: " + retval);

        JointPos posJ = new JointPos(0,0,0,0,0,0);
        DescPose posDec = new DescPose(0, 0, 0, 0, 0, 0);
        double[] joint_toq = new double[6] { 0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        robot.GetActualJointPosDegree(0, ref posJ);
        posJ.jPos[1] = posJ.jPos[1] + 10;
        robot.GetJointTorques(0, joint_toq);
        joint_toq[1] = joint_toq[1] + 2;

        double[] tmpTorque = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        for (int i = 0; i < 6; i++)
        {
            tmpTorque[i] = joint_toq[i];
        }

        retval = robot.LoadIdentifyMain(tmpTorque, posJ.jPos, 1);
        Console.WriteLine("LoadIdentifyMain retval is: " + retval);

        double[] gain = new double[12] { 0, 0.05, 0, 0, 0, 0, 0, 0.02, 0, 0, 0, 0 };
        double weight = 0;
        DescTran load_pos = new DescTran(0, 0, 0);
        retval = robot.LoadIdentifyGetResult(gain, ref weight, ref load_pos);
        Console.WriteLine("LoadIdentifyGetResult retval is: {0}; weight is {1} cog is {2} {3} {4}", retval, weight, load_pos.x, load_pos.y, load_pos.z);
    }

Arrastre asistido por sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
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
    * @param  [in] Fmax Límite máximo de fuerza de arrastre Nm
    * @param  [in] Vmax Límite máximo de velocidad articular °/s
    * @return  Código de error
    */
    int EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag,int ingularityConstraintsFlag,int forceCollisionFlag, double[] M, double[] B, double[] K, double[] F, double Fmax, double Vmax);
    
Obtener el estado del interruptor de arrastre del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el estado del interruptor de arrastre del sensor de fuerza
    * @param  [out] dragState Estado de control del arrastre asistido por sensor de fuerza, 0-desactivar; 1-activar
    * @param  [out] sixDimensionalDragState Estado de control del arrastre asistido por fuerza de seis dimensiones, 0-desactivar; 1-activar
    * @return  Código de error
    */
    int GetForceAndTorqueDragState(ref int dragState, ref int sixDimensionalDragState);

Activación automática del sensor de fuerza tras el borrado de errores
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Activación automática del sensor de fuerza tras el borrado de errores
    * @param  [in] status Estado de control, 0-desactivar; 1-activar
    * @return  Código de error
    */
    int SetForceSensorDragAutoFlag(int status);

Ejemplo de código de arrastre asistido por sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button61_Click(object sender, EventArgs e)
    {
        robot.SetForceSensorDragAutoFlag(1);
        double[] M = { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
        double[] B = { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
        double[] K = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double[] F = { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };

        robot.EndForceDragControl(1, 0, 0, 0, M, B, K, F, 50, 100);
        robot.WaitMs(5000);

        int dragState = 0;
        int sixDimensionalDragState = 0;
        robot.GetForceAndTorqueDragState(ref dragState, ref sixDimensionalDragState);
        Console.WriteLine($"the drag state is {dragState} {sixDimensionalDragState}");

        robot.EndForceDragControl(0, 0, 0, 0, M, B, K, F, 50, 100);
    }

Establecer el interruptor y los parámetros del arrastre mixto de fuerza de seis dimensiones e impedancia articular
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el interruptor y los parámetros del arrastre mixto de fuerza de seis dimensiones e impedancia articular
    * @param  [in] status Estado de control, 0-desactivar; 1-activar
    * @param  [in] impedanceFlag Indicador de activación de la impedancia, 0-desactivar; 1-activar
    * @param  [in] lamdeDain Ganancia de arrastre
    * @param  [in] KGain Ganancia de rigidez
    * @param  [in] BGain Ganancia de amortiguación
    * @param  [in] dragMaxTcpVel Límite máximo de velocidad lineal del extremo durante el arrastre
    * @param  [in] dragMaxTcpOriVel Límite máximo de velocidad angular del extremo durante el arrastre
    * @return  Código de error
    */
    int ForceAndJointImpedanceStartStop(int status, int impedanceFlag, double[] lamdeDain, double[] KGain, double[] BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Ejemplo de código de arrastre asistido por sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button62_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        double[] lambdaGain = { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
        double[] kGain = { 0, 0, 0, 0, 0, 0 };
        double[] bGain = { 150, 150, 150, 5.0, 5.0, 1.0 };
        int rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lambdaGain, kGain, bGain, 1000, 180);
        Console.WriteLine($"ForceAndJointImpedanceStartStop rtn is {rtn}");
        Thread.Sleep(5000); 
        robot.DragTeachSwitch(0);
        rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lambdaGain, kGain, bGain, 1000, 180);
        Console.WriteLine($"ForceAndJointImpedanceStartStop rtn is {rtn}");
    }

Control de inicio/parada de la impedancia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Control de inicio/parada de la impedancia
    * @param [in] status 0：desactivar; 1-activar
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
    public int ImpedanceControlStartStop(int status, int workSpace, double[] forceThreshold, double[] m, double[] b, double[] k, double maxV, double maxVA, double maxW, double maxWA)

Ejemplo de código de control de inicio/parada de la impedancia del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    public void TestImpedanceControl()
    { 
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        int rtn;
        JointPos j1 = new JointPos(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
        JointPos j2 = new JointPos(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
        DescPose desc_pos1 = new DescPose(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
        DescPose desc_pos2 = new DescPose(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);
    
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
    
        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 200.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        float blendR = -1.0f;
    
        byte flag = 0;
    
        byte search = 0;
        robot.SetSpeed(20);
        int company = 17;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config:{company},{device},{softversion},{bus}");
        Thread.Sleep(1000);
    
        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);
        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);
        robot.FT_SetZero(1);
        Thread.Sleep(1000);
    
        double[] forceThreshold = new double[] { 30, 30, 30, 5, 5, 5 };
        double[] m = new double[] { 0.1, 0.1, 0.1, 0.02, 0.02, 0.02 };
        double[] b = new double[] { 1, 1, 1, 0.08, 0.08, 0.08 };
        double[] k = new double[] { 0, 0, 0, 0, 0, 0 };
        rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        Console.WriteLine($"ImpedanceControlStartStop errcode:{rtn}");
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        Console.WriteLine($"movel errcode:{rtn}");
        robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
    }

Activar la función de compensación de par y el coeficiente de compensación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Activar la función de compensación de par y el coeficiente de compensación
    * @param [in] status Interruptor, 0-desactivar; 1-activar
    * @param [in] torqueCoeff Coeficiente de compensación de par J1-J6 [0-1]
    * @return Código de error
    */
    public int SetCoderCompenParams(int status, double[] torqueCoeff)