Movimiento del robot
====================

.. toctree:: 
    :maxdepth: 5


Jog (movimiento manual por pulsación)
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Jog (movimiento manual por pulsación)
    * @param  [in]  ref 0-jog de articulaciones, 2-jog en el sistema de coordenadas base, 4-jog en el sistema de coordenadas de herramienta, 8-jog en el sistema de coordenadas de pieza
    * @param  [in]  nb 1-articulación 1 (o eje x), 2-articulación 2 (o eje y), 3-articulación 3 (o eje z), 4-articulación 4 (o rotación alrededor del eje x), 5-articulación 5 (o rotación alrededor del eje y), 6-articulación 6 (o rotación alrededor del eje z)
    * @param  [in]  dir 0-dirección negativa, 1-dirección positiva
    * @param  [in]  vel Porcentaje de velocidad, [0~100]
    * @param  [in]  acc Porcentaje de aceleración, [0~100]
    * @param  [in]  max_dis Ángulo máximo de un solo jog, unidad [°] o distancia, unidad [mm]
    * @return  Código de error
    */
    errno_t  StartJOG(uint8_t ref, uint8_t nb, uint8_t dir, float vel, float acc, float max_dis);

Parada del jog con desaceleración
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Parada del jog con desaceleración
    * @param  [in]  ref  1-parada del jog de articulaciones, 3-parada del jog en el sistema de coordenadas base, 5-parada del jog en el sistema de coordenadas de herramienta, 9-parada del jog en el sistema de coordenadas de pieza
    * @return  Código de error
    */
    errno_t  StopJOG(uint8_t ref);

Parada inmediata del jog
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Parada inmediata del jog
    * @return  Código de error
    */
    errno_t  ImmStopJOG(); 

Ejemplo de código de control del jog del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestJOG(void)
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
         robot.CloseRPC();
         return 0;
     }

Movimiento en el espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t  MoveJ(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos *epos, float blendT, uint8_t offset_flag, DescPose *offset_pos);

Movimiento en el espacio de articulaciones (cálculo automático de cinemática directa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento en el espacio de articulaciones (cálculo automático de cinemática directa)
    * @param [in] joint_pos Posición articular objetivo, unidad deg
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] epos Posición del eje extendido, unidad mm
    * @param [in] blendT [-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad ms
    * @param [in] offset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos Magnitud del desplazamiento de pose
    * @return Código de error
    */
    errno_t MoveJ(JointPos* joint_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos* epos, float blendT, uint8_t offset_flag, DescPose* offset_pos);
   
Movimiento lineal en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Movimiento lineal en el espacio cartesiano
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
    errno_t MoveL(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos *epos, uint8_t search, uint8_t offset_flag, DescPose *offset_pos, float oacc = 100.0, int velAccParamMode = 0, int overSpeedStrategy = 0, int speedPercent = 10);

Movimiento lineal en el espacio cartesiano (cálculo automático de cinemática inversa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento lineal en el espacio cartesiano (cálculo automático de cinemática inversa)
    * @param [in] desc_pos  Pose cartesiana objetivo
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] blendMode Modo de transición; 0-transición tangente interna; 1-transición por esquina
    * @param [in] epos Posición del eje extendido, unidad mm
    * @param [in] search 0-sin búsqueda de posición del alambre de soldadura, 1-búsqueda de posición del alambre de soldadura
    * @param [in] offset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos Magnitud del desplazamiento de pose
    * @param [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @param [in] overSpeedStrategy Estrategia de tratamiento de exceso de velocidad, 1-estándar; 2-detener con error al exceder la velocidad; 3-reducción adaptativa de velocidad, por defecto 0
    * @param [in] speedPercent Porcentaje de umbral de reducción de velocidad permitido [0-100], por defecto 10%
    * @return Código de error
    */
    errno_t MoveL(DescPose* desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos* epos, uint8_t search, uint8_t offset_flag, DescPose* offset_pos, int config = -1, int overSpeedStrategy = 0, int speedPercent = 10);

Movimiento en arco en el espacio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t MoveC(JointPos *joint_pos_p, DescPose *desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos *epos_p, uint8_t poffset_flag, DescPose *offset_pos_p, JointPos *joint_pos_t, DescPose *desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos *epos_t, uint8_t toffset_flag, DescPose *offset_pos_t, float ovl, float blendR, float oacc = 100.0, int velAccParamMode = 0);

Movimiento en arco en el espacio cartesiano (cálculo automático de cinemática inversa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento en arco en el espacio cartesiano (cálculo automático de cinemática inversa)
    * @param [in] desc_pos_p  Pose cartesiana del punto de ruta
    * @param [in] ptool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] puser Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] pvel Porcentaje de velocidad, rango [0~100]
    * @param [in] pacc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_p Posición del eje extendido, unidad mm
    * @param [in] poffset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_p Magnitud del desplazamiento de pose
    * @param [in] desc_pos_t  Pose cartesiana del punto objetivo
    * @param [in] ttool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] tuser Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] tvel Porcentaje de velocidad, rango [0~100]
    * @param [in] tacc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_t Posición del eje extendido, unidad mm
    * @param [in] toffset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos_t Magnitud del desplazamiento de pose
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return Código de error
    */
    errno_t MoveC(DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, uint8_t poffset_flag, DescPose* offset_pos_p, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, uint8_t toffset_flag, DescPose* offset_pos_t, float ovl, float blendR, int config = -1);

Movimiento de círculo completo en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t Circle(JointPos* joint_pos_p, DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, JointPos* joint_pos_t, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, float ovl, uint8_t offset_flag, DescPose* offset_pos, double oacc = 100.0, double blendR = -1, int velAccParamMode = 0);

Movimiento de círculo completo en el espacio cartesiano (cálculo automático de cinemática inversa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento de círculo completo en el espacio cartesiano (cálculo automático de cinemática inversa)
    * @param [in] desc_pos_p  Pose cartesiana del punto de ruta 1
    * @param [in] ptool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] puser Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] pvel Porcentaje de velocidad, rango [0~100]
    * @param [in] pacc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_p Posición del eje extendido, unidad mm
    * @param [in] desc_pos_t  Pose cartesiana del punto de ruta 2
    * @param [in] ttool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] tuser Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] tvel Porcentaje de velocidad, rango [0~100]
    * @param [in] tacc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos_t Posición del eje extendido, unidad mm
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] offset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos Magnitud del desplazamiento de pose
    * @param [in] oacc Porcentaje de aceleración
    * @param [in] blendR -1: bloqueante; 0~1000: radio de suavizado
    * @param [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return Código de error
    */
    errno_t Circle(DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, float ovl, uint8_t offset_flag, DescPose* offset_pos, double oacc = 100.0, double blendR = -1, int config = -1);
    
Movimiento punto a punto en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Movimiento punto a punto en el espacio cartesiano
    * @param  [in]  desc_pos  Pose cartesiana objetivo o incremento de pose
    * @param  [in] tool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] user  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]
    * @param  [in] blendT [-1.0]-movimiento en posición (bloqueante), [0~500.0]-tiempo de suavizado (no bloqueante), unidad ms 
    * @param  [in] config  Configuración del espacio de articulaciones, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver con referencia a una configuración específica del espacio de articulaciones, por defecto -1   
    * @return  Código de error
    */
    errno_t  MoveCart(DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendT, int config);

Ejemplo de código de instrucciones básicas de movimiento del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestMove(void)
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

        JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0;
        float acc = 100.0;
        float ovl = 100.0;
        float oacc = 100.0;
        float blendT = 0.0;
        float blendR = 0.0;
        uint8_t flag = 0;
        uint8_t search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&j2, &desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, oacc, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&j3, &desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &j4, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, oacc, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&j3, &desc_pos3, tool, user, vel, acc, &epos, &j1, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        rtn = robot.MoveCart(&desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        printf("MoveCart errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, -1, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, -1, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&desc_pos3, tool, user, vel, acc, &epos, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, blendR, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        robot.CloseRPC();
        return 0;
    }

Movimiento helicoidal en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Movimiento helicoidal en el espacio cartesiano
    * @param  [in] joint_pos  Posición articular objetivo, unidad deg
    * @param  [in] desc_pos   Pose cartesiana objetivo
    * @param  [in] tool  Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param  [in] user  Número del sistema de coordenadas de pieza, rango [0~14]
    * @param  [in] vel  Porcentaje de velocidad, rango [0~100]
    * @param  [in] acc  Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param  [in] epos  Posición del eje extendido, unidad mm
    * @param  [in] ovl  Factor de escala de velocidad, rango [0~100]    
    * @param  [in] offset_flag  0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Magnitud del desplazamiento de pose
    * @param  [in] spiral_param  Parámetros de la hélice
    * @return  Código de error
    */
    errno_t  NewSpiral(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, ExaxisPos *epos, float ovl, uint8_t offset_flag, DescPose *offset_pos, SpiralParam spiral_param);  

Movimiento helicoidal en el espacio cartesiano (cálculo automático de cinemática inversa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento helicoidal en el espacio cartesiano (cálculo automático de cinemática inversa)
    * @param [in] desc_pos  Pose cartesiana objetivo
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] epos Posición del eje extendido, unidad mm
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] offset_flag 0-sin desplazamiento, 1-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param [in] offset_pos Magnitud del desplazamiento de pose
    * @param [in] spiral_param Parámetros de la hélice
    * @param [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return Código de error
    */
    errno_t NewSpiral(DescPose* desc_pos, int tool, int user, float vel, float acc, ExaxisPos* epos, float ovl, uint8_t offset_flag, DescPose* offset_pos, SpiralParam spiral_param, int config = -1);

Ejemplo de código de movimiento helicoidal
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSpiral(void)
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
      JointPos j(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      DescPose desc_pos(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose offset_pos1(50, 0, 0, -30, 0, 0);
      DescPose offset_pos2(50, 0, 0, -5, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      SpiralParam sp;
      sp.circle_num = 5;
      sp.circle_angle = 5.0;
      sp.rad_init = 50.0;
      sp.rad_add = 10.0;
      sp.rotaxis_add = 10.0;
      sp.rot_direction = 0;
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = 0.0;
      uint8_t flag = 2;
      robot.SetSpeed(20);
      rtn = robot.MoveJ(&j, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos1);
      printf("movej errcode:%d\n", rtn);
      rtn = robot.NewSpiral(&desc_pos, tool, user, vel, acc, &epos, ovl, flag, &offset_pos2, sp);
      printf("newspiral errcode:%d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Inicio del movimiento servo
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio del movimiento servo, para usar junto con las instrucciones ServoJ y ServoCart
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @param [in] filtertime Tiempo de filtro, unidad ms, por defecto 0
    * @param [in] gain Array de ganancias del lazo de posición, longitud 6, correspondientes a las ganancias del lazo de posición de las articulaciones J1~J6; valor por defecto { -1.0, -1.0, -1.0, -1.0, -1.0, -1.0 }
    * @return Código de error
    */
    errno_t ServoMoveStart(int comType = 0, int filtertime = 0, std::vector<double> gain = { -1.0, -1.0, -1.0, -1.0, -1.0, -1.0 });

Fin del movimiento servo
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fin del movimiento servo, para usar junto con las instrucciones ServoJ y ServoCart
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    errno_t ServoMoveEnd(int comType = 0);

Movimiento en modo servo en el espacio de articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento en modo servo en el espacio de articulaciones
    * @param [in] joint_pos Posición articular objetivo, unidad deg
    * @param [in] axisPos Posición del eje externo, unidad mm
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible, por defecto 0
    * @param [in] vel Porcentaje de velocidad, rango [0~100], aún no disponible, por defecto 0
    * @param [in] cmdT Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016]
    * @param [in] filterT Tiempo de filtro, unidad s, aún no disponible, por defecto 0
    * @param [in] gain Amplificador proporcional de la posición objetivo, aún no disponible, por defecto 0
    * @param [in] id ID de la instrucción servoJ, por defecto 0
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    errno_t ServoJ(JointPos *joint_pos, ExaxisPos* axisPos, float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0);

Ejemplo de código de movimiento servo en modo articular con tiempo de filtro
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestServoJWithFiltertime()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot(false);
        int rtn = 0;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        rtn = robot.SetCmdRpyCallback(UDPFrameCallBack);
        printf("SetCmdRpyCallback rtn is %d\n", rtn);
        robot.SetReConnectParam(true, 300000, 50);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            printf("robot RPC failed, errcode is %d\n", rtn);
            return -1;
        }
        JointPos j(70.000000, -49.000000, -109.000000, -81.000000, 76.000000, 93.000000);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.MoveJ(&j, 1, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        float vel = 0.0;
        float acc = 0.0;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0;
        uint8_t flag = 0;
        float dt = 0.1f;
        int cmdID = 0;
        int ret = robot.GetActualJointPosDegree(flag, &j);
        if (ret != 0)
        {
            printf("GetActualJointPosDegree errcode:%d\n", ret);
        }
        int comType = 0;
        int count = 300;
        int filtertime = 0;
        std::vector<double> ServoGain = { 22.0, 22.0, 22.0, 22.0, 22.0, 22.0 };
        rtn = robot.ServoMoveStart(comType, filtertime, ServoGain);
        printf("ServoMoveStart rtn is %d\n", rtn);
        std::ifstream fin("D://zUP/6RPTPpath.txt");
        std::string line;
        while (std::getline(fin, line))
        {
            JointPos p = {};
            int ret = sscanf(line.c_str(), "ServoJ(%lf,%lf,%lf,%lf,%lf,%lf,", &p.jPos[0], &p.jPos[1], &p.jPos[2], &p.jPos[3], &p.jPos[4], &p.jPos[5]);
            rtn = robot.ServoJ(&p, &epos, acc, vel, cmdT, filterT, gain, cmdID, comType);
        }
        fin.close();
        robot.ServoMoveEnd(comType);
        printf("ServoMoveEnd rtn is %d\n", rtn);
        robot.Sleep(4000);
        robot.CloseRPC();
        return 0;
    }

Ejemplo de código de movimiento servo en el espacio de articulaciones del robot basado en comunicación UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    void UDPFrameCallBack(int srcType, int count, int cmdID, int len, std::string content)
    {
        cout << "recv cmd: cmdID:  " << to_string(cmdID) << "  content is " << content << "  count is " << count << endl;;
            return;
    }

    int TestServoJUDP(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        int rtn = 0;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        rtn = robot.SetCmdRpyCallback(UDPFrameCallBack);
        printf("SetCmdRpyCallback rtn is %d\n", rtn);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 50);
        JointPos j(0, -90, 90, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        while (true)
        {
            robot.MoveJ(&j, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
            float vel = 0.0;
            float acc = 0.0;
            float cmdT = 0.016;
            float filterT = 0.0;
            float gain = 0.0;
            uint8_t flag = 0;
            float dt = 0.1;
            int cmdID = 0;
            int ret = robot.GetActualJointPosDegree(flag, &j);
            if (ret != 0)
            {
                printf("GetActualJointPosDegree errcode:%d\n", ret);
            }
            int comType = 1;
            int count = 300;
            rtn = robot.ServoMoveStart(comType);
            printf("ServoMoveStart rtn is %d\n", rtn);
            while (count)
            {
                rtn = robot.ServoJ(&j, &epos, acc, vel, cmdT, filterT, gain, cmdID, comType);
                printf("ServoJ rtn is %d\n", rtn);
                j.jPos[0] += dt;
                j.jPos[1] += dt;
                j.jPos[2] += dt;
                j.jPos[3] += dt;
                j.jPos[4] += dt;
                j.jPos[5] += dt;
                epos.ePos[0] += dt;
                count -= 1;
                robot.Sleep(15);
            }
            robot.ServoMoveEnd(comType);
            printf("ServoMoveEnd rtn is %d\n", rtn);
            count = 300;
            robot.ServoMoveStart(comType);
            printf("ServoMoveStart rtn is %d\n", rtn);
            while (count)
            {
                robot.ServoJ(&j, &epos, acc, vel, cmdT, filterT, gain, cmdID, comType);
                printf("ServoJ rtn is %d\n", rtn);
                j.jPos[0] -= dt;
                j.jPos[1] -= dt;
                j.jPos[2] -= dt;
                j.jPos[3] -= dt;
                j.jPos[4] -= dt;
                j.jPos[5] -= dt;
                epos.ePos[0] -= dt;
                count -= 1;
                robot.Sleep(15);
            }
            robot.ServoMoveEnd(comType);
            printf("ServoMoveEnd rtn is %d\n", rtn);
        }
        robot.Sleep(4000);
        robot.CloseRPC();
        return 0;
    }

Movimiento en modo servo en el espacio de articulaciones (admite la entrada de múltiples puntos a la vez)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t ServoJ(std::vector<JointPos> joint_pos, ExaxisPos* axisPos, float acc, float vel, float cmdT, float filterT, float gain, int& servoJCmdCount, int id = 0, int comType = 0);

Ejemplo de código de movimiento en modo servo en el espacio de articulaciones (entrada de múltiples puntos)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestServoJMultiPos()
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
        std::ifstream fin("C://Users/fr/Desktop/ServoJPath.txt");
        if (!fin.is_open())
        {
            std::cerr << "open ServoJPath.txt failed\n";
            return -1;
        }
        std::vector<JointPos> all_joint_data;
        std::string line;
        while (std::getline(fin, line))
        {
            std::istringstream iss(line);
            double val;
            int col_idx = 0;
            std::vector<double> one_pose;
            JointPos onePose = {};
            while (iss >> val)
            {
                if (col_idx >= 1 && col_idx <= 6)
                {
                    one_pose.push_back(val);
                }
                col_idx++;
            }
            if (one_pose.size() == 6)
            {
                onePose.jPos[0] = one_pose[0];
                onePose.jPos[1] = one_pose[1];
                onePose.jPos[2] = one_pose[2];
                onePose.jPos[3] = one_pose[3];
                onePose.jPos[4] = one_pose[4];
                onePose.jPos[5] = one_pose[5];
                all_joint_data.push_back(onePose);
            }
        }
        fin.close();
        std::cout << "read " << all_joint_data.size() << " servoJPos\n";
        std::vector<JointPos> back_forth_path;
        back_forth_path.insert(back_forth_path.end(), all_joint_data.begin(), all_joint_data.end());
        for (auto it = all_joint_data.rbegin() + 1; it != all_joint_data.rend(); ++it)
        {
            back_forth_path.push_back(*it);
        }
        ExaxisPos epos = {};
        DescPose offset_pos = {};
        robot.Sleep(1000);
        while (1)
        {
            robot.ResetAllError();
            robot.MoveJ(&all_joint_data[0], 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
            int moveCount = 0;
            while (moveCount < back_forth_path.size() - 10)
            {
                robot.GetRobotRealTimeState(&pkg);
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
                std::vector<JointPos> joint_pos = {};
                for (int j = 0; j < singleServoJCount; j++)
                {
                    joint_pos.push_back(back_forth_path[moveCount]);
                    moveCount++;
                }
                ExaxisPos axisPos = { 0.0, 0.0, 0.0, 0.0 };
                int servoJCmdCount = 0;
                rtn = robot.ServoJ(joint_pos, &axisPos, 100.0, 100.0, 0.008, 0.008, 1.0, servoJCmdCount);
                if (rtn != 0)
                {
                    break;
                }
            }
            robot.Sleep(4000);
        }
        robot.Sleep(1000);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Inicio del control de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio del control de par de las articulaciones
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    errno_t ServoJTStart(int comType = 0);

Control de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Control de par de las articulaciones
    * @param [in] torque Par de las articulaciones j1~j6, unidad Nm
    * @param [in] interval Período de instrucción, unidad s, rango [0.001~0.008]
    * @param [in] checkFlag Estrategia de detección 0-sin limitación; 1-limitar potencia; 2-limitar velocidad; 3-limitar potencia y velocidad simultáneamente
    * @param [in] jPowerLimit Límite de potencia máxima de las articulaciones (W)
    * @param [in] jVelLimit Velocidad máxima de las articulaciones (°/s)
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    errno_t ServoJT(float torque[], double interval, int checkFlag, double jPowerLimit[6], double jVelLimit[6], int comType = 0);

Fin del control de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Fin del control de par de las articulaciones
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    errno_t ServoJTEnd(int comType = 0);

Ejemplo de código de control de par de las articulaciones
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    int TestServoJT(void)
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
         robot.DragTeachSwitch(1);
         float torques[] = { 0, 0, 0, 0, 0, 0 };
         robot.GetJointTorques(1, torques);
         int count = 100;
         robot.ServoJTStart(); 
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

Ejemplo de código de control de par de las articulaciones con protección contra exceso de velocidad
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int ServoJTWithSafety(FRRobot* robot)
    {
        robot->ResetAllError();
        robot->Sleep(500);
        float torques[] = { 0, 0, 0, 0, 0, 0 };
        robot->GetJointTorques(1, torques);
        robot->ServoJTStart(); 
        ROBOT_STATE_PKG pkg = {};
        robot->DragTeachSwitch(1);
        int checkFlag = 3;
        //double jPowerLimit[6] = {1, 1, 1, 1, 1, 1}; 
        double jPowerLimit[6] = { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
        double jVelLimit[6] = { 181, 80, 80, 80, 80, 80 };
        int count = 800000;
        int error = 0;
        while (count > 0)
        {
            torques[2] = torques[2] + 0.01;
            error = robot->ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit); 
            if (error != 0)
            {
                robot->ServoJTEnd();
            }
            printf("ServoJT rtn is %d\n", error);
            count = count - 1;
            robot->Sleep(1);
            robot->GetRobotRealTimeState(&pkg);
            printf("maincode %d, subcode %d\n", pkg.main_code, pkg.sub_code);
        }
        robot->DragTeachSwitch(0);
        error = robot->ServoJTEnd();  
        return 0;
    }

Ejemplo de código de control de par de las articulaciones del robot basado en comunicación UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    void UDPFrameCallBack(int srcType, int count, int cmdID, int len, std::string content)
    {
        cout << "recv cmd: cmdID:  " << to_string(cmdID) << "  content is " << content << "  count is " << count << endl;
        
        return;
    }
    int TestServoJTUDP(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetCmdRpyCallback(UDPFrameCallBack);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
        	return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        JointPos j(0, -90, 90, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.MoveJ(&j, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        float torques[] = { 0, 0, 0, 0, 0, 0 };
        robot.GetJointTorques(1, torques);
        int comType = 1;
        int count = 100;
        int checkFlag = 3;
        double jPowerLimit[6] = { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
        double jVelLimit[6] = { 80, 80, 80, 80, 80, 80 };
        rtn = robot.ServoJTStart(comType);
        printf("ServoJTStart rtn is %d\n", rtn);
        while (true)
        {
            torques[0] = 0.05;
            rtn = robot.ServoJT(torques, 0.001, checkFlag, jPowerLimit, jVelLimit, comType);
            printf("ServoJT rtn is %d\n", rtn);
            robot.Sleep(1);
            robot.GetRobotRealTimeState(&pkg);
            if (pkg.jt_cur_pos[0] > 30)
            {
                break;
            }
        }
        while (true)
        {
            torques[0] = -0.03;
            rtn = robot.ServoJT(torques, 0.001, checkFlag, jPowerLimit, jVelLimit, comType);
            printf("ServoJT rtn is %d\n", rtn);
            robot.Sleep(1);
            robot.GetRobotRealTimeState(&pkg);
            if (pkg.jt_cur_pos[0] < 0 || pkg.jt_cur_pos[1] < -110)
            {
                break;
            }
        }
        rtn = robot.ServoJTEnd(comType);
        printf("ServoJTEnd rtn is %d\n", rtn);
        robot.DragTeachSwitch(0);
        robot.Sleep(1000);
        robot.CloseRPC();
        return 0;
    }

Movimiento en modo servo en el espacio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t ServoCart(int mode, DescPose *desc_pose, ExaxisPos exaxis, float pos_gain[6], float acc, float vel, float cmdT, float filterT, float gain);

Ejemplo de código de movimiento servo en el espacio cartesiano con tiempo de filtro
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestServoCartWithFiltertime()
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
        DescPose desc_pos_dt = { 542.1690,34.7990,114.4800,169.808000,-3.600000,-133.152000 };
        ExaxisPos exaxis = { 0.0, 0.0, 0.0, 0.0 };
        float pos_gain[6] = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        int mode = 0;
        float vel = 0.0;
        float acc = 0.0;
        float cmdT = 0.008f;
        float filterT = 0.0;
        float gain = 0.0;
        uint8_t flag = 0;
        int count = 5000;
        robot.SetSpeed(20);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.MoveL(&desc_pos_dt, 1, 0, 100, 100, 100, -1, 0, &exaxis, 0, 0, &offset_pos);
        int filtertime = 0;
        std::vector<double> ServoGain = { 20.0, 20.0, 20.0, 20.0, 20.0, 20.0 };
        rtn = robot.ServoMoveStart(0, filtertime, ServoGain);
        std::ifstream fin("D://zUP/6RCARpath.txt");
        std::string line;
        while (std::getline(fin, line))
        {
            JointPos p = {};
            int ret = sscanf(line.c_str(), "ServoCart(0,%lf,%lf,%lf,%lf,%lf,%lf,", &desc_pos_dt.tran.x, &desc_pos_dt.tran.y, &desc_pos_dt.tran.z, &desc_pos_dt.rpy.rx, &desc_pos_dt.rpy.ry, &desc_pos_dt.rpy.rz);
            rtn = robot.ServoCart(mode, &desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
            printf("ServoCart rtn is %d\n", rtn);
        }
        fin.close();
        robot.ServoMoveEnd();
        robot.CloseRPC();
        return 0;
    }

Inicio del movimiento de spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Inicio del movimiento de spline
    * @return  Código de error
    */
    errno_t  SplineStart();

Movimiento de spline en el espacio de articulaciones (cálculo automático de cinemática directa)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento de spline en el espacio de articulaciones (cálculo automático de cinemática directa)
    * @param [in] joint_pos Posición articular objetivo, unidad deg
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @return Código de error
    */
    errno_t SplinePTP(JointPos* joint_pos, int tool, int user, float vel, float acc, float ovl);

Spline PTP (movimiento de spline en el espacio de articulaciones)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t  SplinePTP(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl);

Fin del movimiento de spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Fin del movimiento de spline
    * @return  Código de error
    */
    errno_t  SplineEnd();

Ejemplo de código de movimiento de spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSpline(void)
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
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
      JointPos j3(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
      JointPos j4(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_pos3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      DescPose desc_pos4(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = -1.0;
      uint8_t flag = 0;
      robot.SetSpeed(20);
      int err1 = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.SplineStart();
      robot.SplinePTP(&j1, &desc_pos1, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j2, &desc_pos2, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j3, &desc_pos3, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j4, &desc_pos4, tool, user, vel, acc, ovl);
      robot.SplineEnd();
      err1 = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.SplineStart();
      robot.SplinePTP(&j1, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j2, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j3, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j4, tool, user, vel, acc, ovl);
      robot.SplineEnd();
      robot.CloseRPC();
      return 0;
    }

Inicio del nuevo movimiento de spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio del nuevo movimiento de spline
    * @param [in] type  0-transición por arco, 1-los puntos dados son puntos de ruta
    * @param [in] averageTime Tiempo medio global de enlace (ms) (10 ~ ), por defecto 2000
    * @return Código de error
    */
    errno_t NewSplineStart(int type, int averageTime=2000);

Punto de instrucción del nuevo spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Punto de instrucción del nuevo spline
    * @param [in] joint_pos Posición articular objetivo, unidad deg
    * @param [in] desc_pos  Pose cartesiana objetivo
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm 
    * @param  [in] lastFlag Si es el último punto, 0-no, 1-sí
    * @return Código de error
    */ 
    errno_t NewSplinePoint(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag);

Punto de instrucción del nuevo spline (cálculo automático de cinemática inversa)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Punto de instrucción del nuevo spline (cálculo automático de cinemática inversa)
    * @param [in] desc_pos  Pose cartesiana objetivo
    * @param [in] tool Número del sistema de coordenadas de herramienta, rango [0~14]
    * @param [in] user Número del sistema de coordenadas de pieza, rango [0~14]
    * @param [in] vel Porcentaje de velocidad, rango [0~100]
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible
    * @param [in] ovl Factor de escala de velocidad, rango [0~100]
    * @param [in] blendR [-1.0]-movimiento en posición (bloqueante), [0~1000.0]-radio de suavizado (no bloqueante), unidad mm
    * @param [in] lastFlag Si es el último punto, 0-no, 1-sí
    * @param [in] config Configuración del espacio de articulaciones de la solución inversa, [-1]-resolver con referencia a la posición articular actual, [0~7]-resolver según una configuración específica del espacio de articulaciones
    * @return Código de error
    */
    errno_t NewSplinePoint(DescPose* desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag, int config = -1);

Fin del nuevo movimiento de spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fin del nuevo movimiento de spline
    * @return Código de error
    */
    errno_t NewSplineEnd();

Ejemplo de código del nuevo movimiento de spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestNewSpline(void)
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
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
      JointPos j3(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
      JointPos j4(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
      JointPos j5(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_pos3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      DescPose desc_pos4(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
      DescPose desc_pos5(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = -1.0;
      uint8_t flag = 0;
      robot.SetSpeed(20);
      int err1 = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.NewSplineStart(1, 2000);
      robot.NewSplinePoint(&j1, &desc_pos1, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j2, &desc_pos2, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j3, &desc_pos3, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j4, &desc_pos4, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j5, &desc_pos5, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplineEnd();
      err1 = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.NewSplineStart(1, 2000);
      robot.NewSplinePoint(&desc_pos1, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos2, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos3, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos4, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos5, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplineEnd();
      robot.CloseRPC();
      return 0;
    }

Terminar el movimiento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Terminar el movimiento
    * @return  Código de error
    */
    errno_t  StopMotion();

Pausar el movimiento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pausar el movimiento
    * @return Código de error
    */
    errno_t PauseMotion(); 

Reanudar el movimiento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:
    
    /**
    * @brief Reanudar el movimiento
    * @return Código de error
    */
    errno_t ResumeMotion();

Ejemplo de código de pausa, reanudación y parada del movimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestPause(void)
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
         JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos j5(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos5(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 100.0;
         float acc = 100.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         rtn = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         rtn = robot.MoveJ(&j5, &desc_pos5, tool, user, vel, acc, ovl, &epos, 1, flag, &offset_pos);
         robot.Sleep(1000);
         robot.PauseMotion();
         robot.Sleep(1000);
         robot.ResumeMotion();
         robot.Sleep(1000);
         robot.StopMotion();
         robot.Sleep(1000);
         robot.CloseRPC();
         return 0;
     }

Inicio del desplazamiento global de puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Inicio del desplazamiento global de puntos
    * @param  [in]  flag  0-desplazamiento en el sistema de coordenadas base/pieza, 2-desplazamiento en el sistema de coordenadas de herramienta
    * @param  [in] offset_pos  Magnitud del desplazamiento de pose
    * @return  Código de error
    */
    errno_t  PointsOffsetEnable(int flag, DescPose *offset_pos);

Fin del desplazamiento global de puntos
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Fin del desplazamiento global de puntos
    * @return  Código de error
    */
    errno_t  PointsOffsetDisable();

Ejemplo de código de desplazamiento de puntos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestOffset(void)
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
         JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         DescPose offset_pos1(0, 0, 50, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 100.0;
         float acc = 100.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.Sleep(1000);
         robot.PointsOffsetEnable(0, &offset_pos1);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.PointsOffsetDisable();
         robot.CloseRPC();
         return 0;
     }

Inicio del fly-by del AO del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio del fly-by del AO del armario de control
    * @param [in] AONum Número de AO del armario de control
    * @param [in] maxTCPSpeed Valor de velocidad TCP máxima [1-5000mm/s], por defecto 1000
    * @param [in] maxAOPercent Porcentaje de AO correspondiente al valor de velocidad TCP máxima, por defecto 100%
    * @param [in] zeroZoneCmp Valor de compensación de zona muerta en porcentaje de AO, entero, por defecto 20%, rango [0-100]
    * @return Código de error
    */
    errno_t MoveAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Parada del fly-by del AO del armario de control
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0
   
.. code-block:: c++
    :linenos:

    /**
    * @brief Parada del fly-by del AO del armario de control
    * @return Código de error
    */
    errno_t MoveAOStop();
    
Inicio del fly-by del AO del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0
   
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio del fly-by del AO del extremo
    * @param [in] AONum Número de AO del extremo
    * @param [in] maxTCPSpeed Valor de velocidad TCP máxima [1-5000mm/s], por defecto 1000
    * @param [in] maxAOPercent Porcentaje de AO correspondiente al valor de velocidad TCP máxima, por defecto 100%
    * @param [in] zeroZoneCmp Valor de compensación de zona muerta en porcentaje de AO, entero, por defecto 20%, rango [0-100]
    * @return Código de error
    */
    errno_t MoveToolAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);
    
Parada del fly-by del AO del extremo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0
   
.. code-block:: c++
    :linenos:

    /**
    * @brief Parada del fly-by del AO del extremo
    * @return Código de error
    */
    errno_t MoveToolAOStop();

Ejemplo de código de fly-by del AO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestMoveAO(void)
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
         JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         DescPose offset_pos1(0, 0, 50, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 20.0;
         float acc = 20.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         robot.MoveAOStart(0, 100, 100, 20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveAOStop();
         robot.Sleep(1000);
         robot.MoveToolAOStart(0, 100, 100, 20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveToolAOStop();
         robot.CloseRPC();
         return 0;
     }

Inicio del filtro FIR del movimiento PTP
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio del filtro FIR del movimiento PTP
    * @param [in] maxAcc Aceleración máxima extrema (deg/s2)
    * @param [in] maxJek Valor extremo unificado de jerk de las articulaciones (deg/s3)
    * @return Código de error
    */
    errno_t PtpFIRPlanningStart(double maxAcc, double maxJek = 1000);

Desactivar el filtro FIR del movimiento PTP
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
	* @brief Desactivar el filtro FIR del movimiento PTP
	* @return Código de error
	*/
	errno_t PtpFIRPlanningEnd();

Inicio del filtro FIR de los movimientos LIN y ARC
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
	* @brief Inicio del filtro FIR de los movimientos LIN y ARC
	* @param [in] maxAccLin Aceleración lineal máxima (mm/s2)
	* @param [in] maxAccDeg Aceleración angular máxima (deg/s2)
	* @param [in] maxJerkLin Jerk lineal máximo (mm/s3)
	* @param [in] maxJerkDeg Jerk angular máximo (deg/s3)
	* @return Código de error
	*/
	errno_t LinArcFIRPlanningStart(double maxAccLin, double maxAccDeg, double maxJerkLin, double maxJerkDeg);

Desactivar el filtro FIR de los movimientos LIN y ARC
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
	* @brief Desactivar el filtro FIR de los movimientos LIN y ARC
	* @return Código de error
	*/
	errno_t LinArcFIRPlanningEnd();

Ejemplo de código del filtro FIR
+++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

     int TestFIR(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos midjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         JointPos endjointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose middescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose enddescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.PtpFIRPlanningStart(1000, 1000);
         cout << "PtpFIRPlanningStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.PtpFIRPlanningEnd();
         cout << "PtpFIRPlanningEnd rtn is " << rtn << endl;
         robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000);
         cout << "LinArcFIRPlanningStart rtn is " << rtn << endl;
         robot.MoveL(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
         robot.MoveC(&midjointPos, &middescPose, 0, 0, 100, 100, &exaxisPos, 0, &offdese, &endjointPos, &enddescPose, 0, 0, 100, 100, &exaxisPos, 0, &offdese, 100, -1);
         robot.LinArcFIRPlanningEnd();
         cout << "LinArcFIRPlanningEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Activación del suavizado de aceleración
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Activación del suavizado de aceleración
    * @param [in] saveFlag Si se guarda tras el apagado
    * @return Código de error
    */
    errno_t AccSmoothStart(bool saveFlag);

Desactivación del suavizado de aceleración
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Desactivación del suavizado de aceleración
    * @param [in] saveFlag Si se guarda tras el apagado
    * @return Código de error
    */
    errno_t AccSmoothEnd(bool saveFlag);

Ejemplo de código de suavizado de aceleración
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestAccSmooth(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.AccSmoothStart(0);
         cout << "AccSmoothStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.AccSmoothEnd(0);
         cout << "AccSmoothEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }


Activación de la velocidad de orientación especificada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Activación de la velocidad de orientación especificada
    * @param [in] ratio Porcentaje de velocidad de orientación [0-300]
    * @return Código de error
    */
    errno_t AngularSpeedStart(int ratio);

Desactivación de la velocidad de orientación especificada
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Desactivación de la velocidad de orientación especificada
    * @return Código de error
    */
    errno_t AngularSpeedEnd();

Ejemplo de código de velocidad de orientación especificada del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestAngularSpeed(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.AngularSpeedStart(50);
         cout << "AngularSpeedStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.AngularSpeedEnd();
         cout << "AngularSpeedEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Inicio de la protección de posición singular
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

	/**
	* @brief Inicio de la protección de posición singular
	* @param [in] protectMode Modo de protección de singularidad, 0: modo de articulaciones; 1-modo cartesiano
	* @param [in] minShoulderPos Rango de ajuste de singularidad de hombro (mm), por defecto 100
	* @param [in] minElbowPos Rango de ajuste de singularidad de codo (mm), por defecto 50
	* @param [in] minWristPos Rango de ajuste de singularidad de muñeca (°), por defecto 10
	* @return Código de error
	*/
	errno_t SingularAvoidStart(int protectMode, double minShoulderPos, double minElbowPos, double minWristPos);

Detención de la protección de posición singular
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

	/**
	* @brief Detención de la protección de posición singular
	* @return Código de error
	*/
	errno_t SingularAvoidEnd();

Ejemplo de código de protección de posición singular del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestAngularSpeed(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.SingularAvoidStart(2, 10, 5, 5);
         cout << "SingularAvoidStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.SingularAvoidEnd();
         cout << "SingularAvoidEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }
    
Vaciar la cola de instrucciones de movimiento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Vaciar la cola de instrucciones de movimiento
    * @return Código de error
    */
    errno_t MotionQueueClear();
        
Moverse al punto inicial de la línea de intersección
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t MoveToIntersectLineStart(DescPose mainPoint[6], ExaxisPos mainExaxisPos[6], DescPose piecePoint[6], ExaxisPos pieceExaxisPos[6], int extAxisFlag, ExaxisPos exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveType, int moveDirection, DescPose offset);
            
Movimiento de línea de intersección
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
    errno_t MoveIntersectLine(DescPose mainPoint[6], ExaxisPos mainExaxisPos[6], DescPose piecePoint[6], ExaxisPos pieceExaxisPos[6], int extAxisFlag, ExaxisPos exaxisPos[4], int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveDirection, DescPose offset);
                
Ejemplo de código de movimiento de línea de intersección del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
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
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento en vacío en el lugar
    * @return Código de error
    */
    errno_t MoveStationary();

Ejemplo de código de movimiento en vacío en el lugar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestLaserStationary(void)
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 0, 10, 100);
        printf("LaserSensorRecordandReplay rtn is %d\n", rtn);
        rtn = robot.MoveStationary();
        printf("MoveStationary rtn is %d\n", rtn);
        rtn = robot.LaserSensorRecord1(0, 10);
        printf("LaserSensorRecordandReplay rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(9999999);
        return 0;
    }

Esperar a que finalice el movimiento en vacío en el lugar
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Esperar a que finalice el movimiento en vacío en el lugar
    * @return Código de error
    */
    errno_t WaitStationaryMotionDone();

Inicio de la oscilación en punto fijo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio de la oscilación en punto fijo
    * @param [in] weaveNum Número de oscilación [0-7]
    * @param [in] mode 0-sistema de coordenadas de herramienta; 1-punto de referencia
    * @param [in] refPoint Coordenadas cartesianas del punto de referencia [x,y,z,a,b,c]
    * @param [in] weaveTime Tiempo de oscilación [s]
    * @return Código de error
    */
    errno_t OriginPointWeaveStart(int weaveNum, int mode, DescPose refPoint, double weaveTime);
    
Fin de la oscilación en punto fijo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fin de la oscilación en punto fijo
    * @return Código de error
    */
    errno_t OriginPointWeaveEnd();
        
Ejemplo de código SDK de oscilación en punto fijo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestOriginPointWeave()
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
        JointPos j(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        DescPose refPoint = { 400.021,300.022,299.996,179.997,-0.003,-90.956 };
        robot.MoveJ(&j, 1, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.OriginPointWeaveStart(0, 0, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();
        robot.Sleep(2000);
        robot.MoveJ(&j, 1, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.OriginPointWeaveStart(0, 1, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Ejemplo de código de oscilación en punto fijo (incluye sensor láser y eje extendido)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestOriginPointWeave()
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
        JointPos j(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos1(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos2(5, 0.000, 0.000, 0.000);
        DescPose refPoint(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);
        robot.ExtDevLoadUDPDriver();
        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        printf("SetExAxisCmdDoneTime rtn is %d\n" , rtn);
        rtn = robot.ExtAxisServoOn(1, 1);
        printf("ExtAxisServoOn axis id 1 rtn is %d\n" , rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        printf("ExtAxisServoOn axis id 2 rtn is %d\n" , rtn);
        robot.Sleep(2000);
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        rtn = robot.LaserTrackingLaserOnOff(1, 0);
        printf("LaserTrackingLaserOnOff id 2 rtn is %d\n", rtn);
        robot.LaserTrackingTrackOnOff(1, 4);
        robot.Sleep(200);
        robot.OriginPointWeaveStart(0, 0, refPoint, 10);
        robot.MoveStationary();  
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);

        robot.Sleep(2000);      
    
        robot.ExtAxisMove(epos1, 100, -1);
        robot.LaserTrackingTrackOnOff(1, 4);
        robot.OriginPointWeaveStart(0, 0, refPoint, 20);
        robot.ExtAxisMove(epos2, 100, -1);
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Movimiento en modo servo de velocidad en el espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimiento en modo servo de velocidad en el espacio de articulaciones
    * @param [in] joint_pos Velocidades articulares objetivo de las 6 articulaciones, unidad deg/s
    * @param [in] axisPos Velocidades de los 4 ejes externos, unidad deg/s
    * @param [in] acc Porcentaje de aceleración, rango [0~100], aún no disponible, por defecto 0
    * @param [in] vel Porcentaje de velocidad, rango [0~100], aún no disponible, por defecto 0
    * @param [in] cmdT Período de envío de instrucciones, unidad s, rango recomendado [0.001~0.0016]
    * @param [in] filterT Tiempo de filtro, unidad s, aún no disponible, por defecto 0
    * @param [in] gain Amplificador proporcional de la posición objetivo, aún no disponible, por defecto 0
    * @param [in] id ID de la instrucción servoJ, por defecto 0
    * @param[in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    errno_t ServoJV(double jointVel[6], double exisVel[4], float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0);

Ejemplo de código de movimiento en modo servo de velocidad en el espacio de articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int ServoJVtest()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 300000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        double joint_vel[6] = { 10.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double exis_vel[4] { 0.0, 0.0, 0.0, 0.0 };
        float acc = 0.0f;
        float vel = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        int cnt = 0;
        while (cnt < 200)
        {
            int error = robot.ServoJV(joint_vel, exis_vel, acc, vel, cmdT, filterT, gain);
            printf("ServoJV rtn is %d\n", error);
            cnt++;
        }
        robot.CloseRPC();
        robot.Sleep(1000000);
        return 0;
    }

Inicio del control MIT de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio del control MIT de las articulaciones
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    errno_t ServoMITStart(int comType = 0);

Fin del control MIT de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fin del control MIT de las articulaciones
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    errno_t ServoMITEnd(int comType = 0);

Control MIT de las articulaciones
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Control MIT de las articulaciones
    * @param [in] posGain Ganancia de posición de las articulaciones j1~j6
    * @param [in] desPos Posición deseada de las articulaciones j1~j6, unidad: deg
    * @param [in] velGain Ganancia de velocidad de las articulaciones j1~j6
    * @param [in] desVel Velocidad deseada de las articulaciones j1~j6, unidad: deg/s
    * @param [in] torque_ff Par de prealimentación de las articulaciones j1~j6, unidad: Nm
    * @param [in] interval Período de instrucción, unidad s, rango [0.001~0.008]
    * @param [in] comType Tipo de envío de instrucciones; 0-xmlrpc; 1-UDP (corresponde al puerto 20007 del robot)
    * @return Código de error
    */
    errno_t ServoMIT(double posGain[6], double desPos[6], double velGain[6], double desVel[6], double torque_ff[6], double interval, int comType = 0);

Ejemplo de código de control MIT de las articulaciones del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int ServoMITtest()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.SetCmdRpyCallback(UDPFrameCallBack);
        printf("SetCmdRpyCallback rtn is %d\n", rtn);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        while (true)
        {
            robot.ResetAllError();
            robot.Sleep(500);
            double posGain[6] = { 0.0 };
            double desPos[6] = { 0.0 };
            double velGain[6] = { 0.0 };
            double desVel[6] = { 0.0 };
            double torques[6] = { 0.0 };
            float curTorque[6] = { 0.0 };
            robot.GetJointTorques(1, curTorque);
            for (int i = 0; i < 6; i++)
            {
                torques[i] = curTorque[i];
            }
            robot.ServoMITStart(0);
            ROBOT_STATE_PKG pkg = {};
            robot.DragTeachSwitch(1);
            double intev = 0.008;
            double jPowerLimit[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double jVelLimit[6] = { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {
                torques[5] = 0.02;
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);
                robot.Sleep(1);
                robot.GetRobotRealTimeState(&pkg);
                printf("pkg.jt_cur_pos[5]: %f\n", pkg.jt_cur_pos[5]);
                if (pkg.jt_cur_pos[5] > 30)
                {
                    break;
                }
            }
            while (true)
            {
                torques[5] = -0.02;
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);
                robot.Sleep(1);
                robot.GetRobotRealTimeState(&pkg);
                printf("pkg.jt_cur_pos[5]:%f\n", pkg.jt_cur_pos[5]);
                if (pkg.jt_cur_pos[5] < 0)
                {
                    break;
                }
            }
            robot.DragTeachSwitch(0);
            error = robot.ServoMITEnd(0);
        }
        robot.CloseRPC();
        robot.Sleep(1000000);
        return 0;
    }
    
Inicio de la conversión de puntos del sistema de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Inicio de la conversión de puntos del sistema de coordenadas de pieza
    * @param [in] workpieceID Número de pieza [0-14]
    * @return Código de error, devuelve 0 en caso de éxito
    */
    errno_t WorkPieceTrsfStart(int workpieceID);
    
Fin de la conversión de puntos del sistema de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.9.8

.. code-block:: c++
    :linenos:

    /**
    * @brief Fin de la conversión de puntos del sistema de coordenadas de pieza
    * @return Código de error, devuelve 0 en caso de éxito
    */
    errno_t WorkPieceTrsfEnd();
    
Ejemplo de código de movimiento de conversión del sistema de coordenadas de pieza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.9.8

.. code-block:: c++
    :linenos:

    int TestWorkPieceTrsf()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        JointPos j1(-11.188, -64.165, -107.299, -76.706, 89.590, 92.983);
        DescPose desc1(225.986, 190.694, 394.238, -6.230, -23.797, -98.972);
        JointPos j2(-38.148, -97.408, -133.704, -30.999, 89.584, 92.986);
        DescPose desc2(52.741, 262.917, 30.824, -5.696, -9.864, -126.092);
        JointPos j3(-25.561, -123.131, -85.736, -94.911, 89.582, 93.006);
        DescPose desc3(70.455, 88.410, 45.299, -4.101, 31.775, -113.199);
        JointPos j4(-8.013, -125.881, -79.196, -84.440, 89.564, 93.005);
        DescPose desc4(209.453, -73.895, 56.416, -4.727, 17.523, -95.906);
        JointPos j5(-2.722, -94.518, -119.965, -54.518, 89.563, 93.005);
        DescPose desc5(274.800, 81.106, 102.977, -5.467, -2.980, -90.711);
        JointPos j6(-2.671, -56.234, -138.914, -25.099, 95.355, 92.967);
        DescPose desc6(300.392, 177.281, 300.926, -1.909, -51.894, -89.703);
        JointPos j7(-1.229, -121.184, -63.201, -122.331, 93.045, 93.019);
        DescPose desc7(296.856, -31.294, 215.698, -0.589, 34.594, -88.954);
        ExaxisPos exaxis = {0.0, 0.0, 0.0, 0.0};
        DescPose offset(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int tool = 1;
        int workpiece = 1;
        double blend = 5.0;
        robot.MoveJ(&j1, &desc1, tool, workpiece, 100, 100, 100, &exaxis, -1, 0, &offset);
        robot.MoveJ(&j2, &desc2, tool, workpiece, 100, 100, 100, &exaxis, blend, 0, &offset);
        robot.MoveL(&j3, &desc3, tool, workpiece, 10, 100, 100, blend, 0, &exaxis, 0, 1, &offset);
        robot.MoveC(&j4, &desc4, tool, workpiece, 100, 100, &exaxis, 0, &offset, &j5, &desc5, tool, workpiece, 100, 100, &exaxis, 0, &offset, 10, blend);
        robot.Circle(&j6, &desc6, tool, workpiece, 100, 100, &exaxis, &j7, &desc7, tool, workpiece, 100, 100, &exaxis, 10, 0, &offset, 100.0, blend);
        rtn = robot.WorkPieceTrsfStart(2);
        printf("WorkPieceTrsfStart rtn is %d\n", rtn);
        robot.MoveJ(&j1, &desc1, tool, workpiece, 100, 100, 100, &exaxis, -1, 0, &offset);
        robot.MoveJ(&j2, &desc2, tool, workpiece, 100, 100, 100, &exaxis, blend, 0, &offset);
        robot.MoveL(&j3, &desc3, tool, workpiece, 10, 100, 100, blend, 0, &exaxis, 0, 1, &offset);
        robot.MoveC(&j4, &desc4, tool, workpiece, 100, 100, &exaxis, 0, &offset, &j5, &desc5, tool, workpiece, 100, 100, &exaxis, 0, &offset, 10, blend);
        robot.Circle(&j6, &desc6, tool, workpiece, 100, 100, &exaxis, &j7, &desc7, tool, workpiece, 100, 100, &exaxis, 10, 0, &offset, 100.0, blend);    
        rtn = robot.WorkPieceTrsfEnd();
        printf("WorkPieceTrsfEnd rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(2000);
    }