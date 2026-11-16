Terminología
============

.. toctree:: 
	:maxdepth: 5


**Categorías de parada**:

- **Parada de categoría 0**: cuando se corta la alimentación del robot, este deja de funcionar inmediatamente. Se trata de una parada no controlada; dado que cada articulación frena a la máxima velocidad, el robot puede desviarse de la trayectoria programada. Esta parada de protección solo puede utilizarse cuando se supera el límite de evaluación de seguridad o cuando se produce un error en la parte de evaluación de seguridad del sistema de control. Para más información, consulte ENISO13850:2008 o IEC60204-1:2006.
- **Parada de categoría 1**: cuando se alimenta el robot para detenerlo, el robot se detiene; una vez que el robot se ha detenido, se corta la alimentación. Se trata de una parada controlada; el robot sigue la trayectoria programada. La alimentación se corta un segundo después o una vez que el robot se ha detenido por completo. Para más información, consulte ENISO13850:2008 o IEC60204-1:2006.
- **Parada de categoría 2**: parada controlada con el robot alimentado. El robot detiene todos los movimientos en un segundo. El accionamiento del sistema de control de evaluación de seguridad permite que el robot permanezca en la posición de parada. Para más información, consulte IEC60204-1:2006.

**Cobertura de diagnóstico (DC)**: se utiliza para medir la eficacia del diagnóstico implementado para alcanzar el nivel de prestaciones evaluado. Para más información, consulte ENISO13849-1:2008.

**Integrador**: el integrador es el organismo que diseña la instalación final del robot. El integrador es responsable de realizar la evaluación final de riesgos y debe garantizar que la instalación final cumpla la legislación y normativa locales.

**Tiempo medio hasta el fallo peligroso (MTTFd)**: el tiempo medio hasta el fallo peligroso (MTTFd) es el valor obtenido mediante cálculo y comprobación para alcanzar el nivel de prestaciones evaluado. Para más información, consulte ENISO13849-1:2008.

**Evaluación de riesgos**: la evaluación de riesgos es el proceso completo de identificación de todos los riesgos y de reducción de estos a un nivel adecuado. La evaluación de riesgos debe documentarse y archivarse. Para más detalles, consulte ISO12100.

**Nivel de prestaciones**: el nivel de prestaciones (Performance Level, PL) es un nivel discreto que describe la capacidad de las distintas partes relacionadas con la seguridad de un sistema de control para ejecutar una función de seguridad en condiciones predecibles. PLd es la segunda clasificación de fiabilidad más alta; significa que la función de seguridad es bastante fiable. Para más información, consulte EN ISO13849-1:2008.

**Brida de conexión**: estructura utilizada para conectar herramientas externas, generalmente denominada brida.

**Extremo del robot**: el último eje del robot o el punto central de la brida de conexión.

**Punto central de la herramienta (TCP)**: el punto central de la herramienta es el punto característico de la herramienta del robot y es el punto de control del sistema del robot; de fábrica se sitúa por defecto en el último eje de movimiento o en el centro de la brida de conexión. El punto central de la herramienta de cada herramienta incluye la traslación y la rotación establecidas respecto al centro de la brida de salida de la herramienta. Las coordenadas de posición X, Y, Z determinan la posición del punto central de la herramienta, y RX, RY, RZ determinan la orientación de la herramienta. Cuando todos estos valores son cero, el centro de la herramienta coincide con el punto central de la brida de conexión.

**Punto de pose de la herramienta (TCF)**: sobre la base del punto central de la herramienta TCP, refleja la actitud del sistema de coordenadas de la herramienta respecto al sistema de coordenadas del eslabón del extremo.

**Sistema de coordenadas base**: el origen del sistema de coordenadas base se define generalmente en el punto central entre el primer eje del robot y la superficie de montaje; el eje x apunta hacia delante y, en la dirección axial, el eje y se determina según la regla de la mano derecha.

**Sistema de coordenadas mundial**: sistema de coordenadas fijo establecido en la celda de trabajo o en la estación de trabajo. Cuando solo hay un robot, este sistema de coordenadas puede considerarse coincidente con el sistema de coordenadas base; cuando hay varios robots o dispositivos externos, el sistema de coordenadas mundial puede proporcionar un sistema de referencia único para estos dispositivos; su posición concreta puede especificarse arbitrariamente siempre que se cumpla la premisa de facilitar la calibración de los sistemas de coordenadas de otros dispositivos.

**Sistema de coordenadas articular**: el sistema de coordenadas articular es el sistema de coordenadas de las articulaciones del robot; bajo el sistema de coordenadas articular, cada eje del robot puede realizar movimientos individuales en sentido positivo o negativo dentro de los límites. Es aplicable cuando se necesita realizar movimientos de gran amplitud del robot y no se exige la actitud del TCP del robot. El jog de un solo eje en el modo manual del robot se realiza bajo el sistema de coordenadas articular.

**Sistema de coordenadas de herramienta**: sistema de coordenadas utilizado para definir la posición del punto central de la herramienta y la actitud de la herramienta; cuando no está definido, el sistema de coordenadas de herramienta se sitúa por defecto en el centro de la brida de conexión. Tras instalar la herramienta, el TCP cambia y pasa a ser el centro del extremo de la herramienta.

**Sistema de coordenadas de herramienta externa**: sistema de coordenadas utilizado para definir la pose de una herramienta fijada en el exterior del robot.

**Eje extendido**: eje adicional añadido por necesidades de trabajo distinto de los ejes del cuerpo del robot; los ejes extendidos incluyen principalmente tipos como rieles deslizantes, mesas basculantes y equipos de servo adicionales.

**Modo manual**: en este modo, todos los movimientos del robot son controlados manualmente por el usuario, y las instalaciones de seguridad externas como cortinas de luz de seguridad y puertas de seguridad no surten efecto, para facilitar la depuración de proximidad.

**Modo automático**: este modo se utiliza generalmente para que el robot ejecute programas de enseñanza; en este momento las instalaciones de seguridad externas están activadas.

**Precisión de repetibilidad**: grado de coincidencia de la posición y la actitud medidas al repetir n veces la misma operación con el mismo método y en las mismas condiciones por parte del robot.

**Teach pendant**: unidad portátil conectada al sistema de control que se utiliza para programar el robot o hacer que este se mueva.