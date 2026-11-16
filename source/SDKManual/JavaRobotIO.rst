IO del robot
============

.. toctree:: 
    :maxdepth: 5

Establecer la salida digital de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer la salida digital de la caja de control
    * @param  [in] id  Número de io, rango [0~15]
    * @param  [in] status 0-desactivado, 1-activado
    * @param  [in] smooth 0-sin suavizado, 1-suavizado
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    int SetDO(int id, int status, int smooth, int block); 

Establecer la salida digital de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer la salida digital de la herramienta
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in] status 0-desactivado, 1-activado
    * @param  [in] smooth 0-sin suavizado, 1-suavizado
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    int SetToolDO(int id, int status, int smooth, int block); 

Establecer la salida analógica de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer la salida analógica de la caja de control
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in] value Porcentaje del valor de corriente o voltaje, rango [0~100] corresponde al valor de corriente [0~20mA] o voltaje [0~10V]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    int SetAO(int id, double value, int block); 

Establecer la salida analógica de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer la salida analógica de la herramienta
    * @param  [in] id  Número de io, rango [0]
    * @param  [in] value Porcentaje del valor de corriente o voltaje, rango [0~100] corresponde al valor de corriente [0~20mA] o voltaje [0~10V]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    int SetToolAO(int id, double value, int block); 

Ejemplo de código de establecimiento de salidas digitales y analógicas
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAODO(Robot robot)
    {

        int status = 1;
        int smooth = 0;
        int block = 0;

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            robot.Sleep(300);
        }

        status = 0;

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            robot.Sleep(300);
        }

        status = 1;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            robot.Sleep(1000);
        }

        status = 0;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            robot.Sleep(1000);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetAO(0, i, block);
            robot.Sleep(30);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetToolAO(0, i, block);
            robot.Sleep(30);
        }

        robot.CloseRPC();
        return 0;
    }

Obtener la entrada digital de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la entrada digital de la caja de control
    * @param  [in] id  Número de io, rango [0~15]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] level  0-nivel bajo, 1-nivel alto
    * @return  Código de error
    */   
    int GetDI(int id, int block, int[] level);

Obtener la entrada digital de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la entrada digital de la herramienta
    * @param  [in] id    Número de io, rango [0~1]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] level 0-nivel bajo, 1-nivel alto
    * @return  Código de error
    */   
    int GetToolDI(int id, int block, int[] level);

Obtener la entrada analógica de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la entrada analógica de la caja de control
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] persent Porcentaje del valor de corriente o voltaje de entrada, rango [0~100] corresponde al valor de corriente [0~20mS] o voltaje [0~10V]
    * @return  Código de error
    */   
    int GetAI(int id, int block, double[] persent)

Obtener la entrada analógica de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener la entrada analógica de la herramienta
    * @param  [in] id  Número de io, rango [0]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] persent Porcentaje del valor de corriente o voltaje de entrada, rango [0~100] corresponde al valor de corriente [0~20mS] o voltaje [0~10V]
    * @return  Código de error
    */   
    int GetToolAI(int id, int block, double[] persent)

Obtener el estado del botón de registro de puntos del extremo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el estado del botón de registro de puntos del extremo del robot
    * @param  [out] state Estado del botón, 0-pulsado, 1-liberado
    * @return  Código de error
    */   
    int GetAxlePointRecordBtnState(int[] state)

Obtener el estado de salida DO del extremo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el estado de salida DO del extremo del robot
    * @param  [out] do_state Estado de salida DO, do0~do1 corresponden a bit1~bit2, comenzando desde bit0
    * @return  Código de error
    */   
    int GetToolDO(int[] do_state)

Obtener el estado de salida DO del controlador del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el estado de salida DO del controlador del robot
    * @param  [out] do_state_h Estado de salida DO, co0~co7 corresponden a bit0~bit7
    * @param  [out] do_state_l Estado de salida DO, do0~do7 corresponden a bit0~bit7
    * @return  Código de error
    */   
    int GetDO(int[] do_state_h, int[] do_state_l)

Ejemplo de código de obtención del estado DI y DO del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetDIAI(Robot robot)
    {
        int status = 1;
        int smooth = 0;
        int block = 0;
        int[] di =new int[]{0}, tool_di =new int[] {0};
        double[] ai =new double[] {0}, tool_ai = new double[]{0};
        double value = 0.0;


        robot.GetDI(0, block, di);
        System.out.println("di0:"+di[0]);

        robot.GetToolDI(1, block, tool_di);
        System.out.println("tool_di1:"+ tool_di[0]);

        robot.GetAI(0, block, ai);
        System.out.println("ai0:"+ ai[0]);

        robot.GetToolAI(0, block, tool_ai);
        System.out.println("tool_ai0:"+ tool_ai[0]);

        int[] _button_state=new int[]{0};
        robot.GetAxlePointRecordBtnState(_button_state);
        System.out.println("_button_state is: "+ _button_state[0]);

        int[] tool_do_state=new int[]{0};
        robot.GetToolDO(tool_do_state);
        System.out.println("tool DO state is: "+ tool_do_state[0]);

        int[] do_state_h=new int[]{0};
        int[] do_state_l=new int[]{0};
        robot.GetDO(do_state_h, do_state_l);
        System.out.println("DO state high is: "+do_state_h[0]+", DO state low is: "+ do_state_l[0]);

        return 0;
    }

Esperar la entrada digital de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Esperar la entrada digital de la caja de control
    * @param  [in]  id  Número de io, rango [0~15]
    * @param  [in]  status 0-desactivado, 1-activado
    * @param  [in]  max_time  Tiempo máximo de espera, unidad ms
    * @param  [in]  opt  Estrategia tras el tiempo de espera, 0-el programa se detiene y muestra el tiempo de espera agotado, 1-ignorar el tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    int WaitDI(int id, int status, int max_time, int opt); 

Esperar múltiples entradas digitales de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Esperar múltiples entradas digitales de la caja de control
    * @param  [in] mode 0-múltiples en AND, 1-múltiples en OR
    * @param  [in] id  Número de io, bit0~bit7 corresponden a DI0~DI7, bit8~bit15 corresponden a CI0~CI7
    * @param  [in] status 0-desactivado, 1-activado
    * @param  [in] max_time  Tiempo máximo de espera, unidad ms
    * @param  [in] opt  Estrategia tras el tiempo de espera, 0-el programa se detiene y muestra el tiempo de espera agotado, 1-ignorar el tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    int WaitMultiDI(int mode, int id, int status, int max_time, int opt); 

Esperar la entrada digital de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Esperar la entrada digital de la herramienta
    * @param  [in]  id  Número de io, rango [0~1]
    * @param  [in]  status 0-desactivado, 1-activado
    * @param  [in]  max_time  Tiempo máximo de espera, unidad ms
    * @param  [in]  opt  Estrategia tras el tiempo de espera, 0-el programa se detiene y muestra el tiempo de espera agotado, 1-ignorar el tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    int WaitToolDI(int id, int status, int max_time, int opt); 

Esperar la entrada analógica de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Esperar la entrada analógica de la caja de control
    * @param  [in]  id  Número de io, rango [0~1]
    * @param  [in]  sign 0-mayor que, 1-menor que
    * @param  [in]  value Porcentaje del valor de corriente o voltaje de entrada, rango [0~100] corresponde al valor de corriente [0~20mS] o voltaje [0~10V]
    * @param  [in]  max_time  Tiempo máximo de espera, unidad ms
    * @param  [in]  opt  Estrategia tras el tiempo de espera, 0-el programa se detiene y muestra el tiempo de espera agotado, 1-ignorar el tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    int WaitAI(int id, int sign, double value, int max_time, int opt);   

Esperar la entrada analógica de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Esperar la entrada analógica de la herramienta
    * @param  [in]  id  Número de io, rango [0]
    * @param  [in]  sign 0-mayor que, 1-menor que
    * @param  [in]  value Porcentaje del valor de corriente o voltaje de entrada, rango [0~100] corresponde al valor de corriente [0~20mS] o voltaje [0~10V]
    * @param  [in]  max_time  Tiempo máximo de espera, unidad ms
    * @param  [in]  opt  Estrategia tras el tiempo de espera, 0-el programa se detiene y muestra el tiempo de espera agotado, 1-ignorar el tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    int WaitToolAI(int id, int sign, double value, int max_time, int opt); 

Ejemplo de código de espera de señales de entrada digitales y analógicas de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestWaitDIAI(Robot robot)
    {
        int rtn=-1;

        int status = 1;
        int smooth = 0;
        int block = 0;
        int di = 0, tool_di = 0;
        double ai = 0.0, tool_ai = 0.0;
        double value = 0.0;

        rtn = robot.WaitDI(0, 1, 1000, 1);
        System.out.println("WaitDI over; rtn is: "+ rtn);

        robot.WaitMultiDI(1, 3, 3, 1000, 1);
        System.out.println("WaitDI over; rtn is: "+ rtn);

        robot.WaitToolDI(1, 1, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);

        robot.WaitAI(0, 0, 50, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);

        robot.WaitToolAI(0, 0, 50, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);
        return 0;
    }

Establecer si la salida DO de la caja de control se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer si la salida DO de la caja de control se reinicia tras detener/pausar
    * @param resetFlag  0-no reiniciar; 1-reiniciar
    * @param reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag)

Establecer si la salida AO de la caja de control se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer si la salida AO de la caja de control se reinicia tras detener/pausar
    * @param resetFlag  0-no reiniciar; 1-reiniciar
    * @param reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag)

Establecer si la salida DO de la herramienta del extremo se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer si la salida DO de la herramienta del extremo se reinicia tras detener/pausar
    * @param resetFlag  0-no reiniciar; 1-reiniciar
    * @param reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetAxleDO(int resetFlag, int reloadFlag)

Establecer si la salida AO de la herramienta del extremo se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer si la salida AO de la herramienta del extremo se reinicia tras detener/pausar
    * @param resetFlag  0-no reiniciar; 1-reiniciar
    * @param reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetAxleAO(int resetFlag, int reloadFlag)
    
Establecer si la DO extendida se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer si la DO extendida se reinicia tras detener/pausar
    * @param resetFlag  0-no reiniciar; 1-reiniciar
    * @param reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetExtDO(int resetFlag, int reloadFlag)
    
Establecer si la AO extendida se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer si la AO extendida se reinicia tras detener/pausar
    * @param resetFlag  0-no reiniciar; 1-reiniciar
    * @param reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetExtAO(int resetFlag, int reloadFlag)

Establecer si la salida de SmartTool se reinicia tras detener/pausar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer si la salida de SmartTool se reinicia tras detener/pausar
    * @param resetFlag  0-no reiniciar; 1-reiniciar
    * @param reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetSmartToolDO(int resetFlag, int reloadFlag)

Ejemplo de código de reinicio de salida tras detener/pausar el programa LUA
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestDOReset(Robot robot)
    {
        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, 1, 0, 0);
            robot.Sleep(200);
        }
        int resetFlag = 1;
        int resumeReloadFlag = 1;
        int rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetCtlBoxAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetAxleDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetAxleAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetExtDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetExtAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetSmartToolDO(resetFlag, resumeReloadFlag);
        robot.ProgramLoad(test.lua");
        robot.ProgramRun();
        robot.Sleep(2000);
        robot.PauseMotion();
        robot.Sleep(2000);
        robot.ResumeMotion();
        robot.Sleep(2000);
        robot.CloseRPC();
    }

Establecer la función del puerto CI configurable de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la función del puerto CI configurable de la caja de control
    * @param config Código de función de CI0-CI7;
    * 0-ninguna;1-inicio de arco exitoso;2-máquina de soldar preparada;3-detección de cinta transportadora;4-pausa;5-reanudar;6-inicio;7-parada;
    8-pausa/reanudar;9-inicio/parada;10-arrastre con pedal;11-moverse al origen de trabajo;12-conmutación manual/automático;
    13-búsqueda de posición de alambre de soldadura exitosa;14-interrupción de movimiento;15-iniciar programa principal;16-iniciar rebobinado;17-confirmación de inicio;
    18-señal de detección fotoeléctrica X;19-señal de detección fotoeléctrica Y;20-señal de entrada de parada de emergencia externa 1;21-señal de entrada de parada de emergencia externa 2;
    22-modo de reducción de nivel uno;23-modo de reducción de nivel dos;24-modo de reducción de nivel tres (parada);25-reanudar soldadura;26-terminar soldadura;
    27-activar arrastre asistido;28-desactivar arrastre asistido;29-activar/desactivar arrastre asistido;30-borrar todos los errores;
    31-conmutación manual/automático (nivel alto/bajo);32-habilitar;33-deshabilitar;34-habilitar/deshabilitar (flanco de subida/bajada);35-inicio/fin de seguimiento de punto fijo
    36-entrar en movimiento de velocidad de seguridad;37-bloqueo de arrastre del bucle de corriente;38-bloqueo asistido por sensor de fuerza
    * @return Código de error
    */
    public int SetDIConfig(int[] config)

Obtener la función del puerto CI configurable de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener la función del puerto CI configurable de la caja de control
    * @param config Código de función de CI0-CI7;
    * 0-ninguna;1-inicio de arco exitoso;2-máquina de soldar preparada;3-detección de cinta transportadora;4-pausa;5-reanudar;6-inicio;7-parada;
    8-pausa/reanudar;9-inicio/parada;10-arrastre con pedal;11-moverse al origen de trabajo;12-conmutación manual/automático;
    13-búsqueda de posición de alambre de soldadura exitosa;14-interrupción de movimiento;15-iniciar programa principal;16-iniciar rebobinado;17-confirmación de inicio;
    18-señal de detección fotoeléctrica X;19-señal de detección fotoeléctrica Y;20-señal de entrada de parada de emergencia externa 1;21-señal de entrada de parada de emergencia externa 2;
    22-modo de reducción de nivel uno;23-modo de reducción de nivel dos;24-modo de reducción de nivel tres (parada);25-reanudar soldadura;26-terminar soldadura;
    27-activar arrastre asistido;28-desactivar arrastre asistido;29-activar/desactivar arrastre asistido;30-borrar todos los errores;
    31-conmutación manual/automático (nivel alto/bajo);32-habilitar;33-deshabilitar;34-habilitar/deshabilitar (flanco de subida/bajada);35-inicio/fin de seguimiento de punto fijo
    36-entrar en movimiento de velocidad de seguridad;37-bloqueo de arrastre del bucle de corriente;38-bloqueo asistido por sensor de fuerza
    201-señal de entrada de parada de emergencia externa 1-doble canal; 202-señal de entrada de parada de emergencia externa 2-doble canal; 203-modo de reducción de nivel uno-doble canal;
    204-modo de reducción de nivel dos-doble canal; 205-modo de reducción de nivel tres-doble canal; 206-parada normal-doble canal; 207-muro de seguridad 1-doble canal; 208-muro de seguridad 2-doble canal;
    209-muro de seguridad 3-doble canal; 210-muro de seguridad 4-doble canal; 211-muro de seguridad 5-doble canal; 212-muro de seguridad 6-doble canal; 213-muro de seguridad 7-doble canal;
    214-muro de seguridad 8-doble canal; 215-reinicio de parada de seguridad-doble canal;
    * @return Código de error
    */
    public int GetDIConfig(int[] config)

Establecer la función del puerto CO configurable de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la función del puerto CO configurable de la caja de control
    * @param config Código de función de CO0-CO7;
    * 0-ninguna;1-error del robot;2-robot en movimiento;3-inicio/parada de pulverización;4-limpieza de pistola de pulverización;5-señal de suministro de gas;6-señal de inicio de arco;7-alimentación de alambre por impulsos;
    8-alimentación de alambre inversa;9-entrada JOB 1;10-entrada JOB 2;11-entrada JOB 3;12-control de inicio/parada de cinta transportadora;13-robot en pausa;14-llegada al origen de trabajo;
    15-llegada a la zona de interferencia;16-control de inicio/parada de búsqueda de posición de alambre de soldadura;17-inicio del robot completado;18-inicio/parada del programa;19-modo automático/manual;20-señal de salida de parada de emergencia 1-seguridad;
    21-señal de salida de parada de emergencia 2-seguridad;22-ejecución/parada del programa de script LUA;23-salida de estado de seguridad-seguridad;24-salida de estado de parada protectora-seguridad;
    25-robot en movimiento-seguridad;26-modo de reducción del robot-seguridad;27-modo no reducido del robot-seguridad;28-robot no detenido;29-error del robot-error de punto de instrucción;
    30-error del robot-error del accionamiento;31-error del robot-error de fuera del límite suave;32-error del robot-error de colisión;33-error del robot-error del número de esclavos activos;
    34-error del robot-error de esclavo;35-error del robot-error de IO;36-error del robot-error de pinza;37-error del robot-error de archivo;38-error del robot-error de pose singular;
    39-error del robot-error de comunicación del accionamiento;40-error del robot-error de parámetro;41-error del robot-error de eje externo fuera del límite suave;42-advertencia del robot-advertencia;
    43-advertencia del robot-advertencia de puerta de seguridad;44-advertencia del robot-advertencia de movimiento;45-advertencia del robot-advertencia de zona de interferencia;46-advertencia del robot-advertencia de muro de seguridad;
    47-estado de habilitación;48-elevación automática en curso tras desconexión;49-advertencia de interferencia del cubo 1;50-advertencia de interferencia del cubo 2;51-advertencia de interferencia del cubo 3;52-advertencia de interferencia del cubo 4;
    * @return Código de error
    */
    public int SetDOConfig(int[] config)

Obtener la función del puerto CO configurable de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener la función del puerto CO configurable de la caja de control
    * @param config Código de función de CO0-CO7;
    * 0-ninguna;1-error del robot;2-robot en movimiento;3-inicio/parada de pulverización;4-limpieza de pistola de pulverización;5-señal de suministro de gas;6-señal de inicio de arco;7-alimentación de alambre por impulsos;
    8-alimentación de alambre inversa;9-entrada JOB 1;10-entrada JOB 2;11-entrada JOB 3;12-control de inicio/parada de cinta transportadora;13-robot en pausa;14-llegada al origen de trabajo;
    15-llegada a la zona de interferencia;16-control de inicio/parada de búsqueda de posición de alambre de soldadura;17-inicio del robot completado;18-inicio/parada del programa;19-modo automático/manual;20-señal de salida de parada de emergencia 1-seguridad;
    21-señal de salida de parada de emergencia 2-seguridad;22-ejecución/parada del programa de script LUA;23-salida de estado de seguridad-seguridad;24-salida de estado de parada protectora-seguridad;
    25-robot en movimiento-seguridad;26-modo de reducción del robot-seguridad;27-modo no reducido del robot-seguridad;28-robot no detenido;29-error del robot-error de punto de instrucción;
    30-error del robot-error del accionamiento;31-error del robot-error de fuera del límite suave;32-error del robot-error de colisión;33-error del robot-error del número de esclavos activos;
    34-error del robot-error de esclavo;35-error del robot-error de IO;36-error del robot-error de pinza;37-error del robot-error de archivo;38-error del robot-error de pose singular;
    39-error del robot-error de comunicación del accionamiento;40-error del robot-error de parámetro;41-error del robot-error de eje externo fuera del límite suave;42-advertencia del robot-advertencia;
    43-advertencia del robot-advertencia de puerta de seguridad;44-advertencia del robot-advertencia de movimiento;45-advertencia del robot-advertencia de zona de interferencia;46-advertencia del robot-advertencia de muro de seguridad;
    47-estado de habilitación;48-elevación automática en curso tras desconexión;49-advertencia de interferencia del cubo 1;50-advertencia de interferencia del cubo 2;51-advertencia de interferencia del cubo 3;52-advertencia de interferencia del cubo 4;
    201-señal de salida de parada de emergencia 1-doble canal; 202-señal de salida de parada de emergencia 2-doble canal; 203-salida de estado de seguridad-doble canal; 204-salida de estado de parada protectora-doble canal; 205-robot en movimiento-doble canal;
	206-modo de reducción del robot-doble canal; 207-modo no reducido del robot-doble canal;
    * @return Código de error
    */
    public int GetDOConfig(int[] config)

Establecer la función del puerto End-CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer la función del puerto End-CI configurable del extremo
    * @param config Código de función de End CI0-CI1;
    * 0-ninguna;1-interruptor de la herramienta de enseñanza por arrastre;2-señal de registro de punto;3-conmutación manual/automático (señal de pulso);4-inicio/parada del registro TPD;5-pausar movimiento;
    6-reanudar movimiento;7-inicio;8-parada;9-pausa/reanudar;10-inicio/parada;11-activar arrastre asistido por sensor de fuerza;12-desactivar arrastre asistido por sensor de fuerza;
    13-activar/desactivar arrastre asistido por sensor de fuerza;14-señal de detección láser X;15-señal de detección láser Y;16-movimiento PTP al origen de trabajo;17-interrupción de movimiento, detener el movimiento actual según la señal;
    18-iniciar programa principal;19-iniciar rebobinado;20-confirmación de inicio;21-reanudar soldadura;22-terminar soldadura;23-borrar errores;24-conmutación manual/automático (nivel alto/bajo)
    25-habilitar;26-deshabilitar;27-habilitar/deshabilitar;28-señal de inicio/parada del seguimiento servo láser;
    * @return Código de error
    */
    public int SetToolDIConfig(int[] config)

Obtener la función del puerto End-CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener la función del puerto End-CI configurable del extremo
    * @param config Código de función de End CI0-CI1;
    * 0-ninguna;1-interruptor de la herramienta de enseñanza por arrastre;2-señal de registro de punto;3-conmutación manual/automático (señal de pulso);4-inicio/parada del registro TPD;5-pausar movimiento;
    6-reanudar movimiento;7-inicio;8-parada;9-pausa/reanudar;10-inicio/parada;11-activar arrastre asistido por sensor de fuerza;12-desactivar arrastre asistido por sensor de fuerza;
    13-activar/desactivar arrastre asistido por sensor de fuerza;14-señal de detección láser X;15-señal de detección láser Y;16-movimiento PTP al origen de trabajo;17-interrupción de movimiento, detener el movimiento actual según la señal;
    18-iniciar programa principal;19-iniciar rebobinado;20-confirmación de inicio;21-reanudar soldadura;22-terminar soldadura;23-borrar errores;24-conmutación manual/automático (nivel alto/bajo)
    25-habilitar;26-deshabilitar;27-habilitar/deshabilitar;28-señal de inicio/parada del seguimiento servo láser;
    * @return Código de error
    */
    public int GetToolDIConfig(int[] config)
    
Configuración de la función CI de doble canal de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Configuración de la función CI de doble canal de seguridad
    * @param [in] ID ID de doble canal; [0-3]
    * @param [in] config Configuración de función; 0-sin configuración; 201-señal de entrada de parada de emergencia externa 1; 202-señal de entrada de parada de emergencia externa 2; 203-modo de reducción de nivel uno; 204-modo de reducción de nivel dos; 205-modo de reducción de nivel tres;
                        206-parada normal; 207-muro de seguridad 1; 208-muro de seguridad 2; 209-muro de seguridad 3; 210-muro de seguridad 4; 211-muro de seguridad 5; 212-muro de seguridad 6; 213-muro de seguridad 7;
                        214-muro de seguridad 8; 215-reinicio de parada de seguridad;
    * @return Código de error
    */
    public int SetSafetyDIConfig(int ID, int config)
        
Configuración de la función CO de doble canal de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Configuración de la función CO de doble canal de seguridad
    * @param [in] ID ID de doble canal; [0-3]
    * @param [in] config Configuración de función; 0-sin configuración; 201-señal de salida de parada de emergencia 1; 202-señal de salida de parada de emergencia 2; 203-salida de estado de seguridad; 204-salida de estado de parada protectora; 205-robot en movimiento;
                        206-modo de reducción del robot; 207-modo no reducido del robot;
    * @return Código de error
    */
    public int SetSafetyDOConfig(int ID, int config)
            
Verificación de establecimiento-lectura-borrado de la configuración de la función CI/CO de doble canal de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:
    
    public static int TestSafetyIOConfig(Robot robot)
    {
        int[] getDIConfig = new int[8];
        int rtn = robot.SetSafetyDIConfig(0, 201);
        System.out.printf("SetSafetyDIConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDIConfig(1, 202);
        System.out.printf("SetSafetyDIConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDIConfig(2, 203);
        System.out.printf("SetSafetyDIConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDIConfig(3, 204);
        System.out.printf("SetSafetyDIConfig rtn is %d\n", rtn);
        rtn = robot.GetDIConfig(getDIConfig);
        System.out.printf("GetDIConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDIConfig[0], getDIConfig[1], getDIConfig[2], getDIConfig[3], getDIConfig[4], getDIConfig[5], getDIConfig[6], getDIConfig[7]);

        rtn = robot.SetSafetyDIConfig(0, 0);
        System.out.printf("SetSafetyDIConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDIConfig(1, 0);
        System.out.printf("SetSafetyDIConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDIConfig(2, 0);
        System.out.printf("SetSafetyDIConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDIConfig(3, 0);
        System.out.printf("SetSafetyDIConfig rtn is %d\n", rtn);
        rtn = robot.GetDIConfig(getDIConfig);
        System.out.printf("GetDIConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDIConfig[0], getDIConfig[1], getDIConfig[2], getDIConfig[3], getDIConfig[4], getDIConfig[5], getDIConfig[6], getDIConfig[7]);


        int[] getDOConfig = new int[8];
        rtn = robot.SetSafetyDOConfig(0, 204);
        System.out.printf("SetSafetyDOConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDOConfig(1, 205);
        System.out.printf("SetSafetyDOConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDOConfig(2, 206);
        System.out.printf("SetSafetyDOConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDOConfig(3, 207);
        System.out.printf("SetSafetyDOConfig rtn is %d\n", rtn);
        rtn = robot.GetDOConfig(getDOConfig);
        System.out.printf("GetDOConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDOConfig[0], getDOConfig[1], getDOConfig[2], getDOConfig[3], getDOConfig[4], getDOConfig[5], getDOConfig[6], getDOConfig[7]);

        rtn = robot.SetSafetyDOConfig(0, 0);
        System.out.printf("SetSafetyDOConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDOConfig(1, 0);
        System.out.printf("SetSafetyDOConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDOConfig(2, 0);
        System.out.printf("SetSafetyDOConfig rtn is %d\n", rtn);
        rtn = robot.SetSafetyDOConfig(3, 0);
        System.out.printf("SetSafetyDOConfig rtn is %d\n", rtn);
        rtn = robot.GetDOConfig(getDOConfig);
        System.out.printf("GetDOConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDOConfig[0], getDOConfig[1], getDOConfig[2], getDOConfig[3], getDOConfig[4], getDOConfig[5], getDOConfig[6], getDOConfig[7]);

        robot.Sleep(2000);
        robot.Sleep(1000);
        return 0;
    }
    
Establecer el estado válido del CI configurable de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el estado válido del CI configurable de la caja de control
    * @param config Estado válido de los puertos CI0-CI7; 0-nivel alto válido; 1-nivel bajo válido
    * @return Código de error
    */
    public int SetDIConfigLevel(int[] config)
        
Obtener el estado válido del CI configurable de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el estado válido del CI configurable de la caja de control
    * @param config Estado válido de los puertos CI0-CI7; 0-nivel alto válido; 1-nivel bajo válido
    * @return Código de error
    */
    public int GetDIConfigLevel(int[] config)
        
Establecer el estado válido del CO configurable de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el estado válido del CO configurable de la caja de control
    * @param config Estado válido de los puertos CO0-CO7; 0-nivel alto válido; 1-nivel bajo válido
    * @return Código de error
    */
    public int SetDOConfigLevel(int[] config)

Obtener el estado válido del CO configurable de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el estado válido del CO configurable de la caja de control
    * @param config Estado válido de los puertos CO0-CO7; 0-nivel alto válido; 1-nivel bajo válido
    * @return Código de error
    */
    public int GetDOConfigLevel(int[] config)
    
Establecer el estado válido del CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el estado válido del CI configurable del extremo
    * @param config Estado válido de los puertos CI0-CI1; 0-nivel alto válido; 1-nivel bajo válido
    * @return Código de error
    */
    public int SetToolDIConfigLevel(int[] config)
    
Obtener el estado válido del CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el estado válido del CI configurable del extremo
    * @param config Estado válido de los puertos CI0-CI1; 0-nivel alto válido; 1-nivel bajo válido
    * @return Código de error
    */
    public int GetToolDIConfigLevel(int[] config)
    
Establecer el estado válido del DI estándar de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el estado válido del DI estándar de la caja de control
    * @param config Estado válido de los puertos DI0-DI7; 0-nivel alto válido; 1-nivel bajo válido
    * @return Código de error
    */
    public int SetStandardDILevel(int[] config)
    
Obtener el estado válido del DI estándar de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el estado válido del DI estándar de la caja de control
    * @param config Estado válido de los puertos DI0-DI7; 0-nivel alto válido; 1-nivel bajo válido
    * @return Código de error
    */
    public int GetStandardDILevel(int[] config)

Establecer el estado válido del DO estándar de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Establecer el estado válido del DO estándar de la caja de control
    * @param config Estado válido de los puertos DO0-DO7; 0-nivel alto válido; 1-nivel bajo válido
    * @return Código de error
    */
    public int SetStandardDOLevel(int[] config)
    
Obtener el estado válido del DO estándar de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Obtener el estado válido del DO estándar de la caja de control
    * @param config Estado válido de los puertos DO0-DO7; 0-nivel alto válido; 1-nivel bajo válido
    * @return Código de error
    */
    public int GetStandardDOLevel(int[] config)
        
Ejemplo de código de configuración de IO del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    public static int TestIOConfig(Robot robot) {
        int[] setDIConfig = new int[]{1, 2, 3, 4, 5, 6, 7, 8};
        int[] getDIConfig = new int[8];
        int rtn = robot.SetDIConfig(setDIConfig);
        System.out.println("SetDIConfig rtn is " + rtn);
        rtn = robot.GetDIConfig(getDIConfig);
        System.out.println("GetDIConfig rtn is " + rtn + ", value is " + 
            getDIConfig[0] + " " + getDIConfig[1] + " " + getDIConfig[2] + " " + getDIConfig[3] + " " + 
            getDIConfig[4] + " " + getDIConfig[5] + " " + getDIConfig[6] + " " + getDIConfig[7]);

        int[] setDOConfig = new int[]{9, 10, 11, 12, 13, 14, 15, 16};
        int[] getDOConfig = new int[8];
        rtn = robot.SetDOConfig(setDOConfig);
        System.out.println("SetDOConfig rtn is " + rtn);
        rtn = robot.GetDOConfig(getDOConfig);
        System.out.println("GetDOConfig rtn is " + rtn + ", value is " + 
            getDOConfig[0] + " " + getDOConfig[1] + " " + getDOConfig[2] + " " + getDOConfig[3] + " " + 
            getDOConfig[4] + " " + getDOConfig[5] + " " + getDOConfig[6] + " " + getDOConfig[7]);

        int[] setToolDIConfig = new int[]{17, 18};
        int[] getToolDIConfig = new int[2];
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        System.out.println("SetToolDIConfig rtn is " + rtn);
        rtn = robot.GetToolDIConfig(getToolDIConfig);
        System.out.println("GetToolDIConfig rtn is " + rtn + ", value is " + getToolDIConfig[0] + " " + getToolDIConfig[1]);

        int[] setDIConfigLevel = new int[]{1, 1, 1, 1, 0, 0, 0, 0};
        int[] getDIConfigLevel = new int[8];
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        System.out.println("SetDIConfigLevel rtn is " + rtn);
        rtn = robot.GetDIConfigLevel(getDIConfigLevel);
        System.out.println("GetDIConfigLevel rtn is " + rtn + ", value is " + 
            getDIConfigLevel[0] + " " + getDIConfigLevel[1] + " " + getDIConfigLevel[2] + " " + getDIConfigLevel[3] + " " + 
            getDIConfigLevel[4] + " " + getDIConfigLevel[5] + " " + getDIConfigLevel[6] + " " + getDIConfigLevel[7]);

        int[] setDOConfigLevel = new int[]{0, 0, 0, 0, 1, 1, 1, 1};
        int[] getDOConfigLevel = new int[8];
        rtn = robot.SetDOConfigLevel(setDOConfigLevel);
        System.out.println("SetDOConfigLevel rtn is " + rtn);
        rtn = robot.GetDOConfigLevel(getDOConfigLevel);
        System.out.println("GetDOConfigLevel rtn is " + rtn + ", value is " + 
            getDOConfigLevel[0] + " " + getDOConfigLevel[1] + " " + getDOConfigLevel[2] + " " + getDOConfigLevel[3] + " " + 
            getDOConfigLevel[4] + " " + getDOConfigLevel[5] + " " + getDOConfigLevel[6] + " " + getDOConfigLevel[7]);

        int[] setToolDIConfigLevel = new int[]{1, 0};
        int[] getToolDIConfigLevel = new int[2];
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        System.out.println("SetToolDIConfigLevel rtn is " + rtn);
        rtn = robot.GetToolDIConfigLevel(getToolDIConfigLevel);
        System.out.println("GetToolDIConfigLevel rtn is " + rtn + ", value is " + getToolDIConfigLevel[0] + " " + getToolDIConfigLevel[1]);

        int[] setStandardDILevel = new int[]{1, 1, 1, 1, 0, 0, 0, 0};
        int[] getStandardDILevel = new int[8];
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        System.out.println("SetStandardDILevel rtn is " + rtn);
        rtn = robot.GetStandardDILevel(getStandardDILevel);
        System.out.println("GetStandardDILevel rtn is " + rtn + ", value is " + 
            getStandardDILevel[0] + " " + getStandardDILevel[1] + " " + getStandardDILevel[2] + " " + getStandardDILevel[3] + " " + 
            getStandardDILevel[4] + " " + getStandardDILevel[5] + " " + getStandardDILevel[6] + " " + getStandardDILevel[7]);

        int[] setStandardDOLevel = new int[]{0, 0, 0, 0, 1, 1, 1, 1};
        int[] getStandardDOLevel = new int[8];
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        System.out.println("SetStandardDOLevel rtn is " + rtn);
        rtn = robot.GetStandardDOLevel(getStandardDOLevel);
        System.out.println("GetStandardDOLevel rtn is " + rtn + ", value is " + 
            getStandardDOLevel[0] + " " + getStandardDOLevel[1] + " " + getStandardDOLevel[2] + " " + getStandardDOLevel[3] + " " + 
            getStandardDOLevel[4] + " " + getStandardDOLevel[5] + " " + getStandardDOLevel[6] + " " + getStandardDOLevel[7]);

        robot.Sleep(2000);
        return 0;
    }