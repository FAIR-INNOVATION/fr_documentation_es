Descripción de las estructuras de datos
=======================================

.. toctree:: 
    :maxdepth: 5

Tipo de valor de retorno de las llamadas a la interfaz
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    typedef  int errno_t;

Tipo de datos de posición de articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Tipo de datos de posición de articulaciones
    */
    typedef  struct
    {
        double jPos[6];   /* Posición de las seis articulaciones, unidad deg */
    }JointPos;

Tipo de datos de posición en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Tipo de datos de posición en el espacio cartesiano
    */
    typedef struct
    {
        double x;    /* Coordenada del eje x, unidad mm  */
        double y;    /* Coordenada del eje y, unidad mm  */
        double z;    /* Coordenada del eje z, unidad mm  */
    } DescTran;

Tipo de datos de orientación en ángulos de Euler
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Tipo de datos de orientación en ángulos de Euler
    */
    typedef struct
    {
        double rx;   /* Ángulo de rotación alrededor del eje fijo X, unidad: deg  */
        double ry;   /* Ángulo de rotación alrededor del eje fijo Y, unidad: deg  */
        double rz;   /* Ángulo de rotación alrededor del eje fijo Z, unidad: deg  */
    } Rpy;

Tipo de datos de pose en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    *@brief Tipo de pose en el espacio cartesiano
    */
    typedef struct
    {
        DescTran tran;      /* Posición en el espacio cartesiano  */
        Rpy rpy;            /* Orientación en el espacio cartesiano  */
    } DescPose;

Tipo de datos de posición de eje extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Tipo de datos de posición de eje extendido
    */
    typedef  struct
    {
        double ePos[4];   /* Posición de los cuatro ejes extendidos, unidad mm */
    }ExaxisPos;

Tipo de datos del sensor de par
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Componentes de fuerza y componentes de par del sensor de fuerza
    */
    typedef struct
    {
        double fx;  /* Componente de fuerza a lo largo del eje x, unidad N  */
        double fy;  /* Componente de fuerza a lo largo del eje y, unidad N  */
        double fz;  /* Componente de fuerza a lo largo del eje z, unidad N  */
        double tx;  /* Componente de par alrededor del eje x, unidad Nm */
        double ty;  /* Componente de par alrededor del eje y, unidad Nm */
        double tz;  /* Componente de par alrededor del eje z, unidad Nm */
    } ForceTorque;

Tipo de datos de parámetros de hélice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Tipo de datos de parámetros de hélice
    */
    typedef  struct
    {
        int    circle_num;           /* Número de vueltas de la hélice  */
        float  circle_angle;         /* Ángulo de inclinación de la hélice  */
        float  rad_init;             /* Radio inicial de la hélice, unidad mm  */
        float  rad_add;              /* Incremento de radio  */
        float  rotaxis_add;          /* Incremento de dirección del eje de rotación  */
        int rot_direction;   /* Dirección de rotación, 0-horario, 1-antihorario  */
        int velAccMode;      /* Modo de parámetros de velocidad y aceleración: 0-velocidad angular constante; 1-velocidad lineal constante */
    }SpiralParam;

Paquete de datos de retroalimentación de estado del controlador
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Paquete de datos de retroalimentación de estado del controlador
     */
    typedef struct _ROBOT_STATE_PKG
    {
      uint16_t frame_head;   // Cabecera de trama, acordada como 0x5A5A 
      uint8_t frame_cnt;    // Contador de trama, conteo cíclico 0-255 
      uint16_t data_len;    // Longitud del contenido de datos 
      uint8_t program_state;  // Estado de ejecución del programa, 1-detendido; 2-en ejecución; 3-en pausa;
      uint8_t robot_state;   // Estado de movimiento del robot, 1-detendido; 2-en ejecución; 3-en pausa; 4-arrastre 
      int   main_code;    // Código de fallo principal 
      int   sub_code;    // Código de fallo secundario 
      uint8_t robot_mode;   // Modo del robot, 1-modo manual; 0-modo automático; 
      double  jt_cur_pos[6];  // Posición articular actual de los 6 ejes, unidad deg 
      double  tl_cur_pos[6];  // Posición actual de la herramienta
            // tl_cur_pos[0], posición a lo largo del eje x, unidad mm,
            // tl_cur_pos[1], posición a lo largo del eje y, unidad mm,
            // tl_cur_pos[2], posición a lo largo del eje z, unidad mm,
            // tl_cur_pos[3], ángulo de rotación alrededor del eje fijo X, unidad deg
            // tl_cur_pos[4], ángulo de rotación alrededor del eje fijo y, unidad deg
            // tl_cur_pos[5], ángulo de rotación alrededor del eje fijo z, unidad deg 
      double  flange_cur_pos[6]; // Posición actual de la brida del extremo
            // flange_cur_pos[0], posición a lo largo del eje x, unidad mm,
            // flange_cur_pos[1], posición a lo largo del eje y, unidad mm,
            // flange_cur_pos[2], posición a lo largo del eje z, unidad mm,
            // flange_cur_pos[3], ángulo de rotación alrededor del eje fijo X, unidad deg
            // flange_cur_pos[4], ángulo de rotación alrededor del eje fijo y, unidad deg
            // flange_cur_pos[5], ángulo de rotación alrededor del eje fijo z, unidad deg
      double  actual_qd[6];   // Velocidad actual de las 6 articulaciones, unidad deg/s 
      double  actual_qdd[6];   // Aceleración actual de las 6 articulaciones, unidad deg/s^2 
      double  target_TCP_CmpSpeed[2]; 
            // target_TCP_CmpSpeed[0], velocidad compuesta de instrucción TCP (posición), unidad mm/s
            // target_TCP_CmpSpeed[1], velocidad compuesta de instrucción TCP (orientación), unidad deg/s */
      double  target_TCP_Speed[6];  // Velocidad de instrucción TCP
              // target_TCP_Speed[0], velocidad a lo largo del eje x, unidad mm/s,
              // target_TCP_Speed[1], velocidad a lo largo del eje y, unidad mm/s,
              // target_TCP_Speed[2], velocidad a lo largo del eje z, unidad mm/s,
              // target_TCP_Speed[3], velocidad angular de rotación alrededor del eje fijo X, unidad deg/s
              // target_TCP_Speed[4], velocidad angular de rotación alrededor del eje fijo y, unidad deg/s
              // target_TCP_Speed[5], velocidad angular de rotación alrededor del eje fijo z, unidad deg/s */
      double  actual_TCP_CmpSpeed[2]; 
              // actual_TCP_CmpSpeed[0], velocidad compuesta real TCP (posición), unidad mm/s
              // actual_TCP_CmpSpeed[1], velocidad compuesta real TCP (orientación), unidad deg/s 
      double  actual_TCP_Speed[6];  // Velocidad real TCP
              // actual_TCP_Speed[0], velocidad a lo largo del eje x, unidad mm/s,
              // actual_TCP_Speed[1], velocidad a lo largo del eje y, unidad mm/s,
              // actual_TCP_Speed[2], velocidad a lo largo del eje z, unidad mm/s,
              // actual_TCP_Speed[3], velocidad angular de rotación alrededor del eje fijo X, unidad deg/s
              // actual_TCP_Speed[4], velocidad angular de rotación alrededor del eje fijo y, unidad deg/s
              // actual_TCP_Speed[5], velocidad angular de rotación alrededor del eje fijo z, unidad deg/s 
      double  jt_cur_tor[6];   // Par actual de las 6 articulaciones, unidad N·m 
      int   tool;        // Número del sistema de coordenadas de herramienta aplicado 
      int   user;        // Número del sistema de coordenadas de pieza aplicado 
      uint8_t cl_dgt_output_h;  // Salida IO digital del armario de control 15-8 
      uint8_t cl_dgt_output_l;  // Salida IO digital del armario de control 7-0 
      uint8_t tl_dgt_output_l;  // Salida IO digital de la herramienta 7-0, solo bit0-bit1 válidos 
      uint8_t cl_dgt_input_h;   // Entrada IO digital del armario de control 15-8 
      uint8_t cl_dgt_input_l;   // Entrada IO digital del armario de control 7-0 
      uint8_t tl_dgt_input_l;   // Entrada IO digital de la herramienta 7-0, solo bit0-bit1 válidos 
      uint16_t cl_analog_input[2]; // cl_analog_input[0], entrada analógica del armario de control 0
                    //cl_analog_input[1], entrada analógica del armario de control 1 
      uint16_t tl_anglog_input;  // Entrada analógica de la herramienta 
      double  ft_sensor_raw_data[6]; // Datos brutos del sensor de par
              // ft_sensor_raw_data[0], fuerza a lo largo del eje x, unidad N
              // ft_sensor_raw_data[1], fuerza a lo largo del eje y, unidad N
              // ft_sensor_raw_data[2], fuerza a lo largo del eje z, unidad N
              // ft_sensor_raw_data[3], par alrededor del eje x, unidad Nm
              // ft_sensor_raw_data[4], par alrededor del eje y, unidad Nm
              // ft_sensor_raw_data[5], par alrededor del eje z, unidad Nm 
      double  ft_sensor_data[6];   // Datos del sensor de par,
              // ft_sensor_data[0], fuerza a lo largo del eje x, unidad N
              // ft_sensor_data[1], fuerza a lo largo del eje y, unidad N
              // ft_sensor_data[2], fuerza a lo largo del eje z, unidad N
              // ft_sensor_data[3], par alrededor del eje x, unidad Nm
              // ft_sensor_data[4], par alrededor del eje y, unidad Nm
              // ft_sensor_data[5], par alrededor del eje z, unidad Nm 
      uint8_t ft_sensor_active;  // Estado de activación del sensor de par, 0-restablecer, 1-activar 
      uint8_t EmergencyStop;   // Indicador de parada de emergencia, 0-parada de emergencia no pulsada, 1-parada de emergencia pulsada 
      int   motion_done;    // Señal de movimiento en posición, 1-en posición, 0-no en posición 
      uint8_t gripper_motiondone; // Señal de movimiento completado de la pinza, 0-no completado, 1-completado (no se detecta objeto), 2-movimiento completado (se detecta objeto)  
      int   mc_queue_len;    // Longitud de la cola de instrucciones de movimiento 
      uint8_t collisionState;   // Detección de colisión, 1-colisión, 0-sin colisión 
      int   trajectory_pnum;  // Número del punto de trayectoria 
      uint8_t safety_stop0_state; // Señal de parada de seguridad SI0 
      uint8_t safety_stop1_state; // Señal de parada de seguridad SI1 
      uint8_t gripper_fault_id;  // Número de pinza con error 
      uint16_t gripper_fault;   //  Fallo de pinza 0-sin fallo 1-tiempo de espera agotado 485 2-error de instrucción 3-caída de pieza otros-código de fallo de pinza+3  
      uint16_t gripper_active;   // Estado de activación de la pinza 
      uint8_t gripper_position;  // Posición de la pinza 
      int8_t  gripper_speed;   // Velocidad de la pinza 
      int8_t  gripper_current;  // Corriente de la pinza 
      int   gripper_temp;    // Temperatura de la pinza 
      int   gripper_voltage;  // Tensión de la pinza 
      robot_aux_state aux_state;  // Estado del eje extendido 485
      EXT_AXIS_STATUS extAxisStatus[4]; // Estado del eje extendido UDP 
      uint16_t extDIState[8];    // Entrada DI extendida
      uint16_t extDOState[8];    // Salida DO extendida
      uint16_t extAIState[4];    // Entrada AI extendida
      uint16_t extAOState[4];    // Salida AO extendida
      int rbtEnableState;      // Estado de habilitación del robot
      double  jointDriverTorque[6];    //Par del accionamiento de las articulaciones del robot
      double  jointDriverTemperature[6];  //Temperatura del accionamiento de las articulaciones del robot
      RobotTime robotTime;      // Hora del sistema del robot
      int softwareUpgradeState;   // Estado de actualización del software del robot
      uint16_t endLuaErrCode;    // Estado de ejecución del LUA del extremo
      uint16_t cl_analog_output[2]; // Salida analógica del armario de control
      uint16_t tl_analog_output;   // Salida analógica de la herramienta
      float gripperRotNum;      // Número de vueltas actuales de la pinza rotativa
      uint8_t gripperRotSpeed;    // Porcentaje de velocidad de rotación actual de la pinza rotativa
      uint8_t gripperRotTorque;   // Porcentaje de par de rotación actual de la pinza rotativa
      WELDING_BREAKOFF_STATE weldingBreakOffState; //Estado de interrupción de soldadura
      double jt_tgt_tor[6];         // Par de instrucción de las articulaciones
      int smartToolState;          // Estado de los botones del mango SmartTool
      float wideVoltageCtrlBoxTemp;     //Temperatura del armario de control de tensión amplia
      uint16_t wideVoltageCtrlBoxFanCurrent;//Corriente del ventilador del armario de control de tensión amplia (mA)
      double toolCoord[6];    //Valor del sistema de coordenadas de herramienta actual; x,y,z,rx,ry,rz
      double wobjCoord[6];    //Valor del sistema de coordenadas de pieza actual; x,y,z,rx,ry,rz
      double extoolCoord[6];   //Valor del sistema de coordenadas de herramienta externa actual; x,y,z,rx,ry,rz
      double exAxisCoord[6];   //Valor del sistema de coordenadas del eje extendido actual; x,y,z,rx,ry,rz
      double load;        //Masa de la carga
      double loadCog[3];     //Centro de gravedad de la carga
      double lastServoTarget[6]; //Posición objetivo del último ServoJ en la cola
      int servoJCmdNum;      //Contador de instrucciones servoJ
      double targetJointPos[6];  //Posición de instrucción de las 6 articulaciones, unidad °
      double targetJointVel[6];  //Velocidad de instrucción de las 6 articulaciones, unidad °/s
      double targetJointAcc[6];  //Aceleración de instrucción de las 6 articulaciones, unidad °/s2
      double targetJointCurrent[6]; //Corriente de instrucción de las 6 articulaciones, unidad A
      double actualJointCurrent[6]; //Corriente actual de las 6 articulaciones, unidad A
      double actualTCPForce[6];  //Par del extremo del robot Nm; x,y,z,rx,ry,rz
      double targetTCPPos[6];   //Posición de instrucción TCP del robot mm; x,y,z,rx,ry,rz
      uint8_t collisionLevel[6]; //Nivel de colisión del robot
      double speedScaleManual;  //Porcentaje de velocidad global en modo manual
      double speedScaleAuto;   //Porcentaje de velocidad global en modo automático
      int luaLineNum;       //Número de línea actual en ejecución del programa lua
      uint8_t abnomalStop;    //0-sin anomalía; 1-con anomalía
      char currentLuaFileName[256]; //Nombre del programa lua en ejecución actual
      uint8_t programTotalLine;  //Número total de líneas del programa lua
      uint8_t safetyBoxSingal[6]; //Estado de los botones de la caja de botones del robot
      double weldVoltage;     //Tensión de soldadura V
      double weldCurrent;     //Corriente de soldadura
      double weldTrackVel;    //Velocidad de seguimiento de soldadura mm/s
      uint8_t tpdException;    //Número de trayectorias TPD cargadas fuera de límite, 0-no fuera de límite, 1-fuera de límite 
      uint8_t alarmRebootRobot;  //Advertencia, 1-suelte el botón de parada de emergencia y apague y reinicie el armario de control, 2-comunicación anómala de articulaciones, apague y reinicie el armario de control
      uint8_t modbusMasterConnect; //bit0-bit7 corresponden al estado de conexión de los maestros 0-7 de ModbusTCP  0-no conectado  1-conectado
      uint8_t modbusSlaveConnect;  //Estado de conexión del esclavo ModbusTCP 0-no conectado; 1-conectado
      uint8_t btnBoxStopSignal;   //Señal de parada de emergencia de la caja de botones, 0-soltar parada de emergencia; 1-pulsar parada de emergencia
      uint8_t dragAlarm;      //Advertencia de arrastre, actualmente en modo automático, 0-sin alarma, 1-alarma, 2-anomalía de retroalimentación de posición, no cambia
      uint8_t safetyDoorAlarm;   //Advertencia de puerta de seguridad; 0-puerta de seguridad cerrada; 1-puerta de seguridad abierta
      uint8_t safetyPlaneAlarm;   //Advertencia de entrada en la pared de seguridad; 0-no ha entrado en la pared de seguridad; 1-ha entrado en la pared de seguridad
      uint8_t motonAlarm;      //Advertencia de movimiento
      uint8_t interfaceAlarm;    //Advertencia de entrada en la zona de interferencia
      int udpCmdState;       //Estado de conexión de comunicación UDP del puerto 20007
      uint8_t weldReadyState;    //Estado de preparación completada de la soldadora
      uint8_t alarmCheckEmergStopBtn; //0-normal; 1-comunicación anómala, compruebe si el botón de parada de emergencia está suelto
      uint8_t tsTmCmdComError;   //0-normal; 1-fallo de comunicación de instrucción de par
      uint8_t tsTmStateComError;  //0-normal; 1-fallo de comunicación de estado de par
      int ctrlBoxError;       //Error del armario de control
      uint8_t safetyDataState;   //Indicador de estado de los datos de seguridad, 0-normal, 1-anomalía
      uint8_t forceSensorErrState; //Fallo por tiempo de espera agotado en la conexión del sensor de fuerza; bit0-bit1 corresponden a los ID de sensor de fuerza ID1-ID2
      uint8_t ctrlOpenLuaErrCode[4]; //4 códigos de error del protocolo de periféricos del controlador (código de error 500)
      uint8_t strangePosFlag; //Indicador de posición singular actual; 0-normal; 1-posición singular
      uint8_t alarm;      //Advertencia
      uint8_t driverAlarm;   //Número de eje con alarma del accionamiento
      uint8_t aliveSlaveNumError; //Error del número de esclavos activos, 0: normal; 1: número incorrecto
      uint8_t slaveComError[8];  //Error del esclavo, 0: normal; 1: esclavo desconectado; 2: estado del esclavo inconsistente con el valor configurado; 3: esclavo no configurado; 4: error de configuración del esclavo; 5: error de inicialización del esclavo; 6: error de inicialización de la comunicación por buzón del esclavo
      uint8_t cmdPointError;   //Error del punto de instrucción
      uint8_t IOError;      //Error de IO
      uint8_t gripperError;    //Error de la pinza
      uint8_t fileError;     //Error de archivo
      uint8_t paraError;     //Error de parámetros
      uint8_t exaxisOutLimitError;  //Error de superación del límite software del eje externo
      uint8_t driverComError[6];   //Fallo de comunicación con el accionamiento
      uint8_t driverError;      //Número de eje con fallo de comunicación del accionamiento
      uint8_t outSoftLimitError;   //Fallo por superación del límite software
      char axleGenComData[130];   //Datos de retroalimentación de transmisión transparente del extremo del robot
      uint8_t socketConnTimeout;   //tiempo de espera agotado en la conexión socket, bit0-bit4: socketID 1-4
      uint8_t socketReadTimeout;   //tiempo de espera agotado en la lectura socket, bit0-bit4: socketID 1-4
      uint8_t tsWebStateComErr;   //web-fallo de comunicación de par; 0-normal; 1-fallo
      uint8_t exaxisCoordID;     //Número del sistema de coordenadas del eje extendido
      uint8_t programRunState;  //Estado de ejecución del programa LUA 0-programa no en ejecución; 1-programa en ejecución (incluye pausa del programa)
      uint16_t check_sum;     // Suma de verificación
    }ROBOT_STATE_PKG;

Enumeración de configuración de retroalimentación de estado del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    enum class RobotState
    {
        ProgramState = 3,           // Estado de ejecución del programa, 1-detendido; 2-en ejecución; 3-en pausa
        RobotState = 4,             // Estado de movimiento del robot, 1-detendido; 2-en ejecución; 3-en pausa; 4-arrastre
        MainCode = 5,               // Código de fallo principal
        SubCode = 6,                // Código de fallo secundario
        RobotMode = 7,              // Modo del robot, 1-modo manual; 0-modo automático
        JointCurPos = 8,            // Posición articular actual de los 6 ejes, unidad deg
        ToolCurPos = 9,             // Posición actual de la herramienta: [0]posición a lo largo del eje x(mm), [1]a lo largo del eje y(mm), [2]a lo largo del eje z(mm), [3]rotación alrededor del eje fijo X(deg), [4]alrededor del eje fijo Y(deg), [5]alrededor del eje fijo Z(deg)
        FlangeCurPos = 10,          // Posición actual de la brida del extremo: [0]a lo largo del eje x(mm), [1]a lo largo del eje y(mm), [2]a lo largo del eje z(mm), [3]alrededor del eje fijo X(deg), [4]alrededor del eje fijo Y(deg), [5]alrededor del eje fijo Z(deg)
        ActualJointVel = 11,        // Velocidad actual de las 6 articulaciones, unidad deg/s
        ActualJointAcc = 12,        // Aceleración actual de las 6 articulaciones, unidad deg/s^2
        TargetTCPCmpSpeed = 13,     // Velocidad compuesta de instrucción TCP: [0]posición(mm/s), [1]orientación(deg/s)
        TargetTCPSpeed = 14,        // Velocidad de instrucción TCP: [0]a lo largo del eje x(mm/s), [1]a lo largo del eje y(mm/s), [2]a lo largo del eje z(mm/s), [3]velocidad angular alrededor de X(deg/s), [4]alrededor de Y(deg/s), [5]alrededor de Z(deg/s)
        ActualTCPCmpSpeed = 15,     // Velocidad compuesta real TCP: [0]posición(mm/s), [1]orientación(deg/s)
        ActualTCPSpeed = 16,        // Velocidad real TCP: [0]a lo largo del eje x(mm/s), [1]a lo largo del eje y(mm/s), [2]a lo largo del eje z(mm/s), [3]velocidad angular alrededor de X(deg/s), [4]alrededor de Y(deg/s), [5]alrededor de Z(deg/s)
        ActualJointTorque = 17,     // Par actual de las 6 articulaciones, unidad N·m
        Tool = 18,                  // Número del sistema de coordenadas de herramienta aplicado
        User = 19,                  // Número del sistema de coordenadas de pieza aplicado
        ClDgtOutputH = 20,          // Salida IO digital del armario de control 15-8
        ClDgtOutputL = 21,          // Salida IO digital del armario de control 7-0
        TlDgtOutputL = 22,          // Salida IO digital de la herramienta 7-0, solo bit0-bit1 válidos
        ClDgtInputH = 23,           // Entrada IO digital del armario de control 15-8
        ClDgtInputL = 24,           // Entrada IO digital del armario de control 7-0
        TlDgtInputL = 25,           // Entrada IO digital de la herramienta 7-0, solo bit0-bit1 válidos
        ClAnalogInput = 26,         // Entrada analógica del armario de control: [0]canal 0, [1]canal 1
        TlAnalogInput = 27,         // Entrada analógica de la herramienta
        FtSensorRawData = 28,       // Datos brutos del sensor de par: [0]fuerza a lo largo del eje x(N), [1]a lo largo del eje y(N), [2]a lo largo del eje z(N), [3]par alrededor del eje x(Nm), [4]alrededor del eje y(Nm), [5]alrededor del eje z(Nm)
        FtSensorData = 29,          // Datos del sensor de par (procesados): [0]fuerza a lo largo del eje x(N), [1]a lo largo del eje y(N), [2]a lo largo del eje z(N), [3]par alrededor del eje x(Nm), [4]alrededor del eje y(Nm), [5]alrededor del eje z(Nm)
        FtSensorActive = 30,        // Estado de activación del sensor de par, 0-restablecer, 1-activar
        EmergencyStop = 31,         // Indicador de parada de emergencia, 0-parada de emergencia no pulsada, 1-parada de emergencia pulsada
        MotionDone = 32,            // Señal de movimiento en posición, 1-en posición, 0-no en posición
        GripperMotiondone = 33,     // Señal de movimiento completado de la pinza, 0-no completado, 1-completado (no se detecta objeto), 2-movimiento completado (se detecta objeto)
        McQueueLen = 34,            // Longitud de la cola de instrucciones de movimiento
        CollisionState = 35,        // Detección de colisión, 1-colisión, 0-sin colisión
        TrajectoryPnum = 36,        // Número del punto de trayectoria
        SafetyStop0State = 37,      // Señal de parada de seguridad SI0
        SafetyStop1State = 38,      // Señal de parada de seguridad SI1
        GripperFaultId = 39,        // Número de pinza con error
        GripperFault = 40,          // Fallo de pinza 0-sin fallo 1-tiempo de espera agotado 485 2-error de instrucción 3-caída de pieza otros-código de fallo de pinza+3
        GripperActive = 41,         // Estado de activación de la pinza
        GripperPosition = 42,       // Posición de la pinza
        GripperSpeed = 43,          // Velocidad de la pinza
        GripperCurrent = 44,        // Corriente de la pinza
        GripperTemp = 45,           // Temperatura de la pinza
        GripperVoltage = 46,        // Tensión de la pinza
        AuxState = 47,              // Estado del eje extendido 485
        ExtAxisStatus = 48,         // Estado del eje extendido UDP (4 ejes)
        ExtDIState = 49,            // Entrada DI extendida (8)
        ExtDOState = 50,            // Salida DO extendida (8)
        ExtAIState = 51,            // Entrada AI extendida (4)
        ExtAOState = 52,            // Salida AO extendida (4)
        RbtEnableState = 53,        // Estado de habilitación del robot
        JointDriverTorque = 54,     // Par del accionamiento de las articulaciones del robot (6 articulaciones)
        JointDriverTemperature = 55,// Temperatura del accionamiento de las articulaciones del robot (6 articulaciones)
        RobotTime = 56,             // Hora del sistema del robot
        SoftwareUpgradeState = 57,  // Estado de actualización del software del robot
        EndLuaErrCode = 58,         // Estado de ejecución del LUA del extremo
        ClAnalogOutput = 59,        // Salida analógica del armario de control (2)
        TlAnalogOutput = 60,        // Salida analógica de la herramienta
        GripperRotNum = 61,         // Número de vueltas actuales de la pinza rotativa
        GripperRotSpeed = 62,       // Porcentaje de velocidad de rotación actual de la pinza rotativa
        GripperRotTorque = 63,      // Porcentaje de par de rotación actual de la pinza rotativa
        WeldingBreakOffState = 64,  // Estado de interrupción de soldadura
        TargetJointTorque = 65,     // Par de instrucción de las articulaciones (6 articulaciones)
        SmartToolState = 66,        // Estado de los botones del mango SmartTool
        WideVoltageCtrlBoxTemp = 67,// Temperatura del armario de control de tensión amplia
        WideVoltageCtrlBoxFanCurrent = 68, // Corriente del ventilador del armario de control de tensión amplia (mA)
        ToolCoord = 69,             // Valor del sistema de coordenadas de herramienta actual: x,y,z,rx,ry,rz
        WobjCoord = 70,             // Valor del sistema de coordenadas de pieza actual: x,y,z,rx,ry,rz
        ExtoolCoord = 71,           // Valor del sistema de coordenadas de herramienta externa actual: x,y,z,rx,ry,rz
        ExAxisCoord = 72,           // Valor del sistema de coordenadas del eje extendido actual: x,y,z,rx,ry,rz
        Load = 73,                  // Masa de la carga
        LoadCog = 74,               // Centro de gravedad de la carga: x,y,z
        LastServoTarget = 75,       // Posición objetivo del último ServoJ en la cola (6 articulaciones)
        ServoJCmdNum = 76,          // Contador de instrucciones servoJ
        TargetJointPos = 77,        // Posición de instrucción de las 6 articulaciones, unidad °
        TargetJointVel = 78,        // Velocidad de instrucción de las 6 articulaciones, unidad °/s
        TargetJointAcc = 79,        // Aceleración de instrucción de las 6 articulaciones, unidad °/s²
        TargetJointCurrent = 80,    // Corriente de instrucción de las 6 articulaciones, unidad A
        ActualJointCurrent = 81,    // Corriente actual de las 6 articulaciones, unidad A
        ActualTCPForce = 82,        // Par del extremo del robot: x,y,z,rx,ry,rz, unidad Nm
        TargetTCPPos = 83,          // Posición de instrucción TCP del robot: x,y,z,rx,ry,rz, unidad mm
        CollisionLevel = 84,        // Nivel de colisión del robot (6)
        SpeedScaleManual = 85,      // Porcentaje de velocidad global en modo manual
        SpeedScaleAuto = 86,        // Porcentaje de velocidad global en modo automático
        LuaLineNum = 87,            // Número de línea actual en ejecución del programa lua
        AbnomalStop = 88,           // 0-sin anomalía; 1-con anomalía
        CurrentLuaFileName = 89,    // Nombre del programa lua en ejecución actual
        ProgramTotalLine = 90,      // Número total de líneas del programa lua
        SafetyBoxSingal = 91,       // Estado de los botones de la caja de botones del robot (6)
        WeldVoltage = 92,           // Tensión de soldadura V
        WeldCurrent = 93,           // Corriente de soldadura
        WeldTrackVel = 94,          // Velocidad de seguimiento de soldadura mm/s
        TpdException = 95,          // Número de trayectorias TPD cargadas fuera de límite, 0-no fuera de límite, 1-fuera de límite
        AlarmRebootRobot = 96,      // Advertencia: 1-suelte la parada de emergencia y apague y reinicie, 2-comunicación anómala de articulaciones, apague y reinicie
        ModbusMasterConnect = 97,   // bit0-7 corresponden al estado de conexión de los maestros 0-7 de ModbusTCP, 0-no conectado, 1-conectado
        ModbusSlaveConnect = 98,    // Estado de conexión del esclavo ModbusTCP, 0-no conectado, 1-conectado
        BtnBoxStopSignal = 99,      // Señal de parada de emergencia de la caja de botones, 0-soltar parada de emergencia, 1-pulsar parada de emergencia
        DragAlarm = 100,            // Advertencia de arrastre: 0-sin alarma, 1-alarma, 2-anomalía de retroalimentación de posición, no cambia
        SafetyDoorAlarm = 101,      // Advertencia de puerta de seguridad: 0-cerrada, 1-abierta
        SafetyPlaneAlarm = 102,     // Advertencia de pared de seguridad: 0-no ha entrado, 1-ha entrado
        MotonAlarm = 103,           // Advertencia de movimiento
        InterfaceAlarm = 104,       // Advertencia de entrada en la zona de interferencia
        UdpCmdState = 105,          // Estado de conexión de comunicación UDP del puerto 20007
        WeldReadyState = 106,       // Estado de preparación completada de la soldadora
        AlarmCheckEmergStopBtn = 107, // 0-normal; 1-comunicación anómala, compruebe el botón de parada de emergencia
        TsTmCmdComError = 108,      // 0-normal; 1-fallo de comunicación de instrucción de par
        TsTmStateComError = 109,    // 0-normal; 1-fallo de comunicación de estado de par
        CtrlBoxError = 110,         // Error del armario de control
        SafetyDataState = 111,      // Estado de los datos de seguridad, 0-normal, 1-anomalía
        ForceSensorErrState = 112,  // Tiempo de espera agotado en la conexión del sensor de fuerza, bit0-bit1 corresponden a ID1-ID2
        CtrlOpenLuaErrCode = 113,   // 4 códigos de error del protocolo de periféricos del controlador (código de error 500)
        StrangePosFlag = 114,       // Indicador de posición singular: 0-normal, 1-posición singular
        Alarm = 115,                // Advertencia
        DriverAlarm = 116,          // Número de eje con alarma del accionamiento
        AliveSlaveNumError = 117,   // Error del número de esclavos activos: 0-normal, 1-número incorrecto
        SlaveComError = 118,        // Error del esclavo: 0-normal, 1-desconectado, 2-estado inconsistente, 3-no configurado, 4-error de configuración, 5-error de inicialización, 6-error de inicialización de la comunicación por buzón
        CmdPointError = 119,        // Error del punto de instrucción
        IOError = 120,              // Error de IO
        GripperError = 121,         // Error de la pinza
        FileError = 122,            // Error de archivo
        ParaError = 123,            // Error de parámetros
        ExaxisOutLimitError = 124,  // Error de superación del límite software del eje externo
        DriverComError = 125,       // Fallo de comunicación con el accionamiento (6 ejes)
        DriverError = 126,          // Número de eje con fallo de comunicación del accionamiento
        OutSoftLimitError = 127,    // Fallo por superación del límite software
        AxleGenComData = 128,       // Datos de retroalimentación de transmisión transparente del extremo del robot
        SocketConnTimeout = 129,    // tiempo de espera agotado en la conexión socket, bit0-bit4 corresponden a socketID 1-4
        SocketReadTimeout = 130,    // tiempo de espera agotado en la lectura socket, bit0-bit4 corresponden a socketID 1-4
        TsWebStateComErr = 131,     // web-fallo de comunicación de par: 0-normal, 1-fallo
        ExaxisCoordID = 132          //Número del sistema de coordenadas del eje extendido
        ProgramRunState = 133       //Estado de ejecución del programa LUA 0-programa no en ejecución; 1-programa en ejecución (incluye pausa del programa)
    };