..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-11-
   :start: 1

Orden de las Operaciones
----------------------------

.. youtube:: Ezve3QJv6Aw
    :divid: precedencevid
    :height: 315
    :width: 560
    :align: center

Cuando aparece más de un operador en una expresión, el orden de evaluación
depende de las **reglas de precedencia**. Python sigue las mismas reglas de
precedencia para sus operadores matemáticos que las matemáticas.

.. El acrónimo PEMDAS
.. es una forma útil de recordar el orden de las operaciones:

#. *Los paréntesis* tienen la mayor prioridad y se pueden usar para forzar una
   expresión para evaluar en el orden que desee. Desde expresiones en
   los paréntesis se evalúan primero, ``2 * (3-1)`` es 4 y ``(1+1)**(5-2)`` es
   8. También puede usar paréntesis para que una expresión sea más fácil de leer, como en
   ``(minuto * 100) / 60``: en este caso, los paréntesis no cambian el resultado,
   pero refuerzan que la expresión entre paréntesis se evaluará primero.
#. *Exponenciación* tiene la siguiente precedencia más alta, por lo que ``2**1+1`` es 3 y
   no 4, y ``3*1**3`` es 3 y no 27. ¿Puede explicar por qué?
#. *Los operadores de multiplicación y ambas divisiones* tienen la misma
   precedencia, que es mayor que la suma y la resta, que
   también tienen la misma precedencia. Entonces ``2*3-1`` produce 5 en lugar de 4, y
   ``5-2*2`` es 1, no 6.
#. Los operadores con la *misma* precedencia son
   evaluados de izquierda a derecha. En álgebra decimos que son *asociativos a la izquierda*.
   Entonces, en la expresión ``6-3+2``, la resta ocurre primero, produciendo 3.
   Luego agregamos 2 para obtener el resultado 5. Si las operaciones hubieran sido evaluadas desde
   de derecha a izquierda, el resultado habría sido ``6-(3+2)``, que es 1.

.. (The
..   acrónimo PEDMAS podría inducirlo a error al pensar que la división tiene mayor
..   precedencia que multiplicación, y la suma se realiza antes que la resta -
..   no te dejes engañar. La resta y la suma tienen la misma precedencia, y
..   se aplica la regla de izquierda a derecha)

.. note::

    Debido a alguna peculiaridad histórica, una excepción a la izquierda a la derecha
    La regla asociativa izquierda es el operador de exponenciación ``**``. Una pista útil
    es usar siempre paréntesis para forzar exactamente el orden que desea cuando
    La exponenciación está involucrada:

.. activecode:: ac2_11_1
   :nocanvas:

   print(2 ** 3 ** 2)     # ¡el operador más a la derecha ** se hace primero!
   print((2 ** 3) ** 2)   # ¡usa paréntesis para forzar el orden que deseas!

.. note::

   Esta es una segunda forma en que los paréntesis se usan en Python. La primera forma en que ya has visto es que () indica una llamada a la función, con las entradas dentro de los paréntesis. ¿Cómo puede saber Python cuándo los paréntesis especifican llamar a una función y cuándo solo están forzando el orden de las operaciones para expresiones de operador ambiguas?

   La respuesta es que si hay una expresión a la izquierda de los paréntesis que se evalúa como un objeto de función, entonces los paréntesis indican una llamada a la función, y de lo contrario no. Tendrás que acostumbrarte a hacer la misma inferencia cuando veas paréntesis: ¿es esta una llamada a una función, o simplemente especificando la precedencia?

**Revisa tu entendimiento**

.. mchoice:: question2_11_1
   :answer_a: 14
   :answer_b: 24
   :answer_c: 3
   :answer_d: 13.667
   :correct: a
   :feedback_a: Usando paréntesis, la expresión se evalúa como (2*5) primero, luego (10 // 3), luego (16-3), y luego (13+1).
   :feedback_b: Recuerda que * tiene prioridad sobre -.
   :feedback_c: Recuerda que // tiene prioridad sobre -.
   :feedback_d: Recuerda que // hace división entera.
   :practice: T

   ¿Cuál es el valor de la siguiente expresión:

   .. code-block:: python

      16 - 2 * 5 // 3 + 1

Aquí hay una animación para la expresión anterior:

.. showeval:: se_ac2_11_1
   :trace_mode: true

   16 - 2 * 5 // 3 + 1
   ~~~~
   16 - {{2 * 5}}{{10}} // 3 + 1
   16 - {{10 // 3}}{{3}} + 1
   {{16 - 3}}{{13}} + 1
   {{13 + 1}}{{14}}

