Asistente de creación
=========================

.. toctree:: 
   :maxdepth: 6

El "Asistente de creación" es una herramienta de FRCap-Tools; mediante esta herramienta puede inicializar de forma cómoda y rápida un proyecto FRCap introduciendo una pequeña cantidad de parámetros.

Configuración de parámetros
-----------------------------------

La creación de FRCap requiere principalmente dos tipos de parámetros: la información básica de FRCap y las configuraciones de cada nivel. A continuación se describen por separado.

Información básica
+++++++++++++++++++++++++++

La información básica incluye el "Nombre del plugin", el "Autor del plugin" y la "Descripción del plugin".

Nombre del plugin:

- Campo obligatorio;
- No se limitan los caracteres ni la longitud de los caracteres introducidos; no se permite introducir espacios;
- Se recomienda que el nombre no supere los 7 caracteres CKJ (chino, japonés, coreano, etc.) o 10 letras latinas en mayúscula o 14 letras latinas en minúscula (inglés, francés, etc.);
- Ejemplos recomendados:

  - Paletizadora Palletizer;
  - Software de proceso de pulido;
  - Device Config;
  - HELLO FRCAP.

Autor del plugin:

- Campo obligatorio;
- No se limitan los caracteres ni la longitud de los caracteres introducidos; por ejemplo, puede introducir su nombre personal, el nombre de la empresa, etc.;
- Ejemplos recomendados:

  - Zhang San
  - Franklin Peter
  - FAIR Innovation (Suzhou) Robot Systems Co., Ltd.

Descripción del plugin:

- Campo no obligatorio;
- No se limitan los caracteres ni la longitud de los caracteres introducidos; basta con describir brevemente su plugin.

Configuración avanzada
------------------------

Tipo de plugin:

- Campo obligatorio;
- Las opciones de tipo son "Configuración" y "Aplicación".
- "Configuración" se recomienda para FRCap que implementan operaciones de configuración y control relativamente sencillas, como el establecimiento de parámetros y la operación mediante botones. Tras su importación, se utiliza en "Aplicaciones auxiliares"->"FRCap" de WebApp.
- "Aplicación" se recomienda para FRCap que implementan escenarios de proceso complejos, como escenarios de paletizado, procesos de soldadura y otras aplicaciones del sector. Tras su importación, se utiliza directamente en "Aplicaciones auxiliares" de WebApp.

Icono del plugin:

- Campo no obligatorio;
- El icono puede ser el logotipo de su empresa o cualquier icono que desee utilizar; tenga en cuenta los derechos de autor; nuestra empresa no se hace responsable de ningún problema de derechos de autor que se produzca por cualquier motivo;
- Si no ha cargado un icono, el proyecto FRCap exportado utiliza por defecto el icono del logotipo "FAIRINO" de nuestra empresa, que puede sustituir y modificar en la carpeta public del directorio del proyecto. Dicho icono es solo una indicación de inicialización; no utilice directamente el logotipo "FAIRINO" en ningún escenario comercial.


Descarga
-------------
Una vez completada la configuración de todos los parámetros anteriores y creado correctamente FRCap, se saltará a la página de descarga. Debe confirmar que el nombre es correcto para poder descargar el proyecto FRCap creado al ordenador local para el trabajo de desarrollo posterior y su uso en la construcción.

El plugin descargado tiene el formato comprimido ".tar.gz".

En el sistema Windows recomendamos utilizar el software 7-Zip para descomprimirlo.

En el sistema Linux se puede descomprimir en la terminal con la siguiente instrucción.

.. code-block:: c++
   :linenos:

    tar -zxvf frcap_{FRCapName}.tar.gz