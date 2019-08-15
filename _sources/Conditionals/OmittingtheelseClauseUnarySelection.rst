..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: condition-7-
   :start: 1

.. index:: unary selection
   else; omitted

Omitir la cláusula ``else``: Selección Unaria
---------------------------------------------

.. video:: unaryselection
   :controls:
   :thumb: ../_static/unaryselection.png

   http://media.interactivepython.org/thinkcsVideos/unaryselection.mov
   http://media.interactivepython.org/thinkcsVideos/unaryselection.webm

.. sidebar::  Diagrama de flujo de un **if** sin **else**

   .. image:: Figures/flowchart_if_only.png

Otra forma de la declaración ``if`` es aquella en la que la cláusula ``else`` se omite por completo. Esto crea lo que
a veces se llama **selección unaria**. En este caso, cuando la condición se evalúa como ``True``, las declaraciones
son ejecutadas. De lo contrario, el flujo de ejecución continúa a la declaración después del cuerpo del ``if``.

.. activecode:: ac7_7_1

    x = 10
    if x < 0:
        print("El número negativo ",  x, " no es válido aquí.")
    print("Esto se imprimirá siempre")

¿Qué se imprimiría si el valor de ``x`` es negativo? Intentalo.

**Revisa tu entendimiento**

.. mchoice:: question7_7_1
   :answer_a: Salida a
   :answer_b: Salida b
   :answer_c: Salida c
   :answer_d: Causará un error porque cada if debe tener una cláusula else.
   :correct: b
   :feedback_a: Como -10 es menor que 0, Python ejecutará el cuerpo de la declaración if aquí.
   :feedback_b: Python ejecuta el cuerpo del bloque if así como la declaración que sigue al bloque if.
   :feedback_c: Python también ejecutará la declaración que sigue al bloque if (porque no está encerrado en un bloque else, sino simplemente una declaración normal).
   :feedback_d: Es válido tener un bloque if sin el bloque else correspondiente (aunque no puede tener un bloque else sin el bloque if correspondiente).
   :practice: T

   ¿Qué imprime el siguiente código?

   .. code-block:: python
     
     x = -10
     if x < 0:
         print("El número negativo ",  x, " no es válido aquí")
     print("Esto se imprimirá siempre")

   ::

     a.
     Esto se imprimirá siempre

     b.
     El número negativo -10 no es válido aquí
     Esto se imprimirá siempre

     c.
      El número negativo -10 no es válido aquí


.. mchoice:: question7_7_2
   :answer_a: No
   :answer_b: Sí
   :correct: b
   :feedback_a: Todos los demás bloques deben tener exactamente un bloque if correspondiente. Si desea encadenar declaraciones if-else juntas, debe usar la construcción else if, descrita en la sección de condicionales encadenados.
   :feedback_b: Esto causará un error porque el segundo bloque else no está conectado a un bloque if correspondiente.
   :practice: T

   ¿El siguiente código causará un error?

   .. code-block:: python

     x = -10
     if x < 0:
         print("El número negativo ",  x, " no es válido aquí")
     else:
         print(x, " es un número positivo")
     else:
         print("Esto se imprimirá siempre")

