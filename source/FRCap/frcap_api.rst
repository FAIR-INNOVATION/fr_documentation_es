Descripción de la API
=========================

.. toctree:: 
   :maxdepth: 6

Instrucciones act
-------------------------

Todas las instrucciones act siguientes utilizan POST, con URL /action/act.

Guardar punto de enseñanza
+++++++++++++++++++++++++++++++++++++++

Nombre de la instrucción: save_point. 

Parámetros de la instrucción:

.. code-block:: c++
    :linenos:

    /** 
    * @param  string name nombre del punto de enseñanza registrado
    * @param  string speed velocidad
    * @param  string elbow_speed velocidad del codo
    * @param  string acc aceleración
    * @param  string elbow_acc aceleración del codo
    * @param  string toolnum número de herramienta
    * @param  string workpiecenum número de pieza
    */ 

Ejemplo de instrucción:

.. code-block:: c++
    :linenos:

    {
        cmd: "save_point",
        data:{
            name: "point1",
            speed: "100",
            elbow_speed: "100",
            acc: "100",
            elbow_acc: "100",
            toolnum: "1",
            workpiecenum: "1"
        }
    }

Respuesta de la instrucción:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200 "success"
    * @return status:404 "fail"
    */ 

Instrucciones sta
-------------------------

Todas las instrucciones sta siguientes utilizan POST, con URL /action/sta.

Obtener datos de estado del robot
++++++++++++++++++++++++++++++++++++++++++++

Nombre de la instrucción: basic. 

Parámetros de la instrucción: ninguno.

Ejemplo de instrucción:

.. code-block:: c++
    :linenos:

    {
        cmd: "basic",
    }

Respuesta de la instrucción:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200 
    * @param  object joints posición de las articulaciones
    * @param  object tcp pose cartesiana
    * @param  array exAxisPos posición del eje externo
    * @return status:404 "fail"
    */
    {
        joints: {
            j1: "90",
            j2: "90",
            j3: "90",
            j4: "90",
            j5: "90",
            j6: "90",
        },
        tcp: {
            x: "100",
            x: "100",
            z: "100",
            rx: "90",
            ry: "90",
            rz: "90",
        },
        exAxisPos: [0,0,0,0]
    }

Instrucciones get
--------------------------

Todas las instrucciones get siguientes utilizan POST, con URL /action/get. 

Obtener puntos de enseñanza
+++++++++++++++++++++++++++++++++++++++

Nombre de la instrucción: get_points().

Parámetros de la instrucción: ninguno.

Ejemplo de instrucción:

.. code-block:: c++
    :linenos:

    {
        cmd: "get_points"
    }

Respuesta de la instrucción:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200 "success"
    * @param  ${point_name}: object información relacionada con el punto de enseñanza
    * @return status:404 "fail"
    */ 

Ejemplo de respuesta de la instrucción:

.. code-block:: c++
    :linenos:

    {
        "localpoint1": {
            "name":"localpoint1",
            "elbow_speed":"1",
            "elbow_acc":"1",
            "x": "1",
            "y": "1",
            "z": "1",
            "rx": "1",
            "ry": "1",
            "rz": "1",
            "j1": "1",
            "j2": "1",
            "j3": "1",
            "j4": "1",
            "j5": "1",
            "j6": "1",
            "toolnum": "1",
            "workpiecenum": "1",
            "speed": "1",
            "acc": "1",
            "E1": "1",
            "E2: "1",
            "E3": "1",
            "E4": "1"
        }
    }


Obtener configuración del sistema
+++++++++++++++++++++++++++++++++++++++

Nombre de la instrucción: get_syscfg().

Parámetros de la instrucción: ninguno.

Ejemplo de instrucción:

.. code-block:: c++
    :linenos:

    {
        cmd: "get_syscfg"
    }

Respuesta de la instrucción:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200 "success"
    * @param  string log_count número máximo de días de registro
    * @param  string language paquete de idioma utilizado actualmente
    * @param  string lifespan tiempo de espera agotado
    * * @return status:404 "fail"
    */ 

Ejemplo de respuesta de la instrucción:

.. code-block:: c++
    :linenos:

    {
        log_count:"10",
        language:"zh",
        lifespan:"1800"
    }

Instrucciones set
--------------------------

Todas las instrucciones set siguientes utilizan POST, con URL /action/set.

Instrucción de envío de variable del sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++

Nombre de la instrucción: 511.

Parámetros de la instrucción:

.. code-block:: c++
    :linenos:

    /** 
    * @param int index número de variable del sistema: 1-20 
    * @param int value valor de la variable del sistema 
    */ 

Ejemplo de instrucción:

.. code-block:: c++
    :linenos:

    {
        cmd: 511,
        data:{
            content:"SetSysVarValue(2,1)"
        }
    }

Respuesta de la instrucción:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200 1: representa éxito, 0: representa fallo
    * @return status:404 "fail"
    */

Ejemplo de respuesta de la instrucción:

.. code-block:: c++
    :linenos:

    1

Instrucción de obtención de variable del sistema
++++++++++++++++++++++++++++++++++++++++++++++++++++

Nombre de la instrucción: 512.

Parámetros de la instrucción:

.. code-block:: c++
    :linenos:

    /** 
    * @param int index número de variable del sistema: 1-20 
    * /

Ejemplo de instrucción:

.. code-block:: c++
    :linenos:

    {
        cmd: 512,
        data:{
            content:"GetSysVarValue(2)"
        }
    }

Respuesta de la instrucción:

.. code-block:: c++
    :linenos:

    /** 
    * @return status:200
    * @param int value valor de la variable del sistema 
    * @return status:404 "fail"
    * /

Ejemplo de respuesta de la instrucción:

.. code-block:: c++
    :linenos:

    1

Instrucciones better-sqlite3
--------------------------------

Consultar el primer registro de la base de datos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Parámetros de la instrucción:

.. code-block:: c++
    :linenos:

    /**
    * @param string db_name nombre de la base de datos (incluida la ruta absoluta) 
    * @param string sql sentencia sql
    * @return string result primer registro consultado
    */

Contenido de la instrucción:

.. code-block:: c++
    :linenos:

    queryget(string db_name, string sql);

Consultar todos los registros de la base de datos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Parámetros de la instrucción:

.. code-block:: c++
    :linenos:

    /**
    * @param string db_name nombre de la base de datos (incluida la ruta absoluta)
    * @param string sql sentencia sql
    * @return string result todos los registros consultados
    */

Contenido de la instrucción:

.. code-block:: c++
    :linenos:

    queryall(string db_name, string sql);

Ejecutar sentencia de base de datos
++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @param string db_name nombre de la base de datos (incluida la ruta absoluta)
    * @param string sql sentencia sql
    * @param object obj parámetros necesarios para la ejecución de la sentencia sql
    * @return \
    */

Parámetros de la instrucción:

.. code-block:: c++
    :linenos:

    exec(string db_name, string sql, object obj);

Contenido de la instrucción:

Instrucciones socket
-----------------------

socket send
++++++++++++++++++++++

Parámetros de la instrucción:

.. code-block:: c++
    :linenos:

    /**
    * @param string send_content contenido de envío de la instrucción de comunicación socket
    * @return \
    */

Contenido de la instrucción:

.. code-block:: c++
    :linenos:

    socket_cmd.send(string send_content);//8065
    socket_file.send(string send_content);//8067

socket recv
+++++++++++++++++++++

Parámetros de la instrucción:

.. code-block:: c++
    :linenos:

    /**
    * @return string recv_content contenido de respuesta de la instrucción de comunicación socket
    */

Contenido de la instrucción:

.. code-block:: c++
    :linenos:

    socket_cmd.recv();//8065
    socket_file.recv();//8067

Instrucciones de operación de archivos
---------------------------------------------------------

Escribir contenido en un archivo
++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @param String filename ruta del archivo
    * @param string content contenido que se desea escribir
    * @return true/false
    */

    write(filename, content);

Leer contenido de un archivo
++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @param String filename ruta del archivo
    * @param string content contenido que se desea escribir
    * @return String contenido del archivo
    */

    read(filename);

Modificar permisos de archivo
++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:
    
    /**
    * @param String filename ruta del archivo
    * @param Number mode modo de permisos (por ejemplo, 0644)
    * @return true/false
    */

    chmod(filename, mode);

Leer contenido de un directorio, incluidos los subdirectorios
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:
    
    /**
    * @param String path ruta del archivo
    * @return Array array de nombres de archivo
    */

    readdir(path);

Instrucciones de compresión y descompresión
-------------------------------------------------

.. note:: 
    Distinguir entre las versiones LA y QX:

    Importación del módulo LA: var execSync = require('child_process').execSync;

    Importación del módulo QX: var tar_utils = require('/usr/local/etc/node/sys/tools/tar_utils');

Crear archivo comprimido tar.gz
+++++++++++++++++++++++++++++++++

Ejemplo de creación de archivo comprimido tar.gz (LA):

.. code-block:: javascript
    :linenos:
    
    var cmd = 'cd / && tar -zcvf ' + FILENAME + '-C ' + DIR;
    execSync(cmd);
    
Descripción de la instrucción de creación de archivo comprimido tar.gz (QX):

.. code-block:: c++
    :linenos:
    
    /**
    * @param {Array|String} sourcePaths array de rutas de archivos/directorios de origen o una única ruta
    * @param String targetFile ruta del archivo comprimido de destino
    * @param Function callback función de devolución de llamada, con parámetro (error) 
    * @param String basePath ruta base, por defecto '/'
    * @return \
    */

    createTarGz(sourcePaths, targetFile, callback, basePath);

Descomprimir archivo tar.gz
+++++++++++++++++++++++++++++++++

Ejemplo de descompresión de archivo tar.gz (LA):

.. code-block:: javascript
    :linenos:

    var cmd = 'cd / && tar -zxvf ' + FILENAME;
    execSync(cmd);

Descripción de la instrucción de descompresión de archivo tar.gz (QX):

.. code-block:: c++
    :linenos:
    
    /**
    * @param String sourceFile ruta del archivo comprimido de origen
    * @param String targetDir directorio de descompresión de destino
    * @param Function callback función de devolución de llamada, con parámetro (error) 
    * @return \
    */
    extractTarGz(sourceFile, targetDir, callback);