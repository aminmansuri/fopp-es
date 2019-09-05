..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-13-
   :start: 1

Reasignación
------------

.. youtube:: G86akhNFHZA
    :divid: reassignmentvid
    :height: 315
    :width: 560
    :align: left


Como hemos mencionado anteriormente, es legal realizar más de una asignación a
misma variable Una nueva asignación hace que una variable existente se refiera a un nuevo valor
(y deja de referirte al antiguo valor).

.. activecode:: ac2_13_1

    bruce = 5
    print(bruce)
    bruce = 7
    print(bruce)


La primera vez que ``bruce`` es
impreso, su valor es 5 y la segunda vez, su valor es 7. La instrucción de asignación cambia
el valor (el objeto) al que se refiere ``bruce``.

Así es como se ve **la reasignación** en un diagrama de referencia:

.. image:: Figures/reassign1.png
   :alt: reassignment

Es importante tener en cuenta que en matemáticas, una declaración de igualdad siempre es cierta. Si ``a es igual a b``
ahora, entonces ``a siempre será igual a b``. En Python, una declaración de asignación puede hacer
dos variables se refieren al mismo objeto y, por lo tanto, tienen el mismo valor. Parecen ser iguales. Sin embargo, debido a la posibilidad de reasignación,
no tienen que quedarse así:

.. activecode:: ac2_13_2

    a = 5
    b = a    # después de ejecutar esta línea, ayb ahora son iguales
    print(a,b)
    a = 3    # después de ejecutar esta línea, ayb ya no son iguales
    print(a,b)

La línea 4 cambia el valor de ``a`` pero no cambia el valor de
``b``, por lo que ya no son iguales. Tendremos mucho más que decir sobre la igualdad en un capítulo posterior.


Desarrollando el modelo mental de cómo Python evalúa
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Es importante comenzar a desarrollar un buen modelo mental de los pasos que toma el intérprete de Python al evaluar una declaración de asignación. En una declaración de asignación, el intérprete primero evalúa el código en el lado derecho del operador de asignación. Luego le da un nombre a lo que sea que sea. La visualización (muy corta) a continuación muestra lo que está sucediendo.

.. showeval:: se_ac2_13_1a
    :trace_mode: true

    a = 5
    b = a
    ~~~~
    a = {{5}}{{5}}
    b = {{a}}{{5}}

En la primera declaración ``a = 5``, el número literal 5 se evalúa como 5 y recibe el nombre ``a``. En la segunda declaración, la variable ``a`` se evalúa a 5 y 5 ahora termina con un segundo nombre ``b``.

Puede recorrer el código y ver cómo cambian las asignaciones de variables a continuación.

.. codelens:: clens2_13_1
    :python: py3

    a = 5
    b = a    # después de ejecutar esta línea, a y b ahora son iguales
    print(a,b)
    a = 3    # después de ejecutar esta línea, a y b ya no son iguales
    print(a,b)

.. note::

   En algunos lenguajes de programación, un diferente
   símbolo se utiliza para la asignación, como ``<-`` o ``:=``. La intención es
   que esto ayudará a evitar confusiones. Python
   eligió usar los tokens ``=`` para la asignación y ``==`` para la igualdad. Esta es una popular
   opción que también se encuentra en lenguajes como C, C++, Java y C#.


**Revisa tu entendimiento**

.. mchoice:: question2_13_1
   :answer_a: "x" es 15 e "y" es 15
   :answer_b: "x" es 22 e "y" is 22
   :answer_c: "x" es 15 e "y" is 22
   :answer_d: "x" es 22 e "y" is 15
   :correct: d
   :feedback_a: Mira la última declaración de asignación que le da a x un valor diferente.
   :feedback_b: No, x e y son dos variables separadas. Solo porque x cambia en la última declaración de asignación, no cambia el valor que se copió en y en la segunda declaración.
   :feedback_c: Mira la última declaración de asignación, que reasigna x, y no y.
   :feedback_d: Sí, x tiene el valor 22 e y el valor 15.
   :practice: T

   Después de las siguientes afirmaciones, ¿cuáles son los valores de x e y?

   .. code-block:: python

     x = 15
     y = x
     x = 22
