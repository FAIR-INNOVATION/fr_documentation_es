Versión V4.0.1
-----------------

Fecha: 2026-10-27

- **Optimización de la función de programas en segundo plano**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Programa en segundo plano.

    Descripción: 1. El programa en segundo plano admite comunicación socket, comunicación de bus de tarjeta y interacción de IO extendida; 2. El programa en segundo plano admite la función printmsg; 3. Se añade la configuración de salida DO de robot en posición.

- **Optimización de la visualización de la velocidad física de Lin\Arc\Circle**: 

    Descripción: En las interfaces de velocidad de las instrucciones lin, arc y circle, en las interfaces de modificación de las instrucciones correspondientes y en la interfaz de configuración de smarttool, se añade la conversión de unidades para mostrar la velocidad física actual (cm/min).

- **Optimización de la instrucción Servo**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción de movimiento servo.

    Descripción: 1. Configuración de filtrado global, que permite ajustar el tiempo de filtrado durante el movimiento servoj (incluido servocart); 2. Los parámetros de filtrado y ganancia de posición de las instrucciones servoj y servocart se abren y son ajustables.

- **Optimización de la función de consulta del estado de la pinza**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción de pinza.

    Descripción: 1. La interfaz web añade un interruptor de monitorización de estado para las pinzas adaptadas; 2. Se amplía el estado de movimiento de las pinzas adaptadas, añadiendo la detección del estado de agarre de objeto y de caída de objeto, con soporte para consulta mediante instrucciones.

- **Nueva función de tarjeta**: 

    Descripción: Se añade la función de reporte de subcódigo de fallo por tiempo de espera agotado de FieldBusSlaveWaitDI y FieldBusSlaveWaitAI de la tarjeta.

- **Nueva función de depuración paso a paso**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Depuración paso a paso.

    Descripción: El programa de enseñanza lua admite la depuración paso a paso en modo manual, pudiendo añadir puntos de interrupción para la depuración.

- **Nueva función configurable de estrategia de pausa y reanudación de la señal de parada de seguridad**: 
    Ruta: Configuración inicial -> Seguridad -> Parada de seguridad.

    Descripción: Se añade la configuración de la estrategia de pausa y reanudación, pudiendo elegir de forma autónoma la reanudación manual o automática del funcionamiento.

- **Nueva función de fábrica completa automatizada por PLC**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Copia de seguridad de datos; Configuración inicial -> Seguridad -> Seguridad de red.

    Descripción: 1. Carga del paquete de copia de seguridad; 2. Consulta del progreso de actualización de todos los parámetros; 3. Se añaden instrucciones de restauración de configuración de fábrica, configuración del idioma de WebApp, configuración del código SN y obtención del estado de la caja de botones; 4. El PLC obtiene el estado del robot cada 1ms; 5. Configuración de activación de DHCP y NTP (solo versión LA), configuración de activación del puerto 8082.

Versión V4.0.0
-----------------

Fecha: 2026-09-23

- **Optimización del modo de reducción de velocidad**: 

    Descripción: Optimización de la velocidad global tras salir del modo reducido.

- **Optimización de la comunicación en modo remoto de la tarjeta Hilscher**: 
    Ruta: Modo remoto -> Actualización de firmware.

    Descripción: Mejora de la realimentación y la estabilidad de la comunicación.

- **Optimización del problema de identificación de carga del bucle de corriente**: 
    Ruta: Configuración inicial -> Carga -> Movimiento de identificación.

    Descripción: Se oculta la identificación de carga para los modelos grandes; la función de los modelos pequeños (FR3-FR16 y modelos correspondientes) funciona con normalidad; la desviación de la identificación de carga estándar de los modelos pequeños es de aproximadamente el 30%.

- **Nueva función de ajuste de velocidad en tiempo real basado en la velocidad física durante la soldadura**: 

    Descripción: Ajuste en tiempo real de la velocidad de movimiento del robot.

- **Nueva función de interacción de apertura de archivos de programa y modelos de herramienta de WebApp + función de extensión JOB de soldadura**: 
    Ruta: Programa de enseñanza -> Instrucciones de control de fuerza.

    Descripción: 1. La función de apertura de archivos de programa ordena por A-Z o por hora para facilitar la búsqueda; 2. El modelo de herramienta se asocia y carga vinculado a la herramienta; 3. CO se amplía de 3 funciones de señal JOB a 8, con soporte para 256 procesos; 4. La comunicación UDP de la máquina de soldar añade la configuración del número de proceso JOB.

- **Nueva adaptación de modelos a la función de bloqueo de arrastre del bucle de corriente**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Bloqueo de arrastre.

    Descripción: Se amplía a los cuatro nuevos modelos FR20, FR30, FR3WML y FR3WMS.

- **Nueva función de seguridad de red**: 
    Ruta: Configuración inicial -> Seguridad -> Seguridad de red.

    Descripción: 1. Al acceder a webApp desde el navegador, el protocolo de comunicación salta automáticamente a HTTPS; 2. El cliente añade la función de certificado del protocolo de instrucciones; 3. Se añade la verificación de integridad al iniciar el software.

- **Nueva función de exportación del registro de seguridad**: 
    Ruta: Configuración inicial -> Seguridad -> Registro de seguridad.

    Descripción: Se añaden las funciones de exportación y eliminación del registro de seguridad.

Versión V3.9.9
-----------------

Fecha: 2026-09-01

- **Optimización del paquete de proceso de ensamblaje por control de fuerza**: 
    Ruta: Programa de enseñanza -> Instrucciones de control de fuerza.

    Descripción: Mejora de la facilidad de uso y la fiabilidad del proceso.

- **Optimización de la configuración dinámica de esclavos del maestro IGH**: 

    Descripción: Mejora de la compatibilidad entre múltiples modelos y de la facilidad de mantenimiento.

- **Nueva extensión de la función de arrastre por impedancia articular para múltiples modelos**: 
    Ruta: Aplicaciones auxiliares -> Bloqueo de arrastre.

    Descripción: Soporte de la función de arrastre para los modelos FR3-WML, FR3-WMS, FR3-C y FR5-C.

- **Nueva función de verificación de la configuración de seguridad**: 
    Ruta: Configuración inicial -> Seguridad.

    Descripción: Reestructuración de la página de seguridad, verificación de la contraseña de configuración de seguridad, verificación de la legitimidad de la configuración y generación del informe de seguridad en PDF.

- **Nueva adaptación completa del sensor de fuerza de seis dimensiones Kaiwei**: 
    Ruta: Configuración inicial -> Periféricos -> Sensor de fuerza.

    Descripción: Se añade la adaptación del sensor de fuerza KWL.

- **Nuevo soporte de oscilación en la reproducción de escaneo láser**: 
    Ruta: Programación de programas -> Registro láser -> Instrucción de reproducción de seguimiento láser.

    Descripción: Mejora de la adaptabilidad del proceso de soldadura láser y de la calidad de la soldadura.

- **Nuevo diagnóstico de salud del enlace físico de la pila de protocolos IGH**: 

    Descripción: Se añade la lectura y visualización en la interfaz, facilitando la localización rápida de problemas del bus.

Versión V3.9.8
-----------------

Fecha: 2026-07-27

- **Optimización del movimiento de seguimiento de cinta transportadora**: 
    Ruta: Programa de enseñanza -> Instrucción de cinta transportadora.

    Descripción: 1. Optimización del punto de entrada de IO y de la configuración del punto inicial del programa; 2. Optimización de la activación múltiple de la señal IO durante el movimiento.

- **Optimización de la función de carga web de programas LUA de gran tamaño y subprogramas**: 
    Ruta: Programa de enseñanza -> Importar programa.

    Descripción: Carga y ejecución de archivos de programa lua de gran tamaño (superiores a 50M).

- **Optimización de las instrucciones de establecimiento/obtención de herramienta, sistema de coordenadas de pieza y carga del robot**: 
    Ruta: Configuración inicial -> Herramienta, sistema de coordenadas de pieza, carga.

    Descripción: A través del puerto de instrucciones 8080, el SDK y webapp se pueden establecer y obtener con normalidad los parámetros del sistema de coordenadas y de la carga.

- **Nuevas funciones relacionadas con smarttool**: 
    Ruta: Configuración inicial -> Periféricos -> Empuñadura de soldadura.

    Descripción: 1. Tras vaciar el programa o crear un programa nuevo, se restablece la memoria de la tecla IO; 2. Para la generación de las 3 instrucciones relacionadas con el encendido del arco, se añade la selección del número de proceso y se libera la limitación de configuración del tiempo de espera agotado del encendido del arco; 3. Se añade la función de borrado de puntos globales y, tras el borrado, se restablece el número de secuencia; 4. Se libera la limitación de configuración repetida de PTP, LIN y ARC.

- **Nueva función de adaptación de la mano diestra de cinco dedos**: 
    Ruta: Configuración inicial -> Periféricos -> Mano diestra.

    Descripción: Se añade la función de adaptación de la mano diestra de cinco dedos mediante Lua del extremo.

- **Nueva adaptación de FR3-WML a la función de arrastre por impedancia articular**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Bloqueo de arrastre.

    Descripción: Ajuste de los parámetros de arrastre mixto de fuerza de seis dimensiones e impedancia articular para FR3-WML, realizando la función de arrastre.

Versión V3.9.7
-----------------

Fecha: 2026-06-25

- **Optimización del paquete de idioma japonés del software**: 
  
    Descripción: Optimización del contenido de la traducción del paquete de idioma japonés.

- **Optimización de los parámetros de ruta del programa LUA del robot**: 

    Descripción: Para la entrada de archivos solo se necesita el nombre, sin necesidad de proporcionar la ruta.

- **Optimización de la función de oscilación superpuesta a la transición de línea recta y arco en la nueva spline**: 
    Ruta: Aplicaciones auxiliares -> Paquete de proceso -> Biblioteca de expertos en soldadura -> Soldadura oscilante con nueva spline.

    Descripción: Adaptación de la función de oscilación a la función de transición de línea recta y arco en la nueva spline.

- **Optimización de la función de protección de límite suave de articulación**: 
    Ruta: Configuración inicial -> Básico -> Articulación -> Límite suave.

    Descripción: Optimización de los coeficientes de rigidez y amortiguación del límite suave de cada articulación.

- **Nueva función de impresión print del programa LUA del robot**: 
    Ruta: Programa de enseñanza -> Función de impresión.

    Descripción: Consulta en tiempo real de la información de impresión personalizada del programa LUA.

- **Nueva función de adaptación de la mano diestra de tres dedos mediante Lua del extremo**: 
    Ruta: Configuración inicial -> Periféricos -> Ventosa.

    Descripción: 1. Se añade la adaptación de la ventosa y la mano diestra del extremo; 2. Optimización del protocolo abierto Lua del extremo existente.

- **Nueva función de error por monitorización de caída de la pinza**: 
    Ruta: Configuración inicial -> Periféricos -> Pinza.

    Descripción: Se añade el error por caída de pieza de la pinza; tras el error se detiene el movimiento.

- **Nueva función de realimentación de activación de la protección contra cortocircuito de 24V del módulo DO de la caja de control de tensión amplia**: 

    Descripción: Se añade la protección contra cortocircuito y el aviso de error.

Versión V3.9.6
-----------------

Fecha: 2026-05-26

- **Optimización de la función de movimiento matricial**: 
    Ruta: Aplicaciones auxiliares -> Paquete de proceso -> Movimiento matricial.
  
    Descripción: Optimización de la función del conjunto de instrucciones de movimiento matricial.

- **Optimización de la función de deceleración DI**: 
    Ruta: Configuración inicial -> Básico -> Configuración de I/O.
  
    Descripción: 1. Al activarse la señal DI, el proceso de ajuste de velocidad es suave, sin impactos ni bloqueos; 2. La ruta del extremo del robot no cambia antes y después del ajuste de velocidad; 3. Al activarse el ajuste de velocidad por DI no hay errores ni pausas; 4. Al activarse la parada por DI se ejecuta inmediatamente, sin errores.

- **Adición de la función de adaptación de comunicación de la máquina de soldar láser del robot**: 
    Ruta: Configuración inicial -> Periféricos -> Máquina de soldar.
  
    Descripción: 1. WebAPP añade la configuración, depuración e instrucciones de generación de programas lua relacionadas con la máquina de soldar láser; 2. Se añaden parámetros relacionados con la máquina de soldar láser; 3. Programa de adaptación desarrollado en el PLC.
    
- **Adición de la adaptación del protocolo EIP/CClink-IE de la tarjeta FRJ-PCIeN-EIP/CC/PN-RJ-V10**: 
    Ruta: Configuración inicial -> Periféricos -> Comunicación de tarjeta.
  
    Descripción: 1. Soporte de período de comunicación configurable; 2. Soporte de obtención del estado de conexión del bus; 3. Compatibilidad con los protocolos EIP y CC.

Versión V3.9.5
-----------------

Fecha: 2026-04-24

- **Optimización de la función del controlador**: 
    Ruta: Configuración general -> Configuración de red; Programa de enseñanza -> Programación de programas.
  
    Descripción: 1. Error de verificación de configuración de la misma dirección IP en ETH0 y ETH1; 2. Optimización de la visualización del color del número de línea de ejecución actual del programa.

- **Optimización de la velocidad del FR30**: 
  
    Descripción: Mejora de la velocidad de funcionamiento.

- **Optimización de la función de oscilación en arco**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción de arco.
  
    Descripción: Permite realizar el movimiento de oscilación.

- **Optimización de la función de depuración sin bloqueos de SetTrajectoryJSpeed**: 
  
    Descripción: Durante el proceso de ajuste de velocidad de la instrucción, la velocidad del robot no desciende a 0 al conmutar la velocidad.

- **Optimización de la operación del modo de edición de instrucciones del programa Lua en el módulo de programación de programas**: 
    Ruta: Programa de enseñanza -> Programación de programas.
  
    Descripción: Optimización para que el contenido de la instrucción se visualice con coincidencia precisa.

- **Adición de la adaptación del protocolo PN/Ecat/EIP/cclink de la tarjeta FRJ-PCIeN-EC-RJ-V20**: 
    Ruta: Configuración inicial -> Periféricos -> Comunicación de tarjeta.
  
    Descripción: 1. Soporte de actualización/obtención de firmware en línea; 2. Soporte de período de comunicación configurable; 3. Soporte de obtención del estado de conexión del bus.

- **Adición de instrucciones del controlador**: 
    Ruta: Programa de enseñanza -> Programación de programas; Configuración inicial -> Seguridad -> Parada de seguridad.
  
    Descripción: 1. Las instrucciones de movimiento añaden la opción de tipo de desplazamiento del sistema de coordenadas de pieza; 2. Se añade la función de parada de seguridad; 3. La caja de control, el extremo y la IO extendida añaden instrucciones de lectura de DO y AO.

- **Adición de la función de configuración de señal DO tras la parada de emergencia de la caja de control**: 
    Ruta: Configuración inicial -> Básico -> DO.
  
    Descripción: Se añade la función de configuración de señal DO tras la parada de emergencia de la caja de control.

- **Adición de la adaptación del paquete de idioma portugués de la versión de software**: 
  
    Descripción: Se añade la conmutación al idioma portugués.

Versión V3.9.4
-----------------

Fecha: 2026-04-08

- **Optimización de la función TPD de reproducción de la enseñanza de trayectoria del robot**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción TPD.
  
    Descripción: 1. Generación automática de la instrucción lua del punto inicial; 2. Diseño a prueba de errores del botón de inicio.

- **Optimización de la función de copia de seguridad de datos de Webapp**: 
  
    Descripción: Perfeccionamiento y optimización de la función de copia de seguridad de datos.

- **Optimización del límite suave y la actitud de embalaje del FR3WML**: 
  
    Descripción: Rango de configuración del límite suave de la articulación 3 de ±163°.

- **Optimización de la función de compensación de todos los parámetros DH y verificación rápida**: 
  
    Descripción: Modelo de compensación de todos los parámetros.
 
- **Adición de la función de control de impedancia del movimiento PTP**: 
  
    Descripción: Mejora de la seguridad del robot en el proceso de interacción con las personas.

- **Adición de la función de protocolo de comunicación del dispositivo de extremo del cabezal de moxibustión**: 
    Ruta: Configuración inicial -> Periféricos -> Transmisión transparente del extremo.
  
    Descripción: Se añade la adaptación del protocolo de comunicación del dispositivo de extremo.

- **Adición de la adaptación del paquete de idioma alemán de la versión de software**: 
  
    Descripción: Se añade la conmutación al idioma alemán.

- **Adición de la aplicación de la configuración de velocidad de seguridad a las instrucciones de movimiento servo**: 
    Ruta: Configuración inicial -> Seguridad -> Velocidad de seguridad.
  
    Descripción: Se añade la opción de deshabilitar tras parada con error por sobrevelocidad en la estrategia de seguridad.

- **Adición de la adaptación de LA al router inalámbrico TP-LINK AX3000**: 
  
    Descripción: Solución al problema de no poder acceder directamente a webApp de forma inalámbrica tras el reinicio por corte de energía.
    
- **Adición de la función de oscilación en punto fijo**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción Weave.
  
    Descripción: Función de oscilación en punto fijo en combinación con el sensor láser externo.

Versión V3.9.3
-----------------

Fecha: 2026-02-11

- **Optimización de la configuración de velocidad de las instrucciones de movimiento de SmartTool**: 
    Ruta: Configuración inicial -> Periféricos -> Empuñadura de soldadura.
  
    Descripción: El rango de configuración de velocidad de las instrucciones PTP, LIN y ARC se ajusta a 0-100% (anteriormente el límite superior de configuración de velocidad era del 30%).

- **Optimización de la observación de fuerza externa sin sensor de fuerza y mejora de la experiencia de arrastre**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Bloqueo de arrastre.
  
    Descripción: Mejora de la precisión de observación de fuerza externa hasta ±0.5N.

- **Optimización del mecanismo de reconexión del maestro Modbus TCP**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Modbus TCP.
  
    Descripción: Se añade la lógica de pausa.

- **Adición de la función de instrucción de depuración del eje extendido**: 
    Ruta: Configuración inicial -> Periféricos -> Eje extendido.
  
    Descripción: Realización de la cinemática inversa del robot bajo el sistema de coordenadas del eje extendido y del movimiento servo ServoCart con eje extendido.

- **Adición de la función configurable del estado de reinicio de DO en pausa y reanudación**: 
    Ruta: Configuración inicial -> Periféricos -> Empuñadura de soldadura.
  
    Descripción: Permite seleccionar si el estado de salida DO tras reanudar el movimiento es consistente con el anterior a la pausa.

Versión V3.9.2
-----------------

Fecha: 2026-01-26

- **Optimización de la enseñanza por arrastre del bucle de posición del sensor de par articular**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Bloqueo de arrastre.
  
    Descripción: Solución al problema de precisión insuficiente en el posicionamiento entre articulaciones durante el arrastre en 2s.

- **Optimización de la tarjeta de expansión**: 
  
    Descripción: Optimización del mecanismo de sincronización de datos de DO extendida.

- **Optimización de la función de seguimiento de arco**: 
    Ruta: Configuración inicial -> Periféricos -> Máquina de soldar.
  
    Descripción: Se añade la recogida de corriente de soldadura en tiempo real mediante el protocolo abierto de periféricos ModbusTCP.

- **Optimización de la función de restablecimiento de IP del controlador y del teach pendant físico**: 
    Ruta: Configuración del sistema -> Red.
  
    Descripción: ① Se añade la función de restablecimiento de IP del controlador en webrecovery, que requiere segunda confirmación; ② El teach pendant físico añade la función de restablecimiento de IP; ③ El teach pendant físico añade la posibilidad de restablecer su IP mediante botones físicos cuando no está conectado; la IP del teach pendant es 192.168.58.77.

- **Nueva configuración del nuevo robot FR3C**: 
  
    Descripción: El rango de funcionamiento de las articulaciones es idéntico al de la serie FR3; el brazo grande y el pequeño son idénticos a los del WMS; la carga nominal es de 3kg.

- **Nueva función de interferencia de cubo**: 
    Ruta: Configuración inicial -> Seguridad -> Zona de interferencia -> Interferencia de cubo.
  
    Descripción: Realización de la comprobación de interferencia de al menos 4 cubos simultáneamente, pudiendo configurar la salida CO correspondiente a la señal de interferencia.

- **Nueva extensión del módulo slave_interpret (protocolo PROFINET) y función de visualización de IO completa en Web**: 
    Ruta: Configuración inicial -> Periféricos -> Comunicación de tarjeta-> Actualización de tarjeta.
  
    Descripción: Se añade la actualización de firmware EtherCAT de la tarjeta Jiyuan, la detección de comunicación del PLC, el período configurable y la visualización de IO completa en Web (protocolo PROFINET).

- **Nueva función de protocolo abierto de smarttool**: 
    Ruta: Configuración inicial -> Periféricos -> Empuñadura de soldadura.
  
    Descripción: ① Se añaden la creación y el análisis de programas smarttool basados en protocolo abierto y el procesamiento de señales de detección, y se añade la función a prueba de errores de las teclas "Deshacer" y "Eliminar". ② La configuración de teclas del protocolo abierto de smarttool añade la función de generación automática.

- **Nueva compatibilidad mutua de los paquetes de copia de seguridad entre las versiones de software QX y LA**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Copia de seguridad de datos.
  
    Descripción: ① QX admite y puede importar completamente el paquete de copia de seguridad de LA; LA admite y puede importar completamente el paquete de copia de seguridad de QX; ② Compatibilidad con paquetes de copia de seguridad de la versión v3.8.7 y posteriores.

- **Nuevos parámetros configurables de CI del extremo y CI del controlador**: 
    Ruta: Configuración inicial -> Básico -> Configuración de I/O -> DI.
  
    Descripción: Permite configurar la interrupción de movimiento en la CI del extremo y sincronizar parte de las funciones configurables de la CI del controlador en la CI del extremo.

- **Nueva función de seguimiento servo de datos láser del robot**: 
    Ruta: Configuración inicial -> Periféricos -> Sensor láser de línea.
  
    Descripción: Permite que el robot realice el seguimiento directamente con los datos del sensor láser.

- **Nueva función de configuración del teach pendant**: 
  
    Descripción: ① Las teclas F1-F4 del teach pendant permiten configurar funciones personalizadas en la interfaz WEB; ② La conmutación de la llave al modo personalizado se puede configurar como modo de arrastre.

Versión V3.9.1
-----------------

Fecha: 2025-12-30

- **Función de registro en segundo plano de fallos y eventos de alarma del robot**: 
  
    Descripción: Durante el cierre de sesión de la interfaz de usuario se pueden registrar la información de fallos y alarmas, que se puede consultar tras volver a iniciar sesión.

- **Las instrucciones PTP y LIN añaden la función de movimiento relativo a la posición actual; WebApp añade la función de adición de la instrucción ServoJ**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucciones PTP/LIN.
  
    Descripción: Solución al problema de la complejidad de operación de las instrucciones cuando el brazo mecánico no dispone de puntos de enseñanza pero se necesita un desplazamiento basado en la posición actual; basta con introducir una instrucción para realizarlo.

- **Interruptor de depuración del protocolo abierto lua del extremo y función de verificación de sintaxis**: 
    Ruta: Configuración inicial -> Periféricos -> Pinza, sensor de fuerza, empuñadura de soldadura.
  
    Descripción: Actualmente el controlador integra los protocolos de extremo ya adaptados (pinza, sensor de fuerza, empuñadura de soldadura); esta optimización permite seleccionar y aplicar directamente al extremo desde webAPP; webServer añade la verificación de sintaxis del protocolo lua, informando directamente del error en caso de fallo de verificación; webAPP añade el interruptor de depuración del protocolo abierto lua; en estado de depuración, la ejecución del lua del extremo bloquea el error de tiempo de espera agotado de comunicación del sensor.

- **Optimización de la función del escenario de paletizado FRCap**: 
    Ruta: Aplicaciones auxiliares -> Paquete de proceso -> Paletizado.
  
    Descripción: El paletizado admite dos puntos de recogida de material; tras la llegada de material por dos líneas de producción, el robot, según el orden, recoge el material de los puntos de recogida de las dos líneas de producción y lo coloca en las dos paletas de paletizado correspondientes.

- **Optimización de la función del teach pendant físico**: 
    Ruta: Configuración del sistema -> Configuración general -> Red
  
    Descripción: Actualmente el cliente, al utilizar el teach pendant, debe cambiar primero a webapp y luego entrar en su propia interfaz de ordenador superior, lo que resulta engorroso; tras la optimización, sin haber iniciado sesión en la interfaz de enseñanza, al girar el interruptor físico de llave el robot puede conmutar entre modo manual y automático.

- **Optimización de la función de colisión**: 
    Ruta: Configuración inicial -> Básico -> Articulación -> Nivel de colisión -> Detección de falsos positivos.
  
    Descripción: Con el nivel de colisión en 1 también se puede funcionar a cualquier velocidad sin falsos avisos de error por velocidad alta; cuando hay colisión o compresión se informa del error y se detiene;

- **Función de calibración automática del TCP con sensor fotoeléctrico**: 
    Ruta: Configuración inicial -> Básico -> Coordenadas de herramienta -> Calibración automática fotoeléctrica.
  
    Descripción: Compatibilidad con la calibración automática de antorchas de soldadura de mango recto y de mango curvo;

Versión V3.9.0
-----------------

Fecha: 2025-11-27

- **Aplicación del cabezal de pulido de control de fuerza DFC de Daru**: 
    Ruta: Configuración inicial -> Periféricos -> Pulido -> Cabezal de pulido de control de fuerza DFC de Daru.
  
    Descripción: Adaptación y prueba de la parte de software del periférico de control de fuerza de pulido flexible inteligente DFC, satisfaciendo los requisitos de adaptación del sistema de pulido DFC.

- **Calibración de parámetros del sensor de par articular en la máquina completa**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Bloqueo de arrastre -> Arrastre de la máquina completa del sensor de par articular.
  
    Descripción: Ejecución de una trayectoria predefinida para completar la calibración de los parámetros de sensibilidad, linealidad, error de histéresis y precisión de repetición del sensor de par articular.

- **Nueva función de evitación de sobrepaso en la enseñanza por arrastre guiada por sensor de par articular**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Bloqueo de arrastre -> Arrastre de la máquina completa del sensor de par articular.
  
    Descripción: Mitigación del fenómeno de sobrepaso en el arrastre en el bucle de corriente; tras activar esta función se puede realizar cómodamente la operación de posicionamiento por arrastre.

- **Función de soldadura de línea de intersección de tubos**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción de línea de intersección de tubos.
  
    Descripción: Se registran 6 puntos de enseñanza en las secciones transversales del tubo principal y del tubo de unión respectivamente; introduciendo parámetros como la dirección de movimiento, la velocidad, la aceleración y los valores de desplazamiento, el robot puede obtener la trayectoria de la línea de intersección formada por la intersección de los dos tubos circulares y realizar la soldadura.

- **La configuración de espera de entrada analógica de Modbus añade la función de juicio de igualdad**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción Modbus.
  
    Descripción: El estado de espera de espera de entrada analógica del esclavo añade el juicio de igualdad.

- **Función de actualización con un clic de puntos de enseñanza y ejecución de un solo punto Lin**: 
    Ruta: Programa de enseñanza -> Puntos de enseñanza -> Gestión de la enseñanza.
  
    Descripción: La interfaz de puntos de enseñanza actualiza mediante la barra de operación del cuerpo del robot la pose actual del robot al punto correspondiente y permite seleccionar si se sincroniza el programa de enseñanza; se añade el modo de ejecución de un solo punto Lin.

- **Optimización de la función de registro de puntos en el modo de tabla de puntos**: 
    Ruta: Programa de enseñanza -> Puntos de enseñanza -> Gestión de la enseñanza.
  
    Descripción: En el modo de tabla de puntos, el nuevo registro de puntos puede actualizar sincronizadamente el programa lua; optimización y solución de los problemas de sobrevelocidad ocasional en el modo reducido PTP y de parada del movimiento tras alcanzar la posición de forma ocasional en el modo de ajuste de velocidad LIN.

- **Archivo de configuración user**: 
    Descripción: Optimización del problema de fallo de carga del archivo de configuración user del robot; se añaden las funciones de reinicio automático del archivo de configuración de respaldo y reversión del archivo de configuración de respaldo.

- **Versión de la interfaz web**: 
    Descripción: La versión de la interfaz web se actualiza a 2.0, actualizando y optimizando la interfaz de operación del software.

- **Nuevos modelos de robot V6.5**: 
    Descripción: Mediante la optimización de hardware como el reductor y de algoritmos, se reduce la vibración del robot y se mejora la precisión de la trayectoria; se añaden los modelos de robot FR3, FR5, FR10, FR16 y FR20.

- **Nueva configuración del modelo de robot FR5C**: 
    Descripción: La versión de software LA añade la función de configuración del modelo de robot FR5C.

Versión V3.8.7
-----------------

Fecha: 2025-10-21

- **Función de detección de colisiones del robot con riel guía de cremallera recta**: 
    Ruta: Configuración inicial -> Básico -> Articulación -> Nivel de colisión -> Detección de colisiones del robot con riel guía de cremallera recta.
  
    Descripción: Permite la parada de emergencia en caso de colisión durante el movimiento del riel, mejorando así la seguridad de la operación.

- **Nueva función de configuración de la velocidad física real de la nueva hélice**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción de nueva hélice N-Spiral.
  
    Descripción: Hace que el tramo de velocidad uniforme de la velocidad lineal de la herramienta del extremo del robot coincida con el valor establecido;

- **Función opcional de habilitación automática en la recuperación de parada de seguridad**: 
    Ruta: Configuración inicial -> Seguridad -> Parada de emergencia.
  
    Descripción: Se añade la configuración de la estrategia de habilitación tras el restablecimiento de la parada de emergencia de tipo 1b.

- **Puesta a cero con carga del sensor de fuerza y parámetros de admitancia para la conformidad de actitud abierta**: 
    Ruta: Configuración inicial -> Básico -> Carga; Programa de enseñanza -> Programación de programas -> Instrucción F/T Control.
  
    Descripción: Se añaden los parámetros de admitancia para la conformidad de actitud abierta.

- **Nueva función de seguimiento láser para arcos y círculos completos**: 
  
    Descripción: Permite realizar el seguimiento láser en tiempo real de arcos y círculos completos, con cambio de actitud durante el movimiento, y permite realizar la reproducción del escaneo láser de arcos y círculos completos.
    
- **Función de la caja de botones**: 
  
    Descripción: Optimización de la función de restablecimiento de IP de la caja de botones versión 1.0.

Versión V3.8.6
-----------------

Fecha: 2025-09-19

- **Nueva función de control de impedancia del robot**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción F/T.
  
    Descripción: Mediante la detección en tiempo real de la fuerza externa, cuando se alcanza el umbral establecido se adapta activamente a la fuerza externa desviándose de la trayectoria de movimiento, y cuando la fuerza externa desciende por debajo del umbral regresa a la trayectoria de movimiento, realizando así una mejor interacción humano-máquina.

- **Nueva función de detección de par antes del arrastre**: 
    Ruta: Configuración inicial -> Básico -> Nivel de colisión.
  
    Descripción: Antes de entrar en el modo de arrastre se realiza el cálculo de la diferencia entre la instrucción de par y la realimentación de cada articulación. Cuando se configura erróneamente la carga o el modo de instalación, la diferencia supera el umbral y no se puede entrar en el modo de arrastre, evitando que el robot pierda el control tras entrar en el modo de arrastre.

- **Nueva función de soldadura oscilante personalizada**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción Weave.
  
    Descripción: El usuario puede diseñar su propio modo de soldadura oscilante para ejecutar la soldadura oscilante.

- **ModbusTCP**: 
    Ruta: Programa de enseñanza -> Programación de programas -> ModbusTCP.
  
    Descripción: Optimización de la función de detección del tiempo de espera agotado del maestro ModbusTCP.

- **Ventosa neumática**: 
    Ruta: Configuración inicial -> Periféricos -> Ventosas en matriz.
  
    Descripción: Optimización de la función de adaptación de la página web de la ventosa neumática.

- **Error de fallo de búsqueda de posición del alambre de soldadura**: 
  
    Descripción: Optimización del error de fallo de búsqueda de posición del alambre de soldadura de WebAPP, reajustable.

- **Función de IO configurable**: 
  
    Descripción: Se añade la función de IO configurable para FR3C-FR3MT; las entradas configurables son CI0-CI4 y las salidas configurables son CO0-CO4.

Versión V3.8.5
-----------------

Fecha: 2025-08-19

- **Depuración de red Socket**: 
    Ruta: Programa de enseñanza -> Programación de programas -> Depuración de red Socket.
  
    Descripción: Permite añadir, configurar y eliminar configuraciones de conexión socket; se admite la configuración de hasta 4 conexiones socket. Mediante el módulo de instrucciones se puede generar la enseñanza y programación de apertura de conexión, cierre de conexión, envío de datos y recepción de datos.

- **Función de conversión de código G generado por CAD a planificación de trayectoria del robot**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Conversión de código G.
  
    Descripción: En software con función CAM como Solidworks, FUSION360, etc., se genera el archivo de código G de trayectorias de mecanizado como líneas rectas, arcos, círculos y splines, y a continuación se importa el archivo de código G al lado Web.

- **Las instrucciones de movimiento en línea recta, arco y círculo completo añaden la función de velocidad física real**: 
    Ruta: Programa de enseñanza -> Programación de programas; Configuración inicial -> Periféricos -> Empuñadura de soldadura.
  
    Descripción: Permite definir directamente la velocidad física real de funcionamiento de la instrucción de movimiento actual.
    
- **Optimización de la función de ajuste de velocidad PTP**: 
  
    Descripción: Garantiza la fluidez del proceso de ajuste de velocidad y reduce las fluctuaciones de velocidad de la instrucción en la unión del ajuste de velocidad.
    
- **Configuración del modelo de robot**: 
  
    Descripción: Se añade la opción de configuración del modelo de robot FR30L.
    
- **Adaptación de la caja de control**: 
  
    Descripción: Se añade la adaptación de la caja de control a la tarjeta ETMP03E (protocolo EtherCAT).

Versión V3.8.4.1
-----------------

Fecha: 2025-07-30

- **Adaptación de la caja de control al módulo de transmisión transparente Ethernet y función de control de pinza de ventosa**: 
    Ruta: Configuración inicial -> Periféricos -> Ventosas en matriz.
  
    Descripción: Basándose en la página y en el protocolo abierto de periféricos, se pueden controlar las ventosas en matriz (hasta 20) mediante el módulo de transmisión transparente de Ethernet a 485.

- **Planificación de trayectoria con previsión del robot (previsión a velocidad uniforme)**: 
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos.
  
    Descripción: Se añade la opción de interruptor de velocidad uniforme; al activarla, el robot realiza el movimiento con previsión a velocidad uniforme.

- **Optimización de la función del modo esclavo de la caja de control**: 
    Ruta: Configuración inicial -> Periféricos -> Comunicación de tarjeta, modo remoto.
  
    Descripción: Se añade la adaptación de la caja de control a la tarjeta Jiyuan ETMP03E (protocolo EtherCAT).

- **Función de obtención de la posición del punto de búsqueda de posición láser**: 
    Ruta: Configuración inicial -> Periféricos -> Sensor láser de línea.
  
    Descripción: Tras el éxito de la búsqueda de posición láser de la soldadura, se pueden obtener mediante SDK o instrucciones del protocolo TCP los datos de posición almacenados en "seamPos".

- **Función de apertura de velocidad de FR5 y FR10**: 
  
    Descripción: La velocidad lineal del FR5 se eleva de 1.0m/s a 1.7m/s; la velocidad lineal del FR10 se eleva de 1.5m/s a 2.0m/s.

- **Configuración del modelo de robot**: 
  
    Descripción: Se añade la opción de configuración del modelo de robot de brazo largo FR5-WML.

- **Optimización de la actualización de software**: 
  
    Descripción: Reducción del tiempo de actualización, compatibilidad con la degradación de una versión superior a cualquier versión inferior (3.7.6-3.8.4).

- **Optimización de la restauración de la configuración de fábrica**: 
  
    Descripción: La restauración de la configuración de fábrica conserva el modelo de robot, la rigidez, la configuración dinámica, la versión de la caja de botones, etc.

Versión V3.8.4
-----------------

Fecha: 2025-07-18
    
- **Implementación de la función de suavizado blending del eje extendido**: 
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos.
  
    Descripción: Realización del movimiento suave entre instrucciones del eje extendido, mejorando la eficiencia del trabajo.
    
- **Optimización de la función del modo esclavo de la caja de control**: 
    Ruta: Configuración inicial -> Periféricos -> Comunicación de tarjeta, modo remoto.
  
    Descripción: Se añade la configuración de IP de la tarjeta y el envío de instrucciones LUA desde la interfaz; se añade la función de inicio automático del protocolo de esclavo del controlador en modo remoto.
    
- **Adaptación QX de la tarjeta N2L de la caja de control (EtherCAT)**: 
    Descripción: Tarjeta de comunicación de bus en tiempo real industrial de FAIRINO, tarjeta miniPCIe, compatible con comunicación del protocolo EtherCAT.
    
- **Movimiento JOG del robot**: 
    Descripción: Se añade la función de salida del estado CO del movimiento JOG del robot.

Versión V3.8.3
-----------------

Fecha: 2025-06-27
    
- **Función del modo esclavo de la caja de control**: 
    Ruta: Configuración inicial -> Periféricos -> Comunicación de tarjeta.
  
    Descripción: La interfaz de periféricos del robot añade el módulo de configuración de comunicación de tarjeta, que permite, basándose en tarjetas de expansión nacionales, realizar la interacción de los protocolos EIP, CClink y PN con el esclavo del robot.
        
- **Adición de la función de detección de colisiones en el arrastre asistido por sensor de fuerza en modo manual**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Bloqueo de arrastre -> Bloqueo asistido por sensor de fuerza.
  
    Descripción: Al activar la función de arrastre asistido por sensor de fuerza, cuando el robot se encuentra en modo manual también se activa la función de detección de colisiones, evitando daños en el equipo del extremo.

- **Adición de la función de planificación de trayectoria con características de velocidad en forma de T + suavizado blending**: 
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos.
  
    Descripción: Realización del movimiento suave entre las distintas instrucciones de movimiento, mejorando la eficiencia del trabajo.
        
- **Optimización de la función de la interfaz de consulta de estado de WebApp**: 
    Ruta: Información de estado -> Consulta de estado.
  
    Descripción: Optimización de la configuración de parámetros de consulta de estado a 6, tiempo de forma de onda máximo de 30s, adición de la visualización de la vista de datos con posibilidad de copiar datos, y adición del nombre del icono de cambio de nombre.

- **Optimización de la fuerza de arrastre de toda la serie de robots FR**: 
    Ruta: Configuración inicial -> Básico -> Articulación -> Compensación de fricción -> Compensación de la fuerza de arrastre.
  
    Descripción: Hace que el arrastre sea más ligero proporcionando un par de compensación durante el arrastre.
    
- **Optimización de la función de almacenamiento del registro del sistema Web**: 
    Descripción: Corrección del problema de anomalía de los archivos de registro del sistema; se establece el número de días de conservación del registro por defecto en 7 días.

Versión V3.8.2
-----------------

Fecha: 2025-05-29 
    
- **Función de adaptación de la empuñadura de soldadura mediante protocolo abierto Lua del extremo**: 
    Ruta: Configuración inicial -> Periféricos -> Empuñadura de soldadura.
  
    Descripción: Se puede utilizar el protocolo abierto para adaptar la empuñadura de soldadura smarttool, con soporte para todos los parámetros configurables.
    
- **Adición del protocolo abierto de la máquina de soldar al protocolo abierto de periféricos del controlador**: 
    Ruta: Configuración inicial -> Periféricos -> Máquina de soldar.
  
    Descripción: Permite controlar la máquina de soldar comunicándose con ella mediante el protocolo abierto de periféricos del controlador (ModbusTCP).

- **Adición de la función de pausa del programa LUA**: 
    Ruta: Programa de enseñanza -> Programación de programas.
  
    Descripción: Durante la ejecución del programa de enseñanza se puede hacer clic en pausa en cualquier línea, incluidas las instrucciones de espera y las instrucciones de comunicación, y la pausa no ocupa el tiempo de espera agotado.    

- **Adición de la función de modificación de la velocidad en forma de T + Blending**: 
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos.

    Descripción: Tras activar el interruptor de modificación de la velocidad en forma de T, la curva de velocidad es suave; actualmente se admiten los tipos de blending (PTP-PTP, LIN-LIN, ARC-ARC, LIN-ARC, ARC-LIN).
    
- **Función de parámetros adaptativos FIR + función de pausa y reanudación FIR**: 
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos; Configuración inicial -> Seguridad -> Configuración de movimiento.

    Descripción: La función FIR añade el interruptor de activación global de FIR y de parámetros adaptativos; tras activarlo, la ejecución de las instrucciones normales PTP/LIN/ARC se convierte automáticamente en planificación FIR (sin radio de blend).
    
- **Optimización de la función Modbus RTU**: 
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos; Programa de enseñanza -> Programación de programas -> Configuración de Modbus RTU.

    Descripción: Permite configurar el maestro ModbusRTU en WebApp, configurar la velocidad en baudios, el modo de verificación, el número de estación, etc. Permite monitorizar los valores en tiempo real de los registros ModbusRTU.
    
- **Función de protección de límite suave de articulación**: 
    Ruta: Configuración inicial -> Articulación -> Límite suave.

    Descripción: En el modo de arrastre, cuando la articulación se aproxima al límite suave establecido en la interfaz existe una fuerza de amortiguación y, tras retirar el par externo, la articulación puede volver dentro del límite suave.
    
- **Función de ángulo de inclinación lateral de oscilación del robot**: 
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos.

    Descripción: Permite configurar el ángulo de oscilación personalizado de la herramienta del extremo del robot alrededor de la dirección Rx del sistema de coordenadas de oscilación durante el movimiento de oscilación.
    
- **Función de soldadura con variación gradual de los parámetros del proceso**: 
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos.

    Descripción: Permite realizar la variación gradual de la velocidad de avance y de la corriente y la tensión durante el proceso de soldadura.
    
- **Función de seguimiento de arco por señal analógica**: 
    Ruta: Configuración inicial -> Básico -> Configuración de I/O -> AI.

    Descripción: Conexión directa de las DI, DO y AI, AO de la caja de control con los puertos IO de la máquina de soldar, realizando el seguimiento de arco basado en la realimentación de corriente analógica.
    
- **Sistema de plugins FRCap + paquete de plugin de paletizado**: 
  
    Descripción: Se ha adaptado el sistema de plugins FRCap y el paquete de plugin de paletizado para la versión QX x86; FRCap puede interactuar con el controlador del robot mediante las interfaces oficiales proporcionadas, o el cliente puede desarrollar personalizadamente escribiendo instrucciones de interfaz y lógica de tratamiento según sus necesidades reales.
    
- **Modelos y modelos de robot**: 
  
    Descripción: Se añaden el modelo de robot FR3-C y la configuración del modelo.
    
Versión V3.8.1
-----------------

Fecha: 2025-04-14 
    
- **Optimización de la función de velocidad en forma de T**: 
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos; Configuración inicial -> Módulo básico.
  
    Descripción: La configuración de movimiento añade el modo de optimización de velocidad trapezoidal, optimizando el jerk en las fases de arranque y parada y aumentando la aceleración en la fase de aceleración. Se aplica principalmente a condiciones de trabajo propensas a errores de colisión en las fases de arranque y parada, así como a condiciones de trabajo con vibración residual evidente en las fases de arranque y parada.
    
- **Optimización de la función de seguimiento de cinta transportadora**: 
    Ruta: Aplicaciones auxiliares -> Paquete de proceso -> Seguimiento de cinta transportadora.
  
    Descripción: En el modo de movimiento de seguimiento de cinta transportadora se añade la función de movimiento de seguimiento e inspección, que no requiere realizar la enseñanza del movimiento bajo el sistema de coordenadas de pieza y permite personalizar la distancia de retardo de activación.

- **Adición de la función de retorno de impedancia de la zona de interferencia de eje**:
    Ruta: Configuración inicial -> Seguridad -> Zona de interferencia.
  
    Descripción: Con el arrastre asistido por sensor de fuerza, al entrar en la zona de interferencia se produce un efecto de retorno de impedancia.

- **Función de adaptación de la empuñadura de soldadura**:
    Descripción: Se añade la adaptación de la empuñadura de soldadura: la instalación de la empuñadura de soldadura en el extremo del robot permite la escritura de programas de soldadura y el control de las funciones de inicio, parada, conmutación manual/automático y arrastre del robot.

- **Adición de la visualización del anillo de límite articular en la página del lado WEB**:
    Descripción: Al activar la función de visualización del anillo de límite se puede mostrar en tiempo real la posición en que se encuentran las articulaciones.
    
- **Nuevas funciones del SDK**:
    Descripción: El SDK añade las funciones de descarga del registro del controlador, de todas las fuentes de datos y del paquete de copia de seguridad de datos.
    
- **Función de registro de la información de las articulaciones antes y después de la colisión**:
    Descripción: Registro de la posición, velocidad, aceleración e información de par de las articulaciones antes y después de la colisión, facilitando el análisis directo de las causas de la colisión en el sitio del cliente.

Versión V3.8.0
-----------------

Fecha: 2025-03-03 
  
- **Función de seguimiento de arco con desplazamiento y amplitud de oscilación de variación monótona gradual**:
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos.
  
    Descripción: La anchura de oscilación del parámetro de oscilación puede variar gradualmente a lo largo de un movimiento de soldadura, de modo que el parámetro de amplitud del inicio del segmento transita gradualmente hacia el parámetro de amplitud del final del segmento; el centro de soldadura puede desplazarse activamente fuera del centro de la soldadura.
  
- **Función de umbral de par de detección de colisiones personalizado**:
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos.
  
    Descripción: Permite establecer durante el funcionamiento el umbral de par de detección de colisiones. Se puede seleccionar según las necesidades el umbral de par articular o el umbral de par del lado del TCP; tras la colisión se imprimen en el archivo de registro la velocidad, la aceleración, el par y otra información de las articulaciones.
  
- **Función de método de planificación de trayectoria con previsión en tiempo real**:
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos.
  
    Descripción: Realización del ajuste suave de múltiples puntos de trayectoria; la velocidad de funcionamiento se ajusta de forma adaptativa según la curvatura de la ruta.

- **Dibujo de las curvas de carga de toda la serie de modelos FR**:
    Descripción: Actualización de los gráficos de curvas de carga de toda la serie de modelos FR.

- **Optimización de la lógica de conmutación de velocidad del modo reducido**:
    Descripción: Al activarse el modo reducido a veces se producía un movimiento con velocidad muy inferior a la del modo reducido; se optimiza y resuelve dicho problema.

- **Optimización de los puntos de enseñanza**:
    Descripción: Optimización de la información de aviso añadida a los puntos de enseñanza.

- **Función del paquete de funciones CNC basado en FOCAS**:
    Descripción: Se añade la función CNC de FOCAS.

- **Adaptación de las instrucciones de esclavo a las tarjetas**:
    Descripción: Las instrucciones de esclavo se adaptan a la tarjeta EnTalk miniPCIe (protocolo Profinet, protocolo Ethernet/IP, protocolo CC-Link IEF Basic) y a la tarjeta CIFX 9OE-RE/F/PNS miniPCIe (protocolo Profinet, protocolo Ethernet/IP, protocolo Ethercat, protocolo CC-Link IEF Basic).

- **Función de realimentación de marca de tiempo checkpoint**:
    Descripción: El movimiento servo J puede recibir el resultado de la marca de tiempo, incluidos el número de instrucción y las marcas de tiempo de envío, entrada en cola, salida de cola y ejecución.

- **Adaptación del sensor láser al protocolo abierto de periféricos del controlador**:
    Descripción: Se añade la función de comunicación del protocolo abierto de periféricos láser.
   
Versión V3.7.8
-----------------

Fecha: 2025-01-20 
  
- **Función de seguimiento de punto fijo sin transformación de datos láser con eje extendido**:
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos; Configuración inicial -> Periféricos -> Sensor láser de línea.
  
    Descripción: Dirigida principalmente al seguimiento de punto fijo en tiempo real del posicionador, hace que la desviación de la pieza registrada por láser durante el movimiento del eje extendido se compense en el extremo de la herramienta del robot.
  
- **Adición y optimización de la configuración de CI del robot**:
    Ruta: Configuración inicial -> Básico -> Configuración de I/O -> DI; Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos.
  
    Descripción: 1. La entrada configurable CI añade la función de conmutación del modo manual/automático del robot por nivel alto/bajo. Al configurar el puerto CI como "Conmutación manual/automático (nivel alto/bajo)", cuando la señal de entrada de dicho puerto es válida el robot cambia automáticamente al modo automático, y cuando la señal de entrada de dicho puerto no es válida el robot cambia automáticamente al modo manual. 2. Tras abrir un programa LUA en WebApp, al iniciar el programa LUA mediante una CI configurable se ejecuta automáticamente el programa LUA abierto actualmente, en lugar del último programa guardado.
  
- **Optimización de la función de consulta de estado de WebApp**: 
    Ruta: Información de estado -> Consulta de estado.
  
    Descripción: El modo de interacción de datos entre el frontend y el backend se cambia del modo de solicitud de sondeo del frontend al modo de envío activo de datos mediante websocket, reduciendo el uso de CPU.
  
- **Función configurable del nivel alto/bajo válido del DO de encendido del firmware de la caja de control**:
    Ruta: Configuración inicial -> Básico -> Configuración de I/O -> DO.
  
    Descripción: Se añade la configuración "Salida DO de la caja de control durante el encendido"; antes de habilitar el robot, el DO de la caja de control se puede configurar con el estado de nivel alto/bajo requerido según el escenario de uso concreto.
  
- **Función de método de planificación de trayectoria con previsión en tiempo real**:
    Ruta: Programa de enseñanza -> Programación de programas, programación gráfica, programación por grafo de nodos.
  
    Descripción: Se añade la instrucción "TrajectoryLA".

- **Función de estrategia tras la colisión basada en el sensor de fuerza**:
    Ruta: Configuración inicial -> Articulación -> Nivel de colisión.
  
    Descripción: El modo de rebote por colisión añade el parámetro "Velocidad de seguridad".

- **Función de elevación automática tras la colisión del sensor de fuerza**:
    Descripción: Realización de la función de elevación automática del robot tras la detección de colisiones basada en el sensor de fuerza, con limitación de la velocidad durante el proceso de elevación.

- **Dibujo de las curvas de carga de toda la serie de modelos FR**:
    Descripción: Actualización de los gráficos de curvas de carga de toda la serie de modelos FR.

Versión V3.7.7
-----------------

Fecha: 2024-12-30
  
- **Función de monitorización en tiempo real de los datos de estado de la pinza**:
    Ruta: Configuración inicial -> Periféricos -> Pinza -> Monitorización de estado.
  
    Descripción: Visualización en tiempo real de información de estado como la velocidad de funcionamiento, el par y la posición de la pinza.
  
- **Función de recogida de datos de fallo del controlador**:
    Ruta: Configuración del sistema -> Configuración general -> Datos de fallo.

    Descripción: Cuando durante el funcionamiento del robot se producen fallos como colisiones o errores de punto de instrucción, el controlador registra automáticamente información de estado como la posición y la velocidad del robot en los 15s anteriores y posteriores al fallo. WebApp permite exportar la información de fallo en formato .csv, ayudando a investigar y analizar la causa del fallo.
  
- **Función de evitación y cruce de puntos singulares en el arrastre asistido por sensor de fuerza**:
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Bloqueo de arrastre -> Bloqueo asistido por sensor de fuerza.

    Descripción: 1. En la interfaz de arrastre asistido por sensor de fuerza, al seleccionar la estrategia de evitación, cuando se arrastra el robot cerca de un punto singular se genera una fuerza virtual. 2. Al seleccionar la estrategia de cruce, al acercarse al punto singular se cambia al modo de arrastre y, al alejarse del punto singular, se vuelve al arrastre asistido por sensor de fuerza.

- **Adaptación de la dinámica antigua a la instalación libre de 360° y función de adaptación de la dinámica en la importación del paquete de copia de seguridad**:
    Ruta: Configuración inicial -> Básico -> Instalación; Aplicaciones auxiliares -> Aplicación de herramientas -> Copia de seguridad de datos.

    Descripción: Al importar el paquete de copia de seguridad se añade la verificación del tipo de robot, el modo de instalación, el ángulo de instalación y el tipo de configuración dinámica; cuando los parámetros anteriores no son consistentes se avisa de que está prohibida la importación.
  
- **Función de cruce de puntos singulares en modo automático**:
    Ruta: Programa de enseñanza -> Periféricos -> Instrucciones LIN/ARC. 

    Descripción: Se añade la configuración de protección de movimiento "Cruce de puntos singulares".

- **Función de actualización automática del programa Lua del punto correspondiente tras registrar el punto con el botón del extremo**:
    Ruta: Programa de enseñanza -> Programación de programas -> Puntos de enseñanza.

    Descripción: Se añade la función de actualización automática del programa Lua del punto correspondiente tras registrar el punto con el botón del extremo.

- **Optimización de la interfaz de consulta de estado**:
    Ruta: Información de estado -> Consulta de estado.

    Descripción: Optimización de la UI y la interacción de la interfaz de consulta de estado.

- **Optimización de la interfaz de WebApp y del teach pendant**:
    Descripción: WebApp y el teach pendant añaden la visualización de la interfaz en ruso y chino tradicional.

- **Función de optimización de la interfaz de visualización de WebApp**:
    Descripción: La esquina inferior izquierda de la interfaz de WebApp añade la visualización de la versión de software y del modelo de robot.

- **Función de seguimiento láser con eje extendido**:
    Descripción: 1. El robot se mueve sincronizadamente con el eje externo y el láser realiza el seguimiento sincronizado bajo el sistema de coordenadas del eje externo. 2. El robot se mueve de forma asíncrona con el eje externo y el láser puede realizar el seguimiento bajo el sistema de coordenadas base del robot o bajo el sistema de coordenadas del eje externo.

- **Función de arrastre del punto de herramienta basada en el sensor de fuerza**:
    Descripción: En la interfaz web, al configurar el sistema de coordenadas de referencia FT como sistema de coordenadas personalizado y activar el arrastre asistido por sensor de fuerza, el robot se mueve a lo largo del sistema de coordenadas de herramienta establecido.

- **Función CNDE del robot**:
    Descripción: El cliente puede, mediante CNDE, obtener la realimentación de estado del robot y enviar datos de control al robot (comunicación UDP); el período de realimentación de estado es configurable (1-200ms); el contenido de los datos de realimentación de estado del robot y el contenido de los datos de entrada del cliente para controlar el robot se pueden configurar libremente.

Versión V3.7.6
-----------------

Fecha: 2024-11-18

- **Optimización de la disposición de la página de configuración inicial**:
    Ruta: Configuración inicial.
  
    Descripción: Optimización de la interfaz de configuración de herramienta, de la interfaz de configuración de carga y de la visualización de algunos iconos de función.

- **Optimización de la interacción de la función de configuración del eje extendido de periféricos de WebApp**:
    Ruta: Configuración inicial -> Periféricos -> Eje extendido.
  
    Descripción: Optimización de la disposición y la interacción de la interfaz del eje extendido.

- **Optimización de la función del registro del sistema**:
    Ruta: Información de estado -> Registro del sistema.
  
    Descripción: Se añade la visualización paginada del registro y la distinción de categorías de operación detalladas del registro.
  
- **Función de pulido de fuerza constante transversal en dirección XY**:
    Ruta: Programa de enseñanza -> Programación de programas -> Conjunto de control de fuerza -> Instrucción F/T_Control.
  
    Descripción: Se añade el parámetro "Radio del disco de pulido", que permite realizar movimientos repetidos en línea recta/curva adheridos a la superficie de la pieza.
  
- **Función de movimiento de captación por láser**:
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Generación de puntos de intersección.
  
    Descripción: La función de obtención de coordenadas del punto de intersección mediante búsqueda de posición de tres y cuatro puntos añade el uso de instrucciones de script lua.
    
- **Configuración del eje externo - función de carro de dos grados de libertad**:
    Ruta: Configuración inicial -> Periféricos -> Eje extendido.
  
    Descripción: Se añade el esquema de eje extendido "Carro de dos grados de libertad"; el robot se comunica mediante UDP con el PLC y este controla el carro de dos grados de libertad mediante EtherCat.
   
- **Función del método de calibración del TCP basado en la herramienta de placa plana**:
    Ruta: Configuración inicial -> Sistema de coordenadas -> Coordenadas de herramienta.
  
    Descripción: Se añade el método de calibración del sistema de coordenadas "Calibración con herramienta de placa plana".
         
- **Función de programas en segundo plano del robot**:
    Ruta: Programa de enseñanza -> Programación de programas.
  
    Descripción: El programa en segundo plano puede obtener con normalidad los datos de la interfaz de I/O, incluidas las I/O del sistema, modbus y las I/O extendidas.
   
- **Función de evitación automática de puntos singulares en la trayectoria del robot**:
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción de línea recta Lin/arco Arc.
  
    Descripción: Se añade la configuración de protección de movimiento "Evitación de puntos singulares".
   
- **Función de adaptación del extremo de la pinza rotativa**:
    Ruta: Configuración inicial -> Periféricos -> Pinza.
  
    Descripción: Se añade la configuración de códigos de función relacionados con la pinza rotativa.
       
- **Instrucción de esclavo de protocolo personalizado**:
    Ruta: Modo remoto.
  
    Descripción: Se añade la configuración "Protocolo de esclavo del controlador".
    
- **Función de búsqueda de posición del alambre de soldadura por comunicación UDP**:
  
    Descripción: El robot puede, mediante la IO extendida UDP, realizar el control de inicio y parada de la búsqueda de posición del alambre de soldadura y obtener la señal de éxito de la búsqueda de posición del alambre de soldadura.
    
- **Optimización de la función del paquete de copia de seguridad**:

    Descripción: Soporte de importación y uso de paquetes de datos de versiones antiguas (paquetes de datos de QX 3.6.1 y posteriores).

- **Optimización de la función de restauración de configuración de fábrica**: Se añade la verificación de archivos, aumentando la estabilidad de la restauración de configuración de fábrica del sistema.

    Descripción: Se añade la verificación de archivos, aumentando la estabilidad de la restauración de configuración de fábrica del sistema.

- **Optimización de la función de actualización**:

    Descripción: Las versiones QX3.6.9 y posteriores se pueden actualizar directamente a QX3.7.6, conservando tras la actualización los datos de usuario de la versión actual.

- **Función de degradación de página**:
  
    Descripción: La página de WebApp admite la degradación a cualquier versión de QX3.6.9 y posteriores, conservando tras la degradación los datos de usuario de la versión actual.

Versión V3.7.5
-----------------

Fecha: 2024-09-30

- **Función de ajuste de la velocidad angular de transición de actitud de envolvente de esquina**:
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción de línea recta Lin.
  
    Descripción: Se añade la configuración de protección de movimiento "Velocidad angular de punto de transición ajustable".
       
- **Función de soldadura multicapa y multipasada con seguimiento de arco**:
    Ruta: Aplicaciones auxiliares -> Paquete de proceso -> Biblioteca de expertos en soldadura -> Soldadura multicapa y multipasada.
  
    Descripción: Se añaden las configuraciones "Función de oscilación de la primera capa" y "Función de seguimiento de arco".
  
- **Función de configuración del eje extendido 485**:
    Ruta: Configuración inicial -> Periféricos -> Eje extendido.
  
    Descripción: Se añade la configuración "Aceleración y parada de emergencia".
  
- **Función de calibración automática del TCP de la herramienta del robot (utillaje de sensor de fibra óptica de fabricación propia)**:
    Ruta: Configuración inicial -> Básico -> Coordenadas de herramienta.
  
    Descripción: Se añade la calibración del sistema de coordenadas "Calibración automática fotoeléctrica".
  
- **Función de configuración multilingüe del teach pendant**:
    Ruta: Página de inicio de sesión.
  
    Descripción: Se añade la configuración "Conmutación de idioma".
    
Versión V3.7.4
-----------------

Fecha: 2024-08-09

- **Función de software de protocolo abierto del extremo basado en lua (parte de pinza)**:
    Ruta: Configuración inicial -> Periféricos -> Pinza.
  
    Descripción: Se añade la configuración "Habilitación del protocolo del extremo".
       
- **Función de oscilación en diente de sierra inclinado**:
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción de oscilación Weave.
  
    Descripción: Se añade la configuración del parámetro "Ángulo de azimut de la dirección de oscilación".
       
- **Función de optimización del paquete de proceso de soldadura del robot**:
    Ruta: Configuración inicial -> Periféricos -> Máquina de soldar -> Configuración de la máquina de soldar.
  
    Descripción: Se añade la configuración "Parámetros del proceso de soldadura".
       
- **Función de tratamiento de sobrevelocidad articular de la instrucción Lin**:
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción de línea recta Lin.
  
    Descripción: Se añade la configuración de protección de movimiento "Protección contra sobrevelocidad articular".
       
Versión V3.7.3
-----------------

Fecha: 2024-06-28

- **Función de control del robot mediante esclavo Modbus**:
    Ruta: Programa de enseñanza -> Programación de programas -> ModbusTCP.
  
    Descripción: Se añade la configuración "Controlador esclavo".
       
- **Función de tipo de parada de emergencia**: 
    Ruta: Configuración inicial -> Seguridad -> Parada de emergencia.
  
    Descripción: Se añaden los tipos de parada "tipo 1a, tipo 2a y tipo 2".
       
Versión V3.7.2
-----------------

Fecha: 2024-06-07

- **Función de configuración del protocolo abierto del extremo basado en Lua**:
    Ruta: Configuración inicial -> Periféricos -> Herramienta del extremo -> Protocolo abierto.
  
    Descripción: Se añade la configuración "Protocolo abierto".
     
- **Función de instrucción de control AO de movimiento**:
    Ruta: Programa de enseñanza -> Programación de programas.
  
    Descripción: Se añade la "Instrucción AO de movimiento".
     
- **Función de arrastre mixto de fuerza de seis dimensiones e impedancia articular**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Bloqueo de arrastre.
  
    Descripción: Se añade el "Arrastre mixto de fuerza de seis dimensiones e impedancia articular".
     
- **Función de estrategia de respuesta tras la colisión**: 
    Ruta: Configuración inicial -> Básico -> Articulación -> Nivel de colisión.
  
    Descripción: Se añade la configuración "Estrategia de colisión".
     
- **Función de primera activación del robot**: 
    Ruta: Configuración de inicio de sesión.
  
    Descripción: Se añade la función de verificación de la primera activación del robot.
     
Versión V3.7.1
-----------------

Fecha: 2024-05-10

- **Función de bloqueo de la interfaz web**: 
    Ruta: Configuración del sistema -> Información personalizada.
  
    Descripción: Se añade la configuración "Bloqueo de pantalla de la interfaz web". 
     
- **Función de obtención de coordenadas del punto de intersección mediante búsqueda de posición de tres y cuatro puntos**: 
    Ruta: Aplicaciones auxiliares -> Aplicación de herramientas -> Generación de puntos de intersección.
  
    Descripción: Se añade la "Función de obtención de coordenadas del punto de intersección mediante búsqueda de posición de tres y cuatro puntos".
     
- **Función de optimización de la actitud del movimiento de soldadura por segmentos**:
    Ruta: Programa de enseñanza -> Programación de programas -> Instrucción de soldadura por segmentos Segment.
  
    Descripción: Se añade la configuración "Modo de soldadura por segmentos".
  
- **Función de muro virtual basada en sensor de fuerza**:
    Ruta: Configuración inicial -> Periféricos -> Sensor de fuerza; Aplicaciones auxiliares -> Aplicación de herramientas -> Bloqueo de arrastre.
  
    Descripción: La configuración de periféricos del extremo añade los parámetros de configuración relacionados con el "Sensor de fuerza"; el bloqueo asistido por sensor de fuerza añade la configuración "Coeficiente de inercia".
  
- **Nueva función de combinación SmartTool + sensor de fuerza**:
    Ruta: Configuración inicial -> Periféricos -> Empuñadura de soldadura.
  
    Descripción: Se añade la configuración de funciones de las teclas.