..  Copyright (C) Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-7-
   :start: 1

👩‍💻 Imprimiendo Resultados Intermedios
========================================

En este libro de texto, proporcionamos la herramienta de codelens para que pueda avanzar
el programa y observe lo que sucede cada vez que el intérprete de Python evalúa una línea
¿Qué pasaría si no tuvieras codelens?, ¿qué haría?

En ese caso, las declaraciones impresas son su mejor amigo. Pueden mostrarle cuál es el valor de
algo. Esto es especialmente útil en el caso de escribir para bucles o acumular
un valor. Si algo va mal, puede comparar lo que espera que suceda con lo que
en realidad está sucediendo.

.. activecode:: ac6_7_1

   w = range(10)

   tot = 0
   for num in w:
       tot += num
   print(tot)

Digamos que no estábamos seguros de qué ``num`` se asignaba cada vez que iteramos. Una forma de averiguarlo
sería agregar una declaración de impresión dentro del bucle for para ver.

.. activecode:: ac6_7_2

   w = range(10)

   tot = 0
   for num in w:
       print(num)
       tot += num
   print(tot)

Si también quisiéramos ver lo que le estaba sucediendo a ``tot``, ¡también podríamos imprimir eso en el bucle for!

.. activecode:: ac6_7_3
   
   w = range(10)


   tot = 0
   for num in w:
       print(num)
       tot += num
       print(tot)
   print(tot)

Finalmente, si quisiéramos facilitar la comprensión de estos números, ¡podríamos agregar más a las declaraciones impresas
para que sean más fáciles de leer!

.. activecode:: ac6_7_4
   
   w = range(10)

   tot = 0
   print("***** Before the For Loop ******")
   for num in w:
       print("***** A New Loop Iteration ******")
       print("Value of num:", num)
       tot += num
       print("Value of tot:", tot)
   print("***** End of For Loop *****")
   print("Final total:", tot)
       