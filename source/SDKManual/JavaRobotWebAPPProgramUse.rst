Uso del programa WebAPP del robot
=================================

.. toctree:: 
    :maxdepth: 5

Establecer la carga automática del programa de trabajo predeterminado al arrancar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Establecer la carga automática del programa de trabajo predeterminado al arrancar
    * @param  [in] flag  0-no cargar automáticamente el programa predeterminado al arrancar, 1-cargar automáticamente el programa predeterminado al arrancar
    * @param  [in] program_name Nombre y ruta del programa de trabajo, como "movej.lua"
    * @return  Código de error
    */
    int LoadDefaultProgConfig(int flag, String program_name); 

Cargar el programa de trabajo especificado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Cargar el programa de trabajo especificado
    * @param  [in] program_name Nombre y ruta del programa de trabajo, como "movej.lua"
    * @return  Código de error
    */
    int ProgramLoad(String program_name); 

Obtener el nombre del programa de trabajo cargado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el nombre del programa de trabajo cargado
    * @param  [out] program_name program_name[0]:nombre y ruta del programa de trabajo, como "movej.lua"
    * @return  Código de error
    */
    int GetLoadedProgram(String[] program_name); 

Obtener el número de línea de ejecución del programa de trabajo actual del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el número de línea de ejecución del programa de trabajo actual del robot
    * @param  [out] List[0]:código de error; List[1]:int line número de línea
    * @return  Código de error
    */   
    List<Integer> GetCurrentLine();

Ejecutar el programa de trabajo cargado actualmente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ejecutar el programa de trabajo cargado actualmente
    * @return  Código de error
    */
    int ProgramRun();

Pausar el programa de trabajo en ejecución actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Pausar el programa de trabajo en ejecución actual
    * @return  Código de error
    */ 
    int PauseMotion();

Reanudar el programa de trabajo pausado actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Reanudar el programa de trabajo pausado actual
    * @return  Código de error
    */ 
    int ResumeMotion(); 

Terminar el programa de trabajo en ejecución actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Terminar el programa de trabajo en ejecución actual
    * @return  Código de error
    */ 
    int StopMotion();   

Obtener el estado de ejecución del programa de trabajo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Obtener el estado de ejecución del programa de trabajo del robot
    * @param   [out] state 1-programa detenido o sin programa en ejecución, 2-programa en ejecución, 3-programa pausado
    * @return  Código de error
    */
    public int GetProgramState(int[] state)

Ejemplo de código de operación del programa LUA del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLuaOp(Robot robot)
    {
        String program_name = "Text1.lua";
        String[] loaded_name = new String[]{""};
        int[] state=new int[]{0};
        List<Integer> line=new ArrayList<>();

        robot.Mode(0);
        robot.LoadDefaultProgConfig(0, program_name);
        robot.ProgramLoad(program_name);
        robot.ProgramRun();
        robot.Sleep(1000);
        robot.ProgramPause();
        robot.GetProgramState(state);
        System.out.println("program state:"+ state[0]);
        line=robot.GetCurrentLine();
        System.out.println("current line:"+ line);
        robot.GetLoadedProgram(loaded_name);
        System.out.println("program name:"+ loaded_name[0]);
        robot.Sleep(1000);
        robot.ProgramResume();
        robot.Sleep(1000);
        robot.ProgramStop();
        robot.Sleep(1000);

        robot.CloseRPC();
        return 0;
    }

Descargar programa Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Descargar programa de trabajo
    * @param [in] fileName Nombre del archivo lua a descargar "test.lua" o "test.tar.gz"
    * @param [in] savePath Ruta local de guardado del archivo "D://Down/"
    * @return Código de error 
    */
    int LuaDownLoad(String fileName, String savePath);

Eliminar programa Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Eliminar programa de trabajo
    * @param [in] fileName Nombre del programa de trabajo a eliminar "test.lua"
    * @return Código de error 
    */
    int LuaDelete(String fileName);

Obtener los nombres de todos los archivos lua actuales
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Obtener los nombres de todos los archivos lua actuales
    * @param [out] luaNames Lista de nombres de programas de trabajo
    * @return Código de error 
    */
    int GetLuaList(List<String> luaNames);

Subir programa Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Subir programa de trabajo
    * @param [in] filePath Nombre de ruta del archivo lua local ".../test.lua" o ".../test.tar.gz"
    * @param [out] errStr Información de error
    * @return Código de error 
    */
    int LuaUpload(String filePath, String errStr);

Ejemplo de código de carga y descarga de archivos LUA del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLUAUpDownLoad(Robot robot)
    {
        List<String> luaNames=new ArrayList<>();
        int rtn = robot.GetLuaList(luaNames);
        System.out.println("res is: "+rtn);
        System.out.println("size is: "+luaNames.size());
        for (int it =1; it < luaNames.size(); it++)
        {
            System.out.println(luaNames.get(it));
        }

        rtn = robot.LuaDownLoad("test.lua", "D://zDOWN/");
        System.out.println("LuaDownLoad rtn is:"+rtn);

        rtn = robot.LuaUpload("D://zUP/XG.lua","");
        System.out.println("LuaUpload rtn is:"+ rtn);

        rtn = robot.LuaDelete("XG.lua");
        System.out.println("LuaDelete rtn is:"+ rtn);

        return 0;
    }