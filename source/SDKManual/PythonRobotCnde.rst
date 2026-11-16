CNDE
=============

.. toctree:: 
    :maxdepth: 5

Configurar la retroalimentación de estado CNDE del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotRealtimeStateConfig(states: List[RobotState], period: int = 500) -> int:``"
    "Descripción", "Establecer la configuración predeterminada de CNDE (llamar antes de la conexión RPC)"
    "Parámetros obligatorios", "
    - ``states``：Lista de enumeraciones RobotState
    - ``period``：Período de datos (ms), rango 8-1000, por defecto 8ms
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo-errcode"

Añadir un estado del robot a la configuración de estado CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AddRobotRealtimeState(states: List[RobotState], ip: str = None) -> int:``"
    "Descripción", "Añadir una lista de estados CNDE sobre la configuración existente (admite mantenimiento dinámico y aislamiento por IP)"
    "Parámetros obligatorios", "
    - ``states``：Lista de enumeraciones RobotState, los estados a añadir
    - ``ip``：Opcional, especifica la IP del robot (para configuración aislada de múltiples robots; si no se proporciona, se modifica la configuración global)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo-errcode"

Eliminar un estado del robot de la configuración de estado CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``DeleteRobotRealtimeState(states: List[RobotState], ip: str = None) -> int:``"
    "Descripción", "Eliminar una lista de estados CNDE de la configuración existente (admite mantenimiento dinámico y aislamiento por IP)"
    "Parámetros obligatorios", "
    - ``states``：Lista de enumeraciones RobotState, los estados a eliminar
    - ``ip``：Opcional, especifica la IP del robot (para configuración aislada de múltiples robots; si no se proporciona, se modifica la configuración global)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo-errcode"

Establecer el período de retroalimentación de estado CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotRealtimeStatePeriod(period: int, ip: str = None) -> int:``"
    "Descripción", "Establecer el período de retroalimentación de estado CNDE (admite configuración global o aislamiento por IP)"
    "Parámetros obligatorios", "
    - ``period``：Período de datos (ms), rango 8-1000
    - ``ip``：Opcional, especifica la IP del robot (si no se proporciona, se modifica la configuración global)
    "
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo-errcode"

Obtener el conjunto de todos los estados de la retroalimentación de estado CNDE actual
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CNDEGetConfig(self) -> tuple:``"
    "Descripción", "Obtener el conjunto de todos los estados actuales"
    "Parámetros obligatorios", "Ninguno"
    "Parámetros predeterminados", "Ninguno"
    "Valor de retorno", "- Código de error éxito-0  fallo-errcode; estructura de resultado de configuración que contiene la lista de estados"

Ejemplo de código de uso de la retroalimentación de estado CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    from fairino.Robot import RobotState, SetRobotRealtimeStateConfig, DEFAULT_CNDE_STATES, AddRobotRealtimeState, DeleteRobotRealtimeState, SetRobotRealtimeStatePeriod
    import time

    # ==================== Parámetros de configuración global ====================
    ROBOT_IP = '192.168.58.2'       # Dirección IP del robot
    # ========== Test1: Prueba de configuración CNDE y obtención de datos =============
    # Pasos de la prueba:
    # 1. Establecer la configuración CNDE (JointCurPos, ToolCurPos, período de 20ms)
    # 2. Establecer la conexión RPC
    # 3. Imprimir los datos de las articulaciones y la pose TCP del robot
    # 4. Obtener la marca de tiempo y verificar el período
    # 5. Modificar la configuración (RobotMode, RbtEnableState, período de 10ms)
    # 6. Verificar que la nueva configuración surta efecto

    def test1_cnde_config_and_data():
        """Test1: Prueba de configuración CNDE y obtención de datos - verificar el establecimiento de la configuración y la actualidad de los datos"""
        print_separator("Test1: Prueba de configuración CNDE y obtención de datos")

        # ===== Paso 1: Establecer la configuración CNDE (JointCurPos, ToolCurPos, 20ms) =====
        print("\n[Paso 1] Establecer la configuración CNDE...")
        print("  Campos de configuración: JointCurPos, ToolCurPos")
        print("  Período de retroalimentación: 20ms")

        custom_states = [
            RobotState.JointCurPos,   # Posición actual de las articulaciones
            RobotState.ToolCurPos,    # Posición actual de la herramienta (TCP)
        ]

        rtn = SetRobotRealtimeStateConfig(custom_states, 20)
        if rtn != 0:
            print(f"✗ Error al establecer la configuración, código de error: {rtn}")
            return None
        print("✓ Configuración CNDE establecida correctamente")

        # ===== Paso 2: Establecer la conexión RPC =====
        print(f"\n[Paso 2] Establecer la conexión RPC ({ROBOT_IP})...")
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        # Verificar la configuración
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Conexión exitosa, configuración actual: {len(states)} campos, período {period}ms")
        else:
            print("✗ No se puede obtener la configuración CNDE")
            return robot

        # ===== Paso 3: Imprimir los datos de las articulaciones y la pose TCP =====
        print("\n[Paso 3] Imprimir los datos de las articulaciones y la pose TCP del robot...")
        print("  (Sugerencia: arrastre el robot para observar los cambios en los datos)")
        print("  Presione Ctrl+C para detener la impresión de datos")
        print("  (Utilice Wireshark para capturar paquetes y verificar el período real de los datos)\n")

        sample_count = 0
        try:
            while sample_count < 100:  # Recoger 100 muestras
                pkg = robot.robot_state_pkg

                # Imprimir cada 10 fotogramas
                if sample_count % 10 == 0:
                    print(f"--- Muestra #{sample_count} ---")
                    print(f"  Posición de articulaciones (deg): [{', '.join([f'{x:.3f}' for x in pkg.jt_cur_pos])}]")
                    print(f"  Pose TCP (mm/deg): [{', '.join([f'{x:.3f}' for x in pkg.tl_cur_pos])}]")
                    print(f"  Contador de tramas actual: {pkg.frame_cnt}")
                    print()

                sample_count += 1
                time.sleep(0.02)  # 20ms

        except KeyboardInterrupt:
            print("\n  Impresión de datos interrumpida por el usuario")

        # Cerrar la conexión
        robot.CloseRPC()
        time.sleep(1)

        # ===== Paso 4: Modificar la configuración y verificar =====
        print("\n[Paso 4] Modificar la configuración CNDE...")
        print("  Nuevos campos de configuración: RobotMode, RbtEnableState")
        print("  Nuevo período de retroalimentación: 10ms")

        new_states = [
            RobotState.RobotMode,
            RobotState.RbtEnableState,
        ]

        # Establecer la nueva configuración
        rtn = SetRobotRealtimeStateConfig(new_states, 10)
        if rtn != 0:
            print(f"✗ Error al establecer la nueva configuración, código de error: {rtn}")
            return robot
        print("✓ Nueva configuración establecida correctamente")

        # Reconectar
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)

        # Verificar la nueva configuración
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Configuración actual: {[s.name for s in states]}")
            print(f"✓ Período actual: {period}ms")

            if period == 10:
                print("✓ Verificación de modificación de configuración superada (el período ha cambiado a 10ms)")
            else:
                print(f"⚠ El período no ha surtido efecto (se esperaba 10ms, real {period}ms)")

            # Imprimir los nuevos datos
            pkg = robot.robot_state_pkg
            print(f"\n[Datos de la nueva configuración]")
            print(f"  robot_mode: {pkg.robot_mode}")
            print(f"  rbtEnableState: {pkg.rbtEnableState}")
        else:
            print("✗ No se puede obtener la nueva configuración")

        print("\n✓ Test1 completado")
        return robot


    if __name__ == "__main__":
        test1_cnde_config_and_data()


    # ======== Test2: Prueba de adición/eliminación de campos de estado ====================
    # Función: Probar AddRobotRealtimeState() y DeleteRobotRealtimeState()
    # Pasos de la prueba:
    #   1. Utilizar AddRobotRealtimeState() para añadir SpeedScaleManual y SpeedScaleAuto
    #   2. Conectar el robot e imprimir la velocidad global en modo manual/automático
    #   3. Modificar la velocidad global en WebApp y observar los cambios en los datos del SDK
    #   4. Utilizar DeleteRobotRealtimeState() para eliminar los campos añadidos
    #   5. Reconectar y verificar si los valores de velocidad son 0 (los campos ya no se actualizan)


    def test2_add_delete_state():
        """Test2: Prueba de adición/eliminación de campos de estado - verificar la adición y eliminación dinámica de estados CNDE"""
        print_separator("Test2: Prueba de adición/eliminación de campos de estado")

        # ===== Paso 1: Añadir los campos SpeedScaleManual y SpeedScaleAuto =====
        print("\n[Paso 1] Utilizar AddRobotRealtimeState() para añadir los campos de proporción de velocidad...")
        print("  Campos a añadir: SpeedScaleManual, SpeedScaleAuto")

        rtn = AddRobotRealtimeState([
            RobotState.SpeedScaleManual,
            RobotState.SpeedScaleAuto,
        ])

        if rtn != 0:
            print(f"✗ Error al añadir campos, código de error: {rtn}")
            return None
        print("✓ Campos añadidos correctamente")

        # ===== Paso 2: Establecer la conexión RPC e imprimir la velocidad =====
        print(f"\n[Paso 2] Establecer la conexión RPC ({ROBOT_IP})...")
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)  # Esperar la conexión y la recepción de datos

        # Verificar la configuración
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Conexión exitosa, configuración actual: {len(states)} campos")
            # Comprobar si contiene los campos añadidos
            has_manual = RobotState.SpeedScaleManual in states
            has_auto = RobotState.SpeedScaleAuto in states
            if has_manual and has_auto:
                print("✓ Verificación de configuración superada: SpeedScaleManual y SpeedScaleAuto añadidos")
            else:
                print(f"⚠ Advertencia de verificación de configuración: Manual={has_manual}, Auto={has_auto}")
        else:
            print("✗ No se puede obtener la configuración CNDE")

        # Imprimir los datos de velocidad
        print("\n[Datos de velocidad actuales] (modifique la velocidad global en WebApp para observar los cambios)")
        print("  Sugerencia: arrastre el robot para habilitarlo y cambie entre modo manual/automático para observar el valor de velocidad")
        print("  Presione Ctrl+C para detener la impresión de datos\n")

        sample_count = 0
        try:
            while sample_count < 100:  # Recoger 100 muestras (unos 10 segundos, con intervalo de 100ms)
                pkg = robot.robot_state_pkg
                print(f"  [{sample_count:3d}] SpeedScaleManual: {pkg.speedScaleManual:.2f}, "
                    f"SpeedScaleAuto: {pkg.speedScaleAuto:.2f}, "
                    f"Mode: {pkg.robot_mode}")
                sample_count += 1
                time.sleep(0.1)  # Intervalo de 100ms
        except KeyboardInterrupt:
            print("\n  Impresión de datos interrumpida por el usuario")

        print(f"\n✓ Recogida de datos completada, {sample_count} muestras en total")

        # ===== Paso 3: Desconectar =====
        print("\n[Paso 3] Desconectar la conexión actual...")
        robot.CloseRPC()
        time.sleep(1.0)  # Esperar a que CNDE se cierre completamente

        # ===== Paso 4: Eliminar los campos añadidos =====
        print("\n[Paso 4] Utilizar DeleteRobotRealtimeState() para eliminar los campos de proporción de velocidad...")
        rtn = DeleteRobotRealtimeState([
            RobotState.SpeedScaleManual,
            RobotState.SpeedScaleAuto,
        ])

        if rtn != 0:
            print(f"✗ Error al eliminar campos, código de error: {rtn}")
            return robot
        print("✓ Campos eliminados correctamente")

        # ===== Paso 5: Reconectar y verificar que los valores de los campos son 0 =====
        print(f"\n[Paso 5] Reconectar y verificar los valores de los campos tras la eliminación...")

        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)

        # Leer los valores de velocidad
        pkg = robot.robot_state_pkg
        manual_speed = pkg.speedScaleManual
        auto_speed = pkg.speedScaleAuto

        print(f"\n  SpeedScaleManual tras eliminación: {manual_speed:.2f}")
        print(f"  SpeedScaleAuto tras eliminación: {auto_speed:.2f}")

        # Verificar si son 0
        if manual_speed == 0 and auto_speed == 0:
            print("\n✓ Verificación de Test2 superada: los valores de velocidad son 0 tras eliminar los campos")
        else:
            print(f"\n⚠ Advertencia de Test2: los valores de velocidad no son cero tras eliminar los campos")

        print("\n✓ Test2 completado")
        return robot

    if __name__ == "__main__":
        test2_add_delete_state()