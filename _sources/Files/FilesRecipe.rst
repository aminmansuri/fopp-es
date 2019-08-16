..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-6-
   :start: 1

Pasos para leer y procesar un archivo
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Aquí hay una receta infalible para procesar el contenido de un archivo de texto. Si ha digerido completamente las secciones anteriores,
comprenderá que también hay otras opciones. Algunas de esas opciones son preferibles para algunas situaciones, y
los programadores de python prefieren algunos por razones de eficiencia. En este curso, sin embargo, siempre puedes tener éxito
siguiendo estos pasos.

#1. Abra el archivo usando ``with`` y ``open``.

#2. Use ``.readlines()`` para obtener una lista de las líneas de texto en el archivo.

#3. Use un bucle ``for`` para recorrer las cadenas de la lista, cada una de las cuales es una línea del archivo. En cada iteración, procese esa línea de texto

#4. Cuando haya terminado de extraer datos del archivo, continúe escribiendo su código fuera de la sangría. El uso de ``with`` cerrará automáticamente el archivo una vez que el programa salga del bloque with.

::

   fname = "yourfile.txt"
   with open(fname, 'r') as fileref:         # step 1
       lines = fileref.readlines()           # step 2
       for lin in lines:                     # step 3
           #algún código que hace referencia a la variable lin
   #algún otro código que no se base en fileref   # step 4


Sin embargo, esto no será bueno para usar cuando trabaje con datos grandes. Imagine trabajar con un archivo de datos que tiene 1000
filas de datos. Le llevaría mucho tiempo leer todos los datos y luego, si tuviera que repetirlos, aún más tiempo
sería necesario. Este sería un caso en el que los programadores prefieren otra opción por razones de eficiencia.

Esta opción implica iterar sobre el archivo en sí mientras itera sobre cada línea del archivo:

::

   fname = "yourfile.txt"
   with open(fname, 'r') as fileref:         # step 1
       for lin in fileref:                   # step 2
           ## algún código que hace referencia a la variable lin
   #algún otro código que no se base en fileref   # step 3
