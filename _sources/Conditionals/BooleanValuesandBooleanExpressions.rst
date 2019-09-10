..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: condition-2-
   :start: 1

.. index:: True, False, boolean value
   comparison; numbers
   single:  <; numbers
   single:  <=; numbers
   single:  >; numbers
   single:  >=; numbers
   single:  ==; numbers
   single:  !=; numbers

Valores boolean y expresiones boolean
--------------------------------------------

.. youtube:: Y6CwThhquQs
    :divid: booleanexpressions
    :height: 315
    :width: 560
    :align: left

El tipo de de variable en Python para almacenar valores verdaderos y falsos se llama ``bool``, llamado así
en honor al matemático británico, George Boole. George Boole creó el *Álegbra
Boolean*, que es la base de toda la aritmética informática moderna.

Solo hay dos **valores boolean**. Son ``True`` y ``False``. Respetar las mayúsculas
es importante, ya que ``true`` y ``false`` no son valores boolean (recuerde que Python es el caso
sensible).

.. activecode:: ac7_2_1

    print(True)
    print(type(True))
    print(type(False))

.. note:: ¡Los valores booleans no son strings!

    Es extremadamente importante darse cuenta de que True y False no son strings. Ellos no están
    rodeados de comillas. Son los únicos dos valores en el tipo de datos ``bool``. Mira de cerca los
    tipos que se muestran a continuación.


.. activecode:: ac7_2_2

    print(type(True))
    print(type("True"))

Una **expresión boolean** es una expresión que se evalúa como un valor boolean.
El operador de igualdad, ``==``, compara dos valores y produce un valor boolean relacionado si
los valores son iguales el uno al otro.

.. activecode:: ac7_2_3

    print(5 == 5)
    print(5 == 6)

En la primera instrucción, los dos operandos son iguales, por lo que la expresión evalúa
a ``True``. En la segunda declaración, 5 no es igual a 6, por lo que obtenemos ``False``.

El operador ``==`` es uno de los seis operadores de comparación **comunes**; los otros son:

.. sourcecode:: python

    x != y               # x no es igual a y
    x > y                # x es mayor que y
    x < y                # x es menor que y
    x >= y               # x es mayor o igual que y
    x <= y               # x es menor o igual que y

Aunque estas operaciones probablemente le sean familiares, los símbolos de Python son
diferentes de los símbolos matemáticos. Un error común es usar un solo
signo igual (``=``) en lugar de un doble signo igual (``==``). Recuerda que ``=``
es un operador de asignación y ``==`` es un operador de comparación. Además, ahí
no hay tal cosa como `` = <`` o ``=>``.

.. Con la reasignación es especialmente importante distinguir entre una
.. declaración de asignación y una expresión booleana que prueba la igualdad.
.. Debido a que Python usa el token igual (``=``) para la asignación,
.. es tentador interpretar una declaración como
.. ``a = b`` como prueba boolean. A diferencia de las matemáticas, no lo es! Recuerda que el token Python
.. para el operador de igualdad es ``==``.

Tenga en cuenta también que una prueba de igualdad es simétrica, pero la asignación no lo es. Por ejemplo,
si ``a == 7`` entonces ``7 == a``. Pero en Python, la declaración ``a = 7``
es legal y ``7 = a`` no lo es. (¿Puedes explicar porque?)


**Revisa tu entendimiento**

.. mchoice:: question7_2_1
   :multiple_answers:
   :answer_a: True
   :answer_b: 3 == 4
   :answer_c: 3 + 4
   :answer_d: 3 + 4 == 7
   :answer_e: &quot;False&quot;
   :correct: a,b,d
   :feedback_a: True y False son literales boolean.
   :feedback_b: La comparación entre dos números a través de == da como resultado True o False (en este caso False), ambos valores Boolean.
   :feedback_c: 3+4 se evalúa a 7, que es un número, no un valor Boolean.
   :feedback_d: 3+4 se evalúa como 7. 7 == 7 luego se evalúa como True, que es un valor Boolean.
   :feedback_e: Con las comillas dobles que lo rodean, False se interpreta como una string, no como un valor Boolean. Si las comillas no se hubieran incluido, False solo seria  un valor Boolean.
   :practice: T

    ¿Cuál de las siguientes es una expresión Boolean? Seleccione todas las que correspondan.
