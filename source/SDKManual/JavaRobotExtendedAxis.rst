Eje extendido
=================

.. toctree:: 
    :maxdepth: 5

Establecer los parámetros del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer los parámetros del eje extendido 485
    * @param [in] servoId ID del servoaccionamiento, rango [1-16], corresponde al ID de esclavo
    * @param [in] param Parámetros del eje extendido 485
    * @return Código de error 
    */
    int AuxServoSetParam(int servoId, Axis485Param param)
    
Obtener los parámetros del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener los parámetros de configuración del eje extendido 485
    * @param [in] servoId ID del servoaccionamiento, rango [1-16], corresponde al ID de esclavo
    * @param [out] param Parámetros del eje extendido 485
    * @return Código de error 
    */
    int AuxServoGetParam(int servoId, Axis485Param param);

Establecer la habilitación/deshabilitación del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer la habilitación/deshabilitación del eje extendido 485
    * @param [in] servoId ID del servoaccionamiento, rango [1-16], corresponde al ID de esclavo
    * @param [in] status Estado de habilitación, 0-deshabilitar, 1-habilitar
    * @return Código de error 
    */
    int AuxServoEnable(int servoId, int status);
        
Establecer el modo de control del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el modo de control del eje extendido 485
    * @param [in] servoId ID del servoaccionamiento, rango [1-16], corresponde al ID de esclavo
    * @param [in] mode Modo de control, 0-modo de posición, 1-modo de velocidad
    * @return Código de error 
    */
    int AuxServoSetControlMode(int servoId, int mode);

Establecer la posición objetivo del eje extendido 485 (modo de posición)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer la posición objetivo del eje extendido 485 (modo de posición)
    * @param [in] servoId ID del servoaccionamiento, rango [1-16], corresponde al ID de esclavo
    * @param [in] pos Posición objetivo, mm o °
    * @param [in] speed Velocidad objetivo, mm/s o °/s
    * @param [in] acc Porcentaje de aceleración [0-100]
    * @return Código de error 
    */
    int AuxServoSetTargetPos(int servoId, double pos, double speed, double acc);
    
Establecer el par objetivo del eje extendido 485 (modo de par) - aún no disponible
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el par objetivo del eje extendido 485 (modo de par) - aún no disponible
    * @param [in] servoId ID del servoaccionamiento, rango [1-16], corresponde al ID de esclavo
    * @param [in] torque Par objetivo, Nm
    * @return Código de error 
    */
    int AuxServoSetTargetTorque(int servoId, double torque);
        
Establecer el retorno a cero del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el retorno a cero del eje extendido 485
    * @param [in] servoId ID del servoaccionamiento, rango [1-16], corresponde al ID de esclavo
    * @param [in] mode Modo de retorno a cero, 1-retorno a cero en la posición actual; 2-retorno a cero en el límite negativo; 3-retorno a cero en el límite positivo
    * @param [in] searchVel Velocidad de retorno a cero, mm/s o °/s
    * @param [in] latchVel Velocidad de enganche, mm/s o °/s
    * @param [in] acc Porcentaje de aceleración [0-100]
    * @return Código de error 
    */
    int AuxServoHoming(int servoId, int mode, double searchVel, double latchVel);

Borrar la información de error del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Borrar la información de error del eje extendido 485
    * @param [in] servoId ID del servoaccionamiento, rango [1-16], corresponde al ID de esclavo
    * @return Código de error 
    */
    int AuxServoClearError(int servoId);

Obtener el estado del servo del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener el estado del servo del eje extendido 485
    * @param [in] servoId ID del servoaccionamiento, rango [1-16], corresponde al ID de esclavo
    * @param [in] servoErrCode Código de fallo del servoaccionamiento
    * @param [in] servoState Estado del servoaccionamiento bit0:0-no habilitado；1-habilitado;  bit1:0-sin movimiento；1-en movimiento;  bit4 0-posicionamiento no completado；1-posicionamiento completado；  bit5：0-sin retorno a cero；1-retorno a cero completado
    * @param [in] servoPos Posición actual del servo mm o °
    * @param [in] servoSpeed Velocidad actual del servo mm/s o °/s
    * @param [in] servoTorque Par actual del servo Nm
    * @return Código de error 
    */
    int AuxServoGetStatus(int servoId, int[] servoErrCode, int[] servoState, double[] servoPos, double[] servoSpeed, double[] servoTorque)

Establecer la velocidad objetivo del eje extendido 485 (modo de velocidad)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer la velocidad objetivo del eje extendido 485 (modo de velocidad)
    * @param [in] servoId ID del servoaccionamiento, rango [1-16], corresponde al ID de esclavo
    * @param [in] speed Velocidad objetivo, mm/s o °/s
    * @param [in] acc Porcentaje de aceleración [0-100]
    * @return Código de error 
    */
    int AuxServoSetTargetSpeed(int servoId, double speed, double acc);

Establecer el número de eje de los datos del eje extendido 485 en la retroalimentación de estado
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer el número de eje de los datos del eje extendido 485 en la retroalimentación de estado
    * @param [in] servoId ID del servoaccionamiento, rango [1-16], corresponde al ID de esclavo
    * @return Código de error 
    */
    int AuxServosetStatusID(int servoId);

Establecer la aceleración y desaceleración de movimiento del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer la aceleración y desaceleración de movimiento del eje extendido 485
    * @param [in] acc Aceleración de movimiento del eje extendido 485
    * @param [in] dec Desaceleración de movimiento del eje extendido 485
    * @return Código de error 
    */
    int AuxServoSetAcc(double acc, double dec)

Establecer la aceleración y desaceleración de parada de emergencia del eje extendido 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Establecer la aceleración y desaceleración de parada de emergencia del eje extendido 485
    * @param [in] acc Aceleración de parada de emergencia del eje extendido 485
    * @param [in] dec Desaceleración de parada de emergencia del eje extendido 485
    * @return Código de error 
    */
    int AuxServoSetEmergencyStopAcc(double acc, double dec)

Obtener la aceleración y desaceleración de movimiento del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener la aceleración y desaceleración de movimiento del eje extendido 485
    * @return List[0]:código de error; List[1]:aceleración de movimiento del eje extendido 485; List[2]:desaceleración de movimiento del eje extendido 485 
    */
    List<Number> AuxServoGetAcc()

Obtener la aceleración y desaceleración de parada de emergencia del eje extendido 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener la aceleración y desaceleración de parada de emergencia del eje extendido 485
    * @return List[0]:código de error; List[1]:aceleración de parada de emergencia del eje extendido 485; List[2]:desaceleración de parada de emergencia del eje extendido 485
    */
    List<Number> AuxServoGetEmergencyStopAcc()

Ejemplo de código de control del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int Test485Auxservo(Robot robot)
    {
        Axis485Param ax=new Axis485Param(1, 1, 1, 131072, 15.45);
        int retval = robot.AuxServoSetParam(1, ax);

        Axis485Param ax2=new Axis485Param();
        retval = robot.AuxServoGetParam(1, ax2);

        ax.servoCompany=10;
        ax.servoModel=11;
        ax.servoSoftVersion=12;
        ax.servoResolution=13;
        ax.axisMechTransRatio=14;

        retval = robot.AuxServoSetParam(1, ax);

        retval = robot.AuxServoGetParam(1,ax2);

        ax.servoCompany=1;
        ax.servoModel=1;
        ax.servoSoftVersion=1;
        ax.servoResolution=131072;
        ax.axisMechTransRatio=36;

        retval = robot.AuxServoSetParam(1, ax);
        robot.Sleep(3000);

        robot.AuxServoSetAcc(3000, 3000);
        robot.AuxServoSetEmergencyStopAcc(5000, 5000);
        robot.Sleep(1000);
        double emagacc = 0, acc = 0;
        double emagdec = 0, dec = 0;

        List<Number> aux=new ArrayList<>();

        aux=robot.AuxServoGetEmergencyStopAcc();
        aux=robot.AuxServoGetAcc();

        robot.AuxServoSetControlMode(1, 0);
        robot.Sleep(2000);

        retval = robot.AuxServoEnable(1, 0);
        robot.Sleep(1000);
        int[] servoerrcode =new int[]{0};
        int[] servoErrCode=new int[]{0};
        int[] servoState=new int[]{0};
        double[] servoPos=new double[]{0};
        double[] servoSpeed=new double[]{0};
        double[] servoTorque=new double[]{0};
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
        robot.Sleep(1000);;

        retval = robot.AuxServoEnable(1, 1);
        robot.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
        robot.Sleep(1000);

        retval = robot.AuxServoHoming(1, 1, 5, 1,100);
        robot.Sleep(3000);

        retval = robot.AuxServoSetTargetPos(1, 200, 30,100);
        robot.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
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
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Configuración de los parámetros de comunicación del eje extendido UDP
    * @param [in] param Parámetros de comunicación
    * @return Código de error
    */
    int ExtDevSetUDPComParam(UDPComParam param);     

Obtener la configuración de los parámetros de comunicación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener los parámetros de comunicación del eje extendido UDP
    * @param [out] ip Dirección IP del PLC
    * @param [out] port	Número de puerto
    * @param [out] period	Período de comunicación (ms, valor predeterminado 2, no modificar este parámetro)
    * @param [out] lossPkgTime	Tiempo de detección de pérdida de paquetes (ms)
    * @param [out] lossPkgNum	Número de pérdidas de paquetes
    * @param [out] disconnectTime	Duración de confirmación de desconexión de comunicación
    * @param [out] reconnectEnable	Habilitación de reconexión automática tras desconexión de comunicación 0-no habilitar 1-habilitar
    * @param [out] reconnectPeriod	Intervalo del período de reconexión (ms)
    * @param [out] reconnectNum	Número de reconexiones
    * @param [out] selfConnect Si se reconecta automáticamente tras reiniciar la caja de control; 0-no reconectar; 1-reconectar
    * @return Código de error
    */
    public int ExtDevGetUDPComParam(ref string ip, ref int port, ref int period, ref int lossPkgTime, ref int lossPkgNum, ref int disconnectTime, ref int reconnectEnable, ref int reconnectPeriod, ref int reconnectNum, ref int selfConnect)    

Cargar la comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Cargar la comunicación UDP
    * @return Código de error
    */
    int ExtDevLoadUDPDriver();

Descargar la comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Descargar la comunicación UDP
    * @return Código de error
    */
    int ExtDevUnloadUDPDriver();

Restablecer la conexión tras una desconexión anómala de la comunicación del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Restablecer la conexión tras una desconexión anómala de la comunicación del eje extendido UDP
    * @return Código de error
    */
    int ExtDevUDPClientComReset();

Cerrar la comunicación tras una desconexión anómala de la comunicación del eje extendido UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Cerrar la comunicación tras una desconexión anómala de la comunicación del eje extendido UDP
    * @return Código de error
    */
    int ExtDevUDPClientComClose();

Configuración de los parámetros del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
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
    * @param [in] axisCompany Fabricante del accionamiento 1-Huichuan; 2-Inovance; 3-Panasonic
    * @param [in] axisModel Modelo del accionamiento 1-Huichuan-SV-XD3EA040L-E, 2-Huichuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    * @param [in] axisEncType Tipo de codificador 0-incremental; 1-absoluto
    * @return Código de error
    */
    int ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, int encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Obtención de los parámetros del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtención de los parámetros del eje extendido UDP
    * @param  axisID Número de eje extendido [1-4]
    * @param  params Arreglo de parámetros de salida, longitud 12, en orden:
    *               [0] axisType Tipo de eje extendido 0-traslación; 1-rotación
    *               [1] axisDirection Dirección del eje extendido 0-positiva; 1-negativa
    *               [2] axisMax Posición máxima del eje extendido mm
    *               [3] axisMin Posición mínima del eje extendido mm
    *               [4] axisVel Velocidad mm/s
    *               [5] axisAcc Aceleración mm/s2
    *               [6] axisLead Paso mm
    *               [7] encResolution Resolución del codificador
    *               [8] axisOffect Desplazamiento del eje extendido en el punto inicial de la soldadura
    *               [9] axisCompany Fabricante del accionamiento 1-Huichuan; 2-Inovance; 3-Panasonic
    *               [10] axisModel Modelo del accionamiento
    *               [11] axisEncType Tipo de codificador 0-incremental; 1-absoluto
    * @return Código de error
    */
    public int ExtAxisGetParamConfig(int axisID, Object[] params)

Establecer la posición de instalación del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la posición de instalación del eje extendido
    * @param [in] installType 0-robot instalado sobre el eje externo, 1-robot instalado fuera del eje externo
    * @return Código de error
    */
    int SetRobotPosToAxis(int installType);

Establecer la configuración de los parámetros DH del sistema del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la configuración de los parámetros DH del sistema del eje extendido
    * @param [in]  axisConfig Configuración del eje externo, 0-guía lineal de un solo grado de libertad, 1-posicionador tipo L de dos grados de libertad, 2-tres grados de libertad, 3-cuatro grados de libertad, 4-posicionador de un solo grado de libertad
    * @param [in]  axisDHd1 Parámetro DH d1 del eje externo mm
    * @param [in]  axisDHd2 Parámetro DH d2 del eje externo mm
    * @param [in]  axisDHd3 Parámetro DH d3 del eje externo mm
    * @param [in]  axisDHd4 Parámetro DH d4 del eje externo mm
    * @param [in]  axisDHa1 Parámetro DH a1 del eje externo mm
    * @param [in]  axisDHa2 Parámetro DH a2 del eje externo mm
    * @param [in]  axisDHa3 Parámetro DH a3 del eje externo mm
    * @param [in]  axisDHa4 Parámetro DH a4 del eje externo mm
    * @return Código de error
    */
    int SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

Habilitación del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Habilitación del eje extendido UDP
    * @param [in] axisID Número de eje [1-4]
    * @param [in] status 0-deshabilitar; 1-habilitar
    * @return Código de error
    */
    int ExtAxisServoOn(int axisID, int status);

Retorno a cero del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Retorno a cero del eje extendido UDP
    * @param [in] axisID Número de eje [1-4]
    * @param [in] mode Modo de retorno a cero 0-retorno a cero en la posición actual, 1-retorno a cero en el límite negativo, 2-retorno a cero en el límite positivo
    * @param [in] searchVel Velocidad de búsqueda de cero (mm/s)
    * @param [in] latchVel Velocidad de enganche de búsqueda de cero (mm/s)
    * @return Código de error
    */
    int ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

Inicio del jog del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicio del jog del eje extendido UDP
    * @param [in] axisID Número de eje [1-4]
    * @param [in] direction Dirección de giro 0-inversa; 1-positiva
    * @param [in] vel Velocidad (mm/s)
    * @param [in] acc (Aceleración mm/s2)
    * @param [in] maxDistance Distancia máxima de jog
    * @return Código de error
    */
    int ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);
    
Parada del jog del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Parada del jog del eje extendido UDP
    * @param [in] axisID Número de eje [1-4]
    * @return Código de error
    */
    int ExtAxisStopJog(int axisID);

Ejemplo de código de configuración y jog del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestUDPAxis(Robot robot) {
        int rtn = -1;
        
        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
        rtn = robot.ExtDevSetUDPComParam(param);
        System.out.println("ExtDevSetUDPComParam rtn is " + rtn);
        
        UDPComParam getParam = new UDPComParam();
        rtn = robot.ExtDevGetUDPComParam(getParam);
        String paramStr = "\nip " + getParam.ip + "\nport " + getParam.port + "\nperiod " + getParam.period + 
                "\nlossPkgTime " + getParam.lossPkgTime + "\nlossPkgNum " + getParam.lossPkgNum + 
                "\ndisconnectTime " + getParam.disconnectTime + "\nreconnectEnable " + getParam.reconnectEnable + 
                "\nreconnectPeriod " + getParam.reconnectPeriod + "\nreconnectNum " + getParam.reconnectNum + 
                "\nselfConnect " + getParam.selfConnect;
        System.out.println("ExtDevGetUDPComParam rtn is " + rtn + paramStr);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        System.out.println("SetExAxisCmdDoneTime rtn is " + rtn);
        
        rtn = robot.ExtAxisServoOn(1, 1);
        System.out.println("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        System.out.println("ExtAxisServoOn axis id 2 rtn is " + rtn);
        robot.Sleep(2000);

        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        System.out.println("ExtAxisSetHoming rtn is " + rtn);

        robot.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        System.out.println("SetRobotPosToAxis rtn is " + rtn);
        
        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
        System.out.println("SetAxisDHParaConfig rtn is " + rtn);

        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
        System.out.println("ExtAxisParamConfig axis 1 rtn is " + rtn);
        
        Object[] params1 = new Object[12];
        rtn = robot.ExtAxisGetParamConfig(1, params1);
        System.out.printf("axis id 1 ExtAxisGetParamConfig : axisType %d, axisDirection %d, axisMax %.2f, axisMin %.2f, axisVel %.2f, axisAcc %.2f, axisLead %.2f, encResolution %d, axisOffect %.2f, axisCompany %d, axisModel %d, axisEncType %d\n",
                (int)params1[0], (int)params1[1], (double)params1[2], (double)params1[3], 
                (double)params1[4], (double)params1[5], (double)params1[6], (int)params1[7], 
                (double)params1[8], (int)params1[9], (int)params1[10], (int)params1[11]);
        
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);
        System.out.println("ExtAxisParamConfig axis 2 rtn is " + rtn);
        
        Object[] params2 = new Object[12];
        rtn = robot.ExtAxisGetParamConfig(2, params2);
        System.out.printf("axis id 2 ExtAxisGetParamConfig : axisType %d, axisDirection %d, axisMax %.2f, axisMin %.2f, axisVel %.2f, axisAcc %.2f, axisLead %.2f, encResolution %d, axisOffect %.2f, axisCompany %d, axisModel %d, axisEncType %d\n",
                (int)params2[0], (int)params2[1], (double)params2[2], (double)params2[3], 
                (double)params2[4], (double)params2[5], (double)params2[6], (int)params2[7], 
                (double)params2[8], (int)params2[9], (int)params2[10], (int)params2[11]);

        robot.Sleep(3000);
        
        robot.ExtAxisStartJog(1, 0, 10, 10, 30);
        robot.Sleep(1000);
        robot.ExtAxisStopJog(1);
        robot.Sleep(3000);
        robot.ExtAxisServoOn(1, 0);

        robot.Sleep(3000);
        
        robot.ExtAxisStartJog(2, 0, 10, 10, 30);
        robot.Sleep(1000);
        robot.ExtAxisStopJog(2);
        robot.Sleep(3000);
        robot.ExtAxisServoOn(2, 0);
        robot.ExtDevUnloadUDPDriver();

        return 0;
    }

Establecer el punto de referencia del sistema de coordenadas del eje extendido - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el punto de referencia del sistema de coordenadas del eje extendido - método de cuatro puntos
    * @param [in]  pointNum Número de punto [1-4]
    * @return Código de error
    */
    int ExtAxisSetRefPoint(int pointNum);

Calcular el sistema de coordenadas del eje extendido - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calcular el sistema de coordenadas del eje extendido - método de cuatro puntos
    * @param [out]  coord Valor del sistema de coordenadas
    * @return Código de error
    */
    int ExtAxisComputeECoordSys(DescPose coord);

Configuración del punto de referencia del sistema de coordenadas del posicionador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Configuración del punto de referencia del sistema de coordenadas del posicionador
    * @param [in]  pointNum Número de punto [1-4]
    * @return Código de error
    */
    int PositionorSetRefPoint(int pointNum);

Cálculo del sistema de coordenadas del posicionador - método de cuatro puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Cálculo del sistema de coordenadas del posicionador - método de cuatro puntos
    * @param [out] coord Valor del sistema de coordenadas
    * @return Código de error
    */
    int PositionorComputeECoordSys(DescPose coord);

Establecer la pose del punto de referencia de calibración en el sistema de coordenadas del extremo del posicionador
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la pose del punto de referencia de calibración en el sistema de coordenadas del extremo del posicionador
    * @param [in] pos Valor de la pose
    * @return Código de error
    */
    int SetRefPointInExAxisEnd(DescPose pos);

Aplicar el sistema de coordenadas del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aplicar el sistema de coordenadas del eje extendido
    * @param [in]  applyAxisId Número de eje extendido bit0-bit3 corresponden a los números de eje extendido 1-4, por ejemplo, para aplicar los ejes extendidos 1 y 3, sería 0b 0000 0101; es decir, 5
    * @param [in]  axisCoordNum Número del sistema de coordenadas del eje extendido
    * @param [in]  coord Valor del sistema de coordenadas
    * @param [in]  calibFlag Indicador de calibración 0-no, 1-sí
    * @return Código de error
    */
    int ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Obtener el sistema de coordenadas del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener el sistema de coordenadas del eje extendido
    * @param [out] coord Sistema de coordenadas del eje extendido
    * @return Código de error
    */
    int ExtAxisGetCoord(DescPose coord);

Ejemplo de código de calibración del sistema de coordenadas del eje extendido
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestUDPAxisCalib(Robot robot)
    {
        UDPComParam para1=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);

        int rtn = robot.ExtDevSetUDPComParam(para1);
        String ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        UDPComParam para2=new UDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum,0);

        rtn = robot.ExtDevGetUDPComParam(para2);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        rtn = robot.ExtAxisServoOn(2, 1);

        robot.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4,  0, 0, 0, 0, 0, 0);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);

        DescPose toolCoord=new DescPose(0, 0, 210, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);

        JointPos jSafe=new JointPos(115.193, -96.149, 92.489, -87.068, -89.15, -83.488);
        JointPos j1=new JointPos(117.559, -92.624, 100.329, -96.909, -94.057, -83.488);
        JointPos j2=new JointPos(112.239, -90.096, 99.282, -95.909, -89.824, -83.488);
        JointPos j3=new JointPos(110.839, -83.473, 93.166, -89.22, -90.499, -83.487);
        JointPos j4=new JointPos(107.935, -83.572, 95.424, -92.873, -87.933, -83.488);

        DescPose descSafe =new DescPose(0,0,0,0,0,0);
        DescPose desc1 = new DescPose(0,0,0,0,0,0);
        DescPose desc2 = new DescPose(0,0,0,0,0,0);
        DescPose desc3 = new DescPose(0,0,0,0,0,0);
        DescPose desc4 = new DescPose(0,0,0,0,0,0);
        ExaxisPos exaxisPos =new ExaxisPos(0,0,0,0);
        DescPose offdese =new DescPose(0, 0, 0, 0, 0, 0);

        robot.GetForwardKin(jSafe, descSafe);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.Sleep(2000);

        robot.GetForwardKin(j1, desc1);
        robot.MoveJ(j1, desc1, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.Sleep(2000);

        DescPose actualTCPPos =new DescPose(0,0,0,0,0,0);

        robot.GetActualTCPPose(actualTCPPos);
        robot.SetRefPointInExAxisEnd(actualTCPPos);
        rtn = robot.PositionorSetRefPoint(1);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j2, desc2);
        rtn = robot.MoveJ(j2, desc2, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(2);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j3, desc3);
        robot.MoveJ(j3, desc3, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(3);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j4, desc4);
        robot.MoveJ(j4, desc4, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(4);
        robot.Sleep(2000);

        DescPose axisCoord = new DescPose();
        robot.PositionorComputeECoordSys(axisCoord);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);

        robot.CloseRPC();
        return 0;
    }

Movimiento del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Movimiento del eje extendido UDP
    * @param [in] pos Posición objetivo
    * @param [in] ovl Porcentaje de velocidad
    * @param [in] blend Parámetro de suavizado (mm o ms)
    * @return Código de error
    */
    int ExtAxisMove(ExaxisPos pos, double ovl, double blend)

Ejemplo de código de movimiento del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestUDPAxisCalib(Robot robot)
    {
        ExaxisPos exaxisPos = new ExaxisPos( 20, 0, 0, 0 );
        robot.ExtAxisMove(exaxisPos,40);
        robot.CloseRPC();
        return 0;
    }

Movimiento sincronizado del eje extendido UDP con el movimiento de las articulaciones del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimiento sincronizado del eje extendido UDP con el movimiento de las articulaciones del robot
    * @param [in] joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param [in] desc_pos   Pose cartesiana objetivo
    * @param [in] tool  Número de coordenada de herramienta, rango [0~14]
    * @param [in] user  Número de coordenada de pieza, rango [0~14]
    * @param [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] epos  Posición del eje extendido, unidad mm
    * @param [in] blendT [-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad ms
    * @param [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] ffset_pos  Cantidad de desplazamiento de la pose
    * @return Código de error
    */
    int ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos);

Movimiento sincronizado del eje extendido UDP con el movimiento de las articulaciones del robot (cálculo automático de cinemática directa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento sincronizado del eje extendido UDP con el movimiento de las articulaciones del robot (cálculo automático de cinemática directa)
    * @param  [in] joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param  [in] tool  Número de coordenada de herramienta, rango [0~14]
    * @param  [in] user  Número de coordenada de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] epos  Posición del eje extendido, unidad mm
    * @param  [in] blendT [-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad ms
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Cantidad de desplazamiento de la pose
    * @return  Código de error
    */
    int ExtAxisSyncMoveJ(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos) 

Ejemplo de código de movimiento sincronizado del eje extendido UDP con el movimiento de las articulaciones del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public int testSyncMoveJ(Robot robot)
    {
        //1.Calibrar y aplicar el sistema de coordenadas de herramienta del robot; puede utilizar el método de cuatro puntos o de seis puntos para la calibración y aplicación del sistema de coordenadas de herramienta; las interfaces relacionadas con la calibración del sistema de coordenadas de herramienta son las siguientes:
        //  int SetToolPoint(int point_num); //Establecer el punto de referencia de la herramienta - método de seis puntos
        //  int ComputeTool(ref DescPose tcp_pose); //Calcular el sistema de coordenadas de herramienta
        //  int SetTcp4RefPoint(int point_num);  //Establecer el punto de referencia de la herramienta - método de cuatro puntos
        //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
        //  int SetToolCoord(int id, DescPose coord, int type, int install); //Establecer el sistema de coordenadas de herramienta a aplicar
        //  int SetToolList(int id, DescPose coord, int type, int install);  //Establecer la lista de sistemas de coordenadas de herramienta a aplicar
        //2.Establecer los parámetros de comunicación UDP y cargar la comunicación UDP
        UDPComParam param=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        //3.Establecer los parámetros del eje extendido, incluidos el tipo de eje extendido, los parámetros del accionamiento del eje extendido y los parámetros DH del eje extendido
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posicionador de un solo eje y parámetros DH
        robot.SetRobotPosToAxis(1); //Posición de instalación del eje extendido
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parámetros del servoaccionamiento; este ejemplo es un posicionador de un solo eje, por lo que solo se necesita configurar un parámetro de accionamiento; si elige un tipo de eje extendido con varios ejes, debe configurar los parámetros de accionamiento para cada eje
        //4.Habilitar y poner a cero los ejes seleccionados
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        //5.Calibrar y aplicar el sistema de coordenadas del eje extendido
        DescPose pos = new DescPose(/* Introduzca las coordenadas de su punto de calibración */ );
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /*Debe calibrar el eje extendido mediante cuatro puntos en posiciones diferentes, por lo que debe llamar a esta interfaz 4 veces para completar la calibración */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord); //Calcular el resultado de la calibración del eje extendido
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Aplicar el resultado de la calibración al sistema de coordenadas del eje extendido
        //6.Calibrar el sistema de coordenadas de la pieza sobre el eje extendido; necesitará las siguientes interfaces
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);
        //7.Registrar el punto inicial de su movimiento articular sincronizado
        DescPose startdescPose = new DescPose(/*Introduzca sus coordenadas*/ );
        JointPos startjointPos = new JointPos(/*Introduzca sus coordenadas*/ );
        ExaxisPos startexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del punto inicial de su eje extendido */ );
        //8.Registrar las coordenadas del punto final de su movimiento articular sincronizado
        DescPose enddescPose = new DescPose(/*Introduzca sus coordenadas*/ );
        JointPos endjointPos = new JointPos(/*Introduzca sus coordenadas*/ );
        ExaxisPos endexaxisPos =new ExaxisPos(/* Introduzca las coordenadas del punto final de su eje extendido */);
        //9.Escribir el programa de movimiento sincronizado
        //Moverse al punto inicial, suponiendo que el sistema de coordenadas de herramienta y el sistema de coordenadas de pieza aplicados son ambos 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose( 0, 0, 0, 0, 0, 0 );
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniciar el movimiento sincronizado
        robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniciar el movimiento sincronizado
        robot.ExtAxisSyncMoveJ(endjointPos, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
        robot.CloseRPC();
        return 0;
    }

Movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot
    * @param [in] joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param [in] desc_pos   Pose cartesiana objetivo
    * @param [in] tool  Número de coordenada de herramienta, rango [0~14]
    * @param [in] user  Número de coordenada de pieza, rango [0~14]
    * @param [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] epos  Posición del eje extendido, unidad mm
    * @param [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos  Cantidad de desplazamiento de la pose
    * @return Código de error
    */
    int ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot (cálculo automático de cinemática inversa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot (cálculo automático de cinemática inversa)
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número de coordenada de herramienta, rango [0~14]
    * @param  [in] user  Número de coordenada de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] epos  Posición del eje extendido, unidad mm
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Cantidad de desplazamiento de la pose
    * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return  Código de error
    */
    int ExtAxisSyncMoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos,int config)

Ejemplo de código de movimiento sincronizado del eje extendido UDP con el movimiento lineal del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public int testSyncMoveL(Robot robot)
    {
        //1.Calibrar y aplicar el sistema de coordenadas de herramienta del robot; puede utilizar el método de cuatro puntos o de seis puntos para la calibración y aplicación del sistema de coordenadas de herramienta; las interfaces relacionadas con la calibración del sistema de coordenadas de herramienta son las siguientes:
        //  int SetToolPoint(int point_num); //Establecer el punto de referencia de la herramienta - método de seis puntos
        //  int ComputeTool(ref DescPose tcp_pose); //Calcular el sistema de coordenadas de herramienta
        //  int SetTcp4RefPoint(int point_num);  //Establecer el punto de referencia de la herramienta - método de cuatro puntos
        //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
        //  int SetToolCoord(int id, DescPose coord, int type, int install); //Establecer el sistema de coordenadas de herramienta a aplicar
        //  int SetToolList(int id, DescPose coord, int type, int install);  //Establecer la lista de sistemas de coordenadas de herramienta a aplicar
        //2.Establecer los parámetros de comunicación UDP y cargar la comunicación UDP
        UDPComParam param=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        //3.Establecer los parámetros del eje extendido, incluidos el tipo de eje extendido, los parámetros del accionamiento del eje extendido y los parámetros DH del eje extendido
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posicionador de un solo eje y parámetros DH
        robot.SetRobotPosToAxis(1); //Posición de instalación del eje extendido
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parámetros del servoaccionamiento; este ejemplo es un posicionador de un solo eje, por lo que solo se necesita configurar un parámetro de accionamiento; si elige un tipo de eje extendido con varios ejes, debe configurar los parámetros de accionamiento para cada eje
        //4.Habilitar y poner a cero los ejes seleccionados
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        //5.Calibrar y aplicar el sistema de coordenadas del eje extendido
        DescPose pos = new DescPose(/* Introduzca las coordenadas de su punto de calibración */ );
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /*Debe calibrar el eje extendido mediante cuatro puntos en posiciones diferentes, por lo que debe llamar a esta interfaz 4 veces para completar la calibración */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord); //Calcular el resultado de la calibración del eje extendido
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Aplicar el resultado de la calibración al sistema de coordenadas del eje extendido
        //6.Calibrar el sistema de coordenadas de la pieza sobre el eje extendido; necesitará las siguientes interfaces
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);
        //7.Registrar el punto inicial de su movimiento articular sincronizado
        DescPose startdescPose = new DescPose(/*Introduzca sus coordenadas*/ );
        JointPos startjointPos = new JointPos(/*Introduzca sus coordenadas*/ );
        ExaxisPos startexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del punto inicial de su eje extendido */ );
        //8.Registrar las coordenadas del punto final de su movimiento articular sincronizado
        DescPose enddescPose = new DescPose(/*Introduzca sus coordenadas*/ );
        JointPos endjointPos = new JointPos(/*Introduzca sus coordenadas*/ );
        ExaxisPos endexaxisPos =new ExaxisPos(/* Introduzca las coordenadas del punto final de su eje extendido */);
        //9.Escribir el programa de movimiento sincronizado
        //Moverse al punto inicial, suponiendo que el sistema de coordenadas de herramienta y el sistema de coordenadas de pieza aplicados son ambos 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose( 0, 0, 0, 0, 0, 0 );
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniciar el movimiento sincronizado
        robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniciar el movimiento sincronizado
        robot.ExtAxisSyncMoveL(enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese,-1);
        robot.CloseRPC();
        return 0;
    }

Movimiento sincronizado del eje extendido UDP con el movimiento circular del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimiento sincronizado del eje extendido UDP con el movimiento circular del robot
    * @param [in] joint_pos_p  Posición de las articulaciones del punto de trayectoria, unidad deg
    * @param [in] desc_pos_p   Pose cartesiana del punto de trayectoria
    * @param [in] ptool  Número de coordenada de herramienta, rango [0~14]
    * @param [in] puser  Número de coordenada de pieza, rango [0~14]
    * @param [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_p  Posición del eje extendido en el punto intermedio, unidad mm
    * @param [in] poffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_p  Cantidad de desplazamiento de la pose
    * @param [in] joint_pos_t  Posición de las articulaciones del punto objetivo, unidad deg
    * @param [in] desc_pos_t   Pose cartesiana del punto objetivo
    * @param [in] ttool  Número de coordenada de herramienta, rango [0~14]
    * @param [in] tuser  Número de coordenada de pieza, rango [0~14]
    * @param [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_t  Posición del eje extendido, unidad mm
    * @param [in] toffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_t  Cantidad de desplazamiento de la pose
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @return Código de error
    */
    int ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR);

Movimiento sincronizado del eje extendido UDP con el movimiento circular del robot (cálculo automático de cinemática inversa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento sincronizado del eje extendido UDP con el movimiento circular del robot (cálculo automático de cinemática inversa)
    * @param  [in] desc_pos_p   Pose cartesiana del punto de trayectoria
    * @param  [in] ptool  Número de coordenada de herramienta, rango [0~14]
    * @param  [in] puser  Número de coordenada de pieza, rango [0~14]
    * @param  [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_p  Posición del eje extendido, unidad mm
    * @param  [in] poffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_p  Cantidad de desplazamiento de la pose
    * @param  [in] desc_pos_t   Pose cartesiana del punto objetivo
    * @param  [in] ttool  Número de coordenada de herramienta, rango [0~14]
    * @param  [in] tuser  Número de coordenada de pieza, rango [0~14]
    * @param  [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_t  Posición del eje extendido, unidad mm
    * @param  [in] toffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_t  Cantidad de desplazamiento de la pose
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return  Código de error
    */
    int ExtAxisSyncMoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR,int config)

Ejemplo de código de movimiento sincronizado del eje extendido UDP con el movimiento circular del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public int testSyncMoveC(Robot robot)
    {
        //1.Calibrar y aplicar el sistema de coordenadas de herramienta del robot; puede utilizar el método de cuatro puntos o de seis puntos para la calibración y aplicación del sistema de coordenadas de herramienta; las interfaces relacionadas con la calibración del sistema de coordenadas de herramienta son las siguientes:
        //  int SetToolPoint(int point_num); //Establecer el punto de referencia de la herramienta - método de seis puntos
        //  int ComputeTool(ref DescPose tcp_pose); //Calcular el sistema de coordenadas de herramienta
        //  int SetTcp4RefPoint(int point_num);  //Establecer el punto de referencia de la herramienta - método de cuatro puntos
        //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcular el sistema de coordenadas de herramienta - método de cuatro puntos
        //  int SetToolCoord(int id, DescPose coord, int type, int install); //Establecer el sistema de coordenadas de herramienta a aplicar
        //  int SetToolList(int id, DescPose coord, int type, int install);  //Establecer la lista de sistemas de coordenadas de herramienta a aplicar
        //2.Establecer los parámetros de comunicación UDP y cargar la comunicación UDP
        UDPComParam param=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        //3.Establecer los parámetros del eje extendido, incluidos el tipo de eje extendido, los parámetros del accionamiento del eje extendido y los parámetros DH del eje extendido
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posicionador de un solo eje y parámetros DH
        robot.SetRobotPosToAxis(1); //Posición de instalación del eje extendido
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parámetros del servoaccionamiento; este ejemplo es un posicionador de un solo eje, por lo que solo se necesita configurar un parámetro de accionamiento; si elige un tipo de eje extendido con varios ejes, debe configurar los parámetros de accionamiento para cada eje
        //4.Habilitar y poner a cero los ejes seleccionados
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        //5.Calibrar y aplicar el sistema de coordenadas del eje extendido
        DescPose pos = new DescPose(/* Introduzca las coordenadas de su punto de calibración */ );
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /*Debe calibrar el eje extendido mediante cuatro puntos en posiciones diferentes, por lo que debe llamar a esta interfaz 4 veces para completar la calibración */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord); //Calcular el resultado de la calibración del eje extendido
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Aplicar el resultado de la calibración al sistema de coordenadas del eje extendido
        //6.Calibrar el sistema de coordenadas de la pieza sobre el eje extendido; necesitará las siguientes interfaces
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);
        //7.Registrar el punto inicial de su movimiento circular sincronizado
        DescPose startdescPose = new DescPose(/*Introduzca sus coordenadas*/ );
        JointPos startjointPos = new JointPos(/*Introduzca sus coordenadas*/ );
        ExaxisPos startexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del punto inicial de su eje extendido */ );
        //8.Registrar las coordenadas del punto final de su movimiento circular sincronizado
        DescPose enddescPose = new DescPose(/*Introduzca sus coordenadas*/ );
        JointPos endjointPos = new JointPos(/*Introduzca sus coordenadas*/ );
        ExaxisPos endexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del punto final de su eje extendido */ );
        //9.Registrar las coordenadas del punto intermedio de su movimiento circular sincronizado
        DescPose middescPose = new DescPose(/*Introduzca sus coordenadas*/ );
        JointPos midjointPos =new JointPos(/*Introduzca sus coordenadas*/ );
        ExaxisPos midexaxisPos = new ExaxisPos(/* Introduzca las coordenadas del eje extendido en el punto intermedio del arco del robot */ );
        //10.Escribir el programa de movimiento sincronizado
        //Moverse al punto inicial, suponiendo que el sistema de coordenadas de herramienta y el sistema de coordenadas de pieza aplicados son ambos 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose( 0, 0, 0, 0, 0, 0 );
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniciar el movimiento sincronizado
        robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniciar el movimiento sincronizado
        robot.ExtAxisSyncMoveC(middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0,-1);
        robot.CloseRPC();
        return 0;
    }

Establecer DO extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer DO extendida
    * @param [in] DONum Número de DO
    * @param [in] bOpen Interruptor true-abrir; false-cerrar
    * @param [in] smooth Si se suaviza
    * @param [in] block Si es bloqueante
    * @return Código de error
    */
    int SetAuxDO(int DONum, boolean bOpen, boolean smooth, boolean block);

Establecer AO extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer AO extendida
    * @param [in] AONum Número de AO
    * @param [in] value Valor analógico [0-4095]
    * @param [in] block Si es bloqueante
    * @return Código de error
    */
    int SetAuxAO(int AONum, double value, boolean block);

Establecer el tiempo de filtrado de entrada DI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el tiempo de filtrado de entrada DI extendida
    * @param [in] filterTime Tiempo de filtrado (ms)
    * @return  Código de error
    */
    int SetAuxDIFilterTime(int filterTime);

Establecer el tiempo de filtrado de entrada AI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el tiempo de filtrado de entrada AI extendida
    * @param [in] AONum Número de AO
    * @param [in] filterTime Tiempo de filtrado (ms)
    * @return Código de error
    */
    int SetAuxAIFilterTime(int AONum, int filterTime);

Esperar la entrada DI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Esperar la entrada DI extendida
    * @param [in] DINum Número de DI
    * @param [in] bOpen Interruptor 0-cerrado; 1-abierto
    * @param [in] time Tiempo máximo de espera (ms)
    * @param [in] errorAlarm Si se continúa el movimiento
    * @return Código de error
    */
    int WaitAuxDI(int DINum, boolean bOpen, int time, boolean errorAlarm);

Esperar la entrada AI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
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
    int WaitAuxAI(int AINum, int sign, int value, int time, boolean errorAlarm);
    
Obtener el valor de DI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el valor de DI extendida
    * @param [in] DINum Número de DI
    * @param [in] isNoBlock Si es bloqueante
    * @return List[0]:código de error; List[1] : isOpen 0-cerrado; 1-abierto
    */
    List<Integer> GetAuxDI(int DINum, boolean isNoBlock)

Obtener el valor de AI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el valor de AI extendida
    * @param [in] AINum Número de AI
    * @param [in] isNoBlock Si es bloqueante
    * @return List[0]:código de error; List[1] : value valor de entrada
    */
    List<Integer> GetAuxAI(int AINum, boolean isNoBlock);

Ejemplo de código de IO extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAuxDOAO(Robot robot)
    {
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, true, false, true);
            robot.Sleep(100);
        }
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, false, false, true);
            robot.Sleep(100);
        }

        for (int i = 0; i < 409; i++)
        {
            robot.SetAuxAO(0, i * 10, true);
            robot.SetAuxAO(1, 4095 - i * 10, true);
            robot.SetAuxAO(2, i * 10, true);
            robot.SetAuxAO(3, 4095 - i * 10, true);
            robot.Sleep(10);
        }

        robot.SetAuxDIFilterTime(10);
        robot.SetAuxAIFilterTime(0, 10);


        int curValue = -1;
        List<Integer> liter=new ArrayList<>();
        for (int i = 0; i < 4; i++)
        {
            liter = robot.GetAuxAI(i, true);
        }

        robot.WaitAuxDI(1, false, 1000, false);
        robot.WaitAuxAI(1, 1, 132, 1000, false);

        robot.CloseRPC();
        return 0;
    }

Habilitación del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Habilitación del dispositivo móvil
    * @param [in] enable false-deshabilitar; true-habilitar
    * @return Código de error
    */
    int TractorEnable(Boolean enable);

Retorno a cero del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Retorno a cero del dispositivo móvil
    * @return Código de error
    */
    int TractorHoming();

Movimiento lineal del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Movimiento lineal del dispositivo móvil
    * @param [in] distance Distancia del movimiento lineal (mm)
    * @param [in] vel Porcentaje de velocidad del movimiento lineal (0-100)
    * @return Código de error
    */
    int TractorMoveL(double distance, double vel);

Movimiento circular del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Movimiento circular del dispositivo móvil
    * @param [in] radio Radio del movimiento circular (mm)
    * @param [in] angle Ángulo del movimiento circular (°)
    * @param [in] vel Porcentaje de velocidad del movimiento lineal (0-100)
    * @return Código de error
    */
    int TractorMoveC(double radio, double angle, double vel);

Detención del movimiento del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Detención del movimiento del dispositivo móvil
    * @return Código de error
    */
    int TractorStop();

Ejemplo de código del dispositivo móvil
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);//Establecer el número de reconexiones y el intervalo
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("rpc conexión success");
        }
        else
        {
            System.out.println("rpc conexión fail");
            return ;
        }
        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevSetUDPComParam(param);//comunicación del eje extendido UDP
        robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
        robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
        robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);

        robot.TractorEnable(false);
        robot.Sleep(2000);
        robot.TractorEnable(true);
        robot.Sleep(2000);
        robot.TractorHoming();

        robot.Sleep(2000);
        robot.TractorMoveL(100, 20);
        robot.Sleep(5000);
        robot.TractorMoveL(-100, 20);
        robot.Sleep(5000);
        robot.TractorMoveC(300, 90, 20);
        robot.Sleep(2000);
        robot.TractorStop();//Detención del carro
        robot.TractorMoveC(300, -90, 20);
    }
    
Configuración del tiempo de finalización del posicionamiento del eje extendido UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Configuración del tiempo de finalización del posicionamiento del eje extendido UDP
    * @param time Tiempo de finalización del posicionamiento [ms]
    * @return Código de error
    */
    public int SetExAxisCmdDoneTime(double time)