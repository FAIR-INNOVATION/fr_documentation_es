Soldadura del robot
===================

.. toctree:: 
    :maxdepth: 5

Establecer los parámetros de la curva del proceso de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Establecer los parámetros de la curva del proceso de soldadura
     * @param [in] id Número del proceso de soldadura (1-99)
     * @param [in] startCurrent Corriente de inicio de arco (A)
     * @param [in] startVoltage Voltaje de inicio de arco (V)
     * @param [in] startTime Tiempo de inicio de arco (ms)
     * @param [in] weldCurrent Corriente de soldadura (A)
     * @param [in] weldVoltage Voltaje de soldadura (V)
     * @param [in] endCurrent Corriente de cierre de arco (A)
     * @param [in] endVoltage Voltaje de cierre de arco (V)
     * @param [in] endTime Tiempo de cierre de arco (ms)
     * @return Código de error
     */
    errno_t WeldingSetProcessParam(int id, double startCurrent, double startVoltage, double startTime, double weldCurrent, double weldVoltage, double endCurrent, double endVoltage, double endTime);

Obtener los parámetros de la curva del proceso de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Obtener los parámetros de la curva del proceso de soldadura
     * @param [in] id Número del proceso de soldadura (1-99)
     * @param [out] startCurrent Corriente de inicio de arco (A)
     * @param [out] startVoltage Voltaje de inicio de arco (V)
     * @param [out] startTime Tiempo de inicio de arco (ms)
     * @param [out] weldCurrent Corriente de soldadura (A)
     * @param [out] weldVoltage Voltaje de soldadura (V)
     * @param [out] endCurrent Corriente de cierre de arco (A)
     * @param [out] endVoltage Voltaje de cierre de arco (V)
     * @param [out] endTime Tiempo de cierre de arco (ms)
     * @return Código de error
     */
    errno_t WeldingGetProcessParam(int id, double& startCurrent, double& startVoltage, double& startTime, double& weldCurrent, double& weldVoltage, double& endCurrent, double& endVoltage, double& endTime);

Establecer la relación entre la corriente de soldadura y la salida analógica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la relación entre la corriente de soldadura y la salida analógica
    * @param [in] currentMin Valor de corriente del punto izquierdo de la relación lineal corriente de soldadura-salida analógica (A)
    * @param [in] currentMax Valor de corriente del punto derecho de la relación lineal corriente de soldadura-salida analógica (A)
    * @param [in] outputVoltageMin Valor de voltaje de salida analógica del punto izquierdo de la relación lineal corriente de soldadura-salida analógica (V)
    * @param [in] outputVoltageMax Valor de voltaje de salida analógica del punto derecho de la relación lineal corriente de soldadura-salida analógica (V)
    * @return Código de error
    */
    errno_t WeldingSetCurrentRelation(double currentMin, double currentMax, double outputVoltageMin, double outputVoltageMax);

Establecer la relación entre el voltaje de soldadura y la salida analógica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la relación entre el voltaje de soldadura y la salida analógica
    * @param [in] weldVoltageMin Valor de voltaje de soldadura del punto izquierdo de la relación lineal voltaje de soldadura-salida analógica (A)
    * @param [in] weldVoltageMax Valor de voltaje de soldadura del punto derecho de la relación lineal voltaje de soldadura-salida analógica (A)
    * @param [in] outputVoltageMin Valor de voltaje de salida analógica del punto izquierdo de la relación lineal voltaje de soldadura-salida analógica (V)
    * @param [in] outputVoltageMax Valor de voltaje de salida analógica del punto derecho de la relación lineal voltaje de soldadura-salida analógica (V)
    * @return Código de error
    */
    errno_t WeldingSetVoltageRelation(double weldVoltageMin, double weldVoltageMax, double outputVoltageMin, double outputVoltageMax);

Obtener la relación entre la corriente de soldadura y la salida analógica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la relación entre la corriente de soldadura y la salida analógica
    * @param [out] currentMin Valor de corriente del punto izquierdo de la relación lineal corriente de soldadura-salida analógica (A)
    * @param [out] currentMax Valor de corriente del punto derecho de la relación lineal corriente de soldadura-salida analógica (A)
    * @param [out] outputVoltageMin Valor de voltaje de salida analógica del punto izquierdo de la relación lineal corriente de soldadura-salida analógica (V)
    * @param [out] outputVoltageMax Valor de voltaje de salida analógica del punto derecho de la relación lineal corriente de soldadura-salida analógica (V)
    * @return Código de error
    */
    errno_t WeldingGetCurrentRelation(double *currentMin, double *currentMax, double *outputVoltageMin, double *outputVoltageMax);

Obtener la relación entre el voltaje de soldadura y la salida analógica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener la relación entre el voltaje de soldadura y la salida analógica
    * @param [out] weldVoltageMin Valor de voltaje de soldadura del punto izquierdo de la relación lineal voltaje de soldadura-salida analógica (A)
    * @param [out] weldVoltageMax Valor de voltaje de soldadura del punto derecho de la relación lineal voltaje de soldadura-salida analógica (A)
    * @param [out] outputVoltageMin Valor de voltaje de salida analógica del punto izquierdo de la relación lineal voltaje de soldadura-salida analógica (V)
    * @param [out] outputVoltageMax Valor de voltaje de salida analógica del punto derecho de la relación lineal voltaje de soldadura-salida analógica (V)
    * @return Código de error
    */
    errno_t WeldingGetVoltageRelation(double *weldVoltageMin, double *weldVoltageMax, double *outputVoltageMin, double *outputVoltageMax);

Establecer la corriente de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer la corriente de soldadura
    * @param [in] ioType Tipo de IO de control 0-IO de la caja de control; 1-IO extendida
    * @param [in] current Valor de corriente de soldadura (A)
    * @param [in] AOIndex Puerto de salida analógica del control de corriente de soldadura de la caja de control (0-1)
    * @param [in] blend Si se suaviza 0-sin suavizado; 1-suavizado
    * @return Código de error
    */
    errno_t WeldingSetCurrent(int ioType, double current, int AOIndex, int blend);

Establecer el voltaje de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el voltaje de soldadura
    * @param [in] ioType Tipo de IO de control 0-IO de la caja de control; 1-IO extendida
    * @param [in] voltage Valor de voltaje de soldadura (A)
    * @param [in] AOIndex Puerto de salida analógica del control de voltaje de soldadura de la caja de control (0-1)
    * @param [in] blend Si se suaviza 0-sin suavizado; 1-suavizado
    * @return Código de error
    */
    errno_t WeldingSetVoltage(int ioType, double voltage, int AOIndex, int blend);

Establecer los parámetros de oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
     * @brief Establecer los parámetros de oscilación
     * @param [in] weaveNum Número de configuración de los parámetros de oscilación de soldadura
     * @param [in] weaveType Tipo de oscilación 0-oscilación triangular plana; 1-oscilación triangular en L vertical; 2-oscilación circular en sentido horario; 3-oscilación circular en sentido antihorario; 4-oscilación sinusoidal plana; 5-oscilación sinusoidal en L vertical; 6-oscilación triangular vertical; 7-oscilación sinusoidal vertical
     * @param [in] weaveFrequency Frecuencia de oscilación (Hz)
     * @param [in] weaveIncStayTime Modo de espera 0-el ciclo no incluye el tiempo de espera; 1-el ciclo incluye el tiempo de espera
     * @param [in] weaveRange Amplitud de oscilación (mm)
     * @param [in] weaveLeftRange Longitud del lado izquierdo de la oscilación triangular vertical (mm)
     * @param [in] weaveRightRange Longitud del lado derecho de la oscilación triangular vertical (mm)
     * @param [in] additionalStayTime Tiempo de permanencia en el vértice de la oscilación triangular vertical (mm)
     * @param [in] weaveLeftStayTime Tiempo de permanencia izquierdo de la oscilación (ms)
     * @param [in] weaveRightStayTime Tiempo de permanencia derecho de la oscilación (ms)
     * @param [in] weaveCircleRadio Oscilación circular - relación de retorno (0-100%)
     * @param [in] weaveStationary Espera en la posición de oscilación, 0-la posición continúa moviéndose durante el tiempo de espera; 1-la posición permanece estática durante el tiempo de espera
     * @param [in] weaveYawAngle Ángulo de orientación de la dirección de oscilación (rotación alrededor del eje Z de oscilación), unidad °
     * @param [in] weaveRotAngle Ángulo de inclinación lateral de la dirección de oscilación (desviación alrededor del eje X de oscilación), unidad °
     * @return Código de error
     */
      errno_t WeaveSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, double weaveLeftRange, double weaveRightRange, int additionalStayTime, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary, double weaveYawAngle, double weaveRotAngle = 0);

Ejemplo de código de configuración de los parámetros de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestSetWeldParam(void)
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
        robot.WeldingSetProcessParam(1, 177, 27, 1000, 178, 28, 176, 26, 1000);
        robot.WeldingSetProcessParam(2, 188, 28, 555, 199, 29, 133, 23, 333);
        double startCurrent = 0;
        double startVoltage = 0;
        double startTime = 0;
        double weldCurrent = 0;
        double weldVoltage = 0;
        double endCurrent = 0;
        double endVoltage = 0;
        double endTime = 0;
        robot.WeldingGetProcessParam(1, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime);
        cout << "the Num 1 process param is " << startCurrent << " " << startVoltage << " " << startTime << " " << weldCurrent << " " << weldVoltage << " " << endCurrent << " " << endVoltage << " " << endTime << endl;
        robot.WeldingGetProcessParam(2, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime);
        cout << "the Num 2 process param is " << startCurrent << " " << startVoltage << " " << startTime << " " << weldCurrent << " " << weldVoltage << " " << endCurrent << " " << endVoltage << " " << endTime << endl;
        rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0);
        cout << "WeldingSetCurrentRelation rtn is: " << rtn << endl;
        rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1);
        cout << "WeldingSetVoltageRelation rtn is: " << rtn << endl;
        double current_min = 0;
        double current_max = 0;
        double vol_min = 0;
        double vol_max = 0;
        double output_vmin = 0;
        double output_vmax = 0;
        int curIndex = 0;
        int volIndex = 0;
        rtn = robot.WeldingGetCurrentRelation(&current_min, &current_max, &output_vmin, &output_vmax, &curIndex);
        cout << "WeldingGetCurrentRelation rtn is: " << rtn << endl;
        cout << "current min " << current_min << " current max " << current_max << " output vol min " << output_vmin << " output vol max " << output_vmax << endl;
        rtn = robot.WeldingGetVoltageRelation(&vol_min, &vol_max, &output_vmin, &output_vmax, &volIndex);
        cout << "WeldingGetVoltageRelation rtn is: " << rtn << endl;
        cout << "vol min " << vol_min << " vol max " << vol_max << " output vol min " << output_vmin << " output vol max " << output_vmax << endl;
        rtn = robot.WeldingSetCurrent(0, 100, 0, 0);
        cout << "WeldingSetCurrent rtn is: " << rtn << endl;
        this_thread::sleep_for(chrono::seconds(3));
        rtn = robot.WeldingSetVoltage(0, 10, 0, 0);
        cout << "WeldingSetVoltage rtn is: " << rtn << endl;
        rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0, 60.000000);
        cout << "rtn is: " << rtn << endl;
        robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0);
        rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200);
        printf("WeldingSetCheckArcInterruptionParam  %d\n", rtn);
        rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0);
        printf("WeldingSetReWeldAfterBreakOffParam  %d\n", rtn);
        int enable = 0;
        double length = 0;
        double velocity = 0;
        int moveType = 0;
        int checkEnable = 0;
        int arcInterruptTimeLength = 0;
        rtn = robot.WeldingGetCheckArcInterruptionParam(&checkEnable, &arcInterruptTimeLength);
        printf("WeldingGetCheckArcInterruptionParam checkEnable %d  arcInterruptTimeLength %d\n", checkEnable, arcInterruptTimeLength);
        rtn = robot.WeldingGetReWeldAfterBreakOffParam(&enable, &length, &velocity, &moveType);
        printf("WeldingGetReWeldAfterBreakOffParam enable = %d, length = %lf, velocity = %lf, moveType = %d\n", enable, length, velocity, moveType);
        robot.SetWeldMachineCtrlModeExtDoNum(17);
        for (int i = 0; i < 5; i++)
        {
            int getCtrlMode = -1;
            robot.SetWeldMachineCtrlMode(0);
            robot.GetWeldMachineCtrlMode(getCtrlMode);
            printf("GetWeldMachineCtrlMode %d\n", getCtrlMode);
            robot.Sleep(1000);
            robot.SetWeldMachineCtrlMode(1);
            robot.GetWeldMachineCtrlMode(getCtrlMode);
            printf("GetWeldMachineCtrlMode %d\n", getCtrlMode);
            robot.Sleep(1000);
        }
        robot.CloseRPC();
        return 0;
    }

Establecer los parámetros de oscilación en tiempo real
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer los parámetros de oscilación en tiempo real
    * @param [in] weaveNum Número de configuración de los parámetros de oscilación de soldadura
    * @param [in] weaveType Tipo de oscilación 0-oscilación triangular plana; 1-oscilación triangular en L vertical; 2-oscilación circular en sentido horario; 3-oscilación circular en sentido antihorario; 4-oscilación sinusoidal plana; 5-oscilación sinusoidal en L vertical; 6-oscilación triangular vertical; 7-oscilación sinusoidal vertical
    * @param [in] weaveFrequency Frecuencia de oscilación (Hz)
    * @param [in] weaveIncStayTime Modo de espera 0-el ciclo no incluye el tiempo de espera; 1-el ciclo incluye el tiempo de espera
    * @param [in] weaveRange Amplitud de oscilación (mm)
    * @param [in] weaveLeftStayTime Tiempo de permanencia izquierdo de la oscilación (ms)
    * @param [in] weaveRightStayTime Tiempo de permanencia derecho de la oscilación (ms)
    * @param [in] weaveCircleRadio Oscilación circular - relación de retorno (0-100%)
    * @param [in] weaveStationary Espera en la posición de oscilación, 0-la posición continúa moviéndose durante el tiempo de espera; 1-la posición permanece estática durante el tiempo de espera
    * @return Código de error
    */
    errno_t WeaveOnlineSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary);

Establecer los parámetros de detección de interrupción accidental del arco de soldadura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
	 * @brief Establecer los parámetros de detección de interrupción accidental del arco de soldadura del robot
	 * @param [in] checkEnable Si se habilita la detección; 0-no habilitar; 1-habilitar
	 * @param [in] arcInterruptTimeLength Duración de confirmación de interrupción del arco (ms)
	 * @return Código de error
    */
	errno_t WeldingSetCheckArcInterruptionParam(int checkEnable, int arcInterruptTimeLength);

Obtener los parámetros de detección de interrupción accidental del arco de soldadura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
	 * @brief Obtener los parámetros de detección de interrupción accidental del arco de soldadura del robot
	 * @param [out] checkEnable Si se habilita la detección; 0-no habilitar; 1-habilitar
	 * @param [out] arcInterruptTimeLength Duración de confirmación de interrupción del arco (ms)
	 * @return Código de error
    */
	errno_t WeldingGetCheckArcInterruptionParam(int* checkEnable, int* arcInterruptTimeLength);

Establecer los parámetros de recuperación de interrupción de soldadura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
	 * @brief Establecer los parámetros de recuperación de interrupción de soldadura del robot
	 * @param [in] enable Si se habilita la recuperación de interrupción de soldadura
	 * @param [in] length Distancia de solapamiento de la soldadura (mm)
	 * @param [in] velocity Porcentaje de velocidad del robot para volver al punto de reinicio de arco (0-100)
	 * @param [in] moveType Modo de movimiento del robot al punto de reinicio de arco; 0-LIN; 1-PTP
	 * @return Código de error
    */
	errno_t WeldingSetReWeldAfterBreakOffParam(int enable, double length, double velocity, int moveType);
    
Obtener los parámetros de recuperación de interrupción de soldadura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
	 * @brief Obtener los parámetros de recuperación de interrupción de soldadura del robot
	 * @param [out] enable Si se habilita la recuperación de interrupción de soldadura
	 * @param [out] length Distancia de solapamiento de la soldadura (mm)
	 * @param [out] velocity Porcentaje de velocidad del robot para volver al punto de reinicio de arco (0-100)
	 * @param [out] moveType Modo de movimiento del robot al punto de reinicio de arco; 0-LIN; 1-PTP
	 * @return Código de error
    */
	errno_t WeldingGetReWeldAfterBreakOffParam(int* enable, double* length, double* velocity, int* moveType);

Establecer el puerto DO extendido del modo de control de la máquina de soldar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el puerto DO extendido del modo de control de la máquina de soldar
    * @param DONum Puerto DO del modo de control de la máquina de soldar (0-127)
    * @return Código de error
    */
    errno_t SetWeldMachineCtrlModeExtDoNum(int DONum);

Establecer el modo de control de la máquina de soldar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el modo de control de la máquina de soldar
    * @param [in] mode Modo de control de la máquina de soldar; 0-modo de un solo parámetro de CC; 1-modo de un solo parámetro de pulso; 2-modo JOB; 3-modo de control cercano; 4-modo separado; 5-modo CC/CV; 6-TIG; 7-CMT; 8-Panasonic-con modo de pulso; 9-Panasonic-sin modo de pulso
    * @param [in] ioType Tipo de control; 0-IO de la caja de control; 1-protocolo de comunicación digital (UDP); 2-protocolo de comunicación digital (ModbusTCP)
    * @return Código de error
    */
    errno_t SetWeldMachineCtrlMode(int mode, int ioType = 1);

Obtener el modo de control de la máquina de soldar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-V3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el modo de control de la máquina de soldar
    * @param [out] mode Modo de control de la máquina de soldar; 0-modo de un solo parámetro de CC; 1-modo de un solo parámetro de pulso; 2-modo JOB; 3-modo de control cercano; 4-modo separado; 5-modo CC/CV; 6-TIG; 7-CMT
    * @return Código de error
    */
    errno_t GetWeldMachineCtrlMode(int& mode);
    
Inicio de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio de soldadura
    * @param [in] ioType Tipo de io 0-IO del controlador;  1-IO extendida
    * @param [in] arcNum Número del archivo de configuración de la máquina de soldar
    * @param [in] timeout Tiempo de espera de inicio de arco
    * @return Código de error
    */
    errno_t ARCStart(int ioType, int arcNum, int timeout);

Fin de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Fin de soldadura
    * @param [in] ioType Tipo de io 0-IO del controlador;  1-IO extendida
    * @param [in] arcNum Número del archivo de configuración de la máquina de soldar
    * @param [in] timeout Tiempo de espera de extinción de arco
    * @return Código de error
    */
    errno_t ARCEnd(int ioType, int arcNum, int timeout);

Inicio de oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio de oscilación
    * @param [in] weaveNum Número de configuración de los parámetros de oscilación de soldadura
    * @return Código de error
    */
    errno_t WeaveStart(int weaveNum);

Fin de oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Fin de oscilación
    * @param [in] weaveNum Número de configuración de los parámetros de oscilación de soldadura
    * @return Código de error
    */
    errno_t WeaveEnd(int weaveNum);

Alimentación de alambre hacia adelante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Alimentación de alambre hacia adelante
    * @param [in] ioType Tipo de io  0-IO del controlador; 1-IO extendida
    * @param [in] wireFeed Control de alimentación de alambre  0-detener alimentación de alambre; 1-alimentar alambre
    * @return Código de error
    */
    errno_t SetForwardWireFeed(int ioType, int wireFeed);

Alimentación de alambre hacia atrás
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Alimentación de alambre hacia atrás
    * @param [in] ioType Tipo de io  0-IO del controlador; 1-IO extendida
    * @param [in] wireFeed Control de alimentación de alambre  0-detener alimentación de alambre; 1-alimentar alambre
    * @return Código de error
    */
    errno_t SetReverseWireFeed(int ioType, int wireFeed);

Suministro de gas
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Suministro de gas
    * @param [in] ioType Tipo de io  0-IO del controlador; 1-IO extendida
    * @param [in] airControl Control de suministro de gas  0-detener suministro de gas; 1-suministrar gas
    * @return Código de error
    */
    errno_t SetAspirated(int ioType, int airControl);

Establecer la recuperación de soldadura tras la interrupción de soldadura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
	 * @brief Establecer la recuperación de soldadura tras la interrupción de soldadura del robot
	 * @return Código de error
    */
	errno_t WeldingStartReWeldAfterBreakOff();

Establecer la salida de soldadura tras la interrupción de soldadura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
    :linenos:

    /**
	 * @brief Establecer la salida de soldadura tras la interrupción de soldadura del robot
	 * @return Código de error
	 */
	errno_t WeldingAbortWeldAfterBreakOff();

Ejemplo de código de control de soldadura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestWelding(void)
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
      robot.SetForwardWireFeed(0, 1);
      robot.Sleep(1000);
      robot.SetForwardWireFeed(0, 0);
      robot.SetReverseWireFeed(0, 1);
      robot.Sleep(1000);
      robot.SetReverseWireFeed(0, 0);
      robot.SetAspirated(0, 1);
      robot.Sleep(1000);
      robot.SetAspirated(0, 0);
      robot.WeldingSetCurrent(1, 230, 0, 0);
      robot.WeldingSetVoltage(1, 24, 0, 1);
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.ARCStart(1, 0, 10000);
      robot.WeaveStart(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.ARCEnd(1, 0, 10000);
      robot.WeaveEnd(0);
      robot.WeldingStartReWeldAfterBreakOff();
      robot.WeldingAbortWeldAfterBreakOff();
      robot.CloseRPC();
      return 0;
    }


Inicio de soldadura por segmentos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio de soldadura por segmentos
    * @param [in] startDesePos Posición cartesiana del punto inicial
    * @param [in] endDesePos Pose cartesiana del punto final
    * @param [in] startJPos Pose de articulaciones del punto inicial
    * @param [in] endJPos Pose de articulaciones del punto final
    * @param [in] weldLength Longitud del segmento de soldadura (mm)
    * @param [in] noWeldLength Longitud del segmento sin soldadura (mm)
    * @param [in] weldIOType Tipo de IO de soldadura (0-IO de la caja de control; 1-IO extendida)
    * @param [in] arcNum Número del archivo de configuración de la máquina de soldar
    * @param [in] weldTimeout Tiempo de espera de inicio/cierre de arco
    * @param [in] isWeave Si oscila
    * @param [in] weaveNum Número de configuración de los parámetros de oscilación de soldadura
    * @param [in] tool Número de coordenada de herramienta, rango [0~14]
    * @param [in] user Número de coordenada de la pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], no disponible actualmente
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] epos Posición del eje extendido, unidad mm
    * @param [in] search 0-sin búsqueda de posición de alambre de soldadura, 1-búsqueda de posición de alambre de soldadura
    * @param [in] offset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos Cantidad de desplazamiento de la pose
    * @return Código de error
    */
    errno_t SegmentWeldStart(DescPose *startDesePos, DescPose *endDesePos, JointPos *startJPos, JointPos *endJPos, double weldLength, double noWeldLength, int weldIOType, int arcNum, int weldTimeout, bool isWeave, int weaveNum, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos *epos, uint8_t search, uint8_t offset_flag, DescPose *offset_pos);

Ejemplo de código de soldadura por segmentos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    int TestSegWeld(void)
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
      robot.WeldingSetCurrent(1, 230, 0, 0);
      robot.WeldingSetVoltage(1, 24, 0, 1);
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      rtn = robot.SegmentWeldStart(&p1Desc, &p2Desc, &p1Joint, &p2Joint, 20, 20, 0, 0, 5000, 0, 0, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      printf("SegmentWeldStart rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }


Inicio de oscilación de simulación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Inicio de oscilación de simulación
     * @param [in] weaveNum Número de parámetros de oscilación
     * @return Código de error
     */
    errno_t WeaveStartSim(int weaveNum);

Fin de oscilación de simulación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Fin de oscilación de simulación
     * @param [in] weaveNum Número de parámetros de oscilación
     * @return Código de error
     */
    errno_t WeaveEndSim(int weaveNum);

Iniciar la alerta de detección de trayectoria (sin movimiento)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Iniciar la alerta de detección de trayectoria (sin movimiento)
     * @param [in] weaveNum  Número de parámetros de oscilación
     * @return Código de error
     */
    errno_t WeaveInspectStart(int weaveNum);

Finalizar la alerta de detección de trayectoria (sin movimiento)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Finalizar la alerta de detección de trayectoria (sin movimiento)
     * @param [in] weaveNum  Número de parámetros de oscilación
     * @return Código de error
     */
    errno_t WeaveInspectEnd(int weaveNum);

Inicio de cambio gradual de oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
     * @brief Inicio de cambio gradual de oscilación
     * @param [in] weaveChangeFlag 1-cambiar parámetros de oscilación; 2-cambiar parámetros de oscilación + velocidad de soldadura
     * @param [in] weaveNum Número de oscilación 
     * @param [in] velStart Velocidad de inicio de soldadura, (cm/min)
     * @param [in] velEnd Velocidad de fin de soldadura, (cm/min)
     * @return Código de error
     */
     errno_t WeaveChangeStart(int weaveChangeFlag, int weaveNum, double velStart, double velEnd);

Ejemplo de código de soldadura con cambio gradual de oscilación del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:
    
    int TestWeave(void)
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
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.WeaveStartSim(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.WeaveEndSim(0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.WeaveInspectStart(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.WeaveInspectEnd(0);
      robot.WeldingSetVoltage(1, 19, 0, 0);
      robot.WeldingSetCurrent(1, 190, 0, 0);
      robot.MoveL(&p1Joint, &p1Desc, 1, 1, 100, 100, 50, -1, &exaxisPos, 0, 0, &offdese);
      robot.ARCStart(1, 0, 10000);
      robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
      robot.WeaveStart(0);
      robot.WeaveChangeStart(1, 0, 50, 30);
      robot.MoveL(&p2Joint, &p2Desc, 1, 1, 100, 100, 1, -1, &exaxisPos, 0, 0, &offdese);
      robot.WeaveChangeEnd();
      robot.WeaveEnd(0);
      robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
      robot.ARCEnd(1, 0, 10000);
      robot.CloseRPC();
      return 0;
    }

Fin de cambio gradual de oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

	/**
	 * @brief  Fin de cambio gradual de oscilación
	 * @return  Código de error
	 */
    errno_t WeaveChangeEnd();

IO extendida - Configurar la señal de detección de gas de la máquina de soldar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief IO extendida - Configurar la señal de detección de gas de la máquina de soldar
     * @param [in] DONum Número DO extendido de la señal de detección de gas
     * @return Código de error
     */
    errno_t SetAirControlExtDoNum(int DONum);

IO extendida - Configurar la señal de inicio de arco de la máquina de soldar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief IO extendida - Configurar la señal de inicio de arco de la máquina de soldar
     * @param [in] DONum Número DO extendido de la señal de inicio de arco de la máquina de soldar
     * @return Código de error
     */
    errno_t SetArcStartExtDoNum(int DONum);

IO extendida - Configurar la señal de alimentación de alambre hacia atrás de la máquina de soldar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief IO extendida - Configurar la señal de alimentación de alambre hacia atrás de la máquina de soldar
     * @param [in] DONum Número DO extendido de la señal de alimentación de alambre hacia atrás
     * @return Código de error
     */
    errno_t SetWireReverseFeedExtDoNum(int DONum);

IO extendida - Configurar la señal de alimentación de alambre hacia adelante de la máquina de soldar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief IO extendida - Configurar la señal de alimentación de alambre hacia adelante de la máquina de soldar
     * @param [in] DONum Número DO extendido de la señal de alimentación de alambre hacia adelante
     * @return Código de error
     */
    errno_t SetWireForwardFeedExtDoNum(int DONum);

IO extendida - Configurar la señal de inicio de arco exitoso de la máquina de soldar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief IO extendida - Configurar la señal de inicio de arco exitoso de la máquina de soldar
     * @param [in] DINum Número DI extendido de la señal de inicio de arco exitoso
     * @return Código de error
     */
    errno_t SetArcDoneExtDiNum(int DINum);

IO extendida - Configurar la señal de preparación de la máquina de soldar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief IO extendida - Configurar la señal de preparación de la máquina de soldar
     * @param [in] DINum Número DI extendido de la señal de preparación de la máquina de soldar
     * @return Código de error
     */
    errno_t SetWeldReadyExtDiNum(int DINum);

IO extendida - Configurar la señal de recuperación de interrupción de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief IO extendida - Configurar la señal de recuperación de interrupción de soldadura
     * @param [in] reWeldDINum Número DI extendido de la señal de recuperación de soldadura tras la interrupción
     * @param [in] abortWeldDINum Número DI extendido de la señal de salida de soldadura tras la interrupción
     * @return Código de error
     */
    errno_t SetExtDIWeldBreakOffRecover(int reWeldDINum, int abortWeldDINum);

Obtener la configuración de funciones de DI extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-V3.9.8
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Obtener la configuración de funciones de DI extendida
     * @param [out] DIConfig Configuración de entrada DI extendida; DIConfig[0]-puerto DI extendido de preparación de la máquina de soldar;
                                         DIConfig[1]-puerto DI extendido de inicio de arco exitoso;
                                            DIConfig[2]-puerto DI extendido de recuperación de interrupción de soldadura;
                                            DIConfig[3]-puerto DI extendido de salida de interrupción de soldadura;
                                            DIConfig[4]-puerto DI extendido de búsqueda de posición de alambre de soldadura exitosa;
                                            DIConfig[5]-puerto DI extendido del estado de funcionamiento de la máquina de soldadura láser;
                                            DIConfig[6]-puerto DI extendido del estado de fallo de la máquina de soldadura láser;
                                            DIConfig[7-15]-reservado
    * @return  Código de error
    */
    errno_t GetExtDIConfig(int DIConfig[16]);
    
Obtener la configuración de funciones de DO extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-V3.9.8
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Obtener la configuración de funciones de DO extendida
     * @param [out] DOConfig Configuración de salida DO extendida; DOConfig[0]-puerto DO extendido de inicio de arco de la máquina de soldar;
                                            DOConfig[1]-puerto DO extendido de detección de gas;
                                            DOConfig[2]-puerto DO extendido de alimentación de alambre hacia adelante;
                                            DOConfig[3]-puerto DO extendido de alimentación de alambre hacia atrás;
                                            DOConfig[4]-puerto DO extendido de búsqueda de posición de alambre de soldadura;
                                            DOConfig[5]-puerto DO extendido del modo de control de la máquina de soldar;
                                            DOConfig[6]-puerto DO extendido de habilitación de la máquina de soldadura láser;
                                            DOConfig[7]-puerto DO extendido de inicio (emisión de luz) de la máquina de soldadura láser;
                                            DOConfig[8]-puerto DO extendido de reinicio de la máquina de soldadura láser;
                                            DOConfig[9-15]-reservado
    * @return  Código de error
    */
    errno_t GetExtDOConfig(int DOConfig[16]);    

Ejemplo de código de configuración de señales de soldadura de IO extendida
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestExtDIConfig(void)
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
        robot.SetArcStartExtDoNum(10);
        robot.SetAirControlExtDoNum(20);
        robot.SetWireForwardFeedExtDoNum(30);
        robot.SetWireReverseFeedExtDoNum(40);
        robot.SetWeldReadyExtDiNum(50);
        robot.SetArcDoneExtDiNum(60);
        robot.SetExtDIWeldBreakOffRecover(70, 80);
        robot.SetWireSearchExtDIONum(0, 1);
        int DIConfig[16] = { 0 };
        int DOConfig[16] = { 0 };
        rtn = robot.GetExtDIConfig(DIConfig);
        printf("GetExtDIConfig rtn is %d\n welder ready %d\narc done %d\nreweld start %d\nabort reweld %d\nwiresearch done %d\nLaser welding State %d\nlaser welding error state %d\n",
            rtn, DIConfig[0], DIConfig[1], DIConfig[2], DIConfig[3], DIConfig[4], DIConfig[5], DIConfig[6]);
        rtn = robot.GetExtDOConfig(DOConfig);
        printf("GetExtDOConfig rtn is %d\n Arc Start %d\nAir Test %d\nWire forward %d\nWire Inverse %d\nwiresearch %d\nWeld Mode %d\nlaser Enable %d\nLaser On %d\nLaser Reset Error %d\n",
            rtn, DOConfig[0], DOConfig[1], DOConfig[2], DOConfig[3], DOConfig[4], DOConfig[5], DOConfig[6], DOConfig[7], DOConfig[8]);
        robot.CloseRPC();
        return 0;
    }

Control de seguimiento de arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

      /**
      * @brief  Control de seguimiento de arco
   	  * @param  [in] flag Interruptor, 0-apagado; 1-encendido
  	  * @param  [in] dalayTime Tiempo de retardo, unidad ms
  	  * @param  [in] isLeftRight Compensación de desviación izquierda-derecha
  	  * @param  [in] klr Coeficiente de ajuste izquierda-derecha (sensibilidad);
  	  * @param  [in] tStartLr Tiempo de inicio de compensación izquierda-derecha cyc
  	  * @param  [in] stepMaxLr Compensación máxima por paso izquierda-derecha mm
  	  * @param  [in] sumMaxLr Compensación máxima total izquierda-derecha mm
  	  * @param  [in] isUpLow Compensación de desviación arriba-abajo
  	  * @param  [in] kud Coeficiente de ajuste arriba-abajo (sensibilidad);
  	  * @param  [in] tStartUd Tiempo de inicio de compensación arriba-abajo cyc
  	  * @param  [in] stepMaxUd Compensación máxima por paso arriba-abajo mm
  	  * @param  [in] sumMaxUd Compensación máxima total arriba-abajo
  	  * @param  [in] axisSelect Selección del sistema de coordenadas arriba-abajo, 0-oscilación; 1-herramienta; 2-base
  	  * @param  [in] referenceType Modo de configuración de la corriente de referencia arriba-abajo, 0-retroalimentación; 1-constante
  	  * @param  [in] referSampleStartUd Inicio del conteo de muestreo de la corriente de referencia arriba-abajo (retroalimentación); cyc
  	  * @param  [in] referSampleCountUd Conteo de ciclos de muestreo de la corriente de referencia arriba-abajo (retroalimentación); cyc
  	  * @param  [in] referenceCurrent Corriente de referencia arriba-abajo mA
  	  * @param  [in] offsetType Tipo de seguimiento de desplazamiento, 0-sin desplazamiento; 1-muestreo; 2-porcentaje
  	  * @param  [in] offsetParameter Parámetro de desplazamiento; muestreo (tiempo de inicio del muestreo de desplazamiento, por defecto se muestrea un ciclo); porcentaje (porcentaje de desplazamiento (-100 ~ 100))
  	  * @return  Código de error
  	  */
	 errno_t ArcWeldTraceControl(int flag, double delaytime, int isLeftRight, double klr, double tStartLr, double stepMaxLr, double sumMaxLr, int isUpLow, double kud, double tStartUd, double stepMaxUd, double sumMaxUd, int axisSelect, int referenceType, double referSampleStartUd, double referSampleCountUd, double referenceCurrent, int offsetType = 0, int offsetParameter = 0);

Establecer el puerto de señal de entrada del seguimiento de arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

     /**
      * @brief  Establecer el puerto de señal de entrada del seguimiento de arco
      * @param  [in] channel Selección de canal AI del seguimiento de arco, [0-3]
      * @return  Código de error
      */
     errno_t ArcWeldTraceExtAIChannelConfig(int channel);


Inicio de seguimiento de arco + compensación de múltiples capas y pasadas
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio de seguimiento de arco + compensación de múltiples capas y pasadas
    * @return Código de error
    */
    errno_t ArcWeldTraceReplayStart();

Fin de seguimiento de arco + compensación de múltiples capas y pasadas
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Fin de seguimiento de arco + compensación de múltiples capas y pasadas
    * @return Código de error
    */
    errno_t ArcWeldTraceReplayEnd();

Cambio de coordenadas de desplazamiento - Soldadura de múltiples capas y pasadas
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Cambio de coordenadas de desplazamiento - Soldadura de múltiples capas y pasadas
    * @return Código de error
    */
    errno_t MultilayerOffsetTrsfToBase(DescTran pointO, DescTran pointX, DescTran pointZ, double dx, double dy, double db, DescPose& offset);

Ejemplo de código de seguimiento de arco para soldadura de múltiples capas y pasadas
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestArcWeldTrace(void)
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
      JointPos mulitilineorigin1_joint(-24.090, -63.501, 84.288, -111.940, -93.426, 57.669);
      DescPose mulitilineorigin1_desc(-677.559, 190.951, -1.205, 1.144, -41.482, -82.577);
      DescTran mulitilineX1_desc;
      mulitilineX1_desc.x = -677.556;
      mulitilineX1_desc.y = 211.949;
      mulitilineX1_desc.z = -1.206;
      DescTran mulitilineZ1_desc;
      mulitilineZ1_desc.x = -677.564;
      mulitilineZ1_desc.y = 190.956;
      mulitilineZ1_desc.z = 19.817;
      JointPos mulitilinesafe_joint(-25.734, -63.778, 81.502, -108.975, -93.392, 56.021);
      DescPose mulitilinesafe_desc(-677.561, 211.950, 19.812, 1.144, -41.482, -82.577);
      JointPos mulitilineorigin2_joint(-29.743, -75.623, 101.241, -116.354, -94.928, 55.735);
      DescPose mulitilineorigin2_desc(-563.961, 215.359, -0.681, 2.845, -40.476, -87.443);
      DescTran mulitilineX2_desc;
      mulitilineX2_desc.x = -563.965;
      mulitilineX2_desc.y = 220.355;
      mulitilineX2_desc.z = -0.680;
      DescTran mulitilineZ2_desc;
      mulitilineZ2_desc.x = -563.968;
      mulitilineZ2_desc.y = 215.362;
      mulitilineZ2_desc.z = 4.331;
      ExaxisPos epos(0, 0, 0, 0);
      DescPose offset(0, 0, 0, 0, 0, 0);
      robot.Sleep(10);
      int error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.WeaveStart(0);
      printf("WeaveStart return: %d\n", error);
      error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
      printf("ArcWeldTraceControl return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 1, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
      printf("ArcWeldTraceControl return: %d\n", error);
      error = robot.WeaveEnd(0);
      printf("WeaveEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 10000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.ArcWeldTraceReplayStart();
      printf("ArcWeldTraceReplayStart return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceReplayEnd();
      printf("ArcWeldTraceReplayEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 10000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.ArcWeldTraceReplayStart();
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceReplayEnd();
      printf("ArcWeldTraceReplayEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 3000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      robot.CloseRPC();
      return 0;
    }

Selección del canal AI de retroalimentación de corriente de la máquina de soldar para el seguimiento de arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Selección del canal AI de retroalimentación de corriente de la máquina de soldar para el seguimiento de arco
     * @param [in]  channel Canal; 0-AI extendida 0; 1-AI extendida 1; 2-AI extendida 2; 3-AI extendida 3; 4-AI de la caja de control 0; 5-AI de la caja de control 1
     * @return Código de error
     */
     errno_t ArcWeldTraceAIChannelCurrent(int channel);

Selección del canal AI de retroalimentación de voltaje de la máquina de soldar para el seguimiento de arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Selección del canal AI de retroalimentación de voltaje de la máquina de soldar para el seguimiento de arco
     * @param [in]  channel Canal; 0-AI extendida 0; 1-AI extendida 1; 2-AI extendida 2; 3-AI extendida 3; 4-AI de la caja de control 0; 5-AI de la caja de control 1
     * @return Código de error
     */
     errno_t ArcWeldTraceAIChannelVoltage(int channel);

Parámetros de conversión de retroalimentación de corriente de la máquina de soldar para el seguimiento de arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     /**
      * @brief Parámetros de conversión de retroalimentación de corriente de la máquina de soldar para el seguimiento de arco
      * @param [in] AILow Límite inferior del canal AI, valor predeterminado 0V, rango [0-10V]
      * @param [in] AIHigh Límite superior del canal AI, valor predeterminado 10V, rango [0-10V]
      * @param [in] currentLow Valor de corriente de la máquina de soldar correspondiente al límite inferior del canal AI, valor predeterminado 0V, rango [0-200V]
      * @param [in] currentHigh Valor de corriente de la máquina de soldar correspondiente al límite superior del canal AI, valor predeterminado 100V, rango [0-200V]
      * @return Código de error
      */
     errno_t ArcWeldTraceCurrentPara(float AILow, float AIHigh, float currentLow, float currentHigh);

Parámetros de conversión de retroalimentación de voltaje de la máquina de soldar para el seguimiento de arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     /**
    * @brief Parámetros de conversión de retroalimentación de voltaje de la máquina de soldar para el seguimiento de arco
    * @param [in] AILow Límite inferior del canal AI, valor predeterminado 0V, rango [0-10V]
    * @param [in] AIHigh Límite superior del canal AI, valor predeterminado 10V, rango [0-10V]
    * @param [in] voltageLow Valor de voltaje de la máquina de soldar correspondiente al límite inferior del canal AI, valor predeterminado 0V, rango [0-200V]
    * @param [in] voltageHigh Valor de voltaje de la máquina de soldar correspondiente al límite superior del canal AI, valor predeterminado 100V, rango [0-200V]
    * @return Código de error
    */
    errno_t ArcWeldTraceVoltagePara(float AILow, float AIHigh, float voltageLow, float voltageHigh);

Ejemplo de código de seguimiento de arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int WeldTraceControlWithCtrlBoxAI(FRRobot* robot)
    {
      DescPose startdescPose = { -473.86, 257.879, -20.849, -37.317, -42.021, 2.543 };
      JointPos startjointPos = { -43.487, -76.526, 95.568, -104.445, -89.356, 3.72 };

      DescPose enddescPose = { -499.844, 141.225, 7.72, -34.856, -40.17, 13.13 };
      JointPos endjointPos = { -31.305, -82.998, 99.401, -104.426, -89.35, 3.696 };

      DescPose safedescPose = { -504.043, 275.181, 40.908, -28.002, -42.025, -14.044 };
      JointPos safejointPos = { -39.078, -76.732, 87.227, -99.47, -94.301, 18.714 };

      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };

      robot->WeldingSetCurrentRelation(0, 495, 1, 10, 0);
      robot->WeldingSetVoltageRelation(10, 45, 1, 10, 1);

      robot->WeldingSetVoltage(0, 25, 1, 0);// ----establecer voltaje
      robot->WeldingSetCurrent(0, 260, 0, 0);// ----establecer corriente

      int rtn = robot->ArcWeldTraceAIChannelCurrent(4);
      cout << "ArcWeldTraceAIChannelCurrent rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceAIChannelVoltage(5);
      cout << "ArcWeldTraceAIChannelVoltage rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceCurrentPara(0, 5, 0, 500);
      cout << "ArcWeldTraceCurrentPara rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceVoltagePara(1.018, 10, 0, 50);
      cout << "ArcWeldTraceVoltagePara rtn is " << rtn << endl;
      robot->MoveJ(&safejointPos, &safedescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot->MoveJ(&startjointPos, &startdescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      rtn = robot->ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      cout << "ArcWeldTraceControl rtn is " << rtn << endl;
      robot->ARCStart(0, 0, 10000);
      robot->WeaveStart(0);
      robot->MoveL(&endjointPos, &enddescPose, 1, 0, 100, 100, 2, -1, &exaxisPos, 0, 0, &offdese);
      robot->ARCEnd(0, 0, 10000);
      robot->WeaveEnd(0);
      robot->ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      return 0;
    }


Establecer el puerto IO extendido de búsqueda de posición del alambre de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el puerto IO extendido de búsqueda de posición del alambre de soldadura
    * @param searchDoneDINum Puerto DO de búsqueda de posición del alambre de soldadura exitosa (0-127)
    * @param searchStartDONum Puerto DO de control de inicio/parada de búsqueda de posición del alambre de soldadura (0-127)
    * @return Código de error
    */
    errno_t SetWireSearchExtDIONum(int searchDoneDINum, int searchStartDONum);

Programa de ejemplo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    void TestUDPWireSearch(FRRobot* robot)
    {
    robot->ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 50, 5, 50, 1, 50, 10);
    robot->ExtDevLoadUDPDriver();

    robot->SetWireSearchExtDIONum(0, 0);

    int rtn0, rtn1, rtn2 = 0;
    ExaxisPos exaxisPos = { 0.0, 0.0, 0.0, 0.0 };
    DescPose offdese = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
    
    DescPose descStart = { -158.767, -510.596, 271.709, -179.427, -0.745, -137.349 };
    JointPos jointStart = { 61.667, -79.848, 108.639, -119.682, -89.700, -70.985 };
    
    DescPose descEnd = { 0.332, -516.427, 270.688, 178.165, 0.017, -119.989 };
    JointPos jointEnd = { 79.021, -81.839, 110.752, -118.298, -91.729, -70.981 };

    robot->MoveL(&jointStart, &descStart, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->MoveL(&jointEnd, &descEnd, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    
    DescPose descREF0A = { -66.106, -560.746, 270.381, 176.479, -0.126, -126.745 };
    JointPos jointREF0A = { 73.531, -75.588, 102.941, -116.250, -93.347, -69.689 };
    
    DescPose descREF0B = { -66.109, -528.440, 270.407, 176.479, -0.129, -126.744 };
    JointPos jointREF0B = { 72.534, -79.625, 108.046, -117.379, -93.366, -70.687 };
    
    DescPose descREF1A = { 72.975, -473.242, 270.399, 176.479, -0.129, -126.744 };
    JointPos jointREF1A = { 87.169, -86.509, 115.710, -117.341, -92.993, -56.034 };
    
    DescPose descREF1B = { 31.355, -473.238, 270.405, 176.480, -0.130, -126.745 };
    JointPos jointREF1B = { 82.117, -87.146, 116.470, -117.737, -93.145, -61.090 };

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF0A, &descREF0A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punto de inicio
    robot->MoveL(&jointREF0B, &descREF0B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punto de dirección
    rtn1 = robot->WireSearchWait("REF0");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF1A, &descREF1A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punto de inicio
    robot->MoveL(&jointREF1B, &descREF1B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punto de dirección
    rtn1 = robot->WireSearchWait("REF1");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF0A, &descREF0A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punto de inicio
    robot->MoveL(&jointREF0B, &descREF0B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punto de dirección
    rtn1 = robot->WireSearchWait("RES0");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF1A, &descREF1A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punto de inicio
    robot->MoveL(&jointREF1B, &descREF1B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punto de dirección
    rtn1 = robot->WireSearchWait("RES1");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    vector <string> varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
    vector <string> varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
    int offectFlag = 0;
    DescPose offectPos = { 0, 0, 0, 0, 0, 0 };
    rtn0 = robot->GetWireSearchOffset(0, 0, varNameRef, varNameRes, offectFlag, offectPos);
    robot->PointsOffsetEnable(0, &offectPos);
    robot->MoveL(&jointStart, &descStart, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->MoveL(&jointEnd, &descEnd, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->PointsOffsetDisable();
    }

Inicio de búsqueda de posición del alambre de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief  Inicio de búsqueda de posición del alambre de soldadura
    * @param  [in] refPos  1-punto de referencia 0-punto de contacto
    * @param  [in] searchVel   Velocidad de búsqueda de posición %
    * @param  [in] searchDis  Distancia de búsqueda de posición mm
    * @param  [in] autoBackFlag Indicador de retorno automático, 0-no automático; 1-automático
    * @param  [in] autoBackVel  Velocidad de retorno automático %
    * @param  [in] autoBackDis  Distancia de retorno automático mm
    * @param  [in] offectFlag  1-búsqueda de posición con desplazamiento; 0-búsqueda de posición en punto de enseñanza
    * @return  Código de error
    */
     errno_t WireSearchStart(int refPos, float searchVel, int searchDis, int autoBackFlag, float autoBackVel, int autoBackDis, int offectFlag);

Fin de búsqueda de posición del alambre de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief  Fin de búsqueda de posición del alambre de soldadura
      * @param  [in] refPos  1-punto de referencia 2-punto de contacto
      * @param  [in] searchVel   Velocidad de búsqueda de posición %
      * @param  [in] searchDis  Distancia de búsqueda de posición mm
      * @param  [in] autoBackFlag Indicador de retorno automático, 0-no automático; 1-automático
      * @param  [in] autoBackVel  Velocidad de retorno automático %
      * @param  [in] autoBackDis  Distancia de retorno automático mm
      * @param  [in] offectFlag  1-búsqueda de posición con desplazamiento; 2-búsqueda de posición en punto de enseñanza
      * @return  Código de error
      */
     errno_t WireSearchEnd(int refPos, float searchVel, int searchDis, int autoBackFlag, float autoBackVel, int autoBackDis, int offectFlag);

Calcular la cantidad de desplazamiento de la búsqueda de posición del alambre de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief  Calcular la cantidad de desplazamiento de la búsqueda de posición del alambre de soldadura
      * @param  [in] seamType  Tipo de soldadura
      * @param  [in] method   Método de cálculo
      * @param  [in] varNameRef Punto de referencia 1-6, "#" indica que no hay variable de punto
      * @param  [in] varNameRes Punto de contacto 1-6, "#" indica que no hay variable de punto
      * @param  [out] offectFlag 0-la cantidad de desplazamiento se superpone directamente al punto de instrucción; 1-la cantidad de desplazamiento requiere transformación de coordenadas del punto de instrucción
      * @param  [out] offect Pose de desplazamiento [x, y, z, a, b, c]
      * @return  Código de error
      */
     errno_t GetWireSearchOffset(int seamType, int method, std::vector<std::string> varNameRef, std::vector<std::string> varNameRes, int& offectFlag, DescPose& offect);

Esperar a que finalice la búsqueda de posición del alambre de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

     /**
      * @brief  Esperar a que finalice la búsqueda de posición del alambre de soldadura
      * @return  Código de error
      */
     errno_t WireSearchWait(std::string varName);

Escribir el punto de contacto de la búsqueda de posición del alambre de soldadura en la base de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

     /**
      * @brief  Escribir el punto de contacto de la búsqueda de posición del alambre de soldadura en la base de datos
      * @param  [in] varName  Nombre del punto de contacto "RES0" ~ "RES99"
      * @param  [in] pos  Datos del punto de contacto [x, y, x, a, b, c]
      * @return  Código de error
      */
     errno_t SetPointToDatabase(std::string varName, DescPose pos);

Ejemplo de código de búsqueda de posición del alambre de soldadura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    int TestWireSearch(void)
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
      DescPose toolCoord(0, 0, 200, 0, 0, 0);
      robot.SetToolCoord(1, &toolCoord, 0, 0, 1, 0);
      DescPose wobjCoord(0, 0, 0, 0, 0, 0);
      robot.SetWObjCoord(1, &wobjCoord, 0);
      int rtn0, rtn1, rtn2 = 0;
      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      DescPose descStart = { 216.543, 445.175, 93.465, 179.683, 1.757, -112.641 };
      JointPos jointStart = { -128.345, -86.660, 114.679, -119.625, -89.219, 74.303 };
      DescPose descEnd = { 111.143, 523.384, 87.659, 179.703, 1.835, -97.750 };
      JointPos jointEnd = { -113.454, -81.060, 109.328, -119.954, -89.218, 74.302 };
      robot.MoveL(&jointStart, &descStart, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      robot.MoveL(&jointEnd, &descEnd, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      DescPose descREF0A = { 142.135, 367.604, 86.523, 179.728, 1.922, -111.089 };
      JointPos jointREF0A = { -126.794, -100.834, 128.922, -119.864, -89.218, 74.302 };
      DescPose descREF0B = { 254.633, 463.125, 72.604, 179.845, 2.341, -114.704 };
      JointPos jointREF0B = { -130.413, -81.093, 112.044, -123.163, -89.217, 74.303 };
      DescPose descREF1A = { 92.556, 485.259, 47.476, -179.932, 3.130, -97.512 };
      JointPos jointREF1A = { -113.231, -83.815, 119.877, -129.092, -89.217, 74.303 };
      DescPose descREF1B = { 203.103, 583.836, 63.909, 179.991, 2.854, -103.372 };
      JointPos jointREF1B = { -119.088, -69.676, 98.692, -121.761, -89.219, 74.303 };
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF0A, &descREF0A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punto de inicio
      robot.MoveL(&jointREF0B, &descREF0B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punto de dirección
      rtn1 = robot.WireSearchWait("REF0");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF1A, &descREF1A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punto de inicio
      robot.MoveL(&jointREF1B, &descREF1B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punto de dirección
      rtn1 = robot.WireSearchWait("REF1");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF0A, &descREF0A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punto de inicio
      robot.MoveL(&jointREF0B, &descREF0B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punto de dirección
      rtn1 = robot.WireSearchWait("RES0");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF1A, &descREF1A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //punto de inicio
      robot.MoveL(&jointREF1B, &descREF1B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //punto de dirección
      rtn1 = robot.WireSearchWait("RES1");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      vector <string> varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
      vector <string> varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
      int offectFlag = 0;
      DescPose offectPos = { 0, 0, 0, 0, 0, 0 };
      rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, offectFlag, offectPos);
      robot.PointsOffsetEnable(0, &offectPos);
      robot.MoveL(&jointStart, &descStart, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      robot.MoveL(&jointEnd, &descEnd, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese);
      robot.PointsOffsetDisable();
      robot.CloseRPC();
      return 0;

Establecer el inicio del cambio gradual de voltaje de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

     /**
    * @brief Establecer el inicio del cambio gradual de voltaje de soldadura
    * @param [in] IOType Tipo de control; 0-IO de la caja de control; 1-protocolo de comunicación digital (UDP); 2-protocolo de comunicación digital (ModbusTCP)
    * @param [in] voltageStart Voltaje de soldadura inicial (V)
    * @param [in] voltageEnd Voltaje de soldadura final (V)
    * @param [in] AOIndex Número de puerto AO de la caja de control (0-1)
    * @param [in] blend Si se suaviza 0-sin suavizado; 1-suavizado
    * @return Código de error
    */
    errno_t WeldingSetVoltageGradualChangeStart(int IOType, double voltageStart, double voltageEnd, int AOIndex, int blend);

Establecer el fin del cambio gradual de voltaje de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

     /**
      * @brief Establecer el fin del cambio gradual de voltaje de soldadura
      * @return Código de error
      */
     errno_t WeldingSetVoltageGradualChangeEnd();

Establecer el inicio del cambio gradual de corriente de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

     /**
      * @brief Establecer el inicio del cambio gradual de corriente de soldadura
      * @param [in] IOType Tipo de control; 0-IO de la caja de control; 1-protocolo de comunicación digital (UDP); 2-protocolo de comunicación digital (ModbusTCP)
      * @param [in] voltageStart Corriente de soldadura inicial (A)
      * @param [in] voltageEnd Corriente de soldadura final (A)
      * @param [in] AOIndex Número de puerto AO de la caja de control (0-1)
      * @param [in] blend Si se suaviza 0-sin suavizado; 1-suavizado
      * @return Código de error
      */
     errno_t WeldingSetCurrentGradualChangeStart(int IOType, double currentStart, double currentEnd, int AOIndex, int blend);

Establecer el fin del cambio gradual de corriente de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Establecer el fin del cambio gradual de corriente de soldadura
     * @return Código de error
     */
    errno_t WeldingSetCurrentGradualChangeEnd();
    
Ejemplo de código de cambio gradual de corriente y voltaje de soldadura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int WeldparamChange(FRRobot* robot)
    {
      DescPose startdescPose = { -484.707, 276.996, -14.013, -37.657, -40.508, -1.548 };
      JointPos startjointPos = { -45.421, -75.673, 93.627, -104.302, -87.938, 6.005 };
      
      DescPose enddescPose = { -508.767, 137.109, -13.966, -37.639, -40.508, -1.559 };
      JointPos endjointPos = { -32.768, -80.947, 100.254, -106.201, -87.201, 18.648 };

      DescPose safedescPose = { -484.709, 294.436, 13.621, -37.660, -40.508, -1.545 };
      JointPos safejointPos = { -46.604, -75.410, 89.109, -100.003, -88.012, 4.823 };
      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };

      robot->WeldingSetCurrentRelation(0, 495, 1, 10, 0);
      robot->WeldingSetVoltageRelation(10, 45, 1, 10, 1);
      robot->MoveJ(&safejointPos, &safedescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      int rtn = robot->WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0);
      cout << "WeldingSetCurrentGradualChangeStart rtn is " << rtn << endl;
      rtn = robot->WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0);
      cout << "WeldingSetVoltageGradualChangeStart rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      cout << "ArcWeldTraceControl rtn is " << rtn << endl;
      robot->MoveJ(&startjointPos, &startdescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      
      robot->ARCStart(0, 0, 10000);
      robot->WeaveStart(0);
      robot->WeaveChangeStart(2, 1, 24, 36);
      robot->MoveL(&endjointPos, &enddescPose, 1, 0, 100, 100, 2, -1, &exaxisPos, 0, 0, &offdese);
      robot->ARCEnd(0, 0, 10000);
      robot->WeaveChangeEnd();
      robot->WeaveEnd(0);
      robot->ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      robot->WeldingSetCurrentGradualChangeEnd();
      robot->WeldingSetVoltageGradualChangeEnd();
      return 0;
    }

Establecer los parámetros de oscilación personalizados
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer los parámetros de oscilación personalizados
    * @param [in] id Número de oscilación personalizada: 0-2
    * @param [in] pointNum Número de puntos de oscilación 0-10
    * @param [in] point Datos del punto final de movimiento x,y,z
    * @param [in] stayTime Tiempo de permanencia de la oscilación ms
    * @param [in] frequency Frecuencia de oscilación Hz
    * @param [in] incStayType Modo de espera: 0-el ciclo no incluye el tiempo de espera; 1-el ciclo incluye el tiempo de espera
    * @param [in] stationary Espera en la posición de oscilación: 0-continuar moviéndose durante el tiempo de espera; 1-permanecer estático durante el tiempo de espera
    * @return Código de error
    */
    errno_t CustomWeaveSetPara(int id, int pointNum, DescTran point[10], double stayTime[10], double frequency, int incStayType, int stationary);
                
Obtener los parámetros de oscilación personalizados
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener los parámetros de oscilación personalizados
    * @param [in] id Número de oscilación personalizada: 0-2
    * @param [out] pointNum Número de puntos de oscilación 0-10
    * @param [out] point Datos del punto final de movimiento x,y,z
    * @param [out] stayTime Tiempo de permanencia de la oscilación ms
    * @param [out] frequency Frecuencia de oscilación Hz
    * @param [out] incStayType Modo de espera: 0-el ciclo no incluye el tiempo de espera; 1-el ciclo incluye el tiempo de espera
    * @param [out] stationary Espera en la posición de oscilación: 0-continuar moviéndose durante el tiempo de espera; 1-permanecer estático durante el tiempo de espera
    * @return Código de error
    */
    errno_t CustomWeaveGetPara(int id, int& pointNum, DescTran point[10], double stayTime[10], double& frequency, int& incStayType, int& stationary);
                    
Ejemplo de código de parámetros de oscilación personalizados
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    int TestCustomWeaveSetPara()
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return 0;
      }
      robot.SetReConnectParam(true, 30000, 500);
      DescTran point[10] = {}; 
      point[0].x = -3;
      point[0].y = -3;
      point[0].z = 0;
      point[1].x = -6;
      point[1].y = 0;
      point[1].z = 0;
      point[2].x = -3;
      point[2].y = 3;
      point[2].z = 0;
      point[3].x = 0;
      point[3].y = 0;
      point[3].z = 0;
      double stayTime[10] = { 0,0,0,0,0,0,0,0,0,0 };
      rtn = robot.CustomWeaveSetPara(2, 4, point, stayTime, 1.000, 0, 0);
      printf("CustomWeaveSetPara rtn is %d\n", rtn);
      robot.Sleep(1000);
      int pointNum = 0;
      double frequency;
      int incStayType;
      int stationary;
      robot.CustomWeaveGetPara(2, pointNum, point, stayTime, frequency, incStayType, stationary);
      printf("pointNum is %d\n", pointNum);
      for (int i = 0; i < pointNum; i++)
      {
        printf("point %d, point x y z %f %f %f\n", i, point[i].x, point[i].y, point[i].z);
      }
      printf("fre is %f, stay is %d %d \n", frequency, incStayType, stationary);
      robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000);
      DescPose desc_p1 = { -288.650, 367.807, 288.404, 0.000, -0.001, 0.001 };
      DescPose desc_p2 = { -431.714, 367.815, 288.415, 0.001, 0.001, 0.000 };
      DescPose desc_p3 = { -348.666, 427.798, 288.404, -0.000, -0.000, 0.001 };
      JointPos j1 = { 140.656, -84.560, -91.707, -93.734, 90.000, 50.655 };
      JointPos j2 = { 149.873, -98.298, -77.599, -94.103, 90.000, 59.873 };
      JointPos j3 = { 139.773, -96.173, -80.014, -93.814, 90.000, 49.772 };
      ExaxisPos epos = {};
      DescPose offset_pos = {};
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.Circle(&j3, &desc_p3, 3, 0, 100, 100, &epos, &j2, &desc_p2, 3, 0, 100, 100, &epos, 10, -1, &offset_pos);
      robot.WeaveEnd(0);
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.MoveC(&j3, &desc_p3, 3, 0, 100, 100, &epos, 0, &offset_pos, &j2, &desc_p2, 3, 0, 100, 100, &epos, 0, &offset_pos, 10, -1); 
      robot.WeaveEnd(0);
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.MoveL(&j2, &desc_p2, 3, 0, 100, 100, 10, -1, &epos, 0, 0, &offset_pos, 0, 100);
      robot.WeaveEnd(0);
      robot.CloseRPC();
    }
                    
Configuración de parámetros de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configuración de parámetros de la máquina de soldadura láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[in] num Número de grupo a configurar (1~10)
    * @param[in] scanSpeed Velocidad de escaneo
    * @param[in] scanWidth Ancho de escaneo
    * @param[in] peakPower Potencia pico
    * @param[in] dutyCycle Ciclo de trabajo
    * @param[in] freq Frecuencia
    * @return Código de error
    */
    errno_t SetLaserWeldingParam(int io_type, int num, int scanSpeed, int scanWidth, int peakPower, int dutyCycle, int freq);
                        
Establecer el inicio y la parada de la soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el inicio y la parada de la soldadura láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[in] status Palabra de control 0-recepción de luz 1-emisión de luz
    * @param[in] max_waittime Tiempo máximo de espera, unidad milisegundos, por defecto 10000
    * @return Código de error
    */
    errno_t SetLaserWeldingStartEnd(int io_type, int status, int max_waittime = 10000);
                        
Habilitación y deshabilitación de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Habilitación y deshabilitación de la máquina de soldadura láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[in] status 0-deshabilitar 1-habilitar
    * @return Código de error
    */
    errno_t SetLaserWeldingEnable(int io_type, int status);

Reinicio de fallos de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Reinicio de fallos de la máquina de soldadura láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[in] status Palabra de control 0-inválido 1-reinicio de fallos
    * @return Código de error
    */
    errno_t ResetLaserWeldingErr(int io_type, int status);

Obtener el estado de funcionamiento de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado de funcionamiento de la máquina de soldadura láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[out] status Palabra de control 0-parada 1-en funcionamiento
    * @return Código de error
    */
    errno_t GetLaserWeldingRunningState(int io_type, int& status);

Obtener el estado de fallo de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado de fallo de la máquina de soldadura láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[out] status 0-sin fallo 1-con fallo
    * @return Código de error
    */
    errno_t GetLaserWeldingErrState(int io_type, int& status);
    
Obtener los parámetros de configuración de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener los parámetros de configuración de la máquina de soldadura láser
    * @param[in] num Número de grupo a configurar (1~10)
    * @param[out] scanSpeed Velocidad de escaneo
    * @param[out] scanWidth Ancho de escaneo
    * @param[out] peakPower Potencia pico
    * @param[out] dutyCycle Ciclo de trabajo
    * @param[out] freq Frecuencia
    * @return Código de error
    */
    errno_t GetLaserWeldingParamTarget(int num, int& scanSpeed, int& scanWidth, int& peakPower, int& dutyCycle, int& freq);

Obtener los parámetros de configuración vigentes actualmente de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener los parámetros de configuración vigentes actualmente de la máquina de soldadura láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[out] scanSpeed Velocidad de escaneo
    * @param[out] scanWidth Ancho de escaneo
    * @param[out] peakPower Potencia pico
    * @param[out] dutyCycle Ciclo de trabajo
    * @param[out] freq Frecuencia
    * @return Código de error, 0 indica éxito, distinto de 0 indica fallo
    */
    errno_t GetLaserWeldingParamActual(int io_type, int& scanSpeed, int& scanWidth, int& peakPower, int& dutyCycle, int& freq);

Configurar el puerto DO extendido de habilitación de IO de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configurar el puerto DO extendido de habilitación de IO de la máquina de soldadura láser
    * @param[in] ctrlModeDONum Número de puerto DO extendido de habilitación de la máquina de soldadura láser
    * @return Código de error, 0 indica éxito, distinto de 0 indica fallo
    */
    errno_t SetLaserWeldingEnableExtDoNum(int ctrlModeDONum);

Configurar el puerto DO extendido de inicio de IO de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configurar el puerto DO extendido de inicio de IO de la máquina de soldadura láser
    * @param[in] ctrlModeDONum Número de puerto DO extendido de inicio (emisión y recepción de luz) de la máquina de soldadura láser
    * @return Código de error, 0 indica éxito, distinto de 0 indica fallo
    */
    errno_t SetLaserWeldingStartExtDoNum(int ctrlModeDONum);

Configurar el puerto DO extendido de reinicio de fallos de IO de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configurar el puerto DO extendido de reinicio de fallos de IO de la máquina de soldadura láser
    * @param[in] ctrlModeDONum Número de puerto DO extendido de reinicio de fallos de la máquina de soldadura láser
    * @return Código de error, 0 indica éxito, distinto de 0 indica fallo
    */
    errno_t SetLaserWeldingErrResetExtDoNum(int ctrlModeDONum);
    
Configurar el puerto DI extendido del estado de funcionamiento (estado de emisión de luz) de IO de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configurar el puerto DI extendido del estado de funcionamiento (estado de emisión de luz) de IO de la máquina de soldadura láser
    * @param[in] diNum Configurar el puerto DI extendido del estado de funcionamiento (estado de emisión de luz) de la máquina de soldadura láser
    * @return Código de error, 0 indica éxito, distinto de 0 indica fallo
    */
    errno_t SetLaserWeldingRunningStateExtDiNum(int diNum);
    
Configurar el puerto DI extendido del estado de fallo de IO de la máquina de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configurar el puerto DI extendido del estado de fallo de IO de la máquina de soldadura láser
    * @param[in] diNum Configurar el puerto DI extendido del estado de fallo de la máquina de soldadura láser
    * @return Código de error, 0 indica éxito, distinto de 0 indica fallo
    */
    errno_t SetLaserWeldingErrStateExtDiNum(int diNum);
        
Ejemplo de código de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestLaserWeld()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 300000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        rtn = robot.ExtDevLoadUDPDriver();
        if (rtn != 0) 
        {
            std::cout << "Failed to load UDP driver, error code: " << rtn << std::endl;
        }
        robot.Sleep(1000);
        rtn = robot.SetLaserWeldingParam(1, 3, 2000, 3, 1500, 100, 1000);
        if (rtn != 0) 
        {
            std::cout << "SetLaserWeldingParam failed, error code: " << rtn << std::endl;
        }
        else 
        {
            std::cout << "SetLaserWeldingParam success" << std::endl;
        }
        rtn = robot.SetLaserWeldingStartExtDoNum(1);
        if (rtn != 0) 
        {
            std::cout << "SetLaserWeldingStartExtDoNum failed, error code: " << rtn << std::endl;
        }
        rtn = robot.Mode(0);
        if (rtn != 0) 
        {
            std::cout << "Set mode 0 failed, error code: " << rtn << std::endl;
        }
        robot.Sleep(1000);
        DescPose desc_pos1(-303.721, -206.960, 297.105, 152.209, 19.857, 109.166);
        DescPose desc_pos2(-301.575, -254.888, 284.786, 155.919, 26.946, 111.629);
        DescPose desc_safe(-344.386, -280.830, 435.073, 173.835, 15.333, 124.931);
        JointPos jointPos1(9.827, -99.740, 120.088, -78.900, -77.241, -17.904);
        JointPos jointPos2(15.251, -96.456, 120.138, -84.664, -68.542, -17.843);
        JointPos jointSafe(19.142, -98.078, 101.493, -83.078, -77.070, -17.794);
        ExaxisPos exaxis(0.0, 0.0, 0.0, 0.0);
        DescPose offset(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int error = robot.MoveL(&desc_pos1,0, 0, 100, 100, 100, -1, 0, &exaxis, 0, 0, &offset, -1, 0);
        std::cout << "MoveL to pos1 return: " << error << std::endl;
        rtn = robot.SetLaserWeldingStartEnd(1, 1, 10000);
        if (rtn != 0)
        {
            std::cout << "SetLaserWeldingStartEnd (start) failed, error code: " << rtn << std::endl;
        }
        else 
        {
            std::cout << "Laser started" << std::endl;
        }
        rtn = robot.MoveL(&desc_pos2,0, 0, 30, 100, 100, -1, 0, &exaxis, 0, 0, &offset, -1, 0);
        std::cout << "MoveL to pos2 return: " << rtn << std::endl;
        rtn = robot.SetLaserWeldingStartEnd(1, 0, 10000);
        if (rtn != 0)
        {
            std::cout << "SetLaserWeldingStartEnd (stop) failed, error code: " << rtn << std::endl;
        }
        else 
        {
            std::cout << "Laser stopped" << std::endl;
        }
        robot.Sleep(500);
        rtn = robot.MoveL(&desc_safe, 0, 0, 100, 100, 100, -1, 0, &exaxis, 0, 0, &offset, -1, 0);
        std::cout << "MoveL to safe_pos return: " << rtn << std::endl;
        rtn = robot.Mode(1);
        if (rtn != 0) 
        {
            std::cout << "Set mode 1 failed, error code: " << rtn << std::endl;
        }
        robot.Sleep(1000);
        robot.CloseRPC();
        robot.Sleep(1000);
        std::cout << "Test completed" << std::endl;
        return 0;
    }
            
Establecer el retorno al punto cero del ciclo al final de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el retorno al punto cero del ciclo al final de la oscilación
    * @param [in] flag Si al final de la oscilación se retorna al punto cero del ciclo; 0-no retornar al punto cero del ciclo; 1-retornar al punto cero del ciclo
    * @return Código de error
    */
    errno_t SetWeaveBackCenterConfig(int flag);
            
Obtener el parámetro de retorno al punto cero del ciclo al final de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el parámetro de retorno al punto cero del ciclo al final de la oscilación
    * @param [out] flag Si al final de la oscilación se retorna al punto cero del ciclo; 0-no retornar al punto cero del ciclo; 1-retornar al punto cero del ciclo
    * @return Código de error
    */
    errno_t GetWeaveBackCenterConfig(int& flag);
            
Ejemplo de código de retorno al punto cero del ciclo al final de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestSplineWeaveBackCenter()
    {
    ROBOT_STATE_PKG pkg = {};
    FRRobot robot;
    robot.LoggerInit();
    robot.SetLoggerLevel(1);
    robot.SetReConnectParam(true, 30000, 500);
    int rtn = robot.SetCmdRpyCallback(UDPFrameCallBack);
    printf("SetCmdRpyCallback rtn is %d\n", rtn);
    rtn = robot.RPC("192.168.58.2");
    if (rtn != 0)
    {
        return -1;
    }
    JointPos j1(9.000, -66.067, 67.706, -103.217, -90.151, 100.669);
    JointPos j2(-4.660, -107.973, 103.734, -76.214, -89.999, 90.886);
    JointPos j3(-36.762, -77.380, 91.364, -127.159, -90.024, 54.833);
    JointPos j4(-62.875, -89.460, 86.437, -77.030, -90.012, 31.539);
    DescPose desc_pos1(-654.129, -235.344, 246.543, 6.010, -11.535, -176.787);
    DescPose desc_pos2(-273.710, -100.871, 280.935, 5.692, 9.522, 179.512);
    DescPose desc_pos3(-566.093, 311.278, 215.008, -10.453, -17.486, -174.209);
    DescPose desc_pos4(-246.558, 328.240, 292.173, 13.912, 4.437, -179.067);
    DescPose offset_pos(0, 0, 0, 0, 0, 0);
    ExaxisPos epos(0, 0, 0, 0);
    int tool = 2;
    int user = 0;
    float vel = 100.0;
    float acc = 100.0;
    float ovl = 20;
    float oacc = 100.0;
    float blendT = 0.0;
    float blendR = 0.0;
    uint8_t flag = 0;
    uint8_t search = 0;
    int blendMode = 0;
    int velAccMode = 0;
    robot.SetSpeed(1);
    robot.SetWeaveBackCenterConfig(1);
    int weaveBackConfig = 0;
    robot.GetWeaveBackCenterConfig(weaveBackConfig);
    printf("GetWeavebackCenterConfig %d: \n", weaveBackConfig);
    rtn = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, 100.0, &epos, blendT, flag, &offset_pos);
    robot.WeaveStart(0);
    robot.NewSplineStart(0, 6000);
    robot.NewSplinePoint(&j1, &desc_pos1, tool, user, vel, acc, ovl, -1, 0);
    robot.NewSplinePoint(&j2, &desc_pos2, tool, user, vel, acc, ovl, -1, 0);
    robot.NewSplinePoint(&j3, &desc_pos3, tool, user, vel, acc, ovl, -1, 0);
    robot.NewSplinePoint(&j4, &desc_pos4, tool, user, vel, acc, ovl, -1, 1);
    robot.NewSplineEnd();
    }

Establecer el desplazamiento en tiempo real de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el desplazamiento en tiempo real de la oscilación
    * @param [in] offset Desplazamiento en tiempo real [mm, °]
    * @return Código de error
    */
    errno_t SetWeaveOffsetRT(DescPose offset);

Ejemplo de código de regulación de velocidad y desplazamiento en tiempo real de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestWeaveSpeedAndOffset()
    {
    ROBOT_STATE_PKG pkg = {};
    FRRobot robot;
    robot.LoggerInit();
    robot.SetLoggerLevel(1);
    robot.SetReConnectParam(true, 30000, 500);
    int rtn = robot.RPC("192.168.58.2");
    if (rtn != 0)
    {
        return 0;
    }
        std::cout << "============================================================" << std::endl;
    std::cout << " Prueba de regulación de velocidad y desplazamiento en tiempo real de la oscilación" << std::endl;
    std::cout << "============================================================" << std::endl;
    ExaxisPos epos(0, 0, 0, 0);
    DescPose offset_pos(0, 0, 0, 0, 0, 0);
    JointPos j1(5.027, -84.331, -75.139, -103.690, 86.379, 20.794);
    DescPose d1(324.752, -83.339, 366.314, -172.321, -0.936, -106.047);
    JointPos j2(-35.335, -117.598, -57.174, -95.234, 90.001, -19.560);
    DescPose d2(324.999, -355.439, 260.000, 179.995, 0.003, -105.775);
    JointPos j3(59.787, -117.594, -57.183, -95.222, 90.006, 75.562);
    DescPose d3(324.998, 355.441, 260.002, 179.995, 0.003, -105.775);
    // ---- Paso 1: MoveJ al punto de inicio ----
    std::cout << "\nPaso 1: MoveJ al punto de inicio" << std::endl;
    rtn = robot.MoveJ(&j1, &d1, 1, 0, 100, 100, 50, &epos, -1, 0, &offset_pos);
    std::cout << " MoveJ(j1) rtn=" << rtn << std::endl;
    std::this_thread::sleep_for(std::chrono::milliseconds(500));
    // ---- Paso 2: MoveJ al punto de entrada de la oscilación ----
    std::cout << "\nPaso 2: MoveJ al punto de entrada de la oscilación" << std::endl;
    rtn = robot.MoveJ(&j2, &d2, 1, 0, 100, 100, 50, &epos, -1, 0, &offset_pos);
    std::cout << " MoveJ(j2) rtn=" << rtn << std::endl;
    std::this_thread::sleep_for(std::chrono::milliseconds(500));
    // ---- Paso 3: WeaveStart, iniciar el hilo de MoveL de oscilación ----
    std::cout << "\nPaso 3: WeaveStart + MoveL en hilo en segundo plano" << std::endl;
    robot.WeaveStart(0);
    std::atomic<bool> weaveRunning(true);
    std::thread weaveThread([&]() {
        rtn = robot.MoveL(&j3, &d3, 1, 0, 100, 100, 5, -1, 0, &epos, 0, 0, &offset_pos, 5, 0, 0, 10);
        std::cout << " MoveL(weave) thread finished, rtn=" << rtn << std::endl;
        weaveRunning = false;
        });
    weaveThread.detach(); // ejecución en segundo plano
    std::this_thread::sleep_for(std::chrono::milliseconds(500)); // esperar a que comience el movimiento
    // ---- Paso 4: Prueba de regulación de velocidad (hilo principal, MoveL de oscilación en segundo plano) ----
    std::cout << "\nPaso 4: Prueba de SetSpeed durante la oscilación" << std::endl;
    std::vector<int> speedValues = { 20, 50, 80, 30, 60, 10 };
    for (int speed : speedValues)
    {
        if (!weaveRunning.load()) break;
        rtn = robot.SetSpeedInstant(speed);
        robot.GetRobotRealTimeState(&pkg);
        std::cout << " SetSpeed(" << speed << ") -> rtn=" << rtn
        << ", TCP_CmpSpeed=" << pkg.target_TCP_CmpSpeed << std::endl;
        std::this_thread::sleep_for(std::chrono::milliseconds(5000));
    }
    std::this_thread::sleep_for(std::chrono::milliseconds(5000));
    // ---- Paso 5: Prueba de desplazamiento SetWeaveOffsetRT (hilo principal, MoveL de oscilación en segundo plano) ----
    std::cout << "\nPaso 5: Prueba de SetWeaveOffsetRT (50 iteraciones, delta=0.1)" << std::endl;
    double accumOffset = 0.0;
    for (int i = 0; i < 50 && weaveRunning.load(); i++)
    {
        accumOffset += 1;
        DescPose weaveOffset(0, 0, accumOffset, 0, 0, 0);
        rtn = robot.SetWeaveOffsetRT(weaveOffset);
        robot.GetRobotRealTimeState(&pkg);
        std::cout << " [" << (i + 1) << "/50] SetWeaveOffsetRT(x=" << accumOffset << ") -> rtn=" << rtn
        << ", TCP_pos=(" << pkg.tl_cur_pos[0] << "," << pkg.tl_cur_pos[1] << "," << pkg.tl_cur_pos[2] << ")"
        << std::endl;
        std::this_thread::sleep_for(std::chrono::milliseconds(200));
    }
    // ---- Paso 6: Esperar a que finalice el MoveL de oscilación, WeaveEnd ----
    std::cout << "\nPaso 6: Esperar a que finalice el MoveL de oscilación, luego WeaveEnd" << std::endl;
    // Dado que se usó detach, es necesario esperar a que weaveRunning cambie a false
    while (weaveRunning.load()) 
    {
        std::this_thread::sleep_for(std::chrono::milliseconds(100));
    }
    robot.WeaveEnd(0);
    std::this_thread::sleep_for(std::chrono::milliseconds(500));
    // ---- Paso 7: MoveL de regreso al punto de inicio ----
    std::cout << "\nPaso 7: MoveL de regreso al inicio" << std::endl;
    rtn = robot.MoveL(&j1, &d1, 1, 0, 100, 100, 50, -1, 0, &epos, 0, 0, &offset_pos, 50, 0, 0, 10);
    std::cout << " MoveL(back) rtn=" << rtn << std::endl;
    robot.GetRobotRealTimeState(&pkg);
    std::cout << "\n Estado final del robot: main_code=" << pkg.main_code
        << ", sub_code=" << pkg.sub_code << std::endl;
    std::cout << "============================================================" << std::endl;
    std::cout << " Prueba de regulación de velocidad y desplazamiento en tiempo real de la oscilación completada" << std::endl;
    std::cout << "============================================================" << std::endl;
    }