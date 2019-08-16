..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-1-
   :start: 1

Introducción: Trabajar con Archivos de Datos
============================================

Hasta ahora, los datos que hemos usado en este libro han sido codificados directamente en el programa o han sido
ingresados por el usuario. En la vida real, los datos residen en archivos. Por ejemplo, las imágenes con las que trabajamos en
la unidad de procesamiento finalmente vive en archivos en su disco duro. Páginas web y documentos de procesamiento de textos, y
la música son otros ejemplos de datos que viven en archivos. En este breve capítulo presentaremos para Python,
conceptos necesarios para usar datos de archivos en nuestros programas.

Para nuestros propósitos, asumiremos que nuestros archivos de datos son archivos de texto, es decir, archivos llenos de caracteres.
Los programas de Python que escribe se almacenan como archivos de texto. Podemos crear estos archivos en cualquiera de varias
formas. Por ejemplo, podríamos usar un editor de texto para escribir y guardar los datos. También podríamos descargar los datos
desde un sitio web y luego guardarlo en un archivo. Independientemente de cómo se cree el archivo, Python nos permitirá
manipular los contenidos.

En Python, debemos usar **open** *abrir* archivos antes de poder usarlos y **close** *cerrar* cuando hayamos terminado con ellos. Como
es de esperar, una vez que se abre un archivo, se convierte en un objeto Python al igual que todos los demás datos.
:ref:`Table 1<filemethods1a>` muestra las funciones y métodos que se pueden usar para abrir y cerrar archivos.

.. _filemethods1a:

================ ======================== =====================================================
**Nombre**        **Uso**                  **Explicación**
================ ======================== =====================================================
``open``          ``open(filename,'r')``    Abra un archivo llamado nombre de archivo y úselo para leer. Esto devolverá una referencia a un objeto de archivo.
``open``          ``open(filename,'w')``    Abra un archivo llamado nombre de archivo y úselo para escribir. Esto también devolverá una referencia a un objeto de archivo.
``close``        ``filevariable.close()``   El uso del archivo está completo.
================ ======================== =====================================================

Metas de aprendizaje
--------------------

* Comprender la estructura de los sistemas de archivos.
* Para entender como abrir archivos con diferentes modos
* Introducir archivos como otro tipo de secuencia sobre la que uno puede iterar
* Introducir el patrón de lectura/transformación/escritura
* Introducir asignación paralela a dos o tres variables

Objetivos
----------

* Demuestre que puede leer un solo valor de cada línea en un archivo
* Convertir la línea al valor apropiado
* Lea una línea y conviértala en valores múltiples usando división y asignación a múltiples variables

