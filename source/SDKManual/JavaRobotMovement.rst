Movimiento del robot
====================

.. toctree:: 
    :maxdepth: 5


Jog punto a punto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief jog punto a punto 
    * @param [in] refType 0-jog de articulaciones, 2-jog en el sistema de coordenadas base, 4-jog en el sistema de coordenadas de herramienta, 8-jog en el sistema de coordenadas de pieza
    * @param [in] nb 1-articulación 1 (o eje x), 2-articulación 2 (o eje y), 3-articulación 3 (o eje z), 4-articulación 4 (o rotación alrededor del eje x), 5-articulación 5 (o rotación alrededor del eje y), 6-articulación 6 (o rotación alrededor del eje z)
    * @param [in] dir 0-dirección negativa, 1-dirección positiva
    * @param [in] vel Porcentaje de velocidad, [0~100]
    * @param [in] acc Porcentaje de aceleración, [0~100]
    * @param [in] max_dis Ángulo máximo de un solo jog, unidad [°] o distancia, unidad [mm]
    * @return Código de error 
    */ 
    int StartJOG(int refType, int nb, int dir, double vel, double acc, double max_dis);

Parada con desaceleración del jog punto a punto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Parada con desaceleración del jog punto a punto
    * @param  [in]  stopType  1-parada del jog de articulaciones, 3-parada del jog en el sistema de coordenadas base, 5-parada del jog en el sistema de coordenadas de herramienta, 9-parada del jog en el sistema de coordenadas de pieza
    * @return  Código de error
    */
    int StopJOG(int stopType);

Parada inmediata del jog punto a punto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Parada inmediata del jog punto a punto
    * @return  Código de error
    */
    int ImmStopJOG(); 

Ejemplo de código de control del jog punto a punto del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static  int TestJOG(Robot robot)
    {
        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(0, i + 1, 0, 20.0, 20.0, 30.0);
            robot.Sleep(1000);
            robot.ImmStopJOG();
            robot.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(2, i + 1, 0, 20.0, 20.0, 30.0);
            robot.Sleep(1000);
            robot.ImmStopJOG();
            robot.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(4, i + 1, 0, 20.0, 20.0, 30.0);
            robot.Sleep(1000);
            robot.StopJOG(5);
            robot.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(8, i + 1, 0, 20.0, 20.0, 30.0);
            robot.Sleep(1000);
            robot.StopJOG(9);
            robot.Sleep(1000);
        }
        return 0;
    }

Movimiento en el espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento en el espacio de articulaciones
    * @param  [in] joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param  [in] desc_pos  Pose cartesiana objetivo
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
    int MoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos);

Movimiento en el espacio de articulaciones (cálculo automático de cinemática directa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /** 
    * @brief  Movimiento en el espacio de articulaciones (cálculo automático de cinemática directa)
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
    * @return Código de error 
    */ 
    int MoveJ(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos)

Movimiento lineal en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento lineal en el espacio cartesiano (función sobrecargada 1, se añade blendMode)
    * @param  joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param  desc_pos   Pose cartesiana objetivo
    * @param  tool  Número de coordenada de herramienta, rango [1~15]
    * @param  user  Número de coordenada de pieza, rango [1~15]
    * @param  vel  Porcentaje de velocidad, rango [0~100]
    * @param  acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  ovl  Factor de escala de velocidad [0~100]/velocidad física (mm/s)
    * @param  blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  blendMode Modo de transición; 0-transición tangente interna; 1-transición en esquina
    * @param  epos  Posición del eje extendido, unidad mm
    * @param  search  0-sin búsqueda de posición de alambre de soldadura, 1-búsqueda de posición de alambre de soldadura
    * @param  offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  offset_pos  Cantidad de desplazamiento de la pose
    * @param  oacc Factor de escala de aceleración [0-100]/aceleración física (mm/s2)
    * @param  velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @param  overSpeedStrategy  Estrategia de tratamiento de exceso de velocidad, 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, valor predeterminado 0
    * @param  speedPercent  Porcentaje de umbral de reducción de velocidad permitido [0-100], valor predeterminado 10%
    * @return  Código de error
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, double oacc,int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimiento lineal en el espacio cartesiano (cálculo automático de cinemática inversa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento lineal en el espacio cartesiano (cálculo automático de cinemática inversa)
    * @param [in] desc_pos   Pose cartesiana objetivo
    * @param [in] tool  Número de coordenada de herramienta, rango [1~15]
    * @param [in] user  Número de coordenada de pieza, rango [1~15]
    * @param [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] blendMode Modo de transición; 0-transición tangente interna; 1-transición en esquina
    * @param [in] epos  Posición del eje extendido, unidad mm
    * @param [in] search  0-sin búsqueda de posición de alambre de soldadura, 1-búsqueda de posición de alambre de soldadura
    * @param [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos  Cantidad de desplazamiento de la pose
    * @param [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param [in] overSpeedStrategy  Estrategia de tratamiento de exceso de velocidad, 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, valor predeterminado 0
    * @param [in] speedPercent  Porcentaje de umbral de reducción de velocidad permitido [0-100], valor predeterminado 10%
    * @return  Código de error
    */
    int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int overSpeedStrategy, int speedPercent)

Movimiento lineal en el espacio cartesiano (se añade el parámetro velAccParamMode de modo de velocidad y aceleración)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento lineal en el espacio cartesiano (se añade el parámetro velAccParamMode de modo de velocidad y aceleración)
    * @param  [in] joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número de coordenada de herramienta, rango [1~15]
    * @param  [in] user  Número de coordenada de pieza, rango [1~15]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] epos  Posición del eje extendido, unidad mm
    * @param  [in] search  0-sin búsqueda de posición de alambre de soldadura, 1-búsqueda de posición de alambre de soldadura
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Cantidad de desplazamiento de la pose
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @param  [in] overSpeedStrategy  Estrategia de tratamiento de exceso de velocidad, 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, valor predeterminado 0
    * @param  [in] speedPercent  Porcentaje de umbral de reducción de velocidad permitido [0-100], valor predeterminado 10%
    * @return  Código de error
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimiento lineal en el espacio cartesiano (función sobrecargada 1, se añade blendMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento lineal en el espacio cartesiano (función sobrecargada 1, se añade blendMode)
    * @param  [in] joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número de coordenada de herramienta, rango [1~15]
    * @param  [in] user  Número de coordenada de pieza, rango [1~15]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] blendMode Modo de transición; 0-transición tangente interna; 1-transición en esquina
    * @param  [in] epos  Posición del eje extendido, unidad mm
    * @param  [in] search  0-sin búsqueda de posición de alambre de soldadura, 1-búsqueda de posición de alambre de soldadura
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Cantidad de desplazamiento de la pose
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @param  [in] overSpeedStrategy  Estrategia de tratamiento de exceso de velocidad, 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, valor predeterminado 0
    * @param  [in] speedPercent  Porcentaje de umbral de reducción de velocidad permitido [0-100], valor predeterminado 10%
    * @return  Código de error
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimiento lineal en el espacio cartesiano (función sobrecargada 2, no requiere introducir la posición de las articulaciones)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento lineal en el espacio cartesiano (función sobrecargada 2, no requiere introducir la posición de las articulaciones)
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número de coordenada de herramienta, rango [1~15]
    * @param  [in] user  Número de coordenada de pieza, rango [1~15]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] blendMode Modo de transición; 0-transición tangente interna; 1-transición en esquina
    * @param  [in] epos  Posición del eje extendido, unidad mm
    * @param  [in] search  0-sin búsqueda de posición de alambre de soldadura, 1-búsqueda de posición de alambre de soldadura
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Cantidad de desplazamiento de la pose
    * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @param  [in] overSpeedStrategy  Estrategia de tratamiento de exceso de velocidad, 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, valor predeterminado 0
    * @param  [in] speedPercent  Porcentaje de umbral de reducción de velocidad permitido [0-100], valor predeterminado 10%
    * @return  Código de error
    */
    public int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimiento circular en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento circular en el espacio cartesiano
    * @param  joint_pos_p  Posición de las articulaciones del punto de trayectoria, unidad deg
    * @param  desc_pos_p   Pose cartesiana del punto de trayectoria
    * @param  ptool  Número de coordenada de herramienta, rango [1~15]
    * @param  puser  Número de coordenada de pieza, rango [1~15]
    * @param  pvel  Porcentaje de velocidad, rango [0~100]
    * @param  pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  epos_p  Posición del eje extendido, unidad mm
    * @param  poffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  offset_pos_p  Cantidad de desplazamiento de la pose
    * @param  joint_pos_t  Posición de las articulaciones del punto objetivo, unidad deg
    * @param  desc_pos_t   Pose cartesiana del punto objetivo
    * @param  ttool  Número de coordenada de herramienta, rango [1~15]
    * @param  tuser  Número de coordenada de pieza, rango [1~15]
    * @param  tvel  Porcentaje de velocidad, rango [0~100]
    * @param  tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  epos_t  Posición del eje extendido, unidad mm
    * @param  toffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  offset_pos_t  Cantidad de desplazamiento de la pose
    * @param  ovl  Factor de escala de velocidad [0~100]/velocidad física (mm/s)
    * @param  blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  oacc Factor de escala de aceleración [0-100]/aceleración física (mm/s2)
    * @param  velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @return  Código de error
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, double oacc,int velAccParamMode)

Movimiento circular en el espacio cartesiano (cálculo automático de cinemática inversa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento circular en el espacio cartesiano (cálculo automático de cinemática inversa)
    * @param [in] desc_pos_p   Pose cartesiana del punto de trayectoria
    * @param [in] ptool  Número de coordenada de herramienta, rango [1~15]
    * @param [in] puser  Número de coordenada de pieza, rango [1~15]
    * @param [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_p  Posición del eje extendido, unidad mm
    * @param [in] poffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_p  Cantidad de desplazamiento de la pose
    * @param [in] desc_pos_t   Pose cartesiana del punto objetivo
    * @param [in] ttool  Número de coordenada de herramienta, rango [1~15]
    * @param [in] tuser  Número de coordenada de pieza, rango [1~15]
    * @param [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_t  Posición del eje extendido, unidad mm
    * @param [in] toffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_t  Cantidad de desplazamiento de la pose
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return  Código de error
    */
    int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config)

Movimiento circular en el espacio cartesiano (se añade el parámetro velAccParamMode de modo de velocidad y aceleración)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento circular en el espacio cartesiano (se añade el parámetro velAccParamMode de modo de velocidad y aceleración)
    * @param  [in] joint_pos_p  Posición de las articulaciones del punto de trayectoria, unidad deg
    * @param  [in] desc_pos_p   Pose cartesiana del punto de trayectoria
    * @param  [in] ptool  Número de coordenada de herramienta, rango [1~15]
    * @param  [in] puser  Número de coordenada de pieza, rango [1~15]
    * @param  [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_p  Posición del eje extendido, unidad mm
    * @param  [in] poffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_p  Cantidad de desplazamiento de la pose
    * @param  [in] joint_pos_t  Posición de las articulaciones del punto objetivo, unidad deg
    * @param  [in] desc_pos_t   Pose cartesiana del punto objetivo
    * @param  [in] ttool  Número de coordenada de herramienta, rango [1~15]
    * @param  [in] tuser  Número de coordenada de pieza, rango [1~15]
    * @param  [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_t  Posición del eje extendido, unidad mm
    * @param  [in] toffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_t  Cantidad de desplazamiento de la pose
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @return  Código de error
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int velAccParamMode)

Movimiento circular en el espacio cartesiano (función sobrecargada 1, no requiere introducir la posición de las articulaciones)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento circular en el espacio cartesiano (función sobrecargada 1, no requiere introducir la posición de las articulaciones)
    * @param  [in] desc_pos_p   Pose cartesiana del punto de trayectoria
    * @param  [in] ptool  Número de coordenada de herramienta, rango [1~15]
    * @param  [in] puser  Número de coordenada de pieza, rango [1~15]
    * @param  [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_p  Posición del eje extendido, unidad mm
    * @param  [in] poffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_p  Cantidad de desplazamiento de la pose
    * @param  [in] desc_pos_t   Pose cartesiana del punto objetivo
    * @param  [in] ttool  Número de coordenada de herramienta, rango [1~15]
    * @param  [in] tuser  Número de coordenada de pieza, rango [1~15]
    * @param  [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_t  Posición del eje extendido, unidad mm
    * @param  [in] toffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_t  Cantidad de desplazamiento de la pose
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @return  Código de error
    */
    public int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config, int velAccParamMode)

Movimiento circular completo en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    *@brief  Movimiento circular completo en el espacio cartesiano
    *@param  joint_pos_p  Posición de las articulaciones del punto de trayectoria 1, unidad deg
    *@param  desc_pos_p   Pose cartesiana del punto de trayectoria 1
    *@param  ptool  Número de coordenada de herramienta, rango [1~15]
    *@param  puser  Número de coordenada de pieza, rango [1~15]
    *@param  pvel  Porcentaje de velocidad, rango [0~100]
    *@param  pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    *@param  epos_p  Posición del eje extendido, unidad mm
    *@param  joint_pos_t  Posición de las articulaciones del punto de trayectoria 2, unidad deg
    *@param  desc_pos_t   Pose cartesiana del punto de trayectoria 2
    *@param  ttool  Número de coordenada de herramienta, rango [1~15]
    *@param  tuser  Número de coordenada de pieza, rango [1~15]
    *@param  tvel  Porcentaje de velocidad, rango [0~100]
    *@param  tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    *@param  epos_t  Posición del eje extendido, unidad mm
    *@param  ovl  Factor de escala de velocidad [0~100]/velocidad física (mm/s)
    *@param  offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    *@param  offset_pos  Cantidad de desplazamiento de la pose
    *@param  oacc Factor de escala de aceleración [0-100]/aceleración física (mm/s2)
    *@param  blendR -1: bloqueante; 0~1000: radio de suavizado
    *@param  velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    *@return  Código de error
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Movimiento circular completo en el espacio cartesiano (cálculo automático de cinemática inversa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
     * @brief  Movimiento circular completo en el espacio cartesiano (cálculo automático de cinemática inversa)
     * @param  [in] desc_pos_p   Pose cartesiana del punto de trayectoria 1
     * @param  [in] ptool  Número de coordenada de herramienta, rango [0~14]
     * @param  [in] puser  Número de coordenada de pieza, rango [0~14]
     * @param  [in] pvel  Porcentaje de velocidad, rango [0~100]
     * @param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
     * @param  [in] epos_p  Posición del eje extendido, unidad mm
     * @param  [in] desc_pos_t   Pose cartesiana del punto de trayectoria 2
     * @param  [in] ttool  Número de coordenada de herramienta, rango [0~14]
     * @param  [in] tuser  Número de coordenada de pieza, rango [0~14]
     * @param  [in] tvel  Porcentaje de velocidad, rango [0~100]
     * @param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
     * @param  [in] epos_t  Posición del eje extendido, unidad mm
     * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
     * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
     * @param  [in] offset_pos  Cantidad de desplazamiento de la pose
     * @param  [in] oacc Porcentaje de aceleración
     * @param  [in] blendR -1: bloqueante; 0~1000: radio de suavizado
     * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
     * @return  Código de error
     */
    int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR,int config)

Movimiento circular completo en el espacio cartesiano (se añade el parámetro velAccParamMode de modo de velocidad y aceleración)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    *@brief  Movimiento circular completo en el espacio cartesiano (se añade el parámetro velAccParamMode de modo de velocidad y aceleración)
    *@param  [in] joint_pos_p  Posición de las articulaciones del punto de trayectoria 1, unidad deg
    *@param  [in] desc_pos_p   Pose cartesiana del punto de trayectoria 1
    *@param  [in] ptool  Número de coordenada de herramienta, rango [1~15]
    *@param  [in] puser  Número de coordenada de pieza, rango [1~15]
    *@param  [in] pvel  Porcentaje de velocidad, rango [0~100]
    *@param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    *@param  [in] epos_p  Posición del eje extendido, unidad mm
    *@param  [in] joint_pos_t  Posición de las articulaciones del punto de trayectoria 2, unidad deg
    *@param  [in] desc_pos_t   Pose cartesiana del punto de trayectoria 2
    *@param  [in] ttool  Número de coordenada de herramienta, rango [1~15]
    *@param  [in] tuser  Número de coordenada de pieza, rango [1~15]
    *@param  [in] tvel  Porcentaje de velocidad, rango [0~100]
    *@param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    *@param  [in] epos_t  Posición del eje extendido, unidad mm
    *@param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    *@param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    *@param  [in] offset_pos  Cantidad de desplazamiento de la pose
    *@param  [in] oacc Porcentaje de aceleración
    *@param  [in] blendR -1: bloqueante; 0~1000: radio de suavizado
    *@param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    *@return  Código de error
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Movimiento circular completo en el espacio cartesiano (función sobrecargada 1, no requiere introducir la posición de las articulaciones)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento circular completo en el espacio cartesiano (función sobrecargada 1, no requiere introducir la posición de las articulaciones)
    * @param  [in] desc_pos_p   Pose cartesiana del punto de trayectoria 1
    * @param  [in] ptool  Número de coordenada de herramienta, rango [0~14]
    * @param  [in] puser  Número de coordenada de pieza, rango [0~14]
    * @param  [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_p  Posición del eje extendido, unidad mm
    * @param  [in] desc_pos_t   Pose cartesiana del punto de trayectoria 2
    * @param  [in] ttool  Número de coordenada de herramienta, rango [0~14]
    * @param  [in] tuser  Número de coordenada de pieza, rango [0~14]
    * @param  [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_t  Posición del eje extendido, unidad mm
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Cantidad de desplazamiento de la pose
    * @param  [in] oacc Porcentaje de aceleración
    * @param  [in] blendR -1: bloqueante; 0~1000: radio de suavizado
    * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @return  Código de error
    */
    public int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int config, int velAccParamMode)

Movimiento punto a punto en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Movimiento punto a punto en el espacio cartesiano 
    * @param [in] desc_pos  Pose cartesiana objetivo o incremento de pose
    * @param [in] tool  Número de coordenada de herramienta, rango [0~14]
    * @param [in] user  Número de coordenada de pieza, rango [0~14]
    * @param [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] blendT [-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad ms
    * @param [in] config  Configuración del espacio de articulaciones, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver con referencia a una configuración específica del espacio de articulaciones, valor predeterminado -1
    * @return Código de error 
    */ 
    int MoveCart(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendT, int config);

Ejemplo de código de instrucciones de movimiento básico del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestMove(Robot robot)
    {
        int rtn=-1;
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3=new JointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4=new JointPos(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3=new DescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4=new DescPose(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double oacc = 100.0;
        double blendT = 0.0;
        double blendR = 0.0;
        int flag = 0;
        int search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, oacc, velAccMode,0,10);
        System.out.printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, oacc, velAccMode);
        System.out.printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos, j1, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos, oacc, -1, velAccMode);
        System.out.printf("circle errcode:%d\n", rtn);
        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        System.out.printf("MoveCart errcode:%d\n", rtn);
        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode,0,10);
        System.out.printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, -1, velAccMode);
        System.out.printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        System.out.printf("circle errcode:%d\n", rtn);
        return 0;
    }

Movimiento en hélice en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimiento en hélice en el espacio cartesiano 
    * @param [in] joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param [in] desc_pos   Pose cartesiana objetivo
    * @param [in] tool  Número de coordenada de herramienta, rango [0~14]
    * @param [in] user  Número de coordenada de pieza, rango [0~14]
    * @param [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos  Posición del eje extendido, unidad mm
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos  Cantidad de desplazamiento de la pose
    * @return Código de error 
    */
    int NewSpiral(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, ExaxisPos epos, double ovl, int offset_flag, DescPose offset_pos, SpiralParam spiral_param);

Movimiento en hélice en el espacio cartesiano (cálculo automático de cinemática inversa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Movimiento en hélice en el espacio cartesiano (cálculo automático de cinemática inversa)
    * @param [in] desc_pos   Pose cartesiana objetivo
    * @param [in] tool  Número de coordenada de herramienta, rango [0~14]
    * @param [in] user  Número de coordenada de pieza, rango [0~14]
    * @param [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos  Posición del eje extendido, unidad mm
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos  Cantidad de desplazamiento de la pose
    * @param [in] spiral_param  Parámetros de la hélice
    * @param [in] config  Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return Código de error 
    */
    int NewSpiral(DescPose desc_pos, int tool, int user, double vel, double acc, ExaxisPos epos, double ovl, int offset_flag, DescPose offset_pos, SpiralParam spiral_param,int config)

Ejemplo de código de movimiento en hélice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSpiral(Robot robot)
    {
        int rtn=-1;
        JointPos j=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        DescPose desc_pos=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose offset_pos1=new DescPose(50, 0, 0, -30, 0, 0);
        DescPose offset_pos2=new DescPose(50, 0, 0, -5, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        SpiralParam sp=new SpiralParam(1,5.0,50.0,10.0,10.0,0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = 0.0;
        int flag = 2;

        rtn = robot.MoveJ(j, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos1);
        System.out.println("movej errcode:"+ rtn);

        rtn = robot.NewSpiral(desc_pos, tool, user, vel, acc, epos, ovl, flag, offset_pos2, sp,-1);
        System.out.println("newspiral errcode:"+ rtn);

        return 0;
    }

Inicio del movimiento servo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicio del movimiento servo, se utiliza junto con las instrucciones ServoJ y ServoCart
    * @param[in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @param[in] filtertime Tiempo de filtrado, unidad ms, valor predeterminado 0
    * @param[in] gain Arreglo de ganancia del lazo de posición, la longitud debe ser 6, correspondiendo sucesivamente a la ganancia del lazo de posición de las articulaciones J1~J6; al pasar null se usan los valores predeterminados { -1.0, -1.0, -1.0, -1.0, -1.0, -1.0 }
    * @return  Código de error
    */
    public int ServoMoveStart(int comType, int filtertime, double[] gain)

Ejemplo de código ServoJ de inicio del movimiento servo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestServoCartWithFiltertime(Robot robot) {
        // ---- Pose cartesiana objetivo ----
        DescPose desc_pos_dt = new DescPose(542.1690, 34.7990, 114.4800, 169.808000, -3.600000, -133.152000);
        ExaxisPos exaxis = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        double[] pos_gain = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        int mode = 0;
        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        int count = 5000;
        int rtn = 0;

        robot.SetSpeed(20);

        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveL(desc_pos_dt, 1, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset_pos, -1, 0,0,0);

        // ---- Parámetros de ServoMoveStart ----
        int filtertime = 0;
        double[] ServoGain = { 20.0, 20.0, 20.0, 20.0, 20.0, 20.0 };

        rtn = robot.ServoMoveStart(0, filtertime, ServoGain);
        System.out.println("ServoMoveStart rtn is " + rtn);

        // ---- Leer los puntos de trayectoria cartesiana del archivo y enviar ServoCart punto a punto ----
        BufferedReader reader = null;
        try {
            reader = new BufferedReader(new FileReader("D://zUP/6RCARpath.txt"));
            String line;
            while ((line = reader.readLine()) != null) {
                // Formato de análisis: ServoCart(0,x,y,z,rx,ry,rz,...
                String prefix = "ServoCart(0,";
                if (line.startsWith(prefix)) {
                    String body = line.substring(prefix.length());
                    String[] parts = body.split(",");
                    if (parts.length >= 6) {
                        desc_pos_dt.tran.x = Float.parseFloat(parts[0].trim());
                        desc_pos_dt.tran.y = Float.parseFloat(parts[1].trim());
                        desc_pos_dt.tran.z = Float.parseFloat(parts[2].trim());
                        desc_pos_dt.rpy.rx = Float.parseFloat(parts[3].trim());
                        desc_pos_dt.rpy.ry = Float.parseFloat(parts[4].trim());
                        desc_pos_dt.rpy.rz = Float.parseFloat(parts[5].trim());
                    }
                }

                rtn = robot.ServoCart(mode, desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
                System.out.println("ServoCart rtn is " + rtn);
                // robot.Sleep(8);
            }
        } catch (IOException e) {
            System.out.println("Error al leer el archivo: " + e.getMessage());
        } finally {
            if (reader != null) {
                try { reader.close(); } catch (IOException ignored) {}
            }
        }

        // ---- Finalizar el servo ----
        robot.ServoMoveEnd(0);

        return 0;
    }

Ejemplo de código ServoCart de inicio del movimiento servo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestServoCartWithFiltertime(Robot robot) {
        // ---- Pose cartesiana objetivo ----
        DescPose desc_pos_dt = new DescPose(542.1690, 34.7990, 114.4800, 169.808000, -3.600000, -133.152000);
        ExaxisPos exaxis = new ExaxisPos(0.0, 0.0, 0.0, 0.0);

        double[] pos_gain = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };

        int mode = 0;
        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        int count = 5000;
        int rtn = 0;

        robot.SetSpeed(20);

        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveL(desc_pos_dt, 1, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset_pos, -1, 0,0,0);

        // ---- Parámetros de ServoMoveStart ----
        int filtertime = 0;
        double[] ServoGain = { 20.0, 20.0, 20.0, 20.0, 20.0, 20.0 };

        rtn = robot.ServoMoveStart(0, filtertime, ServoGain);
        System.out.println("ServoMoveStart rtn is " + rtn);

        // ---- Leer los puntos de trayectoria cartesiana del archivo y enviar ServoCart punto a punto ----
        BufferedReader reader = null;
        try {
            reader = new BufferedReader(new FileReader("D://zUP/6RCARpath.txt"));
            String line;
            while ((line = reader.readLine()) != null) {
                // Formato de análisis: ServoCart(0,x,y,z,rx,ry,rz,...
                String prefix = "ServoCart(0,";
                if (line.startsWith(prefix)) {
                    String body = line.substring(prefix.length());
                    String[] parts = body.split(",");
                    if (parts.length >= 6) {
                        desc_pos_dt.tran.x = Float.parseFloat(parts[0].trim());
                        desc_pos_dt.tran.y = Float.parseFloat(parts[1].trim());
                        desc_pos_dt.tran.z = Float.parseFloat(parts[2].trim());
                        desc_pos_dt.rpy.rx = Float.parseFloat(parts[3].trim());
                        desc_pos_dt.rpy.ry = Float.parseFloat(parts[4].trim());
                        desc_pos_dt.rpy.rz = Float.parseFloat(parts[5].trim());
                    }
                }

                rtn = robot.ServoCart(mode, desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
                System.out.println("ServoCart rtn is " + rtn);
                // robot.Sleep(8);
            }
        } catch (IOException e) {
            System.out.println("Error al leer el archivo: " + e.getMessage());
        } finally {
            if (reader != null) {
                try { reader.close(); } catch (IOException ignored) {}
            }
        }

        // ---- Finalizar el servo ----
        robot.ServoMoveEnd(0);

        return 0;
    }

Fin del movimiento servo
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicio del movimiento servo, se utiliza junto con las instrucciones ServoJ y ServoCart
    * @param comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    public int ServoMoveEnd (int comType)

Movimiento en modo servo del espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento en modo servo del espacio de articulaciones
    * @param  joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param  axisPos  Posición del eje externo, unidad mm
    * @param  acc  Porcentaje de aceleración, rango [0~100], aún no disponible, valor predeterminado 0
    * @param  vel  Porcentaje de velocidad, rango [0~100], aún no disponible, valor predeterminado 0
    * @param  cmdT  Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016]
    * @param  filterT Tiempo de filtrado, unidad s, aún no disponible, valor predeterminado 0
    * @param  gain  Amplificador proporcional de la posición objetivo, aún no disponible, valor predeterminado 0
    * @param  id ID de la instrucción servoJ, valor predeterminado 0
    * @param comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    public int ServoJ(JointPos joint_pos, ExaxisPos axisPos, float acc, float vel, float cmdT, float filterT, float gain, int id, int comType)

Ejemplo de código SDK de ServoJ, ServoMoveStart y ServoMoveEnd basado en comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestServoJ(Robot robot)
    {
        robot.udpCmdClient.SetUDPCmdRpyCallback((srcType, count, cmdID, dataLen, content) -> {
            System.out.println("\n[Received UDP reply from robot]");
            System.out.println("srcType: " + srcType);
            System.out.println("count: " + count);
            System.out.println("cmdID: " + cmdID);
            System.out.println("dataLen: " + dataLen);
            System.out.println("contenido (content): " + content);
            return 0;
        });
        int rtn=-1;

        JointPos j=new JointPos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        double vel = 0.0;
        double acc = 0.0;
        double cmdT = 0.016;
        double filterT = 0.0;
        double gain = 0.0;
        int flag = 0;
        int count = 300;
        double dt = 0.1;
        int cmdID = 0;
        int comType = 1;
        int ret = robot.GetActualJointPosDegree(j);
        if (ret == 0)
        {
            robot.ServoMoveStart(comType);
            count = 300;
            while (count>0)
            {
                robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, comType);
                j.J1 += dt;
                j.J2 += dt;
                j.J4 += dt;
                j.J5 += dt;
                j.J6 += dt;
                epos.axis1 += dt;
                count -= 1;
                robot.Sleep(10);
            }
            robot.ServoMoveEnd(comType);

            robot.Sleep(1000);
            robot.ServoMoveStart(comType);
            count = 300;
            while (count>0)
            {
                robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, comType);
                j.J1 -= dt;
                j.J2 -= dt;
                j.J4 -= dt;
                j.J5 -= dt;
                j.J6 -= dt;
                epos.axis1 -= dt;
                count -= 1;
                robot.Sleep(10);
            }
            robot.ServoMoveEnd(comType);
        }
        else
        {
            System.out.println("GetActualJointPosDegree errcode:"+ ret);
        }
    }

Programa de ejemplo de movimiento en modo servo del espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestServoJ()
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
        JointPos j5 = new JointPos();
        ExaxisPos ePos=new ExaxisPos();
        int ret = robot.GetActualJointPosDegree(j5);
        if (ret == 0)
        {
            int count = 200;
            while (count > 0)
            {
                robot.ServoJ(j5, ePos,100, 100, 0.008, 0, 0);
                j5.J1 += 0.2;//Incremento de la posición de la articulación 1
                count -= 1;
                robot.WaitMs((int)(8));
            }
        }
    }

Movimiento en modo servo del espacio de articulaciones (admite la entrada de múltiples puntos a la vez)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimiento en modo servo del espacio de articulaciones (admite la entrada de múltiples puntos a la vez)
    * @param [in] joint_pos Conjunto de posiciones objetivo de las articulaciones (admite hasta 10 grupos), unidad deg
    * @param [in] axisPos Posición del eje externo, unidad mm
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible, valor predeterminado 0
    * @param [in] vel Porcentaje de velocidad, rango [0~100], aún no disponible, valor predeterminado 0
    * @param [in] cmdT Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016]
    * @param [in] filterT Tiempo de filtrado, unidad s, aún no disponible, valor predeterminado 0
    * @param [in] gain Amplificador proporcional de la posición objetivo, aún no disponible, valor predeterminado 0
    * @param [out] servoJCmdCount Contador de puntos de la instrucción ServoJ [0-10000]
    * @param [in] id ID de la instrucción servoJ, valor predeterminado 0
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    public int ServoJ(List<JointPos> joint_pos, ExaxisPos axisPos, float acc, float vel, float cmdT, float filterT, float gain, ref int servoJCmdCount, int id = 0, int comType = 0)

Ejemplo de código de movimiento en modo servo del espacio de articulaciones (admite la entrada de múltiples puntos a la vez)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestServoJPath(Robot robot)
    {
        // Lee el archivo de trayectoria ServoJ, tomando las columnas 2~7 de cada línea como las 6 posiciones de articulaciones
        String filePath = "D:\\zUP\\ServoJPath.txt";
        List<JointPos> allJointData = new ArrayList<>();
        try (BufferedReader reader = new BufferedReader(new FileReader(filePath)))
        {
            String line;
            while ((line = reader.readLine()) != null)
            {
                String[] cols = line.split("[ \\t]+");
                if (cols.length < 7)
                    continue;
                JointPos pose = new JointPos(0, 0, 0, 0, 0, 0);
                pose.J1 = Double.parseDouble(cols[1]);
                pose.J2 = Double.parseDouble(cols[2]);
                pose.J3 = Double.parseDouble(cols[3]);
                pose.J4 = Double.parseDouble(cols[4]);
                pose.J5 = Double.parseDouble(cols[5]);
                pose.J6 = Double.parseDouble(cols[6]);
                allJointData.add(pose);
            }
        }
        catch (IOException e)
        {
            System.out.println("Error al leer el archivo: " + e.getMessage());
            return;
        }
        System.out.println("Se leyeron en total " + allJointData.size() + " conjuntos de posiciones de articulaciones");
        if (allJointData.isEmpty())
            return;

        // Construir una trayectoria de ida y vuelta: orden directo + orden inverso
        List<JointPos> backForthPath = new ArrayList<>(allJointData);
        for (int i = allJointData.size() - 2; i >= 0; i--)
        {
            backForthPath.add(allJointData.get(i));
        }

        ExaxisPos epos = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offsetPos = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        robot.MoveJ(allJointData.get(0), 0, 0, 100, 100, 100, epos, -1, 0, offsetPos);

        robot.Sleep(1000);

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        while (true)
        {
            robot.ResetAllError();
            robot.MoveJ(allJointData.get(0), 0, 0, 100, 100, 100, epos, -1, 0, offsetPos);
            int moveCount = 0;
            while (moveCount < backForthPath.size() - 10)
            {
                pkg = robot.GetRobotRealTimeState();

                int singleServoJCount = 50 - pkg.mc_queue_len;
                if (singleServoJCount <= 0)
                {
                    robot.Sleep(100);
                    continue;
                }
                if (singleServoJCount > 10)
                {
                    singleServoJCount = 10;
                }

                List<JointPos> jointPos = new ArrayList<>();
                for (int j = 0; j < singleServoJCount; j++)
                {
                    jointPos.add(backForthPath.get(moveCount));
                    moveCount++;
                }

                System.out.println("Sending " + singleServoJCount + " waypoints, moveCount=" + moveCount);

                ExaxisPos axisPos = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
                int[] servoJCmdCount = new int[1];
                int rtn = robot.ServoJ(jointPos, axisPos, 100.0f, 100.0f, 0.008f, 0.008f, 1.0f, servoJCmdCount, 0, 0);
                if (rtn != 0)
                {
                    System.out.println("ServoJ failed: " + rtn);
                    break;
                }
            }
            robot.Sleep(4000);
        }
    }

Inicio del control de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Inicio del control de par de las articulaciones
    * @param  comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return  Código de error
    */
    public int ServoJTStart (int comType)

Control de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Control de par de las articulaciones
    * @param torque Par de las articulaciones j1~j6, unidad Nm
    * @param interval Período de instrucción, unidad s, rango [0.001~0.008]
    * @param checkFlag Estrategia de detección 0-sin límite; 1-limitar potencia; 2-limitar velocidad; 3-limitar potencia y velocidad simultáneamente
    * @param jPowerLimit Límite máximo de potencia de las articulaciones (W)
    * @param jVelLimit Velocidad máxima de las articulaciones (°/s)
    * @param  comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    public int ServoJT(double[] torque, double interval, int checkFlag, double[] jPowerLimit, double[] jVelLimit, int comType)

Fin del control de par de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Fin del control de par de las articulaciones
    * @param comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return  Código de error
    */
    public int ServoJTEnd (int comType)

Programa de ejemplo de movimiento en modo servo del espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestServoJT(Robot robot)
    {

        robot.DragTeachSwitch(1);
        List<Number> joint_toq=new ArrayList<>();
        joint_toq=robot.GetJointTorques(1);

        int count = 100;
        robot.ServoJTStart(); //   #inicio de servoJT
        int error = 0;
        while (count > 0)
        {
            error = robot.ServoJT(torques, 0.001);
            count = count - 1;
            robot.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);

        robot.CloseRPC();
        return 0;
    }

Ejemplo de código SDK de ServoJT, ServoJTStart y ServoJTEnd basado en comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void ServoJTWithSafety(Robot robot)
    {
        robot.udpCmdClient.SetUDPCmdRpyCallback((srcType, count, cmdID, dataLen, content) -> {
            System.out.println("\n[Received UDP reply from robot]");
            System.out.println("srcType: " + srcType);
            System.out.println("count: " + count);
            System.out.println("cmdID: " + cmdID);
            System.out.println("dataLen: " + dataLen);
            System.out.println("content: " + content);
            return 0;
        });
        while (true) {
            robot.ResetAllError();
            robot.Sleep(500);
            List<Number> torques;
            torques=robot.GetJointTorques(1);
            robot.ServoJTStart(1); //   #inicio de servoJT
            ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);
            int checkFlag = 3;//-1,3
            double[] jPowerLimit = { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
            double[] jVelLimit = { 50, 50, 50, 50, 50, 50};//180.1,-1
            int count = 800000;
            int error = 0;
            int comType = 1;

            double[] tor=new double[]{(double)torques.get(1),(double)torques.get(2),(double)torques.get(3),(double)torques.get(4),(double)torques.get(5),(double)torques.get(6)};

            while (true) {
                tor[0] = 0.08;//  #cada vez la articulación 1 aumenta 0.01NM, se mueve 100 veces
                error = robot.ServoJT(tor, 0.01, checkFlag, jPowerLimit, jVelLimit, comType);  //# movimiento en modo servo del espacio de articulaciones
                System.out.printf("ServoJT rtn is %d\n", error);
                count = count - 1;
                robot.Sleep(1);
                pkg = robot.GetRobotRealTimeState();
                System.out.printf("maincode %d, subcode %d\n", pkg.main_code, pkg.sub_code);
                if (pkg.jt_cur_pos[0] > 30)
                    break;
            }

            tor = new double[]{(double) torques.get(1), (double) torques.get(2), (double) torques.get(3), (double) torques.get(4), (double) torques.get(5), (double) torques.get(6)};
            while (true) {
                tor[0] = -0.08;//  #cada vez la articulación 1 aumenta 0.01NM, se mueve 100 veces
                error = robot.ServoJT(tor, 0.01, checkFlag, jPowerLimit, jVelLimit, 1);  //# movimiento en modo servo del espacio de articulaciones
                System.out.printf("ServoJT rtn is %d\n", error);
                count = count - 1;
                robot.Sleep(1);
                pkg = robot.GetRobotRealTimeState();
                System.out.printf("maincode %d, subcode %d\n", pkg.main_code, pkg.sub_code);
                if (pkg.jt_cur_pos[0] < 0)
                    break;
            }

            robot.DragTeachSwitch(0);

            error = robot.ServoJTEnd(1);  //#fin del movimiento servo
        }
    }

Ejemplo de código de control de par de las articulaciones con protección de exceso de velocidad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void ServoJTWithSafety(Robot robot)
    {
        robot.ResetAllError();
        robot.Sleep(500);
        List<Number> torques;
        torques=robot.GetJointTorques(1);
        robot.ServoJTStart(); //   #inicio de servoJT
        ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
        robot.DragTeachSwitch(1);
        int checkFlag = 3;//-1,3
        //double[] jPowerLimit = {1.0,1.0,1.0,1.0,1.0,1.0};//5001
        double[] jPowerLimit = { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
        double[] jVelLimit = { 50, 50, 50, 50, 50, 50};//180.1,-1
        int count = 800000;
        int error = 0;
        double[] tor=new double[]{(double)torques.get(1),(double)torques.get(2),(double)torques.get(3),(double)torques.get(4),(double)torques.get(5),(double)torques.get(6)};
        while (count > 0)
        {
            tor[2] = tor[2]+0.01;//  #cada vez la articulación 1 aumenta 0.01NM, se mueve 100 veces
            error = robot.ServoJT(tor, 0.01, checkFlag, jPowerLimit, jVelLimit);  //# movimiento en modo servo del espacio de articulaciones
            System.out.printf("ServoJT rtn is %d\n", error);
            count = count - 1;
            robot.Sleep(1);
            pkg=robot.GetRobotRealTimeState();
            System.out.printf("maincode %d, subcode %d\n", pkg.main_code, pkg.sub_code);
        }
        robot.DragTeachSwitch(0);
        error = robot.ServoJTEnd();  //#fin del movimiento servo
    }

Movimiento en modo servo del espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    *@brief Movimiento en modo servo del espacio cartesiano
    *@param mode 0-movimiento absoluto (sistema de coordenadas base), 1-movimiento incremental (sistema de coordenadas base), 2-movimiento incremental (sistema de coordenadas de herramienta)
    *@param desc_pose Pose cartesiana objetivo o incremento de pose
    *@param exaxis Posición del eje extendido
    *@param pos_gain Coeficiente proporcional del incremento de pose, solo efectivo en movimiento incremental, rango [0~1]
    *@param acc Porcentaje de aceleración, rango [0~100], aún no disponible, valor predeterminado 0
    *@param vel Porcentaje de velocidad, rango [0~100], aún no disponible, valor predeterminado 0
    *@param cmdT Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.016]
    *@param filterT Tiempo de filtrado, unidad s, aún no disponible, valor predeterminado 0
    *@param gain Amplificador proporcional de la posición objetivo, aún no disponible, valor predeterminado 0
    *@return Código de error
    */
    public int ServoCart(int mode, DescPose desc_pose, ExaxisPos exaxis, double[] pos_gain, double acc, double vel, double cmdT, double filterT, double gain)

Ejemplo de código de movimiento en modo servo del espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestServoCart1(Robot robot)
    {
        DescPose desc_pos_dt = new DescPose(83.00800, 50.525000 , 29.246 , 179.629 , -7.138 , -166.975 );
        ExaxisPos exaxis = new ExaxisPos( 100.0, 0.0, 0.0, 0.0 );
        double[] pos_gain = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        int mode = 0;
        double vel = 0.0;
        double acc = 0.0;
        double cmdT = 0.001;
        double filterT = 0.0;
        double gain = 0.0;
        int flag = 0;
        int count = 5000;
        robot.SetSpeed(20);
        while (count>0)
        {
            int rtn = robot.ServoCart(mode, desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
            System.out.printf("ServoCart rtn is %d\n", rtn);
            count -= 1;
            desc_pos_dt.tran.x += 0.01;
            exaxis.axis1 += 0.01;
        }
        robot.CloseRPC();
    }

Inicio del movimiento por spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Inicio del movimiento por spline
    * @return  Código de error
    */
    int SplineStart();

Movimiento PTP de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento por spline en el espacio de articulaciones
    * @param  [in] joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número de coordenada de herramienta, rango [0~14]
    * @param  [in] user  Número de coordenada de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @return  Código de error
    */
    int SplinePTP(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl);

Movimiento por spline en el espacio de articulaciones (cálculo automático de cinemática directa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento por spline en el espacio de articulaciones (cálculo automático de cinemática directa)
    * @param  [in] joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param  [in] tool  Número de coordenada de herramienta, rango [0~14]
    * @param  [in] user  Número de coordenada de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @return  Código de error
    */
    int SplinePTP(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl)

Fin del movimiento por spline
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Fin del movimiento por spline
    * @return  Código de error
    */
    int SplineEnd(); 

Ejemplo de código de movimiento por spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSpline(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3=new JointPos(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
        JointPos j4=new JointPos(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        int err1 = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.println("movej errcode:"+ err1);
        robot.SplineStart();
        robot.SplinePTP(j1, tool, user, vel, acc, ovl);
        robot.SplinePTP(j2, tool, user, vel, acc, ovl);
        robot.SplinePTP(j3, tool, user, vel, acc, ovl);
        robot.SplinePTP(j4, tool, user, vel, acc, ovl);
        robot.SplineEnd();
        return 0;
    }

Inicio del nuevo movimiento por spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Inicio del nuevo movimiento por spline 
    * @param [in] type   0-transición de arco, 1-los puntos dados son puntos de trayectoria
    * @param [in] averageTime  Tiempo medio global de conexión (ms) (10 ~  ), valor predeterminado 2000
    * @return Código de error 
    */ 
    int NewSplineStart(int type, int averageTime);
    
Punto de instrucción del nuevo spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Añadir un punto de instrucción de movimiento por spline 
    * @param [in] joint_pos  Posición objetivo de las articulaciones, unidad deg
    * @param [in] desc_pos   Pose cartesiana objetivo
    * @param [in] tool  Número de coordenada de herramienta, rango [0~14]
    * @param [in] user  Número de coordenada de pieza, rango [0~14]
    * @param [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] lastFlag Si es el último punto, 0-no, 1-sí
    * @return Código de error 
    */ 
    int NewSplinePoint(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int lastFlag);

Punto de instrucción del nuevo spline (cálculo automático de cinemática inversa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Punto de instrucción del nuevo spline (cálculo automático de cinemática inversa)
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número de coordenada de herramienta, rango [0~14]
    * @param  [in] user  Número de coordenada de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] lastFlag Si es el último punto, 0-no, 1-sí
    * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición actual de las articulaciones, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return  Código de error
    */
    int NewSplinePoint(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int lastFlag,int config)

Fin del nuevo movimiento por spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Inicio del nuevo movimiento por spline 
    * @return Código de error 
    */ 
    int NewSplineEnd();
    
Ejemplo de código del nuevo movimiento por spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestNewSpline(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3=new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
        DescPose desc_pos4=new DescPose(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
        DescPose desc_pos5=new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);


        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;


        int err1 = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.println("movej errcode:"+ err1);
        robot.NewSplineStart(1, 2000);
        robot.NewSplinePoint(desc_pos1, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos2, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos3, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos4, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos5, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplineEnd();
        return 0;
    }

Terminar el movimiento
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Terminar el movimiento
    * @return  Código de error
    */
    int StopMotion();

Pausar el movimiento
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:
    
    /** 
      * @brief Pausar el movimiento 
      * @return Código de error 
    */  
    int PauseMotion();

Reanudar el movimiento
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Reanudar el movimiento 
    * @return Código de error 
    */ 
    int ResumeMotion();

Ejemplo de código de pausa, reanudación y detención del movimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestPause(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j5=new JointPos(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos5=new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        robot.SetSpeed(20);
        int rtn=-1;
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        rtn = robot.MoveJ(j5, desc_pos5, tool, user, vel, acc, ovl, epos, 1, flag, offset_pos);
        robot.Sleep(1000);
        robot.PauseMotion();

        robot.Sleep(1000);
        robot.ResumeMotion();

        robot.Sleep(1000);
        robot.StopMotion();

        robot.Sleep(1000);

        return 0;
    }

Inicio del desplazamiento global de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Inicio del desplazamiento global de puntos
    * @param  [in]  flag  0-desplazamiento en el sistema de coordenadas base/de pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in]  offset_pos  Cantidad de desplazamiento de la pose
    * @return  Código de error
    */
    int PointsOffsetEnable(int flag, DescPose offset_pos); 


Fin del desplazamiento global de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Fin del desplazamiento global de puntos
    * @return  Código de error
    */
    int PointsOffsetDisable(); 

Ejemplo de código de desplazamiento de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestOffset(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        DescPose offset_pos1=new DescPose(0, 0, 50, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        robot.SetSpeed(20);

        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.Sleep(1000);
        robot.PointsOffsetEnable(0, offset_pos1);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.PointsOffsetDisable();

        return 0;
    }

Inicio de la salida AO sincronizada con el movimiento de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicio de la salida AO sincronizada con el movimiento de la caja de control
    * @param [in] AONum Número de AO de la caja de control
    * @param [in] maxTCPSpeed Valor máximo de velocidad TCP [1-5000mm/s], valor predeterminado 1000
    * @param [in] maxAOPercent Porcentaje de AO correspondiente al valor máximo de velocidad TCP, valor predeterminado 100%
    * @param [in] zeroZoneCmp Valor de compensación de zona muerta, porcentaje de AO, entero, valor predeterminado 20%, rango [0-100]
    * @return Código de error
    */
    int MoveAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Fin de la salida AO sincronizada con el movimiento de la caja de control
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fin de la salida AO sincronizada con el movimiento de la caja de control
    * @return Código de error
    */
    int MoveAOStop();
    
Inicio de la salida AO sincronizada con el movimiento del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicio de la salida AO sincronizada con el movimiento del extremo
    * @param [in] AONum Número de AO del extremo
    * @param [in] maxTCPSpeed Valor máximo de velocidad TCP [1-5000mm/s], valor predeterminado 1000
    * @param [in] maxAOPercent Porcentaje de AO correspondiente al valor máximo de velocidad TCP, valor predeterminado 100%
    * @param [in] zeroZoneCmp Valor de compensación de zona muerta, porcentaje de AO, entero, valor predeterminado 20%, rango [0-100]
    * @return Código de error
    */
    int MoveToolAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);
    
Fin de la salida AO sincronizada con el movimiento del extremo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fin de la salida AO sincronizada con el movimiento del extremo
    * @return Código de error
    */
    int MoveToolAOStop();

Ejemplo de código de salida AO sincronizada con el movimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestMoveAO(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        DescPose offset_pos1=new DescPose(0, 0, 50, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 20.0;
        double acc = 20.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        robot.SetSpeed(20);

        robot.MoveAOStart(0, 100, 100, 20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveAOStop();

        robot.Sleep(1000);

        robot.MoveToolAOStart(0, 100, 100, 20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveToolAOStop();

        return 0;
    }

Inicio del filtrado FIR del movimiento Ptp
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Inicio del filtrado FIR del movimiento Ptp
    * @param [in] maxAcc Valor extremo máximo de aceleración (deg/s2)
    * @param [in] maxJek Valor extremo unificado de jerk (sobreaceleración) de las articulaciones (deg/s3)
    * @return Código de error
    */
    int PtpFIRPlanningStart(double maxAcc,double maxJek);

Cierre del filtrado FIR del movimiento Ptp
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Cierre del filtrado FIR del movimiento Ptp
    * @return Código de error
    */
    int PtpFIRPlanningEnd();

Inicio del filtrado FIR del movimiento LIN y ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicio del filtrado FIR del movimiento LIN y ARC
    * @param [in] maxAccLin Valor extremo de aceleración lineal (mm/s2)
    * @param [in] maxAccDeg Valor extremo de aceleración angular (deg/s2)
    * @param [in] maxJerkLin Valor extremo de jerk lineal (mm/s3)
    * @param [in] maxJerkDeg Valor extremo de jerk angular (deg/s3)
    * @return Código de error
    */
    int LinArcFIRPlanningStart(double maxAccLin, double maxAccDeg, double maxJerkLin, double maxJerkDeg);

Cierre del filtrado FIR del movimiento LIN y ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Cierre del filtrado FIR del movimiento LIN y ARC
    * @return Código de error
    */
    int LinArcFIRPlanningEnd();

Ejemplo de código de filtrado FIR
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFIR(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos midjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos endjointPos=new JointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose middescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose enddescPose=new DescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        int rtn = robot.PtpFIRPlanningStart(1000, 1000);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.PtpFIRPlanningEnd();

        robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000);
        robot.MoveL(startjointPos, startdescPose, 0, 0, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 1, 1);
        robot.MoveC(midjointPos, middescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, endjointPos, enddescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, 100, -1);
        robot.LinArcFIRPlanningEnd();
        return 0;
    }

Activación del suavizado de aceleración
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1
.. code-block:: Java
    :linenos:

    /**
     * @brief Activación del suavizado de aceleración
     * @param [in] saveFlag Si se guarda tras un corte de energía
     * @return  Código de error
     */
    public int AccSmoothStart(boolean saveFlag)

Desactivación del suavizado de aceleración
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1
.. code-block:: Java
    :linenos:

    /**
     * @brief Desactivación del suavizado de aceleración
     * @param [in] saveFlag Si se guarda tras un corte de energía
     * @return  Código de error
     */
    public int AccSmoothEnd(boolean saveFlag)

Ejemplo de código de suavizado de aceleración
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAccSmooth(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos endjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose enddescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0,0,0,0,0,0);
        int rtn = robot.AccSmoothStart(false);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.AccSmoothEnd(false);

        robot.CloseRPC();
        return 0;
    }

Activación de la velocidad de orientación especificada
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Activación de la velocidad de orientación especificada
     * @param [in] ratio Porcentaje de velocidad de orientación [0-300]
     * @return  Código de error
     */
    int AngularSpeedStart(int ratio)

Desactivación de la velocidad de orientación especificada
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Desactivación de la velocidad de orientación especificada
     * @return  Código de error
     */
    int AngularSpeedEnd();

Ejemplo de código de velocidad de orientación especificada del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAngularSpeed(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos endjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose enddescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
        int rtn = robot.AngularSpeedStart(50);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.AngularSpeedEnd();

        return 0;
    }

Inicio de la protección de pose singular
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Inicio de la protección de pose singular
    * @param  [in]  protectMode Modo de protección singular, 0: modo de articulaciones; 1-modo cartesiano
    * @param  [in]  minShoulderPos Rango de ajuste de singularidad de hombro (mm), valor predeterminado 100
    * @param  [in]  minElbowPos Rango de ajuste de singularidad de codo (mm), valor predeterminado 50
    * @param  [in]  minWristPos Rango de ajuste de singularidad de muñeca (°), valor predeterminado 10
    * @return  Código de error
    */
    int SingularAvoidStart(int protectMode, double minShoulderPos, double minElbowPos, double minWristPos);

Detención de la protección de pose singular
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Detención de la protección de pose singular
    * @return  Código de error
    */
    int SingularAvoidEnd();

Espera a que finalice el movimiento en vacío en el lugar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:    

    /**
    * @brief Espera a que finalice el movimiento en vacío en el lugar
    * @return Código de error
    */
    public int WaitStationaryMotionDone()

Ejemplo de código de protección de pose singular del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAngularSpeed(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos endjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose enddescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
        int rtn = robot.AngularSpeedStart(50);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.AngularSpeedEnd();

        return 0;
    }

Vaciar la cola de instrucciones de movimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Vaciar la cola de instrucciones de movimiento
    * @return Código de error
    */
    public int MotionQueueClear()

Moverse al punto inicial de la línea de intersección
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Moverse al punto inicial de la línea de intersección
    * @param [in] mainPoint Pose cartesiana de los 6 puntos de enseñanza del tubo principal
    * @param [in] mainExaxisPos Posición del eje extendido de los 6 puntos de enseñanza del tubo principal
    * @param [in] piecePoint Pose cartesiana de los 6 puntos de enseñanza del tubo auxiliar
    * @param [in] pieceExaxisPos Posición del eje extendido de los 6 puntos de enseñanza del tubo de empalme
    * @param [in] extAxisFlag Si se habilita el eje extendido; 0-no habilitar; 1-habilitar
    * @param [in] exaxisPos Posición del eje extendido del punto inicial
    * @param [in] tool Número del sistema de coordenadas de herramienta
    * @param [in] wobj Número del sistema de coordenadas de pieza
    * @param [in] vel Porcentaje de velocidad
    * @param [in] acc Porcentaje de aceleración
    * @param [in] ovl Factor de escala de velocidad
    * @param [in] oacc Factor de escala de aceleración
    * @param [in] moveType Tipo de movimiento; 0-PTP; 1-LIN
    * @param [in] moveDirection Dirección de movimiento; 0-sentido horario; 1-sentido antihorario
    * @param [in] offset Cantidad de desplazamiento
    * @return Código de error
    */
    public int MoveToIntersectLineStart(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveType, int moveDirection, DescPose offset);
            
Movimiento de línea de intersección
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimiento de línea de intersección
    * @param [in] mainPoint Pose cartesiana de los 6 puntos de enseñanza del tubo principal
    * @param [in] mainExaxisPos Posición del eje extendido de los 6 puntos de enseñanza del tubo principal
    * @param [in] piecePoint Pose cartesiana de los 6 puntos de enseñanza del tubo auxiliar
    * @param [in] pieceExaxisPos Posición del eje extendido de los 6 puntos de enseñanza del tubo de empalme
    * @param [in] extAxisFlag Si se habilita el eje extendido; 0-no habilitar; 1-habilitar
    * @param [in] exaxisPos Posición del eje extendido del punto inicial
    * @param [in] tool Número del sistema de coordenadas de herramienta
    * @param [in] wobj Número del sistema de coordenadas de pieza
    * @param [in] vel Porcentaje de velocidad
    * @param [in] acc Porcentaje de aceleración
    * @param [in] ovl Factor de escala de velocidad
    * @param [in] oacc Factor de escala de aceleración
    * @param [in] moveDirection Dirección de movimiento; 0-sentido horario; 1-sentido antihorario
    * @param [in] offset Cantidad de desplazamiento
    * @return Código de error
    */
    public int MoveIntersectLine(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos[] exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveDirection, DescPose offset);
                
Ejemplo de código de movimiento de línea de intersección del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestIntersectLineMove(Robot robot)
    {
        DescPose[] mainPoint = new DescPose[6];
        DescPose[] piecePoint = new DescPose[6];
        ExaxisPos[] mainExaxisPos = new ExaxisPos[6];
        ExaxisPos[] pieceExaxisPos = new ExaxisPos[6];
        int extAxisFlag = 1;
        ExaxisPos[] exaxisPos = new ExaxisPos[4];
        DescPose offset =new DescPose(0.0, 2.0 ,30.0, -2.0, 0.0, 0.0 );
        mainPoint[0] = new DescPose(490.004, -383.194, 402.735, -9.332, -1.528, 69.594);
        mainPoint[1] = new DescPose(444.950, -407.117, 389.011, -5.546, -2.196, 65.279);
        mainPoint[2] = new DescPose(445.168, -463.605, 355.759, -1.544, -10.886, 57.104);
        mainPoint[3] = new DescPose(507.529, -485.385, 343.013, -0.786, -4.834, 61.799);
        mainPoint[4] = new DescPose(554.390, -442.647, 367.701, -4.761, -10.181, 64.925);
        mainPoint[5] = new DescPose(532.552, -394.003, 396.467, -13.732, -13.592, 67.411);
        mainExaxisPos[0] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[1] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[2] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[3] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[4] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[5] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        piecePoint[0] = new DescPose( 505.571, -192.408, 316.759, 38.098, 37.051, 139.447);
        piecePoint[1] =new DescPose(533.837, -201.558, 332.340, 34.644, 42.339, 137.748);
        piecePoint[2] =new DescPose(530.386, -225.085, 373.808, 35.431, 45.111, 137.560);
        piecePoint[3] =new DescPose(485.646, -229.195, 383.778, 33.870, 45.173, 137.064);
        piecePoint[4] =new DescPose(460.551, -212.161, 354.256, 28.856, 45.602, 135.930);
        piecePoint[5] =new DescPose(474.217, -197.124, 324.611, 42.469, 41.133, 148.167);
        pieceExaxisPos[0] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[1] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[2] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[3] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[4] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[5] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        exaxisPos[0] = new ExaxisPos(-29.996, -0.000, 0.000, 0.000);
        exaxisPos[1] = new ExaxisPos(-44.994, 90.000, 0.000, 0.000);
        exaxisPos[2] = new ExaxisPos(-59.992, 0.002, 0.000, 0.000);
        exaxisPos[3] = new ExaxisPos(-44.994, -89.997, 0.000, 0.000);
        int tool = 2;
        int wobj = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 12.0;
        double oacc = 12.0;
        int moveType = 1;
        int moveDirection = 1;
        int  rtn = robot.MoveToIntersectLineStart(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos[0], tool, wobj, vel, acc, ovl, oacc, moveType, moveDirection, offset);
        System.out.printf("MoveToIntersectLineStart rtn is %d\n", rtn);
        rtn = robot.MoveIntersectLine(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos, tool, wobj, vel, acc, 5.0, 5.0, moveDirection, offset);
        System.out.printf("MoveIntersectLine rtn is %d\n", rtn);
        robot.CloseRPC();
        return ;
    }
                
Movimiento en vacío en el lugar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimiento en vacío en el lugar
    * @return Código de error
    */
    public int MoveStationary()

Ejemplo de código de movimiento en vacío en el lugar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void test_RecordandReplay(Robot robot)
    {
        int rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 1, 10, 100);
        System.out.printf("LaserSensorRecordandReplay rtn is %d\n", rtn);
        rtn = robot.MoveStationary();
        System.out.printf("MoveStationary rtn is %d\n", rtn);
        rtn = robot.LaserSensorRecord1(0, 10);
        System.out.printf("LaserSensorRecordandReplay rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(9999999);
    }

Inicio de la oscilación de punto fijo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicio de la oscilación de punto fijo
    * @param [in] weaveNum Número de oscilación [0-7]
    * @param [in] mode 0-sistema de coordenadas de herramienta; 1-punto de referencia
    * @param [in] refPoint Coordenadas cartesianas del punto de referencia [x,y,z,a,b,c]
    * @param [in] weaveTime Tiempo de oscilación [s]
    * @return Código de error
    */
    public int OriginPointWeaveStart(int weaveNum, int mode, DescPose refPoint, double weaveTime)
    
Fin de la oscilación de punto fijo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fin de la oscilación de punto fijo
    * @return Código de error
    */
    public int OriginPointWeaveEnd();
        
Ejemplo de código SDK de oscilación de punto fijo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestOriginPointWeave(Robot robot) {
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);
        robot.MoveJ(j, 1, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        
        robot.OriginPointWeaveStart(0, 0, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();

        robot.Sleep(2000);

        robot.MoveJ(j, 1, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.OriginPointWeaveStart(0, 1, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();

        robot.Sleep(1000);
        return 0;
    }

Ejemplo de código SDK de oscilación de punto fijo (incluye láser y eje extendido)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestOriginPointWeave(Robot robot) {
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos1 = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos2 = new ExaxisPos(5, 0, 0, 0);
        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);

        int rtn = 0;
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);

        // Cargar el controlador UDP
        robot.ExtDevLoadUDPDriver();

        // Establecer el tiempo de finalización del comando del eje externo
        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        System.out.println("SetExAxisCmdDoneTime rtn is " + rtn);
        // Habilitar los ejes externos 1 y 2
        rtn = robot.ExtAxisServoOn(1, 1);
        System.out.println("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        System.out.println("ExtAxisServoOn axis id 2 rtn is " + rtn);
        robot.Sleep(2000);

        // Establecer el retorno a cero del eje externo
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.LaserTrackingLaserOnOff(1,0);


        // 1---sin eje extendido
        robot.LaserTrackingTrackOnOff(1, 4);
        robot.Sleep(200);
        // Iniciar la oscilación de punto fijo
        robot.OriginPointWeaveStart(0, 0, refPoint, 10);
        robot.MoveStationary();   // Ejecutar el movimiento fijo (se asume que el método existe)
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);

        robot.Sleep(2000);         // Esperar 2 segundos

        // 2----con eje extendido
        robot.ExtAxisMove(epos1, 100, -1);
        robot.LaserTrackingTrackOnOff(1, 4);
        // Iniciar la oscilación de punto fijo
        robot.OriginPointWeaveStart(0, 0, refPoint, 20);
        robot.ExtAxisMove(epos2, 100, -1);
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);

        robot.Sleep(1000);
        return 0;
    }
    
Movimiento en modo servo de velocidad del espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimiento en modo servo de velocidad del espacio de articulaciones
    * @param   joint_vel  Velocidad objetivo de las 6 articulaciones, unidad deg/s
    * @param   exis_vel  Velocidad de los 4 ejes externos, unidad deg/s
    * @param   acc  Porcentaje de aceleración, rango [0~100], aún no disponible, valor predeterminado 0
    * @param   vel  Porcentaje de velocidad, rango [0~100], aún no disponible, valor predeterminado 0
    * @param   cmdT  Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016]
    * @param   filterT Tiempo de filtrado, unidad s, aún no disponible, valor predeterminado 0
    * @param   gain  Amplificador proporcional de la posición objetivo, aún no disponible, valor predeterminado 0
    * @param   id  ID de la instrucción servoJ, valor predeterminado 0
    * @param   comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return  Código de error
    */
    public int ServoJV(double[] joint_vel, double[] exis_vel, double acc, double vel, double cmdT, double filterT, double gain, int id, int comType)

Ejemplo de código de movimiento en modo servo de velocidad del espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int ServoJVtest(Robot robot)
    {
        double[] joint_vel = new double[] { 10, 0, 0, 0, 0, 0 };
        double[] exis_vel = new double[] { 0, 0, 0, 0 };
        double acc = 0.0;
        double vel = 0.0;
        double cmdT = 0.008;
        double filterT = 0.0;
        double gain = 0.0;
        int cnt = 0;
        while (cnt < 200)
        {
            int error = robot.ServoJV(joint_vel, exis_vel, acc, vel, cmdT, filterT, gain);
            System.out.println("MAIN ServoJV rtn is " + error);
    //            robot.Sleep(10);
            cnt++;
        }

        return 0;
    }

Inicio del control MIT de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inicio del control MIT de las articulaciones
    * @param  comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    errno_t ServoMITStart(int comType = 0);

Fin del control MIT de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fin del control MIT de las articulaciones
    * @param  comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    public int ServoMITEnd(int comType);

Control MIT de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Control MIT de las articulaciones
    * @param  posGain Ganancia de posición de las articulaciones j1~j6
    * @param  desPos Posición deseada de las articulaciones j1~j6, unidad: deg
    * @param  velGain Ganancia de velocidad de las articulaciones j1~j6
    * @param  desVel Velocidad deseada de las articulaciones j1~j6, unidad: deg/s
    * @param  torque_ff Par de prealimentación de las articulaciones j1~j6, unidad: Nm
    * @param  interval Período de instrucción, unidad s, rango [0.001~0.008]
    * @param  comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    public int ServoMIT(double[] posGain, double[] desPos, double[] velGain, double[] desVel, double[] torque_ff, double interval, int comType)

Ejemplo de código de control MIT de las articulaciones del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int ServoMITtest(Robot robot)
    {
            robot.udpCmdClient.SetUDPCmdRpyCallback((srcType, count, cmdID, dataLen, content) -> {
            System.out.println("\n[Received UDP reply from robot]");
            System.out.println("srcType: " + srcType);
            System.out.println("count: " + count);
            System.out.println("cmdID: " + cmdID);
            System.out.println("dataLen: " + dataLen);
            System.out.println("content: " + content);
            return 0;
        });
        while (true)
        {
            robot.ResetAllError();
            robot.Sleep(500);

            double[] posGain = new double[] { 0, 0, 0, 0, 0, 0 };
            double[] desPos = new double[] { 0, 0, 0, 0, 0, 0 };
            double[] velGain = new double[] { 0, 0, 0, 0, 0, 0 };
            double[] desVel = new double[] { 0, 0, 0, 0, 0, 0 };

            List<Number> joint_toq=new ArrayList<>();
            joint_toq=robot.GetJointTorques(1);
            double[] torques=new double[]{(double)joint_toq.get(1),(double)joint_toq.get(2),(double)joint_toq.get(3),(double)joint_toq.get(4),(double)joint_toq.get(5),(double)joint_toq.get(6)};
            System.out.println("111111");

            robot.ServoMITStart(0);
            System.out.println("ServoMITStart");

            ROBOT_STATE_PKG pkg = robot.GetRobotRealTimeState();
            robot.DragTeachSwitch(1);
            System.out.println("DragTeachSwitch");

            double intev = 0.008;
            int error = 0;

            while (true)
            {
                torques[5] = 0.03;
                System.out.println("ServoMIT call");
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                System.out.println("ServoMIT111111 rtn is " + error);
                robot.Sleep(1);

                pkg = robot.GetRobotRealTimeState();
                System.out.println("pkg.jt_cur_pos[5]:" + pkg.jt_cur_pos[5]);
                if (pkg.jt_cur_pos[5] > 30)
                {
                    break;
                }
            }

            while (true)
            {
                torques[5] = -0.03;
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                System.out.println("ServoJT222222 rtn is " + error);
                robot.Sleep(1);

                pkg = robot.GetRobotRealTimeState();
                System.out.println("pkg.jt_cur_pos[5]:" + pkg.jt_cur_pos[5]);
                if (pkg.jt_cur_pos[5] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoMITEnd(0);
        }
        // return 0;
    }

Inicio de la conversión de puntos del sistema de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:    

    /**
    * @brief Inicio de la conversión de puntos del sistema de coordenadas de pieza
    * @param workpieceID Número de pieza [0-14]
    * @return Código de error, devuelve 0 en caso de éxito
    */
    public int WorkPieceTrsfStart(int workpieceID)

Fin de la conversión de puntos del sistema de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:    

    /**
    * @brief Fin de la conversión de puntos del sistema de coordenadas de pieza
    * @return Código de error, devuelve 0 en caso de éxito
    */
    public int WorkPieceTrsfEnd()

Ejemplo de código de movimiento de conversión del sistema de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:    
    
    public static int TestWorkPieceTrsf(Robot robot) {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        JointPos j1 = new JointPos(-11.188, -64.165, -107.299, -76.706, 89.590, 92.983);
        DescPose desc1 = new DescPose(225.986, 190.694, 394.238, -6.230, -23.797, -98.972);
        JointPos j2 = new JointPos(-38.148, -97.408, -133.704, -30.999, 89.584, 92.986);
        DescPose desc2 = new DescPose(52.741, 262.917, 30.824, -5.696, -9.864, -126.092);
        JointPos j3 = new JointPos(-25.561, -123.131, -85.736, -94.911, 89.582, 93.006);
        DescPose desc3 = new DescPose(70.455, 88.410, 45.299, -4.101, 31.775, -113.199);
        JointPos j4 = new JointPos(-8.013, -125.881, -79.196, -84.440, 89.564, 93.005);
        DescPose desc4 = new DescPose(209.453, -73.895, 56.416, -4.727, 17.523, -95.906);
        JointPos j5 = new JointPos(-2.722, -94.518, -119.965, -54.518, 89.563, 93.005);
        DescPose desc5 = new DescPose(274.800, 81.106, 102.977, -5.467, -2.980, -90.711);
        JointPos j6 = new JointPos(-2.671, -56.234, -138.914, -25.099, 95.355, 92.967);
        DescPose desc6 = new DescPose(300.392, 177.281, 300.926, -1.909, -51.894, -89.703);
        JointPos j7 = new JointPos(-1.229, -121.184, -63.201, -122.331, 93.045, 93.019);
        DescPose desc7 = new DescPose(296.856, -31.294, 215.698, -0.589, 34.594, -88.954);

        ExaxisPos exaxis = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offset = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);

        int tool = 1;
        int workpiece = 1;
        double blend = 5.0;

        robot.MoveJ(j1, desc1, tool, workpiece, 100, 100, 100, exaxis, -1, 0, offset);
        robot.MoveJ(j2, desc2, tool, workpiece, 100, 100, 100, exaxis, blend, 0, offset);
        robot.MoveL(j3, desc3, tool, workpiece, 10, 100, 100, blend, 0, exaxis, 0, 1, offset,-1, 0,0,0);
        robot.MoveC(j4, desc4, tool, workpiece, 100, 100, exaxis, 0, offset, j5, desc5, tool, workpiece, 100, 100, exaxis, 0, offset, 10, blend,100, 0);
        robot.Circle(j6, desc6, tool, workpiece, 100, 100, exaxis, j7, desc7, tool, workpiece, 100, 100, exaxis, 10, 0, offset, 100.0, blend,0);

        int rtn = robot.WorkPieceTrsfStart(2);
        System.out.printf("WorkPieceTrsfStart rtn is %d\n", rtn);
        robot.MoveJ(j1, desc1, tool, workpiece, 100, 100, 100, exaxis, -1, 0, offset);
        robot.MoveJ(j2, desc2, tool, workpiece, 100, 100, 100, exaxis, blend, 0, offset);
        robot.MoveL(j3, desc3, tool, workpiece, 10, 100, 100, blend, 0, exaxis, 0, 1, offset,-1, 0,0,0);
        robot.MoveC(j4, desc4, tool, workpiece, 100, 100, exaxis, 0, offset, j5, desc5, tool, workpiece, 100, 100, exaxis, 0, offset, 10, blend,100, 0);
        robot.Circle(j6, desc6, tool, workpiece, 100, 100, exaxis, j7, desc7, tool, workpiece, 100, 100, exaxis, 10, 0, offset, 100.0, blend, 0);

        robot.WorkPieceTrsfEnd();
        System.out.printf("WorkPieceTrsfEnd rtn is %d\n", rtn);
        robot.Sleep(2000);
        return 0;
    }