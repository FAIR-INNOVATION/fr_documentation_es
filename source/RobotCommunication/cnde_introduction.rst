Introducción a CNDE
========================

El protocolo de intercambio de datos de red configurable (en adelante, CNDE) del robot colaborativo es una forma mediante la cual el cliente controla el robot y obtiene el estado de retroalimentación del robot a través de la comunicación UDP.

La Tabla 1-1 muestra el conjunto de todos los estados del robot que se pueden obtener mediante CNDE. El cliente puede seleccionar libremente de la tabla cualquier cantidad de estados necesarios y hacer que el robot realice la retroalimentación de estado según el período de retroalimentación establecido.

Del mismo modo, el cliente también puede seleccionar de la Tabla 1-2 la combinación de funciones de control del robot necesarias para realizar operaciones de control del robot. Los datos de comunicación CNDE entre el cliente y el robot deben seguir el formato de trama especificado. Los puertos de comunicación CNDE del robot son 20005 y 20006; el puerto 20005 se utiliza para comunicación TCP y el puerto 20006 para comunicación UDP.

El uso de la función CNDE del robot comprende principalmente los siguientes cuatro pasos:

① Configuración del contenido de los datos de entrada y salida: el cliente envía al robot una instrucción de configuración de entrada y salida, cuyo contenido tiene la forma de una serie de nombres de funciones de control o estado como "std_DI_box,cfg_DI_box,motion_queue_len". Tras registrar e identificar estos nombres, el robot devuelve al cliente los tipos de datos de las funciones correspondientes, como "UINT8,UINT8,INT32", lo que indica que la configuración se ha realizado correctamente.

② Inicio de la salida de datos CNDE del robot: el cliente envía al robot una instrucción de inicio de salida de datos CNDE, y el robot comienza a enviar los datos de estado del robot al cliente por UDP en forma de array de bytes (modo little-endian) según el período configurado.

③ Análisis de los datos de estado del robot: el cliente recibe cíclicamente los datos de estado devueltos por el robot y, según los tipos de datos devueltos por el robot durante la configuración de salida y la longitud en bytes correspondiente a cada tipo de datos de la Tabla 1-3, realiza el análisis de datos para obtener el valor real de cada estado. La salida de datos CNDE del robot admite como máximo 4096 bytes, y el período de salida CNDE se puede configurar entre 1 y 200 ms.

④ Envío de los datos de control del robot: el cliente empaqueta los datos de control según los tipos de datos devueltos por el robot durante la configuración de entrada y la longitud en bytes correspondiente a cada tipo de datos de la Tabla 1-3, y los envía al robot mediante comunicación UDP. Tras recibir los datos de control, el robot realiza el análisis de datos y las operaciones de control del robot. La entrada CNDE del robot admite 256 recetas; el cliente puede configurar previamente varias recetas de entrada según sea necesario, y al enviar datos de entrada al robot debe especificar el número de receta correspondiente a los datos actuales.

.. centered:: Tabla 1-1 Funciones de configuración de salida del robot

.. list-table::
   :widths: 20 40 80
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nombre**
     - **Tipo de datos**
     - **Descripción**

   * - std_DI_box
     - UINT8
     - Entrada DI estándar del armario de control (bit0 ~ bit7 representan DI0 ~ DI7)

   * - cfg_DI_box
     - UINT8
     - Entrada CI configurable del armario de control (bit0 ~ bit7 representan CI0 ~ CI7)

   * - cfg_DI_tool
     - UINT8
     - Entrada DI de herramienta configurable del armario de control (bit0 ~ bit2 representan toolDI0 ~ toolDI1)

   * - std_AI0_box
     - DOUBLE
     - Entrada analógica AI0 del armario de control (0 ~ 4095)

   * - std_AI1_box
     - DOUBLE
     - Entrada analógica AI1 del armario de control (0 ~ 4095)

   * - std_AI_tool
     - DOUBLE
     - Entrada analógica de la herramienta del extremo tool_AI0 (0 ~ 4095)

   * - run_up_time
     - DOUBLE
     - Estadística del tiempo de encendido del robot (s)

   * - target_joint_pos
     - DOUBLE_6
     - Posición objetivo de las articulaciones 1-6 (°)

   * - target_joint_vel
     - DOUBLE_6
     - Velocidad objetivo de las articulaciones 1-6 (°/s)

   * - target_joint_acc
     - DOUBLE_6
     - Aceleración objetivo de las articulaciones 1-6 (°/s2)

   * - target_joint_current
     - DOUBLE_6
     - Corriente objetivo de las articulaciones 1-6 (A)

   * - target_joint_torque
     - DOUBLE_6
     - Par objetivo de las articulaciones 1-6 (Nm)

   * - actual_joint_pos
     - DOUBLE_6
     - Posición actual de las articulaciones 1-6 (°)

   * - actual_joint_vel
     - DOUBLE_6
     - Velocidad actual de las articulaciones 1-6 (°/s)

   * - actual_joint_current
     - DOUBLE_6
     - Corriente actual de las articulaciones 1-6 (A)

   * - actual_joint_torque
     - DOUBLE_6
     - Par objetivo de las articulaciones 1-6 (Nm)

   * - actual_TCP_pos
     - DOUBLE_6
     - Posición actual de la herramienta DKR (mm)

   * - actual_TCP_vel
     - DOUBLE_6
     - Velocidad actual de la herramienta DKR (mm/s)

   * - actual_TCP_force
     - DOUBLE_6
     - Fuerza resultante de la herramienta DKR (N)

   * - target_TCP_pos
     - DOUBLE_6
     - Posición objetivo de la herramienta DKR (mm)

   * - target_TCP_vel
     - DOUBLE_6
     - Velocidad objetivo de la herramienta DKR (mm/s)

   * - std_DO_box
     - UINT8
     - Salida DO estándar del armario de control (bit0 ~ bit7 representan DO0 ~ DO7)

   * - cfg_DO_box
     - UINT8
     - Salida CO configurable del armario de control (bit0 ~ bit7 representan CO0 ~ CO7)

   * - cfg_DO_tool
     - UINT8
     - Salida DO de herramienta estándar del armario de control (bit0 ~ bit1 representan toolDO0 ~ toolDO1)

   * - std_AO0_box
     - DOUBLE
     - Salida analógica AO0 del armario de control (0.0 ~ 4095.0)

   * - std_AO1_box
     - DOUBLE
     - Salida analógica AO1 del armario de control (0.0 ~ 4095.0)

   * - std_AO_tool
     - DOUBLE
     - Salida analógica de la herramienta AO1 (0.0 ~ 4095.0)

   * - robot_mode
     - UINT8
     - Modo del robot (0-automático; 1-manual)

   * - collision_level
     - UINT8_6
     - Nivel de colisión de las articulaciones 1-6 (1 ~ 10)

   * - speed_scaling_man
     - DOUBLE
     - Porcentaje de velocidad en modo manual (0 ~ 100)

   * - speed_scaling_auto
     - DOUBLE
     - Porcentaje de velocidad en modo automático (0 ~ 100)

   * - program_state
     - UINT8
     - Estado de ejecución del programa del robot (1-detendido; 2-en movimiento; 3-en pausa; 4-arrastre)

   * - line_number
     - INT32
     - Número de línea actual en ejecución del programa

   * - payload
     - DOUBLE
     - Masa de la carga (kg)

   * - pay_cog
     - DOUBLE_3
     - Centro de gravedad de la carga (x,y,z) (mm)

   * - motion_queue_len
     - INT32
     - Longitud actual de la cola de movimiento
   
   * - ft_sensor_data
     - DOUBLE_6
     - Datos brutos del sensor de fuerza

   * - main_code
     - INT32
     - Código de fallo principal

   * - sub_code
     - INT32
     - Código de fallo secundario

   * - emergency_stop
     - UINT8
     - Estado de parada de emergencia

   * - motion_done
     - INT32
     - Estado de finalización del movimiento

   * - timestamp_us
     - UINT64
     - Hora del sistema del robot (us)

   * - output_BIT_reg_8xX
     - UINT8_X
     - Registro de salida de tipo BIT del robot (8xX indica el número de registros; si necesita 16 registros de salida de tipo BIT, el nombre real es "output_BIT_reg_8x2"; el robot admite como máximo 128 registros de tipo BIT)

   * - output_INT_reg_X
     - INT32_X
     - Registro de salida de tipo INT del robot (X indica el número de registros; si necesita 16 registros de salida de tipo INT, el nombre real es "output_INT_reg_16"; el robot admite como máximo 64 registros de tipo INT)

   * - output_DOUBLE_reg_X
     - DOUBLE_X
     - Registro de salida de tipo DOUBLE del robot (X indica el número de registros; si necesita 16 registros de salida de tipo DOUBLE, el nombre real es "output_DOUBLE_reg_16"; el robot admite como máximo 64 registros de tipo DOUBLE)

   * - servoj_time
     - UINT64_5
     - Datos de marca de tiempo servoj, en nanosegundos

   * - actual_joint_temp
     - DOUBLE_6
     - Temperatura del accionamiento de las articulaciones j1-j6, en °

   * - axle_gen_com_data
     - UINT8_130
     - Datos periódicos generales del extremo

   * - abnormal_stop
     - UINT8
     - Estado anómalo, 0: sin anomalía, 1: con anomalía

   * - cur_lua_file_name
     - UINT8_256
     - Nombre del archivo lua en ejecución actual

   * - prog_total_line
     - UINT8
     - Número total de líneas del archivo actual

   * - safety_box_signal
     - UINT8_6
     - Señal de los botones de la caja de botones 0: pulsado  1: liberado

   * - welding_voltage
     - DOUBLE
     - Tensión de soldadura real, en V

   * - welding_current
     - DOUBLE
     - Corriente de soldadura real, en A

   * - welding_track_speed
     - DOUBLE
     - Velocidad de seguimiento de la soldadura mm/s

   * - tpd_exception
     - UINT8
     - Excepción TPD

   * - alarm_reboot_robot
     - UINT8
     - Advertencia de reinicio del robot

   * - modbus_master_connect
     - UINT8
     - | Estado de conexión de los 8 maestros Modbus  
       | bit0-bit7 representan los maestros 0-7: 0-no conectado, 1-conectado

   * - modbus_slave_connect
     - UINT8
     - Estado de conexión del esclavo Modbus 0-no conectado 1-conectado

   * - btn_box_stop_signal
     - UINT8
     - Señal del botón de parada de emergencia

   * - drag_alarm
     - UINT8
     - Advertencia de arrastre

   * - safety_door_alarm
     - UINT8
     - Advertencia de puerta de seguridad, 0 sin advertencia, 1 puerta de seguridad activada

   * - safety_plane_alarm
     - UINT8
     - Advertencia de pared de seguridad, 0 sin advertencia, 1 entrada en la pared de seguridad

   * - motion_alarm
     - UINT8
     - | Advertencia de movimiento, 0-sin advertencia,
       | 1-cambio excesivo de orientación en la instrucción LIN,  
       | 2-TCP con exceso de velocidad,
       | 3-colisión producida,  
       | 4-eje 1 supera la velocidad máxima,
       | 5-eje 2 supera la velocidad máxima,  
       | 6-eje 3 supera la velocidad máxima,
       | 7-eje 4 supera la velocidad máxima,  
       | 8-eje 5 supera la velocidad máxima,
       | 9-eje 6 supera la velocidad máxima,  
       | 10-desviación excesiva entre instrucción y retroalimentación del eje 1,
       | 11-desviación excesiva entre instrucción y retroalimentación del eje 2,  
       | 12-desviación excesiva entre instrucción y retroalimentación del eje 3,
       | 13-desviación excesiva entre instrucción y retroalimentación del eje 4,  
       | 14-desviación excesiva entre instrucción y retroalimentación del eje 5,
       | 15-desviación excesiva entre instrucción y retroalimentación del eje 6,  
       | 16-posición singular,
       | 17-adaptación de velocidad de movimiento en la instrucción LIN,  
       | 18-tiempo de espera agotado en el ajuste de velocidad objetivo o ajuste de velocidad no completado,
       | 19-fallo en el movimiento de inserción rotativa,  
       | 20-fallo en el movimiento de inserción helicoidal,
       | 21-fallo en el movimiento de inserción lineal,  
       | 22-fallo en el movimiento de localización de superficie

   * - interfere_alarm
     - UINT8
     - Advertencia de zona de interferencia, 0 sin advertencia, 1 entrada en la zona de interferencia

   * - udp_cmd_state
     - INT32
     - Estado de conexión UDP

   * - weld_ready_state
     - UINT8
     - Estado de preparación de la soldadora, 1: preparada, 0: error de la soldadora

   * - alarm_check_emerg_stop_btn
     - UINT8
     - Advertencia de comunicación anómala de las articulaciones

   * - ts_tm_cmd_com_error
     - UINT8
     - Error de instrucción del sistema de par

   * - ts_tm_state_com_error
     - UINT8
     - Error de estado del sistema de par

   * - ctrl_box_error
     - INT32
     - Error del armario de control

   * - safety_data_state
     - UINT8
     - Indicador de estado de los datos de seguridad, 0 sin anomalía, 1-anomalía

   * - force_sensor_err_state
     - UINT8
     - Fallo por tiempo de espera agotado en la conexión del sensor de fuerza; bit0-bit1 corresponden a los ID de sensor de fuerza ID1-ID2

   * - ctrl_open_lua_errcode
     - UINT8_4
     - Código de error del protocolo abierto del controlador

   * - servo_id
     - UINT8
     - Número de ID del accionamiento servo

   * - servo_errcode
     - INT32
     - Código de fallo del accionamiento servo

   * - servo_state
     - INT32
     - Estado del accionamiento servo

   * - servo_actual_pos
     - DOUBLE
     - Posición actual del servo

   * - servo_actual_speed
     - DOUBLE
     - Velocidad actual del servo
   
   * - servo_actual_torque
     - DOUBLE
     - Par actual del servo
   
   * - gripper_active
     - INT32
     - Estado de activación de la pinza
   
   * - gripper_position
     - UINT8
     - Retroalimentación de posición de la pinza (porcentaje)
   
   * - gripper_speed
     - INT32
     - Retroalimentación de velocidad de la pinza (porcentaje)
   
   * - gripper_current
     - INT32
     - Retroalimentación de corriente de la pinza (porcentaje)
   
   * - gripper_temp
     - INT32
     - Temperatura actual de la pinza, en °
   
   * - gripper_voltage
     - INT32
     - Tensión actual de la pinza, en V
   
   * - rotating_gripper_num
     - DOUBLE
     - Retroalimentación del número de vueltas de la pinza rotativa
   
   * - rotating_gripper_speed
     - UINT8
     - Retroalimentación de la velocidad de rotación de la pinza rotativa (porcentaje)
   
   * - rotating_gripper_tor
     - UINT8
     - Retroalimentación del par de rotación de la pinza rotativa (porcentaje)
   
   * - weld_break_off_state
     - UINT8
     - Estado de interrupción de la soldadura: 0-soldadura no interrumpida   1-soldadura interrumpida
   
   * - weld_arc_state
     - UINT8
     - Estado del arco de soldadura 0-arco no interrumpido 1-arco interrumpido
   
   * - smarttool_state
     - UINT32
     - Datos de E/S de expansión del extremo (Smart-Tool)
   
   * - tool_coord
     - DOUBLE_6
     - Pose actual de la herramienta respecto al extremo
   
   * - wobj_coord
     - DOUBLE_6
     - Pose actual de la pieza respecto a la base
   
   * - exTool_coord
     - DOUBLE_6
     - Pose actual de la herramienta externa respecto a la herramienta
   
   * - exAxis_coord
     - DOUBLE_6
     - Pose actual del eje externo respecto al sistema de coordenadas base
   
   * - robot_state
     - UINT8
     - | Estado de funcionamiento del robot, 
       | 1. detenido; 2. en movimiento; 3. en pausa; 4. arrastre
   
   * - actual_flange_pos
     - DOUBLE_6
     - Pose real del extremo
   
   * - target_TCP_cmpvel
     - DOUBLE_2
     - Velocidad lineal y de orientación de la instrucción TCP, en mm/s y °/s
   
   * - actual_TCP_cmpvel
     - DOUBLE_2
     - Velocidad lineal y de orientación real del TCP, en mm/s y °/s
   
   * - tool_id
     - INT32
     - Número de herramienta
   
   * - wobj_id
     - INT32
     - Número de pieza
   
   * - ft_sensor_raw_data
     - DOUBLE_6
     - Datos brutos de fuerza/par del extremo en el sistema de coordenadas del sensor
   
   * - ft_sensor_active
     - UINT8
     - Estado de activación del sensor de fuerza/par
   
   * - gripper_motion_done
     - UINT8
     - Movimiento de la pinza completado
   
   * - collision_state
     - UINT8
     - Estado de detección de colisión
   
   * - trajectory_pnum
     - INT32
     - Número de secuencia actual del movimiento de puntos discretos
   
   * - safety_stop0_state
     - UINT8
     - Estado de la señal de parada de seguridad SI0
   
   * - safety_stop1_state
     - UINT8
     - Estado de la señal de parada de seguridad SI1
   
   * - gripper_fault_id
     - UINT8
     - Número de pinza con error
   
   * - gripper_fault
     - INT32
     - Número de error de la pinza
   
   * - ext_DI_state
     - UINT8_16
     - DI de expansión
   
   * - ext_DO_state
     - UINT8_16
     - DO de expansión
   
   * - ext_AI_state
     - INT32_4
     - AI de expansión
   
   * - ext_AO_state
     - INT32_4
     - AO de expansión
   
   * - rbt_enable_state
     - INT32
     - Estado de finalización de habilitación del accionamiento
   
   * - joint_driver_torque
     - DOUBLE_6
     - Valor de par real de las articulaciones j1-j6, en Nm
   
   * - robot_time
     - INT32_7
     - Hora del sistema del robot: año, mes, día, hora, minuto, segundo, milisegundo
   
   * - software_upgrade_state
     - INT32
     - Estado de actualización del software del robot
   
   * - end_lua_err_code
     - INT32
     - Estado de la señal de los botones del extremo
   
   * - wide_voltage_ctrl_box_temp
     - DOUBLE
     - Temperatura del armario de control de tensión amplia, en °
   
   * - wide_voltage_ctrl_box_fan_current
     - INT32
     - Corriente del ventilador del armario de control de tensión amplia
   
   * - last_servoJ_target
     - DOUBLE_6
     - Pose de la última instrucción objetivo servoJ
   
   * - servoJ_cmd_num
     - INT32
     - Contador de instrucciones servoJ
   
   * - strange_pos_flag
     - UINT8
     - Indicador de posición singular
   
   * - alarm
     - UINT8
     - | Advertencia, 0-sin advertencia,  
       | 1-cambio de configuración de la articulación del hombro,
       | 2-cambio de configuración de la articulación del codo,  
       | 3-cambio de configuración de la articulación de la muñeca,
       | 4-fallo en la inicialización de RPY,  
       | 5-tiempo de espera agotado en WaitDI,
       | 6-tiempo de espera agotado en WaitAI,  
       | 7-tiempo de espera agotado en WaitToolDI,
       | 8-tiempo de espera agotado en WaitToolAI,  
       | 9-DI de éxito de inicio de arco no configurado,
       | 10-tiempo de espera agotado en WaitAuxDI,  
       | 11-tiempo de espera agotado en WaitAuxAI,
       | 12-existen puntos inalcanzables en la trayectoria de oscilación,  
       | 13-fallo en el cálculo del punto de agarre del seguimiento de cinta transportadora,
       | 14-datos anómalos del sensor de par de las articulaciones
   
   * - dr_alarm
     - UINT8
     - | Advertencia del accionamiento, 0-sin advertencia,
       | 1-advertencia del accionamiento del eje 1, reajustable,  
       | 2-advertencia del accionamiento del eje 2, reajustable,
       | 3-advertencia del accionamiento del eje 3, reajustable,  
       | 4-advertencia del accionamiento del eje 4, reajustable,
       | 5-advertencia del accionamiento del eje 5, reajustable,  
       | 6-advertencia del accionamiento del eje 6, reajustable
   
   * - alive_slave_num_error
     - UINT8
     - Fallo del número de esclavos activos, 0-sin fallo, 1-error, no reajustable
   
   * - slave_com_error
     - UINT8_8
     - | Fallo de comunicación del esclavo, 0-sin fallo,
       | 1-esclavo desconectado,  
       | 2-estado del esclavo inconsistente con el valor configurado,
       | 3-esclavo no configurado,  
       | 4-error de configuración del esclavo,
       | 5-error de inicialización del esclavo,  
       | 6-error de inicialización de la comunicación por buzón del esclavo
   
   * - cmd_point_error
     - UINT8
     - | Fallo del punto de instrucción, 0-sin fallo,
       | 1-error del punto de instrucción de articulación,  
       | 2-error del punto objetivo de línea recta,
       | 3-error del punto intermedio del arco,  
       | 4-error del punto objetivo del arco,
       | 5-distancia entre puntos de instrucción del arco demasiado pequeña,  
       | 6-error del punto intermedio 1 del círculo completo/hélice,
       | 7-error del punto intermedio 2 del círculo completo/hélice,  
       | 8-error del punto intermedio 3 del círculo completo/hélice,
       | 9-distancia entre puntos de instrucción del círculo completo/hélice demasiado pequeña,  
       | 10-error del punto de instrucción TPD,
       | 11-la herramienta de la instrucción TPD no coincide con la herramienta actual,  
       | 12-desviación excesiva entre la instrucción actual y el punto inicial de la siguiente instrucción TPD,
       | 13-error de conmutación de herramienta interna/externa,  
       | 14-error del punto de inicio de la nueva hélice,
       | 15-error del punto de instrucción de la nueva curva spline,  
       | 17-instrucción de articulación PTP fuera de límite,
       | 18-instrucción de articulación TPD fuera de límite,  
       | 19-instrucción de articulación LIN\ARC fuera de límite,
       | 20-instrucción con exceso de velocidad en el espacio cartesiano,  
       | 21-instrucción de par fuera de límite en el espacio de articulaciones,
       | 22-instrucción de articulación JOG fuera de límite,  
       | 23-instrucción con exceso de velocidad en el espacio de articulaciones del eje 1,
       | 24-instrucción con exceso de velocidad en el espacio de articulaciones del eje 2,  
       | 25-instrucción con exceso de velocidad en el espacio de articulaciones del eje 3,
       | 26-instrucción con exceso de velocidad en el espacio de articulaciones del eje 4,  
       | 27-instrucción con exceso de velocidad en el espacio de articulaciones del eje 5,
       | 28-instrucción con exceso de velocidad en el espacio de articulaciones del eje 6,  
       | 29-velocidad de retroalimentación de la articulación con exceso de velocidad,
       | 30-desviación excesiva entre instrucción y retroalimentación de la articulación,  
       | 31-error del punto objetivo DMP (incluida la no coincidencia de herramienta),
       | 32-velocidad TCP con exceso de velocidad,  
       | 33-cambio de configuración de la articulación de la siguiente instrucción,
       | 34-cambio de configuración de la articulación de la instrucción actual,  
       | 35-velocidad de la articulación con exceso de velocidad en la instrucción LIN,
       | 36-velocidad adaptativa de la instrucción LIN supera el umbral,  
       | 37-existen puntos inalcanzables en la trayectoria,
       | 38-existen puntos inalcanzables en la trayectoria - posición singular,  
       | 49-no se permiten instrucciones PTP y SPTP entre ARCSTART y ARCEND,
       | 50-no se permiten instrucciones PTP y SPTP entre WEAVESTART y WEAVEEND,  
       | 51-error en los parámetros de soldadura oscilante,
       | 52-distancia entre puntos de instrucción de soldadura oscilante demasiado pequeña,  
       | 53-existen puntos inalcanzables en la trayectoria de oscilación - posición singular,
       | 54-existen puntos inalcanzables en la trayectoria de oscilación - instrucción de articulación fuera de límite,
       | 55-existen puntos inalcanzables en la trayectoria de oscilación - anomalía de planificación (coincidencia del ángulo entre la Z de la herramienta y la dirección de avance X),
       | 56-existen puntos inalcanzables en la trayectoria de oscilación - anomalía de planificación (error en el punto de ruta del arco),
       | 65-desviación excesiva de la instrucción del sensor láser,  
       | 66-interrupción de la instrucción del sensor láser, finalización anticipada del seguimiento de soldadura,
       | 81-velocidad de la instrucción del eje externo con exceso de velocidad,  
       | 82-desviación excesiva entre instrucción y retroalimentación del eje externo,
       | 83-interrupción de comunicación del periférico de expansión (eje externo/IO),  
       | 84-anomalía por pérdida de paquetes en la comunicación del periférico de expansión (eje externo/IO),
       | 85-instrucción con exceso de velocidad en el espacio de articulaciones del eje externo 1,  
       | 86-instrucción con exceso de velocidad en el espacio de articulaciones del eje externo 2,
       | 87-instrucción con exceso de velocidad en el espacio de articulaciones del eje externo 3,  
       | 88-instrucción con exceso de velocidad en el espacio de articulaciones del eje externo 4,
       | 89-error de comunicación Ethercat del periférico de expansión (eje externo/IO),  
       | 90-error de comunicación Canopen del periférico de expansión (eje externo/IO),
       | 97-seguimiento de cinta transportadora - cambio excesivo de orientación entre el punto inicial y el punto de referencia,  
       | 113-control de fuerza constante - superación de la distancia máxima de ajuste en dirección X,
       | 114-control de fuerza constante - superación de la distancia máxima de ajuste en dirección Y,  
       | 115-control de fuerza constante - superación de la distancia máxima de ajuste en dirección Z,
       | 116-control de fuerza constante - superación del ángulo máximo de ajuste en dirección RX,  
       | 117-control de fuerza constante - superación del ángulo máximo de ajuste en dirección RY,
       | 118-control de fuerza constante - superación del ángulo máximo de ajuste en dirección RZ,  
       | 119-error en los datos del sensor externo,
       | 120-fallo en el movimiento de exploración helicoidal,  
       | 121-fallo en el movimiento de inserción rotativa,
       | 122-fallo en el movimiento de inserción lineal,  
       | 123-fallo en el movimiento de localización de superficie,
       | 124-anomalía de la fuerza de arrastre, fallo al entrar en arrastre,  
       | 129-superación del número máximo de puntos de registro de par,
       | 130-error de conmutación de velocidad,  
       | 131-orientación de la herramienta fuera de límite,  
       | 132-cantidad de movimiento fuera de límite,
       | 133-potencia fuera de límite,  
       | 134-anomalía de diagnóstico STL-Flash,  
       | 135-anomalía de diagnóstico STL-RAM,
       | 136-anomalía de diagnóstico STL-CPU,  
       | 137-anomalía de datos de seguridad ECAT de la placa de seguridad II,
       | 138-anomalía de datos de seguridad ECAT del eje 1,  
       | 139-anomalía de datos de seguridad ECAT del eje 2,
       | 140-anomalía de datos de seguridad ECAT del eje 3,  
       | 141-anomalía de datos de seguridad ECAT del eje 4,
       | 142-anomalía de datos de seguridad ECAT del eje 5,  
       | 143-anomalía de datos de seguridad ECAT del eje 6,
       | 145-anomalía de comunicación entre la placa de seguridad y el controlador,  
       | 147-error de seguimiento del punto focal,
       | 148-velocidad de orientación con exceso de velocidad,  
       | 149-anomalía en la retroalimentación de la palabra de estado de la articulación
   
   * - IO_error
     - UINT8
     - | Fallo de IO, 0-sin fallo,
       | 1-error de canal, reajustable,  
       | 2-error de valor, reajustable,
       | 3-tiempo de espera agotado en WaitDI, reajustable,  
       | 4-tiempo de espera agotado en WaitAI, reajustable,
       | 5-tiempo de espera agotado en WaitAxleDI, reajustable,  
       | 6-tiempo de espera agotado en WaitAxleAI, reajustable,
       | 7-función mal configurada en el canal, reajustable,  
       | 8-tiempo de espera agotado en el inicio de arco, reajustable,
       | 9-tiempo de espera agotado en el cierre de arco, reajustable,  
       | 10-tiempo de espera agotado en la búsqueda de posición, reajustable,
       | 11-tiempo de espera agotado en la detección de IO de la cinta transportadora, reajustable,  
       | 12-tiempo de espera agotado en WaitAuxDI, reajustable,
       | 13-tiempo de espera agotado en WaitAuxAI, reajustable,  
       | 14-tiempo de espera agotado en la búsqueda de posición del alambre de soldadura, reajustable
   
   * - gripper_error
     - UINT8
     - Fallo de la pinza, 0-sin fallo, 1-error por tiempo de espera agotado en el movimiento de la pinza, reajustable
   
   * - file_error
     - UINT8
     - | Fallo del archivo de configuración, 0-sin fallo,
       | 1-error de versión del archivo de configuración zbt, error de inicialización-no reajustable,
       | 2-fallo al cargar el archivo de configuración zbt, error de inicialización-no reajustable,
       | 3-error de versión del archivo de configuración user, error de inicialización-no reajustable,
       | 4-fallo al cargar el archivo de configuración user, error de inicialización-no reajustable,
       | 5-error de versión del archivo de configuración exaxis, error de inicialización-no reajustable,
       | 6-fallo al cargar el archivo de configuración exaxis, error de inicialización-no reajustable,
       | 7-modelo de robot inconsistente, es necesario volver a configurarlo-no reajustable,
       | 8-error de versión del archivo de configuración dhpara, error de inicialización-no reajustable,
       | 9-fallo al cargar el archivo de configuración dhpara, error de inicialización-no reajustable,
       | 10-modelo de robot no configurado-no reajustable,
       | 11-error de versión del archivo de configuración load, error de inicialización-no reajustable,
       | 12-fallo al cargar el archivo de configuración load, error de inicialización-no reajustable,
       | 13-error de versión del archivo de configuración speed, error de inicialización-no reajustable,
       | 14-fallo al cargar el archivo de configuración speed, error de inicialización-no reajustable,
       | 15-error de versión del archivo de configuración weavepara, error de inicialización-no reajustable,
       | 16-fallo al cargar el archivo de configuración weavepara, error de inicialización-no reajustable
   
   * - para_error
     - UINT8
     - | Fallo de parámetros de configuración, 0-sin fallo,
       | 1-error de número de herramienta fuera de límite-reajustable,  
       | 2-error de umbral de finalización de posicionamiento-reajustable,
       | 3-error de nivel de colisión-reajustable,  
       | 4-error de peso de carga-reajustable,
       | 5-error de centro de gravedad de carga X-reajustable,  
       | 6-error de centro de gravedad de carga Y-reajustable,
       | 7-error de centro de gravedad de carga Z-reajustable,  
       | 8-error de tiempo de filtro DI-reajustable,
       | 9-error de tiempo de filtro AxleDI-reajustable,  
       | 10-error de tiempo de filtro AI-reajustable,
       | 11-error de tiempo de filtro AxleAI-reajustable,  
       | 12-error de rango de nivel alto/bajo DI-reajustable,
       | 13-error de rango de nivel alto/bajo DO-reajustable,  
       | 14-error de número de pieza fuera de límite-reajustable,
       | 15-error de número de eje externo fuera de límite-reajustable,  
       | 16-seguimiento de cinta transportadora - error de canal de codificador-reajustable,
       | 17-seguimiento de cinta transportadora - error de número de eje de pieza-reajustable,  
       | 18-FR30L modo de instalación - error de no instalación vertical-reajustable
   
   * - exaxis_out_slimit_error
     - UINT8
     - | Fallo de límite software del eje externo, 0-sin fallo,
       | 1-fallo por superación del límite software del eje externo 1, reajustable,  
       | 2-fallo por superación del límite software del eje externo 2, reajustable,
       | 3-fallo por superación del límite software del eje externo 3, reajustable,  
       | 4-fallo por superación del límite software del eje externo 4, reajustable,
       | 5-fallo por superación del límite software del eje externo 5, reajustable,  
       | 6-fallo por superación del límite software del eje externo 6, reajustable
   
   * - dr_com_err
     - UINT8_6
     - Fallo de comunicación del accionamiento, 0-sin fallo, 1-fallo
   
   * - dr_err
     - UINT8
     - | Fallo del accionamiento, 0-sin fallo,
       | 1-fallo del accionamiento del eje 1, no reajustable,  
       | 2-fallo del accionamiento del eje 2, no reajustable,
       | 3-fallo del accionamiento del eje 3, no reajustable,  
       | 4-fallo del accionamiento del eje 4, no reajustable,
       | 5-fallo del accionamiento del eje 5, no reajustable,  
       | 6-fallo del accionamiento del eje 6, no reajustable
   
   * - out_sflimit_err
     - UINT8
     - | Fallo de límite software, 0-sin fallo,
       | 1-fallo por superación del límite software del eje 1, reajustable,  
       | 2-fallo por superación del límite software del eje 2, reajustable,
       | 3-fallo por superación del límite software del eje 3, reajustable,  
       | 4-fallo por superación del límite software del eje 4, reajustable,
       | 5-fallo por superación del límite software del eje 5, reajustable,  
       | 6-fallo por superación del límite software del eje 6, reajustable

.. centered:: Tabla 1-2 Funciones de configuración de control de entrada del robot

.. list-table::
   :widths: 20 40 80
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nombre**
     - **Tipo de datos**
     - **Descripción**

   * - speed_mask
     - UINT8
     - Máscara de configuración de velocidad global: 0-no efectiva; 1-efectiva

   * - speed
     - UINT8
     - Configurar la velocidad global (0-100)

   * - std_DO_mask
     - UINT8
     - Máscara de control de salida DO estándar del armario de control (bit0 ~ bit7 representan DO0 ~ DO7)

   * - std_DO_box
     - UINT8
     - Salida DO estándar del armario de control (bit0 ~ bit7 representan DO0 ~ DO7)

   * - cfg_DO_mask
     - UINT8
     - Máscara de control de salida CO configurable del armario de control (bit0 ~ bit7 representan CO0 ~ CO7)

   * - cfg_DO_box
     - UINT8
     - Salida CO configurable del armario de control (bit0 ~ bit7 representan CO0 ~ CO7)

   * - cfg_DO_tool_mask
     - UINT8
     - Máscara de control de salida DO de herramienta estándar del armario de control (bit0 ~ bit1 representan toolDO0 ~ toolDO1)

   * - cfg_DO_tool
     - UINT8
     - Salida DO de herramienta estándar del armario de control (bit0 ~ bit1 representan toolDO0 ~ toolDO1)

   * - std_AO_mask
     - UINT8
     - Máscara de control de salida analógica del robot (bit0 ~ bit1 representan AO0 ~ AO1 del armario de control; bit2 representa AO0 de la herramienta)

   * - std_AO0_box
     - DOUBLE
     - Salida analógica AO0 del armario de control (0.0 ~ 4095.0)

   * - std_AO1_box
     - DOUBLE
     - Salida analógica AO1 del armario de control (0.0 ~ 4095.0)

   * - std_AO0_tool
     - DOUBLE
     - Salida analógica de la herramienta AO1 (0.0 ~ 4095.0)

   * - input_BIT_reg_8xX
     - UINT8_X
     - Registro de entrada de tipo BIT del robot (8xX indica el número de registros; si necesita 16 registros de entrada de tipo BIT, el nombre real es "input_BIT_reg_8x2"; el robot admite como máximo 128 registros de tipo BIT)

   * - input_INT_reg_X
     - INT32_X
     - Registro de entrada de tipo INT del robot (X indica el número de registros; si necesita 16 registros de entrada de tipo INT, el nombre real es "input_INT_reg_16"; el robot admite como máximo 64 registros de tipo INT)
  
   * - input_DOUBLE_reg_X
     - DOUBLE_X
     - Registro de entrada de tipo DOUBLE del robot (X indica el número de registros; si necesita 16 registros de entrada de tipo DOUBLE, el nombre real es "input_DOUBLE_reg_16"; el robot admite como máximo 64 registros de tipo DOUBLE)

.. centered:: Tabla 1-3 Correspondencia entre tipos de datos y longitud en bytes

.. list-table::
   :widths: 60 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Tipo de datos**
     - **Longitud en bytes**

   * - UINT8
     - 1

   * - INT32
     - 4

   * - DOUBLE
     - 8

   * - UINT8_X
     - 1*X

   * - INT32_X
     - 4*X

   * - DOUBLE_X
     - 8*X