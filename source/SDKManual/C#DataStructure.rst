Descripción de las estructuras de datos
==============================================

.. toctree:: 
    :maxdepth: 5

Tipo de datos de posición de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Tipo de datos de posición de articulaciones 
    */  
    struct JointPos
    {
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jPos;   /* Posición de las seis articulaciones, unidad deg */
    }

Tipo de datos de posición en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Tipo de datos de posición en el espacio cartesiano
    */
    struct DescTran
    {
        public double x;    /* Coordenada del eje x, unidad mm  */
        public double y;    /* Coordenada del eje y, unidad mm  */
        public double z;    /* Coordenada del eje z, unidad mm  */
    }

Tipo de datos de orientación en ángulos de Euler
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Tipo de datos de orientación en ángulos de Euler
    */
    struct Rpy
    {
    public double rx;   /* Ángulo de rotación alrededor del eje fijo X, unidad: deg  */
    public double ry;   /* Ángulo de rotación alrededor del eje fijo Y, unidad: deg  */
    public double rz;   /* Ángulo de rotación alrededor del eje fijo Z, unidad: deg  */
    }

Tipo de datos de pose en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    *@brief Tipo de pose en el espacio cartesiano
    */
    struct DescPose
    {
        public DescTran tran;     /* Posición en el espacio cartesiano  */
        public Rpy rpy;			/* Orientación en el espacio cartesiano  */
    }

Tipo de datos de posición de eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Tipo de datos de posición de eje extendido
    */
    struct ExaxisPos
    {
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public double[] ePos;   /* Posición de los cuatro ejes extendidos, unidad mm */
    }

Tipo de datos del sensor de par
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Componentes de fuerza y componentes de par del sensor de fuerza
    */
    struct ForceTorque
    {
        public double fx;  /* Componente de fuerza a lo largo del eje x, unidad N  */
        public double fy;  /* Componente de fuerza a lo largo del eje y, unidad N  */
        public double fz;  /* Componente de fuerza a lo largo del eje z, unidad N  */
        public double tx;  /* Componente de par alrededor del eje x, unidad Nm */
        public double ty;  /* Componente de par alrededor del eje y, unidad Nm */
        public double tz;  /* Componente de par alrededor del eje z, unidad Nm */
    }

Tipo de datos de parámetros de hélice
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public struct SpiralParam
    {
        public int circle_num;           /* Número de vueltas de la hélice  */
        public float circle_angle;         /* Ángulo de inclinación de la hélice  */
        public float rad_init;             /* Radio inicial de la hélice, unidad mm  */
        public float rad_add;              /* Incremento de radio  */
        public float rotaxis_add;          /* Incremento de dirección del eje de rotación  */
        public uint rot_direction;  /* Dirección de rotación, 0-horario, 1-antihorario  */
        public int velAccMode;      // Modo de parámetros de velocidad y aceleración: 0-velocidad angular constante; 1-velocidad lineal constante
        public SpiralParam(int num, float angle, float initRad, float addRad, float axisAdd, uint direction, int mode)
        {
            circle_num = num;
            circle_angle = angle;
            rad_init = initRad;
            rad_add = addRad;
            rotaxis_add = axisAdd;
            rot_direction = direction;
            velAccMode = mode;
        }
    }

Tipo de estado de eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief  Tipo de estado de eje extendido
    */
    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public struct ROBOT_AUX_STATE
    {
        public byte servoId;           //Número de ID del accionamiento servo
        public int servoErrCode;       //Código de fallo del accionamiento servo
        public int servoState;         //Estado del accionamiento servo
        public double servoPos;        //Posición actual del servo
        public float servoVel;         //Velocidad actual del servo
        public float servoTorque;      //Par actual del servo
    }

Estado de interrupción de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public struct WELDING_BREAKOFF_STATE
    {
        public byte breakOffState;  // Estado de interrupción de soldadura
        public byte weldArcState;   // Estado de interrupción del arco de soldadura
    }

Tipo de estructura de retroalimentación de estado del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Tipo de estructura de retroalimentación de estado del robot
    */
    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public class ROBOT_STATE_PKG
    {
        public UInt16 frame_head;           //Cabecera de trama 0x5A5A
        public byte frame_cnt;              // Contador de trama
        public UInt16 data_len;             //Longitud de datos  5
        public byte program_state;          // Estado de ejecución del programa, 1-detendido; 2-en ejecución; 3-en pausa;
        public byte robot_state;            // Estado de movimiento del robot, 1-detendido; 2-en ejecución; 3-en pausa; 4-arrastre
        public int main_code;               // Código de fallo principal
        public int sub_code;                // Código de fallo secundario
        public byte robot_mode;             // Modo del robot, 1-modo manual; 0-modo automático;

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_pos;         // Posición articular actual de los 6 ejes, unidad deg
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] tl_cur_pos;         // Posición actual de la herramienta
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] flange_cur_pos;     // Posición actual de la brida del extremo
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qd;          // Velocidad actual de las 6 articulaciones, unidad deg/s
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qdd;         // Aceleración actual de las 6 articulaciones, unidad deg/s^2
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] target_TCP_CmpSpeed;// Velocidad compuesta de instrucción TCP (posición, orientación)
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] target_TCP_Speed;   // Velocidad de instrucción TCP
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] actual_TCP_CmpSpeed;// Velocidad compuesta real TCP
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_TCP_Speed;   // Velocidad real TCP
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_tor;         // Par actual de las 6 articulaciones, unidad N·m

        public int tool;                    // Número del sistema de coordenadas de herramienta aplicado
        public int user;                    // Número del sistema de coordenadas de pieza aplicado
        public byte cl_dgt_output_h;        // Salida IO digital del armario de control 15-8
        public byte cl_dgt_output_l;        // Salida IO digital del armario de control 7-0
        public byte tl_dgt_output_l;        // Salida IO digital de la herramienta 7-0, solo bit0-bit1 válidos
        public byte cl_dgt_input_h;         // Entrada IO digital del armario de control 15-8
        public byte cl_dgt_input_l;         // Entrada IO digital del armario de control 7-0
        public byte tl_dgt_input_l;         // Entrada IO digital de la herramienta 7-0, solo bit0-bit1 válidos

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public UInt16[] cl_analog_input;        //Entrada analógica del armario de control
        public UInt16 tl_anglog_input;          //Entrada analógica de la herramienta                            

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_raw_data; // Datos brutos del sensor de par
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_data;     // Datos del sensor de par
        public byte ft_sensor_active;       // Estado de activación del sensor de par, 0-restablecer, 1-activar

        public byte EmergencyStop;          // Indicador de parada de emergencia, 0-no pulsado, 1-pulsado
        public int motion_done;             // Señal de movimiento en posición, 1-en posición, 0-no en posición
        public byte gripper_motiondone;     // Señal de movimiento completado de la pinza, 0-no completado, 1-completado (no se detecta objeto), 2-movimiento completado (se detecta objeto)
        public int mc_queue_len;            // Longitud de la cola de instrucciones de movimiento
        public byte collisionState;         // Detección de colisión, 1-colisión, 0-sin colisión
        public int trajectory_pnum;         // Número del punto de trayectoria
        public byte safety_stop0_state;     // Señal de parada de seguridad SI0
        public byte safety_stop1_state;     // Señal de parada de seguridad SI1
        public byte gripper_fault_id;       // Número de pinza con error
        public UInt16 gripper_fault;     /* Fallo de pinza 0-sin fallo 1-tiempo de espera agotado 485 2-error de instrucción 3-caída de pieza otros-código de fallo de pinza+3 */
        public UInt16 gripper_active;    /* Estado de activación de la pinza */
        public byte gripper_position;       // Posición de la pinza
        public byte gripper_speed;       /* Velocidad de la pinza */
        public byte gripper_current;     /* Corriente de la pinza */
        public int gripper_temp;            // Temperatura de la pinza
        public int gripper_voltage;         // Tensión de la pinza

        public ROBOT_AUX_STATE auxState;   // Estado del eje extendido 485

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public EXT_AXIS_STATUS[] extAxisStatus; // Estado del eje extendido UDP

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDIState;        //Entrada DI extendida
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDOState;        //Salida DO extendida
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAIState;        //Entrada AI extendida
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAOState;        //Salida AO extendida

        public int rbtEnableState;          // Estado de habilitación del robot

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTorque;      // Par del accionamiento de las articulaciones del robot
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTemperature; // Temperatura del accionamiento de las articulaciones del robot

        public ROBOT_TIME robotTime;        // Hora del sistema del robot
        public int softwareUpgradeState;    // Estado de actualización del software del robot
        public UInt16 endLuaErrCode;    //Estado de ejecución del LUA del extremo 

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public  UInt16[] cl_analog_output;  //Salida analógica del armario de control				  Control box analog output
        public UInt16 tl_analog_output;     //Salida analógica de la herramienta				  Tool analog output

        public float gripperRotNum;         // Número de vueltas actuales de la pinza rotativa
        public byte gripperRotSpeed;        // Porcentaje de velocidad de rotación actual de la pinza rotativa
        public byte gripperRotTorque;       // Porcentaje de par de rotación actual de la pinza rotativa

        public WELDING_BREAKOFF_STATE weldingBreakOffState; // Estado de interrupción de soldadura

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_tgt_tor;         // Par de instrucción de las articulaciones
        public int smartToolState;          // Estado de los botones del mango SmartTool
        public float wideVoltageCtrlBoxTemp; // Temperatura del armario de control de tensión amplia
        public UInt16 wideVoltageCtrlBoxFanVel;   //Corriente del ventilador del armario de control de tensión amplia (mA)

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] toolCoord;          // Valor del sistema de coordenadas de herramienta actual; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] wobjCoord;          // Valor del sistema de coordenadas de pieza actual; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] extoolCoord;        // Valor del sistema de coordenadas de herramienta externa actual; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] exAxisCoord;        // Valor del sistema de coordenadas del eje extendido actual; x,y,z,rx,ry,rz

        public double load;                 // Masa de la carga
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 3)]
        public double[] loadCog;            // Centro de gravedad de la carga
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] lastServoTarget;    // Posición objetivo del último ServoJ en la cola
        public int servoJCmdNum;            // Contador de instrucciones servoJ

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointPos;     // Posición de instrucción de las 6 articulaciones, unidad °
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointVel;     // Velocidad de instrucción de las 6 articulaciones, unidad °/s
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointAcc;     // Aceleración de instrucción de las 6 articulaciones, unidad °/s²
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointCurrent; // Corriente de instrucción de las 6 articulaciones, unidad A
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actualJointCurrent; // Corriente actual de las 6 articulaciones, unidad A
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actualTCPForce;     // Par del extremo del robot Nm; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetTCPPos;       // Posición de instrucción TCP del robot mm; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] collisionLevel;       // Nivel de colisión del robot

        public double speedScaleManual;     // Porcentaje de velocidad global en modo manual
        public double speedScaleAuto;       // Porcentaje de velocidad global en modo automático
        public int luaLineNum;              // Número de línea actual en ejecución del programa lua
        public byte abnomalStop;            // 0-sin anomalía; 1-con anomalía

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 256)]
        public byte[] currentLuaFileName;   // Nombre del programa lua en ejecución actual
        public byte programTotalLine;       // Número total de líneas del programa lua
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] safetyBoxSingal;      // Estado de los botones de la caja de botones del robot

        public double weldVoltage;          // Tensión de soldadura V
        public double weldCurrent;          // Corriente de soldadura
        public double weldTrackVel;         // Velocidad de seguimiento de soldadura mm/s

        public byte tpdException;           // Número de trayectorias TPD cargadas fuera de límite, 0-no fuera de límite, 1-fuera de límite
        public byte alarmRebootRobot;       // Advertencia, 1-suelte el botón de parada de emergencia y apague y reinicie el armario de control, 2-comunicación anómala de articulaciones, apague y reinicie el armario de control
        public byte modbusMasterConnect;    // bit0-bit7 corresponden al estado de conexión de los maestros 0-7 de ModbusTCP  0-no conectado   1-conectado
        public byte modbusSlaveConnect;     // Estado de conexión del esclavo ModbusTCP 0-no conectado; 1-conectado
        public byte btnBoxStopSignal;       // Señal de parada de emergencia de la caja de botones, 0-soltar parada de emergencia; 1-pulsar parada de emergencia
        public byte dragAlarm;              // Advertencia de arrastre, actualmente en modo automático, 0-sin alarma, 1-alarma , 2-anomalía de retroalimentación de posición, no cambia
        public byte safetyDoorAlarm;        // Advertencia de puerta de seguridad; 0-puerta de seguridad cerrada; 1-puerta de seguridad abierta
        public byte safetyPlaneAlarm;       // Advertencia de entrada en la pared de seguridad; 0-no ha entrado en la pared de seguridad; 1-ha entrado en la pared de seguridad
        public byte motonAlarm;             // Advertencia de movimiento
        public byte interfaceAlarm;         // Advertencia de entrada en la zona de interferencia
        public int udpCmdState;             // Estado de conexión de comunicación UDP del puerto 20007
        public byte weldReadyState;         // Estado de preparación completada de la soldadora
        public byte alarmCheckEmergStopBtn; // 0-normal; 1-comunicación anómala, compruebe si el botón de parada de emergencia está suelto
        public byte tsTmCmdComError;        // 0-normal; 1-fallo de comunicación de instrucción de par
        public byte tsTmStateComError;      // 0-normal; 1-fallo de comunicación de estado de par
        public int ctrlBoxError;            // Error del armario de control
        public byte safetyDataState;        // Indicador de estado de los datos de seguridad, 0-normal, 1-anomalía
        public byte forceSensorErrState;    // Fallo por tiempo de espera agotado en la conexión del sensor de fuerza; bit0-bit1 corresponden a los ID de sensor de fuerza ID1-ID2

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public byte[] ctrlOpenLuaErrCode;   // Códigos de error del protocolo de periféricos del controlador (código de error 500)

        public byte strangePosFlag;         // Indicador de posición singular actual; 0-normal; 1-posición singular
        public byte alarm;                  // Advertencia
        public byte driverAlarm;            // Número de eje con alarma del accionamiento
        public byte aliveSlaveNumError;     // Error del número de esclavos activos, 0: normal; 1: número incorrecto

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public byte[] slaveComError;        // Error del esclavo, 0: normal; 1: esclavo desconectado; 2: estado del esclavo inconsistente con el valor configurado; 3: esclavo no configurado; 4: error de configuración del esclavo; 5: error de inicialización del esclavo; 6: error de inicialización de la comunicación por buzón del esclavo

        public byte cmdPointError;          // Error del punto de instrucción
        public byte IOError;                // Error de IO
        public byte gripperError;           // Error de la pinza
        public byte fileError;              // Error de archivo
        public byte paraError;              // Error de parámetros
        public byte exaxisOutLimitError;    // Error de superación del límite software del eje externo

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] driverComError;       // Fallo de comunicación con el accionamiento
        public byte driverError;            // Número de eje con fallo de comunicación del accionamiento
        public byte outSoftLimitError;      // Fallo por superación del límite software

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 130)]
        public byte[] axleGenComData;       // Datos de retroalimentación de transmisión transparente del extremo del robot

        public byte socketConnTimeout;     // Indicador de tiempo de espera agotado en la conexión socket
        public byte socketReadTimeout;     // Indicador de tiempo de espera agotado en la lectura socket
        public byte tsWebStateComErr;      // ts_web_state_com_err
        public byte exaxisCoordID;         //Número del sistema de coordenadas del eje extendido
        public byte programRunState;       //Estado de ejecución del programa LUA 0-programa no en ejecución; 1-programa en ejecución (incluye pausa del programa)
        public UInt16 check_sum;         /* Suma de verificación */                 

        // Constructor: inicializa todos los campos de tipo array
        public ROBOT_STATE_PKG()
        {
            jt_cur_pos = new double[6];
            tl_cur_pos = new double[6];
            flange_cur_pos = new double[6];
            actual_qd = new double[6];
            actual_qdd = new double[6];
            target_TCP_CmpSpeed = new double[2];
            target_TCP_Speed = new double[6];
            actual_TCP_CmpSpeed = new double[2];
            actual_TCP_Speed = new double[6];
            jt_cur_tor = new double[6];
            cl_analog_input = new ushort[2];
            ft_sensor_raw_data = new double[6];
            ft_sensor_data = new double[6];
            extAxisStatus = new EXT_AXIS_STATUS[4];
            extDIState = new ushort[8];
            extDOState = new ushort[8];
            extAIState = new ushort[4];
            extAOState = new ushort[4];
            jointDriverTorque = new double[6];
            jointDriverTemperature = new double[6];
            cl_analog_output = new ushort[2];
            jt_tgt_tor = new double[6];
            toolCoord = new double[6];
            wobjCoord = new double[6];
            extoolCoord = new double[6];
            exAxisCoord = new double[6];
            loadCog = new double[3];
            lastServoTarget = new double[6];
            targetJointPos = new double[6];
            targetJointVel = new double[6];
            targetJointAcc = new double[6];
            targetJointCurrent = new double[6];
            actualJointCurrent = new double[6];
            actualTCPForce = new double[6];
            targetTCPPos = new double[6];
            collisionLevel = new byte[6];
            currentLuaFileName = new byte[256];
            safetyBoxSingal = new byte[6];
            ctrlOpenLuaErrCode = new byte[4];
            slaveComError = new byte[8];
            driverComError = new byte[6];
            axleGenComData = new byte[130];
        }
    }

Enumeración de configuración de retroalimentación de estado del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Enumeración de estados configurables del robot, rango 0~132
    */
    public enum RobotState
    {
        FrameHead = 0,
        FrameCnt = 1,
        DataLen = 2,
        ProgramState = 3,
        RobotState = 4,
        MainCode = 5,
        SubCode = 6,
        RobotMode = 7,
        JointCurPos = 8,
        ToolCurPos = 9,
        FlangeCurPos = 10,
        ActualJointVel = 11,
        ActualJointAcc = 12,
        TargetTCPCmpSpeed = 13,
        TargetTCPSpeed = 14,
        ActualTCPCmpSpeed = 15,
        ActualTCPSpeed = 16,
        ActualJointTorque = 17,
        Tool = 18,
        User = 19,
        ClDgtOutputH = 20,
        ClDgtOutputL = 21,
        TlDgtOutputL = 22,
        ClDgtInputH = 23,
        ClDgtInputL = 24,
        TlDgtInputL = 25,
        ClAnalogInput = 26,
        TlAnglogInput = 27,
        FtSensorRawData = 28,
        FtSensorData = 29,
        FtSensorActive = 30,
        EmergencyStop = 31,
        MotionDone = 32,
        GripperMotiondone = 33,
        McQueueLen = 34,
        CollisionState = 35,
        TrajectoryPnum = 36,
        SafetyStop0State = 37,
        SafetyStop1State = 38,
        GripperFaultId = 39,
        GripperFault = 40,
        GripperActive = 41,
        GripperPosition = 42,
        GripperSpeed = 43,
        GripperCurrent = 44,
        GripperTemp = 45,
        GripperVoltage = 46,
        AuxState = 47,
        ExtAxisStatus = 48,
        ExtDIState = 49,
        ExtDOState = 50,
        ExtAIState = 51,
        ExtAOState = 52,
        RbtEnableState = 53,
        JointDriverTorque = 54,
        JointDriverTemperature = 55,
        RobotTime = 56,
        SoftwareUpgradeState = 57,
        EndLuaErrCode = 58,
        ClAnalogOutput = 59,
        TlAnalogOutput = 60,
        GripperRotNum = 61,
        GripperRotSpeed = 62,
        GripperRotTorque = 63,
        WeldingBreakOffState = 64,
        TargetJointTorque = 65,
        SmartToolState = 66,
        WideVoltageCtrlBoxTemp = 67,
        WideVoltageCtrlBoxFanCurrent = 68,
        ToolCoord = 69,
        WobjCoord = 70,
        ExtoolCoord = 71,
        ExAxisCoord = 72,
        Load = 73,
        LoadCog = 74,
        LastServoTarget = 75,
        ServoJCmdNum = 76,
        TargetJointPos = 77,
        TargetJointVel = 78,
        TargetJointAcc = 79,
        TargetJointCurrent = 80,
        ActualJointCurrent = 81,
        ActualTCPForce = 82,
        TargetTCPPos = 83,
        CollisionLevel = 84,
        SpeedScaleManual = 85,
        SpeedScaleAuto = 86,
        LuaLineNum = 87,
        AbnomalStop = 88,
        CurrentLuaFileName = 89,
        ProgramTotalLine = 90,
        SafetyBoxSingal = 91,
        WeldVoltage = 92,
        WeldCurrent = 93,
        WeldTrackVel = 94,
        TpdException = 95,
        AlarmRebootRobot = 96,
        ModbusMasterConnect = 97,
        ModbusSlaveConnect = 98,
        BtnBoxStopSignal = 99,
        DragAlarm = 100,
        SafetyDoorAlarm = 101,
        SafetyPlaneAlarm = 102,
        MotonAlarm = 103,
        InterfaceAlarm = 104,
        UdpCmdState = 105,
        WeldReadyState = 106,
        AlarmCheckEmergStopBtn = 107,
        TsTmCmdComError = 108,
        TsTmStateComError = 109,
        CtrlBoxError = 110,
        SafetyDataState = 111,
        ForceSensorErrState = 112,
        CtrlOpenLuaErrCode = 113,
        StrangePosFlag = 114,
        Alarm = 115,
        DriverAlarm = 116,
        AliveSlaveNumError = 117,
        SlaveComError = 118,
        CmdPointError = 119,
        IOError = 120,
        GripperError = 121,
        FileError = 122,
        ParaError = 123,
        ExaxisOutLimitError = 124,
        DriverComError = 125,
        DriverError = 126,
        OutSoftLimitError = 127,
        AxleGenComData = 128,
        SocketConnTimeout = 129,     //tiempo de espera agotado en la conexión socket, bit0-bit4: socketID 1-4
        SocketReadTimeout = 130,     //tiempo de espera agotado en la lectura socket, bit0-bit4: socketID 1-4
        TsWebStateComErr = 131,     //web-fallo de comunicación de par; 0-normal; 1-fallo
        ExaxisCoordID = 132          //Número del sistema de coordenadas del eje extendido
        programRunState = 133       //Estado de ejecución del programa LUA 0-programa no en ejecución; 1-programa en ejecución (incluye pausa del programa)
    }