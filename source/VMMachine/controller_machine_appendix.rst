Apéndice
===================

Apéndice 1: Habilitar la virtualización en la BIOS
-----------------------------------------------------------------------

El proceso para habilitar la virtualización puede variar según el modelo de ordenador; a continuación se toma como ejemplo la serie Lenovo ThinkPad con Windows 10:

- Abrir la configuración del ordenador, seleccionar Actualización y seguridad.

.. image:: controller_virtual_machine/013.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/014.png
   :width: 4in
   :align: center

- Seleccionar "Recuperación".

.. image:: controller_virtual_machine/015.png
   :width: 4in
   :align: center

- Seleccionar "Reiniciar ahora".

.. image:: controller_virtual_machine/016.png
   :width: 4in
   :align: center

- Seleccionar "Solucionar problemas".
  
.. image:: controller_virtual_machine/017.png
   :width: 4in
   :align: center

- Seleccionar "Opciones avanzadas".

.. image:: controller_virtual_machine/018.png
   :width: 4in
   :align: center

- Seleccionar Configuración de firmware UEFI.

.. image:: controller_virtual_machine/019.png
   :width: 4in
   :align: center

- Seleccionar "Reiniciar".

.. image:: controller_virtual_machine/020.png
   :width: 4in
   :align: center

- Seleccionar "Virtualization" dentro de "Security".

.. image:: controller_virtual_machine/021.png
   :width: 4in
   :align: center

- Seleccionar "Enabled", pulsar "Enter" para confirmar.

.. image:: controller_virtual_machine/022.png
   :width: 4in
   :align: center

- Pulsar "F10", seleccionar "Yes", pulsar "Enter" para guardar los cambios.

.. image:: controller_virtual_machine/023.png
   :width: 4in
   :align: center

Apéndice 2: Añadir una tarjeta de red virtual (adaptador de red de bucle invertido)
------------------------------------------------------------------------------------------

1. Abrir el Administrador de dispositivos, pulsar "Tecla Windows-X", seleccionar "Administrador de dispositivos".
   
.. image:: controller_virtual_machine/024.png
   :width: 4in
   :align: center

2. Añadir un adaptador de red.

.. image:: controller_virtual_machine/025.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/026.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/027.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/028.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/029.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/030.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/031.png
   :width: 4in
   :align: center
   
3. Ver la tarjeta de red virtual, pulsar "Tecla Windows-X", seleccionar "Conexiones de red".

.. image:: controller_virtual_machine/032.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/033.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/034.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/035.png
   :width: 4in
   :align: center
   
4. Configurar la red del adaptador de bucle invertido.

- Dirección IP: 192.168.58.XXX (basta con estar en el mismo segmento de red que 192.168.58.2).
- Máscara de subred: 255.255.255.0.

.. image:: controller_virtual_machine/012.png
   :width: 6in
   :align: center

5. Abrir la configuración de red de Virtualbox, seleccionar "Adaptador de red de bucle invertido" como nombre de la tarjeta de red e iniciar la máquina virtual.

.. image:: controller_virtual_machine/013.png
   :width: 6in
   :align: center

Apéndice 3: Permisos de root
--------------------------------------

Una vez instalado Ubuntu, el usuario root del sistema Ubuntu no puede iniciar sesión de forma predeterminada y su contraseña está vacía. Si se desea iniciar sesión con el usuario root, primero se debe establecer una contraseña para el usuario root.

1. Abrir la terminal, introducir sudo passwd root, luego pulsar Enter e introducir la contraseña varias veces; se mostrará que la contraseña se ha establecido correctamente.

.. image:: controller_virtual_machine/057.png
   :width: 6in
   :align: center

2. En la terminal, continuar introduciendo el comando su - root para cambiar de usuario, pulsar Enter e introducir la contraseña.

.. warning:: Al introducir el comando es imprescindible escribir "-"; la opción "-" indica que se cambian también las variables de entorno, y "-" no debe omitirse en ningún caso.

.. image:: controller_virtual_machine/058.png
   :width: 6in
   :align: center

Apéndice 4: Comandos básicos de docker
--------------------------------------

1. Comando de ayuda de docker :

.. code-block:: console
   :linenos:

   docker --help

2. Iniciar docker :

.. code-block:: console
   :linenos:

   systemctl start docker

3. Detener docker :

.. code-block:: console
   :linenos:

   systemctl stop docker

4. Reiniciar docker :

.. code-block:: console
   :linenos:

   systemctl restart docker

5. Configurar docker para que se inicie automáticamente con el servicio :

.. code-block:: console
   :linenos:

   systemctl enable docker

6. Ver el estado de ejecución de docker :

.. code-block:: console
   :linenos:

   systemctl status docker
   --si está en ejecución, tras introducir el comando se verá active en verde

7. Imágenes de docker :

.. code-block:: console
   :linenos:

   docker images：lista las imágenes ya descargadas, ver imágenes
   docker rmi id o nombre de imagen：eliminar la imagen local
   docker rmi -f id o nombre de imagen: eliminar la imagen
   docker build：construir una imagen
   docker search id o nombre de imagen：buscar la imagen por palabra clave en el repositorio de Docker Hub
   docker pull id o nombre de imagen：descargar la imagen del repositorio
   docker images：lista las imágenes ya descargadas, ver imágenes
   docker rmi id o nombre de imagen：eliminar la imagen local
   docker rmi -f id o nombre de imagen: eliminar la imagen
   docker build：construir una imagen

8. Contenedores de docker :

.. code-block:: console
   :linenos:

   docker ps：lista los contenedores en ejecución
   docker ps -a ： ver todos los contenedores, incluidos los que no están en ejecución
   docker stop id o nombre de contenedor：detener el contenedor
   docker kill id de contenedor：forzar la detención del contenedor
   docker start id o nombre de contenedor：iniciar un contenedor detenido
   docker inspect id de contenedor：ver toda la información del contenedor
   docker container logs id de contenedor：ver los registros del contenedor
   docker top id de contenedor：ver los procesos dentro del contenedor
   docker exec -it id de contenedor /bin/bash：entrar en el contenedor
   exit：salir del contenedor
   docker rm id o nombre de contenedor：eliminar un contenedor detenido
   docker rm -f id de contenedor：eliminar un contenedor en ejecución
   docker exec -it ID de contenedor sh :entrar en el contenedor