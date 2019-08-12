..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-5-
   :start: 1

Repetición con un bucle for
----------------------------

Algunos de los programas que hemos visto hasta ahora son un poco tediosos de escribir. Si queremos hacer un
patrón repetitivo en nuestros dibujos, entonces puede tomar muchas líneas de código. Afortunadamente, Python
tiene algunas maneras de facilitar este tipo de tarea. Por ahora obtendrá una breve vista previa de una estructura y función de control útil en Python que aprenderá más adelante.

La estructura de control se llama un bucle for. Si has aprendido otros lenguajes de programación
entonces puede estar familiarizado con lo que hace, pero la estructura puede ser nueva. Un bucle for permite
Python para ejecutar un programa de forma no lineal. En lugar de evaluar el código línea por línea hasta que llegue al final, una vez que el programa llegue a un ciclo for, le indicará al programa que ejecute un conjunto de líneas durante n número de veces. Una vez que el programa ha ejecutado el código en lugar del bucle for n veces, el programa continuará evaluando y ejecutando lo que esté debajo del bucle for.

Aquí es donde entra en juego la función ``rango``. Usando la función ``rango``, puede
especificar cuántas veces se ejecutará el contenido dentro del bucle for. Aquí hay una simple
demostración a continuación de cómo funcionará esto.

.. activecode:: ac3_5_1

   print("Esta línea se ejecutará primero")

   for _ in range(3):
       print("Esta línea se ejecutará tres veces")
       print("Esta línea también se ejecutará tres veces")

   print("¡Ahora estamos fuera del bucle!")

Hay algunas cosas a tener en cuenta aquí para cuando use esto más adelante. Primero, es que las dos declaraciones de impresión en la línea 4 y 5 se ejecutan tres veces, pero no imprimimos la línea 4
tres veces y luego imprima la línea 5 tres veces. En su lugar, imprimimos la línea 4, luego la línea 5. Una vez
esto se realiza iteraciones del bucle for o devuelve el programa al comienzo de for
bucle, y continúa imprimiendo las líneas 4 y 5 nuevamente hasta que las haya impreso un total
de tres veces

En segundo lugar, estas líneas se imprimieron con el mismo número que está dentro de la función ``Rango``.
Si nosotros queríamos imprimirlos más o menos veces, entonces solo tendríamos que cambiar el número
dentro de los paréntesis en la línea 3.

Finalmente, el espacio en blanco es importante aquí. Todas las declaraciones que fueron impresas
varias veces se sangraron bajo el bucle for. Una vez que dejamos de sangrar esas líneas,
entonces el programa estaba fuera del ciclo for y continuaría ejecutándose linealmente. Si
te gustaría ver la ejecución, ¡mira el código de arriba en codelens!

Ahora es el momento de combinar esto con el módulo Turtle. ¡Podemos hacer muchas cosas geniales si combinamos estas dos cosas! A continuación hay un código para hacer precisamente eso. Intente predecir lo que hará el programa antes de ejecutarlo.

.. activecode:: ac3_5_2

   import turtle
   wn = turtle.Screen()
   
   elan = turtle.Turtle()

   distance = 50
   for _ in range(10):
       elan.forward(distance)
       elan.right(90)
       distance = distance + 10

.. note::

    Pruébelo usted mismo en el espacio a continuación. ¿Qué puedes hacer?

    .. activecode:: ac3_5_3

       import turtle
       wn = turtle.Screen()
