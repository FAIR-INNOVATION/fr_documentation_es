Uso de programas en la WebAPP del robot
=======================================

.. toctree:: 
    :maxdepth: 5

Establecer la carga automática del programa de trabajo predeterminado al arrancar
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Establecer la carga automática del programa de trabajo predeterminado al arrancar
    * @param  [in] flag  0-no cargar automáticamente el programa predeterminado al arrancar, 1-cargar automáticamente el programa predeterminado al arrancar
    * @param  [in] program_name Nombre y ruta del programa de trabajo, como "movej.lua"
    * @return  Código de error
    */
    int LoadDefaultProgConfig(byte flag, string program_name); 

Cargar el programa de trabajo especificado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Cargar el programa de trabajo especificado
    * @param  [in] program_name Nombre y ruta del programa de trabajo, como "movej.lua"
    * @return  Código de error
    */
    int ProgramLoad(string program_name); 

Obtener el nombre del programa de trabajo cargado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el nombre del programa de trabajo cargado
    * @param  [out] program_name Nombre y ruta del programa de trabajo, como "movej.lua"
    * @return  Código de error
    */
    int GetLoadedProgram(ref string program_name); 

Obtener el número de línea de ejecución del programa de trabajo actual del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el número de línea de ejecución del programa de trabajo actual del robot
    * @param  [out] line  Número de línea
    * @return  Código de error
    */   
    int GetCurrentLine(ref int line);

Ejecutar el programa de trabajo cargado actualmente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ejecutar el programa de trabajo cargado actualmente
    * @return  Código de error
    */
    int ProgramRun();

Pausar el programa de trabajo en ejecución actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pausar el programa de trabajo en ejecución actual
    * @return  Código de error
    */ 
    int ProgramPause();

Reanudar el programa de trabajo pausado actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Reanudar el programa de trabajo pausado actual
    * @return  Código de error
    */ 
    int ProgramResume(); 

Terminar el programa de trabajo en ejecución actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Terminar el programa de trabajo en ejecución actual
    * @return  Código de error
    */ 
    int ProgramStop();   

Obtener el estado de ejecución del programa de trabajo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Obtener el estado de ejecución del programa de trabajo del robot
    * @param  [out]  state 1-programa detenido o sin programa en ejecución, 2-programa en ejecución, 3-programa en pausa
    * @return  Código de error
    */
    int GetProgramState(ref byte state);

Ejemplo de código de operación de programas LUA del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnWebApp_Click(object sender, EventArgs e)
    {
        string program_name = "Text1.lua";
        string loaded_name = "";
        byte state=0;
        int line=0;

        robot.Mode(0);
        robot.LoadDefaultProgConfig(0, program_name);
        robot.ProgramLoad(program_name);
        robot.ProgramRun();
        Thread.Sleep(1000);
        robot.ProgramPause();
        robot.GetProgramState(ref state);
        Console.WriteLine("program state:{0}\n", state);
        robot.GetCurrentLine(ref line);
        Console.WriteLine("current line:{0}\n", line);
        robot.GetLoadedProgram(ref loaded_name);
        Console.WriteLine("program name:{0}\n", loaded_name);
        Thread.Sleep(1000);
        robot.ProgramResume();
        Thread.Sleep(1000);
        robot.ProgramStop();
        Thread.Sleep(1000);
    }

Descargar archivo Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Descargar archivo Lua
    * @param [in] fileName Programa de trabajo a descargar "test.lua" o "test.tar.gz"
    * @param [in] savePath Ruta local de guardado del programa de trabajo "D://Down/"
    * @return Código de error 
    */
    public int LuaDownLoad(string fileName, string savePath);

Cargar archivo Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Cargar archivo Lua
    * @param [in] filePath Ruta y nombre del programa de trabajo local ".../test.lua" o ".../test.tar.gz"
    * @param [out] errStr Información de error
    * @return Código de error 
    */
    public int LuaUpload(string filePath, ref string errStr);

Eliminar archivo Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Eliminar archivo Lua
    * @param [in] fileName Nombre del programa de trabajo a eliminar "test.lua"
    * @return Código de error 
    */
    public int LuaDelete(string fileName);

Obtener el nombre de todos los archivos lua actuales
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Obtener el nombre de todos los archivos lua actuales
    * @param [out] luaNames Lista de nombres de programas de trabajo
    * @return Código de error 
    */
    public int GetLuaList(ref List<string> luaNames) ;


Ejemplo de código de carga y descarga de archivos LUA del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    private void btnUploadLua_Click(object sender, EventArgs e)
    {
        int rtn;
        List<string> luaNames = new List<string>();
        rtn = robot.GetLuaList(ref luaNames);
        Console.WriteLine("res is: {0}", rtn);
        Console.WriteLine("size is: {0}", luaNames.Count);
        foreach (var name in luaNames)
        {
        Console.WriteLine(name);
        }
        rtn = robot.LuaDownLoad("TT.lua", "D://zDOWN/");
        Console.WriteLine("LuaDownLoad rtn is {0}", rtn);
        string errStr = "";
        Thread.Sleep(2000);

        rtn = robot.LuaUpload("D://zUP/airlab.lua", ref errStr);
        Console.WriteLine("LuaUpload rtn is {0}", errStr);
        Thread.Sleep(2000);
        rtn = robot.LuaDelete("TT.lua");
        Console.WriteLine("LuaDelete rtn is {0}", rtn);
    }