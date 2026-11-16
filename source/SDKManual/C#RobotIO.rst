IO del robot
============

.. toctree:: 
    :maxdepth: 5

Establecer la salida digital del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer la salida digital del armario de control
    * @param  [in] id  Número de io, rango [0~15]
    * @param  [in] status 0-desactivado, 1-activado
    * @param  [in] smooth 0-sin suavizado, 1-suavizado
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    int SetDO(int id, byte status, byte smooth, byte block); 

Establecer la salida digital de la herramienta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer la salida digital de la herramienta
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in] status 0-desactivado, 1-activado
    * @param  [in] smooth 0-sin suavizado, 1-suavizado
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    int SetToolDO(int id, byte status, byte smooth, byte block); 

Establecer la salida analógica del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer la salida analógica del armario de control
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in] value Porcentaje del valor de corriente o tensión, rango [0~100] corresponde al valor de corriente [0~20mA] o tensión [0~10V]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    int SetAO(int id, float value, byte block); 

Establecer la salida analógica de la herramienta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer la salida analógica de la herramienta
    * @param  [in] id  Número de io, rango [0]
    * @param  [in] value Porcentaje del valor de corriente o tensión, rango [0~100] corresponde al valor de corriente [0~20mA] o tensión [0~10V]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    int SetToolAO(int id, float value, byte block);

Ejemplo de código de configuración de salidas digitales y analógicas
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos: 

    private void button14_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;


        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            Thread.Sleep(300);
        }

        status = 0;

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            Thread.Sleep(300);
        }

        status = 1;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            Thread.Sleep(1000);
        }

        status = 0;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetAO(0, i, block);
            Thread.Sleep(30);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetToolAO(0, i, block);
            Thread.Sleep(30);
        }

    }

Obtener la entrada digital del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la entrada digital del armario de control
    * @param  [in] id  Número de io, rango [0~15]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] result  0-nivel bajo, 1-nivel alto
    * @return  Código de error
    */   
    int GetDI(int id, byte block, ref byte level);

Obtener la entrada digital de la herramienta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la entrada digital de la herramienta
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] result  0-nivel bajo, 1-nivel alto
    * @return  Código de error
    */   
    int GetToolDI(int id, byte block, ref byte level); 

Obtener la entrada analógica del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la entrada analógica del armario de control
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] result  Porcentaje del valor de corriente o tensión de entrada, rango [0~100] corresponde al valor de corriente [0~20mS] o tensión [0~10V]
    * @return  Código de error
    */   
    int GetAI(int id, byte block, ref float persent); 

Obtener la entrada analógica de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener la entrada analógica de la herramienta
    * @param  [in] id  Número de io, rango [0]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] result  Porcentaje del valor de corriente o tensión de entrada, rango [0~100] corresponde al valor de corriente [0~20mS] o tensión [0~10V]
    * @return  Código de error
    */   
    int GetToolAI(int id, byte block, ref float persent); 

Obtener el estado del botón de registro del extremo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener el estado del botón de registro del extremo del robot
    * @param [out] state Estado del botón, 0-pulsado, 1-suelto
    * @return Código de error 
    */ 
    int GetAxlePointRecordBtnState(ref byte state); 

Obtener el estado de la salida DO del extremo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener el estado de la salida DO del extremo del robot 
    * @param [out] do_state Estado de la salida DO, do0~do1 corresponden a bit1~bit2, empezando desde bit0 
    * @return Código de error 
    */ 
    int GetToolDO(ref byte do_state);

Obtener el estado de la salida DO del controlador del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener el estado de la salida DO del controlador del robot 
    * @param [out] do_state_h Estado de la salida DO, co0~co7 corresponden a bit0~bit7 
    * @param [out] do_state_l Estado de la salida DO, do0~do7 corresponden a bit0~bit7
    * @return Código de error 
    */ 
    int GetDO(ref int do_state_h, ref int do_state_l);   

Ejemplo de código de obtención del estado DI y DO del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button15_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;

        robot.GetDI(0, block, ref di);
        Console.WriteLine($"di0: {di}");

        tool_di = (byte)robot.GetToolDI(1, block, ref tool_di);
        Console.WriteLine($"tool_di1: {tool_di}");

        robot.GetAI(0, block, ref ai);
        Console.WriteLine($"ai0: {ai}");

        tool_ai = robot.GetToolAI(0, block, ref tool_ai);
        Console.WriteLine($"tool_ai0: {tool_ai}");

        byte _button_state = 0;
        robot.GetAxlePointRecordBtnState(ref _button_state);
        Console.WriteLine($"_button_state is: {_button_state}");

        byte tool_do_state = 0;
        robot.GetToolDO(ref tool_do_state);
        Console.WriteLine($"tool DO state is: {tool_do_state}");

        int do_state_h = 0;
        int do_state_l = 0;
        robot.GetDO(ref do_state_h, ref do_state_l);
        Console.WriteLine($"DO state high is: {do_state_h}\n DO state low is: {do_state_l}");
    }

Esperar la entrada digital del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Esperar la entrada digital del armario de control
    * @param  [in] id  Número de io, rango [0~15]
    * @param  [in]  status 0-desactivado, 1-activado
    * @param  [in]  max_time  Tiempo máximo de espera, unidad ms
    * @param  [in]  opt  Estrategia tras tiempo de espera agotado, 0-el programa se detiene y muestra tiempo de espera agotado, 1-ignorar el aviso de tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    int WaitDI(int id, byte status, int max_time, int opt); 

Esperar múltiples entradas digitales del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Esperar múltiples entradas digitales del armario de control
    * @param  [in] mode 0-múltiples en AND, 1-múltiples en OR
    * @param  [in] id  Número de io, bit0~bit7 corresponden a DI0~DI7, bit8~bit15 corresponden a CI0~CI7
    * @param  [in]  status 0-desactivado, 1-activado
    * @param  [in]  max_time  Tiempo máximo de espera, unidad ms
    * @param  [in]  opt  Estrategia tras tiempo de espera agotado, 0-el programa se detiene y muestra tiempo de espera agotado, 1-ignorar el aviso de tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    int WaitMultiDI(int mode, int id, byte status, int max_time, int opt); 

Esperar la entrada digital de la herramienta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Esperar la entrada digital de la herramienta
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in]  status 0-desactivado, 1-activado
    * @param  [in]  max_time  Tiempo máximo de espera, unidad ms
    * @param  [in]  opt  Estrategia tras tiempo de espera agotado, 0-el programa se detiene y muestra tiempo de espera agotado, 1-ignorar el aviso de tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    int WaitToolDI(int id, byte status, int max_time, int opt); 

Esperar la entrada analógica del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Esperar la entrada analógica del armario de control
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in]  sign 0-mayor que, 1-menor que
    * @param  [in]  value Porcentaje del valor de corriente o tensión de entrada, rango [0~100] corresponde al valor de corriente [0~20mS] o tensión [0~10V]
    * @param  [in]  max_time  Tiempo máximo de espera, unidad ms
    * @param  [in]  opt  Estrategia tras tiempo de espera agotado, 0-el programa se detiene y muestra tiempo de espera agotado, 1-ignorar el aviso de tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    int WaitAI(int id, int sign, float value, int max_time, int opt);   

Esperar la entrada analógica de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Esperar la entrada analógica de la herramienta
    * @param  [in] id  Número de io, rango [0]
    * @param  [in]  sign 0-mayor que, 1-menor que
    * @param  [in]  value Porcentaje del valor de corriente o tensión de entrada, rango [0~100] corresponde al valor de corriente [0~20mS] o tensión [0~10V]
    * @param  [in]  max_time  Tiempo máximo de espera, unidad ms
    * @param  [in]  opt  Estrategia tras tiempo de espera agotado, 0-el programa se detiene y muestra tiempo de espera agotado, 1-ignorar el aviso de tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    int WaitToolAI(int id, int sign, float value, int max_time, int opt); 

Ejemplo de código de espera de señales de entrada digitales y analógicas del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnIOTest_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;

        int rtn = robot.WaitDI(0, 1, 1000, 1);
        Console.WriteLine("WaitDI over; rtn is: " + rtn);

        robot.WaitMultiDI(1, 3, 3, 1000, 1);
        Console.WriteLine("WaitMultiDI over; rtn is: " + rtn);

        robot.WaitToolDI(1, 1, 1000, 1);
        Console.WriteLine("WaitToolDI over; rtn is: " + rtn);

        robot.WaitAI(0, 0, 50, 1000, 1);
        Console.WriteLine("WaitAI over; rtn is: " + rtn);

        robot.WaitToolAI(0, 0, 50, 1000, 1);
        Console.WriteLine("WaitToolAI over; rtn is: " + rtn);
    }
    
Establecer si la salida DO del armario de control se restablece tras la parada/pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer si la salida DO del armario de control se restablece tras la parada/pausa
    * @param [in] resetFlag 0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag);

Establecer si la salida AO del armario de control se restablece tras la parada/pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer si la salida AO del armario de control se restablece tras la parada/pausa
    * @param [in] resetFlag  0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag);

Establecer si la salida DO de la herramienta del extremo se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer si la salida DO de la herramienta del extremo se restablece tras la parada/pausa
    * @param [in] resetFlag  0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetAxleDO(int resetFlag, int reloadFlag);

Establecer si la salida AO de la herramienta del extremo se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer si la salida AO de la herramienta del extremo se restablece tras la parada/pausa
    * @param [in] resetFlag 0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetAxleAO(int resetFlag, int reloadFlag);

Establecer si la salida DO extendida se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer si la salida DO extendida se restablece tras la parada/pausa
    * @param [in] resetFlag  0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return  Código de error
    */
    public int SetOutputResetExtDO(int resetFlag, int reloadFlag);

Establecer si la salida AO extendida se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer si la salida AO extendida se restablece tras la parada/pausa
    * @param [in] resetFlag 0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetExtAO(int resetFlag, int reloadFlag);

Establecer si la salida de SmartTool se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer si la salida de SmartTool se restablece tras la parada/pausa
    * @param [in] resetFlag 0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    public int SetOutputResetSmartToolDO(int resetFlag, int reloadFlag);

Ejemplo de código de restablecimiento de salidas tras la parada/pausa del programa LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestDOReset()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, 1, 0, 0);
            Thread.Sleep(200);
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

        robot.ProgramLoad("test.lua");
        robot.ProgramRun();

        Thread.Sleep(2000);
        robot.PauseMotion();
        Thread.Sleep(2000);
        robot.ResumeMotion();
        Thread.Sleep(2000);
    }

Establecer la función del puerto CI configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la función del puerto CI configurable del armario de control
    * @param [in] config Código de función de CI0-CI7;
    * 0-ninguna;1-éxito de inicio de arco;2-soldadora preparada;3-detección de cinta transportadora;4-pausa;5-reanudar;6-iniciar;7-detener;
    8-pausa/reanudar;9-iniciar/detener;10-arrastre por pedal;11-mover al origen de trabajo;12-conmutación manual/automático;
    13-éxito de búsqueda de posición del alambre de soldadura;14-interrupción de movimiento;15-iniciar programa principal;16-iniciar rebobinado;17-confirmación de inicio;
    18-señal de detección fotoeléctrica X;19-señal de detección fotoeléctrica Y;20-señal de entrada de parada de emergencia externa 1;21-señal de entrada de parada de emergencia externa 2;
    22-modo de reducción de nivel 1;23-modo de reducción de nivel 2;24-modo de reducción de nivel 3 (parada);25-reanudar soldadura;26-terminar soldadura;
    27-activar arrastre asistido;28-desactivar arrastre asistido;29-activar/desactivar arrastre asistido;30-borrar todos los errores;
    31-conmutación manual/automático (nivel alto/bajo);32-habilitar;33-deshabilitar;34-habilitar/deshabilitar (flanco de subida/bajada);35-inicio/fin de seguimiento de punto fijo
    36-entrar en movimiento a velocidad de seguridad;37-bloqueo de arrastre por bucle de corriente;38-bloqueo asistido por sensor de fuerza
    * @return Código de error
    */
    public int SetDIConfig(int[] config)

Obtener la función del puerto CI configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la función del puerto CI configurable del armario de control
    * @param [in] config Código de función de CI0-CI7;
    * 0-ninguna;1-éxito de inicio de arco;2-soldadora preparada;3-detección de cinta transportadora;4-pausa;5-reanudar;6-iniciar;7-detener;
    8-pausa/reanudar;9-iniciar/detener;10-arrastre por pedal;11-mover al origen de trabajo;12-conmutación manual/automático;
    13-éxito de búsqueda de posición del alambre de soldadura;14-interrupción de movimiento;15-iniciar programa principal;16-iniciar rebobinado;17-confirmación de inicio;
    18-señal de detección fotoeléctrica X;19-señal de detección fotoeléctrica Y;20-señal de entrada de parada de emergencia externa 1;21-señal de entrada de parada de emergencia externa 2;
    22-modo de reducción de nivel 1;23-modo de reducción de nivel 2;24-modo de reducción de nivel 3 (parada);25-reanudar soldadura;26-terminar soldadura;
    27-activar arrastre asistido;28-desactivar arrastre asistido;29-activar/desactivar arrastre asistido;30-borrar todos los errores;
    31-conmutación manual/automático (nivel alto/bajo);32-habilitar;33-deshabilitar;34-habilitar/deshabilitar (flanco de subida/bajada);35-inicio/fin de seguimiento de punto fijo
    36-entrar en movimiento a velocidad de seguridad;37-bloqueo de arrastre por bucle de corriente;38-bloqueo asistido por sensor de fuerza
    201-señal de entrada de parada de emergencia externa 1-doble canal; 202-señal de entrada de parada de emergencia externa 2-doble canal; 203-modo de reducción de nivel 1-doble canal;
    204-modo de reducción de nivel 2-doble canal; 205-modo de reducción de nivel 3-doble canal; 206-parada normal-doble canal; 207-pared de seguridad 1-doble canal; 208-pared de seguridad 2-doble canal;
    209-pared de seguridad 3-doble canal; 210-pared de seguridad 4-doble canal; 211-pared de seguridad 5-doble canal; 212-pared de seguridad 6-doble canal; 213-pared de seguridad 7-doble canal;
    214-pared de seguridad 8-doble canal; 215-restablecimiento de parada de seguridad-doble canal;
    * @return Código de error
    */
    public int GetDIConfig(out int[] config)

Establecer la función del puerto CO configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la función del puerto CO configurable del armario de control
    * @param [out] config Código de función de CO0-CO7;
    * 0-ninguna;1-error del robot;2-robot en movimiento;3-inicio/parada de pulverización;4-limpieza de pistola de pulverización;5-señal de suministro de aire;6-señal de inicio de arco;7-avance de alambre por pulsación;
    8-retroceso de alambre;9-entrada JOB 1;10-entrada JOB 2;11-entrada JOB 3;12-control de inicio/parada de cinta transportadora;13-robot en pausa;14-llegada al origen de trabajo;
    15-llegada a la zona de interferencia;16-control de inicio/parada de búsqueda de posición del alambre de soldadura;17-inicio del robot completado;18-inicio/parada del programa;19-modo automático/manual;20-señal de salida de parada de emergencia 1-seguridad;
    21-señal de salida de parada de emergencia 2-seguridad;22-inicio/parada del programa de script LUA;23-salida de estado de seguridad-seguridad;24-salida de estado de parada protectora-seguridad;
    25-robot en movimiento-seguridad;26-modo de reducción del robot-seguridad;27-modo no reducido del robot-seguridad;28-robot no detenido;29-error del robot-error de punto de instrucción;
    30-error del robot-error del accionamiento;31-error del robot-error de superación del límite software;32-error del robot-error de colisión;33-error del robot-error del número de esclavos activos;
    34-error del robot-error de esclavo;35-error del robot-error de IO;36-error del robot-error de pinza;37-error del robot-error de archivo;38-error del robot-error de posición singular;
    39-error del robot-error de comunicación del accionamiento;40-error del robot-error de parámetros;41-error del robot-error de superación del límite software del eje externo;42-advertencia del robot-advertencia;
    43-advertencia del robot-advertencia de puerta de seguridad;44-advertencia del robot-advertencia de movimiento;45-advertencia del robot-advertencia de zona de interferencia;46-advertencia del robot-advertencia de pared de seguridad;
    47-estado de habilitación;48-elevación automática en curso por rotura de hilo;49-advertencia de interferencia del cubo 1;50-advertencia de interferencia del cubo 2;51-advertencia de interferencia del cubo 3;52-advertencia de interferencia del cubo 4;
    * @return Código de error
    */
    public int SetDOConfig(int[] config)

Obtener la función del puerto CO configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la función del puerto CO configurable del armario de control
    * @param [out] config Código de función de CO0-CO7;
    * 0-ninguna;1-error del robot;2-robot en movimiento;3-inicio/parada de pulverización;4-limpieza de pistola de pulverización;5-señal de suministro de aire;6-señal de inicio de arco;7-avance de alambre por pulsación;
    8-retroceso de alambre;9-entrada JOB 1;10-entrada JOB 2;11-entrada JOB 3;12-control de inicio/parada de cinta transportadora;13-robot en pausa;14-llegada al origen de trabajo;
    15-llegada a la zona de interferencia;16-control de inicio/parada de búsqueda de posición del alambre de soldadura;17-inicio del robot completado;18-inicio/parada del programa;19-modo automático/manual;20-señal de salida de parada de emergencia 1-seguridad;
    21-señal de salida de parada de emergencia 2-seguridad;22-inicio/parada del programa de script LUA;23-salida de estado de seguridad-seguridad;24-salida de estado de parada protectora-seguridad;
    25-robot en movimiento-seguridad;26-modo de reducción del robot-seguridad;27-modo no reducido del robot-seguridad;28-robot no detenido;29-error del robot-error de punto de instrucción;
    30-error del robot-error del accionamiento;31-error del robot-error de superación del límite software;32-error del robot-error de colisión;33-error del robot-error del número de esclavos activos;
    34-error del robot-error de esclavo;35-error del robot-error de IO;36-error del robot-error de pinza;37-error del robot-error de archivo;38-error del robot-error de posición singular;
    39-error del robot-error de comunicación del accionamiento;40-error del robot-error de parámetros;41-error del robot-error de superación del límite software del eje externo;42-advertencia del robot-advertencia;
    43-advertencia del robot-advertencia de puerta de seguridad;44-advertencia del robot-advertencia de movimiento;45-advertencia del robot-advertencia de zona de interferencia;46-advertencia del robot-advertencia de pared de seguridad;
    47-estado de habilitación;48-elevación automática en curso por rotura de hilo;49-advertencia de interferencia del cubo 1;50-advertencia de interferencia del cubo 2;51-advertencia de interferencia del cubo 3;52-advertencia de interferencia del cubo 4;
    201-señal de salida de parada de emergencia 1-doble canal; 202-señal de salida de parada de emergencia 2-doble canal; 203-salida de estado de seguridad-doble canal; 204-salida de estado de parada protectora-doble canal; 205-robot en movimiento-doble canal;
	206-modo de reducción del robot-doble canal; 207-modo no reducido del robot-doble canal;
    * @return Código de error
    */
    public int GetDOConfig(out int[] config)

Configuración de la función CI de doble canal de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Configuración de la función CI de doble canal de seguridad
    * @param [in] ID ID del doble canal; [0-3]
    * @param [in] config Configuración de la función; 0-sin configuración; 201-señal de entrada de parada de emergencia externa 1; 202-señal de entrada de parada de emergencia externa 2; 203-modo de reducción de nivel 1; 204-modo de reducción de nivel 2; 205-modo de reducción de nivel 3;
                        206-parada normal; 207-pared de seguridad 1; 208-pared de seguridad 2; 209-pared de seguridad 3; 210-pared de seguridad 4; 211-pared de seguridad 5; 212-pared de seguridad 6; 213-pared de seguridad 7;
                        214-pared de seguridad 8; 215-restablecimiento de parada de seguridad;
    * @return Código de error
    */
    public int SetSafetyDIConfig(int ID, int config)

Configuración de la función CO de doble canal de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Configuración de la función CO de doble canal de seguridad
    * @param [in] ID ID del doble canal; [0-3]
    * @param [in] config Configuración de la función; 0-sin configuración; 201-señal de salida de parada de emergencia 1; 202-señal de salida de parada de emergencia 2; 203-salida de estado de seguridad; 204-salida de estado de parada protectora; 205-robot en movimiento;
                        206-modo de reducción del robot; 207-modo no reducido del robot;
    * @return Código de error
    */
    public int SetSafetyDOConfig(int ID, int config)

Ejemplo de código de verificación de la configuración de las funciones CI/CO de doble canal de seguridad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public void TestSafetyIOConfig()
    {
        int rtn = 0;

        rtn = robot.SetSafetyDIConfig(0, 201);
        Console.WriteLine($"SetSafetyDIConfig rtn is {rtn}");
        rtn = robot.SetSafetyDIConfig(1, 202);
        Console.WriteLine($"SetSafetyDIConfig rtn is {rtn}");
        rtn = robot.SetSafetyDIConfig(2, 203);
        Console.WriteLine($"SetSafetyDIConfig rtn is {rtn}");
        rtn = robot.SetSafetyDIConfig(3, 204);
        Console.WriteLine($"SetSafetyDIConfig rtn is {rtn}");

        int[] getDIConfig = new int[8];
        rtn = robot.GetDIConfig(out getDIConfig);
        Console.WriteLine($"GetDIConfig rtn is {rtn}, value is {string.Join(" ", getDIConfig)}");

        rtn = robot.SetSafetyDIConfig(0, 0);
        Console.WriteLine($"SetSafetyDIConfig rtn is {rtn}");
        rtn = robot.SetSafetyDIConfig(1, 0);
        Console.WriteLine($"SetSafetyDIConfig rtn is {rtn}");
        rtn = robot.SetSafetyDIConfig(2, 0);
        Console.WriteLine($"SetSafetyDIConfig rtn is {rtn}");
        rtn = robot.SetSafetyDIConfig(3, 0);
        Console.WriteLine($"SetSafetyDIConfig rtn is {rtn}");

        rtn = robot.GetDIConfig(out getDIConfig);
        Console.WriteLine($"GetDIConfig rtn is {rtn}, value is {string.Join(" ", getDIConfig)}");

        rtn = robot.SetSafetyDOConfig(0, 204);
        Console.WriteLine($"SetSafetyDOConfig rtn is {rtn}");
        rtn = robot.SetSafetyDOConfig(1, 205);
        Console.WriteLine($"SetSafetyDOConfig rtn is {rtn}");
        rtn = robot.SetSafetyDOConfig(2, 206);
        Console.WriteLine($"SetSafetyDOConfig rtn is {rtn}");
        rtn = robot.SetSafetyDOConfig(3, 207);
        Console.WriteLine($"SetSafetyDOConfig rtn is {rtn}");

        int[] getDOConfig = new int[8];
        rtn = robot.GetDOConfig(out getDOConfig);
        Console.WriteLine($"GetDOConfig rtn is {rtn}, value is {string.Join(" ", getDOConfig)}");

        rtn = robot.SetSafetyDOConfig(0, 0);
        Console.WriteLine($"SetSafetyDOConfig rtn is {rtn}");
        rtn = robot.SetSafetyDOConfig(1, 0);
        Console.WriteLine($"SetSafetyDOConfig rtn is {rtn}");
        rtn = robot.SetSafetyDOConfig(2, 0);
        Console.WriteLine($"SetSafetyDOConfig rtn is {rtn}");
        rtn = robot.SetSafetyDOConfig(3, 0);
        Console.WriteLine($"SetSafetyDOConfig rtn is {rtn}");

        rtn = robot.GetDOConfig(out getDOConfig);
        Console.WriteLine($"GetDOConfig rtn is {rtn}, value is {string.Join(" ", getDOConfig)}");
    }

Establecer la función del puerto End-CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer la función del puerto End-CI configurable del extremo
    * @param [in] config Código de función de End CI0-CI1;
    * 0-ninguna;1-interruptor de herramienta de enseñanza por arrastre;2-señal de registro de punto;3-conmutación manual/automático (señal de pulso);4-inicio/parada de registro TPD;5-pausar movimiento;
    6-reanudar movimiento;7-iniciar;8-detener;9-pausa/reanudar;10-iniciar/detener;11-activar arrastre asistido por sensor de fuerza;12-desactivar arrastre asistido por sensor de fuerza;
    13-activar/desactivar arrastre asistido por sensor de fuerza;14-señal de detección láser X;15-señal de detección láser Y;16-movimiento PTP al origen de trabajo;17-interrupción de movimiento, detener el movimiento actual según la señal;
    18-iniciar programa principal;19-iniciar rebobinado;20-confirmación de inicio;21-reanudar soldadura;22-terminar soldadura;23-borrar errores;24-conmutación manual/automático (nivel alto/bajo)
    25-habilitar;26-deshabilitar;27-habilitar/deshabilitar;28-señal de inicio/parada de seguimiento servo láser;
    * @return Código de error
    */
    public int SetToolDIConfig(int[] config)

Obtener la función del puerto End-CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener la función del puerto End-CI configurable del extremo
    * @param [out] config Código de función de End CI0-CI1;
    * 0-ninguna;1-interruptor de herramienta de enseñanza por arrastre;2-señal de registro de punto;3-conmutación manual/automático (señal de pulso);4-inicio/parada de registro TPD;5-pausar movimiento;
    6-reanudar movimiento;7-iniciar;8-detener;9-pausa/reanudar;10-iniciar/detener;11-activar arrastre asistido por sensor de fuerza;12-desactivar arrastre asistido por sensor de fuerza;
    13-activar/desactivar arrastre asistido por sensor de fuerza;14-señal de detección láser X;15-señal de detección láser Y;16-movimiento PTP al origen de trabajo;17-interrupción de movimiento, detener el movimiento actual según la señal;
    18-iniciar programa principal;19-iniciar rebobinado;20-confirmación de inicio;21-reanudar soldadura;22-terminar soldadura;23-borrar errores;24-conmutación manual/automático (nivel alto/bajo)
    25-habilitar;26-deshabilitar;27-habilitar/deshabilitar;28-señal de inicio/parada de seguimiento servo láser;
    * @return Código de error
    */
    public int GetToolDIConfig(out int[] config)
    
Establecer el estado activo del CI configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el estado activo del CI configurable del armario de control
    * @param [in] config Estado activo de los puertos CI0-CI7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    public int SetDIConfigLevel(int[] config)
        
Obtener el estado activo del CI configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado activo del CI configurable del armario de control
    * @param [out] config Estado activo de los puertos CI0-CI7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    public int GetDIConfigLevel(out int[] config)
        
Establecer el estado activo del CO configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el estado activo del CO configurable del armario de control
    * @param [in] config Estado activo de los puertos CO0-CO7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    public int SetDOConfigLevel(int[] config)

Obtener el estado activo del CO configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado activo del CO configurable del armario de control
    * @param [out] config Estado activo de los puertos CO0-CO7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    public int GetDOConfigLevel(out int[] config)
    
Establecer el estado activo del CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el estado activo del CI configurable del extremo
    * @param [in] config Estado activo de los puertos CI0-CI1; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    public int SetToolDIConfigLevel(int[] config)
    
Obtener el estado activo del CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado activo del CI configurable del extremo
    * @param [out] config Estado activo de los puertos CI0-CI1; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    public int GetToolDIConfigLevel(out int[] config)
    
Establecer el estado activo del DI estándar del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el estado activo del DI estándar del armario de control
    * @param [in] config Estado activo de los puertos DI0-DI7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    public int SetStandardDILevel(int[] config)
    
Obtener el estado activo del DI estándar del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado activo del DI estándar del armario de control
    * @param [out] config Estado activo de los puertos DI0-DI7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    public int GetStandardDILevel(out int[] config)

Establecer el estado activo del DO estándar del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Establecer el estado activo del DO estándar del armario de control
    * @param [in] config Estado activo de los puertos DO0-DO7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    public int SetStandardDOLevel(int[] config)
    
Obtener el estado activo del DO estándar del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Obtener el estado activo del DO estándar del armario de control
    * @param [out] config Estado activo de los puertos DO0-DO7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    public int GetStandardDOLevel(out int[] config)
        
Ejemplo de código de configuración de IO del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public void TestIOConfig()
    {
        int rtn = 0;

        // ---------- Probar la función del puerto CI configurable ----------
        int[] setDIConfig = new int[] { 3, 9, 1, 4, 5, 6, 7, 8 };
        rtn = robot.SetDIConfig(setDIConfig);
        Console.WriteLine($"SetDIConfig rtn is {rtn}");

        // Utilizar el parámetro out para recibir el array de configuración obtenido
        int[] getDIConfig;
        rtn = robot.GetDIConfig(out getDIConfig);  
        Console.WriteLine($"GetDIConfig rtn is {rtn}, value is {string.Join(" ", getDIConfig)}");

        // ---------- Probar la función del puerto CO configurable ----------
        int[] setDOConfig = new int[] { 9, 10, 11, 12, 13, 14, 15, 16 };
        rtn = robot.SetDOConfig(setDOConfig);
        Console.WriteLine($"SetDOConfig rtn is {rtn}");

        int[] getDOConfig;
        rtn = robot.GetDOConfig(out getDOConfig);
        Console.WriteLine($"GetDOConfig rtn is {rtn}, value is {string.Join(" ", getDOConfig)}");

        // ---------- Probar la función del puerto CI configurable del extremo ----------
        int[] setToolDIConfig = new int[] { 17, 18 };
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        Console.WriteLine($"SetToolDIConfig rtn is {rtn}");

        int[] getToolDIConfig;
        rtn = robot.GetToolDIConfig(out getToolDIConfig);
        Console.WriteLine($"GetToolDIConfig rtn is {rtn}, value is {string.Join(" ", getToolDIConfig)}");

        // ---------- Probar el estado activo del CI configurable del armario de control ----------
        int[] setDIConfigLevel = new int[] { 1, 1, 1, 1, 0, 0, 0, 0 };
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        Console.WriteLine($"SetDIConfigLevel rtn is {rtn}");

        int[] getDIConfigLevel;
        rtn = robot.GetDIConfigLevel(out getDIConfigLevel);
        Console.WriteLine($"GetDIConfigLevel rtn is {rtn}, value is {string.Join(" ", getDIConfigLevel)}");

        // ---------- Probar el estado activo del CO configurable del armario de control ----------
        int[] setDOConfigLevel = new int[] { 0, 0, 0, 0, 1, 1, 1, 1 };
        rtn = robot.SetDIConfigLevel(setDOConfigLevel);
        Console.WriteLine($"SetDOConfigLevel rtn is {rtn}");

        int[] getDOConfigLevel;
        rtn = robot.GetDOConfigLevel(out getDOConfigLevel);
        Console.WriteLine($"GetDOConfigLevel rtn is {rtn}, value is {string.Join(" ", getDOConfigLevel)}");

        // ---------- Probar el estado activo del CI configurable del extremo ----------
        int[] setToolDIConfigLevel = new int[] { 1, 0 };
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        Console.WriteLine($"SetToolDIConfigLevel rtn is {rtn}");

        int[] getToolDIConfigLevel;
        rtn = robot.GetToolDIConfigLevel(out getToolDIConfigLevel);
        Console.WriteLine($"GetToolDIConfigLevel rtn is {rtn}, value is {string.Join(" ", getToolDIConfigLevel)}");

        // ---------- Probar el estado activo del DI estándar del armario de control ----------
        int[] setStandardDILevel = new int[] { 1, 1, 1, 1, 0, 0, 0, 0 };
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        Console.WriteLine($"SetStandardDILevel rtn is {rtn}");

        int[] getStandardDILevel;
        rtn = robot.GetStandardDILevel(out getStandardDILevel);
        Console.WriteLine($"GetStandardDILevel rtn is {rtn}, value is {string.Join(" ", getStandardDILevel)}");

        // ---------- Probar el estado activo del DO estándar del armario de control ----------
        int[] setStandardDOLevel = new int[] { 0, 0, 0, 0, 1, 1, 1, 1 };
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        Console.WriteLine($"SetStandardDOLevel rtn is {rtn}");

        int[] getStandardDOLevel;
        rtn = robot.GetStandardDOLevel(out getStandardDOLevel);
        Console.WriteLine($"GetStandardDOLevel rtn is {rtn}, value is {string.Join(" ", getStandardDOLevel)}");

    }