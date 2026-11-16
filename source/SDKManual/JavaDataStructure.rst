Descripción de las estructuras de datos
========================================

.. toctree:: 
    :maxdepth: 5

Tipo de dato de posición de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Tipo de dato de posición de articulaciones 
    */  
    public class JointPos
    {
      double J1;
      double J2;
      double J3;
      double J4;
      double J5;
      double J6;

      public JointPos(double j1, double j2, double j3, double j4, double j5, double j6)
      {
        J1 = j1;
        J2 = j2;
        J3 = j3;
        J4 = j4;
        J5 = j5;
        J6 = j6;
      }

      public JointPos()
      {

      }
    }

Tipo de dato de posición en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Tipo de dato de posición en el espacio cartesiano
    */
    public class DescTran
    {
      public double x = 0.0;    /* Coordenada del eje x, unidad mm  */
      public double y = 0.0;    /* Coordenada del eje y, unidad mm  */
      public double z = 0.0;    /* Coordenada del eje z, unidad mm  */
      public DescTran(double posX, double posY, double posZ)
      {
        x = posX;
        y = posY;
        z = posZ;
      }

      public DescTran()
      {

      }

    }

Tipo de dato de orientación en ángulos de Euler
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Tipo de dato de orientación en ángulos de Euler
    */
    public class Rpy
    {
      public double rx = 0.0;   /* Ángulo de rotación alrededor del eje fijo X, unidad: deg  */
      public double ry = 0.0;   /* Ángulo de rotación alrededor del eje fijo Y, unidad: deg  */
      public double rz = 0.0;   /* Ángulo de rotación alrededor del eje fijo Z, unidad: deg  */
      public Rpy(double rotateX, double rotateY, double rotateZ)
      {
        rx = rotateX;
        ry = rotateY;
        rz = rotateZ;
      }
    }

Tipo de dato de pose en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    *@brief Tipo de pose en el espacio cartesiano
    */
    public class DescPose
    {
      public DescTran tran = new DescTran(0.0, 0.0, 0.0);      /* Posición en el espacio cartesiano  */
      public Rpy rpy = new Rpy(0.0, 0.0, 0.0);			       /* Orientación en el espacio cartesiano  */

      public DescPose()
      {

      }

      public DescPose(DescTran descTran, Rpy rotateRpy)
      {
        tran = descTran;
        rpy = rotateRpy;
      }

      public DescPose(double tranX, double tranY, double tranZ, double rX, double ry, double rz)
      {
        tran.x = tranX;
        tran.y = tranY;
        tran.z = tranZ;
        rpy.rx = rX;
        rpy.ry = ry;
        rpy.rz = rz;
      }

      public String toString()
      {
        return String.valueOf(tran.x) + "," +  String.valueOf(tran.y) + "," +String.valueOf(tran.z) + "," +String.valueOf(rpy.rx) + "," +String.valueOf(rpy.ry) + "," +String.valueOf(rpy.rz);
      }
    }

Tipo de dato de posición del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Tipo de dato de posición del eje extendido
    */
    public class ExaxisPos
    {
      public double axis1 = 0.0;
      public double axis2 = 0.0;
      public double axis3 = 0.0;
      public double axis4 = 0.0;

      public ExaxisPos()
      {

      }
      public ExaxisPos(double[] exaxisPos)
      {
        axis1 = exaxisPos[0];
        axis2 = exaxisPos[1];
        axis3 = exaxisPos[2];
        axis4 = exaxisPos[3];
      }

      public ExaxisPos(double pos1, double pos2, double pos3, double pos4)
      {
        axis1 = pos1;
        axis2 = pos2;
        axis3 = pos3;
        axis4 = pos4;
      }
    }

Tipo de dato del sensor de par
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Componentes de fuerza y componentes de par del sensor de fuerza
    */
    public class ForceTorque
    {
      public double fx;  /* Componente de fuerza a lo largo del eje x, unidad N  */
      public double fy;  /* Componente de fuerza a lo largo del eje y, unidad N  */
      public double fz;  /* Componente de fuerza a lo largo del eje z, unidad N  */
      public double tx;  /* Componente de par alrededor del eje x, unidad Nm */
      public double ty;  /* Componente de par alrededor del eje y, unidad Nm */
      public double tz;  /* Componente de par alrededor del eje z, unidad Nm */
      public ForceTorque(double fX, double fY, double fZ, double tX, double tY, double tZ)
      {
        fx = fX;
        fy = fY;
        fz = fZ;
        tx = tX;
        ty = tY;
        tz = tZ;
      }
    }

Tipo de dato de parámetros de hélice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Tipo de dato de parámetros de hélice
    */
    public class SpiralParam
    {
        public int circle_num;           /* Número de vueltas de la hélice  */
        public double circle_angle;         /* Ángulo de inclinación de la hélice  */
        public double rad_init;             /* Radio inicial de la hélice, unidad mm  */
        public double rad_add;              /* Incremento de radio  */
        public double rotaxis_add;          /* Incremento de dirección del eje de rotación  */
        public int rot_direction;  /* Dirección de rotación, 0-sentido horario, 1-sentido antihorario  */
        public int velAccMode;     /* Modo de parámetros de velocidad y aceleración: 0-velocidad angular constante; 1-velocidad lineal constante */
        public SpiralParam(int circleNum, double circleAngle, double radInit, double radAdd, double rotaxisAdd, int rotDirection,int vel_AccMode)
        {
            circle_num = circleNum;
            circle_angle = circleAngle;
            rad_init = radInit;
            rad_add = radAdd;
            rotaxis_add = rotaxisAdd;
            rot_direction = rotDirection;
            velAccMode=vel_AccMode;
        }
    }

Tipo de estado del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Tipo de estado del eje extendido
    */
    public class EXT_AXIS_STATUS
    {
     public double pos = 0;        //Posición del eje extendido
     public double vel = 0;        //Velocidad del eje extendido
     public int errorCode = 0;     //Código de fallo del eje extendido
     public int ready = 0;        //Servo preparado
     public int inPos = 0;        //Servo en posición
     public int alarm = 0;        //Alarma del servo
     public int flerr = 0;        //Error de seguimiento
     public int nlimit = 0;       //Límite negativo alcanzado
     public int pLimit = 0;       //Límite positivo alcanzado
     public int mdbsOffLine = 0;  //Desconexión del bus 485 del accionamiento
     public int mdbsTimeout = 0;  //Tiempo de espera agotado en la comunicación 485 entre la tarjeta de control y la caja de control
     public int homingStatus = 0; //Estado de retorno a cero del eje extendido
    }

Tipo de sensor
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Tipo de sensor
    */
    public class DeviceConfig
    {
      int company = 0;          // Fabricante
      int device = 0;           // Tipo/número de dispositivo
      int softwareVersion = 0;  // Versión de software
      int bus = 0;              // Posición de montaje

      public DeviceConfig()
      {

      }

      public DeviceConfig(int company, int device, int softwareVersion, int bus)
      {
        this.company = company;
        this.device = device;
        this.softwareVersion = softwareVersion;
        this.bus = bus;
      }
    }

Configuración del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Configuración del eje extendido 485
    */
    public class Axis485Param
    {
      int servoCompany;           // Fabricante del servoaccionamiento, 1-Dynatec
      int servoModel;             // Modelo del servoaccionamiento, 1-FD100-750C
      int servoSoftVersion;       // Versión de software del servoaccionamiento, 1-V1.0
      int servoResolution;        // Resolución del codificador
      double axisMechTransRatio;  // Relación de transmisión mecánica

      public Axis485Param(int company, int model, int softVersion, int resolution, double mechTransRatio)
      {
        servoCompany = company;
        servoModel = model;
        servoSoftVersion = softVersion;
        servoResolution = resolution;
        axisMechTransRatio = mechTransRatio;
      }

      public Axis485Param()
      {

      }
    }

Estado del controlador servo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Estado del controlador servo
    */
    public class ROBOT_AUX_STATE
    {
      public int servoId = 0;           //Número de ID del servoaccionamiento
      public int servoErrCode = 0;       //Código de fallo del servoaccionamiento
      public int servoState = 0;         //Estado del servoaccionamiento
      public double servoPos = 0;        //Posición actual del servo
      public float servoVel = 0;         //Velocidad actual del servo
      public float servoTorque = 0;      //Par actual del servo    25
    }

Estado de interrupción de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Estado de interrupción de soldadura
    */
    public class WELDING_BREAKOFF_STATE
    {
      public int breakOffState = 0;  //Estado de interrupción de soldadura
      public int weldArcState = 0;   //Estado de interrupción del arco de soldadura
    }

Parámetros de comunicación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Parámetros de comunicación del eje extendido UDP
    */
    public class WELDING_BREAKOFF_STATE
    {
      public String ip = "192.168.58.88";//Dirección IP
      public int port = 2021;            //Número de puerto
      public int period = 2;             //Período de comunicación (ms, valor predeterminado 2, no modificar este parámetro)
      public int lossPkgTime = 50;       //Tiempo de detección de pérdida de paquetes (ms)
      public int lossPkgNum = 2;         //Número de pérdidas de paquetes
      public int disconnectTime = 100;   //Duración de confirmación de desconexión de comunicación
      public int reconnectEnable = 0;    //Habilitación de reconexión automática tras desconexión de comunicación 0-no habilitar 1-habilitar
      public int reconnectPeriod = 100;  //Intervalo del período de reconexión (ms)
      public int reconnectNum = 3;       //Número de reconexiones
      public int selfConnect =0;         //Si se establece automáticamente la conexión tras reinicio por corte de energía; 0-no establecer conexión; 1-establecer conexión
    }

Tipo de estructura de retroalimentación de estado del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Tipo de estructura de retroalimentación de estado del robot
    * /
    public class ROBOT_STATE_PKG {
        public int frame_head;                      // Cabecera de trama
        public int frame_cnt;                       // Contador de trama
        public int data_len;                        // Longitud de datos
        public int program_state;                   // Estado del programa - 1-detenido; 2-en ejecución; 3-pausado
        public int robot_state;                     // Estado de movimiento del robot - 1-detenido; 2-en ejecución; 3-pausado; 4-arrastre
        public int main_code;                       // Código de fallo principal
        public int sub_code;                        // Código de fallo secundario
        public int robot_mode;                      // Modo del robot - 1-modo manual; 0-modo automático
        public double[] jt_cur_pos = new double[6]; // Posición actual de las 6 articulaciones, unidad deg
        public double[] tl_cur_pos = new double[6]; // Posición actual de la herramienta - [x,y,z,rx,ry,rz]
        public double[] flange_cur_pos = new double[6]; // Posición actual de la brida del extremo - [x,y,z,rx,ry,rz]
        public double[] actual_qd = new double[6];  // Velocidad actual de las 6 articulaciones, unidad deg/s
        public double[] actual_qdd = new double[6]; // Aceleración actual de las 6 articulaciones, unidad deg/s^2
        public double[] target_TCP_CmpSpeed = new double[2]; // Velocidad compuesta de comando del TCP - [posición mm/s, orientación deg/s]
        public double[] target_TCP_Speed = new double[6]; // Velocidad de comando del TCP - [vx,vy,vz,wx,wy,wz]
        public double[] actual_TCP_CmpSpeed = new double[2]; // Velocidad compuesta real del TCP - [posición mm/s, orientación deg/s]
        public double[] actual_TCP_Speed = new double[6]; // Velocidad real del TCP - [vx,vy,vz,wx,wy,wz]
        public double[] jt_cur_tor = new double[6]; // Par actual de las articulaciones
        public int tool;                            // ID de herramienta
        public int user;                            // ID de pieza
        public int cl_dgt_output_h;                 // Byte alto de salida digital del armario de control
        public int cl_dgt_output_l;                 // Byte bajo de salida digital del armario de control
        public int tl_dgt_output_l;                 // Byte bajo de salida digital de la herramienta
        public int cl_dgt_input_h;                  // Byte alto de entrada digital del armario de control
        public int cl_dgt_input_l;                  // Byte bajo de entrada digital del armario de control
        public int tl_dgt_input_l;                  // Byte bajo de entrada digital de la herramienta
        public int[] cl_analog_input = new int[2];  // Entrada analógica del armario de control
        public int tl_anglog_input;                 // Entrada analógica de la herramienta
        public double[] ft_sensor_raw_data = new double[6]; // Datos brutos del sensor de fuerza
        public double[] ft_sensor_data = new double[6]; // Datos del sensor de fuerza
        public int ft_sensor_active;                // Estado de activación del sensor de fuerza
        public int EmergencyStop;                   // Estado de parada de emergencia
        public int motion_done;                     // Movimiento completado
        public int gripper_motiondone;              // Señal de movimiento de la pinza completado, 0-no completado, 1-completado (objeto no detectado), 2-movimiento completado (objeto detectado)
        public int mc_queue_len;                    // Longitud de la cola de movimiento
        public int collisionState;                  // Estado de colisión
        public int trajectory_pnum;                 // Número de punto de trayectoria
        public int safety_stop0_state;              // Estado de parada de seguridad 0
        public int safety_stop1_state;              // Estado de parada de seguridad 1
        public int gripper_fault_id;                // ID de fallo de la pinza
        public int gripper_fault;                   // Fallo de la pinza 0-sin fallo 1-tiempo de espera 485 agotado 2-error de instrucción 3-caída de la pieza otros-código de fallo de la pinza
        public int gripper_active;                  // Activación de la pinza
        public int gripper_position;                // Posición de la pinza
        public int gripper_speed;                   // Velocidad de la pinza
        public int gripper_current;                 // Corriente de la pinza
        public int gripper_temp;                    // Temperatura de la pinza
        public int gripper_voltage;                 // Voltaje de la pinza
        public AuxState aux_state = new AuxState(); // Estado del eje auxiliar interno
        public EXT_AXIS_STATUS[] extAxisStatus = new EXT_AXIS_STATUS[4]; // Arreglo de estado de los ejes extendidos
        public short[] extDIState = new short[8];   // IO extendida
        public short[] extDOState = new short[8];   // IO extendida
        public short[] extAIState = new short[4];   // IO extendida
        public short[] extAOState = new short[4];   // IO extendida
        public int rbtEnableState;                  // Estado de habilitación del robot
        public double[] jointDriverTorque = new double[6]; // Par del accionamiento de las articulaciones
        public double[] jointDriverTemperature = new double[6]; // Temperatura del accionamiento de las articulaciones
        public ROBOT_TIME robotTime = new ROBOT_TIME(); // Objeto de hora del robot
        public int softwareUpgradeState;            // Estado de actualización del software
        public int endLuaErrCode;                   // Código de error de Lua del extremo
        public int[] cl_analog_output = new int[2]; // Salida analógica del armario de control
        public int tl_analog_output;                // Salida analógica de la herramienta
        public float gripperRotNum;                 // Número de vueltas de la pinza giratoria
        public int gripperRotSpeed;                 // Velocidad de la pinza giratoria
        public int gripperRotTorque;                // Par de la pinza giratoria
        public WELDING_BREAKOFF_STATE weldingBreakOffState = new WELDING_BREAKOFF_STATE(); // Estado de interrupción de soldadura
        public double[] jt_tgt_tor = new double[6]; // Par objetivo de las articulaciones
        public int smartToolState;                  // Estado de la herramienta inteligente
        public float wideVoltageCtrlBoxTemp;        // Temperatura de la caja de control de voltaje amplio
        public int wideVoltageCtrlBoxFanCurrent;    // Corriente del ventilador de la caja de control de voltaje amplio
        public double[] toolCoord = new double[6];  // Sistema de coordenadas de herramienta
        public double[] wobjCoord = new double[6];  // Sistema de coordenadas de la pieza
        public double[] extoolCoord = new double[6]; // Sistema de coordenadas de herramienta externa
        public double[] exAxisCoord = new double[6]; // Sistema de coordenadas del eje extendido
        public double load;                         // Carga
        public double[] loadCog = new double[3];    // Centro de gravedad de la carga
        public double[] lastServoTarget = new double[6]; // Última posición objetivo de ServoJ
        public int servoJCmdNum;                    // Número de comandos ServoJ
        public double[] targetJointPos = new double[6]; // Posición objetivo de las articulaciones
        public double[] targetJointVel = new double[6]; // Velocidad objetivo de las articulaciones
        public double[] targetJointAcc = new double[6]; // Aceleración objetivo de las articulaciones
        public double[] targetJointCurrent = new double[6]; // Corriente objetivo de las articulaciones
        public double[] actualJointCurrent = new double[6]; // Corriente real de las articulaciones
        public double[] actualTCPForce = new double[6]; // Fuerza real del TCP
        public double[] targetTCPPos = new double[6]; // Posición objetivo del TCP
        public int[] collisionLevel = new int[6];   // Nivel de colisión
        public double speedScaleManual;              // Proporción de velocidad manual
        public double speedScaleAuto;                // Proporción de velocidad automática
        public int luaLineNum;                       // Número de línea Lua
        public int abnomalStop;                      // Parada anómala
        public String currentLuaFileName;            // Nombre del archivo Lua actual
        public int programTotalLine;                 // Número total de líneas del programa
        public int[] safetyBoxSingal = new int[6];   // Señal de la caja de seguridad
        public double weldVoltage;                   // Voltaje de soldadura
        public double weldCurrent;                   // Corriente de soldadura
        public double weldTrackVel;                  // Velocidad de seguimiento de soldadura
        public int tpdException;                     // Excepción de TPD
        public int alarmRebootRobot;                 // Alarma de reinicio del robot
        public int modbusMasterConnect;              // Conexión de la estación maestra Modbus
        public int modbusSlaveConnect;               // Conexión de la estación esclava Modbus
        public int btnBoxStopSignal;                 // Señal de parada de la caja de botones
        public int dragAlarm;                        // Alarma de arrastre
        public int safetyDoorAlarm;                  // Alarma de puerta de seguridad
        public int safetyPlaneAlarm;                 // Alarma de plano de seguridad
        public int motonAlarm;                       // Alarma de movimiento
        public int interfaceAlarm;                   // Alarma de interferencia
        public int udpCmdState;                      // Estado del comando UDP
        public int weldReadyState;                   // Estado de preparación de soldadura
        public int alarmCheckEmergStopBtn;           // Alarma de verificación del botón de parada de emergencia
        public int tsTmCmdComError;                  // Error de comunicación de comando
        public int tsTmStateComError;                // Error de comunicación de estado
        public int ctrlBoxError;                     // Error de la caja de control
        public int safetyDataState;                  // Estado de los datos de seguridad
        public int forceSensorErrState;              // Estado de error del sensor de fuerza
        public int[] ctrlOpenLuaErrCode = new int[4]; // Código de error de Lua abierto del control
        public int strangePosFlag;                   // Indicador de posición singular
        public int alarm;                            // Alarma
        public int driverAlarm;                      // Alarma del accionamiento
        public int aliveSlaveNumError;               // Error del número de esclavos activos
        public int[] slaveComError = new int[8];     // Error de comunicación de esclavos
        public int cmdPointError;                    // Error del punto de comando
        public int IOError;                          // Error de IO
        public int gripperError;                     // Error de la pinza
        public int fileError;                        // Error de archivo
        public int paraError;                        // Error de parámetro
        public int exaxisOutLimitError;              // Error de eje extendido fuera del límite suave
        public int[] driverComError = new int[6];    // Error de comunicación del accionamiento
        public int driverError;                      // Error del accionamiento
        public int outSoftLimitError;                // Error de fuera del límite suave
        public byte[] axleGenComData = new byte[130]; // Datos de comunicación del eje genérico
        public int check_sum;                        // Suma de verificación
        public int socketConnTimeout;                // Tiempo de espera agotado de conexión del Socket
        public int socketReadTimeout;                // Tiempo de espera agotado de lectura del Socket
        public int tsWebStateComErr;                 // Error de comunicación de estado de TS Web
        public int exaxisCoordID;                  //Número del sistema de coordenadas del eje extendido
        public int programRunState;                  //Estado de ejecución del programa LUA 0-programa no en ejecución; 1-programa en ejecución (incluye programa pausado)

    }

Clase de resultado de configuración de retroalimentación de estado del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * Clase de resultado de configuración de retroalimentación de estado del robot, que contiene la lista de estados y el período
    */
    public static class StateConfigResult {
      public final List<RobotState> stateList;
      public final int period;
    }

Tipo de enumeración de configuración de retroalimentación de estado del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:
    
    /**
    * Tipo de enumeración de estado del robot
    * Utilizado para la configuración de retroalimentación de estado en tiempo real
    */
    enum class RobotState
    {
        ProgramState,           // Estado de ejecución del programa, 1-detenido; 2-en ejecución; 3-pausado
        RobotState,             // Estado de movimiento del robot, 1-detenido; 2-en ejecución; 3-pausado; 4-arrastre
        MainCode,               // Código de fallo principal
        SubCode,                // Código de fallo secundario
        RobotMode,              // Modo del robot, 1-modo manual; 0-modo automático
        JointCurPos,            // Posición actual de las 6 articulaciones, unidad deg
        ToolCurPos,             // Posición actual de la herramienta: [0]posición a lo largo del eje x (mm), [1]a lo largo del eje y (mm), [2]a lo largo del eje z (mm), [3]rotación alrededor del eje fijo X (deg), [4]alrededor del eje fijo Y (deg), [5]alrededor del eje fijo Z (deg)
        FlangeCurPos,          // Posición actual de la brida del extremo: [0]a lo largo del eje x (mm), [1]a lo largo del eje y (mm), [2]a lo largo del eje z (mm), [3]alrededor del eje fijo X (deg), [4]alrededor del eje fijo Y (deg), [5]alrededor del eje fijo Z (deg)
        ActualJointVel,        // Velocidad actual de las 6 articulaciones, unidad deg/s
        ActualJointAcc,        // Aceleración actual de las 6 articulaciones, unidad deg/s^2
        TargetTCPCmpSpeed,     // Velocidad compuesta de comando del TCP: [0]posición (mm/s), [1]orientación (deg/s)
        TargetTCPSpeed,        // Velocidad de comando del TCP: [0]a lo largo del eje x (mm/s), [1]a lo largo del eje y (mm/s), [2]a lo largo del eje z (mm/s), [3]velocidad angular alrededor de X (deg/s), [4]alrededor de Y (deg/s), [5]alrededor de Z (deg/s)
        ActualTCPCmpSpeed,     // Velocidad compuesta real del TCP: [0]posición (mm/s), [1]orientación (deg/s)
        ActualTCPSpeed,        // Velocidad real del TCP: [0]a lo largo del eje x (mm/s), [1]a lo largo del eje y (mm/s), [2]a lo largo del eje z (mm/s), [3]velocidad angular alrededor de X (deg/s), [4]alrededor de Y (deg/s), [5]alrededor de Z (deg/s)
        ActualJointTorque,     // Par actual de las 6 articulaciones, unidad N·m
        Tool,                  // Número del sistema de coordenadas de herramienta aplicado
        User,                  // Número del sistema de coordenadas de la pieza aplicado
        ClDgtOutputH,          // Salida de IO digital de la caja de control 15-8
        ClDgtOutputL,          // Salida de IO digital de la caja de control 7-0
        TlDgtOutputL,          // Salida de IO digital de la herramienta 7-0, solo bit0-bit1 válidos
        ClDgtInputH,           // Entrada de IO digital de la caja de control 15-8
        ClDgtInputL,           // Entrada de IO digital de la caja de control 7-0
        TlDgtInputL,           // Entrada de IO digital de la herramienta 7-0, solo bit0-bit1 válidos
        ClAnalogInput,         // Entrada analógica de la caja de control: [0]canal 0, [1]canal 1
        TlAnalogInput,         // Entrada analógica de la herramienta
        FtSensorRawData,       // Datos brutos del sensor de par: [0]fuerza a lo largo del eje x (N), [1]fuerza a lo largo del eje y (N), [2]fuerza a lo largo del eje z (N), [3]par alrededor del eje x (Nm), [4]alrededor del eje y (Nm), [5]alrededor del eje z (Nm)
        FtSensorData,          // Datos del sensor de par (procesados): [0]fuerza a lo largo del eje x (N), [1]fuerza a lo largo del eje y (N), [2]fuerza a lo largo del eje z (N), [3]par alrededor del eje x (Nm), [4]alrededor del eje y (Nm), [5]alrededor del eje z (Nm)
        FtSensorActive,        // Estado de activación del sensor de par, 0-reiniciado, 1-activado
        EmergencyStop,         // Indicador de parada de emergencia, 0-parada de emergencia no pulsada, 1-parada de emergencia pulsada
        MotionDone,            // Señal de movimiento en posición, 1-en posición, 0-no en posición
        GripperMotiondone,     // Señal de movimiento de la pinza completado, 0-no completado, 1-completado (objeto no detectado), 2-movimiento completado (objeto detectado)
        McQueueLen,            // Longitud de la cola de instrucciones de movimiento
        CollisionState,        // Detección de colisión, 1-colisión, 0-sin colisión
        TrajectoryPnum,        // Número de punto de trayectoria
        SafetyStop0State,      // Señal de parada de seguridad SI0
        SafetyStop1State,      // Señal de parada de seguridad SI1
        GripperFaultId,        // Número de pinza con error
        GripperFault,          // Fallo de la pinza 0-sin fallo 1-tiempo de espera 485 agotado 2-error de instrucción 3-caída de la pieza otros-código de fallo de la pinza
        GripperActive,         // Estado de activación de la pinza
        GripperPosition,       // Posición de la pinza
        GripperSpeed,          // Velocidad de la pinza
        GripperCurrent,        // Corriente de la pinza
        GripperTemp,           // Temperatura de la pinza
        GripperVoltage,        // Voltaje de la pinza
        AuxState,              // Estado del eje extendido 485
        ExtAxisStatus,         // Estado del eje extendido UDP (4 ejes)
        ExtDIState,            // Entrada DI extendida (8)
        ExtDOState,            // Salida DO extendida (8)
        ExtAIState,            // Entrada AI extendida (4)
        ExtAOState,            // Salida AO extendida (4)
        RbtEnableState,        // Estado de habilitación del robot
        JointDriverTorque,     // Par del accionamiento de las articulaciones del robot (6 articulaciones)
        JointDriverTemperature,// Temperatura del accionamiento de las articulaciones del robot (6 articulaciones)
        RobotTime,             // Hora del sistema del robot
        SoftwareUpgradeState,  // Estado de actualización del software del robot
        EndLuaErrCode,         // Estado de ejecución de LUA del extremo
        ClAnalogOutput,        // Salida analógica de la caja de control (2)
        TlAnalogOutput,        // Salida analógica de la herramienta
        GripperRotNum,         // Número de vueltas de rotación actual de la pinza giratoria
        GripperRotSpeed,       // Porcentaje de velocidad de rotación actual de la pinza giratoria
        GripperRotTorque,      // Porcentaje de par de rotación actual de la pinza giratoria
        WeldingBreakOffState,  // Estado de interrupción de soldadura
        TargetJointTorque,     // Par de comando de las articulaciones (6 articulaciones)
        SmartToolState,        // Estado de los botones del mango SmartTool
        WideVoltageCtrlBoxTemp,// Temperatura de la caja de control de voltaje amplio
        WideVoltageCtrlBoxFanCurrent, // Corriente del ventilador de la caja de control de voltaje amplio (mA)
        ToolCoord,             // Valor actual del sistema de coordenadas de herramienta: x,y,z,rx,ry,rz
        WobjCoord,             // Valor actual del sistema de coordenadas de la pieza: x,y,z,rx,ry,rz
        ExtoolCoord,           // Valor actual del sistema de coordenadas de herramienta externa: x,y,z,rx,ry,rz
        ExAxisCoord,           // Valor actual del sistema de coordenadas del eje extendido: x,y,z,rx,ry,rz
        Load,                  // Masa de la carga
        LoadCog,               // Centro de masa de la carga: x,y,z
        LastServoTarget,       // Última posición objetivo de ServoJ en la cola (6 articulaciones)
        ServoJCmdNum,          // Contador de comandos servoJ
        TargetJointPos,        // Posición de comando de las 6 articulaciones, unidad °
        TargetJointVel,        // Velocidad de comando de las 6 articulaciones, unidad °/s
        TargetJointAcc,        // Aceleración de comando de las 6 articulaciones, unidad °/s²
        TargetJointCurrent,    // Corriente de comando de las 6 articulaciones, unidad A
        ActualJointCurrent,    // Corriente actual de las 6 articulaciones, unidad A
        ActualTCPForce,        // Par del extremo del robot: x,y,z,rx,ry,rz, unidad Nm
        TargetTCPPos,          // Posición de comando del TCP del robot: x,y,z,rx,ry,rz, unidad mm
        CollisionLevel,        // Nivel de colisión del robot (6)
        SpeedScaleManual,      // Porcentaje de velocidad global en modo manual
        SpeedScaleAuto,        // Porcentaje de velocidad global en modo automático
        LuaLineNum,            // Número de línea de ejecución actual del programa lua
        AbnomalStop,           // 0-sin anomalía; 1-con anomalía
        CurrentLuaFileName,    // Nombre del programa lua en ejecución actual
        ProgramTotalLine,      // Número total de líneas del programa lua
        SafetyBoxSingal,       // Estado de los botones de la caja de botones del robot (6)
        WeldVoltage,           // Voltaje de soldadura V
        WeldCurrent,           // Corriente de soldadura
        WeldTrackVel,          // Velocidad de seguimiento de soldadura mm/s
        TpdException,          // Cantidad de carga de trayectoria TPD excede el límite, 0-no excede, 1-excede
        AlarmRebootRobot,      // Advertencia: 1-es necesario reiniciar tras liberar la parada de emergencia, 2-es necesario reiniciar tras anomalía de comunicación de articulaciones
        ModbusMasterConnect,   // bit0-7 corresponden al estado de conexión de las estaciones maestras ModbusTCP 0-7, 0-no conectada, 1-conectada
        ModbusSlaveConnect,    // Estado de conexión de la estación esclava ModbusTCP, 0-no conectada, 1-conectada
        BtnBoxStopSignal,      // Señal de parada de emergencia de la caja de botones, 0-parada de emergencia liberada, 1-parada de emergencia pulsada
        DragAlarm,            // Advertencia de arrastre: 0-no alarma, 1-alarma, 2-no cambiar por anomalía de retroalimentación de posición
        SafetyDoorAlarm,      // Advertencia de puerta de seguridad: 0-cerrada, 1-abierta
        SafetyPlaneAlarm,     // Advertencia de muro de seguridad: 0-no entra, 1-entra
        MotonAlarm,           // Advertencia de movimiento
        InterfaceAlarm,       // Advertencia de entrada en zona de interferencia
        UdpCmdState,          // Estado de conexión de comunicación UDP del puerto 20007
        WeldReadyState,       // Estado de preparación completada de la máquina de soldar
        AlarmCheckEmergStopBtn, // 0-normal; 1-anomalía de comunicación, verificar el botón de parada de emergencia
        TsTmCmdComError,      // 0-normal; 1-fallo de comunicación de comando de par
        TsTmStateComError,    // 0-normal; 1-fallo de comunicación de estado de par
        CtrlBoxError,         // Error de la caja de control
        SafetyDataState,      // Estado de los datos de seguridad, 0-normal, 1-anómalo
        ForceSensorErrState,  // Tiempo de espera agotado de conexión del sensor de fuerza, bit0-bit1 corresponden a ID1-ID2
        CtrlOpenLuaErrCode,   // 4 códigos de error de protocolo de periféricos del controlador (código de error 500)
        StrangePosFlag,       // Indicador de pose singular: 0-normal, 1-pose singular
        Alarm,                // Advertencia
        DriverAlarm,          // Número de eje de alarma del accionamiento
        AliveSlaveNumError,   // Error del número de esclavos activos: 0-normal, 1-error de número
        SlaveComError,        // Error de esclavo: 0-normal, 1-desconectado, 2-estado inconsistente, 3-no configurado, 4-error de configuración, 5-error de inicialización, 6-error de inicialización de comunicación de buzón
        CmdPointError,        // Error del punto de comando
        IOError,              // Error de IO
        GripperError,         // Error de la pinza
        FileError,            // Error de archivo
        ParaError,            // Error de parámetro
        ExaxisOutLimitError,  // Error de eje externo fuera del límite suave
        DriverComError,       // Fallo de comunicación con el accionamiento (6 ejes)
        DriverError,          // Número de eje de fallo de comunicación del accionamiento
        OutSoftLimitError,    // Fallo de fuera del límite suave
        AxleGenComData,       // Datos de retroalimentación de transmisión transparente del extremo del robot
        SocketConnTimeout,    // Tiempo de espera agotado de conexión del socket, bit0-bit4 corresponden a socketID 1-4
        SocketReadTimeout,    // Tiempo de espera agotado de lectura del socket, bit0-bit4 corresponden a socketID 1-4
        TsWebStateComErr,     // Fallo de comunicación web-par: 0-normal, 1-fallo
        ExaxisCoordID          //Número del sistema de coordenadas del eje extendido
        programRunState;       //Estado de ejecución del programa LUA 0-programa no en ejecución; 1-programa en ejecución (incluye programa pausado)
    };