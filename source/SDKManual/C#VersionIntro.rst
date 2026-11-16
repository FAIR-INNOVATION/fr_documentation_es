Notas de actualización de versión
==================================

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
     - | 1.Se modifica el comentario de la interfaz GetGripperMotionDone() para obtener el estado de movimiento de la pinza; a partir de la versión 401, el protocolo del extremo está unificado con la definición de retroalimentación del estado de movimiento de la pinza de los dispositivos ya adaptados, y se añade a status el valor 3=movimiento completado con detección de caída del objeto;
       | 2.Se modifica el comentario de la interfaz GripperWaitMotionDone() para esperar el estado de movimiento de la pinza; a partir de la versión 401, el protocolo del extremo está unificado con la definición de retroalimentación del estado de movimiento de la pinza de los dispositivos ya adaptados, y se añade a status el valor 3=movimiento completado con detección de caída del objeto;
       | 3.Se modifica la descripción de los parámetros de la interfaz ServoMoveStart() de inicio del movimiento servo, añadiendo los parámetros filtertime (tiempo de filtro) y gain (array de ganancias del lazo de posición), para usar junto con las instrucciones ServoJ y ServoCart, y se añaden los ejemplos de código correspondientes;
       | 4.Se añade la interfaz DataPackageUpgrade() de carga y actualización del paquete de copia de seguridad de datos y su ejemplo de código;
       | 5.Se añade la interfaz GetDataPackageUpgradeProgress() para obtener el porcentaje de progreso de la actualización del paquete de copia de seguridad de datos;
       | 6.Se añade la interfaz GetJointAllParamUpgradeProgress() para obtener el porcentaje de progreso de la actualización de todos los parámetros de las articulaciones;
       | 7.Se añade el ejemplo de código de carga y actualización del paquete de copia de seguridad de datos y consulta del progreso de actualización;
       | 8.Se añade el ejemplo de código de actualización de todos los parámetros de las articulaciones y consulta del progreso de actualización de todos los parámetros de las articulaciones.

   * - V4.0.0
     - 2026-09-23
     - | 1.Se modifica la descripción de los parámetros de la interfaz SetWeldMachineCtrlMode() para establecer el modo de control de la soldadora, añadiendo los modos con pulso y sin pulso de la soldadora Panasonic;
       | 2.Se añade SendTCPFrame() para enviar tramas de instrucción personalizadas a través de TCP 8080 y su ejemplo de código;
       | 3.Se añade la instrucción TCFToAllJoint() para obtener las 8 soluciones de cinemática inversa del robot y su ejemplo de código;
       | 4.Se añade la instrucción SetPhySpeedInstant() para establecer la velocidad física de forma instantánea y su ejemplo de código;
       | 5.Se añade la instrucción MtlsLink() para establecer la ruta del certificado de cifrado TLS del protocolo de instrucciones integrado en el SDK y su ejemplo de código;
       | 6.Se añade la función de cifrado mTLS para el protocolo de instrucciones integrado en el SDK (TCP-8080, UDP-20007), añadiendo la habilitación del cifrado y los parámetros de configuración de la ruta del certificado de cifrado.

   * - V3.9.9
     - 2026-09-01
     - | 1.Se actualiza la interfaz GetGripperMotionDone() para obtener el estado de movimiento de la pinza, actualizando la definición del parámetro de salida del estado de la pinza y su rango de uso;
       | 2.Se modifica la interfaz GetInverseKinExaxis() de resolución de cinemática inversa con posición del eje extendido, añadiendo el parámetro de configuración de articulaciones, con valor por defecto -1 para referenciar la configuración actual de articulaciones;
       | 3.Se modifican las interfaces de control de fuerza FT_SpiralSearch()、FT_LinInsertion()、FT_FindSurface(), añadiendo el parámetro de estrategia de tratamiento cuando no se detecta fuerza/par;
       | 4.Se modifican las interfaces SetDIConfig()、GetDIConfig()、SetDOConfig()、GetDOConfig() de configuración de funciones CIO del armario de control del robot;
       | 5.Se actualizan los nombres y códigos de función añadidos en la descripción de los parámetros de la interfaz; se añade la interfaz GetSafetyParamsCheckSum() para obtener la suma de verificación de los parámetros de configuración de seguridad;
       | 6.Se modifica el ejemplo de código de control básico del robot, añadiendo el ejemplo de código de conmutación al modo manual de alta velocidad;
       | 7.Se añade la interfaz SafetyOPPasswordCheck() de verificación de la contraseña de operaciones de seguridad;
       | 8.Se añade la interfaz GripperWaitMotionDone() para esperar el estado de movimiento de la pinza, que admite configuración de tiempo de espera agotado y estrategia (solo aplicable al protocolo abierto del extremo);
       | 9.Se añade la interfaz SetRobottime() para sincronizar la hora del sistema con el robot;
       | 10.Se añade la interfaz ServoJ() de movimiento en modo servo en el espacio de articulaciones, que admite la entrada de múltiples puntos a la vez;
       | 11.Se añade el ejemplo de código de registro y reproducción láser + oscilación convencional;
       | 12.Se añade el ejemplo de código de registro y reproducción láser + movimiento asíncrono del eje extendido + oscilación en punto fijo;
       | 13.Se añade la interfaz FT_SpiralSearch() de exploración helicoidal;
       | 14.Se añade la interfaz HiSpeedManualSwitch() de conmutación al modo manual de alta velocidad;
       | 15.Se añade la interfaz SetSafetyDIConfig() de configuración de la función CI de doble canal de seguridad;
       | 16.Se añade la interfaz SetSafetyDOConfig() de configuración de la función CO de doble canal de seguridad;
       | 17.Se añade el ejemplo de verificación de configuración-lectura-puesta a cero de las funciones CI/CO de doble canal de seguridad.

   * - V3.9.8
     - 2026-07-27
     - | 1.Se actualiza la estructura de retroalimentación de estado del robot, añadiendo el estado de ejecución del programa lua actual del robot, 0-programa no en ejecución; 1-programa en ejecución (incluye pausa del programa);
       | 2.Se actualiza la descripción de los parámetros de las interfaces SetExToolCoord()、SetExToolList() para establecer el sistema de coordenadas de herramienta externa y la lista de sistemas de coordenadas de herramienta, donde el número del sistema de coordenadas de herramienta externa se actualiza a 20-39. Y se actualiza el ejemplo de código de operación del sistema de coordenadas de herramienta externa.
       | 3.Se añade a la interfaz GetToolCoordWithID() para obtener los parámetros del sistema de coordenadas de herramienta la obtención de los parámetros tipo de herramienta, posición de instalación, ID de herramienta y número de carga.
       | 4.Se añade a la interfaz GetWObjCoordWithID() para obtener los parámetros del sistema de coordenadas de pieza la obtención del parámetro sistema de coordenadas de referencia;
       | 5.Se añade a la interfaz GetExToolCoordWithID() para obtener los parámetros del sistema de coordenadas de herramienta externa la obtención del parámetro de pose del sistema de coordenadas de pieza instalado en el extremo del robot.
       | 6.Se añade a la interfaz GetExAxisCoordWithID() para obtener los parámetros del sistema de coordenadas del eje extendido la obtención de los parámetros número de eje extendido e indicador de calibración.
       | 7.Se añade a la interfaz SetVelReducePara() para establecer la velocidad de seguridad del robot la configuración del parámetro de velocidad de seguridad de las articulaciones del robot.
       | 8.Se añade al ejemplo de código de configuración de parámetros de soldadura un ejemplo de obtención del modo de control de la soldadora.
       | 9.Se añade al ejemplo de código de configuración de señales de soldadura de IO extendida un ejemplo de código de obtención de la configuración de funciones DI extendida y DO extendida.
       | 10.Se añade el ejemplo de código de configuración de la velocidad de seguridad de las articulaciones del robot;
       | 11.Se añade la interfaz WaitStationaryMotionDone() para esperar a que finalice el movimiento en vacío en el lugar;
       | 12.Se añade la interfaz SetStationaryTrackPara() de configuración de parámetros del seguimiento en el lugar de la cinta transportadora, y el ejemplo de código de seguimiento en el lugar de la cinta transportadora;
       | 13.Se añaden las interfaces WorkPieceTrsfStart()、WorkPieceTrsfEnd() de inicio y fin de la conversión del sistema de coordenadas de pieza, y el ejemplo de código de conversión del sistema de coordenadas de pieza.
       | 14.Se añade la interfaz GetWeldMachineCtrlMode() para obtener el modo de control de la soldadora.
       | 15.Se añaden las interfaces GetExtDIConfig()、GetExtDOConfig() para obtener la función DI extendida y la función DI extendida.
       
   * - V3.9.7
     - 2026-06-25
     - | 1.Se añade el error de alarma de caída de pieza de la pinza, código de fallo principal 8, código de fallo secundario 3.
       | 2.Se actualiza la estructura de retroalimentación de estado del robot, la señal de movimiento completado de la pinza añade el estado de detección de objeto; el fallo de la pinza añade 2-error de instrucción, 3-caída de pieza, otros-código de fallo de pinza+3;
       | 3.Se actualiza el ejemplo de código de restablecimiento de salidas tras la parada/pausa del programa LUA, optimizando la interfaz de carga del archivo lua, que solo requiere introducir el nombre del archivo lua y ya no la ruta.
       | 4.Se actualiza el ejemplo de código de calibración TCP con sensor fotoeléctrico, optimizando la interfaz de carga de archivos, que solo requiere introducir el nombre del archivo lua y ya no la ruta.
       | 5.Se actualiza el ejemplo de código de configuración de la velocidad durante la ejecución de la trayectoria, optimizando la interfaz de carga del archivo de trayectoria J, que solo requiere introducir el nombre del archivo de trayectoria J y ya no la ruta.
       | 6.Se actualiza el ejemplo de código de reproducción del archivo de trayectoria J del robot, optimizando la interfaz de carga del archivo de trayectoria J, que solo requiere introducir el nombre del archivo de trayectoria J y ya no la ruta.
       | 7.Se actualiza el ejemplo de código de reproducción de trayectoria (previsión de trayectoria), optimizando la interfaz de carga del archivo de trayectoria J, que solo requiere introducir el nombre del archivo de trayectoria J y ya no la ruta.
       | 8.El parámetro del nombre del programa de trabajo de la interfaz LoadDefaultProgConfig() solo requiere introducir el nombre del archivo lua y ya no la ruta.
       | 9.El parámetro del nombre del programa de trabajo de la interfaz ProgramLoad() solo requiere introducir el nombre del archivo lua y ya no la ruta.
       | 10.El parámetro del nombre del programa de trabajo de la interfaz GetLoadedProgram() solo requiere introducir el nombre del archivo lua y ya no la ruta.
       | 11.Se actualiza el ejemplo de código de operación de programas LUA del robot, optimizando la interfaz de carga de archivos, que solo requiere introducir el nombre del archivo lua y ya no la ruta.
       | 12.Se añade a la interfaz SetAxleLuaEnableDeviceType() el parámetro de estado de habilitación de la mano diestra;
       | 13.Se añade a la interfaz GetAxleLuaEnableDeviceType() el parámetro de estado de habilitación de la mano diestra;
       | 14.Se añade a la interfaz GetAxleLuaEnableDevice() el parámetro de estado del número de dispositivo habilitado de la mano diestra;
       | 15.Se amplía a 32 el array de códigos de función de la pinza de la interfaz SetAxleLuaGripperFunc(), añadiendo el control de la pinza rotativa, etc.;
       | 16.Se amplía a 32 el array de códigos de función de la pinza de la interfaz GetAxleLuaGripperFunc(), añadiendo el estado de la pinza rotativa, etc.;
       | 17.Se corrige el error en el nombre de la interfaz SetCoderCompenParams();
       | 18.Se añade la interfaz SetDexterousHandsMove() para controlar el movimiento de la mano diestra.
       | 19.Se añade la interfaz SetDexterousHandsAct() para controlar el restablecimiento y activación de la mano diestra.
       | 20.Se añade la interfaz ClearDexterousHandsError() para borrar los errores de la mano diestra.
       | 21.Se añade la interfaz SetDexterousHandsFunc() para establecer la habilitación de la función de control de movimiento de la mano diestra.
       | 22.Se añade la interfaz GetDexterousHandsFunc() para obtener la habilitación de la función de control de movimiento de la mano diestra.
       | 23.Se añade la interfaz FT_LinInsertion() de inserción lineal y el ejemplo de código de inserción rotativa con sensor de fuerza.
       | 24.Se añaden las interfaces FT_FindSurface()、FT_CalCenterStart()、FT_CalCenterEnd() relacionadas con la localización de superficie y sus ejemplos de código.
       | 25.Se añaden SetWeaveBackCenterConfig()、GetWeaveBackCenterConfig() para establecer y obtener el parámetro de retorno al punto cero del ciclo al final de la oscilación.
       | 26.Se añade la interfaz SetWeaveOffsetRT() para establecer el desplazamiento en tiempo real de la oscilación;
       | 27.Se añade la interfaz SetSpeedInstant() para establecer la velocidad en tiempo real;

   * - V3.9.6
     - 2026-05-26
     - | 1.Se actualiza la estructura de retroalimentación de estado del robot, añadiendo el estado del número del sistema de coordenadas del eje extendido;
       | 2.Se actualiza la enumeración de configuración de retroalimentación de estado del robot, añadiendo la enumeración de configuración del número del sistema de coordenadas del eje extendido;
       | 3.Se añade la interfaz ExtAxisGetParamConfig() para obtener la configuración de parámetros del eje extendido UDP.
       | 4.Se añade la interfaz ServoJV() de movimiento en modo servo de velocidad en el espacio de articulaciones del robot.
       | 5.Se añade la interfaz ServoMITStart() de inicio del control MIT de las articulaciones del robot.
       | 6.Se añade la interfaz ServoMITEnd() de fin del control MIT de las articulaciones del robot.
       | 7.Se añade la interfaz ServoMIT() de control MIT de las articulaciones del robot.
       | 8.Se añade la interfaz SetLaserWeldingParam() de configuración de parámetros de soldadura láser del robot.
       | 9.Se añade la interfaz SetLaserWeldingStartEnd() para establecer el inicio y la parada de la soldadura láser del robot.
       | 10.Se añade la interfaz SetLaserWeldingEnable() para establecer la habilitación/deshabilitación de la soldadora láser.
       | 11.Se añade la interfaz ResetLaserWeldingErr() para establecer el reinicio de fallos de la soldadora láser.
       | 12.Se añade la interfaz GetLaserWeldingRunningState() para obtener el estado de funcionamiento de la soldadora láser.
       | 13.Se añade la interfaz GetLaserWeldingErrState() para obtener el estado de fallo de la soldadora láser.
       | 14.Se añade la interfaz GetLaserWeldingParamTarget() para obtener los parámetros de configuración de la soldadura láser.
       | 15.Se añade la interfaz GetLaserWeldingParamActual() para obtener los parámetros de configuración vigentes actualmente en la soldadora láser.
       | 16.Se añade la interfaz SetLaserWeldingEnableExtDoNum() para configurar el puerto DO de habilitación de IO extendida de la soldadora láser.
       | 17.Se añade la interfaz SetLaserWeldingStartExtDoNum() para configurar el puerto DO de inicio de IO extendida de la soldadora láser.
       | 18.Se añade la interfaz SetLaserWeldingErrResetExtDoNum() para configurar el puerto DO de reinicio de fallos de IO extendida de la soldadora láser.
       | 19.Se añade la interfaz SetLaserWeldingRunningStateExtDiNum() para configurar el puerto DI del estado de funcionamiento (estado de emisión de luz) de IO extendida de la soldadora láser.
       | 20.Se añade la interfaz SetLaserWeldingErrStateExtDiNum() para configurar el puerto DI del estado de fallo de IO extendida de la soldadora láser.

   * - V3.9.5
     - 2026-04-24
     - | 1.La interfaz GetRobotRealTimeState() para obtener la última trama de datos de estado en tiempo real del robot cambia en su mecanismo interno, sin cambios en sus características externas;
       | 2.La interfaz SetTrajectoryJSpeed() añade el modo de reducción de velocidad y la conmutación directa;
       | 3.La interfaz GetSystemClock() añade la retroalimentación del código de error y la descripción de la función;
       | 4.La interfaz FieldBusSlaveWriteAO() cambia el tipo de valor de escritura a double, donde AO0~AO15 son enteros y AO16~AO31 son flotantes;
       | 5.Se actualiza el tipo de estructura de retroalimentación de estado del robot, ROBOT_STATE_PKG pasa de struct a class;
       | 6.Se añade el tipo de enumeración de configuración de retroalimentación de estado del robot;
       | 7.Se añade el ejemplo de código de configuración de la velocidad durante la ejecución de la trayectoria del robot;
       | 8.Se añade la interfaz SetRobotRealtimeStateConfig() para configurar la retroalimentación de estado CNDE del robot;
       | 9.Se añade la interfaz AddRobotRealtimeState() para añadir un estado del robot a la configuración de estados CNDE;
       | 10.Se añade la interfaz DeleteRobotRealtimeState() para eliminar un estado del robot de la configuración de estados CNDE;
       | 11.Se añade la interfaz SetRobotRealtimeStatePeriod() para establecer el período de retroalimentación de estado CNDE;
       | 12.Se añade la interfaz GetRobotRealtimeStateConfig() para obtener el conjunto de todos los estados y el período de la retroalimentación de estado CNDE actual;
       | 13.Las siguientes interfaces añaden lógica de bloqueo en estado de reconexión tras desconexión: GetSafetyCode、GetAI、GetToolAI、GetAxlePointRecordBtnState、GetToolDO、GetDO、GetActualJointPosDegree、GetActualJointSpeedsDegree、GetActualJointAccDegree、GetTargetTCPCompositeSpeed、GetActualTCPCompositeSpeed、GetTargetTCPSpeed、GetActualTCPSpeed、GetActualTCPPose、GetActualTCPNum、GetActualWObjNum、GetActualToolFlangePose、GetJointTorques、GetRobotMotionDone、GetRobotErrorCode、GetError、GetMotionQueueLength、GetProgramState、GetGripperActivateStatus、GetGripperCurPosition、GetGripperCurSpeed、GetGripperCurCurrent、GetGripperVoltage、GetGripperTemp、FT_GetForceTorqueRCS、FT_GetForceTorqueOrigin、FT_Control、GetRobotEmergencyStopState、GetSDKComState、GetSafetyStopState、LuaUpload、LuaDownLoad、ForceSensorAutoComputeLoad、AxleLuaUpload、GetGripperRotNum、GetGripperRotSpeed、GetGripperRotTorque.

   * - V3.9.4
     - 2026-03-25
     - | 1.La interfaz ServoJTStart() añade el parámetro de selección del tipo de comunicación, admitiendo comunicación XMLRPC/UDP;
       | 2.La interfaz ServoJTEnd() añade el parámetro de selección del tipo de comunicación, admitiendo comunicación XMLRPC/UDP;
       | 3.La interfaz ServoJT() añade el parámetro de selección del tipo de comunicación, admitiendo comunicación XMLRPC/UDP;
       | 4.La interfaz ServoMoveStart() añade el parámetro de selección del tipo de comunicación, admitiendo comunicación XMLRPC/UDP;
       | 5.La interfaz ServoMoveEnd() añade el parámetro de selección del tipo de comunicación, admitiendo comunicación XMLRPC/UDP;
       | 6.La interfaz ServoJ() añade el parámetro de selección del tipo de comunicación, admitiendo comunicación XMLRPC/UDP;
       | 7.La interfaz SetWeldMachineCtrlMode() añade el parámetro de selección del modo de control;
       | 8.La interfaz ExtDevGetUDPComParam() añade la obtención del parámetro de comunicación UDP: si se reconecta automáticamente tras reiniciar el armario de control;
       | 9.Se añade la interfaz SetAxleGenComEnable() para activar la función de transmisión transparente general del extremo;
       | 10.Se añade la interfaz SndRcvAxleGenComCmdData() para que el extremo envíe datos no periódicos y espere la respuesta;
       | 11.Se añade la interfaz SetRobotStopOnComDisc() para establecer la parada del robot al desconectarse la comunicación del puerto;
       | 12.Se añade la interfaz GetRobotStopOnComDisc() para obtener los parámetros de parada del robot al desconectarse la comunicación del puerto;
       | 13.Se añade la interfaz SetDIConfig() para establecer la función del puerto CI configurable del armario de control;
       | 14.Se añade la interfaz GetDIConfig() para obtener la función del puerto CI configurable del armario de control;
       | 15.Se añade la interfaz SetDOConfig() para establecer la función del puerto CO configurable del armario de control;
       | 16.Se añade la interfaz GetDOConfig() para obtener la función del puerto CO configurable del armario de control;
       | 17.Se añade la interfaz SetToolDIConfig() para establecer la función del puerto End-CI configurable del extremo;
       | 18.Se añade la interfaz GetToolDIConfig() para obtener la función del puerto End-CI configurable del extremo;
       | 19.Se añade la interfaz SetDIConfigLevel() para establecer el estado activo del CI configurable del armario de control;
       | 20.Se añade la interfaz GetDIConfigLevel() para obtener el estado activo del CI configurable del armario de control;
       | 21.Se añade la interfaz SetDOConfigLevel() para establecer el estado activo del CO configurable del armario de control;
       | 22.Se añade la interfaz GetDOConfigLevel() para obtener el estado activo del CO configurable del armario de control;
       | 23.Se añade la interfaz SetToolDIConfigLevel() para establecer el estado activo del CI configurable del extremo;
       | 24.Se añade la interfaz GetToolDIConfigLevel() para obtener el estado activo del CI configurable del extremo;
       | 25.Se añade la interfaz SetStandardDILevel() para establecer el estado activo del DI estándar del armario de control;
       | 26.Se añade la interfaz GetStandardDILevel() para obtener el estado activo del DI estándar del armario de control;
       | 27.Se añade la interfaz SetStandardDOLevel() para establecer el estado activo del DO estándar del armario de control;
       | 28.Se añade la interfaz GetStandardDOLevel() para obtener el estado activo del DO estándar del armario de control;
       | 29.Se añade la interfaz SetExAxisCmdDoneTimeUDP() de configuración del tiempo de finalización de posicionamiento del eje extendido;
       | 30.Se añade la interfaz OpenLuaDownload() para descargar el archivo Lua de protocolo abierto;
       | 31.Se añade la interfaz OpenLuaDelete() para eliminar el archivo Lua de protocolo abierto;
       | 32.Se añade la interfaz AllOpenLuaDelete() para eliminar el archivo Lua de protocolo abierto;
       | 33.Se añade la interfaz SendUDPFrameUDP () para enviar tramas de instrucción;
       | 34.Se añade la interfaz SetCmdRpyCallback() para establecer la función de callback del resultado de ejecución de las instrucciones enviadas por el SDK a través de UDP;
       | 35.Se añade la interfaz SetVelReducePara() para establecer los parámetros de velocidad de seguridad;
       | 36.Se añade la interfaz OriginPointWeaveStart() de inicio de la oscilación en punto fijo;
       | 37.Se añade la interfaz OriginPointWeaveEnd() de fin de la oscilación en punto fijo;
       | 38.Se añade la interfaz SetUserLEDColor() para establecer el color de la luz del extremo del robot definido por el usuario;
       | 39.Se añade la interfaz MoveToTPDStart() para moverse al punto inicial del registro de trayectoria TPD;
   
   * - V3.9.3
     - 2026-02-11
     - | 1.La interfaz ServoCart() añade el parámetro del eje extendido
       | 2.La interfaz SetOutputResetCtlBoxDO() añade el parámetro de si se recarga el estado DO antes del restablecimiento tras reanudar la pausa
       | 3.La interfaz SetOutputResetCtlBoxAO() añade el parámetro de si se recarga el estado DO antes del restablecimiento tras reanudar la pausa
       | 4.La interfaz SetOutputResetAxleDO() añade el parámetro de si se recarga el estado DO antes del restablecimiento tras reanudar la pausa
       | 5.La interfaz SetOutputResetAxleAO() añade el parámetro de si se recarga el estado DO antes del restablecimiento tras reanudar la pausa
       | 6.La interfaz SetOutputResetExtDO() añade el parámetro de si se recarga el estado DO antes del restablecimiento tras reanudar la pausa
       | 7.La interfaz SetOutputResetExtAO() añade el parámetro de si se recarga el estado DO antes del restablecimiento tras reanudar la pausa
       | 8.La interfaz SetOutputResetSmartToolDO() añade el parámetro de si se recarga el estado DO antes del restablecimiento tras reanudar la pausa
       | 9.Se añade la interfaz GetInverseKinExaxis() de resolución de cinemática inversa con posición del eje extendido

   * - V3.9.2
     - 2026-01-26
     - | 1.La interfaz FT_RotInsertion() añade el parámetro de estrategia de tratamiento cuando no se detecta fuerza/par
       | 2.La interfaz LaserSensorRecordandReplay() añade los parámetros relacionados con el seguimiento en punto fijo del robot
       | 3.Se añade la interfaz MoveStationary()
       | 4.Se añade la interfaz TCPComputeRPY()
       | 5.Se añade la interfaz TCPComputeXYZ()
       | 6.Se añade la interfaz TCPRecordFlangePosStart()
       | 7.Se añade la interfaz TCPRecordFlangePosEnd()
       | 8.Se añade la interfaz TCPGetRecordFlangePos()
       | 9.Se añade la interfaz PhotoelectricSensorTCPCalibration()

   * - V3.9.1
     - 2025-12-25
     - | 1.La interfaz MoveL() añade el parámetro oacc de factor de escala de aceleración/parámetro de aceleración física
       | 2.La interfaz MoveC() añade el parámetro oacc de factor de escala de aceleración/parámetro de aceleración física
       | 3.La interfaz Circle() optimiza la descripción de los parámetros de velocidad física y aceleración física
       | 4.Se añade la función sobrecargada FT_Control() con los parámetros umbral de activación rx, ry y coeficiente de ajuste de par
       | 5.Se añade la interfaz SerCoderCompenParams()

   * - V3.9.0
     - 2025-11-26
     - | 1.La interfaz JointSensitivityCalibration() añade el retorno de la linealidad de las articulaciones j1~j6
       | 2.Se añade la interfaz JointHysteresisError()
       | 3.Se añade la interfaz JointRepeatability()
       | 4.Se añade la interfaz SetAdmittanceParams()
       | 5.Se añade la interfaz MoveToIntersectLineStart()
       | 6.Se añade la interfaz MoveIntersectLine()
       
   * - V3.8.7
     - 2025-10-21
     - | 1.FT_Control() añade los parámetros de masa y amortiguación
       | 2.Se añade la interfaz JointSensitivityCalibration()
       | 3.Se añade la interfaz JointSensitivityCollect()
       | 4.Se añade la interfaz MotionQueueClear()
       | 5.Se añade la interfaz GetSlavePortErrCounter()
       | 6.Se añade la interfaz SlavePortErrCounterClear()
       | 7.Se añade la interfaz SetVelFeedForwardRatio()
       | 8.Se añade la interfaz GetVelFeedForwardRatio()
       | 9.Se añade la interfaz RobotMCULogCollect()
       | 10.La estructura de estado añade el contador de instrucciones ServoJ y los datos de la última posición objetivo de instrucción
       | 11.La estructura de parámetros de la nueva hélice SpiralParam añade el modo de parámetros de velocidad y aceleración

   * - V3.8.6
     - 2025-09-19
     - | 1.La interfaz SetLoadCoord() añade el parámetro del número de carga
       | 2.Se añade la interfaz LaserTrackingLaserOnOff()
       | 3.Se añade la interfaz LaserTrackingTrackOnOff()
       | 4.Se añade la interfaz LaserTrackingSearchStart_xyz()
       | 5.Se añade la interfaz LaserTrackingSearchStart_point()
       | 6.Se añade la interfaz LaserTrackingSearchStop()
       | 7.Se añade la interfaz LaserTrackingSensorConfig()
       | 8.Se añade la interfaz LaserTrackingSensorSamplePeriod()
       | 9.Se añade la interfaz LoadPosSensorDriver()
       | 10.Se añade la interfaz UnLoadPosSensorDriver()
       | 11.Se añade la interfaz LaserSensorRecord1()
       | 12.Se añade la interfaz LaserSensorReplay()
       | 13.Se añade la interfaz MoveLTR()
       | 14.Se añade la interfaz LaserSensorRecordandReplay()
       | 15.Se añade la interfaz MoveToLaserRecordStart()
       | 16.Se añade la interfaz MoveToLaserRecordEnd()
       | 17.Se añade la interfaz MoveToLaserSeamPos()
       | 18.Se añade la interfaz GetLaserSeamPos()
       | 19.Se añade la interfaz ImpedanceControlStartStop()
       | 20.Se añade la interfaz GetToolCoordWithID()
       | 21.Se añade la interfaz GetWObjCoordWithID()
       | 22.Se añade la interfaz GetExToolCoordWithID()
       | 23.Se añade la interfaz GetExAxisCoordWithID()
       | 24.Se añade la interfaz GetTargetPayloadWithID()
       | 25.Se añade la interfaz GetExAxisCoordWithID()
       | 26.Se añade la interfaz GetCurWObjCoord()
       | 27.Se añade la interfaz GetCurExToolCoord()
       | 28.Se añade la interfaz GetCurExToolCoord()
       | 29.Se añade la interfaz KernelUpgrade()
       | 30.Se añade la interfaz GetKernelUpgradeResult()
       | 31.Se añade la interfaz CustomWeaveSetPara()
       | 32.Se añade la interfaz CustomWeaveGetPara()
       | 33.La estructura de estado añade los datos del sistema de coordenadas de herramienta, pieza, herramienta externa y eje extendido, así como la masa y el centro de gravedad de la carga

   * - V3.8.5
     - 2025-08-20
     - | 1.Se añade la interfaz OpenLuaUpload()
       | 2.Se añade la interfaz GetFieldBusConfig()
       | 3.Se añade la interfaz FieldBusSlaveWriteDO()
       | 4.Se añade la interfaz FieldBusSlaveWriteAO()
       | 5.Se añade la interfaz FieldBusSlaveReadDI()
       | 6.Se añade la interfaz FieldBusSlaveReadAI()
       | 7.Se añade la interfaz FieldBusSlaveWaitDI()
       | 8.Se añade la interfaz FieldBusSlaveWaitAI()
       | 9.Se añade la interfaz SetSuckerCtrl()
       | 10.Se añade la interfaz GetSuckerState()
       | 11.Se añade la interfaz WaitSuckerState()
       | 12.Se añade la interfaz MoveL() con el modo de parámetros de velocidad y aceleración velAccParamMode
       | 13.Se añade la función sobrecargada 1 de MoveL()
       | 14.Se añade la función sobrecargada 2 de MoveL()
       | 15.Se añade la interfaz MoveC() con el modo de parámetros de velocidad y aceleración velAccParamMode
       | 16.Se añade la función sobrecargada 1 de MoveC()
       | 17.Se añade la interfaz Circle() con el modo de parámetros de velocidad y aceleración velAccParamMode
       | 18.Se añade la función sobrecargada 1 de Circle()
       | 19.Se añade la interfaz SetExAxisRobotPlan()

   * - V3.8.4
     - 2025-07-17
     - | 1.La interfaz ExtAxisMove() añade el parámetro de suavizado blend
       | 2.Se añade la interfaz SetFocusCalibPoint()
       | 3.Se añade la interfaz ComputeFocusCalib()
       | 4.Se añade la interfaz SetFocusPosition()
       | 5.Se añade la interfaz FocusStart()
       | 6.Se añade la interfaz FocusEnd()
       | 7.Se añade la interfaz SetEncoderUpgrade()
       | 8.Se añade la interfaz SetJointFirmwareUpgrade()
       | 9.Se añade la interfaz SetCtrlFirmwareUpgrade()
       | 10.Se añade la interfaz SetEndFirmwareUpgrade()
       | 11.Se añade la interfaz JointAllParamUpgrade()
       
   * - V3.8.3
     - 2025-06-24
     - | 1.La interfaz Circle() añade los parámetros de porcentaje de aceleración y radio de suavizado
       | 2.La interfaz EndForceDragControl() añade el parámetro del indicador de detección de colisiones del robot durante el arrastre asistido
       | 3.La interfaz ServoJ() añade el parámetro de ID de instrucción
       | 4.Se añade la interfaz SetSSHScpCmd()
       | 5.Se añade la interfaz SetWideBoxTempFanMonitorParam()
       | 6.Se añade la interfaz GetWideBoxTempFanMonitorParam()
       | 7.La estructura de estado añade los datos de estado de temperatura y corriente del ventilador del armario de control
              
   * - V3.8.2
     - 2025-06-13
     - | 1.La interfaz WeaveSetPara() añade el parámetro del ángulo de inclinación lateral de la dirección de oscilación (desviación alrededor del eje X de oscilación)
       | 2.La interfaz WeaveChangeStart() añade los parámetros número de oscilación, velocidad de inicio de soldadura y velocidad de fin de soldadura
       | 3.La interfaz ExtDevSetUDPComParam() añade el parámetro de si se establece automáticamente la conexión tras apagado y reinicio
       | 4.La interfaz SetCollisionDetectionMethod() añade la selección del modo de umbral del nivel de colisión
       | 5.La interfaz PtpFIRPlanningStart() añade el valor extremo unificado de jerk de las articulaciones
       | 6.Se añade la interfaz WeldingSetVoltageGradualChangeStart()
       | 7.Se añade la interfaz WeldingSetVoltageGradualChangeEnd()
       | 8.Se añade la interfaz WeldingSetCurrentGradualChangeStart()
       | 9.Se añade la interfaz WeldingSetCurrentGradualChangeEnd()
       | 10.Se añade la interfaz ArcWeldTraceAIChannelCurrent()
       | 11.Se añade la interfaz ArcWeldTraceAIChannelVoltage()
       | 12.Se añade la interfaz ArcWeldTraceCurrentPara()
       | 13.Se añade la interfaz ArcWeldTraceVoltagePara()
       | 14.Se añade la interfaz GetSmarttoolBtnState()
       | 15.Se añade la interfaz ExtAxisGetCoord()
                     
   * - V3.8.1
     - 2025-04-24
     - | 1.La interfaz ConveyorSetParam() añade los parámetros tipo de movimiento de seguimiento, distancia de inicio de seguimiento y distancia de fin de seguimiento
       | 2.Se añade la interfaz AccSmoothStart()
       | 3.Se añade la interfaz AccSmoothEnd()
       | 4.Se añade la interfaz RbLogDownload()
       | 5.Se añade la interfaz AllDataSourceDownload()
       | 6.Se añade la interfaz DataPackageDownload()
       | 7.Se añade la interfaz GetRobotSN()
       | 8.Se añade la interfaz ShutDownRobotOS()
       | 9.Se añade la interfaz ConveyorComDetect()
       | 10.Se añade la interfaz ConveyorComDetectTrigger()
                     
   * - V3.8.0
     - 2025-02-12
     - | 1.La interfaz EndForceDragControl() añade el parámetro de evitación de singularidades
       | 2.La interfaz ArcWeldTraceControl() añade el parámetro de desplazamiento
       | 3.Se añade la interfaz WeaveChangeStart()
       | 4.Se añade la interfaz WeaveChangeEnd()
       | 5.Se añade la interfaz LoadTrajectoryLA()
       | 6.Se añade la interfaz MoveTrajectoryLA()
       | 7.Se añade la interfaz CustomCollisionDetectionStart()
       | 8.Se añade la interfaz CustomCollisionDetectionEnd()