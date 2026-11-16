Uso del programa WebAPP del robot
=================================

.. toctree:: 
    :maxdepth: 5

Establecer la carga automática del programa de trabajo predeterminado al arrancar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Establecer la carga automática del programa de trabajo predeterminado al arrancar
    * @param  [in] flag  0-no cargar automáticamente el programa predeterminado al arrancar, 1-cargar automáticamente el programa predeterminado al arrancar
    * @param  [in] program_name Nombre y ruta del programa de trabajo, como "movej.lua"
    * @return  Código de error
    */
    errno_t  LoadDefaultProgConfig(uint8_t flag, char program_name[64]);

Cargar el programa de trabajo especificado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Cargar el programa de trabajo especificado
    * @param  [in] program_name Nombre y ruta del programa de trabajo, como "movej.lua"
    * @return  Código de error
    */
    errno_t  ProgramLoad(char program_name[64]);

Obtener el nombre del programa de trabajo cargado
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el nombre del programa de trabajo cargado
    * @param  [out] program_name Nombre y ruta del programa de trabajo, como "movej.lua"
    * @return  Código de error
    */
    errno_t  GetLoadedProgram(char program_name[64]);  

Obtener el número de línea de ejecución del programa de trabajo actual del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el número de línea de ejecución del programa de trabajo actual del robot
    * @param  [out] line  Número de línea
    * @return  Código de error
    */   
    errno_t  GetCurrentLine(int *line);

Ejecutar el programa de trabajo cargado actualmente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ejecutar el programa de trabajo cargado actualmente
    * @return  Código de error
    */
    errno_t  ProgramRun();

Pausar el programa de trabajo en ejecución actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Pausar el programa de trabajo en ejecución actual
    * @return  Código de error
    */ 
    errno_t  ProgramPause();

Reanudar el programa de trabajo pausado actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Reanudar el programa de trabajo pausado actual
    * @return  Código de error
    */ 
    errno_t  ProgramResume();  

Terminar el programa de trabajo en ejecución actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Terminar el programa de trabajo en ejecución actual
    * @return  Código de error
    */ 
    errno_t  ProgramStop();    

Obtener el estado de ejecución del programa de trabajo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Obtener el estado de ejecución del programa de trabajo del robot
    * @param  [out]  state 1-programa detenido o sin programa en ejecución, 2-programa en ejecución, 3-programa pausado
    * @return  Código de error
    */
    errno_t  GetProgramState(uint8_t *state);

Ejemplo de código de operación del programa LUA del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestLuaOp(void)
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
      char program_name[64] = "test.lua";
      char loaded_name[64] = "";
      uint8_t state;
      int line;
      robot.Mode(0);
      robot.LoadDefaultProgConfig(0, program_name);
      robot.ProgramLoad(program_name);
      robot.ProgramRun();
      robot.Sleep(1000);
      robot.ProgramPause();
      robot.GetProgramState(&state);
      printf("program state:%u\n", state);
      robot.GetCurrentLine(&line);
      printf("current line:%d\n", line);
      robot.GetLoadedProgram(loaded_name);
      printf("program name:%s\n", loaded_name);
      robot.Sleep(1000);
      robot.ProgramResume();
      robot.Sleep(1000);
      robot.ProgramStop();
      robot.Sleep(1000);
      robot.CloseRPC();
      return 0;
    }

Descargar archivo Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Descargar archivo Lua
    * @param [in] fileName Nombre del archivo lua a descargar, por ejemplo: "test.lua"
    * @param [in] savePath Ruta local de guardado del archivo, por ejemplo: "D://Down/"
    * @return Código de error
    */
    errno_t LuaDownLoad(std::string fileName, std::string savePath);

Eliminar archivo Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Eliminar archivo Lua
    * @param [in] fileName Nombre del archivo lua a eliminar, por ejemplo: "test.lua"
    * @return Código de error
    */
    errno_t LuaDelete(std::string fileName);

Obtener los nombres de todos los archivos lua actuales
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Obtener los nombres de todos los archivos lua actuales
    * @param [out] luaNames Lista de nombres de archivos lua
    * @return Código de error
    */
    errno_t GetLuaList(std::list<std::string>* luaNames);

Subir archivo Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Subir archivo Lua
    * @param [in] filePath Nombre de ruta del archivo lua local
    * @return Código de error
    */
    errno_t LuaUpload(std::string filePath);

Ejemplo de código de carga y descarga de archivos LUA del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestLUAUpDownLoad(void)
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
      list<std::string> luaNames;
      rtn = robot.GetLuaList(&luaNames);
      std::cout << "res is: " << rtn << std::endl;
      std::cout << "size is: " << luaNames.size() << std::endl;
      for (auto it = luaNames.begin(); it != luaNames.end(); it++)
      {
        std::cout << it->c_str() << std::endl;
      }
      rtn = robot.LuaDownLoad("test.lua", "D://zDOWN/");
      printf("LuaDownLoad rtn is %d\n", rtn);
      rtn = robot.LuaUpload("D://zUP/airlab.lua");
      printf("LuaUpload rtn is %d\n", rtn);
      rtn = robot.LuaDelete("test.lua");
      printf("LuaDelete rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }