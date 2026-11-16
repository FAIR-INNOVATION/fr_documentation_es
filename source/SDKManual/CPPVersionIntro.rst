Descripción de actualización de versión
========================================

.. toctree:: 
    :maxdepth: 5

.. list-table::
   :widths: 10 10 30
   :header-rows: 0
   :align: center

   * - **Número de versión**
     - **Fecha**
     - **Descripción de la actualización**

   * - V4.0.1
     - 2026-10-27
     - | 1.Modificar la descripción de los parámetros de las instrucciones GetGripperMotionDone() para obtener el estado de movimiento de la pinza y GripperWaitMotionDone() para esperar a que finalice el movimiento de la pinza; el parámetro de estado de movimiento de la pinza añade el estado de detección de caída de objeto al completarse el movimiento;
       | 2.Modificar la instrucción ServoMoveStart() de inicio de movimiento servo, añadiendo la configuración de parámetros de tiempo de filtrado y ganancia;
       | 3.Añadir las instrucciones DataPackageUpgrade() y GetDataPackageUpgradeProgress() para la carga y actualización del paquete de copia de seguridad de datos del robot y la obtención del porcentaje de progreso de la actualización, junto con ejemplos de código;
       | 4.Añadir la instrucción GetJointAllParamUpgradeProgress() para obtener el porcentaje de progreso de la actualización de todos los parámetros de las articulaciones del robot, junto con un ejemplo de código;

   * - V4.0.0
     - 2026-09-23
     - | 1.Modificar la interfaz de instanciación del robot FRRobot(), añadiendo la configuración del parámetro de habilitación del cifrado TLS para la comunicación del protocolo de instrucciones integrado en el SDK;
       | 2.Modificar la descripción de los parámetros de la interfaz SetWeldMachineCtrlMode() para establecer el modo de control de la máquina de soldar, añadiendo los modos con pulso y sin pulso de la máquina de soldar Panasonic;
       | 3.Añadir la instrucción SendTCPFrame() para enviar tramas de instrucciones personalizadas a través de TCP 8080, junto con un ejemplo de código;
       | 4.Añadir la instrucción TCFToAllJoint() para obtener las 8 soluciones de cinemática inversa del robot, junto con un ejemplo de código;
       | 5.Añadir la instrucción SetPhySpeedInstant() para establecer la velocidad física en tiempo real, junto con un ejemplo de código;
       | 6.Añadir la instrucción MtlsLink() para establecer la ruta del certificado de cifrado de comunicación TLS del protocolo de instrucciones integrado en el SDK, junto con un ejemplo de código;
       | 7.Añadir la descripción de algunos códigos de error del SDK.

   * - V3.9.9
     - 2026-09-01
     - | 1.Modificar la descripción de los parámetros de la interfaz GetGripperMotionDone() para obtener el estado de la pinza, actualizando la definición del estado de la pinza;
       | 2.Modificar la interfaz GetInverseKinExaxis() de solución de cinemática inversa que incluye la posición del eje extendido, añadiendo el parámetro de configuración de articulaciones, con valor predeterminado -1 para referenciar la configuración actual de articulaciones;
       | 3.Modificar las interfaces de control de fuerza FT_SpiralSearch(), FT_LinInsertion() y FT_FindSurface(), añadiendo el parámetro de estrategia de tratamiento cuando no se detecta fuerza/par;
       | 4.Modificar la descripción de los parámetros de las interfaces SetDIConfig(), GetDIConfig(), SetDOConfig() y GetDOConfig() de configuración de funciones CIO de la caja de control del robot, actualizando los nombres de función y códigos de función añadidos;
       | 5.Modificar el ejemplo de código de control básico del robot, añadiendo un ejemplo de código de conmutación del modo manual de alta velocidad;
       | 6.Añadir la instrucción ServoJ() de movimiento en modo servo del espacio de articulaciones (entrada de múltiples puntos), junto con un ejemplo de código;
       | 7.Añadir las instrucciones GetSafetyParamsCheckSum() para obtener la suma de verificación de los parámetros de configuración de seguridad y SafetyOPPasswordCheck() para la verificación de la contraseña de operación de seguridad, junto con ejemplos de código;
       | 8.Añadir la instrucción GripperWaitMotionDone() para esperar a que finalice el movimiento de la pinza, junto con un ejemplo de código;
       | 9.Añadir la instrucción SetRobotTime() para sincronizar la hora del sistema con el robot, junto con un ejemplo de código;
       | 10.Añadir SetSafetyDIConfig() para la configuración de la función CI de doble canal de seguridad, SetSafetyDOConfig() para la configuración de la función CO de doble canal de seguridad, junto con ejemplos de código;
       | 11.Añadir la instrucción HiSpeedManualSwitch() para conmutar el modo manual de alta velocidad;
       | 12.Añadir un ejemplo de código de superposición de oscilación durante la reproducción de trayectoria del sensor láser;

   * - V3.9.8
     - 2026-07-27
     - | 1.Actualizar la estructura de retroalimentación de estado del robot, añadiendo el estado de ejecución actual del programa lua del robot, 0-programa no en ejecución; 1-programa en ejecución (incluye programa pausado);
       | 2.Actualizar la descripción de los parámetros de las interfaces SetExToolCoord() y SetExToolList() para establecer el sistema de coordenadas de herramienta externa y la lista de sistemas de coordenadas de herramienta, donde el número del sistema de coordenadas de herramienta externa se actualiza a 20-39. Y actualizar el ejemplo de código de operación del sistema de coordenadas de herramienta externa.
       | 3.La interfaz GetToolCoordWithID() para obtener los parámetros del sistema de coordenadas de herramienta añade la obtención de los parámetros de tipo de herramienta, posición de instalación, ID de herramienta y número de carga.
       | 4.La interfaz GetWObjCoordWithID() para obtener los parámetros del sistema de coordenadas de la pieza añade la obtención del parámetro del sistema de coordenadas de referencia;
       | 5.La interfaz GetExToolCoordWithID() para obtener los parámetros del sistema de coordenadas de herramienta externa añade la obtención del parámetro de pose del sistema de coordenadas de la pieza instalada en el extremo del robot.
       | 6.La interfaz GetExAxisCoordWithID() para obtener los parámetros del sistema de coordenadas del eje extendido añade la obtención de los parámetros de número de eje extendido y marca de calibración.
       | 7.La interfaz SetVelReducePara() para establecer la velocidad de seguridad del robot añade la configuración del parámetro de velocidad de seguridad de las articulaciones del robot.
       | 8.En el ejemplo de código de configuración de los parámetros de soldadura se añade un ejemplo de obtención del modo de control de la máquina de soldar.
       | 9.En el ejemplo de código de configuración de las señales de soldadura de IO extendida se añade un ejemplo de código de obtención de la configuración de funciones de DI extendida y DO extendida;
       | 10.Añadir un ejemplo de código de configuración de la velocidad de seguridad de las articulaciones del robot;
       | 11.Añadir la interfaz WaitStationaryMotionDone() para esperar a que finalice el movimiento en vacío en el lugar;
       | 12.Añadir la interfaz SetStationaryTrackPara() de configuración de parámetros de seguimiento en el lugar de la cinta transportadora, junto con un ejemplo de código de seguimiento en el lugar de la cinta transportadora;
       | 13.Añadir las interfaces WorkPieceTrsfStart() y WorkPieceTrsfEnd() de inicio y fin de la transformación del sistema de coordenadas de la pieza, junto con un ejemplo de código de transformación del sistema de coordenadas de la pieza.
       | 14.Añadir la interfaz GetWeldMachineCtrlMode() para obtener el modo de control de la máquina de soldar.
       | 15.Añadir las interfaces GetExtDIConfig() y GetExtDOConfig() para obtener la función de DI extendida y la función de DO extendida.

   * - V3.9.7
     - 2026-06-25
     - | 1.Actualizar la estructura de retroalimentación de estado del robot, la señal de finalización de movimiento de la pinza añade el estado de detección de objeto; el fallo de la pinza añade 2-error de instrucción, 3-caída de la pieza, otros-código de fallo de la pinza +3;
       | 2.Actualizar el ejemplo de código de reinicio de salida tras detener/pausar el programa LUA, optimizando la interfaz de carga de archivos lua para que solo requiera el nombre del archivo lua, sin necesidad de introducir la ruta.
       | 3.Actualizar el ejemplo de código de calibración TCP del sensor fotoeléctrico, optimizando la interfaz de carga de archivos para que solo requiera el nombre del archivo lua, sin necesidad de introducir la ruta.
       | 4.Actualizar el ejemplo de código de establecimiento de la velocidad durante la ejecución de la trayectoria, optimizando la interfaz de carga de archivos de trayectoria J para que solo requiera el nombre del archivo de trayectoria J, sin necesidad de introducir la ruta.
       | 5.Actualizar el ejemplo de código de reproducción de archivos de trayectoria J del robot, optimizando la interfaz de carga de archivos de trayectoria J para que solo requiera el nombre del archivo de trayectoria J, sin necesidad de introducir la ruta.
       | 6.Actualizar el ejemplo de código de reproducción de trayectoria (previsión de trayectoria), optimizando la interfaz de carga de archivos de trayectoria J para que solo requiera el nombre del archivo de trayectoria J, sin necesidad de introducir la ruta.
       | 7.El parámetro de nombre del programa de trabajo de la interfaz LoadDefaultProgConfig() solo requiere el nombre del archivo lua, sin necesidad de introducir la ruta.
       | 8.El parámetro de nombre del programa de trabajo de la interfaz ProgramLoad() solo requiere el nombre del archivo lua, sin necesidad de introducir la ruta.
       | 9.El parámetro de nombre del programa de trabajo de la interfaz GetLoadedProgram() solo requiere el nombre del archivo lua, sin necesidad de introducir la ruta.
       | 10.Actualizar el ejemplo de código de operación del programa LUA del robot, optimizando la interfaz de carga de archivos para que solo requiera el nombre del archivo lua, sin necesidad de introducir la ruta.
       | 11.La interfaz SetAxleLuaEnableDeviceType() añade el parámetro de estado de habilitación de la mano diestra;
       | 12.La interfaz GetAxleLuaEnableDeviceType() añade el parámetro de estado de habilitación de la mano diestra;
       | 13.La interfaz GetAxleLuaEnableDevice() añade el parámetro de estado del número de dispositivo habilitado de la mano diestra;
       | 14.El arreglo de códigos de función de la pinza de la interfaz SetAxleLuaGripperFunc() se amplía a 32, añadiendo el control de la pinza giratoria, etc.;
       | 15.El arreglo de códigos de función de la pinza de la interfaz GetAxleLuaGripperFunc() se amplía a 32, añadiendo el estado de la pinza giratoria, etc.;
       | 16.Corregir el error de nombre de la interfaz SetCoderCompenParams();
       | 17.Añadir la interfaz SetDexterousHandsMove () para controlar el movimiento de la mano diestra.
       | 18.Añadir la interfaz SetDexterousHandsAct () para controlar la activación de reinicio de la mano diestra.
       | 19.Añadir la interfaz ClearDexterousHandsError () para borrar los errores de la mano diestra.
       | 20.Añadir la interfaz SetDexterousHandsFunc() para establecer la habilitación de la función de control de acciones de la mano diestra.
       | 21.Añadir la interfaz GetDexterousHandsFunc() para obtener la habilitación de la función de control de acciones de la mano diestra.
       | 22.Añadir SetWeaveBackCenterConfig() y GetWeaveBackCenterConfig() para establecer y obtener el parámetro de retorno al punto cero del ciclo al final de la oscilación.
       | 23.Añadir la interfaz SetWeaveOffsetRT() para establecer el desplazamiento en tiempo real de la oscilación;
       | 24.Añadir la interfaz SetSpeedInstant() para establecer la velocidad en tiempo real;

   * - V3.9.6
     - 2026-05-26
     - | 1.Actualizar la estructura de retroalimentación de estado del robot, añadiendo el estado del número del sistema de coordenadas del eje extendido;
       | 2.Actualizar la enumeración de tipos de configuración de retroalimentación de estado del robot, añadiendo la enumeración de configuración del número del sistema de coordenadas del eje extendido;
       | 3.Añadir la interfaz ExtAxisGetParamConfig() para obtener la configuración de parámetros del eje extendido UDP.
       | 4.Añadir la interfaz ServoJV() de movimiento en modo servo de velocidad del espacio de articulaciones del robot.
       | 5.Añadir la interfaz ServoMITStart() de inicio de control MIT de las articulaciones del robot.
       | 6.Añadir la interfaz ServoMITEnd() de fin de control MIT de las articulaciones del robot.
       | 7.Añadir la interfaz ServoMIT() de control MIT de las articulaciones del robot.
       | 8.Añadir la interfaz SetLaserWeldingParam() de configuración de parámetros de soldadura láser del robot.
       | 9.Añadir la interfaz SetLaserWeldingStartEnd() para establecer el inicio y la parada de la soldadura láser del robot.
       | 10.Añadir la interfaz SetLaserWeldingEnable() para establecer la habilitación y deshabilitación de la máquina de soldadura láser.
       | 11.Añadir la interfaz ResetLaserWeldingErr() para establecer el reinicio de fallos de la máquina de soldadura láser.
       | 12.Añadir la interfaz GetLaserWeldingRunningState() para obtener el estado de funcionamiento de la máquina de soldadura láser.
       | 13.Añadir la interfaz GetLaserWeldingErrState() para obtener el estado de fallo de la máquina de soldadura láser.
       | 14.Añadir la interfaz GetLaserWeldingParamTarget() para obtener los parámetros de configuración de la soldadura láser.
       | 15.Añadir la interfaz GetLaserWeldingParamActual() para obtener los parámetros de configuración vigentes actualmente de la máquina de soldadura láser.
       | 16.Añadir la interfaz SetLaserWeldingEnableExtDoNum() para configurar el puerto DO extendido de habilitación de IO de la máquina de soldadura láser.
       | 17.Añadir la interfaz SetLaserWeldingStartExtDoNum() para configurar el puerto DO extendido de inicio de IO de la máquina de soldadura láser.
       | 18.Añadir la interfaz SetLaserWeldingErrResetExtDoNum() para configurar el puerto DO extendido de reinicio de fallos de IO de la máquina de soldadura láser.
       | 19.Añadir la interfaz SetLaserWeldingRunningStateExtDiNum() para configurar el puerto DI extendido del estado de funcionamiento (estado de emisión de luz) de IO de la máquina de soldadura láser.
       | 20.Añadir la interfaz SetLaserWeldingErrStateExtDiNum() para configurar el puerto DI extendido del estado de fallo de IO de la máquina de soldadura láser.
  
   * - V3.9.5
     - 2026-04-24
     - | 1.La interfaz SetTrajectoryJSpeed() añade el modo de reducción de velocidad y el cambio directo;
       | 2.La interfaz FieldBusSlaveWriteAO() cambia el tipo de valor de escritura a tipo double, donde AO0~AO15 son de tipo entero y AO16~AO31 son de tipo flotante;
       | 3.La interfaz FieldBusSlaveReadAI() cambia el tipo de valor de lectura a tipo double, donde AI0~AI15 son de tipo entero y AO16~AI31 son de tipo flotante;
       | 4.Actualizar el tipo de estructura de retroalimentación de estado del robot;
       | 5.Añadir el tipo de enumeración de configuración de retroalimentación de estado del robot;
       | 6.Añadir la interfaz SetRobotRealtimeStateConfig() para configurar la retroalimentación de estado CNDE del robot;
       | 7.Añadir la interfaz AddRobotRealtimeState() para añadir un estado del robot a la configuración de estado CNDE;
       | 8.Añadir la interfaz DeleteRobotRealtimeState() para eliminar un estado del robot de la configuración de estado CNDE;
       | 9.Añadir la interfaz SetRobotRealtimeStatePeriod() para establecer el período de retroalimentación de estado CNDE;
       | 10.Añadir la interfaz GetRobotRealtimeStateConfig() para obtener el conjunto de todos los estados y el período de la retroalimentación de estado CNDE actual.

   * - V3.9.4
     - 2026-03-25
     - | 1.La interfaz ServoJTStart() añade el parámetro de selección de tipo de comunicación, compatible con comunicación XMLPRC/UDP;
       | 2.La interfaz ServoJTEnd() añade el parámetro de selección de tipo de comunicación, compatible con comunicación XMLPRC/UDP;
       | 3.La interfaz ServoJT() añade el parámetro de selección de tipo de comunicación, compatible con comunicación XMLPRC/UDP;
       | 4.La interfaz ServoMoveStart() añade el parámetro de selección de tipo de comunicación, compatible con comunicación XMLPRC/UDP;
       | 5.La interfaz ServoMoveEnd() añade el parámetro de selección de tipo de comunicación, compatible con comunicación XMLPRC/UDP;
       | 6.La interfaz ServoJ() añade el parámetro de selección de tipo de comunicación, compatible con comunicación XMLPRC/UDP;
       | 7.La interfaz SetWeldMachineCtrlMode() añade el parámetro de selección del modo de control;
       | 8.La interfaz ExtDevGetUDPComParam() añade la obtención del parámetro de comunicación UDP: si se reconecta automáticamente tras reiniciar la caja de control;
       | 9.Añadir la interfaz SetAxleGenComEnable() para habilitar la función de transmisión transparente general del extremo;
       | 10.Añadir la interfaz SndRcvAxleGenComCmdData() para enviar datos no periódicos desde el extremo y esperar la respuesta;
       | 11.Añadir la interfaz SetRobotStopOnComDisc() para establecer la detención del robot cuando se desconecta la comunicación del puerto;
       | 12.Añadir la interfaz GetRobotStopOnComDisc() para obtener el parámetro de detención del robot cuando se desconecta la comunicación del puerto;
       | 13.Añadir la interfaz SetDIConfig() para establecer la función del puerto CI configurable de la caja de control;
       | 14.Añadir la interfaz GetDIConfig() para obtener la función del puerto CI configurable de la caja de control;
       | 15.Añadir la interfaz SetDOConfig() para establecer la función del puerto CO configurable de la caja de control;
       | 16.Añadir la interfaz GetDOConfig() para obtener la función del puerto CO configurable de la caja de control;
       | 17.Añadir la interfaz SetToolDIConfig() para establecer la función del puerto End-CI configurable del extremo;
       | 18.Añadir la interfaz GetToolDIConfig() para obtener la función del puerto End-CI configurable del extremo;
       | 19.Añadir la interfaz SetDIConfigLevel() para establecer el estado válido del CI configurable de la caja de control;
       | 20.Añadir la interfaz GetDIConfigLevel() para obtener el estado válido del CI configurable de la caja de control;
       | 21.Añadir la interfaz SetDOConfigLevel() para establecer el estado válido del CO configurable de la caja de control;
       | 22.Añadir la interfaz GetDOConfigLevel() para obtener el estado válido del CO configurable de la caja de control;
       | 23.Añadir la interfaz SetToolDIConfigLevel() para establecer el estado válido del CI configurable del extremo;
       | 24.Añadir la interfaz GetToolDIConfigLevel() para obtener el estado válido del CI configurable del extremo;
       | 25.Añadir la interfaz SetStandardDILevel() para establecer el estado válido del DI estándar de la caja de control;
       | 26.Añadir la interfaz GetStandardDILevel() para obtener el estado válido del DI estándar de la caja de control;
       | 27.Añadir la interfaz SetStandardDOLevel() para establecer el estado válido del DO estándar de la caja de control;
       | 28.Añadir la interfaz GetStandardDOLevel() para obtener el estado válido del DO estándar de la caja de control;
       | 29.Añadir la interfaz SetExAxisCmdDoneTimeUDP() para establecer el tiempo de finalización del posicionamiento del eje extendido;
       | 30.Añadir la interfaz OpenLuaDownload() para descargar el archivo Lua de protocolo abierto;
       | 31.Añadir la interfaz OpenLuaDelete() para eliminar el archivo Lua de protocolo abierto;
       | 32.Añadir la interfaz AllOpenLuaDelete() para eliminar el archivo Lua de protocolo abierto;
       | 33.Añadir la interfaz SendUDPFrameUDP () para enviar tramas de instrucciones;
       | 34.Añadir la interfaz SetCmdRpyCallback() para establecer la función de devolución de llamada del resultado de ejecución de las instrucciones enviadas por el SDK a través de UDP;
       | 35.Añadir la interfaz SetVelReducePara() para establecer los parámetros de velocidad de seguridad;
       | 36.Añadir la interfaz OriginPointWeaveStart() de inicio de oscilación de punto fijo;
       | 37.Añadir la interfaz OriginPointWeaveEnd() de fin de oscilación de punto fijo;
       | 38.Añadir la interfaz SetUserLEDColor() para establecer el color de la luz del extremo del robot personalizado por el usuario;
       | 39.Añadir la interfaz MoveToTPDStart() para moverse al punto de inicio del registro de trayectoria TPD;

   * - V3.9.3
     - 2026-02-11
     - | 1.La interfaz ServoCart() añade el parámetro de eje extendido
       | 2.La interfaz SetOutputResetCtlBoxDO() añade el parámetro de si se recarga el estado DO antes del reinicio tras la reanudación de la pausa
       | 3.La interfaz SetOutputResetCtlBoxAO() añade el parámetro de si se recarga el estado DO antes del reinicio tras la reanudación de la pausa
       | 4.La interfaz SetOutputResetAxleDO() añade el parámetro de si se recarga el estado DO antes del reinicio tras la reanudación de la pausa
       | 5.La interfaz SetOutputResetAxleAO() añade el parámetro de si se recarga el estado DO antes del reinicio tras la reanudación de la pausa
       | 6.La interfaz SetOutputResetExtDO() añade el parámetro de si se recarga el estado DO antes del reinicio tras la reanudación de la pausa
       | 7.La interfaz SetOutputResetExtAO() añade el parámetro de si se recarga el estado DO antes del reinicio tras la reanudación de la pausa
       | 8.La interfaz SetOutputResetSmartToolDO() añade el parámetro de si se recarga el estado DO antes del reinicio tras la reanudación de la pausa
       | 9.Añadir la interfaz GetInverseKinExaxis() de solución de cinemática inversa que incluye la posición del eje extendido
       
   * - V3.9.2
     - 2026-01-26
     - | 1.La interfaz FT_RotInsertion() añade el parámetro de estrategia de tratamiento cuando no se detecta fuerza/par
       | 2.La interfaz LaserSensorRecordandReplay() añade los parámetros relacionados con el seguimiento de punto fijo del robot
       | 3.Añadir la interfaz MoveStationary()
       | 4.Añadir la interfaz TCPComputeRPY()
       | 5.Añadir la interfaz TCPComputeXYZ()
       | 6.Añadir la interfaz TCPRecordFlangePosStart()
       | 7.Añadir la interfaz TCPRecordFlangePosEnd()
       | 8.Añadir la interfaz TCPGetRecordFlangePos()
       | 9.Añadir la interfaz PhotoelectricSensorTCPCalibration()

   * - V3.9.1
     - 2025-12-25
     - | 1.La interfaz MoveL() añade el parámetro de factor de escala de velocidad oacc / parámetro de aceleración física;
       | 2.La interfaz MoveC() añade el parámetro de factor de escala de velocidad oacc / parámetro de aceleración física;
       | 3.La interfaz Circle() optimiza la descripción de los parámetros de velocidad física y aceleración física;
       | 4.Añadir la función sobrecargada FT_Control(), con los parámetros de umbral de activación de rx, ry y coeficiente de ajuste de par;
       | 5.Añadir la interfaz SerCoderCompenParams();
   
   * - V3.9.0
     - 2025-11-26
     - | 1.La interfaz JointSensitivityCalibration() añade el retorno de la linealidad de las articulaciones j1~j6
       | 2.Añadir la interfaz JointHysteresisError()
       | 3.Añadir la interfaz JointRepeatability()
       | 4.Añadir la interfaz SetAdmittanceParams()
       | 5.Añadir la interfaz MoveToIntersectLineStart()
       | 6.Añadir la interfaz MoveIntersectLine()

   * - V3.8.7
     - 2025-10-21
     - | 1.FT_Control() añade los parámetros de masa y amortiguación
       | 2.Añadir la interfaz JointSensitivityCalibration()
       | 3.Añadir la interfaz JointSensitivityCollect()
       | 4.Añadir la interfaz MotionQueueClear()
       | 5.Añadir la interfaz GetSlavePortErrCounter()
       | 6.Añadir la interfaz SlavePortErrCounterClear()
       | 7.Añadir la interfaz SetVelFeedForwardRatio()
       | 8.Añadir la interfaz GetVelFeedForwardRatio()
       | 9.Añadir la interfaz RobotMCULogCollect()
       | 10.La estructura de estado añade el contador de instrucciones ServoJ y los datos de la posición objetivo de la última instrucción
       | 11.La nueva estructura de parámetros de hélice SpiralParam añade el modo de parámetros de velocidad y aceleración

   * - V3.8.6
     - 2025-09-19
     - | 1.La interfaz SetLoadCoord() añade el parámetro de número de carga
       | 2.Añadir la interfaz LaserTrackingLaserOnOff()
       | 3.Añadir la interfaz LaserTrackingTrackOnOff()
       | 4.Añadir la interfaz LaserTrackingSearchStart_xyz()
       | 5.Añadir la interfaz LaserTrackingSearchStart_point()
       | 6.Añadir la interfaz LaserTrackingSearchStop()
       | 7.Añadir la interfaz LaserTrackingSensorConfig()
       | 8.Añadir la interfaz LaserTrackingSensorSamplePeriod()
       | 9.Añadir la interfaz LoadPosSensorDriver()
       | 10.Añadir la interfaz UnLoadPosSensorDriver()
       | 11.Añadir la interfaz LaserSensorRecord1()
       | 12.Añadir la interfaz LaserSensorReplay()
       | 13.Añadir la interfaz MoveLTR()
       | 14.Añadir la interfaz LaserSensorRecordandReplay()
       | 15.Añadir la interfaz MoveToLaserRecordStart()
       | 16.Añadir la interfaz MoveToLaserRecordEnd()
       | 17.Añadir la interfaz MoveToLaserSeamPos()
       | 18.Añadir la interfaz GetLaserSeamPos()
       | 19.Añadir la interfaz ImpedanceControlStartStop()
       | 20.Añadir la interfaz GetToolCoordWithID()
       | 21.Añadir la interfaz GetWObjCoordWithID()
       | 22.Añadir la interfaz GetExToolCoordWithID()
       | 23.Añadir la interfaz GetExAxisCoordWithID()
       | 24.Añadir la interfaz GetTargetPayloadWithID()
       | 25.Añadir la interfaz GetExAxisCoordWithID()
       | 26.Añadir la interfaz GetCurWObjCoord()
       | 27.Añadir la interfaz GetCurExToolCoord()
       | 28.Añadir la interfaz GetCurExToolCoord()
       | 29.Añadir la interfaz KernelUpgrade()
       | 30.Añadir la interfaz GetKernelUpgradeResult()
       | 31.Añadir la interfaz CustomWeaveSetPara()
       | 32.Añadir la interfaz CustomWeaveGetPara()
       | 33.La estructura de estado añade los datos de herramienta, pieza, herramienta externa, sistema de coordenadas del eje extendido y masa y centro de masa de la carga

   * - V3.8.5
     - 2025-08-20
     - | 1.Las instrucciones MoveL(), MoveC() y Circle() añaden el parámetro velAccParamMode
       | 2.Añadir las interfaces de cálculo automático de cinemática directa MoveJ(), SplinePTP() y ExtAxisSyncMoveJ()
       | 3.LoadTrajectoryLA() añade el parámetro de activación del interruptor de previsión de velocidad constante
       | 4.Añadir las interfaces de cálculo automático de cinemática inversa MoveL(), MoveC(), Circle(), NewSplinePoint(), NewSpiral(), ExtAxisSyncMoveL() y ExtAxisSyncMoveC()
       | 5.Añadir las interfaces de control de ventosa SetSuckerCtrl(), GetSuckerState(), WaitSuckerState(), etc., y la interfaz de estrategia de movimiento sincronizado SetExAxisRobotPlan()
       | 6.Añadir las instrucciones de control del modo esclavo del robot OpenLuaUpload(), GetFieldBusConfig(), FieldBusSlaveWriteDO(), FieldBusSlaveWriteAO(), FieldBusSlaveReadDI(), FieldBusSlaveReadAI(), FieldBusSlaveWaitDI(), FieldBusSlaveWaitAI(), etc.

   * - V3.8.4
     - 2025-07-17
     - | 1.La interfaz ExtAxisMove() añade el parámetro de suavizado blend
       | 2.Añadir la interfaz SetFocusCalibPoint()
       | 3.Añadir la interfaz ComputeFocusCalib()
       | 4.Añadir la interfaz SetFocusPosition()
       | 5.Añadir la interfaz FocusStart()
       | 6.Añadir la interfaz FocusEnd()
       | 7.Añadir la interfaz SetJointFirmwareUpgrade()
       | 8.Añadir la interfaz SetCtrlFirmwareUpgrade()
       | 9.Añadir la interfaz SetEndFirmwareUpgrade()
       | 10.Añadir la interfaz JointAllParamUpgrade()
       
   * - V3.8.3
     - 2025-06-24
     - | 1.La interfaz Circle() añade los parámetros de porcentaje de aceleración y radio de suavizado
       | 2.La interfaz EndForceDragControl() añade el parámetro del indicador de detección de colisión del robot durante el arrastre asistido
       | 3.La interfaz ServoJ() añade el parámetro de ID de instrucción
       | 4.Añadir la interfaz SetWideBoxTempFanMonitorParam()
       | 5.Añadir la interfaz GetWideBoxTempFanMonitorParam()
       | 6.La estructura de estado añade los datos de estado de la temperatura de la caja de control y la corriente del ventilador
              
   * - V3.8.2
     - 2025-06-13
     - | 1.La interfaz WeaveSetPara() añade el parámetro de ángulo de inclinación lateral de la dirección de oscilación (desviación alrededor del eje X de oscilación)
       | 2.La interfaz WeaveChangeStart() añade los parámetros de número de oscilación, velocidad de inicio de soldadura y velocidad de fin de soldadura
       | 3.La interfaz ExtDevSetUDPComParam() añade el parámetro de si se establece automáticamente la conexión tras un reinicio por corte de energía
       | 4.La interfaz SetCollisionDetectionMethod() añade la selección del modo de umbral del nivel de colisión
       | 5.La interfaz PtpFIRPlanningStart() añade el valor extremo unificado de sobreaceleración (jerk) de las articulaciones
       | 6.Añadir la interfaz WeldingSetVoltageGradualChangeStart()
       | 7.Añadir la interfaz WeldingSetVoltageGradualChangeEnd()
       | 8.Añadir la interfaz WeldingSetCurrentGradualChangeStart()
       | 9.Añadir la interfaz WeldingSetCurrentGradualChangeEnd()
       | 10.Añadir la interfaz ArcWeldTraceAIChannelCurrent()
       | 11.Añadir la interfaz ArcWeldTraceAIChannelVoltage()
       | 12.Añadir la interfaz ArcWeldTraceCurrentPara()
       | 13.Añadir la interfaz ArcWeldTraceVoltagePara()
       | 14.Añadir la interfaz GetSmarttoolBtnState()
       | 15.Añadir la interfaz ExtAxisGetCoord()
                     
   * - V3.8.1
     - 2025-04-24
     - | 1.La interfaz ConveyorSetParam() añade los parámetros de tipo de movimiento de seguimiento, distancia de inicio de seguimiento y distancia de fin de seguimiento
       | 2.Añadir la interfaz AccSmoothStart()
       | 3.Añadir la interfaz AccSmoothEnd()
       | 4.Añadir la interfaz RbLogDownload()
       | 5.Añadir la interfaz AllDataSourceDownload()
       | 6.Añadir la interfaz DataPackageDownload()
       | 7.Añadir la interfaz GetRobotSN()
       | 8.Añadir la interfaz ShutDownRobotOS()
       | 9.Añadir la interfaz ConveyorComDetect()
       | 10.Añadir la interfaz ConveyorComDetectTrigger()
                     
   * - V3.8.0
     - 2025-02-12
     - | 1.La interfaz EndForceDragControl() añade el parámetro de evitación de puntos singulares
       | 2.La interfaz ArcWeldTraceControl() añade el parámetro de desplazamiento
       | 3.Añadir la interfaz WeaveChangeStart()
       | 4.Añadir la interfaz WeaveChangeEnd()
       | 5.Añadir la interfaz LoadTrajectoryLA()
       | 6.Añadir la interfaz MoveTrajectoryLA()
       | 7.Añadir la interfaz CustomCollisionDetectionStart()
       | 8.Añadir la interfaz CustomCollisionDetectionEnd()