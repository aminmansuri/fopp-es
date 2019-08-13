..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sequences-7-
   :start: 1

.. index::
   single: +; list concatenation
   single: *; list repetition


Concatenación y repetición
----------------------------

Nuevamente, como con las cadenas, el operador ``+`` concatena las listas.
Del mismo modo, el operador ``*`` repite los elementos en una lista un número dado de veces.

.. activecode:: ac5_7_1

    fruit = ["manzana","naranja","banana","cereza"]
    print([1,2] + [3,4])
    print(fruit+[6,7,8,9])

    print([0] * 4)

Es importante ver que estos operadores crean nuevas listas a partir de los elementos de las listas de operandos.
Si concatena una lista con 2 elementos y una lista con 4 elementos, obtendrá una nueva lista con 6 elementos
(No es una lista con dos sublistas). Del mismo modo, la repetición de una lista de 2 elementos 4 veces dará una lista
con 8 artículos.

Una forma de aclarar esto es ejecutar una parte de este ejemplo en codelens.
A medida que avanza por el código, verá las variables que se crean y las listas a las que hacen referencia.
Preste especial atención al hecho de que cuando la declaración crea ``nueva lista``
``newlist = fruit + numlist``, se refiere a una lista completamente nueva formada al hacer copias de los elementos de ``fruit`` y ``numlist``. Puede ver esto muy claramente en el diagrama de objetos de codelens. Los objetos son diferentes.

.. codelens:: clens5_7_1
    :python: py3

    fruit = ["manzana","naranja","banana","cereza"]
    numlist = [6,7]

    newlist = fruit + numlist

    zeros = [0] * 4

.. note:: WP: Agregar tipos juntos

    ¡Tenga cuidado al agregar diferentes tipos juntos! Python no entiende cómo concatenar diferentes
    tipos juntos. Por lo tanto, si intentamos agregar una cadena a una lista con ``['first'] + "second"`` entonces el
    intérprete devolverá un error. Para hacer esto, deberá hacer que los dos objetos sean del mismo tipo. En este
    caso, significa poner la cadena en su propia lista y luego agregar los dos juntos de la siguiente manera:
    ``['first'] + ["second"]``. Sin embargo, este proceso se verá diferente para otros tipos. Recuerda que hay
    son funciones para convertir tipos!

**Revisa tu entendimiento**

.. mchoice:: question5_7_1
   :answer_a: 6
   :answer_b: [1,2,3,4,5,6]
   :answer_c: [1,3,5,2,4,6]
   :answer_d: [3,7,11]
   :correct: c
   :feedback_a: La concatenación no agrega las longitudes de las listas.
   :feedback_b: La concatenación no reordena los artículos.
   :feedback_c: Sí, una nueva lista con todos los elementos de la primera lista seguidos de todos los de la segunda.
   :feedback_d: La concatenación no agrega los elementos individuales.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

     alist = [1,3,5]
     blist = [2,4,6]
     print(alist + blist)

.. mchoice:: question5_7_2
   :answer_a: 9
   :answer_b: [1,1,1,3,3,3,5,5,5]
   :answer_c: [1,3,5,1,3,5,1,3,5]
   :answer_d: [3,9,15]
   :correct: c
   :feedback_a: La repetición no multiplica las longitudes de las listas. Repite los artículos.
   :feedback_b: La repetición no repite cada elemento individualmente.
   :feedback_c: Sí, los elementos de la lista se repiten 3 veces, uno tras otro.
   :feedback_d: La repetición no multiplica los elementos individuales.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

     alist = [1,3,5]
     print(alist * 3)
