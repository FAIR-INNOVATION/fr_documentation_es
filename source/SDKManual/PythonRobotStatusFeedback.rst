Descripción de las estructuras de datos
========================================

.. toctree:: 
    :maxdepth: 5

Tipo de estructura de retroalimentación de estado del robot
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:

    class ROBOT_AUX_STATE(Structure):
        _pack_ = 1
        _fields_ = [
            ("servoId", c_uint8),         # ID del servomotor
            ("servoErrCode", c_int),     # Código de fallo del servomotor
            ("servoState", c_int),       # Estado del servomotor
            ("servoPos", c_double),      # Posición actual del servomotor
            ("servoVel", c_float),       # Velocidad actual del servomotor
            ("servoTorque", c_float),    # Par actual del servomotor
        ]

    class EXT_AXIS_STATUS(Structure):
        _pack_ = 1
        _fields_ = [
            ("pos", c_double),        # Posición del eje extendido
            ("vel", c_double),        # Velocidad del eje extendido
            ("errorCode", c_int),     # Código de fallo del eje extendido
            ("ready", c_uint8),        # Servomotor preparado
            ("inPos", c_uint8),        # Servomotor en posición
            ("alarm", c_uint8),        # Alarma del servomotor
            ("flerr", c_uint8),        # Error de seguimiento
            ("nlimit", c_uint8),       # Límite negativo alcanzado
            ("pLimit", c_uint8),       # Límite positivo alcanzado
            ("mdbsOffLine", c_uint8),  # Bus 485 del accionamiento desconectado
            ("mdbsTimeout", c_uint8),  # Tiempo de espera agotado en la comunicación 485 entre la tarjeta de control y la caja de control
            ("homingStatus", c_uint8), # Estado de retorno a cero del eje extendido
        ]

    class WELDING_BREAKOFF_STATE(Structure):
        _pack_ = 1
        _fields_ = [
            ("breakOffState", c_uint8),        # Estado de interrupción de soldadura
            ("weldArcState", c_uint8),        # Estado de interrupción del arco de soldadura
        ]

    # ==================== Estructura completa del estado del robot ====================
    class RobotStatePkg(Structure):
        """
        Paquete de datos de retroalimentación del estado del robot
        """
        _pack_ = 1
        _fields_ = [
            # Información de cabecera de trama
            ("frame_head", c_uint16),           # Cabecera de trama, definida como 0x5A5A
            ("frame_cnt", c_uint8),             # Contador de trama, conteo cíclico 0-255
            ("data_len", c_uint16),             # Longitud del contenido de datos
            ("program_state", c_uint8),         # Estado de ejecución del programa, 1-detener; 2-ejecutar; 3-pausar
            ("robot_state", c_uint8),             # Estado de movimiento del robot, 1-detener; 2-ejecutar; 3-pausar; 4-arrastrar
            ("main_code", c_int),               # Código de fallo principal
            ("sub_code", c_int),                # Código de fallo secundario
            ("robot_mode", c_uint8),            # Modo del robot, 1-modo manual; 0-modo automático

            # Posición y velocidad articular
            ("jt_cur_pos", c_double * 6),       # Posición articular actual de los 6 ejes, unidad deg
            ("tl_cur_pos", c_double * 6),       # Posición actual de la herramienta [x,y,z,rx,ry,rz]
            ("flange_cur_pos", c_double * 6),   # Posición actual de la brida del extremo [x,y,z,rx,ry,rz]
            ("actual_qd", c_double * 6),        # Velocidad actual de las 6 articulaciones, unidad deg/s
            ("actual_qdd", c_double * 6),       # Aceleración actual de las 6 articulaciones, unidad deg/s^2
            ("target_TCP_CmpSpeed", c_double * 2),  # Velocidad compuesta de comando TCP [posición mm/s, orientación deg/s]
            ("target_TCP_Speed", c_double * 6), # Velocidad de comando TCP [x,y,z,rx,ry,rz]
            ("actual_TCP_CmpSpeed", c_double * 2),  # Velocidad compuesta real TCP [posición mm/s, orientación deg/s]
            ("actual_TCP_Speed", c_double * 6), # Velocidad real TCP [x,y,z,rx,ry,rz]
            ("jt_cur_tor", c_double * 6),       # Par actual de los 6 ejes, unidad N·m

            # Sistemas de coordenadas de herramienta y de usuario
            ("tool", c_int),                    # Número del sistema de coordenadas de herramienta aplicado
            ("user", c_int),                    # Número del sistema de coordenadas de pieza aplicado

            # IO digital
            ("cl_dgt_output_h", c_uint8),       # Salida IO digital de la caja de control 15-8
            ("cl_dgt_output_l", c_uint8),       # Salida IO digital de la caja de control 7-0
            ("tl_dgt_output_l", c_uint8),       # Salida IO digital de la herramienta 7-0, solo bit0-bit1 válidos
            ("cl_dgt_input_h", c_uint8),        # Entrada IO digital de la caja de control 15-8
            ("cl_dgt_input_l", c_uint8),        # Entrada IO digital de la caja de control 7-0
            ("tl_dgt_input_l", c_uint8),        # Entrada IO digital de la herramienta 7-0, solo bit0-bit1 válidos

            # IO analógico
            ("cl_analog_input", c_uint16 * 2),  # Entrada analógica de la caja de control [0],[1]
            ("tl_anglog_input", c_uint16),      # Entrada analógica de la herramienta

            # Sensor de par
            ("ft_sensor_raw_data", c_double * 6),   # Datos originales del sensor de par
            ("ft_sensor_data", c_double * 6),      # Datos del sensor de par
            ("ft_sensor_active", c_uint8),          # Estado de activación del sensor de par

            # Señales de estado
            ("EmergencyStop", c_uint8),         # Indicador de parada de emergencia, 0-parada de emergencia no pulsada, 1-parada de emergencia pulsada
            ("motion_done", c_int),             # Señal de movimiento en posición, 1-en posición, 0-no en posición
            ("gripper_motiondone", c_uint8),    # Señal de movimiento completado de la pinza, 0-no completado, 1-completado (sin objeto detectado), 2-movimiento completado (objeto detectado)
            ("mc_queue_len", c_int),            # Longitud de la cola de comandos de movimiento
            ("collisionState", c_uint8),        # Detección de colisión, 1-colisión, 0-sin colisión
            ("trajectory_pnum", c_int),         # Número de punto de trayectoria
            ("safety_stop0_state", c_uint8),    # Señal de parada de seguridad SI0
            ("safety_stop1_state", c_uint8),    # Señal de parada de seguridad SI1

            # Información de la pinza
            ("gripper_fault_id", c_uint8),      # Número de pinza con error
            ("gripper_fault", c_uint16),        # Fallo de la pinza 0-sin fallo 1-tiempo de espera 485 2-error de comando 3-pieza caída otro-código de fallo de la pinza
            ("gripper_active", c_uint16),      # Estado de activación de la pinza
            ("gripper_position", c_uint8),      # Posición de la pinza
            ("gripper_speed", c_int8),          # Velocidad de la pinza
            ("gripper_current", c_int8),        # Corriente de la pinza
            ("gripper_temp", c_int),            # Temperatura de la pinza
            ("gripper_voltage", c_int),         # Voltaje de la pinza

            # Estado del eje extendido
            ("aux_axis_state", ROBOT_AUX_STATE * 25),    # Estado del eje extendido 485 (25)
            ("extAxisStatus", EXT_AXIS_STATUS * 4), # Estado del eje extendido UDP (4)

            # Estado de IO extendido
            ("extDIState", c_uint16 * 8),       # Entrada DI extendida
            ("extDOState", c_uint16 * 8),       # Salida DO extendida
            ("extAIState", c_uint16 * 4),        # Entrada AI extendida
            ("extAOState", c_uint16 * 4),        # Salida AO extendida

            # Estado del robot y de las articulaciones
            ("rbtEnableState", c_int),                  # Estado de habilitación del robot
            ("jointDriverTorque", c_double * 6),        # Par del accionamiento articular del robot
            ("jointDriverTemperature", c_double * 6),   # Temperatura del accionamiento articular del robot

            # Hora del robot
            #("robotTime", c_int * 7),             # Hora del sistema del robot [year,month,day,hour,min,sec,ms]
            ("year", ctypes.c_uint16),  # Año
            ("mouth", ctypes.c_uint8),  # Mes
            ("day", ctypes.c_uint8),  # Día
            ("hour", ctypes.c_uint8),  # Hora
            ("minute", ctypes.c_uint8),  # Minuto
            ("second", ctypes.c_uint8),  # Segundo
            ("millisecond", ctypes.c_uint16),  # Milisegundo

            ("softwareUpgradeState", c_int),      # Estado de actualización del software del robot
            ("endLuaErrCode", c_uint16),          # Estado de ejecución de LUA del extremo

            # Salida analógica
            ("cl_analog_output", c_uint16 * 2), # Salida analógica de la caja de control [0],[1]
            ("tl_analog_output", c_uint16),       # Salida analógica de la herramienta

            # Pinza rotativa
            ("gripperRotNum", c_float),         # Número de revoluciones actual de la pinza rotativa
            ("gripperRotSpeed", c_uint8),       # Porcentaje de velocidad de rotación actual de la pinza rotativa
            ("gripperRotTorque", c_uint8),      # Porcentaje de par de rotación actual de la pinza rotativa

            # Estado de interrupción de soldadura - usando estructura
            ("weldingBreakOffState", WELDING_BREAKOFF_STATE),  # Estado de interrupción de soldadura

            # Par articular objetivo
            ("jt_tgt_tor", c_double * 6),       # Par de comando articular

            ("smartToolState", c_int),          # Estado de los botones del mango SmartTool
            ("wideVoltageCtrlBoxTemp", c_float),        # Temperatura de la caja de control de voltaje amplio
            ("wideVoltageCtrlBoxFanCurrent", c_uint16), # Corriente del ventilador de la caja de control de voltaje amplio (mA)

            # Valores del sistema de coordenadas
            ("toolCoord", c_double * 6),        # Valor actual del sistema de coordenadas de herramienta; x,y,z,rx,ry,rz
            ("wobjCoord", c_double * 6),        # Valor actual del sistema de coordenadas de pieza; x,y,z,rx,ry,rz
            ("extoolCoord", c_double * 6),      # Valor actual del sistema de coordenadas de herramienta externa; x,y,z,rx,ry,rz
            ("exAxisCoord", c_double * 6),      # Valor actual del sistema de coordenadas del eje extendido; x,y,z,rx,ry,rz

            # Carga
            ("load", c_double),                 # Masa de la carga
            ("loadCog", c_double * 3),            # Centro de gravedad de la carga

            # Comando de servomotor
            ("lastServoTarget", c_double * 6),  # Última posición objetivo ServoJ en la cola
            ("servoJCmdNum", c_int),            # Contador de comandos ServoJ

            # Datos articulares objetivo
            ("targetJointPos", c_double * 6),   # Posición de comando de las 6 articulaciones, unidad °
            ("targetJointVel", c_double * 6),   # Velocidad de comando de las 6 articulaciones, unidad °/s
            ("targetJointAcc", c_double * 6),   # Aceleración de comando de las 6 articulaciones, unidad °/s2
            ("targetJointCurrent", c_double * 6), # Corriente de comando de las 6 articulaciones, unidad A
            ("actualJointCurrent", c_double * 6), # Corriente actual de las 6 articulaciones, unidad A
            ("actualTCPForce", c_double * 6),   # Par del extremo del robot Nm; x,y,z,rx,ry,rz
            ("targetTCPPos", c_double * 6),     # Posición de comando TCP del robot mm; x,y,z,rx,ry,rz

            ("collisionLevel", c_uint8 * 6),    # Nivel de colisión del robot
            ("speedScaleManual", c_double),     # Porcentaje de velocidad global en modo manual
            ("speedScaleAuto", c_double),       # Porcentaje de velocidad global en modo automático
            ("luaLineNum", c_int),              # Número de línea actual del programa lua en ejecución
            ("abnomalStop", c_uint8),           # 0-sin anomalía; 1-con anomalía
            ("currentLuaFileName", c_uint8 * 256),  # Nombre del programa lua actual en ejecución
            ("programTotalLine", c_uint8),      # Número total de líneas del programa lua
            ("safetyBoxSingal", c_uint8 * 6),   # Estado de los botones de la caja de botones del robot

            # Datos de soldadura
            ("weldVoltage", c_double),          # Voltaje de soldadura V
            ("weldCurrent", c_double),          # Corriente de soldadura
            ("weldTrackVel", c_double),         # Velocidad de seguimiento de soldadura mm/s

            ("tpdException", c_uint8),            # Número de trayectorias TPD cargadas fuera de límite, 0-no excedido, 1-excedido
            ("alarmRebootRobot", c_uint8),      # Advertencia, 1-suelte el botón de parada de emergencia y reinicie la caja de control, 2-anomalía de comunicación articular, reinicie la caja de control
            ("modbusMasterConnect", c_uint8),   # bits 0-7 corresponden al estado de conexión maestro ModbusTCP 0-7
            ("modbusSlaveConnect", c_uint8),    # Estado de conexión del esclavo ModbusTCP
            ("btnBoxStopSignal", c_uint8),      # Señal de parada de emergencia de la caja de botones
            ("dragAlarm", c_uint8),             # Advertencia de arrastre
            ("safetyDoorAlarm", c_uint8),       # Advertencia de puerta de seguridad
            ("safetyPlaneAlarm", c_uint8),      # Advertencia de entrada en muro de seguridad
            ("motonAlarm", c_uint8),            # Advertencia de movimiento
            ("interfaceAlarm", c_uint8),        # Advertencia de entrada en zona de interferencia
            ("udpCmdState", c_int),             # Estado de conexión de comunicación UDP del puerto 20007
            ("weldReadyState", c_uint8),        # Estado de preparación completada de la soldadora
            ("alarmCheckEmergStopBtn", c_uint8),    # 0-normal; 1-anomalía de comunicación, compruebe si el botón de parada de emergencia está suelto
            ("tsTmCmdComError", c_uint8),       # 0-normal; 1-fallo de comunicación del comando de par
            ("tsTmStateComError", c_uint8),     # 0-normal; 1-fallo de comunicación del estado de par
            ("ctrlBoxError", c_int),            # Error de la caja de control
            ("safetyDataState", c_uint8),       # Indicador de estado de datos de seguridad
            ("forceSensorErrState", c_uint8),   # Fallo por tiempo de espera de conexión del sensor de fuerza
            ("ctrlOpenLuaErrCode", c_uint8 * 4),  # Códigos de error del protocolo de periféricos de los 4 controladores
            ("strangePosFlag", c_uint8),        # Indicador de pose singular actual
            ("alarm", c_uint8),                 # Advertencia
            ("driverAlarm", c_uint8),           # Número de eje con alarma del accionamiento
            ("aliveSlaveNumError", c_uint8),    # Error en el número de esclavos activos
            ("slaveComError", c_uint8 * 8),     # Estado de error del esclavo
            ("cmdPointError", c_uint8),         # Error de punto de comando
            ("IOError", c_uint8),               # Error de IO
            ("gripperError", c_uint8),          # Error de pinza
            ("fileError", c_uint8),             # Error de archivo
            ("paraError", c_uint8),             # Error de parámetro
            ("exaxisOutLimitError", c_uint8),   # Error de eje externo fuera de límite suave
            ("driverComError", c_uint8 * 6),    # Fallo de comunicación con el accionamiento
            ("driverError", c_uint8),           # Número de eje con fallo de comunicación del accionamiento
            ("outSoftLimitError", c_uint8),     # Fallo por fuera de límite suave
            ("axleGenComData", c_uint8 * 130),   # Datos no periódicos de comunicación general del eje
            ("socketConnTimeout", c_uint8),     # Tiempo de espera de conexión de socket
            ("socketReadTimeout", c_uint8),     # Tiempo de espera de lectura de socket
            ("tsWebStateComErr", c_uint8),      # Error de comunicación del estado TS_WEB
            ("exaxisCoordID", c_uint8),         # ID del eje extendido externo
            ("ProgramRunState", c_uint8),       # Estado de ejecución del programa LUA 0-programa no en ejecución; 1-programa en ejecución (incluye pausa del programa)
            ("check_sum", c_uint16)          # Suma de verificación
        ]

Paquete de datos de retroalimentación del estado del controlador
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: python SDK-v2.1.7
    
.. csv-table:: 
    :header-rows: 1
    :name: Paquete de datos de retroalimentación del estado del controlador
    :widths: 20 30

    "Variable","Significado"
    "program_state","Estado de ejecución del programa, 1-detener; 2-ejecutar; 3-pausar"
    "robot_state","Estado de movimiento del robot, 1-detener; 2-ejecutar; 3-pausar; 4-arrastrar"
    "main_code","Código de fallo principal"
    "sub_code","Código de fallo secundario"
    "robot_mode","Modo del robot, 0-modo automático; 1-modo manual"
    "jt_cur_pos[i]","Posición articular actual, unidad deg, i:0~5"
    "tl_cur_pos[i]","Pose actual de la herramienta, unidad deg&mm, i:0~5"
    "flange_cur_pos[i]","Pose actual de la brida del extremo, unidad deg&mm, i:0~5"
    "actual_qd[i]","Velocidad articular actual del robot, unidad deg/s, i:0~5"
    "actual_qdd[i]","Aceleración articular actual del robot, unidad deg/s^2, i:0~5"
    "target_TCP_CmpSpeed[i]","Velocidad compuesta de comando TCP del robot, unidad mm/s&deg/s, i:0~1"
    "target_TCP_Speed[i]","Velocidad de comando TCP del robot, unidad mm/s&deg/s, i:0~5"
    "actual_TCP_CmpSpeed[i]","Velocidad compuesta real TCP del robot, unidad mm/s&deg/s, i:0~1"
    "actual_TCP_Speed[i]","Velocidad real TCP del robot, unidad mm/s&deg/s, i:0~5"
    "jt_cur_tor[i]","Par actual, unidad N·m, i:0~5"
    "tool","Número del sistema de coordenadas de herramienta aplicado"
    "user","Número del sistema de coordenadas de pieza aplicado"
    "cl_dgt_output_h","Salida IO digital de la caja de control 15-8"
    "cl_dgt_output_l","Salida IO digital de la caja de control 7-0"
    "tl_dgt_output_l","Salida IO digital de la herramienta 7-0, solo bit0-bit1 válidos"
    "dgt_input_h","Entrada IO digital de la caja de control 15-8"
    "cl_dgt_input_l","Entrada IO digital de la caja de control 7-0"
    "tl_dgt_input_l","Entrada IO digital de la herramienta 7-0, solo bit0-bit1 válidos"
    "cl_analog_input[i]","Entrada analógica de la caja de control, i:0~2"
    "tl_anglog_input","Entrada analógica de la herramienta"
    "ft_sensor_raw_data","Datos originales del sensor de par, unidad N&Nm, i:0~5"
    "ft_sensor_data","Datos del sensor de par, unidad N&Nm, i:0~5"
    "ft_sensor_active","Estado de activación del sensor de par, 0-restablecer, 1-activar"
    "EmergencyStop","Indicador de parada de emergencia, 0-parada de emergencia no pulsada, 1-parada de emergencia pulsada"
    "motion_done","Señal de movimiento en posición, 1-en posición, 0-no en posición"
    "gripper_motiondone","Señal de movimiento completado de la pinza, 0-no completado, 1-completado (sin objeto detectado), 2-movimiento completado (objeto detectado)"
    "mc_queue_len","Longitud de la cola de comandos de movimiento"
    "collisionState","Detección de colisión, 1-colisión, 0-sin colisión"
    "trajectory_pnum","Número de punto de trayectoria"
    "safety_stop0_state","Señal de parada de seguridad SI0"
    "safety_stop1_state","Señal de parada de seguridad SI1"
    "gripper_fault_id","Número de pinza con error"
    "gripper_fault","Fallo de la pinza 0-sin fallo 1-tiempo de espera 485 2-error de comando 3-pieza caída otro-código de fallo de la pinza"
    "gripper_active","Estado de activación de la pinza, 0-no activada, 1-activada"
    "gripper_position","Posición de la pinza (porcentaje)"
    "gripper_speed","Velocidad de la pinza (porcentaje)"
    "gripper_current","Corriente de la pinza (porcentaje)"
    "gripper_tmp","Temperatura de la pinza, unidad ℃"
    "gripper_voltage","Voltaje de la pinza, unidad V"
    "auxState.servoId","Eje extendido 485, ID del servomotor, i:0~3"
    "auxState.servoErrCode","Eje extendido 485, código de fallo del servomotor, i:0~3"
    "auxState.servoState","Eje extendido 485, estado del servomotor, i:0~3"
    "auxState.servoPos","Eje extendido 485, posición actual del servomotor, i:0~3"
    "auxState.servoVel","Eje extendido 485, velocidad actual del servomotor, i:0~3"
    "auxState.servoTorque","Eje extendido 485, par actual del servomotor, i:0~3"
    "extAxisStatus[i].pos","Eje extendido UDP, posición, i:0~3"
    "extAxisStatus[i].vel","Eje extendido UDP, velocidad, i:0~3"
    "extAxisStatus[i].errorCode","Eje extendido UDP, código de fallo, i:0~3"
    "extAxisStatus[i].ready","Eje extendido UDP, servomotor preparado, i:0~3"
    "extAxisStatus[i].inPos","Eje extendido UDP, servomotor en posición, i:0~3"
    "extAxisStatus[i].alarm","Eje extendido UDP, alarma del servomotor, i:0~3"
    "extAxisStatus[i].flerr","Eje extendido UDP, error de seguimiento, i:0~3"
    "extAxisStatus[i].nlimit","Eje extendido UDP, límite negativo alcanzado, i:0~3"
    "extAxisStatus[i].pLimit","Eje extendido UDP, límite positivo alcanzado, i:0~3"
    "extAxisStatus[i].mdbsOffLine","Eje extendido UDP, bus 485 del accionamiento desconectado"
    "extAxisStatus[i].mdbsTimeout","Eje extendido UDP, tiempo de espera agotado en la comunicación 485 entre la tarjeta de control y la caja de control"
    "extAxisStatus[i].homingStatus","Eje extendido UDP, estado de retorno a cero"
    "extDIState","Estado de entrada digital extendida"
    "extDOState","Estado de salida digital extendida"
    "extAIState","Estado de entrada analógica extendida"
    "extAOState","Estado de salida analógica extendida"
    "rbtEnableState","Estado de habilitación del robot"
    "jointDriverTorque","Par actual del accionamiento articular"
    "jointDriverTemperature","Temperatura actual del accionamiento articular"
    "year","Año"
    "mouth","Mes"
    "day","Día"
    "hour","Hora"
    "minute","Minuto"
    "second","Segundo"
    "millisecond","Milisegundo"
    "softwareUpgradeState","Estado de actualización del software del robot"
    "endLuaErrCode","Estado de ejecución de LUA del extremo"
    "cl_analog_output[i]","Salida analógica de la caja de control, i:0~1"
    "tl_analog_output","Salida analógica de la herramienta"
    "gripperRotNum","Número de revoluciones actual de la pinza rotativa"
    "gripperRotSpeed","Porcentaje de velocidad de rotación actual de la pinza rotativa"
    "gripperRotTorque","Porcentaje de par de rotación actual de la pinza rotativa"
    "weldingBreakOffState","Estado de interrupción de soldadura"
    "jt_tgt_tor","Par de comando articular"
    "smartToolState","Estado de los botones del mango SmartTool"
    "wideVoltageCtrlBoxTemp","Temperatura de la caja de control de voltaje amplio"
    "wideVoltageCtrlBoxFanCurrent","Corriente del ventilador de la caja de control de voltaje amplio (ma)"
    "toolCoord[i]","Sistema de coordenadas de herramienta, i:0~5"
    "wobjCoord[i]","Sistema de coordenadas de pieza, i:0~5"
    "extoolCoord[i]","Sistema de coordenadas de herramienta externa, i:0~5"
    "exAxisCoord[i]","Sistema de coordenadas del eje extendido, i:0~5"
    "load","Masa de la carga"
    "loadCog[i]","Centro de gravedad de la carga, i:0~2"
    "lastServoTarget[i]","Última posición objetivo ServoJ en la cola, i:0~5"
    "servoJCmdNum","Contador de comandos ServoJ"

Estado del controlador del servomotor
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: python SDK-v2.1.3
    
.. csv-table:: 
    :header-rows: 1
    :name: Estado del controlador del servomotor
    :widths: 20 30

    "Variable","Significado"
    "servoId","ID del servomotor"
    "servoErrCode","Código de fallo del servomotor"
    "servoState","Estado del servomotor"
    "servoPos","Posición actual del servomotor"
    "servoVel","Velocidad actual del servomotor"
    "servoTorque","Par actual del servomotor"

Estado del eje extendido
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: python SDK-v2.1.3
    
.. csv-table:: 
    :header-rows: 1
    :name: Estado del eje extendido
    :widths: 20 30

    "Variable","Significado"
    "pos","Posición del eje extendido"
    "vel","Velocidad del eje extendido"
    "errorCode","Código de fallo del eje extendido"
    "ready","Servomotor preparado"
    "inPos","Servomotor en posición"
    "alarm","Alarma del servomotor"
    "flerr","Error de seguimiento"
    "nlimit","Límite negativo alcanzado"
    "pLimit","Límite positivo alcanzado"
    "mdbsOffLine","Bus 485 del accionamiento desconectado"
    "mdbsTimeout","Tiempo de espera agotado en la comunicación 485 entre la tarjeta de control y la caja de control"
    "homingStatus","Estado de retorno a cero del eje extendido"

Estado de interrupción de soldadura
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: python SDK-v2.1.3
    
.. csv-table:: 
    :header-rows: 1
    :name: Estado de interrupción de soldadura
    :widths: 20 30

    "Variable","Significado"
    "breakOffState","Estado de interrupción de soldadura"
    "weldArcState","Estado de interrupción del arco de soldadura"

Ejemplo de código
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Establecer conexión con el controlador del robot; si la conexión es exitosa, devuelve un objeto robot
    robot = Robot.RPC('192.168.58.2')
    print("program_state:", robot.robot_state_pkg.program_state)
    print("robot_state:", robot.robot_state_pkg.robot_state)
    print("main_code:", robot.robot_state_pkg.main_code)
    print("sub_code:", robot.robot_state_pkg.sub_code)
    print("robot_mode:", robot.robot_state_pkg.robot_mode)
    print("jt_cur_pos0:", robot.robot_state_pkg.jt_cur_pos[0])
    print("jt_cur_pos1:", robot.robot_state_pkg.jt_cur_pos[1])
    print("jt_cur_pos2:", robot.robot_state_pkg.jt_cur_pos[2])
    print("jt_cur_pos3:", robot.robot_state_pkg.jt_cur_pos[3])
    print("jt_cur_pos4:", robot.robot_state_pkg.jt_cur_pos[4])
    print("jt_cur_pos5:", robot.robot_state_pkg.jt_cur_pos[5])
    print("tl_cur_pos0:", robot.robot_state_pkg.tl_cur_pos[0])
    print("tl_cur_pos1:", robot.robot_state_pkg.tl_cur_pos[1])
    print("tl_cur_pos2:", robot.robot_state_pkg.tl_cur_pos[2])
    print("tl_cur_pos3:", robot.robot_state_pkg.tl_cur_pos[3])
    print("tl_cur_pos4:", robot.robot_state_pkg.tl_cur_pos[4])
    print("tl_cur_pos5:", robot.robot_state_pkg.tl_cur_pos[5])
    print("flange_cur_pos0:", robot.robot_state_pkg.flange_cur_pos[0])
    print("flange_cur_pos1:", robot.robot_state_pkg.flange_cur_pos[1])
    print("flange_cur_pos2:", robot.robot_state_pkg.flange_cur_pos[2])
    print("flange_cur_pos3:", robot.robot_state_pkg.flange_cur_pos[3])
    print("flange_cur_pos4:", robot.robot_state_pkg.flange_cur_pos[4])
    print("flange_cur_pos5:", robot.robot_state_pkg.flange_cur_pos[5])
    print("actual_qd0:", robot.robot_state_pkg.actual_qd[0])
    print("actual_qd1:", robot.robot_state_pkg.actual_qd[1])
    print("actual_qd2:", robot.robot_state_pkg.actual_qd[2])
    print("actual_qd3:", robot.robot_state_pkg.actual_qd[3])
    print("actual_qd4:", robot.robot_state_pkg.actual_qd[4])
    print("actual_qd5:", robot.robot_state_pkg.actual_qd[5])
    print("actual_qdd0:", robot.robot_state_pkg.actual_qdd[0])
    print("actual_qdd1:", robot.robot_state_pkg.actual_qdd[1])
    print("actual_qdd2:", robot.robot_state_pkg.actual_qdd[2])
    print("actual_qdd3:", robot.robot_state_pkg.actual_qdd[3])
    print("actual_qdd4:", robot.robot_state_pkg.actual_qdd[4])
    print("actual_qdd5:", robot.robot_state_pkg.actual_qdd[5])
    print("target_TCP_CmpSpeed0:", robot.robot_state_pkg.target_TCP_CmpSpeed[0])
    print("target_TCP_CmpSpeed1:", robot.robot_state_pkg.target_TCP_CmpSpeed[1])
    print("target_TCP_Speed0:", robot.robot_state_pkg.target_TCP_Speed[0])
    print("target_TCP_Speed1:", robot.robot_state_pkg.target_TCP_Speed[1])
    print("target_TCP_Speed2:", robot.robot_state_pkg.target_TCP_Speed[2])
    print("target_TCP_Speed3:", robot.robot_state_pkg.target_TCP_Speed[3])
    print("target_TCP_Speed4:", robot.robot_state_pkg.target_TCP_Speed[4])
    print("target_TCP_Speed5:", robot.robot_state_pkg.target_TCP_Speed[5])
    print("actual_TCP_CmpSpeed0:", robot.robot_state_pkg.actual_TCP_CmpSpeed[0])
    print("actual_TCP_CmpSpeed1:", robot.robot_state_pkg.actual_TCP_CmpSpeed[1])
    print("actual_TCP_Speed0:", robot.robot_state_pkg.actual_TCP_Speed[0])
    print("actual_TCP_Speed1:", robot.robot_state_pkg.actual_TCP_Speed[1])
    print("actual_TCP_Speed2:", robot.robot_state_pkg.actual_TCP_Speed[2])
    print("actual_TCP_Speed3:", robot.robot_state_pkg.actual_TCP_Speed[3])
    print("actual_TCP_Speed4:", robot.robot_state_pkg.actual_TCP_Speed[4])
    print("actual_TCP_Speed5:", robot.robot_state_pkg.actual_TCP_Speed[5])
    print("jt_cur_tor0:", robot.robot_state_pkg.jt_cur_tor[0])
    print("jt_cur_tor1:", robot.robot_state_pkg.jt_cur_tor[1])
    print("jt_cur_tor2:", robot.robot_state_pkg.jt_cur_tor[2])
    print("jt_cur_tor3:", robot.robot_state_pkg.jt_cur_tor[3])
    print("jt_cur_tor4:", robot.robot_state_pkg.jt_cur_tor[4])
    print("jt_cur_tor5:", robot.robot_state_pkg.jt_cur_tor[5])
    print("tool:", robot.robot_state_pkg.tool)
    print("user:", robot.robot_state_pkg.user)
    print("cl_dgt_output_h:", robot.robot_state_pkg.cl_dgt_output_h)
    print("cl_dgt_output_l:", robot.robot_state_pkg.cl_dgt_output_l)
    print("tl_dgt_output_l:", robot.robot_state_pkg.tl_dgt_output_l)
    print("cl_dgt_input_h:", robot.robot_state_pkg.cl_dgt_input_h)
    print("cl_dgt_input_l:", robot.robot_state_pkg.cl_dgt_input_l)
    print("tl_dgt_input_l:", robot.robot_state_pkg.tl_dgt_input_l)
    print("cl_analog_input0:", robot.robot_state_pkg.cl_analog_input[0])
    print("cl_analog_input1:", robot.robot_state_pkg.cl_analog_input[1])
    print("tl_anglog_input:", robot.robot_state_pkg.tl_anglog_input)
    print("ft_sensor_raw_data0:", robot.robot_state_pkg.ft_sensor_raw_data[0])
    print("ft_sensor_raw_data1:", robot.robot_state_pkg.ft_sensor_raw_data[1])
    print("ft_sensor_raw_data2:", robot.robot_state_pkg.ft_sensor_raw_data[2])
    print("ft_sensor_raw_data3:", robot.robot_state_pkg.ft_sensor_raw_data[3])
    print("ft_sensor_raw_data4:", robot.robot_state_pkg.ft_sensor_raw_data[4])
    print("ft_sensor_raw_data5:", robot.robot_state_pkg.ft_sensor_raw_data[5])
    print("ft_sensor_data0:", robot.robot_state_pkg.ft_sensor_data[0])
    print("ft_sensor_data1:", robot.robot_state_pkg.ft_sensor_data[1])
    print("ft_sensor_data2:", robot.robot_state_pkg.ft_sensor_data[2])
    print("ft_sensor_data3:", robot.robot_state_pkg.ft_sensor_data[3])
    print("ft_sensor_data4:", robot.robot_state_pkg.ft_sensor_data[4])
    print("ft_sensor_data5:", robot.robot_state_pkg.ft_sensor_data[5])
    print("ft_sensor_active:", robot.robot_state_pkg.ft_sensor_active)
    print("EmergencyStop:", robot.robot_state_pkg.EmergencyStop)
    print("motion_done:", robot.robot_state_pkg.motion_done)
    print("gripper_motiondone:", robot.robot_state_pkg.gripper_motiondone)
    print("mc_queue_len:", robot.robot_state_pkg.mc_queue_len)
    print("collisionState:", robot.robot_state_pkg.collisionState)
    print("trajectory_pnum:", robot.robot_state_pkg.trajectory_pnum)
    print("safety_stop0_state:", robot.robot_state_pkg.safety_stop0_state)
    print("safety_stop1_state:", robot.robot_state_pkg.safety_stop1_state)
    print("gripper_fault_id:", robot.robot_state_pkg.gripper_fault_id)
    print("gripper_fault:", robot.robot_state_pkg.gripper_fault)
    print("gripper_active:", robot.robot_state_pkg.gripper_active)
    print("gripper_position:", robot.robot_state_pkg.gripper_position)
    print("gripper_speed:", robot.robot_state_pkg.gripper_speed)
    print("gripper_current:", robot.robot_state_pkg.gripper_current)
    print("gripper_tmp:", robot.robot_state_pkg.gripper_tmp)
    print("gripper_voltage:", robot.robot_state_pkg.gripper_voltage)
    print("auxState.servoId:", robot.robot_state_pkg.auxState.servoId)
    print("auxState.servoErrCode:", robot.robot_state_pkg.auxState.servoErrCode)
    print("auxState.servoState:", robot.robot_state_pkg.auxState.servoState)
    print("auxState.servoPos:", robot.robot_state_pkg.auxState.servoPos)
    print("auxState.servoVel:", robot.robot_state_pkg.auxState.servoVel)
    print("auxState.servoTorque:", robot.robot_state_pkg.auxState.servoTorque)
    for i in range(4):
        print("extAxisStatus.pos:", i,robot.robot_state_pkg.extAxisStatus[i].pos)
        print("extAxisStatus.vel:", i,robot.robot_state_pkg.extAxisStatus[i].vel)
        print("extAxisStatus.errorCode:", i,robot.robot_state_pkg.extAxisStatus[i].errorCode)
        print("extAxisStatus.ready:", i,robot.robot_state_pkg.extAxisStatus[i].ready)
        print("extAxisStatus.inPos:", i,robot.robot_state_pkg.extAxisStatus[i].inPos)
        print("extAxisStatus.alarm:", i,robot.robot_state_pkg.extAxisStatus[i].alarm)
        print("extAxisStatus.flerr:", i,robot.robot_state_pkg.extAxisStatus[i].flerr)
        print("extAxisStatus.nlimit:", i,robot.robot_state_pkg.extAxisStatus[i].nlimit)
        print("extAxisStatus.pLimit:", i,robot.robot_state_pkg.extAxisStatus[i].pLimit)
        print("extAxisStatus.mdbsOffLine:", i,robot.robot_state_pkg.extAxisStatus[i].mdbsOffLine)
        print("extAxisStatus.mdbsTimeout:", i,robot.robot_state_pkg.extAxisStatus[i].mdbsTimeout)
        print("extAxisStatus.homingStatus:", i,robot.robot_state_pkg.extAxisStatus[i].homingStatus)
    for i in range(8):
        print("extDIState:",i, robot.robot_state_pkg.extDIState[i])
        print("extDOState:", i,robot.robot_state_pkg.extDOState[i])
    for i in range(4):
        print("extAIState:", i,robot.robot_state_pkg.extAIState[i])
        print("extAOState:", robot.robot_state_pkg.extAOState[i])
    print("rbtEnableState:", robot.robot_state_pkg.rbtEnableState)
    print("jointDriverTorque0:", robot.robot_state_pkg.jointDriverTorque[0])
    print("jointDriverTorque1:", robot.robot_state_pkg.jointDriverTorque[1])
    print("jointDriverTorque2:", robot.robot_state_pkg.jointDriverTorque[2])
    print("jointDriverTorque3:", robot.robot_state_pkg.jointDriverTorque[3])
    print("jointDriverTorque4:", robot.robot_state_pkg.jointDriverTorque[4])
    print("jointDriverTorque5:", robot.robot_state_pkg.jointDriverTorque[5])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[0])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[1])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[2])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[3])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[4])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[5])
    print("year:", robot.robot_state_pkg.year)
    print("mouth:", robot.robot_state_pkg.mouth)
    print("day:", robot.robot_state_pkg.day)
    print("hour:", robot.robot_state_pkg.hour)
    print("minute:", robot.robot_state_pkg.minute)
    print("second:", robot.robot_state_pkg.second)
    print("millisecond:", robot.robot_state_pkg.millisecond)
    print("softwareUpgradeState:", robot.robot_state_pkg.softwareUpgradeState)
    print("endLuaErrCode:", robot.robot_state_pkg.endLuaErrCode)
    print("cl_analog_output[0]:", robot.robot_state_pkg.cl_analog_output[0])
    print("cl_analog_output[1]:", robot.robot_state_pkg.cl_analog_output[1])
    print("tl_analog_output:", robot.robot_state_pkg.tl_analog_output)
    print("gripperRotNum:", robot.robot_state_pkg.gripperRotNum)
    print("gripperRotSpeed:", robot.robot_state_pkg.gripperRotSpeed)
    print("gripperRotTorque:", robot.robot_state_pkg.gripperRotTorque)
    print("jt_tgt_tor:", robot.robot_state_pkg.jt_tgt_tor)
    print("smartToolState:", robot.robot_state_pkg.smartToolState)
    print("wideVoltageCtrlBoxTemp:", robot.robot_state_pkg.wideVoltageCtrlBoxTemp)
    print("wideVoltageCtrlBoxFanCurrent:", robot.robot_state_pkg.wideVoltageCtrlBoxFanCurrent)
    print("toolCoord0:", robot.robot_state_pkg.toolCoord[0])
    print("toolCoord1:", robot.robot_state_pkg.toolCoord[1])
    print("toolCoord2:", robot.robot_state_pkg.toolCoord[2])
    print("toolCoord3:", robot.robot_state_pkg.toolCoord[3])
    print("toolCoord4:", robot.robot_state_pkg.toolCoord[4])
    print("toolCoord5:", robot.robot_state_pkg.toolCoord[5])
    print("wobjCoord0:", robot.robot_state_pkg.wobjCoord[0])
    print("wobjCoord1:", robot.robot_state_pkg.wobjCoord[1])
    print("wobjCoord2:", robot.robot_state_pkg.wobjCoord[2])
    print("wobjCoord3:", robot.robot_state_pkg.wobjCoord[3])
    print("wobjCoord4:", robot.robot_state_pkg.wobjCoord[4])
    print("wobjCoord5:", robot.robot_state_pkg.wobjCoord[5])
    print("extoolCoord0:", robot.robot_state_pkg.extoolCoord[0])
    print("extoolCoord1:", robot.robot_state_pkg.extoolCoord[1])
    print("extoolCoord2:", robot.robot_state_pkg.extoolCoord[2])
    print("extoolCoord3:", robot.robot_state_pkg.extoolCoord[3])
    print("extoolCoord4:", robot.robot_state_pkg.extoolCoord[4])
    print("extoolCoord5:", robot.robot_state_pkg.extoolCoord[5])
    print("exAxisCoord0:", robot.robot_state_pkg.exAxisCoord[0])
    print("exAxisCoord1:", robot.robot_state_pkg.exAxisCoord[1])
    print("exAxisCoord2:", robot.robot_state_pkg.exAxisCoord[2])
    print("exAxisCoord3:", robot.robot_state_pkg.exAxisCoord[3])
    print("exAxisCoord4:", robot.robot_state_pkg.exAxisCoord[4])
    print("exAxisCoord5:", robot.robot_state_pkg.exAxisCoord[5])
    print("load:", robot.robot_state_pkg.load)
    print("loadCog0:", robot.robot_state_pkg.loadCog[0])
    print("loadCog1:", robot.robot_state_pkg.loadCog[1])
    print("loadCog2:", robot.robot_state_pkg.loadCog[2])
    print("lastServoTarget0:", robot.robot_state_pkg.lastServoTarget[0])
    print("lastServoTarget1:", robot.robot_state_pkg.lastServoTarget[1])
    print("lastServoTarget2:", robot.robot_state_pkg.lastServoTarget[2])
    print("lastServoTarget3:", robot.robot_state_pkg.lastServoTarget[3])
    print("lastServoTarget4:", robot.robot_state_pkg.lastServoTarget[4])
    print("lastServoTarget5:", robot.robot_state_pkg.lastServoTarget[5])
    print("servoJCmdNum:", robot.robot_state_pkg.servoJCmdNum)

Tipo de enumeración de la lista de configuración de retroalimentación de estado del robot
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:

    class RobotState(enum.Enum):
        """Enumeración de tipos de estado CNDE"""
        FrameHead = 0
        FrameCnt = 1
        DataLen = 2
        ProgramState = 3
        RobotState = 4
        MainCode = 5
        SubCode = 6
        RobotMode = 7
        JointCurPos = 8
        ToolCurPos = 9
        FlangeCurPos = 10
        ActualJointVel = 11
        ActualJointAcc = 12
        TargetTCPCmpSpeed = 13
        TargetTCPSpeed = 14
        ActualTCPCmpSpeed = 15
        ActualTCPSpeed = 16
        ActualJointTorque = 17
        Tool = 18
        User = 19
        ClDgtOutputH = 20
        ClDgtOutputL = 21
        TlDgtOutputL = 22
        ClDgtInputH = 23
        ClDgtInputL = 24
        TlDgtInputL = 25
        ClAnalogInput = 26
        TlAnglogInput = 27
        FtSensorRawData = 28
        FtSensorData = 29
        FtSensorActive = 30
        EmergencyStop = 31
        MotionDone = 32
        GripperMotiondone = 33
        McQueueLen = 34
        CollisionState = 35
        TrajectoryPnum = 36
        SafetyStop0State = 37
        SafetyStop1State = 38
        GripperFaultId = 39
        GripperFault = 40
        GripperActive = 41
        GripperPosition = 42
        GripperSpeed = 43
        GripperCurrent = 44
        GripperTemp = 45
        GripperVoltage = 46
        AuxState = 47
        ExtAxisStatus = 48
        ExtDIState = 49
        ExtDOState = 50
        ExtAIState = 51
        ExtAOState = 52
        RbtEnableState = 53
        JointDriverTorque = 54
        JointDriverTemperature = 55
        RobotTime = 56
        SoftwareUpgradeState = 57
        EndLuaErrCode = 58
        ClAnalogOutput = 59
        TlAnalogOutput = 60
        GripperRotNum = 61
        GripperRotSpeed = 62
        GripperRotTorque = 63
        WeldingBreakOffState = 64
        TargetJointTorque = 65
        SmartToolState = 66
        WideVoltageCtrlBoxTemp = 67
        WideVoltageCtrlBoxFanCurrent = 68
        ToolCoord = 69
        WobjCoord = 70
        ExtoolCoord = 71
        ExAxisCoord = 72
        Load = 73
        LoadCog = 74
        LastServoTarget = 75
        ServoJCmdNum = 76
        TargetJointPos = 77
        TargetJointVel = 78
        TargetJointAcc = 79
        TargetJointCurrent = 80
        ActualJointCurrent = 81
        ActualTCPForce = 82
        TargetTCPPos = 83
        CollisionLevel = 84
        SpeedScaleManual = 85
        SpeedScaleAuto = 86
        LuaLineNum = 87
        AbnomalStop = 88
        CurrentLuaFileName = 89
        ProgramTotalLine = 90
        SafetyBoxSingal = 91
        WeldVoltage = 92
        WeldCurrent = 93
        WeldTrackVel = 94
        TpdException = 95
        AlarmRebootRobot = 96
        ModbusMasterConnect = 97
        ModbusSlaveConnect = 98
        BtnBoxStopSignal = 99
        DragAlarm = 100
        SafetyDoorAlarm = 101
        SafetyPlaneAlarm = 102
        MotonAlarm = 103
        InterfaceAlarm = 104
        UdpCmdState = 105
        WeldReadyState = 106
        AlarmCheckEmergStopBtn = 107
        TsTmCmdComError = 108
        TsTmStateComError = 109
        CtrlBoxError = 110
        SafetyDataState = 111
        ForceSensorErrState = 112
        CtrlOpenLuaErrCode = 113
        StrangePosFlag = 114
        Alarm = 115
        DriverAlarm = 116
        AliveSlaveNumError = 117
        SlaveComError = 118
        CmdPointError = 119
        IOError = 120
        GripperError = 121
        FileError = 122
        ParaError = 123
        ExaxisOutLimitError = 124
        DriverComError = 125
        DriverError = 126
        OutSoftLimitError = 127
        AxleGenComData = 128
        SocketConnTimeout = 129
        SocketReadTimeout = 130
        TsWebStateComErr = 131
        ExaxisCoordID = 132
        ProgramRunState = 133