..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-4-
   :start: 1

Strings y bucles ``for``
-------------------------

Como una cadena es simplemente una secuencia de caracteres, el ciclo ``for`` itera sobre cada carácter
automáticamente. (Como siempre, intente predecir cuál será la salida de este código antes de ejecutarlo).

.. activecode:: ac6_4_1
    :nocanvas:

    for achar in "Go Spot Go":
        print(achar)

La variable de iteración ``achar`` se reasigna automáticamente a cada carácter en la cadena "Go Spot Go".
Nos referiremos a este tipo de iteración de secuencia como **iteración por elemento**. Tenga en cuenta que el bucle for
procesa los caracteres en una cadena o elementos en una secuencia uno a la vez de izquierda a derecha.

**Revisa tu entendimiento**

.. mchoice:: question6_4_1
   :answer_a: 10
   :answer_b: 11
   :answer_c: 12
   :answer_d: Error, la sentencia for necesita usar la función range.
   :correct: c
   :feedback_a: La iteración por elemento se procesará una vez para cada elemento de la secuencia.
   :feedback_b: El espacio en blanco es parte de la secuencia.
   :feedback_c: Sí, hay 12 caracteres, incluido el espacio en blanco.
   :feedback_d: La instrucción for puede iterar sobre una secuencia elemento por elemento.
   :practice: T

   ¿Cuántas veces se imprime la palabra HOLA con las siguientes afirmaciones?
   
   .. code-block:: python

      s = "python rocks"
      for ch in s:
         print("HELLO")
   
.. mchoice:: question6_4_2
   :answer_a: 4
   :answer_b: 5
   :answer_c: 6
   :answer_d: Error, la sentencia for no puede usar slice.
   :correct: b
   :feedback_a: Slice retorna una secuencia que puede ser iterada.
   :feedback_b: Sí, el espacio en blanco es parte de la secuencia devuelta por slice.
   :feedback_c: Revisa el resultado s[3:8]. No incluye el artículo en el índice 8.
   :feedback_d: Slice devuelve una secuencia.
   :practice: T

   ¿Cuántas veces se imprime la palabra HOLA con las siguientes afirmaciones?
   
   .. code-block:: python

      s = "python rocks"
      for ch in s[3:8]:
         print("HELLO")
