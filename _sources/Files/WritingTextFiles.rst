..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-7-
   :start: 1

Escribir archivos de texto
--------------------------

Una de las tareas de procesamiento de datos más comúnmente realizadas es leer datos de un archivo,
manipúlelo de alguna manera y luego escriba los datos resultantes en un nuevo archivo de datos para usar
para otros fines más tarde. Para lograr esto, la función ``open`` discutida anteriormente también puede ser
utilizada para crear un nuevo archivo preparado para escribir. Note en:ref:`Table 1<filemethods1a>`
que la única diferencia entre abrir un archivo para escribir y abrir un archivo para leer es
el uso de la bandera ``'w'`` en lugar de la bandera ``'r'`` como segundo parámetro. Cuando abrimos
un archivo para escribir, un nuevo archivo vacío con ese nombre se crea y se prepara para aceptar nuestros
datos. Si un archivo existente tiene el mismo nombre, su contenido se sobrescribe. Como antes, la función devuelve una referencia al nuevo objeto de archivo.

:ref:`Table 2 <filemethods2a>` muestra un método adicional en objetos de archivo que no hemos usado
hasta ahora. El método ``write`` nos permite agregar datos a un archivo de texto. Recordemos que los archivos de texto
contienen secuencias de personajes. Usualmente pensamos que estas secuencias de personajes son las
líneas del archivo donde cada línea termina con el carácter de newline ``\n``. Ten mucho cuidado de
Tenga en cuenta que el método ``write`` toma un parámetro, un string. Cuando se invoca, los personajes del
string se agregará al final del archivo. Esto significa que es tarea del programador que
incluya los caracteres de nueva línea como parte de la cadena si lo desea.

Supongamos que se nos ha pedido que proporcionemos un archivo que contenga todos los números al cuadrado del 1
a 12.

Primero, necesitaremos abrir el archivo. Luego, recorreremos los números del 1 al
12, y al cuadrado cada uno de ellos. Este nuevo número deberá convertirse en una cadena, y
entonces se puede escribir en el archivo.

El siguiente programa resuelve parte del problema. Primero queremos asegurarnos de que hemos escrito el
código correcto para calcular el cuadrado de cada número.

.. activecode:: ac9_7_1

    for number in range(1, 13):
        square = number * number
        print(square)

Cuando ejecutamos este programa, vemos las líneas de salida en la pantalla. Una vez que estemos satisfechos
está creando la salida adecuada, el siguiente paso es agregar las piezas necesarias para producir
un archivo de salida y escriba las líneas de datos en él. Para comenzar, necesitamos abrir un nuevo archivo de salida
llamando a la función ``open`` , ``outfile = open("squared_numbers.txt",'w')``, usando el ``'w'``
bandera. Podemos elegir cualquier nombre de archivo que nos guste. Si el archivo no existe, se creará.
Sin embargo, si el archivo existe, se reiniciará como vacío y perderá cualquier
contenidos previos.

Una vez que el archivo ha sido creado, solo necesitamos llamar al método ``write`` pasando el string
que deseamos agregar al archivo. En este caso, el string ya se está imprimiendo, así que haremos
que simplemente cambie el ``print`` en una llamada al método ``write``. Sin embargo, hay un adicional
paso a seguir, ya que el método de escritura solo puede aceptar un string como entrada. Necesitaremos convertir
el número de un string. Luego, solo necesitamos agregar un caracter adicional al string. Los
el carácter de nueva línea debe concatenarse al final de la línea. Toda la línea ahora se convierte
``outfile.write(str(square)+ '\n')``. La declaración de impresión genera automáticamente una nueva línea
después de cualquier texto que salga, pero el método de escritura no lo hace automáticamente.
También debemos cerrar el archivo cuando hayamos terminado.

El programa completo se muestra a continuación.

.. note::

    Al igual que con la lectura de archivos, por razones de seguridad, el entorno de libro de texto interactivo de runestone no escribe archivos en el sistema de archivos en su computadora local. En una ventana de código activo, simulamos la escritura en un archivo. Se muestra el contenido del archivo escrito y puede realizar una lectura posterior del contenido de ese nombre de archivo. Si intenta sobrescribir un archivo integrado en la página, es posible que no lo permita; ¡no intentes ponerte demasiado exigente con nuestro simulador de sistema de archivos!

    A continuación, imprimimos los primeros 10 caracteres en la ventana de salida.


.. activecode:: ac9_7_2
    :nocodelens:

    filename = "squared_numbers.txt"
    outfile = open(filename, "w")

    for number in range(1, 13):
        square = number * number
        outfile.write(str(square) + "\n")

    outfile.close()

    infile = open(filename, "r")
    print(infile.read()[:10])

    
