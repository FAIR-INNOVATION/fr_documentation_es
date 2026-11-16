Soldadura del robot
===================

.. toctree:: 
    :maxdepth: 5

Establecer los parámetros de la curva del proceso de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer los parámetros de la curva del proceso de soldadura
    * @param  [in] id Número del proceso de soldadura (1-99)
    * @param  [in] startCurrent Corriente de inicio de arco (A)
    * @param  [in] startVoltage Tensión de inicio de arco (V)
    * @param  [in] startTime Tiempo de inicio de arco (ms)
    * @param  [in] weldCurrent Corriente de soldadura (A)
    * @param  [in] weldVoltage Tensión de soldadura (V)
    * @param  [in] endCurrent Corriente de cierre de arco (A)
    * @param  [in] endVoltage Tensión de cierre de arco (V)
    * @param  [in] endTime Tiempo de cierre de arco (ms)
    * @return  Código de error
    */
    int WeldingSetProcessParam(int id, double startCurrent, double startVoltage, double startTime, double weldCurrent, double weldVoltage, double endCurrent, double endVoltage, double endTime);

Obtener los parámetros de la curva del proceso de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener los parámetros de la curva del proceso de soldadura
    * @param  [in] id Número del proceso de soldadura (1-99)
    * @param  [out] startCurrent Corriente de inicio de arco (A)
    * @param  [out] startVoltage Tensión de inicio de arco (V)
    * @param  [out] startTime Tiempo de inicio de arco (ms)
    * @param  [out] weldCurrent Corriente de soldadura (A)
    * @param  [out] weldVoltage Tensión de soldadura (V)
    * @param  [out] endCurrent Corriente de cierre de arco (A)
    * @param  [out] endVoltage Tensión de cierre de arco (V)
    * @param  [out] endTime Tiempo de cierre de arco (ms)
    * @return  Código de error
    */
    int WeldingGetProcessParam(int id, ref double startCurrent, ref double startVoltage, ref double startTime, ref double weldCurrent, ref double weldVoltage, ref double endCurrent, ref double endVoltage, ref double endTime);

Establecer la relación entre la corriente de soldadura y la salida analógica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la relación entre la corriente de soldadura y la salida analógica
    * @param [in] currentMin Valor de corriente del punto izquierdo de la relación lineal corriente de soldadura-salida analógica (A)
    * @param [in] currentMax Valor de corriente del punto derecho de la relación lineal corriente de soldadura-salida analógica (A)
    * @param [in] outputVoltageMin Valor de tensión de salida analógica del punto izquierdo de la relación lineal corriente de soldadura-salida analógica (V)
    * @param [in] outputVoltageMax Valor de tensión de salida analógica del punto derecho de la relación lineal corriente de soldadura-salida analógica (V)
    * @return Código de error
    */
    int WeldingSetCurrentRelation(double currentMin, double currentMax, double outputVoltageMin, double outputVoltageMax);

Establecer la relación entre la tensión de soldadura y la salida analógica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la relación entre la tensión de soldadura y la salida analógica
    * @param [in] weldVoltageMin Valor de tensión de soldadura del punto izquierdo de la relación lineal tensión de soldadura-salida analógica (A)
    * @param [in] weldVoltageMax Valor de tensión de soldadura del punto derecho de la relación lineal tensión de soldadura-salida analógica (A)
    * @param [in] outputVoltageMin Valor de tensión de salida analógica del punto izquierdo de la relación lineal tensión de soldadura-salida analógica (V)
    * @param [in] outputVoltageMax Valor de tensión de salida analógica del punto derecho de la relación lineal tensión de soldadura-salida analógica (V)
    * @return Código de error
    */
    int WeldingSetVoltageRelation(double weldVoltageMin, double weldVoltageMax, double outputVoltageMin, double outputVoltageMax);

Obtener la relación entre la corriente de soldadura y la salida analógica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la relación entre la corriente de soldadura y la salida analógica
    * @param [out] currentMin Valor de corriente del punto izquierdo de la relación lineal corriente de soldadura-salida analógica (A)
    * @param [out] currentMax Valor de corriente del punto derecho de la relación lineal corriente de soldadura-salida analógica (A)
    * @param [out] outputVoltageMin Valor de tensión de salida analógica del punto izquierdo de la relación lineal corriente de soldadura-salida analógica (V)
    * @param [out] outputVoltageMax Valor de tensión de salida analógica del punto derecho de la relación lineal corriente de soldadura-salida analógica (V)
    * @return Código de error
    */
    int WeldingGetCurrentRelation(ref double currentMin, ref double currentMax, ref double outputVoltageMin, ref double outputVoltageMax);

Obtener la relación entre la tensión de soldadura y la salida analógica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la relación entre la tensión de soldadura y la salida analógica
    * @param [out] weldVoltageMin Valor de tensión de soldadura del punto izquierdo de la relación lineal tensión de soldadura-salida analógica (A)
    * @param [out] weldVoltageMax Valor de tensión de soldadura del punto derecho de la relación lineal tensión de soldadura-salida analógica (A)
    * @param [out] outputVoltageMin Valor de tensión de salida analógica del punto izquierdo de la relación lineal tensión de soldadura-salida analógica (V)
    * @param [out] outputVoltageMax Valor de tensión de salida analógica del punto derecho de la relación lineal tensión de soldadura-salida analógica (V)
    * @return Código de error
    */
    int WeldingGetVoltageRelation(ref double weldVoltageMin, ref double weldVoltageMax, ref double outputVoltageMin, ref double outputVoltageMax);

Establecer la corriente de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la corriente de soldadura
    * @param [in] ioType Tipo de IO de control 0-IO del armario de control; 1-IO extendida
    * @param [in] current Valor de corriente de soldadura (A)
    * @param [in] AOIndex Puerto de salida analógica del armario de control de corriente de soldadura (0-1)
    * @return Código de error
    */
    int WeldingSetCurrent(int ioType, double current, int AOIndex);

Establecer la tensión de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la tensión de soldadura
    * @param [in] ioType Tipo de IO de control 0-IO del armario de control; 1-IO extendida
    * @param [in] voltage Valor de tensión de soldadura (A)
    * @param [in] AOIndex Puerto de salida analógica del armario de control de tensión de soldadura (0-1)
    * @return Código de error
    */
    int WeldingSetVoltage(int ioType, double voltage, int AOIndex);

Establecer los parámetros de oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /** 
    * @brief Establecer los parámetros de oscilación
    * @param [in] weaveNum Número de configuración de parámetros de soldadura oscilante
    * @param [in] weaveType Tipo de oscilación: 0-oscilación triangular plana; 1-oscilación triangular tipo L vertical; 2-oscilación circular en sentido horario; 3-oscilación circular en sentido antihorario; 4-oscilación sinusoidal plana; 5-oscilación sinusoidal tipo L vertical; 6-oscilación triangular vertical; 7-oscilación sinusoidal vertical
    * @param [in] weaveFrequency Frecuencia de oscilación (Hz)
    * @param [in] weaveIncStayTime Modo de espera: 0-el ciclo no incluye tiempo de espera; 1-el ciclo incluye tiempo de espera
    * @param [in] weaveRange Amplitud de oscilación (mm)
    * @param [in] weaveLeftRange Longitud del lado izquierdo de la oscilación triangular vertical (mm)
    * @param [in] weaveRightRange Longitud del lado derecho de la oscilación triangular vertical (mm)
    * @param [in] additionalStayTime Tiempo de permanencia en el vértice de la oscilación triangular vertical (mm)
    * @param [in] weaveLeftStayTime Tiempo de permanencia izquierdo de la oscilación (ms)
    * @param [in] weaveRightStayTime Tiempo de permanencia derecho de la oscilación (ms)
    * @param [in] weaveCircleRadio Oscilación circular - relación de retorno (0-100%)
    * @param [in] weaveStationary Espera en la posición de oscilación: 0-durante el tiempo de espera la posición continúa moviéndose; 1-durante el tiempo de espera la posición permanece estática
    * @param [in] weaveYawAngle Ángulo de orientación de la dirección de oscilación (rotación alrededor del eje Z de oscilación), unidad °
    * @return Código de error 
    */
    int WeaveSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, double weaveLeftRange, double weaveRightRange, int additionalStayTime, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary, double weaveYawAngle, double weaveRotAngle=0);

Ejemplo de código de configuración de parámetros de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V3.9.8
    
.. code-block:: c#
    :linenos:

    private void button42_Click(object sender, EventArgs e)
    {
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

        robot.WeldingGetProcessParam(1, ref startCurrent, ref startVoltage, ref startTime, ref weldCurrent, ref weldVoltage, ref endCurrent, ref endVoltage, ref endTime);
        Console.WriteLine("the Num 1 process param is " + startCurrent + " " + startVoltage + " " + startTime + " " + weldCurrent + " " + weldVoltage + " " + endCurrent + " " + endVoltage + " " + endTime);
        robot.WeldingGetProcessParam(2, ref startCurrent, ref startVoltage, ref startTime, ref weldCurrent, ref weldVoltage, ref endCurrent, ref endVoltage, ref endTime);
        Console.WriteLine("the Num 2 process param is " + startCurrent + " " + startVoltage + " " + startTime + " " + weldCurrent + " " + weldVoltage + " " + endCurrent + " " + endVoltage + " " + endTime);

        int rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0);
        Console.WriteLine("WeldingSetCurrentRelation rtn is: " + rtn);

        rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1);
        Console.WriteLine("WeldingSetVoltageRelation rtn is: " + rtn);

        double current_min = 0;
        double current_max = 0;
        double vol_min = 0;
        double vol_max = 0;
        double output_vmin = 0;
        double output_vmax = 0;
        int curIndex = 0;
        int volIndex = 0;
        rtn = robot.WeldingGetCurrentRelation(ref current_min, ref current_max, ref output_vmin, ref output_vmax, ref curIndex);
        Console.WriteLine("WeldingGetCurrentRelation rtn is: " + rtn);
        Console.WriteLine("current min " + current_min + " current max " + current_max + " output vol min " + output_vmin + " output vol max " + output_vmax);

        rtn = robot.WeldingGetVoltageRelation(ref vol_min, ref vol_max, ref output_vmin, ref output_vmax, ref volIndex);
        Console.WriteLine("WeldingGetVoltageRelation rtn is: " + rtn);
        Console.WriteLine("vol min " + vol_min + " vol max " + vol_max + " output vol min " + output_vmin + " output vol max " + output_vmax);

        rtn = robot.WeldingSetCurrent(1, 100, 0, 0);
        Console.WriteLine("WeldingSetCurrent rtn is: " + rtn);

        System.Threading.Thread.Sleep(3000);

        rtn = robot.WeldingSetVoltage(1, 10, 0, 0);
        Console.WriteLine("WeldingSetVoltage rtn is: " + rtn);

        rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0, 60.000000);
        Console.WriteLine("rtn is: " + rtn);

        robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0);

        rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200);
        Console.WriteLine("WeldingSetCheckArcInterruptionParam    " + rtn);
        rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0);
        Console.WriteLine("WeldingSetReWeldAfterBreakOffParam    " + rtn);
        int enable = 0;
        double length = 0;
        double velocity = 0;
        int moveType = 0;
        int checkEnable = 0;
        int arcInterruptTimeLength = 0;
        rtn = robot.WeldingGetCheckArcInterruptionParam(ref checkEnable, ref arcInterruptTimeLength);
        Console.WriteLine("WeldingGetCheckArcInterruptionParam  checkEnable  " + checkEnable + "   arcInterruptTimeLength  " + arcInterruptTimeLength);
        rtn = robot.WeldingGetReWeldAfterBreakOffParam(ref enable, ref length, ref velocity, ref moveType);
        Console.WriteLine("WeldingGetReWeldAfterBreakOffParam  enable = " + enable + ", length = " + length + ", velocity = " + velocity + ", moveType = " + moveType);

        robot.SetWeldMachineCtrlModeExtDoNum(17);
        for (int i = 0; i < 5; i++)
        {
            int getCtrlMode = -1;
            robot.SetWeldMachineCtrlMode(0);
            robot.GetWeldMachineCtrlMode(ref getCtrlMode);
            Console.WriteLine("GetWeldMachineCtrlMode {0}", getCtrlMode);
            Thread.Sleep(1000);
            robot.SetWeldMachineCtrlMode(1);
            robot.GetWeldMachineCtrlMode(ref getCtrlMode);
            Console.WriteLine("GetWeldMachineCtrlMode {0}", getCtrlMode);
            Thread.Sleep(1000);
        }
    }

Establecer los parámetros de oscilación en tiempo real
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer los parámetros de oscilación en tiempo real
    * @param [in] weaveNum Número de configuración de parámetros de soldadura oscilante
    * @param [in] weaveType Tipo de oscilación: 0-oscilación triangular plana; 1-oscilación triangular tipo L vertical; 2-oscilación circular en sentido horario; 3-oscilación circular en sentido antihorario; 4-oscilación sinusoidal plana; 5-oscilación sinusoidal tipo L vertical; 6-oscilación triangular vertical; 7-oscilación sinusoidal vertical
    * @param [in] weaveFrequency Frecuencia de oscilación (Hz)
    * @param [in] weaveIncStayTime Modo de espera: 0-el ciclo no incluye tiempo de espera; 1-el ciclo incluye tiempo de espera
    * @param [in] weaveRange Amplitud de oscilación (mm)
    * @param [in] weaveLeftStayTime Tiempo de permanencia izquierdo de la oscilación (ms)
    * @param [in] weaveRightStayTime Tiempo de permanencia derecho de la oscilación (ms)
    * @param [in] weaveCircleRadio Oscilación circular - relación de retorno (0-100%)
    * @param [in] weaveStationary Espera en la posición de oscilación: 0-durante el tiempo de espera la posición continúa moviéndose; 1-durante el tiempo de espera la posición permanece estática
    * @return Código de error
    */
    int WeaveOnlineSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary);

Establecer los parámetros de detección de interrupción accidental del arco de soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer los parámetros de detección de interrupción accidental del arco de soldadura del robot
    * @param [in] checkEnable Si se habilita la detección; 0-no habilitar; 1-habilitar
    * @param [in] arcInterruptTimeLength Duración de confirmación de interrupción del arco (ms)
    * @return Código de error
    */
    int WeldingSetCheckArcInterruptionParam(int checkEnable, int arcInterruptTimeLength)

Obtener los parámetros de detección de interrupción accidental del arco de soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener los parámetros de detección de interrupción accidental del arco de soldadura del robot
    * @param [out] checkEnable Si se habilita la detección; 0-no habilitar; 1-habilitar
    * @param [out] arcInterruptTimeLength Duración de confirmación de interrupción del arco (ms)
    * @return Código de error
    */
    int WeldingGetCheckArcInterruptionParam(ref int checkEnable, ref int arcInterruptTimeLength)

Establecer los parámetros de recuperación tras la interrupción de la soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer los parámetros de recuperación tras la interrupción de la soldadura del robot
    * @param[in] enable Si se habilita la recuperación tras la interrupción de la soldadura
    * @param[in] length Distancia de solapamiento de la soldadura (mm)
    * @param[in] velocity Porcentaje de velocidad del robot al regresar al punto de reinicio de arco (0-100)
    * @param[in] moveType Modo de movimiento del robot al punto de reinicio de arco; 0-LIN; 1-PTP
    * @return Código de error
    */
    int WeldingSetReWeldAfterBreakOffParam(int enable, double length, double velocity, int moveType)

Obtener los parámetros de recuperación tras la interrupción de la soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener los parámetros de recuperación tras la interrupción de la soldadura del robot
    * @param [out] enable Si se habilita la recuperación tras la interrupción de la soldadura
    * @param [out] length Distancia de solapamiento de la soldadura (mm)
    * @param [out] velocity Porcentaje de velocidad del robot al regresar al punto de reinicio de arco (0-100)
    * @param [out] moveType Modo de movimiento del robot al punto de reinicio de arco; 0-LIN; 1-PTP
    * @return Código de error
    */
    int WeldingGetReWeldAfterBreakOffParam(ref int enable, ref double length, ref double velocity, ref int moveType)

Establecer el puerto DO extendido del modo de control de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el puerto DO extendido del modo de control de la soldadora
    * @param DONum Puerto DO del modo de control de la soldadora (0-127)
    * @return Código de error
    */
    int SetWeldMachineCtrlModeExtDoNum(int DONum);

Establecer el modo de control de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el modo de control de la soldadora
    * @param [in] mode Modo de control de la soldadora; 0-modo unificado de CC; 1-modo unificado de pulso; 2-modo JOB; 3-modo de control cercano; 4-modo separado; 5-modo CC/CV; 6-TIG; 7-CMT; 8-Panasonic-con pulso, 9-Panasonic-sin pulso
    * @param [in] ioType Tipo de control; 0-IO del armario de control; 1-protocolo de comunicación digital (UDP); 2-protocolo de comunicación digital (ModbusTCP)
    * @return Código de error
    */
    public int SetWeldMachineCtrlMode(int mode,int ioType = 1)

Obtener el modo de control de la soldadora
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el modo de control de la soldadora
    * @param [out] mode Modo de control de la soldadora; 0-modo unificado de CC; 1-modo unificado de pulso; 2-modo JOB; 3-modo de control cercano; 4-modo separado; 5-modo CC/CV; 6-TIG; 7-CMT
    * @return Código de error
    */
    public int GetWeldMachineCtrlMode(ref int mode)

Inicio de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Inicio de soldadura
    * @param [in] ioType Tipo de io 0-IO del controlador; 1-IO extendida
    * @param [in] arcNum Número del archivo de configuración de la soldadora
    * @param [in] timeout Tiempo de espera agotado del inicio de arco
    * @return Código de error
    */
    int ARCStart(int ioType, int arcNum, int timeout);

Fin de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Fin de soldadura
    * @param [in] ioType Tipo de io 0-IO del controlador; 1-IO extendida
    * @param [in] arcNum Número del archivo de configuración de la soldadora
    * @param [in] timeout Tiempo de espera agotado del cierre de arco
    * @return Código de error
    */
    int ARCEnd(int ioType, int arcNum, int timeout);

Inicio de oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Inicio de oscilación
    * @param [in] weaveNum Número de configuración de parámetros de soldadura oscilante
    * @return Código de error
    */
    int WeaveStart(int weaveNum);

Fin de oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Fin de oscilación
    * @param [in] weaveNum Número de configuración de parámetros de soldadura oscilante
    * @return Código de error
    */
    int WeaveEnd(int weaveNum);

Avance de alambre
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Avance de alambre
    * @param [in] ioType Tipo de io  0-IO del controlador; 1-IO extendida
    * @param [in] wireFeed Control de avance de alambre  0-detener el avance de alambre; 1-avanzar alambre
    * @return Código de error
    */
    int SetForwardWireFeed(int ioType, int wireFeed); 	

Retroceso de alambre
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Retroceso de alambre
    * @param [in] ioType Tipo de io  0-IO del controlador; 1-IO extendida
    * @param [in] wireFeed Control de avance de alambre  0-detener el avance de alambre; 1-avanzar alambre
    * @return Código de error
    */
    int SetReverseWireFeed(int ioType, int wireFeed);

Suministro de gas
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Suministro de gas
    * @param [in] ioType Tipo de io  0-IO del controlador; 1-IO extendida
    * @param [in] airControl Control de suministro de gas  0-detener el suministro de gas; 1-suministrar gas
    * @return Código de error
    */
    int SetAspirated(int ioType, int airControl);

Establecer la recuperación de la soldadura tras la interrupción del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la recuperación de la soldadura tras la interrupción del robot
    * @return Código de error
    */
    int WeldingStartReWeldAfterBreakOff()

Establecer la salida de la soldadura tras la interrupción del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la salida de la soldadura tras la interrupción del robot
    * @return Código de error
    */
    int WeldingAbortWeldAfterBreakOff()

Ejemplo de código
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button7_Click(object sender, EventArgs e)
    {
        robot.WeldingSetCurrent(1, 230, 0, 0);
        robot.WeldingSetVoltage(1, 24, 0, 1);

        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ARCStart(1, 0, 10000);
        robot.WeaveStart(0);
        robot.MoveL (p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
        robot.ARCEnd(1, 0, 10000);
        robot.WeaveEnd(0);
    }

Inicio de soldadura por segmentos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /** 
    * @brief Inicio de soldadura por segmentos
    * @param [in] startDesePos Posición cartesiana del punto inicial
    * @param [in] endDesePos Pose cartesiana del punto final
    * @param [in] startJPos Pose articular del punto inicial
    * @param [in] endJPos Pose articular del punto final
    * @param [in] weldLength Longitud del segmento de soldadura (mm)
    * @param [in] noWeldLength Longitud del segmento sin soldadura (mm)
    * @param [in] weldIOType Tipo de IO de soldadura (0-IO del armario de control; 1-IO extendida)
    * @param [in] arcNum Número del archivo de configuración de la soldadora
    * @param [in] weldTimeout Tiempo de espera agotado de inicio/cierre de arco
    * @param [in] isWeave Si se oscila
    * @param [in] weaveNum Número de configuración de parámetros de soldadura oscilante
    * @param [in] tool Número de herramienta
    * @param [in] user Número de pieza
    * @param [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm	 
    * @param [in] epos  Posición del eje extendido, unidad mm
    * @param [in] search  0-sin búsqueda de posición del alambre de soldadura, 1-búsqueda de posición del alambre de soldadura
    * @param [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos  Magnitud del desplazamiento de pose
    * @return Código de error 
    */
    int SegmentWeldStart(DescPose startDesePos, DescPose endDesePos, JointPos startJPos, JointPos endJPos, double weldLength, double noWeldLength, int weldIOType, int arcNum, int weldTimeout,bool isWeave, int weaveNum, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, byte search, byte offset_flag, DescPose offset_pos);

Ejemplo de código de soldadura por segmentos del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    private void btnWeldStart_Click(object sender, EventArgs e)
    {
        robot.WeldingSetCurrent(1, 230, 0, 0);
        robot.WeldingSetVoltage(1, 24, 0, 1);

        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        int rtn = robot.SegmentWeldStart( p1Desc,  p2Desc,  p1Joint,  p2Joint, 20, 20, 0, 0, 5000, false, 0, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
        Console.WriteLine("SegmentWeldStart rtn is {0}", rtn);
    }

Inicio de oscilación simulada
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inicio de oscilación simulada
    * @param  [in] weaveNum  Número del parámetro de oscilación
    * @return  Código de error
    */
    int WeaveStartSim(int weaveNum);

Fin de oscilación simulada
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Fin de oscilación simulada
    * @param  [in] weaveNum  Número del parámetro de oscilación
    * @return  Código de error
    */
    int WeaveEndSim(int weaveNum);

Inicio de la prealerta de detección de trayectoria (sin movimiento)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inicio de la prealerta de detección de trayectoria (sin movimiento)
    * @param  [in] weaveNum   Número del parámetro de oscilación
    * @return  Código de error
    */
    int WeaveInspectStart(int weaveNum);

Fin de la prealerta de detección de trayectoria (sin movimiento)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Fin de la prealerta de detección de trayectoria (sin movimiento)
    * @param  [in] weaveNum   Número del parámetro de oscilación
    * @return  Código de error
    */
    int WeaveInspectEnd(int weaveNum);

Inicio del cambio gradual de oscilación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inicio del cambio gradual de oscilación
    * @param [in] weaveChangeFlag 1-cambiar parámetros de oscilación; 2-cambiar parámetros de oscilación + velocidad de soldadura
    * @param [in] weaveNum Número de oscilación 
    * @param [in] velStart Velocidad de inicio de soldadura, (cm/min)
    * @param [in] velEnd Velocidad de fin de soldadura, (cm/min)
    * @return  Código de error
    */
    int WeaveChangeStart(int weaveChangeFlag, int weaveNum, double velStart, double velEnd);

Fin del cambio gradual de oscilación
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Fin del cambio gradual de oscilación
    * @return  Código de error
    */
    int WeaveChangeEnd()

Ejemplo de código de soldadura con cambio gradual de oscilación del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void btnweld_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveStartSim(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
        robot.WeaveEndSim(0);
        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveInspectStart(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
        robot.WeaveInspectEnd(0);

        robot.WeldingSetVoltage(1, 19, 0, 0);
        robot.WeldingSetCurrent(1, 190, 0, 0);
        robot.MoveL( p1Joint,  p1Desc, 1, 1, 100, 100, 50, -1,  exaxisPos, 0, 0,  offdese);
        robot.ARCStart(1, 0, 10000);
        robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.WeaveStart(0);
        robot.WeaveChangeStart(1, 0, 50, 30);
        robot.MoveL( p2Joint,  p2Desc, 1, 1, 100, 100, 1, -1,  exaxisPos, 0, 0,  offdese);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.ARCEnd(1, 0, 10000);
    }

IO extendida - Configurar la señal de detección de gas de la soldadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief IO extendida - Configurar la señal de detección de gas de la soldadora
    * @param  [in] DONum  Número DO extendido de la señal de detección de gas
    * @return  Código de error
    */
    int SetAirControlExtDoNum(int DONum);

IO extendida - Configurar la señal de inicio de arco de la soldadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief IO extendida - Configurar la señal de inicio de arco de la soldadora
    * @param  [in] DONum  Número DO extendido de la señal de inicio de arco de la soldadora
    * @return  Código de error
    */
    int SetArcStartExtDoNum(int DONum);

IO extendida - Configurar la señal de retroceso de alambre de la soldadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief IO extendida - Configurar la señal de retroceso de alambre de la soldadora
    * @param  [in] DONum  Número DO extendido de la señal de retroceso de alambre
    * @return  Código de error
    */
    int SetWireReverseFeedExtDoNum(int DONum);

IO extendida - Configurar la señal de avance de alambre de la soldadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief IO extendida - Configurar la señal de avance de alambre de la soldadora
    * @param  [in] DONum  Número DO extendido de la señal de avance de alambre
    * @return  Código de error
    */
    int SetWireForwardFeedExtDoNum(int DONum);

IO extendida - Configurar la señal de éxito de inicio de arco de la soldadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief IO extendida - Configurar la señal de éxito de inicio de arco de la soldadora
    * @param  [in] DINum  Número DI extendido de la señal de éxito de inicio de arco
    * @return  Código de error
    */
    int SetArcDoneExtDiNum(int DINum);

IO extendida - Configurar la señal de preparación de la soldadora
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief IO extendida - Configurar la señal de preparación de la soldadora
    * @param  [in] DINum  Número DI extendido de la señal de preparación de la soldadora
    * @return  Código de error
    */
    int SetWeldReadyExtDiNum(int DINum);

IO extendida - Configurar la señal de recuperación tras la interrupción de la soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief IO extendida - Configurar la señal de recuperación tras la interrupción de la soldadura
    * @param  [in] reWeldDINum  Número DI extendido de la señal de recuperación de la soldadura tras la interrupción
    * @param  [in] abortWeldDINum  Número DI extendido de la señal de salida de la soldadura tras la interrupción
    * @return  Código de error
    */
    int SetExtDIWeldBreakOffRecover(int reWeldDINum, int abortWeldDINum);

Ejemplo de código de configuración y obtención de IO extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button51_Click(object sender, EventArgs e)
    {
        robot.SetArcStartExtDoNum(10);
        robot.SetAirControlExtDoNum(20);
        robot.SetWireForwardFeedExtDoNum(30);
        robot.SetWireReverseFeedExtDoNum(40);

        robot.SetWeldReadyExtDiNum(50);
        robot.SetArcDoneExtDiNum(60);
        robot.SetExtDIWeldBreakOffRecover(70, 80);
        robot.SetWireSearchExtDIONum(0, 1);

        int[] DIConfig = new int[16];
        int[] DOConfig = new int[16];
        int rtn = robot.GetExtDIConfig(ref DIConfig);
        Console.WriteLine("GetExtDIConfig rtn={0}, welder ready={1}, arc done={2}, reweld start={3}, abort reweld={4}, wiresearch done={5}, laser state={6}, laser err={7}",
            rtn, DIConfig[0], DIConfig[1], DIConfig[2], DIConfig[3], DIConfig[4], DIConfig[5], DIConfig[6]);
        rtn = robot.GetExtDOConfig(ref DOConfig);
        Console.WriteLine("GetExtDOConfig rtn={0}, arc start={1}, air test={2}, wire forward={3}, wire inverse={4}, wiresearch={5}, weld mode={6}, laser enable={7}, laser on={8}, laser reset={9}",
            rtn, DOConfig[0], DOConfig[1], DOConfig[2], DOConfig[3], DOConfig[4], DOConfig[5], DOConfig[6], DOConfig[7], DOConfig[8]);
    }

Obtener la configuración de funciones DI extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la configuración de funciones DI extendida
    * @param [out] DIConfig Configuración de entrada DI extendida; [0]-soldadora preparada; [1]-éxito de inicio de arco; [2]-recuperación tras la interrupción de la soldadura; [3]-salida tras la interrupción de la soldadura; [4]-éxito de búsqueda de posición del alambre de soldadura; [5]-estado de funcionamiento de la soldadora láser; [6]-estado de fallo de la soldadora láser; [7-15]-reservado
    * @return  Código de error
    */
    public int GetExtDIConfig(ref int[] DIConfig)

Obtener la configuración de funciones DO extendida
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la configuración de funciones DO extendida
    * @param [out] DOConfig Configuración de entrada DO extendida; [0]-inicio de arco de la soldadora; [1]-detección de gas; [2]-avance de alambre; [3]-retroceso de alambre; [4]-búsqueda de posición del alambre de soldadura; [5]-modo de control de la soldadora; [6]-habilitación de la soldadora láser; [7]-inicio de la soldadora láser; [8]-reinicio de la soldadora láser; [9-15]-reservado
    * @return  Código de error
    */
    public int GetExtDOConfig(ref int[] DOConfig)

Control de seguimiento de arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Control de seguimiento de arco
    * @param  [in] flag Interruptor, 0-desactivado; 1-activado
    * @param  [in] dalayTime Tiempo de retardo, unidad ms
    * @param  [in] isLeftRight Compensación de desviación izquierda-derecha
    * @param  [in] klr Coeficiente de ajuste izquierda-derecha (sensibilidad)
    * @param  [in] tStartLr Tiempo de inicio de compensación izquierda-derecha cyc
    * @param  [in] stepMaxLr Compensación máxima izquierda-derecha por vez mm
    * @param  [in] sumMaxLr Compensación máxima total izquierda-derecha mm
    * @param  [in] isUpLow Compensación de desviación arriba-abajo
    * @param  [in] kud Coeficiente de ajuste arriba-abajo (sensibilidad)
    * @param  [in] tStartUd Tiempo de inicio de compensación arriba-abajo cyc
    * @param  [in] stepMaxUd Compensación máxima arriba-abajo por vez mm
    * @param  [in] sumMaxUd Compensación máxima total arriba-abajo
    * @param  [in] axisSelect Selección del sistema de coordenadas arriba-abajo, 0-oscilación; 1-herramienta; 2-base
    * @param  [in] referenceType Modo de configuración de la corriente de referencia arriba-abajo, 0-realimentación; 1-constante
    * @param  [in] referSampleStartUd Inicio del conteo de muestreo de la corriente de referencia arriba-abajo (realimentación), cyc
    * @param  [in] referSampleCountUd Conteo cíclico de muestreo de la corriente de referencia arriba-abajo (realimentación), cyc
    * @param  [in] referenceCurrent Corriente de referencia arriba-abajo mA
    *  @param  [in] offsetType Tipo de seguimiento con desplazamiento, 0-sin desplazamiento; 1-muestreo; 2-porcentaje  /version 3.7.9
    * @param  [in] offsetParameter Parámetro de desplazamiento; muestreo (tiempo de inicio del muestreo de desplazamiento, por defecto se muestrea un ciclo); porcentaje (porcentaje de desplazamiento (-100 ~ 100)) /version 3.7.9
    * @return  Código de error
    */
    int ArcWeldTraceControl(int flag, double delaytime, int isLeftRight, double klr, double tStartLr, double stepMaxLr, double sumMaxLr, int isUpLow, double kud, double tStartUd, double stepMaxUd, double sumMaxUd, int axisSelect, int referenceType, double referSampleStartUd, double referSampleCountUd, double referenceCurrent, int offsetType, int offsetParameter);

Selección del canal AI de seguimiento de arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Selección del canal AI de seguimiento de arco
    * @param  [in] channel Selección del canal AI de seguimiento de arco, [0-3]
    * @return  Código de error
    */
    int ArcWeldTraceExtAIChannelConfig(int channel);

Inicio del seguimiento de arco + compensación multipasada multicapa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Inicio del seguimiento de arco + compensación multipasada multicapa
    * @return Código de error
    */
    int ArcWeldTraceReplayStart();

Fin del seguimiento de arco + compensación multipasada multicapa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

        /**
         * @brief Fin del seguimiento de arco + compensación multipasada multicapa
         * @return Código de error
         */
    int ArcWeldTraceReplayEnd();

Transformación de coordenadas de desplazamiento - soldadura multipasada multicapa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

     /**
     * @brief Transformación de coordenadas de desplazamiento - soldadura multipasada multicapa
     * @param [in] pointO Pose cartesiana del punto de referencia
     * @param [in] pointX Pose cartesiana del punto de dirección de desplazamiento X del punto de referencia
     * @param [in] pointZ Pose cartesiana del punto de dirección de desplazamiento Z del punto de referencia
     * @param [in] dx Desplazamiento en dirección x (mm)
     * @param [in] z方向偏移量(mm)
     * @param [in] 绕y轴偏移量(°)
     * @param [out] 计算结果偏移量
     * @return 错误码
     */
    int MultilayerOffsetTrsfToBase(DescTran pointO, DescTran pointX, DescTran pointZ, double dx, double dy, double db, ref DescPose offset);

Ejemplo de código de seguimiento de arco para soldadura multipasada multicapa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    private void button52_Click(object sender, EventArgs e)
    {
        JointPos mulitilineorigin1_joint = new JointPos(-24.090, -63.501, 84.288, -111.940, -93.426, 57.669);
        DescPose mulitilineorigin1_desc = new DescPose(-677.559, 190.951, -1.205, 1.144, -41.482, -82.577);

        DescTran mulitilineX1_desc = new DescTran();
        mulitilineX1_desc.x = -677.556;
        mulitilineX1_desc.y = 211.949;
        mulitilineX1_desc.z = -1.206;

        DescTran mulitilineZ1_desc = new DescTran();
        mulitilineZ1_desc.x = -677.564;
        mulitilineZ1_desc.y = 190.956;
        mulitilineZ1_desc.z = 19.817;

        JointPos mulitilinesafe_joint = new JointPos(-25.734, -63.778, 81.502, -108.975, -93.392, 56.021);
        DescPose mulitilinesafe_desc = new DescPose(-677.561, 211.950, 19.812, 1.144, -41.482, -82.577);
        JointPos mulitilineorigin2_joint = new JointPos(-29.743, -75.623, 101.241, -116.354, -94.928, 55.735);
        DescPose mulitilineorigin2_desc = new DescPose(-563.961, 215.359, -0.681, 2.845, -40.476, -87.443);

        DescTran mulitilineX2_desc = new DescTran();
        mulitilineX2_desc.x = -563.965;
        mulitilineX2_desc.y = 220.355;
        mulitilineX2_desc.z = -0.680;

        DescTran mulitilineZ2_desc = new DescTran();
        mulitilineZ2_desc.x = -563.968;
        mulitilineZ2_desc.y = 215.362;
        mulitilineZ2_desc.z = 4.331;

        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset = new DescPose(0, 0, 0, 0, 0, 0);

        Thread.Sleep(10);
        int error = robot.MoveJ( mulitilinesafe_joint,  mulitilinesafe_desc, 13, 0, 10, 100, 100,  epos, -1, 0,  offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ARCStart(1, 0, 3000);
        Console.WriteLine("ARCStart return: {0}", error);

        error = robot.WeaveStart(0);
        Console.WriteLine("WeaveStart return: {0}", error);

        error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
        Console.WriteLine("ArcWeldTraceControl return: {0}", error);

        error = robot.MoveL( mulitilineorigin2_joint,  mulitilineorigin2_desc, 13, 0, 1, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
        Console.WriteLine("ArcWeldTraceControl return: {0}", error);

        error = robot.WeaveEnd(0);
        Console.WriteLine("WeaveEnd return: {0}", error);

        error = robot.ARCEnd(1, 0, 10000);
        Console.WriteLine("ARCEnd return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ARCStart(1, 0, 3000);
        Console.WriteLine("ARCStart return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.ArcWeldTraceReplayStart();
        Console.WriteLine("ArcWeldTraceReplayStart return: {0}", error);

        error = robot.MoveL( mulitilineorigin2_joint,  mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ArcWeldTraceReplayEnd();
        Console.WriteLine("ArcWeldTraceReplayEnd return: {0}", error);

        error = robot.ARCEnd(1, 0, 10000);
        Console.WriteLine("ARCEnd return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ARCStart(1, 0, 3000);
        Console.WriteLine("ARCStart return: {0}", error);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0, ref offset);
        Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

        error = robot.ArcWeldTraceReplayStart();
        Console.WriteLine("MoveJ return: {0}", error);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 1, 2, 100, 100, -1, epos, 1, 1, offset, 1, 100);
        Console.WriteLine("MoveL return: {0}", error);

        error = robot.ArcWeldTraceReplayEnd();
        Console.WriteLine("ArcWeldTraceReplayEnd return: {0}", error);

        error = robot.ARCEnd(1, 0, 3000);
        Console.WriteLine("ARCEnd return: {0}", error);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
        Console.WriteLine("MoveJ return: {0}", error);
    }

Selección del canal AI de realimentación de corriente de la soldadora para seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:
    
    /**
    * @brief Selección del canal AI de realimentación de corriente de la soldadora para seguimiento de arco
    * @param [in]  channel Canal; 0-AI extendida 0; 1-AI extendida 1; 2-AI extendida 2; 3-AI extendida 3; 4-AI del armario de control 0; 5-AI del armario de control 1
    * @return Código de error
    */
    int ArcWeldTraceAIChannelCurrent(int channel);

Selección del canal AI de realimentación de tensión de la soldadora para seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Selección del canal AI de realimentación de tensión de la soldadora para seguimiento de arco
    * @param [in]  channel Canal; 0-AI extendida 0; 1-AI extendida 1; 2-AI extendida 2; 3-AI extendida 3; 4-AI del armario de control 0; 5-AI del armario de control 1
    * @return Código de error
    */
    int ArcWeldTraceAIChannelVoltage(int channel);

Parámetros de conversión de la realimentación de corriente de la soldadora para seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Parámetros de conversión de la realimentación de corriente de la soldadora para seguimiento de arco
    * @param [in] AILow Límite inferior del canal AI, valor por defecto 0V, rango [0-10V]
    * @param [in] AIHigh Límite superior del canal AI, valor por defecto 10V, rango [0-10V]
    * @param [in] currentLow Valor de corriente de la soldadora correspondiente al límite inferior del canal AI, valor por defecto 0V, rango [0-200V]
    * @param [in] currentHigh Valor de corriente de la soldadora correspondiente al límite superior del canal AI, valor por defecto 100V, rango [0-200V]
    * @return Código de error
    */
    public int ArcWeldTraceCurrentPara(double AILow, double AIHigh, double currentLow, double currentHigh)

Parámetros de conversión de la realimentación de tensión de la soldadora para seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Parámetros de conversión de la realimentación de tensión de la soldadora para seguimiento de arco
    * @param [in] AILow Límite inferior del canal AI, valor por defecto 0V, rango [0-10V]
    * @param [in] AIHigh Límite superior del canal AI, valor por defecto 10V, rango [0-10V]
    * @param [in] voltageLow Valor de tensión de la soldadora correspondiente al límite inferior del canal AI, valor por defecto 0V, rango [0-200V]
    * @param [in] voltageHigh Valor de tensión de la soldadora correspondiente al límite superior del canal AI, valor por defecto 100V, rango [0-200V]
    * @return Código de error
    */
    public int ArcWeldTraceVoltagePara(double AILow, double AIHigh, double voltageLow, double voltageHigh)

Ejemplo de código de seguimiento de arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void button8_Click(object sender, EventArgs e)
    {
        DescPose startdescPose = new DescPose(441.901, 416.508, -51.979, -179.234, 0.718, -115.305);
        JointPos startjointPos = new JointPos(-146.22, -60.551, 104.859, -135.317, -90.289, 59.088);

        DescPose enddescPose = new DescPose(441.901, 615.317, -51.979, -179.234, 0.718, -115.305);
        JointPos endjointPos = new JointPos(-133.22, -44.193, 74.934, -121.661, -90.509, 72.087);

        DescPose safetydescPose = new DescPose(441.901, 416.508, -51.979, -179.234, 0.718, -115.305);
        JointPos safetyjointPos = new JointPos(-146.22, -60.551, 104.859, -135.317, -90.289, 59.088);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(safetyjointPos, safetydescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);

        robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0);
        robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1);
        robot.WeldingSetVoltage(0, 25, 1, 0); 
        robot.WeldingSetCurrent(0, 260, 0, 0); 

        int rtn = robot.ArcWeldTraceAIChannelCurrent(4);
        Console.WriteLine("ArcWeldTraceAIChannelCurrent rtn is " + rtn);
        rtn = robot.ArcWeldTraceAIChannelVoltage(5);
        Console.WriteLine("ArcWeldTraceAIChannelVoltage rtn is " + rtn);
        rtn = robot.ArcWeldTraceCurrentPara((double)0, (double)5, (double)0, (double)500);
        Console.WriteLine("ArcWeldTraceCurrentPara rtn is " + rtn);
        rtn = robot.ArcWeldTraceVoltagePara((double)1.018, (double)10, (double)0, (double)50);
        Console.WriteLine("ArcWeldTraceVoltagePara rtn is " + rtn);

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, 0,exaxisPos, 0, 0, offdese);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.MoveJ(safetyjointPos, safetydescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);

    }

Establecer el puerto IO extendido de búsqueda de posición del alambre de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el puerto IO extendido de búsqueda de posición del alambre de soldadura
    * @param searchDoneDINum Puerto DO de éxito de búsqueda de posición del alambre de soldadura (0-127)
    * @param searchStartDONum Puerto DO de control de inicio/parada de búsqueda de posición del alambre de soldadura (0-127)
    * @return Código de error
    */
    int SetWireSearchExtDIONum(int searchDoneDINum, int searchStartDONum);

Inicio de búsqueda de posición del alambre de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inicio de búsqueda de posición del alambre de soldadura
    * @param  [in] refPos  1-punto de referencia 0-punto de contacto
    * @param  [in] searchVel   Velocidad de búsqueda de posición %
    * @param  [in] searchDis  Distancia de búsqueda de posición mm
    * @param  [in] autoBackFlag Indicador de retorno automático, 0-no automático; -automático
    * @param  [in] autoBackVel  Velocidad de retorno automático %
    * @param  [in] autoBackDis  Distancia de retorno automático mm
    * @param  [in] offectFlag  1-búsqueda de posición con desplazamiento; 0-búsqueda de posición en el punto de enseñanza
    * @return  Código de error
    */
    int WireSearchStart(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Fin de búsqueda de posición del alambre de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Fin de búsqueda de posición del alambre de soldadura
    * @param  [in] refPos  1-punto de referencia 2-punto de contacto
    * @param  [in] searchVel   Velocidad de búsqueda de posición %
    * @param  [in] searchDis  Distancia de búsqueda de posición mm
    * @param  [in] autoBackFlag Indicador de retorno automático, 0-no automático; -automático
    * @param  [in] autoBackVel  Velocidad de retorno automático %
    * @param  [in] autoBackDis  Distancia de retorno automático mm
    * @param  [in] offectFlag  1-búsqueda de posición con desplazamiento; 2-búsqueda de posición en el punto de enseñanza
    * @return  Código de error
    */
    int WireSearchEnd(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Calcular el desplazamiento de búsqueda de posición del alambre de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Calcular el desplazamiento de búsqueda de posición del alambre de soldadura
    * @param  [in] seamType  Tipo de soldadura
    * @param  [in] method   Método de cálculo
    * @param  [in] varNameRef Punto de referencia 1-6, "#" indica variable sin punto
    * @param  [in] varNameRes Punto de contacto 1-6, "#" indica variable sin punto
    * @param  [out] offectFlag 0-el desplazamiento se superpone directamente al punto de instrucción; 1-el desplazamiento requiere transformación de coordenadas del punto de instrucción
    * @param  [out] offect Pose de desplazamiento [x, y, z, a, b, c]
    * @return  Código de error
    */
    int GetWireSearchOffset(int seamType, int method, string[] varNameRef, string[] varNameRes, ref int offsetFlag, ref DescPose offset);

Esperar a que finalice la búsqueda de posición del alambre de soldadura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Esperar a que finalice la búsqueda de posición del alambre de soldadura
    * @return  Código de error
    */
    int WireSearchWait(string name);

Escritura del punto de contacto de búsqueda de posición del alambre de soldadura en la base de datos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Escritura del punto de contacto de búsqueda de posición del alambre de soldadura en la base de datos
    * @param  [in] varName  Nombre del punto de contacto "RES0" ~ "RES99"
    * @param  [in] pos  Datos del punto de contacto [x, y, x, a, b, c]
    * @return  Código de error
    */
    int SetPointToDatabase(string varName, DescPose pos);

Ejemplo de código de búsqueda de posición del alambre de soldadura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button53_Click(object sender, EventArgs e)
    {
        DescPose toolCoord=new DescPose(0, 0, 200, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);
        DescPose wobjCoord=new DescPose(0, 0, 0, 0, 0, 0);
        robot.SetWObjCoord(1, wobjCoord, 0);

        int rtn0, rtn1, rtn2 = 0;
        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose descStart = new DescPose(216.543, 445.175, 93.465, 179.683, 1.757, -112.641);
        JointPos jointStart = new JointPos(-128.345, -86.660, 114.679, -119.625, -89.219, 74.303);

        DescPose descEnd = new DescPose(111.143, 523.384, 87.659, 179.703, 1.835, -97.750);
        JointPos jointEnd = new JointPos(-113.454, -81.060, 109.328, -119.954, -89.218, 74.302);

        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);

        DescPose descREF0A = new DescPose(142.135, 367.604, 86.523, 179.728, 1.922, -111.089);
        JointPos jointREF0A = new JointPos(-126.794, -100.834, 128.922, -119.864, -89.218, 74.302);

        DescPose descREF0B = new DescPose(254.633, 463.125, 72.604, 179.845, 2.341, -114.704);
        JointPos jointREF0B = new JointPos(-130.413, -81.093, 112.044, -123.163, -89.217, 74.303);

        DescPose descREF1A = new DescPose(92.556, 485.259, 47.476, -179.932, 3.130, -97.512);
        JointPos jointREF1A = new JointPos(-113.231, -83.815, 119.877, -129.092, -89.217, 74.303);

        DescPose descREF1B = new DescPose(203.103, 583.836, 63.909, 179.991, 2.854, -103.372);
        JointPos jointREF1B = new JointPos(-119.088, -69.676, 98.692, -121.761, -89.219, 74.303);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //起点
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //方向点
        rtn1 = robot.WireSearchWait("REF0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //起点
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //方向点
        rtn1 = robot.WireSearchWait("REF1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //起点
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //方向点
        rtn1 = robot.WireSearchWait("RES0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //起点
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //方向点
        rtn1 = robot.WireSearchWait("RES1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        string[] varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
        string[] varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
        int offectFlag = 0;
        DescPose offectPos = new DescPose(0, 0, 0, 0, 0, 0);
        rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, ref offectFlag, ref offectPos);
        robot.PointsOffsetEnable(0, offectPos);
        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);
        robot.PointsOffsetDisable();
    }

Establecer el inicio del cambio gradual de la tensión de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el inicio del cambio gradual de la tensión de soldadura
    * @param [in] IOType Tipo de control; 0-IO del armario de control; 1-protocolo de comunicación digital (UDP); 2-protocolo de comunicación digital (ModbusTCP)
    * @param [in] voltageStart Tensión de soldadura inicial (V)
    * @param [in] voltageEnd Tensión de soldadura final (V)
    * @param [in] AOIndex Número de puerto AO del armario de control (0-1)
    * @param [in] blend Si se suaviza 0-sin suavizado; 1-suavizado
    * @return Código de error
    */
    int WeldingSetVoltageGradualChangeStart(int IOType, double voltageStart, double voltageEnd, int AOIndex, int blend);

Establecer el fin del cambio gradual de la tensión de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el fin del cambio gradual de la tensión de soldadura
    * @return Código de error
    */
    int WeldingSetVoltageGradualChangeEnd();

Establecer el inicio del cambio gradual de la corriente de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el inicio del cambio gradual de la corriente de soldadura
    * @param [in] IOType Tipo de control; 0-IO del armario de control; 1-protocolo de comunicación digital (UDP); 2-protocolo de comunicación digital (ModbusTCP)
    * @param [in] voltageStart Corriente de soldadura inicial (A)
    * @param [in] voltageEnd Corriente de soldadura final (A)
    * @param [in] AOIndex Número de puerto AO del armario de control (0-1)
    * @param [in] blend Si se suaviza 0-sin suavizado; 1-suavizado
    * @return Código de error
    */
    int WeldingSetCurrentGradualChangeStart(int IOType, double currentStart, double currentEnd, int AOIndex, int blend);

Establecer el fin del cambio gradual de la corriente de soldadura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el fin del cambio gradual de la corriente de soldadura
    * @return Código de error
    */
    int WeldingSetCurrentGradualChangeEnd();

Ejemplo de código de cambio gradual de corriente y tensión de soldadura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void btnweld_Click(object sender, EventArgs e)
    {
        DescPose startdescPose = new DescPose(-319.303, -240.689, 116.379, -175.879, -0.337, 148.239);
        JointPos startjointPos = new JointPos(20.474, -103.554, 126.774, -116.682, -87.746, -37.709);

        DescPose enddescPose = new DescPose(-454.166, -327.159, 62.217, 177.199, -2.276, 154.955);
        JointPos endjointPos = new JointPos(27.176, -74.423, 104.557, -119.315, -93.514, -37.698);

        DescPose safedescPose = new DescPose(-375.533, -543.319, 19.798, 177.486, -2.489, 175.825);
        JointPos safejointPos = new JointPos(48.074, -59.714, 89.955, -119.777, -93.508, -37.683);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0);
        robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1);

        robot.WeldingSetVoltage(0, 25, 1, 0);//
        robot.WeldingSetCurrent(0, 260, 0, 0);// 

        robot.MoveJ(safejointPos, safedescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);

        int rtn = robot.WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0);
        Console.WriteLine($"WeldingSetCurrentGradualChangeStart rtn is {rtn}");
        rtn = robot.WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0);
        Console.WriteLine($"WeldingSetVoltageGradualChangeStart rtn is {rtn}");

        rtn = robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        Console.WriteLine($"ArcWeldTraceControl rtn is {rtn}");

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);

        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
        rtn = robot.WeaveChangeStart(2, 1, 24, 36);
        Console.WriteLine($"WeaveChangeStart rtn is {rtn}");
        //robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, exaxisPos, 0, 0, offdese);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.WeldingSetCurrentGradualChangeEnd();
        robot.WeldingSetVoltageGradualChangeEnd();
    }

Establecer parámetros de oscilación personalizados
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Establecer parámetros de oscilación personalizados
     * @param [in] id Número de oscilación personalizada: 0-2
     * @param [in] pointNum Número de puntos de oscilación 0-10
     * @param [in] point Datos del punto de desplazamiento x,y,z
     * @param [in] stayTime Tiempo de permanencia de la oscilación ms
     * @param [in] frequency Frecuencia de oscilación Hz
     * @param [in] incStayType Modo de espera: 0-el ciclo no incluye tiempo de espera; 1-el ciclo incluye tiempo de espera
     * @param [in] stationary Espera en la posición de oscilación: 0-durante el tiempo de espera continúa el movimiento; 1-durante el tiempo de espera la posición permanece estática
     * @return  Código de error
     */
    public int CustomWeaveSetPara(int id, int pointNum, DescTran[] points, double[] stayTimes, double frequency, int incStayType, int stationary)

Obtener parámetros de oscilación personalizados
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Obtener parámetros de oscilación personalizados
     * @param [in] id Número de oscilación personalizada: 0-2
     * @param [out] pointNum Número de puntos de oscilación 0-10
     * @param [out] point Datos del punto de desplazamiento x,y,z
     * @param [out] stayTime Tiempo de permanencia de la oscilación ms
     * @param [out] frequency Frecuencia de oscilación Hz
     * @param [out] incStayType Modo de espera: 0-el ciclo no incluye tiempo de espera; 1-el ciclo incluye tiempo de espera
     * @param [out] stationary Espera en la posición de oscilación: 0-durante el tiempo de espera continúa el movimiento; 1-durante el tiempo de espera la posición permanece estática
     * @return  Código de error
     */
    public int CustomWeaveGetPara(int id, ref int pointNum, ref DescTran[] points, ref double[] stayTimes, ref double frequency, ref int incStayType, ref int stationary)

Ejemplo de código de parámetros de oscilación personalizados
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    public void TestCoordMain5()
    {  
        DescTran[] points = new DescTran[10];
        for (int i = 0; i < 10; i++)
        {
            points[i] = new DescTran();
        }
        points[0].x = -3;
        points[0].y = -3;
        points[0].z = 0;
        points[1].x = -6;
        points[1].y = 0;
        points[1].z = 0;
        points[2].x = -3;
        points[2].y = 3;
        points[2].z = 0;
        points[3].x = 0;
        points[3].y = 0;
        points[3].z = 0;
        double[] stayTimes = new double[10] { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
        int rtn = robot.CustomWeaveSetPara(2, 4, points, stayTimes, 1.000, 0, 0);
        Console.WriteLine($"CustomWeaveSetPara rtn is {rtn}");
        System.Threading.Thread.Sleep(1000);
        int pointNum = 0;
        double frequency = 0;
        int incStayType = 0;
        int stationary = 0;
        rtn = robot.CustomWeaveGetPara(2, ref pointNum, ref points, ref stayTimes, ref frequency, ref incStayType, ref stationary);
        Console.WriteLine($"pointNum is {pointNum}");
        for (int i = 0; i < pointNum; i++)
        {
            Console.WriteLine($"point {i}, point x y z {points[i].x:F6} {points[i].y:F6} {points[i].z:F6}");
        }
        Console.WriteLine($"fre is {frequency:F6}, stay is {incStayType} {stationary}");
        robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000);
        DescPose desc_p1 = new DescPose(-288.650, 367.807, 288.404, 0.000, -0.001, 0.001);
        DescPose desc_p2 = new DescPose(-431.714, 367.815, 288.415, 0.001, 0.001, 0.000);    
        DescPose desc_p3 = new DescPose(-348.666, 427.798, 288.404, -0.000, -0.000, 0.001);
        JointPos j1 = new JointPos(140.656,  -84.560,  -91.707, -93.734,  90.000,50.655 );
        JointPos j2 = new JointPos ( 149.873, -98.298, -77.599,  -94.103,  90.000,  59.873 );
        JointPos j3 = new JointPos (139.773,  -96.173, -80.014,  -93.814,  90.000,  49.772 );
        ExaxisPos epos = new ExaxisPos(0,0,0,0);
        DescPose offset_pos = new DescPose(0,0,0,0,0,0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.Circle(j3, desc_p3, 3, 0, 100, 100, epos, j2, desc_p2, 3, 0, 100, 100, epos, 10, -1, offset_pos, 100, -1, 0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveC(j3, desc_p3, 3, 0, 100, 100, epos, 0, offset_pos, j2, desc_p2, 3, 0, 100, 100, epos, 0, offset_pos, 10, -1, 0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveL(j2, desc_p2, 3, 0, 100, 100, 10, -1, epos, 0, 0, offset_pos, 0, 0, 10);
        robot.WeaveEnd(0);
    }

Configuración de parámetros de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Escribir los parámetros de configuración de uno de los 10 grupos de procesos de la soldadora láser y configurarlos en la soldadora
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[in] num Número de grupo a configurar (1~10)
    * @param[in] scanSpeed Velocidad de escaneo
    * @param[in] scanWidth Ancho de escaneo
    * @param[in] peakPower Potencia pico
    * @param[in] dutyCycle Ciclo de trabajo
    * @param[in] freq Frecuencia
    * @return Código de error
    */
    public int SetLaserWeldingParam(int io_type, int num, int scanSpeed, int scanWidth, int peakPower, int dutyCycle, int freq)

Establecer el inicio y la parada de la soldadura láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el encendido y apagado de la soldadora láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[in] status Palabra de control 0-recepción de luz 1-emisión de luz
    * @param[in] max_waittime Tiempo máximo de espera
    * @return Código de error
    */
    public int SetLaserWeldingStartEnd(int io_type, int status, int max_waittime)

Habilitación/deshabilitación de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Habilitación/deshabilitación de la soldadora láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[in] status 0-deshabilitar 1-habilitar
    * @return Código de error
    */
    public int SetLaserWeldingEnable(int io_type, int status)

Reinicio de fallos de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Reinicio de fallos de la soldadora láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[in] status Palabra de control 0-no válida 1-reinicio de fallos
    * @return Código de error
    */
    public int ResetLaserWeldingErr(int io_type, int status)

Obtener el estado de funcionamiento de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado de funcionamiento de la soldadora láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[out] status Palabra de control 0-parada 1-en funcionamiento
    * @return Código de error
    */
    public int GetLaserWeldingRunningState(int io_type, ref int status)

Obtener el estado de fallo de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado de fallo de la soldadora láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[out] status 0-sin fallo 1-con fallo
    * @return Código de error
    */
    public int GetLaserWeldingErrState(int io_type, ref int status)

Obtener los parámetros de configuración de la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener los parámetros de configuración de uno de los 10 grupos de procesos de la soldadora láser
    * @param[in] num Número de grupo a configurar (1~10)
    * @param[out] scanSpeed Velocidad de escaneo
    * @param[out] scanWidth Ancho de escaneo
    * @param[out] peakPower Potencia pico
    * @param[out] dutyCycle Ciclo de trabajo
    * @param[out] freq Frecuencia
    * @return Código de error
    */
    public int GetLaserWeldingParamTarget(int num, ref int scanSpeed, ref int scanWidth, ref int peakPower, ref int dutyCycle, ref int freq)

Obtener los parámetros de configuración vigentes actualmente en la soldadora láser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener los parámetros de configuración vigentes actualmente en la soldadora láser
    * @param[in] io_type Tipo de comunicación 0-IO 1-UDP
    * @param[out] scanSpeed Velocidad de escaneo
    * @param[out] scanWidth Ancho de escaneo
    * @param[out] peakPower Potencia pico
    * @param[out] dutyCycle Ciclo de trabajo
    * @param[out] freq Frecuencia
    * @return Código de error
    */
    public int GetLaserWeldingParamActual(int io_type, ref int scanSpeed, ref int scanWidth, ref int peakPower, ref int dutyCycle, ref int freq)
    
Configurar el puerto DO de habilitación de IO extendida de la soldadora láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Configuración de IO extendida de la soldadora láser, puerto DO de habilitación
    * @param[in] ctrlModeDONum Número de puerto DO extendido de habilitación de la soldadora láser
    * @return Código de error
    */
    public int SetLaserWeldingEnableExtDoNum(int ctrlModeDONum)

Configurar el puerto DO de inicio de IO extendida de la soldadora láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Configuración de IO extendida de la soldadora láser, puerto DO de inicio
    * @param[in] ctrlModeDONum Número de puerto DO extendido de inicio (emisión/recepción de luz) de la soldadora láser
    * @return Código de error
    */
    public int SetLaserWeldingStartExtDoNum(int ctrlModeDONum)

Puerto DO de reinicio de fallos de IO extendida de la soldadora láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Configuración de IO extendida de la soldadora láser, puerto DO de reinicio de fallos
    * @param[in] ctrlModeDONum Número de puerto DO extendido de reinicio de fallos de la soldadora láser
    * @return Código de error
    */
    public int SetLaserWeldingErrResetExtDoNum(int ctrlModeDONum)

Configurar DI extendida del estado de funcionamiento (estado de emisión de luz) de la soldadora láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Configurar DI extendida del estado de funcionamiento (estado de emisión de luz) de la soldadora láser
    * @param[in] diNum Configurar el puerto DI extendido del estado de funcionamiento (estado de emisión de luz) de la soldadora láser
    * @return Código de error
    */
    public int SetLaserWeldingRunningStateExtDiNum(int diNum)
    
Configurar el puerto DI extendido del estado de fallo de IO extendida de la soldadora láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Configurar DI extendida del estado de fallo de la soldadora láser
    * @param[in] diNum Configurar el puerto DI extendido del estado de fallo de la soldadora láser
    * @return Código de error
    */
    public int SetLaserWeldingErrStateExtDiNum(int diNum)
        
Ejemplo de código de soldadura láser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    private void btnLaserWeld_Click(object sender, EventArgs e)
    {

        int rtn = -1;
        // Cargar el controlador UDP
        rtn = robot.ExtDevLoadUDPDriver();
        if (rtn != 0)
        {
            Console.WriteLine("Failed to load UDP driver, error code: " + rtn);
        }
        Thread.Sleep(1000);

        // Establecer los parámetros de soldadura láser: io_type=1, num=3, scanSpeed=2000, scanWidth=3, peakPower=1500, dutyCycle=100, freq=1000
        rtn = robot.SetLaserWeldingParam(1, 3, 2000, 3, 1500, 100, 1000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingParam failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("SetLaserWeldingParam success");
        }

        // Establecer el número de puerto DO de inicio
        rtn = robot.SetLaserWeldingStartExtDoNum(1);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartExtDoNum failed, error code: " + rtn);
        }

        // Establecer el modo 0 (modo de enseñanza)
        rtn = robot.Mode(0);
        if (rtn != 0)
        {
            Console.WriteLine("Set mode 0 failed, error code: " + rtn);
        }
        Thread.Sleep(1000);


        DescPose desc_pos1 = new DescPose(-303.721, -206.960, 297.105, 152.209, 19.857, 109.166);
        DescPose desc_pos2 = new DescPose(-301.575, -254.888, 284.786, 155.919, 26.946, 111.629);
        DescPose desc_safe = new DescPose(-344.386, -280.830, 435.073, 173.835, 15.333, 124.931);


        ExaxisPos exaxis = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offset = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);

        // Moverse al primer punto de soldadura
        int error = robot.MoveL(desc_pos1, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to pos1 return: " + error);

        // Encender el láser (emisión de luz)
        rtn = robot.SetLaserWeldingStartEnd(1, 1, 10000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartEnd (start) failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("Laser started");
        }

        // Moverse al segundo punto de soldadura (durante la soldadura)
        rtn = robot.MoveL(desc_pos2, 0, 0, 30, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to pos2 return: " + rtn);

        Thread.Sleep(500);
        // Apagar el láser (recepción de luz)
        rtn = robot.SetLaserWeldingStartEnd(1, 0, 10000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartEnd (stop) failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("Laser stopped");
        }

        // Moverse al punto seguro
        rtn = robot.MoveL(desc_safe, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to safe_pos return: " + rtn);

        // Establecer el modo 1 (modo remoto)
        rtn = robot.Mode(1);
        if (rtn != 0)
        {
            Console.WriteLine("Set mode 1 failed, error code: " + rtn);
        }
        Thread.Sleep(1000);

        // Cerrar la conexión
        robot.CloseRPC();
        Thread.Sleep(1000);

        Console.WriteLine("Test completed");

        return ;
    }
           
Establecer el retorno al punto cero del ciclo al final de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer el retorno al punto cero del ciclo al final de la oscilación
    * @param [in] flag Si la oscilación regresa al punto cero del ciclo al finalizar; 0-no regresar al punto cero del ciclo; 1-regresar al punto cero del ciclo
    * @return  Código de error
    */
    public int SetWeavebackCenterConfig(int flag) 
           
Obtener el parámetro de retorno al punto cero del ciclo al final de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el parámetro de retorno al punto cero del ciclo al final de la oscilación
    * @param [out] flag Si la oscilación regresa al punto cero del ciclo al finalizar; 0-no regresar al punto cero del ciclo; 1-regresar al punto cero del ciclo
    * @return  Código de error
    */
    public int GetWeavebackCenterConfig(ref int flag)
           
Ejemplo de código de retorno al punto cero del ciclo al final de la oscilación
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    public void TestSplineWeave()
    {
        int rtn;

        // Configuración de retorno al centro de la oscilación
        robot.SetWeavebackCenterConfig(1);
        int weaveBackConfig = 0;
        robot.GetWeavebackCenterConfig(ref weaveBackConfig);
        Console.WriteLine("GetWeavebackCenterConfig: {0}", weaveBackConfig);

        JointPos j1 = new JointPos(9.000, -66.067, 67.706, -103.217, -90.151, 100.669);
        JointPos j2 = new JointPos(-4.660, -107.973, 103.734, -76.214, -89.999, 90.886);
        JointPos j3 = new JointPos(-36.762, -77.380, 91.364, -127.159, -90.024, 54.833);
        JointPos j4 = new JointPos(-62.875, -89.460, 86.437, -77.030, -90.012, 31.539);
        DescPose desc_pos1 = new DescPose(-654.129, -235.344, 246.543, 6.010, -11.535, -176.787);
        DescPose desc_pos2 = new DescPose(-273.710, -100.871, 280.935, 5.692, 9.522, 179.512);
        DescPose desc_pos3 = new DescPose(-566.093, 311.278, 215.008, -10.453, -17.486, -174.209);
        DescPose desc_pos4 = new DescPose(-246.558, 328.240, 292.173, 13.912, 4.437, -179.067);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        int tool = 2;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 20.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;

        robot.SetSpeed(1);

        // Moverse al punto inicial j1
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, 100.0f, epos, blendT, flag, offset_pos);
        Console.WriteLine("MoveJ to j1 rtn: {0}", rtn);

        // Movimiento de oscilación + spline
        robot.WeaveStart(0);
        robot.NewSplineStart(0, 6000);
        robot.NewSplinePoint(j1, desc_pos1, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j2, desc_pos2, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j3, desc_pos3, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j4, desc_pos4, tool, user, vel, acc, ovl, -1.0f, 1);
        robot.NewSplineEnd();

        Console.WriteLine("TestSplineWeave completed");
    }