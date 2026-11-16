Movimiento del robot
====================

.. toctree:: 
    :maxdepth: 5


Jog (movimiento manual por pulsación)
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief  Jog (movimiento manual por pulsación)
    * @param [in] refType Tipo de jog: 0-jog de articulaciones, 2-jog en el sistema de coordenadas base, 4-jog en el sistema de coordenadas de herramienta, 8-jog en el sistema de coordenadas de pieza 
    * @param [in] nb 1-articulación 1 (o eje x), 2-articulación 2 (o eje y), 3-articulación 3 (o eje z), 4-articulación 4 (o rotación alrededor del eje x), 5-articulación 5 (o rotación alrededor del eje y), 6-articulación 6 (o rotación alrededor del eje z)
    * @param [in] dir 0-dirección negativa, 1-dirección positiva 
    * @param [in] vel Porcentaje de velocidad, [0~100] 
    * @param [in] acc Porcentaje de aceleración, [0~100] 
    * @param [in] max_dis Ángulo máximo de un solo jog, unidad [°] o distancia, unidad [mm] 
    * @return Código de error 
    */ 
    int StartJOG(byte refType, byte nb, byte dir, float vel, float acc, float max_dis);

Parada del jog con desaceleración
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Parada del jog con desaceleración
    * @param  [in]  ref  1-parada del jog de articulaciones, 3-parada del jog en el sistema de coordenadas base, 5-parada del jog en el sistema de coordenadas de herramienta, 9-parada del jog en el sistema de coordenadas de pieza
    * @return  Código de error
    */
    int StopJOG(byte stopType);

Parada inmediata del jog
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Parada inmediata del jog
    * @return  Código de error
    */
    int ImmStopJOG(); 

Ejemplo de código de control del jog del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnJOG_Click(object sender, EventArgs e)
    {
        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(0, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.ImmStopJOG();
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(2, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.ImmStopJOG();
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(4, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.StopJOG(5);
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(8, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.StopJOG(9);
            Thread.Sleep(1000);
        }
    }

Movimiento en el espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento en el espacio de articulaciones
    * @param  [in] joint_pos  Posición articular objetivo, unidad deg
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] user  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] epos  Posición del eje extendido, unidad mm
    * @param  [in] blendT [-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad ms
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Magnitud del desplazamiento de pose
    * @return  Código de error
    */
    int MoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos); 

Movimiento en el espacio de articulaciones (cálculo automático de cinemática directa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief  Movimiento en el espacio de articulaciones (cálculo automático de cinemática directa)
    * @param  [in] joint_pos  Posición articular objetivo, unidad deg
    * @param  [in] tool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] user  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] epos  Posición del eje extendido, unidad mm
    * @param  [in] blendT [-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad ms
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Magnitud del desplazamiento de pose
    * @return Código de error 
    */ 
    int MoveJ(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos)


Movimiento lineal en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimiento lineal en el espacio cartesiano
    * @param [in] joint_pos Posición articular objetivo, unidad deg
    * @param [in] desc_pos Pose cartesiana objetivo
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl Factor de escala de velocidad [0~100]/velocidad física (mm/s)
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] blendMode Modo de transición; 0-transición tangente interna; 1-transición por esquina
    * @param [in] epos Posición del eje extendido, unidad mm
    * @param [in] search 0-sin búsqueda de posición del alambre de soldadura, 1-búsqueda de posición del alambre de soldadura
    * @param [in] offset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos Magnitud del desplazamiento de pose
    * @param [in] oacc Factor de escala de aceleración [0-100]/aceleración física (mm/s2)
    * @param [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @param [in] overSpeedStrategy Estrategia de tratamiento de exceso de velocidad, 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, por defecto 0
    * @param [in] speedPercent Porcentaje de umbral de reducción de velocidad permitido [0-100], por defecto 10%
    * @return Código de error
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, float oacc, int velAccParamMode, int overSpeedStrategy = 0, int speedPercent = 10)

Movimiento lineal en el espacio cartesiano (cálculo automático de cinemática inversa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento lineal en el espacio cartesiano (cálculo automático de cinemática inversa)
    * @param [in] desc_pos   Pose cartesiana objetivo
    * @param [in] tool  Número del sistema de coordenadas de herramienta, rango [1~15]
    * @param [in] user  Número del sistema de coordenadas de pieza, rango [1~15]
    * @param [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] blendMode Modo de transición; 0-transición tangente interna; 1-transición por esquina
    * @param [in] epos  Posición del eje extendido, unidad mm
    * @param [in] search  0-sin búsqueda de posición del alambre de soldadura, 1-búsqueda de posición del alambre de soldadura
    * @param [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos  Magnitud del desplazamiento de pose
    * @param [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param [in] overSpeedStrategy  Estrategia de tratamiento de exceso de velocidad, 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, por defecto 0
    * @param [in] speedPercent  Porcentaje de umbral de reducción de velocidad permitido [0-100], por defecto 10%
    * @return  Código de error
    */
    int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int overSpeedStrategy, int speedPercent)

Movimiento lineal en el espacio cartesiano (con el parámetro velAccParamMode de modo de parámetros de velocidad y aceleración)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento lineal en el espacio cartesiano (con el parámetro velAccParamMode de modo de parámetros de velocidad y aceleración)
    * @param  [in] joint_pos  Posición articular objetivo, unidad deg
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número del sistema de coordenadas de herramienta, rango [1~15]
    * @param  [in] user  Número del sistema de coordenadas de pieza, rango [1~15]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] epos  Posición del eje extendido, unidad mm
    * @param  [in] search  0-sin búsqueda de posición del alambre de soldadura, 1-búsqueda de posición del alambre de soldadura
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Magnitud del desplazamiento de pose
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @param  [in] overSpeedStrategy  Estrategia de tratamiento de exceso de velocidad, 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, por defecto 0
    * @param  [in] speedPercent  Porcentaje de umbral de reducción de velocidad permitido [0-100], por defecto 10%
    * @return  Código de error
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimiento lineal en el espacio cartesiano (función sobrecargada 1, añade blendMode)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento lineal en el espacio cartesiano (función sobrecargada 1, añade blendMode)
    * @param  [in] joint_pos  Posición articular objetivo, unidad deg
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número del sistema de coordenadas de herramienta, rango [1~15]
    * @param  [in] user  Número del sistema de coordenadas de pieza, rango [1~15]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] blendMode Modo de transición; 0-transición tangente interna; 1-transición por esquina
    * @param  [in] epos  Posición del eje extendido, unidad mm
    * @param  [in] search  0-sin búsqueda de posición del alambre de soldadura, 1-búsqueda de posición del alambre de soldadura
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Magnitud del desplazamiento de pose
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @param  [in] overSpeedStrategy  Estrategia de tratamiento de exceso de velocidad, 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, por defecto 0
    * @param  [in] speedPercent  Porcentaje de umbral de reducción de velocidad permitido [0-100], por defecto 10%
    * @return  Código de error
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimiento lineal en el espacio cartesiano (función sobrecargada 2, no requiere introducir la posición articular)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento lineal en el espacio cartesiano (función sobrecargada 2, no requiere introducir la posición articular)
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número del sistema de coordenadas de herramienta, rango [1~15]
    * @param  [in] user  Número del sistema de coordenadas de pieza, rango [1~15]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] blendMode Modo de transición; 0-transición tangente interna; 1-transición por esquina
    * @param  [in] epos  Posición del eje extendido, unidad mm
    * @param  [in] search  0-sin búsqueda de posición del alambre de soldadura, 1-búsqueda de posición del alambre de soldadura
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Magnitud del desplazamiento de pose
    * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @param  [in] overSpeedStrategy  Estrategia de tratamiento de exceso de velocidad, 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, por defecto 0
    * @param  [in] speedPercent  Porcentaje de umbral de reducción de velocidad permitido [0-100], por defecto 10%
    * @return  Código de error
    */
    public int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimiento en arco en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento en arco en el espacio cartesiano
    * @param  [in] joint_pos_p  Posición articular del punto de ruta, unidad deg
    * @param  [in] desc_pos_p   Pose cartesiana del punto de ruta
    * @param  [in] ptool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] puser  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_p  Posición del eje extendido, unidad mm
    * @param  [in] poffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_p  Magnitud del desplazamiento de pose
    * @param  [in] joint_pos_t  Posición articular del punto objetivo, unidad deg
    * @param  [in] desc_pos_t   Pose cartesiana del punto objetivo
    * @param  [in] ttool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] tuser  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_t  Posición del eje extendido, unidad mm
    * @param  [in] toffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_t  Magnitud del desplazamiento de pose
    * @param  [in] ovl  Factor de escala de velocidad [0~100]/velocidad física (mm/s)
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] oacc Factor de escala de aceleración [0-100]/aceleración física (mm/s2)
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @return  Código de error
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc,ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p,JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc,ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t,float ovl, float blendR, float oacc, int velAccParamMode)

Movimiento en arco en el espacio cartesiano (cálculo automático de cinemática inversa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento en arco en el espacio cartesiano (cálculo automático de cinemática inversa)
    * @param [in] desc_pos_p   Pose cartesiana del punto de ruta
    * @param [in] ptool  Número del sistema de coordenadas de herramienta, rango [1~15]
    * @param [in] puser  Número del sistema de coordenadas de pieza, rango [1~15]
    * @param [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_p  Posición del eje extendido, unidad mm
    * @param [in] poffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_p  Magnitud del desplazamiento de pose
    * @param [in] desc_pos_t   Pose cartesiana del punto objetivo
    * @param [in] ttool  Número del sistema de coordenadas de herramienta, rango [1~15]
    * @param [in] tuser  Número del sistema de coordenadas de pieza, rango [1~15]
    * @param [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_t  Posición del eje extendido, unidad mm
    * @param [in] toffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_t  Magnitud del desplazamiento de pose
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return  Código de error
    */
    int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config)

Movimiento en arco en el espacio cartesiano (con el parámetro velAccParamMode de modo de parámetros de velocidad y aceleración)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento en arco en el espacio cartesiano (con el parámetro velAccParamMode de modo de parámetros de velocidad y aceleración)
    * @param  [in] joint_pos_p  Posición articular del punto de ruta, unidad deg
    * @param  [in] desc_pos_p   Pose cartesiana del punto de ruta
    * @param  [in] ptool  Número del sistema de coordenadas de herramienta, rango [1~15]
    * @param  [in] puser  Número del sistema de coordenadas de pieza, rango [1~15]
    * @param  [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_p  Posición del eje extendido, unidad mm
    * @param  [in] poffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_p  Magnitud del desplazamiento de pose
    * @param  [in] joint_pos_t  Posición articular del punto objetivo, unidad deg
    * @param  [in] desc_pos_t   Pose cartesiana del punto objetivo
    * @param  [in] ttool  Número del sistema de coordenadas de herramienta, rango [1~15]
    * @param  [in] tuser  Número del sistema de coordenadas de pieza, rango [1~15]
    * @param  [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_t  Posición del eje extendido, unidad mm
    * @param  [in] toffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_t  Magnitud del desplazamiento de pose
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @return  Código de error
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int velAccParamMode)

Movimiento en arco en el espacio cartesiano (función sobrecargada 1, no requiere introducir la posición articular)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento en arco en el espacio cartesiano (función sobrecargada 1, no requiere introducir la posición articular)
    * @param  [in] desc_pos_p   Pose cartesiana del punto de ruta
    * @param  [in] ptool  Número del sistema de coordenadas de herramienta, rango [1~15]
    * @param  [in] puser  Número del sistema de coordenadas de pieza, rango [1~15]
    * @param  [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_p  Posición del eje extendido, unidad mm
    * @param  [in] poffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_p  Magnitud del desplazamiento de pose
    * @param  [in] desc_pos_t   Pose cartesiana del punto objetivo
    * @param  [in] ttool  Número del sistema de coordenadas de herramienta, rango [1~15]
    * @param  [in] tuser  Número del sistema de coordenadas de pieza, rango [1~15]
    * @param  [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_t  Posición del eje extendido, unidad mm
    * @param  [in] toffset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos_t  Magnitud del desplazamiento de pose
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @return  Código de error
    */
    public int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config, int velAccParamMode)

Movimiento punto a punto en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Movimiento punto a punto en el espacio cartesiano 
    * @param [in] desc_pos Pose cartesiana objetivo en el sistema de coordenadas base 
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14] 
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14] 
    * @param [in] vel Porcentaje de velocidad, rango [0~100] 
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible 
    * @param [in] ovl Factor de escala de velocidad, rango [0~100] 
    * @param [in] blendT [-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad ms 
    * @param [in] config Configuración del espacio de articulaciones, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver con referencia a una configuración específica del espacio de articulaciones, por defecto -1 
    * @return Código de error 
    */ 
    int MoveCart(DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendT, int config);

Movimiento de círculo completo en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento de círculo completo en el espacio cartesiano
    * @param  [in] joint_pos_p  Posición articular del punto de ruta 1, unidad deg
    * @param  [in] desc_pos_p   Pose cartesiana del punto de ruta 1
    * @param  [in] ptool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] puser  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_p  Posición del eje extendido, unidad mm
    * @param  [in] joint_pos_t  Posición articular del punto de ruta 2, unidad deg
    * @param  [in] desc_pos_t   Pose cartesiana del punto de ruta 2
    * @param  [in] ttool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] tuser  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_t  Posición del eje extendido, unidad mm
    * @param  [in] ovl  Factor de escala de velocidad [0~100]/velocidad física (mm/s)
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Magnitud del desplazamiento de pose
    * @param  [in] oacc Factor de escala de aceleración [0-100]/aceleración física (mm/s2)
    * @param  [in] blendR -1: bloqueante; 0~1000: radio de suavizado
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @return  Código de error
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc,ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser,float tvel, float tacc, ExaxisPos epos_t, float ovl, int offset_flag,DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Movimiento de círculo completo en el espacio cartesiano (cálculo automático de cinemática inversa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
     * @brief  Movimiento de círculo completo en el espacio cartesiano (cálculo automático de cinemática inversa)
     * @param  [in] desc_pos_p   Pose cartesiana del punto de ruta 1
     * @param  [in] ptool  Número del sistema de coordenadas de herramienta, rango [0~14]
     * @param  [in] puser  Número del sistema de coordenadas de pieza, rango [0~14]
     * @param  [in] pvel  Porcentaje de velocidad, rango [0~100]
     * @param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
     * @param  [in] epos_p  Posición del eje extendido, unidad mm
     * @param  [in] desc_pos_t   Pose cartesiana del punto de ruta 2
     * @param  [in] ttool  Número del sistema de coordenadas de herramienta, rango [0~14]
     * @param  [in] tuser  Número del sistema de coordenadas de pieza, rango [0~14]
     * @param  [in] tvel  Porcentaje de velocidad, rango [0~100]
     * @param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
     * @param  [in] epos_t  Posición del eje extendido, unidad mm
     * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
     * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
     * @param  [in] offset_pos  Magnitud del desplazamiento de pose
     * @param  [in] oacc Porcentaje de aceleración
     * @param  [in] blendR -1: bloqueante; 0~1000: radio de suavizado
     * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
     * @return  Código de error
     */
    int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR,int config)

Movimiento de círculo completo en el espacio cartesiano (con el parámetro velAccParamMode de modo de parámetros de velocidad y aceleración)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    *@brief  Movimiento de círculo completo en el espacio cartesiano (con el parámetro velAccParamMode de modo de parámetros de velocidad y aceleración)
    *@param  [in] joint_pos_p  Posición articular del punto de ruta 1, unidad deg
    *@param  [in] desc_pos_p   Pose cartesiana del punto de ruta 1
    *@param  [in] ptool  Número del sistema de coordenadas de herramienta, rango [1~15]
    *@param  [in] puser  Número del sistema de coordenadas de pieza, rango [1~15]
    *@param  [in] pvel  Porcentaje de velocidad, rango [0~100]
    *@param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    *@param  [in] epos_p  Posición del eje extendido, unidad mm
    *@param  [in] joint_pos_t  Posición articular del punto de ruta 2, unidad deg
    *@param  [in] desc_pos_t   Pose cartesiana del punto de ruta 2
    *@param  [in] ttool  Número del sistema de coordenadas de herramienta, rango [1~15]
    *@param  [in] tuser  Número del sistema de coordenadas de pieza, rango [1~15]
    *@param  [in] tvel  Porcentaje de velocidad, rango [0~100]
    *@param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    *@param  [in] epos_t  Posición del eje extendido, unidad mm
    *@param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    *@param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    *@param  [in] offset_pos  Magnitud del desplazamiento de pose
    *@param  [in] oacc Porcentaje de aceleración
    *@param  [in] blendR -1: bloqueante; 0~1000: radio de suavizado
    *@param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    *@return  Código de error
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Movimiento de círculo completo en el espacio cartesiano (función sobrecargada 1, no requiere introducir la posición articular)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento de círculo completo en el espacio cartesiano (función sobrecargada 1, no requiere introducir la posición articular)
    * @param  [in] desc_pos_p   Pose cartesiana del punto de ruta 1
    * @param  [in] ptool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] puser  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] pvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] pacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_p  Posición del eje extendido, unidad mm
    * @param  [in] desc_pos_t   Pose cartesiana del punto de ruta 2
    * @param  [in] ttool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] tuser  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] tvel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] tacc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos_t  Posición del eje extendido, unidad mm
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Magnitud del desplazamiento de pose
    * @param  [in] oacc Porcentaje de aceleración
    * @param  [in] blendR -1: bloqueante; 0~1000: radio de suavizado
    * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param  [in] velAccParamMode Modo de parámetros de velocidad y aceleración; 0-porcentaje; 1-velocidad física (mm/s) y aceleración (mm/s2)
    * @return  Código de error
    */
    public int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int config, int velAccParamMode)

Ejemplo de código de instrucciones básicas de movimiento del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    public void TestMove()
        int rtn;
        JointPos j1 = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos j2 = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);
        JointPos j3 = new JointPos(-29.777f, -84.536f, 109.275f, -114.075f, -86.655f, 74.257f);
        JointPos j4 = new JointPos(-31.154f, -95.317f, 94.276f, -88.079f, -89.740f, 74.256f);
        DescPose desc_pos1 = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose desc_pos2 = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);
        DescPose desc_pos3 = new DescPose(-487.434f, 154.362f, 308.576f, 176.600f, 0.268f, -14.061f);
        DescPose desc_pos4 = new DescPose(-443.165f, 147.881f, 480.951f, 179.511f, -0.775f, -15.409f);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float oacc = 100.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;
        byte search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, oacc, velAccMode,0,10);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, oacc, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos,j1, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        Console.WriteLine($"MoveCart errcode:{rtn}");
        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,desc_pos4, tool, user, vel, acc, epos, flag, offset_pos,ovl, blendR, -1, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
    }

Movimiento helicoidal en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimiento helicoidal en el espacio cartesiano 
    * @param [in] joint_pos Posición articular objetivo, unidad deg 
    * @param [in] desc_pos Pose cartesiana objetivo 
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14] 
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14] 
    * @param [in] vel Porcentaje de velocidad, rango [0~100] 
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible 
    * @param [in] epos Posición del eje extendido, unidad mm 
    * @param [in] ovl Factor de escala de velocidad, rango [0~100] 
    * @param [in] offset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta 
    * @param [in] offset_pos Magnitud del desplazamiento de pose 
    * @param [in] spiral_param Parámetros de la hélice 
    * @return Código de error 
    */
    int NewSpiral(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, ExaxisPos epos, float ovl, byte offset_flag, DescPose offset_pos, SpiralParam spiral_param); 

Movimiento helicoidal en el espacio cartesiano (cálculo automático de cinemática inversa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Movimiento helicoidal en el espacio cartesiano (cálculo automático de cinemática inversa)
    * @param [in] desc_pos   Pose cartesiana objetivo
    * @param [in] tool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos  Posición del eje extendido, unidad mm
    * @param [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos  Magnitud del desplazamiento de pose
    * @param [in] spiral_param  Parámetros de la hélice
    * @param [in] config  Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return Código de error 
    */
    int NewSpiral(DescPose desc_pos, int tool, int user, double vel, double acc, ExaxisPos epos, double ovl, int offset_flag, DescPose offset_pos, SpiralParam spiral_param,int config)

Ejemplo de código de movimiento helicoidal
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
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
         Console.WriteLine("movej errcode:"+ rtn);

        rtn = robot.NewSpiral(desc_pos, tool, user, vel, acc, epos, ovl, flag, offset_pos2, sp,-1);
        Console.WriteLine("newspiral errcode:"+ rtn);

        return 0;
    }

Inicio del movimiento servo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Inicio del movimiento servo, para usar junto con las instrucciones ServoJ y ServoCart
    * @param[in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @param[in] filtertime Tiempo de filtro, unidad ms, por defecto 0
    * @param[in] gain Array de ganancias del lazo de posición, longitud 6, correspondientes a las ganancias del lazo de posición de las articulaciones J1~J6; si se pasa null se utilizan los valores por defecto { -1.0, -1.0, -1.0, -1.0, -1.0, -1.0 }
    * @return Código de error
    */
    public int ServoMoveStart (int comType = 0, int filtertime = 0, double[] gain = null)

Fin del movimiento servo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Fin del movimiento servo, para usar junto con las instrucciones ServoJ y ServoCart
    * @param[in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return  Código de error
    */
    public int ServoMoveEnd (int comType = 0)

Movimiento en modo servo en el espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento en modo servo en el espacio de articulaciones
    * @param  [in] joint_pos  Posición articular objetivo, unidad deg
    * @param  [in] axisPos  Posición del eje externo, unidad mm
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible, por defecto 0
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100], aún no disponible, por defecto 0
    * @param  [in] cmdT  Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016]
    * @param  [in] filterT Tiempo de filtro, unidad s, aún no disponible, por defecto 0
    * @param  [in] gain  Amplificador proporcional de la posición objetivo, aún no disponible, por defecto 0
    * @param  [in] id ID de la instrucción servoJ, por defecto 0
    * @param  [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return  Código de error
    */
    public int ServoJ(JointPos joint_pos, ExaxisPos axisPos, float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0)

Ejemplo de código SDK de ServoJ, ServoMoveStart y ServoMoveEnd basado en comunicación UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    public void TestServoJUDP()
    {
        // Callback de suscripción
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 300;
        float dt = 0.1f;
        int cmdID = 0;

        while (true)
        {
            JointPos j = new JointPos(0, -90, 90, 0, 0, 0);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(0, -90, 90, 0, 0, 0);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
            int ret = robot.GetActualJointPosDegree(flag, ref j);
            if (ret == 0)
            {
                count = 300;
                cmdID += 1;
                robot.ServoMoveStart(1);

                while (count > 0)
                {
                    robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, 1);
                    j.jPos[0] += dt;
                    j.jPos[1] += dt;
                    j.jPos[3] += dt;
                    j.jPos[4] += dt;
                    j.jPos[5] += dt;
                    epos.ePos[0] += dt;
                    count -= 1;
                    Thread.Sleep(1);
                    robot.GetRobotRealTimeState(ref pkg);
                }
                robot.ServoMoveEnd(1);

                Thread.Sleep(1000);
                count = 300;
                robot.ServoMoveStart(1);
                while (count > 0)
                {
                    robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, 1);
                    j.jPos[0] -= dt;
                    j.jPos[1] -= dt;
                    j.jPos[3] -= dt;
                    j.jPos[4] -= dt;
                    j.jPos[5] -= dt;
                    epos.ePos[0] -= dt;
                    count -= 1;
                    Thread.Sleep(1);
                    robot.GetRobotRealTimeState(ref pkg);
                }
                robot.ServoMoveEnd(1);
            }
            else
            {
                Console.WriteLine($"GetActualJointPosDegree errcode:{ret}");
            }
        }
    }

Ejemplo de código de movimiento en modo servo en el espacio de articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestServoJwithParam()
    {
        // Callback de suscripción: imprime la trama completa de respuesta UDP (trama de protocolo original descifrada)
        int udpRcvCnt = 0;
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            udpRcvCnt++;
            Console.WriteLine($"[UDP reply #{udpRcvCnt}] {DateTime.Now:HH:mm:ss.fff} comType={comType}");
            Console.WriteLine($"  Complete frame: /f/bIII{frameCount}III{frameCmdID}III{contentLen}III{content}III/b/f");
            Console.WriteLine($"  Fields: count={frameCount}, cmdID={frameCmdID}, contentLen={contentLen}, content={content}");
        };

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.010f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 300;
        float dt = 0.1f;
        int cmdID = 0;
        int comtype = 0;

        int filtertime = 0;                     // Tiempo de filtro en ms; 0 significa deshabilitado; ejemplo: 5 ms
        double[] jointGain = { 20.0, 20.0, 20.0, 20.0, 20.0, 20.0 };
        // jointGain: ganancias del lazo de posición para J1-J6; -1 significa usar el valor por defecto; modifique según las ganancias reales

        JointPos j = new JointPos(0, -90, 90, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, -90, 90, 0, 0, 0);
        robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        int ret = robot.GetActualJointPosDegree(flag, ref j);
        if (ret == 0)
        {
            count = 300;
            cmdID += 1;
            // Enviar el tiempo de filtro y las ganancias del lazo de posición de las articulaciones
            robot.ServoMoveStart(comtype, filtertime, jointGain);

            while (count > 0)
            {
                robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, comtype);
                j.jPos[0] += dt;
                j.jPos[2] += dt;
                j.jPos[3] += dt;
                j.jPos[4] += dt;
                j.jPos[5] += dt;
                epos.ePos[0] += dt;
                count -= 1;
                Thread.Sleep(1);
                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"ServoJ command count: {pkg.servoJCmdNum}");
                Console.WriteLine($"ServoJ Count {pkg.servoJCmdNum}; last pos is {pkg.lastServoTarget[0]} {pkg.lastServoTarget[1]} {pkg.lastServoTarget[2]} {pkg.lastServoTarget[3]} {pkg.lastServoTarget[4]} {pkg.lastServoTarget[5]}");
            }
            robot.ServoMoveEnd(comtype);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        }
        else
        {
            Console.WriteLine($"GetActualJointPosDegree errcode:{ret}");
        }
    }

Inicio del control de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Inicio del control de par de las articulaciones
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    public int ServoJTStart (int comType = 0)
    
Movimiento en modo servo en el espacio de articulaciones (admite la entrada de múltiples puntos a la vez)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimiento en modo servo en el espacio de articulaciones (admite la entrada de múltiples puntos a la vez)
    * @param [in] joint_pos Conjunto de posiciones articulares objetivo (admite hasta 10 grupos), unidad deg
    * @param [in] axisPos Posición del eje externo, unidad mm
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible, por defecto 0
    * @param [in] vel Porcentaje de velocidad, rango [0~100], aún no disponible, por defecto 0
    * @param [in] cmdT Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016]
    * @param [in] filterT Tiempo de filtro, unidad s, aún no disponible, por defecto 0
    * @param [in] gain Amplificador proporcional de la posición objetivo, aún no disponible, por defecto 0
    * @param [out] servoJCmdCount Contador de puntos de la instrucción ServoJ [0-10000]
    * @param [in] id ID de la instrucción servoJ, por defecto 0
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    public int ServoJ(List<JointPos> joint_pos, ExaxisPos axisPos, float acc, float vel, float cmdT, float filterT, float gain, ref int servoJCmdCount, int id = 0, int comType = 0)
    
Ejemplo de código de movimiento en modo servo en el espacio de articulaciones (admite la entrada de múltiples puntos a la vez)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestServoJPath()
    {
        // Lee el archivo de ruta ServoJ, tomando las columnas 2~7 de cada línea como las 6 posiciones articulares
        string filePath = "D://zUP/ServoJPath.txt";
        List<JointPos> allJointData = new List<JointPos>();
        using (StreamReader reader = new StreamReader(filePath))
        {
            string line;
            while ((line = reader.ReadLine()) != null)
            {
                string[] cols = line.Split(new[] { ' ', '\t' }, StringSplitOptions.RemoveEmptyEntries);
                if (cols.Length < 7)
                    continue;
                JointPos pose = new JointPos(0, 0, 0, 0, 0, 0);
                pose.jPos[0] = double.Parse(cols[1]);
                pose.jPos[1] = double.Parse(cols[2]);
                pose.jPos[2] = double.Parse(cols[3]);
                pose.jPos[3] = double.Parse(cols[4]);
                pose.jPos[4] = double.Parse(cols[5]);
                pose.jPos[5] = double.Parse(cols[6]);
                allJointData.Add(pose);
            }
        }
        Console.WriteLine($"Total {allJointData.Count} joint position sets read");
        if (allJointData.Count == 0)
            return;

        // Construir una ruta de ida y vuelta: orden directo + orden inverso
        List<JointPos> backForthPath = new List<JointPos>(allJointData);
        for (int i = allJointData.Count - 2; i >= 0; i--)
        {
            backForthPath.Add(allJointData[i]);
        }

        ExaxisPos epos = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offsetPos = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        robot.MoveJ(allJointData[0], 0, 0, 100, 100, 100, epos, -1, 0, offsetPos);

        robot.Sleep(1000);

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        while (true)
        {
            robot.ResetAllError();
            robot.MoveJ(allJointData[0], 0, 0, 100, 100, 100, epos, -1, 0, offsetPos);
            int moveCount = 0;
            while (moveCount < backForthPath.Count - 10)
            {
                robot.GetRobotRealTimeState(ref pkg);

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

                List<JointPos> jointPos = new List<JointPos>();
                for (int j = 0; j < singleServoJCount; j++)
                {
                    jointPos.Add(backForthPath[moveCount]);
                    moveCount++;
                }

                Console.WriteLine($"Sending {singleServoJCount} waypoints, moveCount={moveCount}");

                ExaxisPos axisPos = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
                int servoJCmdCount = 0;
                int rtn = robot.ServoJ(jointPos, axisPos, 100.0f, 100.0f, 0.008f, 0.008f, 1.0f, ref servoJCmdCount);
                if (rtn != 0)
                {
                    Console.WriteLine($"ServoJ failed: {rtn}");
                    break;
                }
            }
            robot.Sleep(4000);
        }
    }

Control de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Control de par de las articulaciones
    * @param [in] torque Par de las articulaciones j1~j6, unidad Nm
    * @param [in] interval Período de instrucción, unidad s, rango [0.001~0.008]
    * @param [in] checkFlag Estrategia de detección 0-sin limitación; 1-limitar potencia; 2-limitar velocidad; 3-limitar potencia y velocidad simultáneamente
    * @param [in] jPowerLimit Límite de potencia máxima de las articulaciones (W)
    * @param [in] jVelLimit Velocidad máxima de las articulaciones (°/s)
    * @param [in]  comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    public int ServoJT(double[] torque, double interval, int checkFlag, double[] jPowerLimit, double[] jVelLimit, int comType = 0)

Fin del control de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Fin del control de par de las articulaciones
    * @param[in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return  Código de error
    */
    public int ServoJTEnd (int comType = 0)

Ejemplo de código SDK de ServoJT, ServoJTStart y ServoJTEnd basado en comunicación UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJTWithSafetyUDP()
    {
        // Callback de suscripción
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[UDP响应] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };
        while (true)
        {
            robot.ResetAllError();
            Thread.Sleep(500);

            JointPos j = new JointPos(7.053, -89.699, 156.141, -72.751, 7.829, 1.889);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(-151.288, -321.186, 221.989, 89.140, 4.361, -0.795);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
            robot.GetJointTorques(1, torques);

            robot.ServoJTStart(1);
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);

            int checkFlag = 0;
            double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double[] jVelLimit = new double[6] { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {

                torques[0] = 0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 1);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] > 30)
                {
                    break;
                }
            }

            while (true)
            {

                torques[0] = -0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 1);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoJTEnd(1);
        }
        return 0;
    }

Ejemplo de código de control de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button27_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        double[] torques = { 0, 0, 0, 0, 0, 0 };
        robot.GetJointTorques(1, torques);

        int count = 100;
        robot.ServoJTStart();
        int error = 0;
        while (count > 0)
        {
            error = robot.ServoJT(torques, 0.001f);
            count--;
            Thread.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);
    }

Ejemplo de código de control de par de las articulaciones con protección contra exceso de velocidad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJTWithSafety()
    {
        while (true)
        {
            robot.ResetAllError();
            Thread.Sleep(500);

            JointPos j = new JointPos(7.053, -89.699, 156.141, -72.751, 7.829, 1.889);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(-151.288, -321.186, 221.989, 89.140, 4.361, -0.795);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
            robot.GetJointTorques(1, torques);

            robot.ServoJTStart(0);
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);

            int checkFlag = 0;
            double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double[] jVelLimit = new double[6] { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {

                torques[0] = 0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 0);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] > 30)
                {
                    break;
                }
            }

            while (true)
            {

                torques[0] = -0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 0);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoJTEnd(0);
        }
    }

Movimiento en modo servo en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimiento en modo servo en el espacio cartesiano
    * @param [in] mode 0-movimiento absoluto (sistema de coordenadas base), 1-movimiento incremental (sistema de coordenadas base), 2-movimiento incremental (sistema de coordenadas de herramienta)
    * @param [in] desc_pos Pose cartesiana objetivo o incremento de pose
    * @param [in] exaxis Posición del eje extendido
    * @param [in] pos_gain Coeficiente proporcional del incremento de pose, solo efectivo en movimiento incremental, rango [0~1]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible, por defecto 0
    * @param [in] vel Porcentaje de velocidad, rango [0~100], aún no disponible, por defecto 0
    * @param [in] cmdT Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.016]
    * @param [in] filterT Tiempo de filtro, unidad s, aún no disponible, por defecto 0
    * @param [in] gain Amplificador proporcional de la posición objetivo, aún no disponible, por defecto 0
    * @return Código de error
    */
    public int ServoCart(int mode, DescPose desc_pose, ExaxisPos exaxis, double[] pos_gain, double acc, double vel, double cmdT, double filterT, double gain);

Ejemplo de código de movimiento en modo servo en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestServoCart()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        int rtn;
        DescPose desc_pos_dt = new DescPose(83.00800f, 50.525000f, 29.246f, 179.629f, -7.138f, -166.975f);
        ExaxisPos exaxis = new ExaxisPos(100.0f, 0.0f, 0.0f, 0.0f);
        double[] pos_gain = { 0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        int mode = 0;
        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.001f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 5000;

        robot.SetSpeed(20);

        while (count > 0)
        {
            rtn = robot.ServoCart(mode, desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
            Console.WriteLine($"ServoCart rtn is {rtn}");
            count -= 1;
            desc_pos_dt.tran.x += 0.01f;
            exaxis.ePos[0] += 0.01f;
        }
    }

Ejemplo de código de ServoCart con inicio de movimiento servo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestServoCartwithParam()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        int rtn;
        DescPose desc_pos_dt = new DescPose(-396, -202, 475, 90, 2, 0);

        ExaxisPos exaxis = new ExaxisPos(0.0f, 0.0f, 0.0f, 0.0f);
        double[] pos_gain = { 22.0, 22.0, 22.0, 22.0, 22.0, 22.0 };  // Parámetros de ganancia de ServoCart
        int mode = 0;
        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        int count = 5000;

        // ===== Parámetros de ServoMoveStart =====
        int comType = 0;                        // 0-xmlrpc; 1-UDP(20007)
        int filtertime = 0;                     // Tiempo de filtro en ms; 0 significa deshabilitado; ejemplo: 5 ms
        double[] jointGain = { 22.0, 22.0, 22.0, 22.0, 22.0, 22.0 };
        // jointGain: ganancias del lazo de posición para J1-J6; -1 significa usar el valor por defecto; modifique según las ganancias reales, por ejemplo { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 }

        robot.SetSpeed(20);

        JointPos j = new JointPos(0, -90, 90, 0, 1, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(2000);
        robot.GetActualTCPPose(0, ref desc_pos_dt);

        // Iniciar el movimiento servo: enviar el tiempo de filtro y las ganancias del lazo de posición de las articulaciones
        rtn = robot.ServoMoveStart(comType, filtertime, jointGain);
        Console.WriteLine($"ServoMoveStart rtn is {rtn}");

        while (count > 0)
        {
            rtn = robot.ServoCart(mode, desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
            Console.WriteLine($"ServoCart rtn is {rtn}");
            count -= 1;
            desc_pos_dt.tran.x += 0.05f;
            //exaxis.ePos[0] += 0.01f;
        }

        // Finalizar el movimiento servo
        rtn = robot.ServoMoveEnd(comType);
        Console.WriteLine($"ServoMoveEnd rtn is {rtn}");
    }

Inicio del movimiento de spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inicio del movimiento de spline
    * @return  Código de error
    */
    int SplineStart();

Spline PTP (movimiento de spline en el espacio de articulaciones)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento de spline en el espacio de articulaciones
    * @param  [in] joint_pos  Posición articular objetivo, unidad deg
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] user  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]   
    * @return  Código de error
    */
    int SplinePTP(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl);

Movimiento de spline en el espacio de articulaciones (cálculo automático de cinemática directa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento de spline en el espacio de articulaciones (cálculo automático de cinemática directa)
    * @param  [in] joint_pos  Posición articular objetivo, unidad deg
    * @param  [in] tool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] user  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @return  Código de error
    */
    int SplinePTP(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl)

Fin del movimiento de spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Fin del movimiento de spline
    * @return  Código de error
    */
    int SplineEnd(); 

Ejemplo de código de movimiento de spline
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnSplineMove_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3 = new JointPos(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
        JointPos j4 = new JointPos(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
        DescPose desc_pos4 = new DescPose(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        int err = -1;
        err = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:  {err}");

        robot.SplineStart();
        robot.SplinePTP(j1, desc_pos1, tool, user, vel, acc, ovl);
        robot.SplinePTP(j2, desc_pos2, tool, user, vel, acc, ovl);
        robot.SplinePTP(j3, desc_pos3, tool, user, vel, acc, ovl);
        robot.SplinePTP(j4, desc_pos4, tool, user, vel, acc, ovl);
        robot.SplineEnd();
    }

Inicio del nuevo movimiento de spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Inicio del nuevo movimiento de spline 
    * @param [in] type  0-transición por arco, 1-los puntos dados son puntos de ruta
    * @param [in] averageTime  Tiempo medio global de enlace (ms) (10 ~  ), por defecto 2000
    * @return Código de error 
    */ 
    int NewSplineStart(int type, int averageTime=2000);
    
Punto de instrucción del nuevo spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Añadir un punto de instrucción de movimiento de spline 
    * @param [in] joint_pos Posición articular objetivo, unidad deg 
    * @param [in] desc_pos Pose cartesiana objetivo 
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14] 
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14] 
    * @param [in] vel Porcentaje de velocidad, rango [0~100] 
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible 
    * @param [in] ovl Factor de escala de velocidad, rango [0~100] 
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] lastFlag  Si es el último punto, 0-no, 1-sí
    * @return Código de error 
    */ 
    int NewSplinePoint(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag);

Punto de instrucción del nuevo spline (cálculo automático de cinemática inversa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Punto de instrucción del nuevo spline (cálculo automático de cinemática inversa)
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] user  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param  [in] lastFlag Si es el último punto, 0-no, 1-sí
    * @param  [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return  Código de error
    */
    int NewSplinePoint(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int lastFlag,int config)

Fin del nuevo movimiento de spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Fin del nuevo movimiento de spline 
    * @return Código de error 
    */ 
    int NewSplineEnd();
    
Ejemplo de código del nuevo movimiento de spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnNewSpline_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3 = new JointPos(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
        JointPos j4 = new JointPos(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
        JointPos j5 = new JointPos(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
        DescPose desc_pos4 = new DescPose(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
        DescPose desc_pos5 = new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        int err = -1;
        err = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:  {err}");

        robot.NewSplineStart(1, 2000);
        robot.NewSplinePoint(j1, desc_pos1, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j2, desc_pos2, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j3, desc_pos3, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j4, desc_pos4, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j5, desc_pos5, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplineEnd();
    }

Terminar el movimiento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Terminar el movimiento
    * @return  Código de error
    */
    int StopMotion();

Pausar el movimiento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
    
    /** 
      * @brief Pausar el movimiento 
      * @return Código de error 
    */  
    int PauseMotion();

Reanudar el movimiento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Reanudar el movimiento 
    * @return Código de error 
    */ 
    int ResumeMotion();

Ejemplo de código de pausa, reanudación y parada del movimiento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnMotionPause_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j5 = new JointPos(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos5 = new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        rtn = robot.MoveJ(j5, desc_pos5, tool, user, vel, acc, ovl, epos, 1, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PauseMotion();

        Thread.Sleep(1000);
        robot.ResumeMotion();

        Thread.Sleep(1000);
        robot.StopMotion();

        Thread.Sleep(1000);

    }

Inicio del desplazamiento global de puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inicio del desplazamiento global de puntos
    * @param  [in]  flag  0-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Magnitud del desplazamiento de pose
    * @return  Código de error
    */
    int PointsOffsetEnable(int flag, DescPose offset_pos); 


Fin del desplazamiento global de puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Fin del desplazamiento global de puntos
    * @return  Código de error
    */
    int PointsOffsetDisable(); 

Ejemplo de código de desplazamiento de puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnPointOffect_Click(object sender, EventArgs e)
    {
        JointPos j1, j2;
        DescPose desc_pos1, desc_pos2, offset_pos, offset_pos1;
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);

        j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        offset_pos1 = new DescPose(50.0, 50.0, 50.0, 5.0, 5.0, 5.0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;
        int type = 0;

        robot.SetSpeed(20);

        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PointsOffsetEnable(type, offset_pos1);
        Thread.Sleep(1000);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PointsOffsetDisable();
    }

Inicio del fly-by del AO del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: c#
    :linenos:

    /**
    * @brief Inicio del fly-by del AO del armario de control
    * @param [in] AONum Número de AO del armario de control
    * @param [in] maxTCPSpeed Valor de velocidad TCP máxima [1-5000mm/s], por defecto 1000
    * @param [in] maxAOPercent Porcentaje de AO correspondiente al valor de velocidad TCP máxima, por defecto 100%
    * @param [in] zeroZoneCmp Valor de compensación de zona muerta en porcentaje de AO, entero, por defecto 20%, rango [0-100]
    * @return Código de error
    */
    int MoveAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Parada del fly-by del AO del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7
   
.. code-block:: c#
    :linenos:

    /**
    * @brief Parada del fly-by del AO del armario de control
    * @return Código de error
    */
    int MoveAOStop();
    
Inicio del fly-by del AO del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7
   
.. code-block:: c#
    :linenos:

    /**
    * @brief Inicio del fly-by del AO del extremo
    * @param [in] AONum Número de AO del extremo
    * @param [in] maxTCPSpeed Valor de velocidad TCP máxima [1-5000mm/s], por defecto 1000
    * @param [in] maxAOPercent Porcentaje de AO correspondiente al valor de velocidad TCP máxima, por defecto 100%
    * @param [in] zeroZoneCmp Valor de compensación de zona muerta en porcentaje de AO, entero, por defecto 20%, rango [0-100]
    * @return Código de error
    */
    int MoveToolAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);
    
Parada del fly-by del AO del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7
   
.. code-block:: c#
    :linenos:

    /**
    * @brief Parada del fly-by del AO del extremo
    * @return Código de error
    */
    int MoveToolAOStop();

Ejemplo de código de fly-by del AO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnMoveAO_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;
        byte search = 0;

        robot.SetSpeed(5);

        robot.MoveAOStart(0,100,100,20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveAOStop();

        robot.MoveToolAOStart(0, 100, 100, 20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveToolAOStop();
    }

Inicio del filtro FIR del movimiento PTP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:


    /**
    * @brief Inicio del filtro FIR del movimiento PTP
    * @param [in] maxAcc Aceleración máxima extrema (deg/s2)
    * @param [in] maxJek Valor extremo unificado de jerk de las articulaciones (deg/s3)
    * @return Código de error
    */
    int PtpFIRPlanningStart(double maxAcc, double maxJek=1000);

Desactivar el filtro FIR del movimiento PTP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Desactivar el filtro FIR del movimiento PTP
    * @return Código de error
    */
    int PtpFIRPlanningEnd();

Inicio del filtro FIR de los movimientos LIN y ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Inicio del filtro FIR de los movimientos LIN y ARC
    * @param [in] maxAccLin Aceleración lineal máxima (mm/s2)
    * @param [in] maxAccDeg Aceleración angular máxima (deg/s2)
    * @param [in] maxJerkLin Jerk lineal máximo (mm/s3)
    * @param [in] maxJerkDeg Jerk angular máximo (deg/s3)
    * @return Código de error
    */
    int LinArcFIRPlanningStart(double maxAccLin, double maxAccDeg, double maxJerkLin, double maxJerkDeg);

Desactivar el filtro FIR de los movimientos LIN y ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Desactivar el filtro FIR de los movimientos LIN y ARC
    * @return Código de error
    */
    int LinArcFIRPlanningEnd();

Ejemplo de código del filtro FIR
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void button69_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos midjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);
        JointPos endjointPos = new JointPos(-29.777f, -84.536f, 109.275f, -114.075f, -86.655f, 74.257f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose middescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);
        DescPose enddescPose = new DescPose(-487.434f, 154.362f, 308.576f, 176.600f, 0.268f, -14.061f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        rtn = robot.PtpFIRPlanningStart(1000, 1000);
        Console.WriteLine("PtpFIRPlanningStart rtn is " + rtn);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.PtpFIRPlanningEnd();
        Console.WriteLine("PtpFIRPlanningEnd rtn is " + rtn);

        robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000);
        Console.WriteLine("LinArcFIRPlanningStart rtn is " + rtn);
        robot.MoveL(startjointPos, startdescPose, 0, 0, 20, 100, 100, -1,0, exaxisPos, 0, 0, offdese, 1, 50);
        robot.MoveC(midjointPos, middescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, endjointPos, enddescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, 100, -1, 100, 0);
        robot.LinArcFIRPlanningEnd();
        Console.WriteLine("LinArcFIRPlanningEnd rtn is " + rtn);
    }

Activación del suavizado de aceleración
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Activación del suavizado de aceleración
    * @param  [in] saveFlag Si se guarda tras el apagado
    * @return  Código de error
    */
    int AccSmoothStart(bool saveFlag);

Desactivación del suavizado de aceleración
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Desactivación del suavizado de aceleración
    * @param  [in] saveFlag Si se guarda tras el apagado
    * @return  Código de error
    */
    int AccSmoothEnd(bool saveFlag);

Ejemplo de código
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button1_Click(object sender, EventArgs e)
    {

        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.AccSmoothStart(false);
        Console.WriteLine("AccSmoothStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.AccSmoothEnd(false);
        Console.WriteLine("AccSmoothEnd rtn is " + rtn);
    }

Activación de la velocidad de orientación especificada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Activación de la velocidad de orientación especificada
    * @param [in] ratio Porcentaje de velocidad de orientación [0-300]
    * @return  Código de error
    */
    int AngularSpeedStart(int ratio);

Desactivación de la velocidad de orientación especificada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
   
    /**
    * @brief Desactivación de la velocidad de orientación especificada
    * @return  Código de error
    */
    int AngularSpeedEnd();

Ejemplo de código de velocidad de orientación especificada del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button71_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.AngularSpeedStart(50);
        Console.WriteLine("AngularSpeedStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.AngularSpeedEnd();
        Console.WriteLine("AngularSpeedEnd rtn is " + rtn);
    }

Inicio de la protección de posición singular
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Inicio de la protección de posición singular
    * @param [in] protectMode Modo de protección de singularidad, 0: modo de articulaciones; 1-modo cartesiano
    * @param [in] minShoulderPos Rango de ajuste de singularidad de hombro (mm), por defecto 100
    * @param [in] minElbowPos Rango de ajuste de singularidad de codo (mm), por defecto 50
    * @param [in] minWristPos Rango de ajuste de singularidad de muñeca (°), por defecto 10
    * @return Código de error
    */
    int SingularAvoidStart(int protectMode, double minShoulderPos, double minElbowPos, double minWristPos);

Detención de la protección de posición singular
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Detención de la protección de posición singular
    * @return Código de error
    */
    int SingularAvoidEnd();

Ejemplo de código
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9
    
.. code-block:: c#
    :linenos:

    private void btnTestSingularAvoidEArc_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        rtn = robot.SingularAvoidStart(2, 10, 5, 5);
        Console.WriteLine("SingularAvoidStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.SingularAvoidEnd();
        Console.WriteLine("SingularAvoidEnd rtn is " + rtn);
    }

Disparo de la parada de seguridad
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Señal de disparo de la parada de seguridad
    * @return Código de error
    */
    int GetSafetyCode();

Vaciar la cola de instrucciones de movimiento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Vaciar la cola de instrucciones de movimiento
    * @return Código de error
    */
    public int MotionQueueClear();

Moverse al punto inicial de la línea de intersección
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Moverse al punto inicial de la línea de intersección
    * @param [in] mainPoint Poses cartesianas de los 6 puntos de enseñanza del tubo principal
    * @param [in] mainExaxisPos Posiciones del eje extendido de los 6 puntos de enseñanza del tubo principal
    * @param [in] piecePoint Poses cartesianas de los 6 puntos de enseñanza del tubo auxiliar
    * @param [in] pieceExaxisPos Posiciones del eje extendido de los 6 puntos de enseñanza del tubo de unión
    * @param [in] extAxisFlag Si se habilita el eje extendido; 0-no habilitar; 1-habilitar
    * @param [in] exaxisPos Posición del eje extendido del punto inicial
    * @param [in] tool Número del sistema de coordenadas de herramienta
    * @param [in] wobj Número del sistema de coordenadas de pieza
    * @param [in] vel Porcentaje de velocidad
    * @param [in] acc Porcentaje de aceleración
    * @param [in] ovl Factor de escala de velocidad
    * @param [in] oacc Factor de escala de aceleración
    * @param [in] moveType Tipo de movimiento; 0-PTP; 1-LIN
    * @param [in] moveDirection Dirección de movimiento; 0-horario; 1-antihorario
    * @param [in] offset Magnitud del desplazamiento
    * @return Código de error
    */
    public int MoveToIntersectLineStart(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveType, int moveDirection, DescPose offset);
            
Movimiento de línea de intersección
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimiento de línea de intersección
    * @param [in] mainPoint Poses cartesianas de los 6 puntos de enseñanza del tubo principal
    * @param [in] mainExaxisPos Posiciones del eje extendido de los 6 puntos de enseñanza del tubo principal
    * @param [in] piecePoint Poses cartesianas de los 6 puntos de enseñanza del tubo auxiliar
    * @param [in] pieceExaxisPos Posiciones del eje extendido de los 6 puntos de enseñanza del tubo de unión
    * @param [in] extAxisFlag Si se habilita el eje extendido; 0-no habilitar; 1-habilitar
    * @param [in] exaxisPos Posición del eje extendido del punto inicial
    * @param [in] tool Número del sistema de coordenadas de herramienta
    * @param [in] wobj Número del sistema de coordenadas de pieza
    * @param [in] vel Porcentaje de velocidad
    * @param [in] acc Porcentaje de aceleración
    * @param [in] ovl Factor de escala de velocidad
    * @param [in] oacc Factor de escala de aceleración
    * @param [in] moveDirection Dirección de movimiento; 0-horario; 1-antihorario
    * @param [in] offset Magnitud del desplazamiento
    * @return Código de error
    */
    public int MoveIntersectLine(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos[] exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveDirection, DescPose offset);
                
Ejemplo de código de movimiento de línea de intersección del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void TestIntersectLineMove()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(3);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return ;
        }
        robot.SetReConnectParam(true, 30000, 500);
        DescPose mainPoint[6] = {};
        DescPose piecePoint[6] = {};
        ExaxisPos mainExaxisPos[6] = {};
        ExaxisPos pieceExaxisPos[6] = {};
        int extAxisFlag = 1;
        ExaxisPos exaxisPos[4] = {};
        DescPose offset = { 0.0, 2.0 ,30.0, -2.0, 0.0, 0.0 };
        mainPoint[0] = {490.004, -383.194, 402.735, -9.332, -1.528, 69.594};
        mainPoint[1] = {444.950, -407.117, 389.011, -5.546, -2.196, 65.279};
        mainPoint[2] = {445.168, -463.605, 355.759, -1.544, -10.886, 57.104};
        mainPoint[3] = {507.529, -485.385, 343.013, -0.786, -4.834, 61.799};
        mainPoint[4] = {554.390, -442.647, 367.701, -4.761, -10.181, 64.925};
        mainPoint[5] = {532.552, -394.003, 396.467, -13.732, -13.592, 67.411};
        mainExaxisPos[0] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[1] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[2] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[3] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[4] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[5] = { -29.996, 0.000, 0.000, 0.000 };
        piecePoint[0] = { 505.571, -192.408, 316.759, 38.098, 37.051, 139.447 };
        piecePoint[1] = {533.837, -201.558, 332.340, 34.644, 42.339, 137.748};
        piecePoint[2] = {530.386, -225.085, 373.808, 35.431, 45.111, 137.560};
        piecePoint[3] = {485.646, -229.195, 383.778, 33.870, 45.173, 137.064};
        piecePoint[4] = {460.551, -212.161, 354.256, 28.856, 45.602, 135.930};
        piecePoint[5] = {474.217, -197.124, 324.611, 42.469, 41.133, 148.167};
        pieceExaxisPos[0] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[1] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[2] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[3] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[4] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[5] = { -29.996, -0.000, 0.000, 0.000 };
        exaxisPos[0] = {-29.996, -0.000, 0.000, 0.000};
        exaxisPos[1] = {-44.994, 90.000, 0.000, 0.000};
        exaxisPos[2] = {-59.992, 0.002, 0.000, 0.000};
        exaxisPos[3] = {-44.994, -89.997, 0.000, 0.000};
        int tool = 2;
        int wobj = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 12.0;
        double oacc = 12.0; 
        int moveType = 1;
        int moveDirection = 1;
        rtn = robot.MoveToIntersectLineStart(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos[0], tool, wobj, vel, acc, ovl, oacc, moveType, moveDirection, offset);
        printf("MoveToIntersectLineStart rtn is %d\n", rtn);
        rtn = robot.MoveIntersectLine(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos, tool, wobj, vel, acc, 5.0, 5.0, moveDirection, offset);
        printf("MoveIntersectLine rtn is %d\n", rtn);
        robot.CloseRPC();
        return ;
    }

Movimiento en vacío en el lugar
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimiento en vacío en el lugar
    * @return Código de error
    */
    public int MoveStationary()

Ejemplo de código de movimiento en vacío en el lugar
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void LaserSensorRecordandReplay()
    {
        int rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 1, 10, 100);
        Console.WriteLine($"LaserSensorRecordandReplay rtn is {rtn}");
        rtn = robot.MoveStationary();
        Console.WriteLine($"MoveStationary rtn is {rtn}");
        rtn = robot.LaserSensorRecord1(0, 10);
        Console.WriteLine($"LaserSensorRecord1 rtn is {rtn}"); 
    }

Inicio de la oscilación en punto fijo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Inicio de la oscilación en punto fijo
    * @param [in] weaveNum Número de oscilación [0-7]
    * @param [in] mode 0-sistema de coordenadas de herramienta; 1-punto de referencia
    * @param [in] refPoint Coordenadas cartesianas del punto de referencia [x,y,z,a,b,c]
    * @param [in] weaveTime Tiempo de oscilación [s]
    * @return Código de error
    */
    public int OriginPointWeaveStart(int weaveNum, int mode, DescPose refPoint, double weaveTime);
    
Fin de la oscilación en punto fijo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Fin de la oscilación en punto fijo
    * @return Código de error
    */
    public int OriginPointWeaveEnd();
        
Ejemplo de código SDK de oscilación en punto fijo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void TestOriginPointWeave()
    {
        // Crear objeto de posición articular
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        // Coordenadas del punto de referencia
        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);

        //// Primer movimiento
        robot.MoveJ(j, 1, 0, 100, 100, 100, epos, -1, 0, offset_pos);

        // Iniciar la oscilación en punto fijo (modo 0)
        robot.OriginPointWeaveStart(0, 0, refPoint, 3);
        robot.MoveStationary();   // Ejecutar movimiento fijo (se asume que el método existe)
        robot.OriginPointWeaveEnd();

        Thread.Sleep(2000);         // Esperar 2 segundos

        // Segundo movimiento
        robot.MoveJ(j, 1, 0, 100, 100, 100, epos, -1, 0, offset_pos);

        // Iniciar la oscilación en punto fijo (modo 1)
        robot.OriginPointWeaveStart(0, 1, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();
    }
        
Ejemplo de código SDK de oscilación en punto fijo (incluye láser y eje extendido)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void TestOriginPointWeave2()
    {
        // Crear objeto de posición articular
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos1 = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos2 = new ExaxisPos(5, 0.000, 0.000, 0.000);

        // Coordenadas del punto de referencia
        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);

        int rtn = 0;
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);

        // Cargar el controlador UDP
        robot.ExtDevLoadUDPDriver();

        // Establecer el tiempo de finalización del comando del eje externo
        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        Console.WriteLine("SetExAxisCmdDoneTime rtn is " + rtn);

        // Habilitar los ejes externos 1 y 2
        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        // Establecer el retorno a cero del eje externo
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.LaserTrackingLaserOnOff(1);


        //// 1---sin eje extendido
        robot.LaserTrackingTrackOnOff(1, 4);
        robot.Sleep(200);
        // Iniciar la oscilación en punto fijo
        robot.OriginPointWeaveStart(0, 0, refPoint, 10);
        robot.MoveStationary();   // Ejecutar movimiento fijo
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);

        Thread.Sleep(2000);         // Esperar 2 segundos

        //// 2----con eje extendido
        robot.ExtAxisMove(epos1, 100, -1);
        robot.LaserTrackingTrackOnOff(1, 4);
        // Iniciar la oscilación en punto fijo
        robot.OriginPointWeaveStart(0, 0, refPoint, 20);
        robot.ExtAxisMove(epos2, 100, -1);
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);
    }
        
Movimiento en modo servo de velocidad en el espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimiento en modo servo de velocidad en el espacio de articulaciones
    * @param  [in] joint_pos  Velocidades articulares objetivo de las 6 articulaciones, unidad deg/s
    * @param  [in] axisPos  Velocidades de los 4 ejes externos, unidad deg/s
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible, por defecto 0
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100], aún no disponible, por defecto 0
    * @param  [in] cmdT  Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016]
    * @param  [in] filterT Tiempo de filtro, unidad s, aún no disponible, por defecto 0
    * @param  [in] gain  Amplificador proporcional de la posición objetivo, aún no disponible, por defecto 0
    * @param  [in] id ID de la instrucción servoJ, por defecto 0
    * @param[in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return  Código de error
    */
    public int ServoJV(double[] joint_vel, double[] exis_vel, float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0)

Ejemplo de código de movimiento en modo servo de velocidad en el espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJVtest()
    {
        double[] joint_vel = new double[6] { 10, 0, 0, 0, 0, 0 };
        double[] exis_vel = new double[4] { 0, 0, 0, 0 };
        float acc = 0.0f; 
        float vel = 0.0f;
        float cmdT = 0.01f; 
        float filterT = 0.0f; 
        float gain = 0.0f;
        int cnt = 0;
        while (cnt < 200)
        {
            int error = robot.ServoJV(joint_vel, exis_vel, acc, vel, cmdT, filterT, gain);
            Console.WriteLine($"ServoJV rtn is {error}");
            cnt++;
        }
        return 0;
    }

Inicio del control MIT de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Inicio del control MIT de las articulaciones
    * @param [in]  comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return  Código de error
    */
    public int ServoMITStart(int comType = 0)

Fin del control MIT de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Fin del control MIT de las articulaciones
    * @param [in]  comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return  Código de error
    */
    public int ServoMITEnd(int comType = 0)

Control MIT de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Control MIT de las articulaciones
    * @param [in] posGain Ganancia de posición de las articulaciones j1~j6
    * @param [in] desPos Posición deseada de las articulaciones j1~j6, unidad: deg
    * @param [in] velGain Ganancia de velocidad de las articulaciones j1~j6
    * @param [in] desVel Velocidad deseada de las articulaciones j1~j6, unidad: deg/s
    * @param [in] torque_ff Par de prealimentación de las articulaciones j1~j6, unidad: Nm
    * @param [in] interval Período de instrucción, unidad s, rango [0.001~0.008]
    * @param [in]  comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    public int ServoMIT(double[] posGain, double[] desPos, double[] velGain, double[] desVel, double[] torque_ff, double interval, int comType = 0)

Ejemplo de código de movimiento de control MIT de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoMITtest()
    {
        // Callback de suscripción
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[UDP响应] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };
        while (true)
        {
            robot.ResetAllError();
            Thread.Sleep(500);

            double[] posGain = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] desPos = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] velGain = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] desVel = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
            robot.GetJointTorques(1, torques);
            Console.WriteLine($"111111");
            //robot.ServoMITEnd(0);
            robot.ServoMITStart(0);
            Console.WriteLine($"ServoMITStart");
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);
            Console.WriteLine($"DragTeachSwitch");
            double intev = 0.008;
            double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double[] jVelLimit = new double[6] { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {

                torques[5] = 0.03;
                Console.WriteLine($"ServoMIT call ");
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                Console.WriteLine($"ServoMIT111111 rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                //Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                Console.WriteLine($"pkg.jt_cur_pos[5]:{pkg.jt_cur_pos[5]}");
                if (pkg.jt_cur_pos[5] > 30)
                {
                    break;
                }
            }

            while (true)
            {

                torques[5] = -0.03;
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                Console.WriteLine($"ServoJT222222 rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                //Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                Console.WriteLine($"pkg.jt_cur_pos[5]:{pkg.jt_cur_pos[5]}");
                if (pkg.jt_cur_pos[5] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoMITEnd(0);
        }
        return 0;
    }

Inicio de la conversión de puntos del sistema de coordenadas de pieza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inicio de la conversión de puntos del sistema de coordenadas de pieza
    * @param  [in] workpieceID Número de pieza [0-14]
    * @return  Código de error, devuelve 0 en caso de éxito
    */
    public int WorkPieceTrsfStart(int workpieceID)
    
Fin de la conversión de puntos del sistema de coordenadas de pieza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Fin de la conversión de puntos del sistema de coordenadas de pieza
    * @return  Código de error, devuelve 0 en caso de éxito
    */
    public int WorkPieceTrsfEnd()
        
Ejemplo de código de conversión de puntos del sistema de coordenadas de pieza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int TestWorkPieceTrsf()
    {

        // ---- Definición de puntos ----
        JointPos j1 = new JointPos(-11.188, -64.165, -107.299, -76.706, 89.590, 92.983);
        DescPose d1 = new DescPose(225.986, 190.694, 394.238, -6.230, -23.797, -98.972);
        JointPos j2 = new JointPos(-38.148, -97.408, -133.704, -30.999, 89.584, 92.986);
        DescPose d2 = new DescPose(52.741, 262.917, 30.824, -5.696, -9.864, -126.092);
        JointPos j3 = new JointPos(-25.561, -123.131, -85.736, -94.911, 89.582, 93.006);
        DescPose d3 = new DescPose(70.455, 88.410, 45.299, -4.101, 31.775, -113.199);
        JointPos j4 = new JointPos(-8.013, -125.881, -79.196, -84.440, 89.564, 93.005);
        DescPose d4 = new DescPose(209.453, -73.895, 56.416, -4.727, 17.523, -95.906);
        JointPos j5 = new JointPos(-2.722, -94.518, -119.965, -54.518, 89.563, 93.005);
        DescPose d5 = new DescPose(274.800, 81.106, 102.977, -5.467, -2.980, -90.711);
        JointPos j6 = new JointPos(-2.671, -56.234, -138.914, -25.099, 95.355, 92.967);
        DescPose d6 = new DescPose(300.392, 177.281, 300.926, -1.909, -51.894, -89.703);
        JointPos j7 = new JointPos(-1.229, -121.184, -63.201, -122.331, 93.045, 93.019);
        DescPose d7 = new DescPose(296.856, -31.294, 215.698, -0.589, 34.594, -88.954);

        ExaxisPos ex = new ExaxisPos(0, 0, 0, 0);
        DescPose zeroOff = new DescPose(0, 0, 0, 0, 0, 0);

        int tool = 1;
        int workpiece = 1;
        float blend = 5.0f;

        // ===== Sistema de coordenadas 1 =====
        // Home
        robot.MoveJ(j1, d1, tool, workpiece, 100, 100, 100, ex, -1, 0, zeroOff);
        // PTP
        robot.MoveJ(j2, d2, tool, workpiece, 100, 100, 100, ex, blend, 0, zeroOff);
        // LIN
        robot.MoveL(j3, d3, tool, workpiece, 10, 100, 100, blend, 0, ex, 0, 1, zeroOff, 0, 90);
        // ARC
        robot.MoveC(j4, d4, tool, workpiece, 100, 100, ex, 0, zeroOff,
                    j5, d5, tool, workpiece, 100, 100, ex, 0, zeroOff,
                    10, blend, 100, 0);
        // CIR
        robot.Circle(j6, d6, tool, workpiece, 100, 100, ex,
                        j7, d7, tool, workpiece, 100, 100, ex,
                        10, 0, zeroOff, 100.0, blend, 0);

        // ===== WorkPieceTrsfStart(2) =====
        int rtn = robot.WorkPieceTrsfStart(2);
        Console.WriteLine("  WorkPieceTrsfStart(2) rtn={0}", rtn);

        // ===== Sistema de coordenadas 2 (tras la conversión) =====
        robot.MoveJ(j1, d1, tool, workpiece, 100, 100, 100, ex, -1, 0, zeroOff);
        robot.MoveJ(j2, d2, tool, workpiece, 100, 100, 100, ex, blend, 0, zeroOff);
        robot.MoveL(j3, d3, tool, workpiece, 10, 100, 100, blend, 0, ex, 0, 1, zeroOff, 0, 90);
        robot.MoveC(j4, d4, tool, workpiece, 100, 100, ex, 0, zeroOff,
                    j5, d5, tool, workpiece, 100, 100, ex, 0, zeroOff,
                    10, blend, 100, 0);
        robot.Circle(j6, d6, tool, workpiece, 100, 100, ex,
                        j7, d7, tool, workpiece, 100, 100, ex,
                        10, 0, zeroOff, 100.0, blend, 0);

        // ===== WorkPieceTrsfEnd =====
        rtn = robot.WorkPieceTrsfEnd();
        Console.WriteLine("  WorkPieceTrsfEnd() rtn={0}", rtn);

        return rtn;
    }