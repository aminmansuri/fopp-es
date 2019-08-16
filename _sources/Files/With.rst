..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _with_page:

.. qnum::
   :prefix: files-12-
   :start: 1

Usando ``with`` para archivos
=============================

.. note:: 
   Esta sección es un tema un poco avanzado y se puede omitir fácilmente. Pero las declaraciones se están volviendo muy comunes y no está de más saberlas en caso de que te encuentres con una en la naturaleza.

Ahora que has visto y practicado un poco abrir y cerrar archivos, hay otro mecanismo que Python
proporciona para nosotros que limpia el cierre a menudo olvidado. Olvidar cerrar un archivo no necesariamente causa un tiempo de ejecución
error en los tipos de programas que normalmente escribe en un curso introductorio de programación. Sin embargo, si estás escribiendo un
programa que puede ejecutarse durante días o semanas a la vez que lee y escribe muchos archivos y puede tener problemas.

Python tiene la noción de un administrador de contexto que automatiza el proceso de hacer
operaciones comunes al comienzo de alguna tarea, así como la automatización de ciertas operaciones al final de alguna tarea. Para leer y escribir un archivo, la operación normal es abrir el archivo y asignarlo a una variable. Al final
de trabajar con un archivo, la operación común es asegurarse de que el archivo esté cerrado.

El Python con declaración facilita el uso de administradores de contexto. La forma general de una declaración with es::

    with <create some object that understands context> as <some name>:
        do some stuff with the object
        ...

Cuando el programa sale del bloque with, el administrador de contexto maneja las cosas comunes que normalmente ocurren al final, en nuestro caso cerrando un archivo. Un simple ejemplo aclarará toda esta discusión abstracta de contextos. Aquí están los contenidos de un archivo llamado "mydata.txt".

.. datafile:: mydata.txt

   1 2 3
   4 5 6

.. activecode:: ac9_12_1
   :nocodelens:
   :available_files: mydata.txt
   
   with open('mydata.txt', 'r') as md:
       for line in md:
           print(line)
   # continue con otro código

La primera línea de la instrucción `with` abre el archivo y lo asigna a la variable ``md``. Luego podemos iterar sobre el archivo en cualquiera
de las formas habituales. Cuando terminamos, simplemente dejamos de sangrar y dejamos que Python se encargue de cerrar el archivo y
limpiar. La línea final ``print(md)``

Esto es equivalente al código que cierra específicamente el archivo al final, pero marca claramente el conjunto de código que puede usar el archivo abierto como un bloque sangrado, y asegura que el programador no se olvide de incluir la invocación .close()

.. activecode:: ac9_12_2
   :nocodelens:
   :available_files: mydata.txt
   
   md = open('mydata.txt', 'r')
   for line in md:
       print(line)
   md.close()
   # continue con otro código
    
