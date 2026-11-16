Control de fuerza del robot
====================================

.. toctree:: 
    :maxdepth: 5

Configurar el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Configurar el sensor de fuerza
    * @param  config company: Fabricante del sensor de fuerza, 17-Kunwei Technology, 19-11º Instituto de Aeroespacial, 20-Sensor ATI, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xinjingcheng (XJC), 26-NSR
    * @param  config device: Número de dispositivo, Kunwei(0-KWR75B), 11º Instituto de Aeroespacial(0-MCS6A-200-4), ATI(0-AXIA80-M8), Zhongke Midian(0-MST2010), Weihang Minxin(0-WHC6L-YB-10A), NBIT(0-XLH93003ACS), Xinjingcheng XJC(0-XJC-6F-D82), NSR(0-NSR-FTSensorA)
    * @param  config softvesion: Número de versión de software, aún no utilizado, valor predeterminado 0
    * @param  config bus: Posición del bus del extremo donde está montado el dispositivo, aún no utilizado, valor predeterminado 0
    * @return  Código de error
    */
    int FT_SetConfig(DeviceConfig config); 

Obtener la configuración del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener la configuración del sensor de fuerza 
    * @param [out] config company: Fabricante del sensor de fuerza, 17-Kunwei Technology, 19-11º Instituto de Aeroespacial, 20-Sensor ATI, 21-Zhongke Midian, 22-Weihang Minxin
    * @param [out] config device: Número de dispositivo, Kunwei(0-KWR75B), 11º Instituto de Aeroespacial(0-MCS6A-200-4), ATI(0-AXIA80-M8), Zhongke Midian(0-MST2010), Weihang Minxin(0-WHC6L-YB-10A)
    * @param [out] config softvesion: Número de versión de software, aún no utilizado, valor predeterminado 0
    * @param [out] config bus: Posición del bus del extremo donde está montado el dispositivo, aún no utilizado, valor predeterminado 0
    * @return Código de error 
    */ 
    int FT_GetConfig(DeviceConfig config); 

Activación del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Activación del sensor de fuerza
    * @param  [in] act  0-reiniciar, 1-activar
    * @return  Código de error
    */
    int FT_Activate(int act); 

Puesta a cero del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Puesta a cero del sensor de fuerza
    * @param  [in] act  0-eliminar el punto cero, 1-corrección del punto cero
    * @return  Código de error
    */
    int FT_SetZero(int act); 

Establecer el sistema de coordenadas de referencia del sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer el sistema de coordenadas de referencia del sensor de fuerza
    * @param  [in] type  0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base, 2-sistema de coordenadas libre
    * @param  [in] coord  Valor del sistema de coordenadas libre
    * @return  Código de error
    */
    int FT_SetRCS(int type, DescPose coord);

Establecer el peso de la carga bajo el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el peso de la carga bajo el sensor de fuerza
    * @param [in] weight Peso de la carga kg
    * @return Código de error
    */
    int SetForceSensorPayLoad(double weight);

Establecer el centro de masa de la carga bajo el sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el centro de masa de la carga bajo el sensor de fuerza
    * @param [in] cog Centro de masa de la carga mm
    * @return Código de error
    */
    int SetForceSensorPayLoadCog(DescTran cog);

Obtener el peso de la carga bajo el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el peso de la carga bajo el sensor de fuerza
    * @return List[0]:código de error; List[1] : weight peso de la carga kg
    */
    List<Number> GetForceSensorPayLoad();

Obtener el centro de masa de la carga bajo el sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el centro de masa de la carga bajo el sensor de fuerza
    * @param [out] cog Centro de masa de la carga mm
    * @return Código de error
    */
    int GetForceSensorPayLoadCog(DescTran cog);

Puesta a cero automática del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Puesta a cero automática del sensor de fuerza
    * @param [in] massCenter Masa del sensor (kg) y centro de masa (mm)
    * @return Código de error
    */
    int ForceSensorAutoComputeLoad(MassCenter massCenter);

Obtener los datos de fuerza/par en el sistema de coordenadas de referencia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener los datos de fuerza/par en el sistema de coordenadas de referencia
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] ft  Fuerza/par, fx,fy,fz,tx,ty,tz
    * @return  Código de error
    */   
    int FT_GetForceTorqueRCS(int flag, ForceTorque ft); 

Obtener los datos brutos de fuerza/par del sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener los datos brutos de fuerza/par del sensor de fuerza
    * @param  [in] flag 0-bloqueante, 1-no bloqueante
    * @param  [out] ft  Fuerza/par, fx,fy,fz,tx,ty,tz
    * @return  Código de error
    */   
    int FT_GetForceTorqueOrigin(int flag, ForceTorque ft); 

Ejemplo de código de configuración del sensor de fuerza y puesta a cero automática
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFTInit(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company,device,softversion,bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ft);
        robot.FT_SetZero(1);
        robot.Sleep(1000);

        DescPose ftCoord = new DescPose();
        robot.FT_SetRCS(0, ftCoord);

        robot.SetForceSensorPayload(0.824);

        DescTran tr=new DescTran(0.778, 2.554, 48.765);
        robot.SetForceSensorPayloadCog(tr);
        List<Number> weight = new ArrayList<>();
        double x = 0, y = 0, z = 0;
        weight=robot.GetForceSensorPayload();
        robot.GetForceSensorPayloadCog(tr);
        tr.x=0;
        tr.y=0;
        tr.z=0;
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr);

        double computeWeight = 0;
        DescTran tran = new DescTran();
        MassCenter mass=new MassCenter();
        mass.weight=weight.get(1).doubleValue();
        mass.cog=tran;
        robot.ForceSensorAutoComputeLoad(mass);
        return 0;
    }

Registro de identificación del peso de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registro de identificación del peso de la carga
    * @param  [in] id  Número del sistema de coordenadas del sensor, rango [1~14]
    * @return  Código de error
    */
    int FT_PdIdenRecord(int id);

Cálculo de identificación del peso de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Cálculo de identificación del peso de la carga
    * @return  List[0]:código de error; List[1] : double weight  peso de la carga, unidad kg
    */   
    List<Number> FT_PdIdenCompute();

Registro de identificación del centro de masa de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registro de identificación del centro de masa de la carga
    * @param  [in] id  Número del sistema de coordenadas del sensor, rango [1~14]
    * @param  [in] index Número de punto, rango [1~3]
    * @return  Código de error
    */
    int FT_PdCogIdenRecord(int id, int index); 

Cálculo de identificación del centro de masa de la carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Cálculo de identificación del centro de masa de la carga
    * @param  [out] cog  Centro de masa de la carga, unidad mm
    * @return  Código de error
    */   
    int FT_PdCogIdenCompute(DescTran cog);

Ejemplo de código de identificación de carga del sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFTLoadCompute(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ft);
        robot.FT_SetZero(1);
        robot.Sleep(1000);

        DescPose tcoord = new DescPose();
        tcoord.tran.z = 35.0;
        robot.SetToolCoord(10, tcoord, 1, 0, 0, 0);

        robot.FT_PdIdenRecord(10);
        robot.Sleep(1000);

        List<Number> weight =new ArrayList<>();
        weight=robot.FT_PdIdenCompute();

        DescPose desc_p1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3=new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.MoveCart(desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 1);
        robot.MoveCart(desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 2);
        robot.MoveCart(desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 3);
        robot.Sleep(1000);
        DescTran cog=new DescTran(0,0,0);
        robot.FT_PdCogIdenCompute(cog);

        robot.CloseRPC();
        return 0;
    }

Protección de colisión
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Protección de colisión
    * @param  [in] flag 0-desactivar la protección de colisión, 1-activar la protección de colisión
    * @param  [in] sensor_id Número del sensor de fuerza
    * @param  [in] select  Selección de cuáles de los seis grados de libertad se detectan para colisión, 0-no detectar, 1-detectar
    * @param  [in] ft  Fuerza/par de colisión, fx,fy,fz,tx,ty,tz
    * @param  [in] max_threshold Umbral máximo
    * @param  [in] min_threshold Umbral mínimo
    * @note   Rango de detección de fuerza/par: (ft-min_threshold, ft+max_threshold)
    * @return  Código de error
    */   
    int FT_Guard(int flag, int sensor_id, Object[] select, ForceTorque ft, Object[] max_threshold, Object[] min_threshold); 

Ejemplo de código de protección de colisión
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);//设置重连次数、间隔
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("rpc连接 success");
        }
        else
        {
            System.out.println("rpc连接 fail");
            return ;
        }
        byte flag = 1;
        byte sensor_id = 8;
        Object[] select = { 1, 0, 0, 0, 0, 0 };//Solo se habilita la protección de colisión del eje x
        Object[] max_threshold = { 5.0, 0.01, 0.01, 0.01, 0.01, 0.01 };
        Object[] min_threshold = { 3.0, 0.01, 0.01, 0.01, 0.01, 0.01 };

        ForceTorque ft = new ForceTorque(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        DescPose  desc_p1, desc_p2, desc_p3;
        desc_p1 = new DescPose(-14.404,-455.283,319.847,-172.935,25.141,-68.097);
        desc_p2 = new DescPose(-107.999,-599.174,285.939,153.472,12.686,-71.284);
        desc_p3 = new DescPose(6.586,-704.897,309.638,178.909,-27.759,-70.479);

        int rtn =  robot.FT_Guard(flag, sensor_id, select, ft, max_threshold, min_threshold);
        System.out.println("FT_Guard start rtn {rtn}");
        robot.MoveCart(desc_p1, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart(desc_p2, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart(desc_p3, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
    }

Control de fuerza constante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Control de fuerza constante
    * @param  flag 0-desactivar el control de fuerza constante, 1-activar el control de fuerza constante
    * @param  sensor_id Número del sensor de fuerza
    * @param  select  Selección de cuáles de los seis grados de libertad se detectan para colisión, 0-no detectar, 1-detectar
    * @param  ft  Fuerza/par de colisión, fx,fy,fz,tx,ty,tz
    * @param  ft_pid Parámetros PID de fuerza, parámetros PID de par
    * @param  adj_sign Control de inicio/parada adaptativo, 0-desactivar, 1-activar
    * @param  ILC_sign Control de inicio/parada ILC, 0-detener, 1-entrenamiento, 2-operación práctica
    * @param  max_dis Distancia máxima de ajuste, unidad mm
    * @param  max_ang Ángulo máximo de ajuste, unidad deg
    * @param  M Parámetros de masa rx、ry [0.1-10], valor predeterminado 2
    * @param  B Parámetros de amortiguación rx、ry [0.1-50], valor predeterminado 8
    * @param  threshold Umbral de activación rx、ry [0-10], valor predeterminado 0.2
    * @param  adjustCoeff Coeficiente de ajuste del par rx、ry [0-1], valor predeterminado 1
    * @param  polishRadio Radio de pulido, unidad mm
    * @param  filter_Sign Indicador de activación del filtrado 0-desactivado; 1-activado, desactivado por defecto
    * @param  posAdapt_sign Indicador de activación de adaptación de orientación 0-desactivado; 1-activado, desactivado por defecto
    * @param  isNoBlock Indicador de bloqueo, 0-bloqueante; 1-no bloqueante
    * @return  Código de error
    */
    public int FT_Control(int flag, int sensor_id, int[] select, ForceTorque ft, double[] ft_pid, int adj_sign, int ILC_sign, double max_dis, double max_ang,double[] M,double[] B, double[] threshold, double[] adjustCoeff, double polishRadio,int filter_Sign, int posAdapt_sign, int isNoBlock)

Ejemplo de código de control de fuerza constante con amortiguación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFTControlWithAdjustCoeff(Robot robot)
    {
        int sensor_id = 10;
        int[] select = { 0,0,1,0,0,0 };
        double[] ft_pid = { 0.0008, 0.0, 0.0, 0.0, 0.0, 0.0 };
        int adj_sign = 0;
        int ILC_sign = 0;
        double max_dis = 1000.0;
        double max_ang = 20;
        ForceTorque ft = new ForceTorque(0.0,0,0,0,0,0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        JointPos j1=new JointPos(80.765, -98.795, 106.548, -97.734, -89.999, 94.842);
        JointPos j2=new JointPos(43.067, -84.429, 92.620, -98.175, -90.011, 57.144);
        DescPose desc_p1=new DescPose(5.009, -547.463, 262.053, -179.999, -0.019, 75.923);
        DescPose desc_p2=new DescPose(-347.966, -547.463, 262.048, -180.000, -0.019, 75.923);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        double[] M = { 2.0, 2.0 };
        double[] B = { 15.0, 15.0 };
        double[] threshold = {1.0, 1.0};
        double[] adjustCoeff = {1.0, 0.8};
        double polishRadio = 0.0;
        int filter_Sign = 0;
        int posAdapt_sign = 1;
        int isNoBlock;
        ft.fz = -10.0;
        while(true)
        {
            int rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            System.out.printf("FT_Control start rtn is %d\n", rtn);
            robot.MoveL(j1, desc_p1, 1, 0, 100.0, 100.0, 100.0, -1.0, 0, epos, 0, 0, offset_pos, 0,0, 0,10);
            robot.MoveL(j2, desc_p2, 1, 0, 100.0, 100.0, 100.0, -1.0, 0, epos, 0, 0, offset_pos, 0,0, 0,10);
            rtn = robot.FT_Control(0, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            System.out.printf("FT_Control end rtn is %d\n", rtn);
        }
    }

Inserción giratoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inserción giratoria
    * @param rcs Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    * @param angVelRot Velocidad angular de rotación, unidad deg/s
    * @param ft  Umbral de fuerza/par, fx,fy,fz,tx,ty,tz, rango [0~100]
    * @param max_angle Ángulo máximo de rotación, unidad deg
    * @param orn Dirección de fuerza/par, 1-a lo largo del eje z, 2-alrededor del eje z
    * @param max_angAcc Aceleración angular máxima de rotación, unidad deg/s^2, aún no utilizada, valor predeterminado 0
    * @param rotorn Dirección de rotación, 1-sentido horario, 2-sentido antihorario
    * @param strategy Estrategia de tratamiento cuando no se detecta fuerza/par, 0-error; 1-advertencia, continuar el movimiento
    * @return  Código de error
    */
    public int FT_RotInsertion(int rcs, double angVelRot, double ft, double max_angle, int orn, double max_angAcc, int rotorn, int strategy)

Exploración en hélice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Exploración en hélice
    * @param  [in] rcs Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    * @param  [in] dr Avance de radio por vuelta
    * @param  [in] ft Umbral de fuerza/par, fx,fy,fz,tx,ty,tz, rango [0~100]
    * @param  [in] max_t_ms Tiempo máximo de exploración, unidad ms
    * @param  [in] max_vel Velocidad lineal máxima, unidad mm/s
    * @param  [in] strategy Estrategia de tratamiento cuando no se detecta fuerza/par, 0-error; 1-advertencia, continuar el movimiento
    * @return  Código de error
    */
    public int FT_SpiralSearch(int rcs, double dr, double ft, double max_t_ms, double max_vel, int strategy)

Inserción recta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inserción recta
    * @param rcs Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    * @param ft Umbral de fuerza/par, fx,fy,fz,tx,ty,tz, rango [0~100]
    * @param lin_v Velocidad lineal, unidad mm/s
    * @param lin_a Aceleración lineal, unidad mm/s^2, aún no utilizada
    * @param max_dis Distancia máxima de inserción, unidad mm
    * @param linorn Dirección de inserción, 0-dirección negativa, 1-dirección positiva
    * @return Código de error
    */
    public int FT_LinInsertion(int rcs, double ft, double lin_v, double lin_a, double max_dis, int linorn, int strategy)

Localización de superficie
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Localización de superficie
    * @param rcs Sistema de coordenadas de referencia, 0-sistema de coordenadas de herramienta, 1-sistema de coordenadas base
    * @param dir Dirección de movimiento, 1-dirección positiva, 2-dirección negativa
    * @param axis Eje de movimiento, 1-eje x, 2-eje y, 3-eje z
    * @param lin_v Velocidad lineal de exploración, unidad mm/s
    * @param lin_a Aceleración lineal de exploración, unidad mm/s^2, aún no utilizada, valor predeterminado 0
    * @param max_dis Distancia máxima de exploración, unidad mm
    * @param ft Umbral de fuerza/par de terminación de la acción, fx,fy,fz,tx,ty,tz
    * @return Código de error
    */
    public int FT_FindSurface(int rcs, int dir, int axis, double lin_v, double lin_a, double max_dis, double ft, int strategy)

Ejemplo de código de inserción giratoria del sensor de fuerza del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestMove(Robot robot)
    {
        int rtn=-1;
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3=new JointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4=new JointPos(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3=new DescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4=new DescPose(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double oacc = 100.0;
        double blendT = 0.0;
        double blendR = 0.0;
        int flag = 0;
        int search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, oacc, velAccMode,0,10);
        System.out.printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, oacc, velAccMode);
        System.out.printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos, j1, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos, oacc, -1, velAccMode);
        System.out.printf("circle errcode:%d\n", rtn);
        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        System.out.printf("MoveCart errcode:%d\n", rtn);
        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode,0,10);
        System.out.printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, -1, velAccMode);
        System.out.printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        System.out.printf("circle errcode:%d\n", rtn);
        return 0;
    }

Activación del control de cumplimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Activación del control de cumplimiento
    * @param  [in] p Coeficiente de ajuste de posición o coeficiente de cumplimiento
    * @param  [in] force Umbral de fuerza de activación del cumplimiento, unidad N
    * @return  Código de error
    */   
    int FT_ComplianceStart(double p, double force);

Desactivación del control de cumplimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Desactivación del control de cumplimiento
    * @return  Código de error
    */   
    int FT_ComplianceStop(); 

Ejemplo de código de control de cumplimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestCompliance(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);

        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        int flag = 1;
        int sensor_id = 1;
        Object[] select =new Object[] { 1,1,1,0,0,0 };
        Object[] ft_pid =new Object[] { 0.0005,0.0,0.0,0.0,0.0,0.0 };
        int adj_sign = 0;
        int ILC_sign = 0;
        double max_dis = 100.0;
        double max_ang = 0.0;

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        DescPose  offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);


        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_p1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ft.fx = -10.0;
        ft.fy = -10.0;
        ft.fz = -10.0;
        robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
        double p = 0.00005;
        double force = 30.0;
        int rtn = robot.FT_ComplianceStart(p, force);

        int count = 15;
        while (count>0)
        {
            robot.MoveL(j1, desc_p1, 0, 0, 100.0, 180.0, 100.0, -1.0,0, epos, 0, 1, offset_pos,0,10);
            robot.MoveL(j2, desc_p2, 0, 0, 100.0, 180.0, 100.0, -1.0,0, epos, 0, 0, offset_pos,0,10);
            count -= 1;
        }
        robot.FT_ComplianceStop();
        flag = 0;
        robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);

        robot.CloseRPC();
        return 0;
    }

Inicialización de identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicialización de identificación de carga
    * @return Código de error
    */
    int LoadIdentifyDynFilterInit();

Inicialización de variables de identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicialización de variables de identificación de carga
    * @return Código de error
    */
    int LoadIdentifyDynVarInit();

Programa principal de identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Programa principal de identificación de carga
    * @param [in] joint_torque Par de las articulaciones
    * @param [in] joint_pos Posición de las articulaciones
    * @param [in] t Período de muestreo
    * @return Código de error
    */
    int LoadIdentifyMain(Object[] joint_torque, Object[] joint_pos, double t);

Obtener el resultado de la identificación de carga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el resultado de la identificación de carga
    * @param [in] gain
    * @return List[0]:código de error; List[1] : double weight peso de la carga; List[2]: x centro de masa de la carga X mm; List[3] : y centro de masa de la carga Y mm; List[2]: z centro de masa de la carga Z mm
    */
    List<Number> LoadIdentifyGetResult(Object[] gain);

Ejemplo de código de identificación de carga del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestIdentify(Robot robot)
    {
        int retval = 0;

        retval = robot.LoadIdentifyDynFilterInit();

        retval = robot.LoadIdentifyDynVarInit();

        JointPos posJ = new JointPos(0,0,0,0,0,0);
        DescPose posDec = new DescPose(0,0,0,0,0,0);
        List<Number> joint_toq=new ArrayList<>();
        robot.GetActualJointPosDegree( posJ);
        posJ.J2 = posJ.J2 + 10;
        joint_toq=robot.GetJointTorques(0);

        Object[] gain =new Object[] { 0,0.05,0,0,0,0,0,0.02,0,0,0,0 };
        double weight = 0;
        DescTran load_pos=new DescTran(0,0,0);
        List<Number> num=new ArrayList<>();
        num = robot.LoadIdentifyGetResult(gain);

        robot.CloseRPC();
        return 0;

    }

Arrastre asistido por sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief Arrastre asistido por sensor de fuerza
    * @param [in] status Estado de control, 0-desactivar; 1-activar
    * @param [in] asaptiveFlag Indicador de activación adaptativa, 0-desactivar; 1-activar
    * @param [in] interfereDragFlag Indicador de arrastre en zona de interferencia, 0-desactivar; 1-activar
    * @param [in] ingularityConstraintsFlag Estrategia de puntos singulares, 0-evitar; 1-atravesar
    * @param [in] forceCollisionFlag Indicador de detección de colisión del robot durante el arrastre asistido; 0-desactivar; 1-activar
    * @param [in] M Coeficientes de inercia
    * @param [in] B Coeficientes de amortiguación
    * @param [in] K Coeficientes de rigidez
    * @param [in] F Umbral de fuerza de seis dimensiones para el arrastre
    * @param [in] Fmax Límite máximo de fuerza de arrastre Nm
    * @param [in] Vmax Límite máximo de velocidad de las articulaciones °/s
    * @return Código de error
    */
    int EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag,int ingularityConstraintsFlag, int forceCollisionFlag, Object[] M, Object[] B, Object[] K, Object[] F, double Fmax, double Vmax)

Obtener el estado del interruptor de arrastre del sensor de fuerza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el estado del interruptor de arrastre del sensor de fuerza
    * @return List[0]:código de error; List[1] : dragState estado de control del arrastre asistido por sensor de fuerza, 0-desactivar; 1-activar; List[1] : sixDimensionalDragState estado de control del arrastre asistido de fuerza de seis dimensiones, 0-desactivar; 1-activar
    */
    List<Integer> GetForceAndTorqueDragState();

Apertura automática del sensor de fuerza tras el borrado de errores
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Apertura automática del sensor de fuerza tras el borrado de errores
    * @param [in] status Estado de control, 0-desactivar; 1-activar
    * @return Código de error
    */
    int SetForceSensorDragAutoFlag(int status)

Ejemplo de código de arrastre asistido por sensor de fuerza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestEndForceDragCtrl(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        robot.SetForceSensorDragAutoFlag(1);

        Object[] M =new Object[] { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
        Object[] B =new Object[] { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
        Object[] K =new Object[] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        Object[] F =new Object[] { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };
        robot.EndForceDragControl(1, 0, 0, 0, M, B, K, F, 50, 100);

        robot.Sleep(10000);

        int dragState = 0;
        int sixDimensionalDragState = 0;
        List<Integer> state=new ArrayList<>();
        state=robot.GetForceAndTorqueDragState();

        robot.EndForceDragControl(0, 0, 0, 0, M, B, K, F, 50, 100);
        return 0;
    }

Establecer el interruptor y los parámetros del arrastre mixto de fuerza de seis dimensiones e impedancia de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el interruptor y los parámetros del arrastre mixto de fuerza de seis dimensiones e impedancia de articulaciones
    * @param [in] status Estado de control, 0-desactivar; 1-activar
    * @param [in] impedanceFlag Indicador de activación de impedancia, 0-desactivar; 1-activar
    * @param [in] lamdeGain Ganancia de arrastre
    * @param [in] KGain Ganancia de rigidez
    * @param [in] BGain Ganancia de amortiguación
    * @param [in] dragMaxTcpVel Límite máximo de velocidad lineal del extremo durante el arrastre
    * @param [in] dragMaxTcpOriVel Límite máximo de velocidad angular del extremo durante el arrastre
    * @return Código de error
    */
    int ForceAndJointImpedanceStartStop(int status, int impedanceFlag, Object[] lamdeGain, Object[] KGain, Object[] BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Ejemplo de código de arrastre mixto de fuerza de seis dimensiones e impedancia de articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestForceAndJointImpedance(Robot robot)
    {
        robot.DragTeachSwitch(1);
        Object[] lamdeDain =new Object[] { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
        Object[] KGain = new Object[]{ 0, 0, 0, 0, 0, 0 };
        Object[] BGain =new Object[] { 150, 150, 150, 5.0, 5.0, 1.0 };
        int rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lamdeDain, KGain, BGain, 1000.0, 180.0);

        robot.Sleep(10000);

        robot.DragTeachSwitch(0);
        rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lamdeDain, KGain, BGain, 1000.0, 180.0);

        robot.CloseRPC();
        return 0;
    }

Control de inicio/parada de impedancia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Control de inicio/parada de impedancia
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
    public int ImpedanceControlStartStop(int status, int workSpace, double[] forceThreshold, double[] m, double[] b, double[] k, double maxV, double maxVA, double maxW, double maxWA)


Ejemplo de código de control de inicio/parada de impedancia del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestImpedanceControl(Robot robot)
    {
        JointPos j1=new JointPos(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
        JointPos j2=new JointPos(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
        DescPose desc_pos1=new DescPose(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
        DescPose desc_pos2=new DescPose(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 200.0;
        double ovl = 100.0;
        double blendT = -1.0;
        double blendR = -1.0;
        int flag = 0;
        int search = 0;
        robot.SetSpeed(20);
        int company = 17;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        System.out.println("FT config:"+con.company+","+con.device+","+con.softwareVersion+"con"+ con.bus);
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
        double[] forceThreshold = { 30,30,30,5,5,5 };
        double[] m= { 0.1,0.1,0.1,0.02,0.02,0.02 };
        double[] b = { 1,1,1,0.08,0.08,0.08 };
        double[] k = { 0,0,0,0,0,0 };
        int rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        System.out.println("ImpedanceControlStartStop errcode:"+ rtn);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        System.out.println("movel errcode:"+ rtn);
        robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        robot.CloseRPC();
        return 0;
    }

Activar la función de compensación de par y los coeficientes de compensación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Activar la función de compensación de par y los coeficientes de compensación
    * @param  status Interruptor, 0-desactivar; 1-activar
    * @param  torqueCoeff Coeficientes de compensación de par J1-J6 [0-1]
    * @return Código de error
    */
    public int SetCoderCompenParams(int status, double[] torqueCoeff)