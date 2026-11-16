Descripción de la actualización de versión
============================================

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
     - | 1.Modificar el comentario de la interfaz GetGripperMotionDone() para obtener el estado de movimiento de la pinza; a partir de la versión 401, la definición de retroalimentación del estado de movimiento de la pinza del protocolo del extremo y los dispositivos adaptados está unificada, status añade 3=movimiento completado con detección de caída del objeto;
       | 2.Modificar el comentario de la interfaz GripperWaitMotionDone() para esperar el estado de movimiento de la pinza; a partir de la versión 401, la definición de retroalimentación del estado de movimiento de la pinza del protocolo del extremo y los dispositivos adaptados está unificada, status añade 3=movimiento completado con detección de caída del objeto;
       | 3.Modificar la descripción de los parámetros de la interfaz ServoMoveStart() de inicio de movimiento servo, añadir los parámetros filtertime (tiempo de filtrado) y gain (matriz de ganancia del lazo de posición), para usar junto con las instrucciones ServoJ y ServoCart, y añadir el ejemplo de código correspondiente;
       | 4.Añadir la interfaz DataPackageUpgrade() de carga y actualización del paquete de copia de seguridad de datos y su ejemplo de código;
       | 5.Añadir la interfaz GetDataPackageUpgradeProgress() para obtener el porcentaje de progreso de la actualización del paquete de copia de seguridad de datos;
       | 6.Añadir la interfaz GetJointAllParamUpgradeProgress() para obtener el porcentaje de progreso de la actualización de todos los parámetros articulares;
       | 7.Añadir el ejemplo de código de carga y actualización del paquete de copia de seguridad de datos y consulta del progreso de la actualización;
       | 8.Añadir el ejemplo de código de actualización de todos los parámetros articulares y consulta del progreso de la actualización de todos los parámetros articulares.
       
   * - V4.0.0
     - 2026-09-23
     - | 1.Modificar la interfaz de instanciación Robot() para establecer la conexión RPC con el robot, añadir la configuración del parámetro de habilitación del cifrado TLS de comunicación del protocolo de instrucciones integrado en el SDK; para usarlo es necesario instalar primero las bibliotecas de dependencia de python, los comandos de instalación son: pip install python3-dtls, pip install python-mbedtls;
       | 2.Modificar la descripción de los parámetros de la interfaz SetWeldMachineCtrlMode() para establecer el modo de control de la soldadora, añadir los modos con pulso y sin pulso de la soldadora Panasonic;
       | 3.Añadir la instrucción SendTCPFrame() para enviar tramas de instrucciones personalizadas a través de TCP 8080 y su ejemplo de código;
       | 4.Añadir la instrucción TCFToAllJoint() para obtener las 8 soluciones inversas del robot y su ejemplo de código;
       | 5.Añadir la instrucción SetPhySpeedInstant() para establecer instantáneamente la velocidad física y su ejemplo de código.

   * - V3.9.9
     - 2026-09-01
     - | 1.Actualizar la interfaz GetGripperMotionDone() para obtener el estado de movimiento de la pinza, actualizar la definición de los parámetros de salida del estado de la pinza y su ámbito de uso;
       | 2.Modificar la interfaz GetInverseKinExaxis() de solución de cinemática inversa que incluye la posición del eje extendido, añadir el parámetro de configuración articular, valor predeterminado -1 para referenciar la configuración articular actual;
       | 3.Modificar las interfaces de control de fuerza FT_SpiralSearch(), FT_LinInsertion(), FT_FindSurface() añadiendo el parámetro de estrategia de tratamiento cuando no se detecta fuerza/par;
       | 4.Modificar las interfaces SetDIConfig(), GetDIConfig(), SetDOConfig(), GetDOConfig() de configuración de funciones CIO de la caja de control del robot;
       | 5.Actualizar la descripción de los parámetros de la interfaz de configuración de funciones, actualizar los nombres de funciones y códigos de función añadidos; añadir la interfaz GetSafetyParamsCheckSum() para obtener la suma de verificación de los parámetros de configuración de seguridad;
       | 6.Modificar el ejemplo de código de control básico del robot, añadir el ejemplo de código de cambio al modo manual de alta velocidad;
       | 7.Añadir la interfaz SafetyOPPasswordCheck() de verificación de contraseña de operación de seguridad;
       | 8.Añadir la interfaz GripperWaitMotionDone() para esperar el estado de movimiento de la pinza, soporta tiempo de espera y configuración de estrategia (solo aplicable al protocolo abierto del extremo);
       | 9.Añadir la interfaz SetRobottime() para sincronizar la hora del sistema con el robot;
       | 10.Añadir la interfaz ServoJ() de movimiento en modo servo del espacio articular, soporta entrada de múltiples puntos a la vez;
       | 11.Añadir el ejemplo de código de registro y reproducción láser + oscilación convencional;
       | 12.Añadir el ejemplo de código de registro y reproducción láser + movimiento asíncrono del eje extendido + oscilación en punto fijo;
       | 13.Añadir la interfaz FT_SpiralSearch() de exploración en espiral;
       | 14.Añadir la interfaz HiSpeedManualSwitch() para cambiar al modo manual de alta velocidad;
       | 15.Añadir la interfaz SetSafetyDIConfig() de configuración de funciones CI de doble canal de seguridad;
       | 16.Añadir la interfaz SetSafetyDOConfig() de configuración de funciones CO de doble canal de seguridad;
       | 17.Añadir el ejemplo de verificación de configuración-establecimiento-lectura-puesta a cero de funciones CI/CO de doble canal de seguridad.
       
   * - V3.9.8
     - 2026-07-27
     - | 1.Actualizar la estructura de retroalimentación del estado del robot, añadir el estado de ejecución del programa lua actual del robot, 0-programa no en ejecución; 1-programa en ejecución (incluye pausa del programa);
       | 2.Actualizar la descripción de los parámetros de las interfaces SetExToolCoord() y SetExToolList() para establecer el sistema de coordenadas de herramienta externa y la lista de sistemas de coordenadas de herramienta, donde el número del sistema de coordenadas de herramienta externa se actualiza a 20-39. Y actualizar el ejemplo de código de operación del sistema de coordenadas de herramienta externa.
       | 3.Añadir a la interfaz GetToolCoordWithID() para obtener los parámetros del sistema de coordenadas de herramienta la obtención de los parámetros tipo de herramienta, posición de instalación, ID de herramienta y número de carga.
       | 4.Añadir a la interfaz GetWObjCoordWithID() para obtener los parámetros del sistema de coordenadas de pieza la obtención del parámetro del sistema de coordenadas de referencia;
       | 5.Añadir a la interfaz GetExToolCoordWithID() para obtener los parámetros del sistema de coordenadas de herramienta externa la obtención del parámetro de pose del sistema de coordenadas de pieza instalado en el extremo del robot.
       | 6.Añadir a la interfaz GetExAxisCoordWithID() para obtener los parámetros del sistema de coordenadas del eje extendido la obtención de los parámetros número de eje extendido e indicador de calibración.
       | 7.Añadir a la interfaz SetVelReducePara() para establecer la velocidad de seguridad del robot la configuración del parámetro de velocidad de seguridad articular del robot.
       | 8.Añadir en el ejemplo de código de configuración de parámetros de soldadura un ejemplo de obtención del modo de control de la soldadora.
       | 9.Añadir en el ejemplo de código de configuración de señales de soldadura de IO extendido un ejemplo de código de obtención de la configuración de funciones de DI extendido y DO extendido;
       | 10.Añadir el ejemplo de código de configuración de la velocidad de seguridad articular del robot;
       | 11.Añadir la interfaz WaitStationaryMotionDone() para esperar a que finalice el movimiento en vacío en el lugar;
       | 12.Añadir la interfaz SetStationaryTrackPara() de configuración de parámetros de seguimiento en el lugar de la cinta transportadora, y el ejemplo de código de seguimiento en el lugar de la cinta transportadora;
       | 13.Añadir las interfaces WorkPieceTrsfStart() y WorkPieceTrsfEnd() de inicio y fin de conversión del sistema de coordenadas de pieza, y el ejemplo de código de conversión del sistema de coordenadas de pieza.
       | 14.Añadir la interfaz GetWeldMachineCtrlMode() para obtener el modo de control de la soldadora.
       | 15.Añadir las interfaces GetExtDIConfig() y GetExtDOConfig() para obtener la función de DI extendido y la función de DO extendido.
       
   * - V3.9.7
     - 2026-06-25
     - | 1.El parámetro de PhotoelectricSensorTCPCalibration() puede adaptarse a nombres de archivo sin ruta;
       | 2.El parámetro de LoadTrajectoryJ() puede adaptarse a nombres de archivo sin ruta;
       | 3.El parámetro de LoadTrajectoryLA() puede adaptarse a nombres de archivo sin ruta;
       | 4.El parámetro de LoadDefaultProgConfig() puede adaptarse a nombres de archivo sin ruta;
       | 5.El parámetro de ProgramLoad() puede adaptarse a nombres de archivo sin ruta;
       | 6.Añadir a la interfaz SetAxleLuaEnableDeviceType() el parámetro de estado de habilitación de la mano diestra;
       | 7.Añadir a la interfaz GetAxleLuaEnableDeviceType() el parámetro de estado de habilitación de la mano diestra;
       | 8.Modificar la interfaz para obtener el tipo de habilitación del dispositivo del extremo configurado actualmente y la interfaz de control de movimiento de la pinza;
       | 9.Añadir la habilitación de la mano diestra y el código de función;
       | 10.Añadir la interfaz SetDexterousHandsMove() para controlar el movimiento de la mano diestra;
       | 11.Añadir la interfaz SetDexterousHandsAct() para controlar el restablecimiento y activación de la mano diestra;
       | 12.Añadir la interfaz ClearDexterousHandsError() para borrar el error de la mano diestra;
       | 13.Añadir la interfaz SetDexterousHandsFunc() para establecer la habilitación de la función de control de movimiento de la mano diestra;
       | 14.Añadir la interfaz GetDexterousHandsFunc() para obtener la habilitación de la función de control de movimiento de la mano diestra;
       | 15.Añadir las interfaces para establecer y obtener el retorno al punto cero del ciclo al final de la oscilación;
       | 16.Añadir las interfaces SetWeaveOffsetRT() para establecer el desplazamiento en tiempo real de la oscilación y SetSpeedInstant() para establecer la velocidad en tiempo real.
       
   * - V3.9.6
     - 2026-05-26
     - | 1.Actualizar la estructura de retroalimentación del estado del robot, añadir el estado del número del sistema de coordenadas del eje extendido;
       | 2.Actualizar la enumeración de tipos de configuración de retroalimentación del estado del robot, añadir la enumeración de configuración del número del sistema de coordenadas del eje extendido;
       | 3.Añadir la interfaz ExtAxisGetParamConfig() para obtener la configuración de parámetros del eje extendido UDP.
       | 4.Añadir la interfaz ServoJV() de movimiento en modo servo de velocidad del espacio articular del robot.
       | 5.Añadir la interfaz ServoMITStart() de inicio del control MIT articular del robot.
       | 6.Añadir la interfaz ServoMITEnd() de fin del control MIT articular del robot.
       | 7.Añadir la interfaz ServoMIT() de control MIT articular del robot.
       | 8.Añadir la interfaz SetLaserWeldingParam() de configuración de parámetros de soldadura láser del robot.
       | 9.Añadir la interfaz SetLaserWeldingStartEnd() para establecer el inicio y la parada de la soldadura láser del robot.
       | 10.Añadir la interfaz SetLaserWeldingEnable() para establecer la habilitación y deshabilitación de la soldadora láser.
       | 11.Añadir la interfaz ResetLaserWeldingErr() para establecer el restablecimiento de fallos de la soldadora láser.
       | 12.Añadir la interfaz GetLaserWeldingRunningState() para obtener el estado de funcionamiento de la soldadora láser.
       | 13.Añadir la interfaz GetLaserWeldingErrState() para obtener el estado de fallo de la soldadora láser.
       | 14.Añadir la interfaz GetLaserWeldingParamTarget() para obtener los parámetros de configuración de la soldadura láser.
       | 15.Añadir la interfaz GetLaserWeldingParamActual() para obtener los parámetros de configuración vigentes actualmente de la soldadora láser.
       | 16.Añadir la interfaz SetLaserWeldingEnableExtDoNum() para configurar el puerto DO extendido de habilitación de la soldadora láser.
       | 17.Añadir la interfaz SetLaserWeldingStartExtDoNum() para configurar el puerto DO extendido de inicio de la soldadora láser.
       | 18.Añadir la interfaz SetLaserWeldingErrResetExtDoNum() para configurar el puerto DO extendido de restablecimiento de fallos de la soldadora láser.
       | 19.Añadir la interfaz SetLaserWeldingRunningStateExtDiNum() para configurar el puerto DI extendido del estado de funcionamiento (estado de emisión de luz) de la soldadora láser.
       | 20.Añadir la interfaz SetLaserWeldingErrStateExtDiNum() para configurar el puerto DI extendido del estado de fallo de la soldadora láser.

   * - V3.9.5
     - 2026-04-24
     - | 1.La interfaz SetTrajectoryJSpeed() añade el modo de reducción de velocidad y el cambio directo;
       | 2.La interfaz FieldBusSlaveWriteAO() cambia el tipo de valor escrito a tipo double, donde AO0~AO15 son enteros, AO16~AO31 son de punto flotante;
       | 3.La interfaz FieldBusSlaveReadAI() cambia el tipo de valor leído a tipo double, donde AI0~AI15 son enteros, AO16~AI31 son de punto flotante;
       | 4.Actualizar el tipo de estructura de retroalimentación del estado del robot;
       | 5.Añadir el tipo de enumeración de configuración de retroalimentación del estado del robot; añadir la interfaz SetRobotRealtimeStateConfig() para configurar la retroalimentación de estado CNDE del robot;
       | 6.Añadir la interfaz AddRobotRealtimeState() para añadir un estado del robot a la configuración de estado CNDE;
       | 7.Añadir la interfaz DeleteRobotRealtimeState() para eliminar un estado del robot de la configuración de estado CNDE;
       | 8.Añadir la interfaz SetRobotRealtimeStatePeriod() para establecer el período de retroalimentación del estado CNDE;
       | 9.Añadir la interfaz GetRobotRealtimeStateConfig() para obtener el conjunto de todos los estados y el período de la retroalimentación de estado CNDE actual.

   * - V3.9.4
     - 2026-03-25
     - | 1.La interfaz ServoJTStart() añade el parámetro de selección del tipo de comunicación, soporta comunicación XMLPRC/UDP;
       | 2.La interfaz ServoJTEnd() añade el parámetro de selección del tipo de comunicación, soporta comunicación XMLPRC/UDP;
       | 3.La interfaz ServoJT() añade el parámetro de selección del tipo de comunicación, soporta comunicación XMLPRC/UDP;
       | 4.La interfaz ServoMoveStart() añade el parámetro de selección del tipo de comunicación, soporta comunicación XMLPRC/UDP;
       | 5.La interfaz ServoMoveEnd() añade el parámetro de selección del tipo de comunicación, soporta comunicación XMLPRC/UDP;
       | 6.La interfaz ServoJ() añade el parámetro de selección del tipo de comunicación, soporta comunicación XMLPRC/UDP;
       | 7.La interfaz SetWeldMachineCtrlMode() añade el parámetro de selección del modo de control;
       | 8.La interfaz ExtDevGetUDPComParam() añade la obtención del parámetro de comunicación UDP: si se reconecta automáticamente tras reiniciar la caja de control;
       | 9.Añadir la interfaz SetAxleGenComEnable() para activar la función de transmisión transparente general del extremo;
       | 10.Añadir la interfaz SndRcvAxleGenComCmdData() para enviar datos no periódicos desde el extremo y esperar respuesta;
       | 11.Añadir la interfaz SetRobotStopOnComDisc() para establecer la parada del funcionamiento del robot cuando se desconecta la comunicación del puerto;
       | 12.Añadir la interfaz GetRobotStopOnComDisc() para obtener el parámetro de parada del funcionamiento del robot cuando se desconecta la comunicación del puerto;
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
       | 30.Añadir la interfaz SendUDPFrameUDP() para enviar tramas de instrucciones;
       | 31.Añadir la interfaz SetUDPCmdRpyCallback() para establecer la función de devolución de llamada del resultado de ejecución de las instrucciones enviadas por el SDK a través de UDP;
       | 32.Añadir la interfaz SetVelReducePara() para establecer los parámetros de velocidad de seguridad;
       | 33.Añadir la interfaz OriginPointWeaveStart() de inicio de oscilación en punto fijo;
       | 34.Añadir la interfaz OriginPointWeaveEnd() de fin de oscilación en punto fijo;
       | 35.Añadir la interfaz SetUserLEDColor() para establecer el color de la luz del extremo del robot personalizado por el usuario;
       | 36.Añadir la interfaz MoveToTPDStart() para moverse al punto inicial del registro de trayectoria TPD;
       | 37.Añadir la interfaz OpenLuaDownload() para descargar el archivo Lua de protocolo abierto;
       | 38.Añadir la interfaz OpenLuaDelete() para eliminar el archivo Lua de protocolo abierto;
       | 39.Añadir la interfaz AllOpenLuaDelete() para eliminar el archivo Lua de protocolo abierto;

   * - V3.9.3
     - 2026-02-11
     - | 1.La interfaz ServoCart() añade el parámetro del eje extendido
       | 2.La interfaz SetOutputResetCtlBoxDO() añade el parámetro de si recargar el estado DO antes del restablecimiento tras la reanudación de la pausa
       | 3.La interfaz SetOutputResetCtlBoxAO() añade el parámetro de si recargar el estado DO antes del restablecimiento tras la reanudación de la pausa
       | 4.La interfaz SetOutputResetAxleDO() añade el parámetro de si recargar el estado DO antes del restablecimiento tras la reanudación de la pausa
       | 5.La interfaz SetOutputResetAxleAO() añade el parámetro de si recargar el estado DO antes del restablecimiento tras la reanudación de la pausa
       | 6.La interfaz SetOutputResetExtDO() añade el parámetro de si recargar el estado DO antes del restablecimiento tras la reanudación de la pausa
       | 7.La interfaz SetOutputResetExtAO() añade el parámetro de si recargar el estado DO antes del restablecimiento tras la reanudación de la pausa
       | 8.La interfaz SetOutputResetSmartToolDO() añade el parámetro de si recargar el estado DO antes del restablecimiento tras la reanudación de la pausa
       | 9.Añadir la interfaz GetInverseKinExaxis() de solución de cinemática inversa que incluye la posición del eje extendido
       
   * - V3.9.2
     - 2026-01-26
     - | 1.La interfaz FT_RotInsertion() añade el parámetro de estrategia de tratamiento cuando no se detecta fuerza/par
       | 2.La interfaz LaserSensorRecordandReplay() añade los parámetros relacionados con el seguimiento en punto fijo del robot
       | 3.Añadir la interfaz MoveStationary()
       | 4.Añadir la interfaz TCPComputeRPY()
       | 5.Añadir la interfaz TCPComputeXYZ()
       | 6.Añadir la interfaz TCPRecordFlangePosStart()
       | 7.Añadir la interfaz TCPRecordFlangePosEnd()
       | 8.Añadir la interfaz TCPGetRecordFlangePos()
       | 9.Añadir la interfaz PhotoelectricSensorTCPCalibration()

   * - V3.9.1
     - 2025-12-25
     - | 1.La interfaz MoveL() añade el parámetro oacc factor de escala de velocidad/parámetro de aceleración física;
       | 2.La interfaz MoveC() añade el parámetro oacc factor de escala de velocidad/parámetro de aceleración física;
       | 3.La interfaz Circle() optimiza la descripción de los parámetros sobre velocidad física y aceleración física;
       | 4.Añadir la función sobrecargada FT_Control(), con los parámetros umbral de inicio rx, ry y coeficiente de ajuste de par;
       | 5.Añadir la interfaz SerCoderCompenParams();
       
   * - V3.9.0
     - 2025-11-26
     - | 1.La interfaz JointSensitivityCalibration() añade el retorno de linealidad de las articulaciones j1~j6
       | 2.Añadir la interfaz JointHysteresisError()
       | 3.Añadir la interfaz JointRepeatability()
       | 4.Añadir la interfaz SetAdmittanceParams()
       | 5.Añadir la interfaz MoveToIntersectLineStart()
       | 6.Añadir la interfaz MoveIntersectLine()

   * - V3.8.7
     - 2025-10-21
     - | 1.La interfaz NewSpiral() añade el parámetro velAccMode
       | 2.FT_Control() añade los parámetros de masa y amortiguación
       | 3.Añadir la interfaz JointSensitivityCalibration()
       | 4.Añadir la interfaz JointSensitivityCollect()
       | 5.Añadir la interfaz MotionQueueClear()
       | 6.Añadir la interfaz GetSlavePortErrCounter()
       | 7.Añadir la interfaz SlavePortErrCounterClear()
       | 8.Añadir la interfaz SetVelFeedForwardRatio()
       | 9.Añadir la interfaz GetVelFeedForwardRatio()
       | 10.Añadir la interfaz RobotMCULogCollect()
       | 11.La estructura de estado añade la última posición objetivo ServoJ en la cola y el contador de comandos ServoJ

   * - V3.8.6
     - 2025-09-19
     - | 1.La interfaz SetLoadCoord() añade el parámetro del número de carga
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
       | 33.La estructura de estado añade los datos de los sistemas de coordenadas de herramienta, pieza, herramienta externa y eje extendido, y la masa y el centro de gravedad de la carga

   * - V3.8.5
     - 2025-08-20
     - | 1.La interfaz MoveL() añade el parámetro config de cinemática inversa y el parámetro velAccParamMode
       | 2.La interfaz MoveC() añade el parámetro config de cinemática inversa y el parámetro velAccParamMode
       | 3.La interfaz Circle() añade el parámetro config de cinemática inversa y el parámetro velAccParamMode
       | 4.La interfaz NewSpiral() añade el parámetro config de cinemática inversa
       | 5.La interfaz NewSplinePoint() añade el parámetro config de cinemática inversa
       | 6.La interfaz ExtAxisSyncMoveJ() añade el parámetro config de cinemática inversa
       | 7.La interfaz ExtAxisSyncMoveL() añade el parámetro config de cinemática inversa
       | 8.La interfaz ExtAxisSyncMoveC() añade el parámetro config de cinemática inversa
       | 9.Añadir la interfaz LaserRecordPoint(coordID)
       | 10.Añadir la interfaz SetExAxisRobotPlan(strategy)
       | 11.Añadir la interfaz OpenLuaUpload(filePath)
       | 12.Añadir la interfaz GetFieldBusConfig()
       | 13.Añadir la interfaz FieldBusSlaveWriteDO(DOIndex,wirteNum,status)
       | 14.Añadir la interfaz FieldBusSlaveWriteAO(AOIndex,wirteNum,status)
       | 15.Añadir la interfaz FieldBusSlaveReadDI(DOIndex,readeNum)
       | 16.Añadir la interfaz FieldBusSlaveReadAI(AOIndex,readeNum)
       | 17.Añadir la interfaz FieldBusSlaveWaitDI(DIIndex,status,waitMs)
       | 18.Añadir la interfaz FieldBusSlaveWaitAI(AIIndex,waitType,value,waitMs)
       | 19.Añadir la interfaz SetSuckerCtrl(slaveID,len,ctrlValue)
       | 20.Añadir la interfaz GetSuckerState(slaveID)
       | 21.Añadir la interfaz WaitSuckerState(slaveID,state,ms)

   * - V3.8.4
     - 2025-07-17
     - | 1.La interfaz ExtAxisMove() añade el parámetro de suavizado blend
       | 2.Añadir la interfaz SetFocusCalibPoint(pointNum,point)
       | 3.Añadir la interfaz ComputeFocusCalib(pointNum)
       | 4.Añadir la interfaz FocusStart(kp,kpredic,aMax,vMax,type)
       | 5.Añadir la interfaz FocusEnd()
       | 6.Añadir la interfaz SetFocusPosition(pos)
       | 7.Añadir la interfaz SetEncoderUpgrade(path)
       | 8.Añadir la interfaz SetJointFirmwareUpgrade(type,path)
       | 9.Añadir la interfaz SetCtrlFirmwareUpgrade(type,path)
       | 10.Añadir la interfaz SetEndFirmwareUpgrade(type,path)
       | 11.Añadir la interfaz JointAllParamUpgrade(path)
       
   * - V3.8.3
     - 2025-06-24
     - | 1.La interfaz Circle() añade el porcentaje de aceleración y el parámetro de radio de suavizado
       | 2.La interfaz EndForceDragControl() añade el parámetro del indicador de detección de colisión del robot durante el arrastre asistido
       | 3.La interfaz ServoJ() añade el parámetro de ID de instrucción
       | 4.Añadir la interfaz SetSSHScpCmd()
       | 5.Añadir la interfaz SetWideBoxTempFanMonitorParam()
       | 6.Añadir la interfaz GetWideBoxTempFanMonitorParam()
       | 7.La estructura de estado añade los datos de estado de temperatura y corriente del ventilador de la caja de control
              
   * - V3.8.2
     - 2025-06-13
     - | 1.La interfaz WeaveSetPara() añade el parámetro del ángulo de inclinación lateral de la dirección de oscilación (desviación alrededor del eje X de oscilación)
       | 2.La interfaz WeaveChangeStart() añade los parámetros número de oscilación, velocidad de inicio de soldadura y velocidad de fin de soldadura
       | 3.La interfaz ExtDevSetUDPComParam() añade el parámetro de si establecer automáticamente la conexión tras un reinicio por corte de energía
       | 4.La interfaz SetCollisionDetectionMethod() añade la selección del modo de umbral del nivel de colisión
       | 5.La interfaz PtpFIRPlanningStart() añade el valor extremo unificado de sacudida articular
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
     - | 1.La interfaz ConveyorSetParam() añade los parámetros tipo de movimiento de seguimiento, distancia de inicio de seguimiento y distancia de fin de seguimiento
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