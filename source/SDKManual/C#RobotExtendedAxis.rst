Eje extendido
=================

.. toctree:: 
    :maxdepth: 5

Establecer los parámetros del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
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
    int AuxServoSetParam(int servoId, int servoCompany, int servoModel, int servoSoftVersion, int servoResolution, double axisMechTransRatio);
    
Obtener los parámetros de configuración del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
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
    int AuxServoGetParam(int servoId, ref int servoCompany, ref int servoModel, ref int servoSoftVersion, ref int servoResolution, ref double axisMechTransRatio);
    
Establecer la habilitación/deshabilitación del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer la habilitación/deshabilitación del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo 
    * @param [in] status Estado de habilitación, 0-deshabilitar, 1-habilitar
    * @return Código de error 
    */
    int AuxServoEnable(int servoId, int status);
        
Establecer el modo de control del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el modo de control del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo 
    * @param [in] mode Modo de control, 0-modo de posición, 1-modo de velocidad
    * @return Código de error 
    */
    int AuxServoSetControlMode(int servoId, int mode);

Establecer la posición objetivo del eje extendido 485 (modo de posición)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer la posición objetivo del eje extendido 485 (modo de posición)
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo 
    * @param [in] pos Posición objetivo, mm o °
    * @param [in] speed Velocidad objetivo, mm/s o °/s
    * @return Código de error 
    */
    int AuxServoSetTargetPos(int servoId, double pos, double speed);

Establecer la velocidad objetivo del eje extendido 485 (modo de velocidad)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer la velocidad objetivo del eje extendido 485 (modo de velocidad)
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo 
    * @param [in] speed Velocidad objetivo, mm/s o °/s
    * @return Código de error 
    */
    int AuxServoSetTargetSpeed(int servoId, double speed);
    
Establecer el par objetivo del eje extendido 485 (modo de par) - aún no disponible
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el par objetivo del eje extendido 485 (modo de par) - aún no disponible
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo 
    * @param [in] torque Par objetivo, Nm
    * @return Código de error 
    */
    int AuxServoSetTargetTorque(int servoId, double torque);

Establecer el retorno a cero del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el retorno a cero del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo 
    * @param [in] mode Modo de retorno a cero, 1-retorno a cero en la posición actual; 2-retorno a cero en el límite negativo; 3-retorno a cero en el límite positivo
    * @param [in] searchVel Velocidad de retorno a cero, mm/s o °/s
    * @param [in] latchVel Velocidad de enclavamiento, mm/s o °/s
    * @return Código de error 
    */
    int AuxServoHoming(int servoId, int mode, double searchVel, double latchVel);
        
Borrar la información de error del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Borrar la información de error del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo 
    * @return Código de error 
    */
    int AuxServoClearError(int servoId);

Obtener el estado del servo del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener el estado del servo del eje extendido 485
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo 
    * @param [out] servoErrCode Código de fallo del accionamiento servo
    * @param [out] servoState Estado del accionamiento servo  bit0:0-no habilitado; 1-habilitado;  bit1:0-sin movimiento; 1-en movimiento;  bit2 0-límite positivo no activado; 1-límite positivo activado; bit3 0-límite negativo no activado; 1-límite negativo activado; bit4 0-posicionamiento no completado; 1-posicionamiento completado;  bit5: 0-sin retorno a cero; 1-retorno a cero completado
    * @param [out] servoPos Posición actual del servo mm o °
    * @param [out] servoSpeed Velocidad actual del servo mm/s o °/s
    * @param [out] servoTorque Par actual del servo Nm
    * @return Código de error 
    */
    int AuxServoGetStatus(int servoId, ref int servoErrCode, ref int servoState, ref double servoPos, ref double servoSpeed, ref double servoTorque);
    
Establecer el número de eje de los datos del eje extendido 485 en la retroalimentación de estado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6
    
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer el número de eje de los datos del eje extendido 485 en la retroalimentación de estado
    * @param [in] servoId ID del accionamiento servo, rango [1-15], corresponde al ID de esclavo 
    * @return Código de error 
    */
    int AuxServosetStatusID(int servoId);

Establecer la aceleración y desaceleración de movimiento del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Establecer la aceleración y desaceleración de movimiento del eje extendido 485
    * @param [in] acc Aceleración de movimiento del eje extendido 485
    * @param [in] dec Desaceleración de movimiento del eje extendido 485
    * @return  Código de error
    */
    int AuxServoSetAcc(double acc, double dec);

Establecer la aceleración y desaceleración de parada de emergencia del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Establecer la aceleración y desaceleración de parada de emergencia del eje extendido 485
    * @param [in] acc Aceleración de parada de emergencia del eje extendido 485
    * @param [in] dec Desaceleración de parada de emergencia del eje extendido 485
    * @return  Código de error
    */
    int AuxServoSetEmergencyStopAcc(double acc, double dec);

Obtener la aceleración y desaceleración de movimiento del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Obtener la aceleración y desaceleración de movimiento del eje extendido 485
    * @param [out] acc Aceleración de movimiento del eje extendido 485
    * @param [out] dec Desaceleración de movimiento del eje extendido 485
    * @return  Código de error
    */
    int AuxServoGetAcc(ref double acc, ref double dec);

Obtener la aceleración y desaceleración de parada de emergencia del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Obtener la aceleración y desaceleración de parada de emergencia del eje extendido 485
    * @param [out] acc Aceleración de parada de emergencia del eje extendido 485
    * @param [out] dec Desaceleración de parada de emergencia del eje extendido 485
    * @return  Código de error
    */
    int AuxServoGetEmergencyStopAcc(ref double acc, ref double dec);

Ejemplo de código de control del eje extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
    :linenos:

    private void button64_Click(object sender, EventArgs e)
    {
        int retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45);
        Console.WriteLine($"AuxServoSetParam is: {retval}");

        int servoCompany = 0;
        int servoModel = 0;
        int servoSoftVersion = 0;
        int servoResolution = 0;
        double axisMechTransRatio = 0;
        retval = robot.AuxServoGetParam(1, ref servoCompany, ref servoModel, ref servoSoftVersion, ref servoResolution, ref axisMechTransRatio);
        Console.WriteLine($"servoCompany {servoCompany}\n" +
            $"servoModel {servoModel}\n" +
            $"servoSoftVersion {servoSoftVersion}\n" +
            $"servoResolution {servoResolution}\n" +
            $"axisMechTransRatio {axisMechTransRatio}\n");

        retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14);
        Console.WriteLine($"AuxServoSetParam is: {retval}");

        retval = robot.AuxServoGetParam(1, ref servoCompany, ref servoModel, ref servoSoftVersion, ref servoResolution, ref axisMechTransRatio);
        Console.WriteLine($"servoCompany {servoCompany}\n" +
            $"servoModel {servoModel}\n" +
            $"servoSoftVersion {servoSoftVersion}\n" +
            $"servoResolution {servoResolution}\n" +
            $"axisMechTransRatio {axisMechTransRatio}\n");

        retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36);
        Console.WriteLine($"AuxServoSetParam is: {retval}");
        Thread.Sleep(3000);

        robot.AuxServoSetAcc(3000, 3000);
        robot.AuxServoSetEmergencyStopAcc(5000, 5000);
        Thread.Sleep(1000);
        double emagacc = 0, acc = 0;
        double emagdec = 0, dec = 0;
        robot.AuxServoGetEmergencyStopAcc(ref emagacc, ref emagdec);
        Console.WriteLine($"emergency acc is {emagacc}  dec is {emagdec}");
        robot.AuxServoGetAcc(ref acc, ref dec);
        Console.WriteLine($"acc is {acc}  dec is {dec}");

        robot.AuxServoSetControlMode(1, 0);
        Thread.Sleep(2000);

        retval = robot.AuxServoEnable(1, 0);
        Console.WriteLine($"AuxServoEnable disenable {retval}");
        Thread.Sleep(1000);
        int servoerrcode = 0;
        int servoErrCode = 0;
        int servoState = 0;
        double servoPos = 0;
        double servoSpeed = 0;
        double servoTorque = 0;
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoState {servoState}");
        Thread.Sleep(1000);

        retval = robot.AuxServoEnable(1, 1);
        Console.WriteLine($"AuxServoEnable enable {retval}");
        Thread.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoState {servoState}");
        Thread.Sleep(1000);

        retval = robot.AuxServoHoming(1, 1, 5, 1);
        Console.WriteLine($"AuxServoHoming {retval}");
        Thread.Sleep(3000);

        retval = robot.AuxServoSetTargetPos(1, 200, 30);
        Console.WriteLine($"AuxServoSetTargetPos {retval}");
        Thread.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoSpeed {servoSpeed}");
        Thread.Sleep(8000);

        robot.AuxServoSetControlMode(1, 1);
        Thread.Sleep(2000);

        robot.AuxServoEnable(1, 0);
        Thread.Sleep(1000);
        robot.AuxServoEnable(1, 1);
        Thread.Sleep(1000);
        robot.AuxServoSetTargetSpeed(1, 100, 80);

        Thread.Sleep(5000);
        robot.AuxServoSetTargetSpeed(1, 0, 80);
    }

Configuración de los parámetros de comunicación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Configuración de los parámetros de comunicación del eje extendido UDP
    * @param [in] ip Dirección IP del PLC
    * @param [in] port	Número de puerto
    * @param [in] period	Período de comunicación (ms, por defecto 2, no modifique este parámetro)
    * @param [in] lossPkgTime	Tiempo de detección de pérdida de paquetes (ms)
    * @param [in] lossPkgNum	Número de pérdidas de paquetes
    * @param [in] disconnectTime	Duración de confirmación de desconexión de comunicación
    * @param [in] reconnectEnable	Habilitación de reconexión automática tras desconexión de comunicación 0-no habilitar 1-habilitar
    * @param [in] reconnectPeriod	Intervalo del período de reconexión (ms)
    * @param [in] reconnectNum	Número de reconexiones
    * @param [in] selfConnect Si se establece automáticamente la conexión tras apagado y reinicio; 0-no establecer conexión; 1-establecer conexión
    * @return Código de error
    */
    int ExtDevSetUDPComParam(std::string ip, int port, int period, int lossPkgTime, int lossPkgNum, int disconnectTime, int reconnectEnable, int reconnectPeriod, int reconnectNum, int selfConnect);
         
Obtener los parámetros de comunicación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Obtener los parámetros de comunicación del eje extendido UDP
    * @param [out] ip Dirección IP del PLC
    * @param [out] port	Número de puerto
    * @param [out] period	Período de comunicación (ms, por defecto 2, no modifique este parámetro)
    * @param [out] lossPkgTime	Tiempo de detección de pérdida de paquetes (ms)
    * @param [out] lossPkgNum	Número de pérdidas de paquetes
    * @param [out] disconnectTime	Duración de confirmación de desconexión de comunicación
    * @param [out] reconnectEnable	Habilitación de reconexión automática tras desconexión de comunicación 0-no habilitar 1-habilitar
    * @param [out] reconnectPeriod	Intervalo del período de reconexión (ms)
    * @param [out] reconnectNum	Número de reconexiones
    * @param [out] selfConnect Si se reconecta automáticamente tras reiniciar el armario de control; 0-no reconectar; 1-reconectar
    * @return Código de error
    */
    public int ExtDevGetUDPComParam(ref string ip, ref int port, ref int period, ref int lossPkgTime, ref int lossPkgNum, ref int disconnectTime, ref int reconnectEnable, ref int reconnectPeriod, ref int reconnectNum, ref int selfConnect)
        
Cargar la comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Cargar la comunicación UDP
    * @return Código de error
    */
    int ExtDevLoadUDPDriver();

Descargar la comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Descargar la comunicación UDP
    * @return Código de error
    */
    int ExtDevUnloadUDPDriver();

Restablecer la conexión tras una desconexión anómala de la comunicación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Restablecer la conexión tras una desconexión anómala de la comunicación del eje extendido UDP
    * @return Código de error
    */
    int ExtDevUDPClientComReset();

Cerrar la comunicación tras una desconexión anómala de la comunicación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Cerrar la comunicación tras una desconexión anómala de la comunicación del eje extendido UDP
    * @return Código de error
    */
    int ExtDevUDPClientComClose();

Configuración de los parámetros del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
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
    int ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, long encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Obtener la configuración de los parámetros del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Obtener la configuración de los parámetros del eje extendido UDP
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
    public int ExtAxisGetParamConfig(int axisID, ref int axisType, ref int axisDirection, ref double axisMax, ref double axisMin, ref double axisVel, ref double axisAcc, ref double axisLead, ref int encResolution, ref double axisOffect, ref int axisCompany, ref int axisModel, ref int axisEncType)

Establecer la posición de instalación del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Establecer la posición de instalación del eje extendido
    * @param [in] installType 0-robot instalado sobre el eje externo, 1-robot instalado fuera del eje externo
    * @return Código de error
    */
    int SetRobotPosToAxis(int installType);

Establecer la configuración de los parámetros DH del sistema de ejes extendidos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
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
    int SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

Habilitación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Habilitación del eje extendido UDP
    * @param [in] axisID Número de eje [1-4]
    * @param [in] status 0-deshabilitar; 1-habilitar
    * @return Código de error
    */
    int ExtAxisServoOn(int axisID, int status);

Retorno a cero del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Retorno a cero del eje extendido UDP
    * @param [in] axisID Número de eje [1-4]
    * @param [in] mode Modo de retorno a cero 0-retorno a cero en la posición actual, 1-retorno a cero en el límite negativo, 2-retorno a cero en el límite positivo
    * @param [in] searchVel Velocidad de búsqueda de cero (mm/s)
    * @param [in] latchVel Velocidad de enclavamiento en la búsqueda de cero (mm/s)
    * @return Código de error
    */
    int ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

Inicio del jog del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
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
    int ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);
    
Parada del jog del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Parada del jog del eje extendido UDP
    * @param [in] axisID Número de eje [1-4]
    * @return Código de error
    */
    int ExtAxisStopJog(int axisID);

Ejemplo de código de configuración y jog del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    private void button65_Click(object sender, EventArgs e)
    {
        int rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
        Console.WriteLine("ExtDevSetUDPComParam rtn is " + rtn);
        string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0; int selfConnect = 0;
        rtn = robot.ExtDevGetUDPComParam(ref ip, ref port, ref period, ref lossPkgTime, ref lossPkgNum, ref disconnectTime, ref reconnectEnable, ref reconnectPeriod, ref reconnectNum, ref selfConnect);
        string param = "\nip " + ip + "\nport " + port.ToString() + "\nperiod  " + period.ToString() + "\nlossPkgTime " + lossPkgTime.ToString() + "\nlossPkgNum  " + lossPkgNum.ToString() + "\ndisConntime  " + disconnectTime.ToString() + "\nreconnecable  " + reconnectEnable.ToString() + "\nreconnperiod  " + reconnectPeriod.ToString() + "\nreconnnun  " + reconnectNum.ToString() + "\nselfConnect  " + selfConnect.ToString();
        Console.WriteLine("ExtDevGetUDPComParam rtn is " + rtn + param);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        rtn = robot.ExtAxisSetHoming(1, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming 1 rtnn is  " + rtn);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming 2 rtnn is  " + rtn);

        Thread.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        Console.WriteLine("SetRobotPosToAxis rtn is " + rtn);
        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
        Console.WriteLine("SetAxisDHParaConfig rtn is " + rtn);


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

        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);
        rtn = robot.ExtAxisGetParamConfig(1, ref axisType, ref axisDirection, ref axisMax, ref axisMin, ref axisVel, ref axisAcc, ref axisLead, ref encResolution, ref axisOffect, ref axisCompany, ref axisModel, ref axisEncType);
        Console.WriteLine($"axis id 1 ExtAxisGetParamConfig : axisType {axisType}, axisDirection {axisDirection}, axisMax {axisMax}, axisMin {axisMin}, axisVel {axisVel}, axisAcc {axisAcc}, axisLead {axisLead}, encResolution {encResolution}, axisOffect {axisOffect}, axisCompany {axisCompany}, axisModel {axisModel}, axisEncType {axisEncType}\n");
                                                                                                                                                                                    

        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 2 rtn is " + rtn);
        rtn = robot.ExtAxisGetParamConfig(2, ref axisType, ref axisDirection, ref axisMax,  ref axisMin, ref axisVel, ref axisAcc, ref axisLead, ref encResolution, ref axisOffect, ref axisCompany, ref axisModel, ref axisEncType);
        Console.WriteLine($"axis id 2 ExtAxisGetParamConfig : axisType {axisType}, axisDirection {axisDirection}, axisMax {axisMax}, axisMin {axisMin}, axisVel {axisVel}, axisAcc {axisAcc}, axisLead {axisLead}, encResolution {encResolution}, axisOffect {axisOffect}, axisCompany {axisCompany}, axisModel {axisModel}, axisEncType {axisEncType}\n");


        Thread.Sleep(3000);
        robot.ExtAxisStartJog(1, 0, 10, 10, 30);
        Thread.Sleep(1000);
        robot.ExtAxisStopJog(1);
        Thread.Sleep(3000);
        robot.ExtAxisServoOn(1, 0);

        Thread.Sleep(3000);
        robot.ExtAxisStartJog(2, 0, 10, 10, 30);
        Thread.Sleep(1000);
        robot.ExtAxisStopJog(2);
        Thread.Sleep(3000);
        robot.ExtAxisServoOn(2, 0);
        Thread.Sleep(3000);
        robot.ExtDevUnloadUDPDriver();
    }

Establecer el punto de referencia del sistema de coordenadas del eje extendido - método de cuatro puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Establecer el punto de referencia del sistema de coordenadas del eje extendido - método de cuatro puntos
    * @param [in]  pointNum Número de punto [1-4]
    * @return Código de error
    */
    int ExtAxisSetRefPoint(int pointNum);

Calcular el sistema de coordenadas del eje extendido - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Calcular el sistema de coordenadas del eje extendido - método de cuatro puntos
    * @param [out]  coord Valor del sistema de coordenadas
    * @return Código de error
    */
    int ExtAxisComputeECoordSys(DescPose& coord);

Aplicar el sistema de coordenadas del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Aplicar el sistema de coordenadas del eje extendido
    * @param [in]  applyAxisId Número del eje extendido; bit0-bit3 corresponden a los números de eje extendido 1-4; por ejemplo, para aplicar los ejes extendidos 1 y 3, sería 0b 0000 0101, es decir, 5
    * @param [in]  axisCoordNum Número del sistema de coordenadas del eje extendido
    * @param [in]  coord Valor del sistema de coordenadas
    * @param [in]  calibFlag Indicador de calibración 0-no, 1-sí
    * @return Código de error
    */
    int ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Establecer la pose del punto de referencia de calibración en el sistema de coordenadas del extremo del posicionador
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Establecer la pose del punto de referencia de calibración en el sistema de coordenadas del extremo del posicionador
    * @param [in] pos Valor de la pose
    * @return Código de error
    */
    int SetRefPointInExAxisEnd(DescPose pos);

Configuración del punto de referencia del sistema de coordenadas del posicionador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Configuración del punto de referencia del sistema de coordenadas del posicionador
    * @param [in]  pointNum Número de punto [1-4]
    * @return Código de error
    */
    int PositionorSetRefPoint(int pointNum);

Cálculo del sistema de coordenadas del posicionador - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Cálculo del sistema de coordenadas del posicionador - método de cuatro puntos
    * @param [out] coord Valor del sistema de coordenadas
    * @return Código de error
    */
    int PositionorComputeECoordSys(DescPose& coord);

Obtener el sistema de coordenadas del eje extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el sistema de coordenadas del eje extendido
    * @param [out] coord Sistema de coordenadas del eje extendido
    * @return Código de error
    */
    int ExtAxisGetCoord(ref DescPose coord);

Ejemplo de código de calibración del sistema de coordenadas del eje extendido
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void button66_Click(object sender, EventArgs e)
    {
        int rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5,1);
        Console.WriteLine("ExtDevSetUDPComParam rtn is " + rtn);
        string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        rtn = robot.ExtDevGetUDPComParam(ref ip, ref port, ref period, ref lossPkgTime, ref lossPkgNum, ref disconnectTime, ref reconnectEnable, ref reconnectPeriod, ref reconnectNum);
        string param = "\nip " + ip + "\nport " + port.ToString() + "\nperiod  " + period.ToString() + "\nlossPkgTime " + lossPkgTime.ToString() + "\nlossPkgNum  " + lossPkgNum.ToString() + "\ndisConntime  " + disconnectTime.ToString() + "\nreconnecable  " + reconnectEnable.ToString() + "\nreconnperiod  " + reconnectPeriod.ToString() + "\nreconnnun  " + reconnectNum.ToString();
        Console.WriteLine("ExtDevGetUDPComParam rtn is " + rtn + param);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.ExtAxisSetHoming(1, 0, 10, 2);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming rtnn is  " + rtn);

        Thread.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        Console.WriteLine("SetRobotPosToAxis rtn is " + rtn);
        rtn = robot.SetAxisDHParaConfig(1, 128.5f, 206.4f, 0, 0, 0, 0, 0, 0);
        Console.WriteLine("SetAxisDHParaConfig rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);

        DescPose toolCoord = new DescPose(0, 0, 210, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);

        JointPos jSafe = new JointPos(115.193f, -96.149f, 92.489f, -87.068f, -89.15f, -83.488f);
        JointPos j1 = new JointPos(117.559f, -92.624f, 100.329f, -96.909f, -94.057f, -83.488f);
        JointPos j2 = new JointPos(112.239f, -90.096f, 99.282f, -95.909f, -89.824f, -83.488f);
        JointPos j3 = new JointPos(110.839f, -83.473f, 93.166f, -89.22f, -90.499f, -83.487f);
        JointPos j4 = new JointPos(107.935f, -83.572f, 95.424f, -92.873f, -87.933f, -83.488f);

        DescPose descSafe = new DescPose();
        DescPose desc1 = new DescPose();
        DescPose desc2 = new DescPose();
        DescPose desc3 = new DescPose();
        DescPose desc4 = new DescPose();
        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.GetForwardKin( jSafe,  ref descSafe);
        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        Thread.Sleep(2000);

        robot.GetForwardKin( j1, ref desc1);
        robot.MoveJ( j1,  desc1, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        Thread.Sleep(2000);

        DescPose actualTCPPos = new DescPose();
        robot.GetActualTCPPose(0, ref actualTCPPos);
        robot.SetRefPointInExAxisEnd(actualTCPPos);
        rtn = robot.PositionorSetRefPoint(1);
        Console.WriteLine("PositionorSetRefPoint 1 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin( j2, ref desc2);
        rtn = robot.MoveJ( j2,  desc2, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.PositionorSetRefPoint(2);
        Console.WriteLine("PositionorSetRefPoint 2 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin( j3, ref desc3);
        robot.MoveJ( j3,  desc3, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.PositionorSetRefPoint(3);
        Console.WriteLine("PositionorSetRefPoint 3 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin(j4, ref desc4);
        robot.MoveJ(j4, desc4, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(4);
        Console.WriteLine("PositionorSetRefPoint 4 rtn is " + rtn);
        Thread.Sleep(2000);

        DescPose axisCoord = new DescPose();
        robot.PositionorComputeECoordSys(ref axisCoord);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        Console.WriteLine("PositionorComputeECoordSys rtn is {0} {1} {2} {3} {4} {5}", axisCoord.tran.x, axisCoord.tran.y, axisCoord.tran.z, axisCoord.rpy.rx, axisCoord.rpy.ry, axisCoord.rpy.rz);
        rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);
        Console.WriteLine("ExtAxisActiveECoordSys rtn is " + rtn);
    }

Movimiento del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: C#
    :linenos:

    /**
    * @brief Movimiento del eje extendido UDP
    * @param [in] pos Posición objetivo
    * @param [in] ovl Porcentaje de velocidad
    * @param [in] blend Parámetro de suavizado (mm o ms)
    * @return Código de error
    */
    int ExtAxisMove(ExaxisPos pos, double ovl, double blend=-1);

Ejemplo de código de movimiento del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    private void button66_Click(object sender, EventArgs e)
    {
        ExaxisPos axisPos;
        axisPos.ePos[0] = 20;
        axisPos.ePos[1] = 0;
        axisPos.ePos[2] = 0;
        axisPos.ePos[3] = 0;
        robot.ExtAxisMove(axisPos, 50);
    }

Movimiento sincronizado del eje extendido UDP con el movimiento articular del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
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
    int ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos);

Ejemplo de código
++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveJ_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

        //1.Calibrar y aplicar el sistema de coordenadas de herramienta del robot; puede utilizar el método de cuatro puntos o de seis puntos para la calibración y aplicación del sistema de coordenadas de herramienta. Las interfaces relacionadas con la calibración del sistema de coordenadas de herramienta son las siguientes:
        //    int SetToolPoint(int point_num);  //Establecer el punto de referencia de la herramienta - método de seis puntos
        //    int ComputeTool(ref DescPose tcp_pose);  //Calcular el sistema de coordenadas de herramienta
        //    int SetTcp4RefPoint(int point_num);    //Establecer el punto de referencia de la herramienta - método de cuatro puntos
        //    int ComputeTcp4(ref DescPose tcp_pose);   //Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  //Establecer el sistema de coordenadas de herramienta a aplicar
        //    int SetToolList(int id, DescPose coord, int type, int install);   //Establecer la lista de sistemas de coordenadas de herramienta a aplicar

        //2.Configurar los parámetros de comunicación UDP y cargar la comunicación UDP
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3.Configurar los parámetros del eje extendido, incluyendo el tipo de eje extendido, los parámetros del accionamiento del eje extendido y los parámetros DH del eje extendido
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posicionador de un solo eje y parámetros DH
        robot.SetRobotPosToAxis(1);  //Posición de instalación del eje extendido
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parámetros del accionamiento servo; este ejemplo es un posicionador de un solo eje, por lo que solo es necesario configurar los parámetros de un accionamiento; si elige un tipo de eje extendido con varios ejes, deberá configurar los parámetros del accionamiento para cada eje

        //4.Establecer la habilitación y el retorno a cero de los ejes seleccionados
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5.Realizar la calibración y aplicación del sistema de coordenadas del eje extendido (nota: las interfaces de calibración del posicionador y de la guía lineal son diferentes; las siguientes son las interfaces de calibración del posicionador)
        DescPose pos = new DescPose(/* Introduzca las coordenadas de su punto de calibración */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /*Debe calibrar el eje extendido mediante cuatro puntos en posiciones diferentes, por lo que es necesario llamar a esta interfaz 4 veces para completar la calibración */
        DescPose coord = new DescPose( );
        robot.PositionorComputeECoordSys(ref coord); //Calcular el resultado de la calibración del eje extendido
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  //Aplicar el resultado de la calibración al sistema de coordenadas del eje extendido

        //6.Calibrar el sistema de coordenadas de pieza sobre el eje extendido; necesitará las siguientes interfaces
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7.Registrar el punto inicial de su movimiento articular sincronizado
        DescPose startdescPose = new DescPose(/*Introduzca sus coordenadas*/);
        JointPos startjointPos = new JointPos(/*Introduzca sus coordenadas*/);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del punto inicial de su eje extendido */);

        //8.Registrar las coordenadas del punto final de su movimiento articular sincronizado
        DescPose enddescPose = new DescPose(/*Introduzca sus coordenadas*/);
        JointPos endjointPos = new JointPos(/*Introduzca sus coordenadas*/);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del punto final de su eje extendido */);

        //9.Escribir el programa de movimiento sincronizado
        //Moverse al punto inicial, suponiendo que el sistema de coordenadas de herramienta y el sistema de coordenadas de pieza aplicados son ambos el 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        //Iniciar el movimiento sincronizado
        robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
    }

Movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
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
    int ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Ejemplo de código
++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveL_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

    //1.Calibrar y aplicar el sistema de coordenadas de herramienta del robot; puede utilizar el método de cuatro puntos o de seis puntos para la calibración y aplicación del sistema de coordenadas de herramienta. Las interfaces relacionadas con la calibración del sistema de coordenadas de herramienta son las siguientes:
        //    int SetToolPoint(int point_num);  //Establecer el punto de referencia de la herramienta - método de seis puntos
        //    int ComputeTool(ref DescPose tcp_pose);  //Calcular el sistema de coordenadas de herramienta
        //    int SetTcp4RefPoint(int point_num);    //Establecer el punto de referencia de la herramienta - método de cuatro puntos
        //    int ComputeTcp4(ref DescPose tcp_pose);   //Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  //Establecer el sistema de coordenadas de herramienta a aplicar
        //    int SetToolList(int id, DescPose coord, int type, int install);   //Establecer la lista de sistemas de coordenadas de herramienta a aplicar

        //2.Configurar los parámetros de comunicación UDP y cargar la comunicación UDP
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3.Configurar los parámetros del eje extendido, incluyendo el tipo de eje extendido, los parámetros del accionamiento del eje extendido y los parámetros DH del eje extendido
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posicionador de un solo eje y parámetros DH
        robot.SetRobotPosToAxis(1);  //Posición de instalación del eje extendido
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parámetros del accionamiento servo; este ejemplo es un posicionador de un solo eje, por lo que solo es necesario configurar los parámetros de un accionamiento; si elige un tipo de eje extendido con varios ejes, deberá configurar los parámetros del accionamiento para cada eje

        //4.Establecer la habilitación y el retorno a cero de los ejes seleccionados
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5.Realizar la calibración y aplicación del sistema de coordenadas del eje extendido
        DescPose pos = new DescPose(/* Introduzca las coordenadas de su punto de calibración */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /*Debe calibrar el eje extendido mediante cuatro puntos en posiciones diferentes, por lo que es necesario llamar a esta interfaz 4 veces para completar la calibración */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(ref coord); //Calcular el resultado de la calibración del eje extendido
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  //Aplicar el resultado de la calibración al sistema de coordenadas del eje extendido

        //6.Calibrar el sistema de coordenadas de pieza sobre el eje extendido; necesitará las siguientes interfaces
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7.Registrar el punto inicial de su movimiento lineal sincronizado
        DescPose startdescPose = new DescPose(/*Introduzca sus coordenadas*/);
        JointPos startjointPos = new JointPos(/*Introduzca sus coordenadas*/);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del punto inicial de su eje extendido */);

        //8.Registrar las coordenadas del punto final de su movimiento lineal sincronizado
        DescPose enddescPose = new DescPose(/*Introduzca sus coordenadas*/);
        JointPos endjointPos = new JointPos(/*Introduzca sus coordenadas*/);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del punto final de su eje extendido */);

        //9.Escribir el programa de movimiento sincronizado
        //Moverse al punto inicial, suponiendo que el sistema de coordenadas de herramienta y el sistema de coordenadas de pieza aplicados son ambos el 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        //Iniciar el movimiento sincronizado
        robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
    }
    
Movimiento sincronizado del eje extendido UDP con el movimiento en arco del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
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
    int ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, float ovl, float blendR);
    
Ejemplo de código
++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveC_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

    //1.Calibrar y aplicar el sistema de coordenadas de herramienta del robot; puede utilizar el método de cuatro puntos o de seis puntos para la calibración y aplicación del sistema de coordenadas de herramienta. Las interfaces relacionadas con la calibración del sistema de coordenadas de herramienta son las siguientes:
        //    int SetToolPoint(int point_num);  //Establecer el punto de referencia de la herramienta - método de seis puntos
        //    int ComputeTool(ref DescPose tcp_pose);  //Calcular el sistema de coordenadas de herramienta
        //    int SetTcp4RefPoint(int point_num);    //Establecer el punto de referencia de la herramienta - método de cuatro puntos
        //    int ComputeTcp4(ref DescPose tcp_pose);   //Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  //Establecer el sistema de coordenadas de herramienta a aplicar
        //    int SetToolList(int id, DescPose coord, int type, int install);   //Establecer la lista de sistemas de coordenadas de herramienta a aplicar

        //2.Configurar los parámetros de comunicación UDP y cargar la comunicación UDP
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3.Configurar los parámetros del eje extendido, incluyendo el tipo de eje extendido, los parámetros del accionamiento del eje extendido y los parámetros DH del eje extendido
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posicionador de un solo eje y parámetros DH
        robot.SetRobotPosToAxis(1);  //Posición de instalación del eje extendido
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parámetros del accionamiento servo; este ejemplo es un posicionador de un solo eje, por lo que solo es necesario configurar los parámetros de un accionamiento; si elige un tipo de eje extendido con varios ejes, deberá configurar los parámetros del accionamiento para cada eje

        //4.Establecer la habilitación y el retorno a cero de los ejes seleccionados
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5.Realizar la calibración y aplicación del sistema de coordenadas del eje extendido
        DescPose pos = new DescPose(/* Introduzca las coordenadas de su punto de calibración */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /*Debe calibrar el eje extendido mediante cuatro puntos en posiciones diferentes, por lo que es necesario llamar a esta interfaz 4 veces para completar la calibración */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(ref coord); //Calcular el resultado de la calibración del eje extendido
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  //Aplicar el resultado de la calibración al sistema de coordenadas del eje extendido

        //6.Calibrar el sistema de coordenadas de pieza sobre el eje extendido; necesitará las siguientes interfaces
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7.Registrar el punto inicial de su movimiento en arco sincronizado
        DescPose startdescPose = new DescPose(/*Introduzca sus coordenadas*/);
        JointPos startjointPos = new JointPos(/*Introduzca sus coordenadas*/);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del punto inicial de su eje extendido */);

        //8.Registrar las coordenadas del punto final de su movimiento en arco sincronizado
        DescPose enddescPose = new DescPose(/*Introduzca sus coordenadas*/);
        JointPos endjointPos = new JointPos(/*Introduzca sus coordenadas*/);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del punto final de su eje extendido */);

        //8.Registrar las coordenadas del punto intermedio de su movimiento en arco sincronizado
        DescPose middescPose = new DescPose(/*Introduzca sus coordenadas*/);
        JointPos midjointPos = new JointPos(/*Introduzca sus coordenadas*/);
        ExaxisPos midexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del eje extendido en el punto intermedio del arco del robot */);

        //9.Escribir el programa de movimiento sincronizado
        //Moverse al punto inicial, suponiendo que el sistema de coordenadas de herramienta y el sistema de coordenadas de pieza aplicados son ambos el 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        //Iniciar el movimiento sincronizado
        robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
    }

Establecer DO extendida
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Establecer DO extendida
    * @param [in] DONum Número de DO
    * @param [in] bOpen Interruptor true-activado; false-desactivado
    * @param [in] smooth Si se suaviza
    * @param [in] block Si es bloqueante
    * @return Código de error
    */
    int SetAuxDO(int DONum, bool bOpen, bool smooth, bool block);
        
Establecer AO extendida
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Establecer AO extendida
    * @param [in] AONum Número de AO 
    * @param [in] value Valor analógico [0-4095]
    * @param [in] block Si es bloqueante
    * @return Código de error
    */
    int SetAuxAO(int AONum, double value, bool block);
            
Establecer el tiempo de filtro de entrada DI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Establecer el tiempo de filtro de entrada DI extendida
    * @param [in] filterTime Tiempo de filtro (ms)
    * @return Código de error
    */
    int SetAuxDIFilterTime(int filterTime);

Establecer el tiempo de filtro de entrada AI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Establecer el tiempo de filtro de entrada AI extendida
    * @param [in] filterTime Tiempo de filtro (ms)
    * @return Código de error
    */
    int SetAuxAIFilterTime(int filterTime);

Esperar la entrada DI extendida
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Esperar la entrada DI extendida
    * @param [in] DINum Número de DI
    * @param [in] bOpen Interruptor 0-desactivado; 1-activado
    * @param [in] time Tiempo máximo de espera (ms)
    * @param [in] errorAlarm Si se continúa el movimiento
    * @return Código de error
    */
    int WaitAuxDI(int DINum, bool bOpen, int time, bool errorAlarm);
    
Esperar la entrada AI extendida
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
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
    int WaitAuxAI(int AINum, int sign, int value, int time, bool errorAlarm);
        
Obtener el valor de DI extendida
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Obtener el valor de DI extendida
    * @param [in] DINum Número de DI
    * @param [in] isNoBlock Si es bloqueante
    * @param [out] isOpen 0-desactivado; 1-activado
    * @return Código de error
    */
    int GetAuxDI(int DINum, bool isNoBlock, bool& isOpen);
            
Obtener el valor de AI extendida
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Obtener el valor de AI extendida
    * @param [in] AINum Número de AI
    * @param [in] isNoBlock Si es bloqueante
    * @param [in] value Valor de entrada
    * @return Código de error
    */
    int GetAuxAI(int AINum, bool isNoBlock, int& value);

Ejemplo de código de IO extendida
++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnAODO_Click(object sender, EventArgs e)
    {
        int rtn;
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, true, false, true);
            Thread.Sleep(100);
        }
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, false, false, true);
            Thread.Sleep(100);
        }

        for (int i = 0; i < 409; i++)
        {
            robot.SetAuxAO(0, i * 10, true);
            robot.SetAuxAO(1, 4095 - i * 10, true);
            robot.SetAuxAO(2, i * 10, true);
            robot.SetAuxAO(3, 4095 - i * 10, true);
            Thread.Sleep(10);
        }

        robot.SetAuxDIFilterTime(10);
        robot.SetAuxAIFilterTime(0, 10);

        for (int i = 0; i < 20; i++)
        {
            bool curValue = false;
            rtn = robot.GetAuxDI(i, false, ref curValue);
            Console.WriteLine("DI" + i + "   " + curValue);
        }
        int curValueAI = -1;
        for (int i = 0; i < 4; i++)
        {
            rtn = robot.GetAuxAI(i, true, ref curValueAI);
        }

        robot.WaitAuxDI(1, false, 1000, false);
        robot.WaitAuxAI(1, 1, 132, 1000, false);
    }

Habilitación del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Habilitación del dispositivo móvil
    * @param enable false-deshabilitar; true-habilitar
    * @return Código de error
    */
    int TractorEnable(bool enable);

Parada del movimiento del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Parada del movimiento del dispositivo móvil
    * @return Código de error
    */
    int TractorStop();

Retorno a cero del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Retorno a cero del dispositivo móvil
    * @return Código de error
    */
    int  TractorHoming();

Movimiento lineal del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Movimiento lineal del dispositivo móvil
    * @param distance Distancia del movimiento lineal (mm)
    * @param vel Porcentaje de velocidad del movimiento lineal (0-100)
    * @return Código de error
    */
    int TractorMoveL(double distance, double vel);

Movimiento en arco del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Movimiento en arco del dispositivo móvil
    * @param radio Radio del movimiento en arco (mm)
    * @param angle Ángulo del movimiento en arco (°)
    * @param vel Porcentaje de velocidad del movimiento lineal (0-100)
    * @return Código de error
    */
    int TractorMoveC(double radio, double angle, double vel);

Ejemplo de código
++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    private void button6_Click(object sender, EventArgs e)
    {
        int rtn;
        robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10,1);
        robot.ExtDevLoadUDPDriver();
        rtn = robot.ExtAxisServoOn(1, 1);
        rtn = robot.ExtAxisServoOn(2, 1);
        Thread.Sleep(2000);
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Thread.Sleep(4000);
        robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280f, 16384, 200, 0, 0, 0);
        robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280f, 16384, 200, 0, 0, 0);
        robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);
        robot.TractorEnable(false);
        Thread.Sleep(2000);
        robot.TractorEnable(true);
        Thread.Sleep(2000);
        robot.TractorHoming();
        Thread.Sleep(2000);
        robot.TractorMoveL(100, 2);
        Thread.Sleep(5000);
        robot.TractorStop();
        robot.TractorMoveL(-100, 20);
        Thread.Sleep(5000);
        robot.TractorMoveC(300, 90, 20);
        Thread.Sleep(10000);
        robot.TractorMoveC(300, -90, 20);
        Thread.Sleep(1000);
        robot.TractorStop();    
    }

Establecer la estrategia de movimiento sincronizado entre el eje extendido y el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:


    /**
    * @brief Establecer la estrategia de movimiento sincronizado entre el eje extendido y el robot
    * @param strategy Estrategia; 0-el robot como referencia; 1-el eje extendido sincronizado con el robot
    * @return Código de error
    */
    int SetExAxisRobotPlan(int strategy)

Ejemplo de código de configuración de la estrategia de movimiento sincronizado entre el eje extendido y el robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:


    private void button94_Click(object sender, EventArgs e)
    {
        JointPos joint_pos1 = new JointPos(-22.016, -49.217, 124.714, -161.100, -85.108, -0.333);
        JointPos joint_pos2 = new JointPos(-21.083, -46.613, 110.079, -147.796, -80.757, -0.330);
        JointPos joint_pos3 = new JointPos(-25.572, -60.090, 135.397, -163.889, -82.489, -0.345);
        DescPose desc_pos1 = new DescPose(2.637, -0.001, 30.673, 178.786, -4.134, 68.326);
        DescPose desc_pos2 = new DescPose(213.812, -1.440, 47.311, 177.410, 0.166, 68.946);
        DescPose desc_pos3 = new DescPose(444.342, -12.723, 82.470, -177.701, -1.325, 65.151);   
        ExaxisPos epos1 = new ExaxisPos(0.001, 0.000, 0.000, 0.000);
        ExaxisPos epos2 = new ExaxisPos(299.977, 0.000, 0.000, 0.000);
        ExaxisPos epos3 = new ExaxisPos(399.969, 0.000, 0.000, 0.000);      
        DescPose offset_pos = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.SetExAxisRobotPlan(0);
        Console.WriteLine($"SetExAxisRobotPlan rtn is {rtn}");
        Thread.Sleep(1000);
        rtn = robot.ExtAxisSyncMoveL(joint_pos1, desc_pos1, 1, 0, 100, 100, 100, -1, epos1, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 1 rtn is {rtn}");

        rtn = robot.ExtAxisSyncMoveL(joint_pos2, desc_pos2, 1, 0, 100, 100, 100, -1, epos2, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 2 rtn is {rtn}");
        rtn = robot.ExtAxisSyncMoveL(joint_pos3, desc_pos3, 1, 0, 100, 100, 100, -1, epos3, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 3 rtn is {rtn}");
        Thread.Sleep(8000);
    }

Configuración del tiempo de finalización de posicionamiento del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Configuración del tiempo de finalización de posicionamiento del eje extendido UDP
    * @param [in] time Tiempo de finalización del posicionamiento [ms]
    * @return Código de error
    */
    public int SetExAxisCmdDoneTime(double time)