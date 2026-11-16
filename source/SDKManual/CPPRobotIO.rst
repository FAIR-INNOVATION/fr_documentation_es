IO del robot
============

.. toctree:: 
    :maxdepth: 5

Establecer la salida digital del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer la salida digital del armario de control
    * @param  [in] id  Número de io, rango [0~15]
    * @param  [in] status 0-desactivado, 1-activado
    * @param  [in] smooth 0-sin suavizado, 1-suavizado
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    errno_t  SetDO(int id, uint8_t status, uint8_t smooth, uint8_t block);

Establecer la salida digital de la herramienta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer la salida digital de la herramienta
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in] status 0-desactivado, 1-activado
    * @param  [in] smooth 0-sin suavizado, 1-suavizado
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    errno_t  SetToolDO(int id, uint8_t status, uint8_t smooth, uint8_t block);

Establecer la salida analógica del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer la salida analógica del armario de control
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in] value Porcentaje del valor de corriente o tensión, rango [0~100] corresponde al valor de corriente [0~20mA] o tensión [0~10V]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    errno_t  SetAO(int id, float value, uint8_t block);

Establecer la salida analógica de la herramienta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer la salida analógica de la herramienta
    * @param  [in] id  Número de io, rango [0]
    * @param  [in] value Porcentaje del valor de corriente o tensión, rango [0~100] corresponde al valor de corriente [0~20mA] o tensión [0~10V]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @return  Código de error
    */
    errno_t  SetToolAO(int id, float value, uint8_t block);

Ejemplo de código de configuración de salidas digitales y analógicas
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestAODO(void)
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
         uint8_t status = 1;
         uint8_t smooth = 0;
         uint8_t block = 0;
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
             robot.SetAO(0, i * 40.96, block);
             robot.Sleep(30);
         }
         for (int i = 0; i < 100; i++)
         {
             robot.SetToolAO(0, i * 40.96, block);
             robot.Sleep(30);
         }
         robot.CloseRPC();
         return 0;
     }

Obtener la entrada digital del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener la entrada digital del armario de control
    * @param  [in] id  Número de io, rango [0~15]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] result  0-nivel bajo, 1-nivel alto
    * @return  Código de error
    */   
    errno_t  GetDI(int id, uint8_t block, uint8_t *result);

Obtener la entrada digital de la herramienta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener la entrada digital de la herramienta
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] result  0-nivel bajo, 1-nivel alto
    * @return  Código de error
    */   
    errno_t  GetToolDI(int id, uint8_t block, uint8_t *result);

Obtener la entrada analógica del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener la entrada analógica del armario de control
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] result  Porcentaje del valor de corriente o tensión de entrada, rango [0~100] corresponde al valor de corriente [0~20mS] o tensión [0~10V]
    * @return  Código de error
    */   
    errno_t  GetAI(int id, uint8_t block, float *result); 

Obtener la entrada analógica de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener la entrada analógica de la herramienta
    * @param  [in] id  Número de io, rango [0]
    * @param  [in] block  0-bloqueante, 1-no bloqueante
    * @param  [out] result  Porcentaje del valor de corriente o tensión de entrada, rango [0~100] corresponde al valor de corriente [0~20mS] o tensión [0~10V]
    * @return  Código de error
    */   
    errno_t  GetToolAI(int id, uint8_t block, float *result);

Obtener el estado del botón de registro del punto del extremo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Obtener el estado del botón de registro del punto del extremo del robot
     * @param [out] state Estado del botón, 0-pulsado, 1-suelto
     * @return Código de error
     */
    errno_t  GetAxlePointRecordBtnState(uint8_t *state);

Obtener el estado de la salida DO del extremo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Obtener el estado de la salida DO del extremo del robot
     * @param [out] do_state Estado de la salida DO, do0~do1 corresponden a bit1~bit2, empezando desde bit0
     * @return Código de error
     */
    errno_t  GetToolDO(uint8_t *do_state);

Obtener el estado de la salida DO del controlador del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Obtener el estado de la salida DO del controlador del robot
     * @param [out] do_state_h Estado de la salida DO, co0~co7 corresponden a bit0~bit7
     * @param [out] do_state_l Estado de la salida DO, do0~do7 corresponden a bit0~bit7
     * @return Código de error
     */
    errno_t  GetDO(uint8_t *do_state_h, uint8_t *do_state_l);

Ejemplo de código de obtención del estado DI y DO del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestGetDIAI(void)
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
         uint8_t status = 1;
         uint8_t smooth = 0;
         uint8_t block = 0;
         uint8_t di = 0, tool_di = 0;
         float ai = 0.0, tool_ai = 0.0;
         float value = 0.0;
         robot.GetDI(0, block, &di);
         printf("di0:%u\n", di);
         tool_di = robot.GetToolDI(1, block, &tool_di);
         printf("tool_di1:%u\n", tool_di);
         robot.GetAI(0, block, &ai);
         printf("ai0:%f\n", ai);
         tool_ai = robot.GetToolAI(0, block, &tool_ai);
         printf("tool_ai0:%f\n", tool_ai);
         uint8_t _button_state = 0;
         robot.GetAxlePointRecordBtnState(&_button_state);
         printf("_button_state is: %u\n", _button_state);
         uint8_t tool_do_state = 0;
         robot.GetToolDO(&tool_do_state);
         printf("tool DO state is: %u\n", tool_do_state);
         uint8_t do_state_h = 0;
         uint8_t do_state_l = 0;
         robot.GetDO(&do_state_h, &do_state_l);
         printf("DO state high is: %u \n DO state low is: %u\n", do_state_h, do_state_l);
         robot.CloseRPC();
         return 0;
     }

Esperar la entrada digital del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Esperar la entrada digital del armario de control
    * @param  [in] id  Número de io, rango [0~15]
    * @param  [in]  status 0-desactivado, 1-activado
    * @param  [in]  max_time  Tiempo máximo de espera, unidad ms
    * @param  [in]  opt  Estrategia tras tiempo de espera agotado, 0-el programa se detiene y muestra tiempo de espera agotado, 1-ignorar el aviso de tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    errno_t  WaitDI(int id, uint8_t status, int max_time, int opt);

Esperar múltiples entradas digitales del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t  WaitMultiDI(int mode, int id, uint8_t status, int max_time, int opt);

Esperar la entrada digital de la herramienta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Esperar la entrada digital de la herramienta
    * @param  [in] id  Número de io, rango [0~1]
    * @param  [in]  status 0-desactivado, 1-activado
    * @param  [in]  max_time  Tiempo máximo de espera, unidad ms
    * @param  [in]  opt  Estrategia tras tiempo de espera agotado, 0-el programa se detiene y muestra tiempo de espera agotado, 1-ignorar el aviso de tiempo de espera agotado y continuar la ejecución del programa, 2-esperar siempre
    * @return  Código de error
    */
    errno_t  WaitToolDI(int id, uint8_t status, int max_time, int opt);

Esperar la entrada analógica del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t  WaitAI(int id, int sign, float value, int max_time, int opt);  

Esperar la entrada analógica de la herramienta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t  WaitToolAI(int id, int sign, float value, int max_time, int opt); 

Ejemplo de código de espera de señales de entrada digitales y analógicas del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.2.0
    
.. code-block:: c++
    :linenos:

     int TestWaitDIAI(void)
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
         uint8_t status = 1;
         uint8_t smooth = 0;
         uint8_t block = 0;
         uint8_t di = 0, tool_di = 0;
         float ai = 0.0, tool_ai = 0.0;
         float value = 0.0;
         rtn = robot.WaitDI(0, 1, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitMultiDI(1, 3, 3, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitToolDI(1, 1, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitAI(0, 0, 50, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitToolAI(0, 0, 50, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }


Establecer si la salida DO del armario de control se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer si la salida DO del armario de control se restablece tras la parada/pausa
    * @param [in] resetFlag 0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    errno_t SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag = 0);

Establecer si la salida AO del armario de control se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer si la salida AO del armario de control se restablece tras la parada/pausa
    * @param [in] resetFlag  0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    errno_t SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag = 0);

Establecer si la salida DO de la herramienta del extremo se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer si la salida DO de la herramienta del extremo se restablece tras la parada/pausa
    * @param [in] resetFlag  0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return Código de error
    */
    errno_t SetOutputResetAxleDO(int resetFlag, int reloadFlag = 0);

Establecer si la salida AO de la herramienta del extremo se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer si la salida AO de la herramienta del extremo se restablece tras la parada/pausa
    * @param [in] resetFlag  0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return  Código de error
    */
    errno_t SetOutputResetAxleAO(int resetFlag, int reloadFlag = 0);

Establecer si la salida DO extendida se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer si la salida DO extendida se restablece tras la parada/pausa
    * @param [in] resetFlag  0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return  Código de error
    */
    errno_t SetOutputResetExtDO(int resetFlag, int reloadFlag = 0);

Establecer si la salida AO extendida se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer si la salida AO extendida se restablece tras la parada/pausa
    * @param [in] resetFlag  0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return  Código de error
    */
    errno_t SetOutputResetExtAO(int resetFlag, int reloadFlag = 0);

Establecer si la salida de SmartTool se restablece tras la parada/pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer si la salida de SmartTool se restablece tras la parada/pausa
    * @param [in] resetFlag  0-no restablecer; 1-restablecer
    * @param [in] reloadFlag Si se recarga tras reanudar la pausa, 0-no cargar; 1-cargar
    * @return  Código de error
    */
    errno_t SetOutputResetSmartToolDO(int resetFlag, int reloadFlag = 0);

Ejemplo de código de restablecimiento de salidas tras la parada/pausa del programa LUA
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    int TestDOReset(void)
    {
    ROBOT_STATE_PKG pkg = {};
    FRRobot robot;
    robot.LoggerInit();
    robot.SetLoggerLevel(3);
    int rtn = robot.RPC("192.168.58.2");
    if (rtn != 0)
    {
        return -1;
    }
    robot.SetReConnectParam(true, 30000, 500);
    for (int i = 0; i < 16; i++)
    {
        robot.SetDO(i, 1, 0, 0);
        robot.Sleep(200);
    }
    int resetFlag = 0;
    int resumeReloadFlag = 0;
    rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetCtlBoxAO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetAxleDO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetAxleAO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetExtDO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetExtAO(resetFlag, resumeReloadFlag);
    robot.SetOutputResetSmartToolDO(resetFlag, resumeReloadFlag);
    robot.ProgramLoad("test.lua");
    robot.ProgramRun();
    robot.Sleep(2000);
    robot.PauseMotion();
    robot.Sleep(2000);
    robot.ResumeMotion();
    robot.Sleep(2000);
    robot.CloseRPC();
    return 0;
    }

Establecer la función del puerto CI configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t SetDIConfig(int config[8]);

Obtener la función del puerto CI configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t GetDIConfig(int config[8]);

Establecer la función del puerto CO configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t SetDOConfig(int config[8]);

Obtener la función del puerto CO configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t GetDOConfig(int config[8]);

Establecer la función del puerto End-CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t SetToolDIConfig(int config[2]);

Obtener la función del puerto End-CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t GetToolDIConfig(int config[2]);
    
Establecer el estado activo del CI configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el estado activo del CI configurable del armario de control
    * @param [in] config Estado activo de los puertos CI0-CI7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    errno_t SetDIConfigLevel(int config[8]);
        
Obtener el estado activo del CI configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado activo del CI configurable del armario de control
    * @param [out] config Estado activo de los puertos CI0-CI7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    errno_t GetDIConfigLevel(int config[8]);
        
Establecer el estado activo del CO configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el estado activo del CO configurable del armario de control
    * @param [in] config Estado activo de los puertos CO0-CO7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    errno_t SetDOConfigLevel(int config[8]);

Obtener el estado activo del CO configurable del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado activo del CO configurable del armario de control
    * @param [out] config Estado activo de los puertos CO0-CO7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    errno_t GetDOConfigLevel(int config[8]);
    
Establecer el estado activo del CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el estado activo del CI configurable del extremo
    * @param [in] config Estado activo de los puertos CI0-CI1; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    errno_t SetToolDIConfigLevel(int config[2]);
    
Obtener el estado activo del CI configurable del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado activo del CI configurable del extremo
    * @param [out] config Estado activo de los puertos CI0-CI1; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    errno_t GetToolDIConfigLevel(int config[2]);
    
Establecer el estado activo del DI estándar del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el estado activo del DI estándar del armario de control
    * @param [in] config Estado activo de los puertos DI0-DI7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    errno_t SetStandardDILevel(int config[8]);
    
Obtener el estado activo del DI estándar del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado activo del DI estándar del armario de control
    * @param [out] config Estado activo de los puertos DI0-DI7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    errno_t GetStandardDILevel(int config[8]);

Establecer el estado activo del DO estándar del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Establecer el estado activo del DO estándar del armario de control
    * @param [in] config Estado activo de los puertos DO0-DO7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    errno_t SetStandardDOLevel(int config[8]);
    
Obtener el estado activo del DO estándar del armario de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener el estado activo del DO estándar del armario de control
    * @param [out] config Estado activo de los puertos DO0-DO7; 0-activo a nivel alto; 1-activo a nivel bajo
    * @return Código de error
    */
    errno_t GetStandardDOLevel(int config[8]);
        
Ejemplo de código de configuración de IO del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestIOConfig()
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
        int setDIConfig[8] = { 1, 2, 3, 4, 5, 6, 7, 8 };
        int getDIConfig[8] = { 0 };
        rtn = robot.SetDIConfig(setDIConfig);
        printf("SetDIConfig rtn is %d\n", rtn);
        rtn = robot.GetDIConfig(getDIConfig);
        printf("GetDIConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn, 
            getDIConfig[0], getDIConfig[1], getDIConfig[2], getDIConfig[3], getDIConfig[4], getDIConfig[5], getDIConfig[6], getDIConfig[7]);
        int setDOConfig[8] = { 9, 10, 11, 12, 13, 14, 15, 16 };
        int getDOConfig[8] = { 0 };
        rtn = robot.SetDOConfig(setDOConfig);
        printf("SetDOConfig rtn is %d\n", rtn);
        rtn = robot.GetDOConfig(getDOConfig);
        printf("GetDOConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDOConfig[0], getDOConfig[1], getDOConfig[2], getDOConfig[3], getDOConfig[4], getDOConfig[5], getDOConfig[6], getDOConfig[7]);
        int setToolDIConfig[2] = { 17, 18 };
        int getToolDIConfig[2] = { 0 };
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        printf("SetToolDIConfig rtn is %d\n", rtn);
        rtn = robot.GetToolDIConfig(getToolDIConfig);
        printf("GetToolDIConfig rtn is %d, value is %d %d \n", rtn, getToolDIConfig[0], getToolDIConfig[1]);
        int setDIConfigLevel[8] = { 1, 1, 1, 1, 0, 0, 0, 0 };
        int getDIConfigLevel[8] = { 0 };
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        printf("SetDIConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetDIConfigLevel(getDIConfigLevel);
        printf("GetDIConfigLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDIConfigLevel[0], getDIConfigLevel[1], getDIConfigLevel[2], getDIConfigLevel[3], getDIConfigLevel[4], getDIConfigLevel[5], getDIConfigLevel[6], getDIConfigLevel[7]);
        int setDOConfigLevel[8] = { 0, 0, 0, 0, 1, 1, 1, 1 };
        int getDOConfigLevel[8] = { 0 };
        rtn = robot.SetDOConfigLevel(setDOConfigLevel);
        printf("SetDOConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetDOConfigLevel(getDOConfigLevel);
        printf("GetDOConfigLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDOConfigLevel[0], getDOConfigLevel[1], getDOConfigLevel[2], getDOConfigLevel[3], getDOConfigLevel[4], getDOConfigLevel[5], getDOConfigLevel[6], getDOConfigLevel[7]);
        int setToolDIConfigLevel[2] = { 1, 0 };
        int getToolDIConfigLevel[2] = { 0 };
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        printf("SetToolDIConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetToolDIConfigLevel(getToolDIConfigLevel);
        printf("GetToolDIConfigLevel rtn is %d, value is %d %d \n", rtn, getToolDIConfigLevel[0], getToolDIConfigLevel[1]);
        int setStandardDILevel[8] = { 1, 1, 1, 1, 0, 0, 0, 0 };
        int getStandardDILevel[8] = { 0 };
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        printf("SetStandardDILevel rtn is %d\n", rtn);
        rtn = robot.GetStandardDILevel(getStandardDILevel);
        printf("GetStandardDILevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getStandardDILevel[0], getStandardDILevel[1], getStandardDILevel[2], getStandardDILevel[3], getStandardDILevel[4], getStandardDILevel[5], getStandardDILevel[6], getStandardDILevel[7]);
        int setStandardDOLevel[8] = { 0, 0, 0, 0, 1, 1, 1, 1 };
        int getStandardDOLevel[8] = { 0 };
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        printf("SetStandardDOLevel rtn is %d\n", rtn);
        rtn = robot.GetStandardDOLevel(getStandardDOLevel);
        printf("GetStandsrdDOLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getStandardDOLevel[0], getStandardDOLevel[1], getStandardDOLevel[2], getStandardDOLevel[3], getStandardDOLevel[4], getStandardDOLevel[5], getStandardDOLevel[6], getStandardDOLevel[7]);
        robot.Sleep(2000);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }
            
Configuración de la función CI de doble canal de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configuración de la función CI de doble canal de seguridad
    * @param [in] ID ID del doble canal; [0-3]
    * @param [in] config Configuración de la función; 0-sin configuración; 201-señal de entrada de parada de emergencia externa 1; 202-señal de entrada de parada de emergencia externa 2; 203-modo de reducción de nivel 1; 204-modo de reducción de nivel 2; 205-modo de reducción de nivel 3;206-parada normal; 207-pared de seguridad 1; 208-pared de seguridad 2; 209-pared de seguridad 3; 210-pared de seguridad 4; 211-pared de seguridad 5; 212-pared de seguridad 6; 213-pared de seguridad 7;214-pared de seguridad 8; 215-restablecimiento de parada de seguridad;
    * @return Código de error
    */
    errno_t SetSafetyDIConfig(int ID, int config);
                
Configuración de la función CO de doble canal de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configuración de la función CO de doble canal de seguridad
    * @param [in] ID ID del doble canal; [0-3]
    * @param [in] config Configuración de la función; 0-sin configuración; 201-señal de salida de parada de emergencia 1; 202-señal de salida de parada de emergencia 2; 203-salida de estado de seguridad; 204-salida de estado de parada protectora; 205-robot en movimiento;206-modo de reducción del robot; 207-modo no reducido del robot;
    * @return Código de error
    */
    errno_t SetSafetyDOConfig(int ID, int config);
                    
Ejemplo de código de configuración de la función IO de doble canal de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestSafetyIOConfig()
    {
    ROBOT_STATE_PKG pkg = {};
    FRRobot robot;
    robot.LoggerInit();
    robot.SetLoggerLevel(1);
    robot.SetReConnectParam(true, 30000, 500);
    int rtn = robot.RPC("192.168.58.2");
    if (rtn != 0)
    {
        return -1;
    }
    
    int getDIConfig[8] = { 0 };
    rtn = robot.SetSafetyDIConfig(0, 201);
    printf("SetSafetyDIConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDIConfig(1, 202);
    printf("SetSafetyDIConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDIConfig(2, 203);
    printf("SetSafetyDIConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDIConfig(3, 204);
    printf("SetSafetyDIConfig rtn is %d\n", rtn);
    rtn = robot.GetDIConfig(getDIConfig);
    printf("GetDIConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
        getDIConfig[0], getDIConfig[1], getDIConfig[2], getDIConfig[3], getDIConfig[4], getDIConfig[5], getDIConfig[6], getDIConfig[7]);

    rtn = robot.SetSafetyDIConfig(0, 0);
    printf("SetSafetyDIConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDIConfig(1, 0);
    printf("SetSafetyDIConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDIConfig(2, 0);
    printf("SetSafetyDIConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDIConfig(3, 0);
    printf("SetSafetyDIConfig rtn is %d\n", rtn);
    rtn = robot.GetDIConfig(getDIConfig);
    printf("GetDIConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
        getDIConfig[0], getDIConfig[1], getDIConfig[2], getDIConfig[3], getDIConfig[4], getDIConfig[5], getDIConfig[6], getDIConfig[7]);

    int getDOConfig[8] = { 0 };
    rtn = robot.SetSafetyDOConfig(0, 204);
    printf("SetSafetyDOConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDOConfig(1, 205);
    printf("SetSafetyDOConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDOConfig(2, 206);
    printf("SetSafetyDOConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDOConfig(3, 207);
    printf("SetSafetyDOConfig rtn is %d\n", rtn);
    rtn = robot.GetDOConfig(getDOConfig);
    printf("GetDOConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
        getDOConfig[0], getDOConfig[1], getDOConfig[2], getDOConfig[3], getDOConfig[4], getDOConfig[5], getDOConfig[6], getDOConfig[7]);
    
    rtn = robot.SetSafetyDOConfig(0, 0);
    printf("SetSafetyDOConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDOConfig(1, 0);
    printf("SetSafetyDOConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDOConfig(2, 0);
    printf("SetSafetyDOConfig rtn is %d\n", rtn);
    rtn = robot.SetSafetyDOConfig(3, 0);
    printf("SetSafetyDOConfig rtn is %d\n", rtn);
    rtn = robot.GetDOConfig(getDOConfig);
    printf("GetDOConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
        getDOConfig[0], getDOConfig[1], getDOConfig[2], getDOConfig[3], getDOConfig[4], getDOConfig[5], getDOConfig[6], getDOConfig[7]);

    robot.Sleep(2000);
    robot.CloseRPC();
    robot.Sleep(1000);
    return 0;
    }