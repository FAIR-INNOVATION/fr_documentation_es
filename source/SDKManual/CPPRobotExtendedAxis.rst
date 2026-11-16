Eje extendido
=================

.. toctree:: 
    :maxdepth: 5

Establecer los parámetros del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer los parámetros del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo
    * @param [in] servoCompany Fabricante del accionamiento servo, 1-Dynatech
    * @param [in] servoModel Modelo del accionamiento servo, 1-FD100-750C
    * @param [in] servoSoftVersion Versión de software del accionamiento servo, 1-V1.0
    * @param [in] servoResolution Resolución del codificador
    * @param [in] axisMechTransRatio Relación de transmisión mecánica
    * @return Código de error
    */
    errno_t AuxServoSetParam(int servoId, int servoCompany, int servoModel, int servoSoftVersion, int servoResolution, double axisMechTransRatio);

Obtener los parámetros de configuración del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener los parámetros de configuración del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo
    * @param [out] servoCompany Fabricante del accionamiento servo, 1-Dynatech
    * @param [out] servoModel Modelo del accionamiento servo, 1-FD100-750C
    * @param [out] servoSoftVersion Versión de software del accionamiento servo, 1-V1.0
    * @param [out] servoResolution Resolución del codificador
    * @param [out] axisMechTransRatio Relación de transmisión mecánica
    * @return Código de error
    */
    errno_t AuxServoGetParam(int servoId, int* servoCompany, int* servoModel, int* servoSoftVersion, int* servoResolution, double* axisMechTransRatio);
    
Establecer la habilitación/deshabilitación del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la habilitación/deshabilitación del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo
    * @param [in] status Estado de habilitación, 0-deshabilitar, 1-habilitar
    * @return Código de error
    */
    errno_t AuxServoEnable(int servoId, int status);

Establecer el modo de control del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el modo de control del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo
    * @param [in] mode Modo de control, 0-modo de posición, 1-modo de velocidad
    * @return Código de error
    */
    errno_t AuxServoSetControlMode(int servoId, int mode);

Establecer la posición objetivo del eje extendido 485 (modo de posición)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la posición objetivo del eje extendido 485 (modo de posición)
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo
    * @param [in] pos Posición objetivo, mm o °
    * @param [in] speed Velocidad objetivo, mm/s o °/s
    * @return Código de error
    */
    errno_t AuxServoSetTargetPos(int servoId, double pos, double speed);

Establecer el par objetivo del eje extendido 485 (modo de par) - aún no disponible
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el par objetivo del eje extendido 485 (modo de par)
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo
    * @param [in] torque Par objetivo, Nm
    * @return Código de error
    */
    errno_t AuxServoSetTargetTorque(int servoId, double torque);

Establecer el retorno a cero del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el retorno a cero del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo
    * @param [in] mode Modo de retorno a cero, 0-retorno a cero en la posición actual; 1-retorno a cero en el límite
    * @param [in] searchVel Velocidad de retorno a cero, mm/s o °/s
    * @param [in] latchVel Velocidad de enclavamiento, mm/s o °/s
    * @return Código de error
    */
    errno_t AuxServoHoming(int servoId, int mode, double searchVel, double latchVel);
    
Borrar la información de error del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Borrar la información de error del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo
    * @return Código de error
    */
    errno_t AuxServoClearError(int servoId);

Obtener el estado del servo del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado del servo del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo
    * @param [out] servoErrCode Código de fallo del accionamiento servo
    * @param [out] servoState Estado del accionamiento servo [número decimal convertido a binario, bit0-bit5: servo habilitado-servo en funcionamiento-límite positivo activado-límite negativo activado-posicionamiento completado-retorno a cero completado]
    * @param [out] servoPos Posición actual del servo mm o °
    * @param [out] servoSpeed Velocidad actual del servo mm/s o °/s
    * @param [out] servoTorque Par actual del servo Nm
    * @return Código de error
    */
    errno_t AuxServoGetStatus(int servoId, int* servoErrCode, int* servoState, double* servoPos, double* servoSpeed, double* servoTorque);

Establecer la velocidad objetivo del eje extendido 485 (modo de velocidad)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la velocidad objetivo del eje extendido 485 (modo de velocidad)
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo
    * @param [in] speed Velocidad objetivo, mm/s o °/s
    * @return Código de error
    */
    errno_t AuxServoSetTargetSpeed(int servoId, double speed);
    
Establecer el número de eje de los datos del eje extendido 485 en la retroalimentación de estado
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el número de eje de los datos del eje extendido 485 en la retroalimentación de estado
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo
    * @return Código de error
    */
    errno_t AuxServosetStatusID(int servoId);

Establecer la aceleración y desaceleración de movimiento del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la aceleración y desaceleración de movimiento del eje extendido 485
    * @param [in] acc Aceleración de movimiento del eje extendido 485
    * @param [in] dec Desaceleración de movimiento del eje extendido 485
    * @return Código de error
    */
    errno_t AuxServoSetAcc(double acc, double dec);

Establecer la aceleración y desaceleración de parada de emergencia del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la aceleración y desaceleración de parada de emergencia del eje extendido 485
    * @param [in] acc Aceleración de parada de emergencia del eje extendido 485
    * @param [in] dec Desaceleración de parada de emergencia del eje extendido 485
    * @return Código de error
    */
    errno_t AuxServoSetEmergencyStopAcc(double acc, double dec);

Obtener la aceleración y desaceleración de movimiento del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la aceleración y desaceleración de movimiento del eje extendido 485
    * @param [out] acc Aceleración de movimiento del eje extendido 485
    * @param [out] dec Desaceleración de movimiento del eje extendido 485
    * @return Código de error
    */
    errno_t AuxServoGetAcc(double& acc, double& dec);

Obtener la aceleración y desaceleración de parada de emergencia del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la aceleración y desaceleración de parada de emergencia del eje extendido 485
    * @param [out] acc Aceleración de parada de emergencia del eje extendido 485
    * @param [out] dec Desaceleración de parada de emergencia del eje extendido 485
    * @return Código de error
    */
    errno_t AuxServoGetEmergencyStopAcc(double& acc, double& dec);

Ejemplo de código de control del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:
        
    int Test485Auxservo(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      int retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      int servoCompany;
      int servoModel;
      int servoSoftVersion;
      int servoResolution;
      double axisMechTransRatio;
      retval = robot.AuxServoGetParam(1, &servoCompany, &servoModel, &servoSoftVersion, &servoResolution, &axisMechTransRatio);
      std::cout << "servoCompany " << servoCompany << "\n"
        << "servoModel " << servoModel << "\n"
        << "servoSoftVersion " << servoSoftVersion << "\n"
        << "servoResolution " << servoResolution << "\n"
        << "axisMechTransRatio " << axisMechTransRatio << "\n"
        << std::endl;
      retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      retval = robot.AuxServoGetParam(1, &servoCompany, &servoModel, &servoSoftVersion, &servoResolution, &axisMechTransRatio);
      std::cout << "servoCompany " << servoCompany << "\n"
        << "servoModel " << servoModel << "\n"
        << "servoSoftVersion " << servoSoftVersion << "\n"
        << "servoResolution " << servoResolution << "\n"
        << "axisMechTransRatio " << axisMechTransRatio << "\n"
        << std::endl;
      retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      robot.Sleep(3000);
      robot.AuxServoSetAcc(3000, 3000);
      robot.AuxServoSetEmergencyStopAcc(5000, 5000);
      robot.Sleep(1000);
      double emagacc = 0, acc = 0;
      double emagdec = 0, dec = 0;
      robot.AuxServoGetEmergencyStopAcc(emagacc, emagdec);
      printf("emergency acc is %f dec is %f \n", emagacc, emagdec);
      robot.AuxServoGetAcc(acc, dec);
      printf("acc is %f dec is %f \n", acc, dec);
      robot.AuxServoSetControlMode(1, 0);
      robot.Sleep(2000);
      retval = robot.AuxServoEnable(1, 0);
      std::cout << "AuxServoEnable disenable " << retval << std::endl;
      robot.Sleep(1000);
      int servoerrcode = 0;
      int servoErrCode;
      int servoState;
      double servoPos;
      double servoSpeed;
      double servoTorque;
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoState " << servoState << std::endl;
      robot.Sleep(1000);;
      retval = robot.AuxServoEnable(1, 1);
      std::cout << "AuxServoEnable enable " << retval << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoState " << servoState << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoHoming(1, 1, 5, 1);
      std::cout << "AuxServoHoming " << retval << std::endl;
      robot.Sleep(3000);
      retval = robot.AuxServoSetTargetPos(1, 200, 30);
      std::cout << "AuxServoSetTargetPos " << retval << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoSpeed " << servoSpeed << std::endl;
      robot.Sleep(8000);
      robot.AuxServoSetControlMode(1, 1);
      robot.Sleep(2000);
      robot.AuxServoEnable(1, 0);
      robot.Sleep(1000);
      robot.AuxServoEnable(1, 1);
      robot.Sleep(1000);
      robot.AuxServoSetTargetSpeed(1, 100, 80);
      robot.Sleep(5000);
      robot.AuxServoSetTargetSpeed(1, 0, 80);
      robot.CloseRPC();
      return 0;
    }

Configuración de los parámetros de comunicación del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Configuración de los parámetros de comunicación del eje extendido UDP
    * @param [in] ip Dirección IP del PLC
    * @param [in] port  Número de puerto
    * @param [in] period    Período de comunicación (ms, por defecto 2, no modifique este parámetro)
    * @param [in] lossPkgTime   Tiempo de detección de pérdida de paquetes (ms)
    * @param [in] lossPkgNum    Número de pérdidas de paquetes
    * @param [in] disconnectTime    Duración de confirmación de desconexión de comunicación
    * @param [in] reconnectEnable   Habilitación de reconexión automática tras desconexión de comunicación 0-no habilitar 1-habilitar
    * @param [in] reconnectPeriod   Intervalo del período de reconexión (ms)
    * @param [in] reconnectNum  Número de reconexiones
    * @param [in] selfConnect Si se establece automáticamente la conexión tras apagado y reinicio; 0-no establecer conexión; 1-establecer conexión
    * @return Código de error
    */
    errno_t ExtDevSetUDPComParam(std::string ip, int port, int period, int lossPkgTime, int lossPkgNum, int disconnectTime, int reconnectEnable, int reconnectPeriod, int reconnectNum, int selfConnect = 1);
        
Obtener los parámetros de comunicación del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener los parámetros de comunicación del eje extendido UDP
    * @param [out] ip Dirección IP del PLC
    * @param [out] port Número de puerto
    * @param [out] period   Período de comunicación (ms, por defecto 2, no modifique este parámetro)
    * @param [out] lossPkgTime  Tiempo de detección de pérdida de paquetes (ms)
    * @param [out] lossPkgNum   Número de pérdidas de paquetes
    * @param [out] disconnectTime   Duración de confirmación de desconexión de comunicación
    * @param [out] reconnectEnable  Habilitación de reconexión automática tras desconexión de comunicación 0-no habilitar 1-habilitar
    * @param [out] reconnectPeriod  Intervalo del período de reconexión (ms)
    * @param [out] reconnectNum Número de reconexiones
    * @param [out] selfStart Si se reconecta automáticamente tras reiniciar el armario de control; 0-no reconectar; 1-reconectar
    * @return Código de error
    */
    errno_t ExtDevGetUDPComParam(std::string& ip, int& port, int& period, int& lossPkgTime, int& lossPkgNum, int& disconnectTime, int& reconnectEnable, int& reconnectPeriod, int& reconnectNum, int& selfConnect);
        
Cargar la comunicación UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Cargar la comunicación UDP
    * @return Código de error
    */
    errno_t ExtDevLoadUDPDriver();

Descargar la comunicación UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Descargar la comunicación UDP
    * @return Código de error
    */
    errno_t ExtDevUnloadUDPDriver();

Restablecer la conexión tras una desconexión anómala de la comunicación del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Restablecer la conexión tras una desconexión anómala de la comunicación del eje extendido UDP
    * @return Código de error
    */
    errno_t ExtDevUDPClientComReset();

Cerrar la comunicación tras una desconexión anómala de la comunicación del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Cerrar la comunicación tras una desconexión anómala de la comunicación del eje extendido UDP
    * @return Código de error
    */
    errno_t ExtDevUDPClientComClose();

Configuración de los parámetros del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Configuración de los parámetros del eje extendido UDP
    * @param [in] axisID Número de eje
    * @param [in] axisType Tipo de eje extendido 0-traslación; 1-rotación
    * @param [in] axisDirection Dirección del eje extendido 0-positiva; 1-negativa 
    * @param [in] axisMax Posición máxima del eje extendido mm
    * @param [in] axisMin Posición mínima del eje extendido mm
    * @param [in] axisVel Velocidad mm/s
    * @param [in] axisAcc Aceleración mm/s2
    * @param [in] axisLead Paso mm
    * @param [in] encResolution Resolución del codificador
    * @param [in] axisOffect Desplazamiento del eje extendido en el punto inicial de la soldadura
    * @param [in] axisCompany Fabricante del accionamiento 1-Hechuan; 2-Inovance; 3-Panasonic
    * @param [in] axisModel Modelo del accionamiento 1-Hechuan-SV-XD3EA040L-E, 2-Hechuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    * @param [in] axisEncType Tipo de codificador  0-incremental; 1-absoluto
    * @return Código de error
    */
    errno_t ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, long encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Obtener los parámetros del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener los parámetros del eje extendido UDP
    * @param [in] axisID Número del eje extendido [1-4]
    * @param [out] axisType Tipo de eje extendido 0-traslación; 1-rotación
    * @param [out] axisDirection Dirección del eje extendido 0-positiva; 1-negativa
    * @param [out] axisMax Posición máxima del eje extendido mm
    * @param [out] axisMin Posición mínima del eje extendido mm
    * @param [out] axisVel Velocidad mm/s
    * @param [out] axisAcc Aceleración mm/s2
    * @param [out] axisLead Paso mm
    * @param [out] encResolution Resolución del codificador
    * @param [out] axisOffect Desplazamiento del eje extendido en el punto inicial de la soldadura
    * @param [out] axisCompany Fabricante del accionamiento 1-Hechuan; 2-Inovance; 3-Panasonic
    * @param [out] axisModel Modelo del accionamiento 1-Hechuan-SV-XD3EA040L-E, 2-Hechuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    * @param [out] axisEncType Tipo de codificador  0-incremental; 1-absoluto
    * @return Código de error
    */
    errno_t ExtAxisGetParamConfig(int axisID, int& axisType, int& axisDirection, double& axisMax, double& axisMin, double& axisVel, double& axisAcc, double& axisLead, int& encResolution, double& axisOffect, int& axisCompany, int& axisModel, int& axisEncType);

Establecer la posición de instalación del eje extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la posición de instalación del eje extendido
    * @param [in] installType 0-robot instalado sobre el eje externo, 1-robot instalado fuera del eje externo
    * @return Código de error
    */
    errno_t SetRobotPosToAxis(int installType);

Establecer la configuración de los parámetros DH del sistema de ejes extendidos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la configuración de los parámetros DH del sistema de ejes extendidos
    * @param [in]  axisConfig Configuración del eje externo, 0-guía lineal de un solo grado de libertad, 1-posicionador tipo L de dos grados de libertad, 2-tres grados de libertad, 3-cuatro grados de libertad, 4-posicionador de un solo grado de libertad
    * @param [in]  axisDHd1 Parámetro DH del eje externo d1 mm
    * @param [in]  axisDHd2 Parámetro DH del eje externo d2 mm
    * @param [in]  axisDHd3 Parámetro DH del eje externo d3 mm
    * @param [in]  axisDHd4 Parámetro DH del eje externo d4 mm
    * @param [in]  axisDHa1 Parámetro DH del eje externo a1 mm
    * @param [in]  axisDHa2 Parámetro DH del eje externo a2 mm
    * @param [in]  axisDHa3 Parámetro DH del eje externo a3 mm
    * @param [in]  axisDHa4 Parámetro DH del eje externo a4 mm
    * @return Código de error
    */
    errno_t SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

Habilitación del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Habilitación del eje extendido UDP
    * @param [in] axisID Número de eje [1-4]
    * @param [in] status 0-deshabilitar; 1-habilitar
    * @return Código de error
    */
    errno_t ExtAxisServoOn(int axisID, int status);

Retorno a cero del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Retorno a cero del eje extendido UDP
    * @param [in] axisID Número de eje [1-4]
    * @param [in] mode Modo de retorno a cero 0-retorno a cero en la posición actual, 1-retorno a cero en el límite negativo, 2-retorno a cero en el límite positivo
    * @param [in] searchVel Velocidad de búsqueda de cero (mm/s)
    * @param [in] latchVel Velocidad de enclavamiento en la búsqueda de cero (mm/s)
    * @return Código de error
    */
    errno_t ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

Inicio del jog del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio del jog del eje extendido UDP
    * @param [in] axisID Número de eje [1-4]
    * @param [in] direction Dirección de giro 0-inversa; 1-positiva
    * @param [in] vel Velocidad (mm/s)
    * @param [in] acc Aceleración (mm/s2)
    * @param [in] maxDistance Distancia máxima del jog
    * @return Código de error
    */
    errno_t ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);
    
Parada del jog del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Parada del jog del eje extendido UDP
    * @param [in] axisID Número de eje [1-4]
    * @return Código de error
    */
    errno_t ExtAxisStopJog(int axisID);

Ejemplo de código de configuración y jog del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestUDPAxis(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
        cout << "ExtDevSetUDPComParam rtn is " << rtn << endl;
        string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0; int selfConnect = 0;
        rtn = robot.ExtDevGetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum, selfConnect);
        string patam = "\nip " + ip + "\nport " + to_string(port) + "\nperiod  " + to_string(period) + "\nlossPkgTime " + to_string(lossPkgTime) + "\nlossPkgNum  " + to_string(lossPkgNum) + "\ndisConntime  " +
            to_string(disconnectTime) + "\nreconnecable  " + to_string(reconnectEnable) + "\nreconnperiod  " + to_string(reconnectPeriod) + "\nreconnnun  " + to_string(reconnectNum) + "\nselfConnect  " + to_string(selfConnect);
        cout << "ExtDevGetUDPComParam rtn is " << rtn << patam << endl;
        robot.ExtDevLoadUDPDriver();
        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        cout << "SetExAxisCmdDoneTime rtn is " << rtn << endl;
        rtn = robot.ExtAxisServoOn(1, 1);
        cout << "ExtAxisServoOn axis id 1 rtn is " << rtn << endl;
        rtn = robot.ExtAxisServoOn(2, 1);
        cout << "ExtAxisServoOn axis id 2 rtn is " << rtn << endl;
        robot.Sleep(2000);
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        cout << "ExtAxisSetHoming rtnn is  " << rtn << endl;
        robot.Sleep(4000);
        rtn = robot.SetRobotPosToAxis(1);
        cout << "SetRobotPosToAxis rtn is " << rtn << endl;
        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
        cout << "SetAxisDHParaConfig rtn is " << rtn << endl;
        int axisType = -1;
        int axisDirection = -1;
        double axisMax = -1;
        double axisMin = -1;
        double axisVel = -1;
        double axisAcc = -1;
        double axisLead = -1;
        int encResolution = -1;
        double axisOffect = -1;
        int axisCompany = -1;
        int axisModel = -1;
        int axisEncType = -1;
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
        cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
        rtn = robot.ExtAxisGetParamConfig(1, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType);
        printf("axis id 1 ExtAxisGetParamConfig : axisType %d, axisDirection %d, axisMax %lf, axisMin %lf, axisVel %lf, axisAcc %lf, axisLead%lf, encResolution %d, axisOffect %f, axisCompany %d, axisModel %d, axisEncType %d\n",
            axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType);
            rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);
        cout << "ExtAxisParamConfig axis 2 rtn is " << rtn << endl;
        rtn = robot.ExtAxisGetParamConfig(2, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType);
        printf("axis id 2 ExtAxisGetParamConfig : axisType %d, axisDirection %d, axisMax %lf, axisMin %lf, axisVel %lf, axisAcc %lf, axisLead%lf, encResolution %d, axisOffect %f, axisCompany %d, axisModel %d, axisEncType %d\n",
            axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc, axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType);
        robot.Sleep(1000 * 3);
        robot.ExtAxisStartJog(1, 0, 10, 10, 30);
        robot.Sleep(1000 * 1);
        robot.ExtAxisStopJog(1);
        robot.Sleep(1000 * 3);
        robot.ExtAxisServoOn(1, 0);
        robot.Sleep(1000 * 3);
        robot.ExtAxisStartJog(2, 0, 10, 10, 30);
        robot.Sleep(1000 * 1);
        robot.ExtAxisStopJog(2);
        robot.Sleep(1000 * 3);
        robot.ExtAxisServoOn(2, 0);
        robot.Sleep(1000 * 1);
        robot.ExtDevUnloadUDPDriver();
        robot.CloseRPC();
        return 0;
    }

Establecer el punto de referencia del sistema de coordenadas del eje extendido - método de cuatro puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el punto de referencia del sistema de coordenadas del eje extendido - método de cuatro puntos
    * @param [in]  pointNum Número de punto [1-4]
    * @return Código de error
    */
    errno_t ExtAxisSetRefPoint(int pointNum);

Calcular el sistema de coordenadas del eje extendido - método de cuatro puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Calcular el sistema de coordenadas del eje extendido - método de cuatro puntos
    * @param [out]  coord Valor del sistema de coordenadas
    * @return Código de error
    */
    errno_t ExtAxisComputeECoordSys(DescPose& coord);

Configuración del punto de referencia del sistema de coordenadas del posicionador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Configuración del punto de referencia del sistema de coordenadas del posicionador
    * @param [in]  pointNum Número de punto [1-4]
    * @return Código de error
    */
    errno_t PositionorSetRefPoint(int pointNum);

Cálculo del sistema de coordenadas del posicionador - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Cálculo del sistema de coordenadas del posicionador - método de cuatro puntos
    * @param [out] coord Valor del sistema de coordenadas
    * @return Código de error
    */
    errno_t PositionorComputeECoordSys(DescPose& coord);

Establecer la pose del punto de referencia de calibración en el sistema de coordenadas del extremo del posicionador
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la pose del punto de referencia de calibración en el sistema de coordenadas del extremo del posicionador
    * @param [in] pos Valor de la pose
    * @return Código de error
    */
    errno_t SetRefPointInExAxisEnd(DescPose pos);

Aplicar el sistema de coordenadas del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Aplicar el sistema de coordenadas del eje extendido
    * @param [in]  applyAxisId Número del eje extendido; bit0-bit3 corresponden a los números de eje extendido 1-4; por ejemplo, para aplicar los ejes extendidos 1 y 3, sería 0b 0000 0101, es decir, 5
    * @param [in]  axisCoordNum Número del sistema de coordenadas del eje extendido
    * @param [in]  coord Valor del sistema de coordenadas
    * @param [in]  calibFlag Indicador de calibración 0-no, 1-sí
    * @return Código de error
    */
    errno_t ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Obtener el sistema de coordenadas del eje extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas del eje extendido
    * @param [out] coord Sistema de coordenadas del eje extendido
    * @return Código de error
    */
    errno_t ExtAxisGetCoord(DescPose& coord);

Ejemplo de código de calibración del sistema de coordenadas del eje extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestUDPAxisCalib(void)
    {
       ROBOT_STATE_PKG pkg = {};
       FRRobot robot;
       robot.LoggerInit();
       robot.SetLoggerLevel(1);
       int rtn = robot.RPC("192.168.58.2");
       if (rtn != 0)
       {
          return -1;
       }
       robot.SetReConnectParam(true, 30000, 500);
       rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
       cout << "ExtDevSetUDPComParam rtn is " << rtn << endl;
       string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
       rtn = robot.ExtDevGetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum);
       string patam = "\nip " + ip + "\nport " + to_string(port) + "\nperiod " + to_string(period) + "\nlossPkgTime " + to_string(lossPkgTime) + "\nlossPkgNum " + to_string(lossPkgNum) + "\ndisConntime " + to_string(disconnectTime) + "\nreconnecable " + to_string(reconnectEnable) + "\nreconnperiod " + to_string(reconnectPeriod) + "\nreconnnun " + to_string(reconnectNum);
       cout << "ExtDevGetUDPComParam rtn is " << rtn << patam << endl;
       robot.ExtDevLoadUDPDriver();
       rtn = robot.ExtAxisServoOn(1, 1);
       cout << "ExtAxisServoOn axis id 1 rtn is " << rtn << endl;
       rtn = robot.ExtAxisServoOn(2, 1);
       cout << "ExtAxisServoOn axis id 2 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.ExtAxisSetHoming(1, 0, 10, 2);
       robot.Sleep(2000);
       rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
       cout << "ExtAxisSetHoming rtnn is " << rtn << endl;
       robot.Sleep(4000);
       rtn = robot.SetRobotPosToAxis(1);
       cout << "SetRobotPosToAxis rtn is " << rtn << endl;
       rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4, 0, 0, 0, 0, 0, 0);
       cout << "SetAxisDHParaConfig rtn is " << rtn << endl;
       rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
       cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
       rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);
       cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
       DescPose toolCoord(0, 0, 210, 0, 0, 0);
       robot.SetToolCoord(1, &toolCoord, 0, 0, 1, 0);
       JointPos jSafe(115.193, -96.149, 92.489, -87.068, -89.15, -83.488);
       JointPos j1(117.559, -92.624, 100.329, -96.909, -94.057, -83.488);
       JointPos j2(112.239, -90.096, 99.282, -95.909, -89.824, -83.488);
       JointPos j3(110.839, -83.473, 93.166, -89.22, -90.499, -83.487);
       JointPos j4(107.935, -83.572, 95.424, -92.873, -87.933, -83.488);
       DescPose descSafe = {};
       DescPose desc1 = {};
       DescPose desc2 = {};
       DescPose desc3 = {};
       DescPose desc4 = {};
       ExaxisPos exaxisPos = { 0, 0, 0, 0 };
       DescPose offdese = { 0, 0, 0, 0, 0, 0 };
       robot.GetForwardKin(&jSafe, &descSafe);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.Sleep(2000);
       robot.GetForwardKin(&j1, &desc1);
       robot.MoveJ(&j1, &desc1, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.Sleep(2000);
       DescPose actualTCPPos = {};
       robot.GetActualTCPPose(0, &actualTCPPos);
       robot.SetRefPointInExAxisEnd(actualTCPPos);
       rtn = robot.PositionorSetRefPoint(1);
       cout << "PositionorSetRefPoint 1 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j2, &desc2);
       rtn = robot.MoveJ(&j2, &desc2, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(2);
       cout << "PositionorSetRefPoint 2 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j3, &desc3);
       robot.MoveJ(&j3, &desc3, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(3);
       cout << "PositionorSetRefPoint 3 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j4, &desc4);
       robot.MoveJ(&j4, &desc4, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(4);
       cout << "PositionorSetRefPoint 4 rtn is " << rtn << endl;
       robot.Sleep(2000);
       DescPose axisCoord = {};
       robot.PositionorComputeECoordSys(axisCoord);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       printf("PositionorComputeECoordSys rtn is %f %f %f %f %f %f\n", axisCoord.tran.x, axisCoord.tran.y, axisCoord.tran.z, axisCoord.rpy.rx, axisCoord.rpy.ry, axisCoord.rpy.rz);
       rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);
       cout << "ExtAxisActiveECoordSys rtn is " << rtn << endl;
    DescPose getCoord(0, 0, 0, 0, 0, 0);
    rtn = robot.ExtAxisGetCoord(getCoord);
    printf("ExtAxisGetCoord rtn is %f %f %f %f %f %f\n", getCoord.tran.x, getCoord.tran.y, getCoord.tran.z, getCoord.rpy.rx, getCoord.rpy.ry, getCoord.rpy.rz);
    robot.CloseRPC();
    return 0;
    }

Movimiento del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento del eje extendido UDP
    * @param [in] pos Posición objetivo
    * @param [in] ovl Porcentaje de velocidad
    * @param [in] blend Parámetro de suavizado (mm o ms); -1: esperar a que finalice el movimiento
    * @return Código de error
    */
    errno_t ExtAxisMove(ExaxisPos pos, double ovl, double blend = -1);

Ejemplo de código de movimiento del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestUDPAxisCalib(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      ExaxisPos axisPos;
      axisPos.ePos[0] = 20;
      axisPos.ePos[1] = 0;
      axisPos.ePos[2] = 0;
      axisPos.ePos[3] = 0;
      robot.ExtAxisMove(axisPos, 50);
      robot.CloseRPC();
      return 0;
    }

Movimiento sincronizado del eje extendido UDP con el movimiento articular del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento sincronizado del eje extendido UDP con el movimiento articular del robot
    * @param [in] joint_pos Posición articular objetivo, unidad deg
    * @param [in] desc_pos Pose cartesiana objetivo
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] epos Posición del eje extendido, unidad mm
    * @param [in] blendT [-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad ms
    * @param [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos  Magnitud del desplazamiento de pose
    * @return  Código de error
    */
    errno_t ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos);

Movimiento sincronizado del eje extendido UDP con el movimiento articular del robot (cálculo automático de cinemática directa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento sincronizado del eje extendido UDP con el movimiento articular del robot (cálculo automático de cinemática directa)
    * @param [in] joint_pos Posición articular objetivo, unidad deg
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] epos Posición del eje extendido, unidad mm
    * @param [in] blendT [-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad ms
    * @param [in] offset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos Magnitud del desplazamiento de pose
    * @return Código de error
    */
    errno_t ExtAxisSyncMoveJ(JointPos joint_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, uint8_t offset_flag, DescPose offset_pos);

Ejemplo de código de movimiento sincronizado del eje extendido UDP con el movimiento articular del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int testSyncMoveJ()
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      //1.Calibrar y aplicar el sistema de coordenadas de herramienta del robot; puede utilizar el método de cuatro puntos o de seis puntos para la calibración y aplicación del sistema de coordenadas de herramienta. Las interfaces relacionadas con la calibración del sistema de coordenadas de herramienta son las siguientes:
      //  int SetToolPoint(int point_num); //Establecer el punto de referencia de la herramienta - método de seis puntos
      //  int ComputeTool(ref DescPose tcp_pose); //Calcular el sistema de coordenadas de herramienta
      //  int SetTcp4RefPoint(int point_num);  //Establecer el punto de referencia de la herramienta - método de cuatro puntos
      //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
      //  int SetToolCoord(int id, DescPose coord, int type, int install); //Establecer el sistema de coordenadas de herramienta a aplicar
      //  int SetToolList(int id, DescPose coord, int type, int install);  //Establecer la lista de sistemas de coordenadas de herramienta a aplicar
      //2.Configurar los parámetros de comunicación UDP y cargar la comunicación UDP
      robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
      robot.ExtDevLoadUDPDriver();
      //3.Configurar los parámetros del eje extendido, incluyendo el tipo de eje extendido, los parámetros del accionamiento del eje extendido y los parámetros DH del eje extendido
      robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posicionador de un solo eje y parámetros DH
      robot.SetRobotPosToAxis(1); //Posición de instalación del eje extendido
      robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parámetros del accionamiento servo; este ejemplo es un posicionador de un solo eje, por lo que solo es necesario configurar los parámetros de un accionamiento; si elige un tipo de eje extendido con varios ejes, deberá configurar los parámetros del accionamiento para cada eje
      //4.Establecer la habilitación y el retorno a cero de los ejes seleccionados
      robot.ExtAxisServoOn(1, 0);
      robot.ExtAxisSetHoming(1, 0, 20, 3);
      //5.Realizar la calibración y aplicación del sistema de coordenadas del eje extendido
      DescPose pos = {/* Introduzca las coordenadas de su punto de calibración */ };
      robot.SetRefPointInExAxisEnd(pos);
      robot.PositionorSetRefPoint(1); /*Debe calibrar el eje extendido mediante cuatro puntos en posiciones diferentes, por lo que es necesario llamar a esta interfaz 4 veces para completar la calibración */
      DescPose coord = {};
      robot.PositionorComputeECoordSys(coord); //Calcular el resultado de la calibración del eje extendido
      robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Aplicar el resultado de la calibración al sistema de coordenadas del eje extendido
      //6.Calibrar el sistema de coordenadas de pieza sobre el eje extendido; necesitará las siguientes interfaces
      //int SetWObjCoordPoint(int point_num);
      //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
      //int SetWObjCoord(int id, DescPose coord);
      //int SetWObjList(int id, DescPose coord);
      //7.Registrar el punto inicial de su movimiento articular sincronizado
      DescPose startdescPose = {/*Introduzca sus coordenadas*/ };
      JointPos startjointPos = {/*Introduzca sus coordenadas*/ };
      ExaxisPos startexaxisPos = {/* Introduzca las coordenadas del punto inicial de su eje extendido */ };
      //8.Registrar las coordenadas del punto final de su movimiento articular sincronizado
      DescPose enddescPose = {/*Introduzca sus coordenadas*/ };
      JointPos endjointPos = {/*Introduzca sus coordenadas*/ };
      ExaxisPos endexaxisPos = {/* Introduzca las coordenadas del punto final de su eje extendido */ };
      //9.Escribir el programa de movimiento sincronizado
      //Moverse al punto inicial, suponiendo que el sistema de coordenadas de herramienta y el sistema de coordenadas de pieza aplicados son ambos el 1
      robot.ExtAxisMove(startexaxisPos, 20);
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniciar el movimiento sincronizado
      robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
      robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniciar el movimiento sincronizado
      robot.ExtAxisSyncMoveJ(endjointPos, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
      robot.CloseRPC();
    }

Movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot
    * @param [in] joint_pos  Posición articular objetivo, unidad deg
    * @param [in] desc_pos   Pose cartesiana objetivo
    * @param [in] tool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] epos  Posición del eje extendido, unidad mm
    * @param [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos  Magnitud del desplazamiento de pose
    * @return Código de error
    */
    errno_t ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot (cálculo automático de cinemática inversa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot (cálculo automático de cinemática inversa)
    * @param [in] desc_pos  Pose cartesiana objetivo
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] epos Posición del eje extendido, unidad mm
    * @param [in] offset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos Magnitud del desplazamiento de pose
    * @param [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return Código de error
    */
    errno_t ExtAxisSyncMoveL(DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, uint8_t offset_flag, DescPose offset_pos, int config = -1);

Ejemplo de código de movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int testSyncMoveL()
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      //1.Calibrar y aplicar el sistema de coordenadas de herramienta del robot; puede utilizar el método de cuatro puntos o de seis puntos para la calibración y aplicación del sistema de coordenadas de herramienta. Las interfaces relacionadas con la calibración del sistema de coordenadas de herramienta son las siguientes:
      //  int SetToolPoint(int point_num); //Establecer el punto de referencia de la herramienta - método de seis puntos
      //  int ComputeTool(ref DescPose tcp_pose); //Calcular el sistema de coordenadas de herramienta
      //  int SetTcp4RefPoint(int point_num);  //Establecer el punto de referencia de la herramienta - método de cuatro puntos
      //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
      //  int SetToolCoord(int id, DescPose coord, int type, int install); //Establecer el sistema de coordenadas de herramienta a aplicar
      //  int SetToolList(int id, DescPose coord, int type, int install);  //Establecer la lista de sistemas de coordenadas de herramienta a aplicar
      //2.Configurar los parámetros de comunicación UDP y cargar la comunicación UDP
      robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
      robot.ExtDevLoadUDPDriver();
      //3.Configurar los parámetros del eje extendido, incluyendo el tipo de eje extendido, los parámetros del accionamiento del eje extendido y los parámetros DH del eje extendido
      robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posicionador de un solo eje y parámetros DH
      robot.SetRobotPosToAxis(1); //Posición de instalación del eje extendido
      robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parámetros del accionamiento servo; este ejemplo es un posicionador de un solo eje, por lo que solo es necesario configurar los parámetros de un accionamiento; si elige un tipo de eje extendido con varios ejes, deberá configurar los parámetros del accionamiento para cada eje
      //4.Establecer la habilitación y el retorno a cero de los ejes seleccionados
      robot.ExtAxisServoOn(1, 0);
      robot.ExtAxisSetHoming(1, 0, 20, 3);
      //5.Realizar la calibración y aplicación del sistema de coordenadas del eje extendido
      DescPose pos = {/* Introduzca las coordenadas de su punto de calibración */ };
      robot.SetRefPointInExAxisEnd(pos);
      robot.PositionorSetRefPoint(1); /*Debe calibrar el eje extendido mediante cuatro puntos en posiciones diferentes, por lo que es necesario llamar a esta interfaz 4 veces para completar la calibración */
      DescPose coord = {};
      robot.PositionorComputeECoordSys(coord); //Calcular el resultado de la calibración del eje extendido
      robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Aplicar el resultado de la calibración al sistema de coordenadas del eje extendido
      //6.Calibrar el sistema de coordenadas de pieza sobre el eje extendido; necesitará las siguientes interfaces
      //int SetWObjCoordPoint(int point_num);
      //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
      //int SetWObjCoord(int id, DescPose coord);
      //int SetWObjList(int id, DescPose coord);
      //7.Registrar el punto inicial de su movimiento lineal sincronizado
      DescPose startdescPose = {/*Introduzca sus coordenadas*/ };
      JointPos startjointPos = {/*Introduzca sus coordenadas*/ };
      ExaxisPos startexaxisPos = {/* Introduzca las coordenadas del punto inicial de su eje extendido */ };
      //8.Registrar las coordenadas del punto final de su movimiento lineal sincronizado
      DescPose enddescPose = {/*Introduzca sus coordenadas*/ };
      JointPos endjointPos = {/*Introduzca sus coordenadas*/ };
      ExaxisPos endexaxisPos = {/* Introduzca las coordenadas del punto final de su eje extendido */ };
      //9.Escribir el programa de movimiento sincronizado
      //Moverse al punto inicial, suponiendo que el sistema de coordenadas de herramienta y el sistema de coordenadas de pieza aplicados son ambos el 1
      robot.ExtAxisMove(startexaxisPos, 20);
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniciar el movimiento sincronizado
      robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
      
      robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniciar el movimiento sincronizado
      robot.ExtAxisSyncMoveL(enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
      robot.CloseRPC();
    }
    
Movimiento sincronizado del eje extendido UDP con el movimiento en arco del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento sincronizado del eje extendido UDP con el movimiento en arco del robot
    * @param [in] joint_pos_p  Posición articular del punto de ruta, unidad deg
    * @param [in] desc_pos_p   Pose cartesiana del punto de ruta
    * @param [in] ptool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] puser  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_p  Posición del eje extendido en el punto intermedio, unidad mm
    * @param [in] poffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_p  Magnitud del desplazamiento de pose
    * @param [in] joint_pos_t  Posición articular del punto objetivo, unidad deg
    * @param [in] desc_pos_t   Pose cartesiana del punto objetivo
    * @param [in] ttool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] tuser  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_t  Posición del eje extendido, unidad mm
    * @param [in] toffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_t  Magnitud del desplazamiento de pose	 
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @return Código de error
    */
    errno_t ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, float ovl, float blendR);
        
Movimiento sincronizado del eje extendido UDP con el movimiento en arco del robot (cálculo automático de cinemática inversa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento sincronizado del eje extendido UDP con el movimiento en arco del robot (cálculo automático de cinemática inversa)
    * @param [in] desc_pos_p  Pose cartesiana del punto de ruta
    * @param [in] ptool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] puser Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] pvel Porcentaje de velocidad, rango [0~100]
    * @param [in] pacc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_p Posición del eje extendido, unidad mm
    * @param [in] poffset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_p Magnitud del desplazamiento de pose
    * @param [in] desc_pos_t  Pose cartesiana del punto objetivo
    * @param [in] ttool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] tuser Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] tvel Porcentaje de velocidad, rango [0~100]
    * @param [in] tacc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_t Posición del eje extendido, unidad mm
    * @param [in] toffset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_t Magnitud del desplazamiento de pose
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return Código de error
    */
    errno_t ExtAxisSyncMoveC(DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, uint8_t poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, uint8_t toffset_flag, DescPose offset_pos_t, float ovl, float blendR, int config = -1);

Ejemplo de código de movimiento sincronizado del eje extendido UDP con el movimiento en arco del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int testSyncMoveC()
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      //1.Calibrar y aplicar el sistema de coordenadas de herramienta del robot; puede utilizar el método de cuatro puntos o de seis puntos para la calibración y aplicación del sistema de coordenadas de herramienta. Las interfaces relacionadas con la calibración del sistema de coordenadas de herramienta son las siguientes:
      //  int SetToolPoint(int point_num); //Establecer el punto de referencia de la herramienta - método de seis puntos
      //  int ComputeTool(ref DescPose tcp_pose); //Calcular el sistema de coordenadas de herramienta
      //  int SetTcp4RefPoint(int point_num);  //Establecer el punto de referencia de la herramienta - método de cuatro puntos
      //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
      //  int SetToolCoord(int id, DescPose coord, int type, int install); //Establecer el sistema de coordenadas de herramienta a aplicar
      //  int SetToolList(int id, DescPose coord, int type, int install);  //Establecer la lista de sistemas de coordenadas de herramienta a aplicar
      //2.Configurar los parámetros de comunicación UDP y cargar la comunicación UDP
      robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
      robot.ExtDevLoadUDPDriver();
      //3.Configurar los parámetros del eje extendido, incluyendo el tipo de eje extendido, los parámetros del accionamiento del eje extendido y los parámetros DH del eje extendido
      robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posicionador de un solo eje y parámetros DH
      robot.SetRobotPosToAxis(1); //Posición de instalación del eje extendido
      robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parámetros del accionamiento servo; este ejemplo es un posicionador de un solo eje, por lo que solo es necesario configurar los parámetros de un accionamiento; si elige un tipo de eje extendido con varios ejes, deberá configurar los parámetros del accionamiento para cada eje
      //4.Establecer la habilitación y el retorno a cero de los ejes seleccionados
      robot.ExtAxisServoOn(1, 0);
      robot.ExtAxisSetHoming(1, 0, 20, 3);
      //5.Realizar la calibración y aplicación del sistema de coordenadas del eje extendido
      DescPose pos = {/* Introduzca las coordenadas de su punto de calibración */ };
      robot.SetRefPointInExAxisEnd(pos);
      robot.PositionorSetRefPoint(1); /*Debe calibrar el eje extendido mediante cuatro puntos en posiciones diferentes, por lo que es necesario llamar a esta interfaz 4 veces para completar la calibración */
      DescPose coord = {};
      robot.PositionorComputeECoordSys(coord); //Calcular el resultado de la calibración del eje extendido
      robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Aplicar el resultado de la calibración al sistema de coordenadas del eje extendido
      //6.Calibrar el sistema de coordenadas de pieza sobre el eje extendido; necesitará las siguientes interfaces
      //int SetWObjCoordPoint(int point_num);
      //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
      //int SetWObjCoord(int id, DescPose coord);
      //int SetWObjList(int id, DescPose coord);
      //7.Registrar el punto inicial de su movimiento en arco sincronizado
      DescPose startdescPose = {/*Introduzca sus coordenadas*/ };
      JointPos startjointPos = {/*Introduzca sus coordenadas*/ };
      ExaxisPos startexaxisPos = {/* Introduzca las coordenadas del punto inicial de su eje extendido */ };
      //8.Registrar las coordenadas del punto final de su movimiento en arco sincronizado
      DescPose enddescPose = {/*Introduzca sus coordenadas*/ };
      JointPos endjointPos = {/*Introduzca sus coordenadas*/ };
      ExaxisPos endexaxisPos = {/* Introduzca las coordenadas del punto final de su eje extendido */ };
      //9.Registrar las coordenadas del punto intermedio de su movimiento en arco sincronizado
      DescPose middescPose = {/*Introduzca sus coordenadas*/ };
      JointPos midjointPos = {/*Introduzca sus coordenadas*/ };
      ExaxisPos midexaxisPos = {/* Introduzca las coordenadas del eje extendido en el punto intermedio del arco del robot */ };
      //10.Escribir el programa de movimiento sincronizado
      //Moverse al punto inicial, suponiendo que el sistema de coordenadas de herramienta y el sistema de coordenadas de pieza aplicados son ambos el 1
      robot.ExtAxisMove(startexaxisPos, 20);
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniciar el movimiento sincronizado
      robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
      robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniciar el movimiento sincronizado
      robot.ExtAxisSyncMoveC(middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
      robot.CloseRPC();
    }
    
Establecer DO extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer DO extendida
    * @param [in] DONum Número de DO
    * @param [in] bOpen Interruptor true-activado; false-desactivado
    * @param [in] smooth Si se suaviza
    * @param [in] block Si es bloqueante
    * @return Código de error
    */
    errno_t SetAuxDO(int DONum, bool bOpen, bool smooth, bool block);
        
Establecer AO extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer AO extendida
    * @param [in] AONum Número de AO 
    * @param [in] value Valor analógico [0-4095]
    * @param [in] block Si es bloqueante
    * @return Código de error
    */
    errno_t SetAuxAO(int AONum, double value, bool block);
  
Establecer el tiempo de filtro de entrada DI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el tiempo de filtro de entrada DI extendida
    * @param [in] filterTime Tiempo de filtro (ms)
    * @return Código de error
    */
    errno_t SetAuxDIFilterTime(int filterTime);

Establecer el tiempo de filtro de entrada AI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el tiempo de filtro de entrada AI extendida
    * @param [in] filterTime Tiempo de filtro (ms)
    * @return Código de error
    */
    errno_t SetAuxAIFilterTime(int filterTime);

Esperar la entrada DI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Esperar la entrada DI extendida
    * @param [in] DINum Número de DI
    * @param [in] bOpen Interruptor 0-desactivado; 1-activado
    * @param [in] time Tiempo máximo de espera (ms)
    * @param [in] errorAlarm Si se continúa el movimiento
    * @return Código de error
    */
    errno_t WaitAuxDI(int DINum, bool bOpen, int time, bool errorAlarm);
    
Esperar la entrada AI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Esperar la entrada AI extendida
    * @param [in] AINum Número de AI
    * @param [in] sign 0-mayor que; 1-menor que
    * @param [in] value Valor de AI
    * @param [in] time Tiempo máximo de espera (ms)
    * @param [in] errorAlarm Si se continúa el movimiento
    * @return Código de error
    */
    errno_t WaitAuxAI(int AINum, int sign, int value, int time, bool errorAlarm);
        
Obtener el valor de DI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el valor de DI extendida
    * @param [in] DINum Número de DI
    * @param [in] isNoBlock Si es bloqueante
    * @param [out] isOpen 0-desactivado; 1-activado
    * @return Código de error
    */
    errno_t GetAuxDI(int DINum, bool isNoBlock, bool& isOpen);
            
Obtener el valor de AI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el valor de AI extendida
    * @param [in] AINum Número de AI
    * @param [in] isNoBlock Si es bloqueante
    * @param [in] value Valor de entrada
    * @return Código de error
    */
    errno_t GetAuxAI(int AINum, bool isNoBlock, int& value);

Ejemplo de código de IO extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestAuxDOAO(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      for (int i = 0; i < 128; i++)
      {
        robot.SetAuxDO(i, true, false, true);
        Sleep(100);
      }
      for (int i = 0; i < 128; i++)
      {
        robot.SetAuxDO(i, false, false, true);
        Sleep(100);
      }
      for (int i = 0; i < 409; i++)
      {
        robot.SetAuxAO(0, i * 10, true);
        robot.SetAuxAO(1, 4095 - i * 10, true);
        robot.SetAuxAO(2, i * 10, true);
        robot.SetAuxAO(3, 4095 - i * 10, true);
        Sleep(10);
      }
      robot.SetAuxDIFilterTime(10);
      robot.SetAuxAIFilterTime(0, 10);
      for (int i = 0; i < 20; i++)
      {
        bool curValue = false;
        int rtn = robot.GetAuxDI(i, false, curValue);
        cout << "DI" << i << "  " << curValue << endl;
      }
      int curValue = -1;
      for (int i = 0; i < 4; i++)
      {
        rtn = robot.GetAuxAI(i, true, curValue);
      }
      robot.WaitAuxDI(1, false, 1000, false);
      robot.WaitAuxAI(1, 1, 132, 1000, false);
      robot.CloseRPC();
      return 0;
    }

Habilitación del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Habilitación del dispositivo móvil
    * @param enable false-deshabilitar; true-habilitar
    * @return Código de error
    */
    errno_t TractorEnable(bool enable);

Retorno a cero del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Retorno a cero del dispositivo móvil
    * @return Código de error
    */
    errno_t TractorHoming();

Movimiento lineal del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:
    
    /**
    * @brief Movimiento lineal del dispositivo móvil
    * @param distance Distancia del movimiento lineal (mm)
    * @param vel Porcentaje de velocidad del movimiento lineal (0-100)
    * @return Código de error
    */
    errno_t TractorMoveL(double distance, double vel);

Movimiento en arco del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento en arco del dispositivo móvil
    * @param radio Radio del movimiento en arco (mm)
    * @param angle Ángulo del movimiento en arco (°)
    * @param vel Porcentaje de velocidad del movimiento lineal (0-100)
    * @return Código de error
    */
    errno_t TractorMoveC(double radio, double angle, double vel);

Parada del movimiento del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Parada del movimiento del dispositivo móvil
    * @return Código de error
    */
    errno_t TractorStop();

Ejemplo de código del dispositivo móvil
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestTractor(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10, 1);
      robot.ExtDevLoadUDPDriver();
      rtn = robot.ExtAxisServoOn(1, 1);
      rtn = robot.ExtAxisServoOn(2, 1);
      robot.Sleep(2000);
      robot.ExtAxisSetHoming(1, 0, 10, 2);
      robot.Sleep(2000);
      rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
      robot.Sleep(4000);
      robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
      robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
      robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);
      robot.TractorEnable(false);
      robot.Sleep(2000);
      robot.TractorEnable(true);
      robot.Sleep(2000);
      robot.TractorHoming();
      robot.Sleep(2000);
      robot.TractorMoveL(100, 2);
      robot.Sleep(5000);
      robot.TractorStop();
      robot.TractorMoveL(-100, 20);
      robot.Sleep(5000);
      robot.TractorMoveC(300, 90, 20);
      robot.Sleep(10000);
      robot.TractorMoveC(300, -90, 20);
      robot.Sleep(1);
      robot.CloseRPC();
      return 0;
    }

Configuración del tiempo de finalización de posicionamiento del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configuración del tiempo de finalización de posicionamiento del eje extendido UDP
    * @param [in] time Tiempo de finalización del posicionamiento [ms]
    * @return Código de error
    */
    errno_t SetExAxisCmdDoneTime(double time);