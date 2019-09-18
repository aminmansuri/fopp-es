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

👩‍💻 Realizando un seguimiento de su variable iteradora y su iterable
======================================================================

Cuando los estudiantes comienzan a usar bucles por primera vez, a veces tienen dificultades para comprender la diferencia entre la variable iteradora (la variable de bucle) y la iterable.

El iterable es el objeto que analizará en un bucle for. Generalmente, este objeto no cambia mientras se ejecuta el bucle for.

La variable iterador (bucle) es la variable que almacena una parte del iterable cuando se ejecuta el bucle for. Cada vez que el ciclo itera, el valor de la variable iterador cambiará a una porción diferente del iterable.

.. mchoice:: question6_100_1
   :answer_a: string
   :answer_b: lista
   :answer_c: tupla
   :answer_d: iterable
   :answer_e: error, incapaz de iterar sobre el objeto.
   :feedback_a: Incorrecto, ese no es el tipo del iterable.
   :feedback_b: Sí, el iterable es n, y es una lista.
   :feedback_c: Incorrecto, ese no es el tipo del iterable.
   :feedback_d: Incorrecto, ese no es el tipo del iterable.
   :feedback_e: Incorrecto, Python puede iterar sobre este tipo.
   :correct: b
   :practice: T

   ¿Cuál es el tipo del iterable?

   .. sourcecode:: python

       n = ["word", "phrase", 8, ("beam")]
       for item in n:
           print(item)


.. mchoice:: question6_100_2
   :answer_a: string
   :answer_b: lista
   :answer_c: tupla
   :answer_d: iterable
   :answer_e: error, incapaz de iterar sobre el objeto.
   :feedback_a: Sí, el iterable en este ejemplo es un string
   :feedback_b: Incorrecto, ese no es el tipo del iterable.
   :feedback_c: Incorrecto, ese no es el tipo del iterable.
   :feedback_d: Incorrecto, ese no es el tipo del iterable.
   :feedback_e: Incorrecto, Python puede iterar sobre este tipo.
   :correct: a
   :practice: T

   ¿Cuál es el tipo del iterable?

   .. sourcecode:: python

       t = "couch"
       for z in t:
           print(z)

.. mchoice:: question6_100_3
   :answer_a: string
   :answer_b: lista
   :answer_c: tupla
   :answer_d: iterable
   :answer_e: error, incapaz de iterar sobre el objeto.
   :feedback_a: Incorrecto, no hay strings presentes en el código.
   :feedback_b: Incorrecto, no hay listas presentes en el código.
   :feedback_c: Incorrecto, no hay tuplas presentes en el código.
   :feedback_d: Incorrecto, no hay objetos iterables en el código.
   :feedback_e: Sí, Python es incapaz de iterar sobre integers y floats.
   :correct: e
   :practice: T

    ¿Cuál es el tipo del iterable?

   .. sourcecode:: python

       y = 18
       for z in y:
           print(z)


.. mchoice:: question6_100_4
   :answer_a: string
   :answer_b: lista
   :answer_c: tupla
   :answer_d: iterable
   :answer_e: error, incapaz de iterar sobre el objeto.
   :feedback_a: Incorrecto, el iterable no es un string.
   :feedback_b: Incorrecto, no hay una lista en el código.
   :feedback_c: Sí, el iterable en esta situación es una tupla.
   :feedback_d: Incorrecto, esa no es la mejor respuesta para este problema.
   :feedback_e: Incorrecto, Python puede iterar sobre este tipo.
   :correct: c
   :practice: T

   ¿Cuál es el tipo del iterable?

   .. sourcecode:: python

       t = ("couch", "chair", "washer", "dryer", "table")
       for z in t:
           print(z)


.. mchoice:: question6_100_5
   :answer_a: string
   :answer_b: lista
   :answer_c: tupla
   :answer_d: iterable
   :answer_e: error, incapaz de iterar sobre el objeto.
   :feedback_a: ¡Correcto! El iterable es un string.
   :feedback_b: Incorrecto, no hay una lista en el código
   :feedback_c: Incorrecto, el iterable no es una tupla.
   :feedback_d: Incorrecto, esa no es la mejor respuesta para este problema.
   :feedback_e: Incorrecto, Python puede iterar sobre este tipo.
   :correct: a
   :practice: T

   ¿Cuál es el tipo del iterable?

   .. sourcecode:: python

       t = "couch"
       for z in t:
           print(z)



.. mchoice:: question6_100_6
   :answer_a: string
   :answer_b: lista
   :answer_c: tupla
   :answer_d: integer
   :answer_e: error, incapaz de iterar e inicializar la variable iteradora
   :feedback_a: ¡Correcto! Cada elemento en la variable iteradora será una cadena.
   :feedback_b: Incorrecto, ese no es el tipo de la variable iteradora.
   :feedback_c: Incorrecto, ese no es el tipo de la variable iteradora.
   :feedback_d: Incorrecto, ese no es el tipo de la variable iteradora.
   :feedback_e: Incorrecto, el bucle for está iterando sobre un objeto iterable.
   :correct: a
   :practice: T

   ¿Cuál es el tipo del iterable?

   .. sourcecode:: python

       t = ["couch", "chair", "washer", "dryer", "table"]
       for z in t:
           print(z)


.. mchoice:: question6_100_7
   :answer_a: string
   :answer_b: lista
   :answer_c: tupla
   :answer_d: integer
   :answer_e: error, incapaz de iterar e inicializar la variable iteradora
   :feedback_a: Incorrecto, Piense primero en cómo se verá el bucle for.
   :feedback_b: Incorrecto, ese es el tipo del iterable, no de la variable iteradora.
   :feedback_c: Incorrecto, no hay una tupla en el código.
   :feedback_d: Sí, el primer elemento en t es un número entero.
   :feedback_e: Incorrecto, el bucle for está iterando sobre un objeto iterable.
   :correct: d
   :practice: T

   ¿Cuál es el tipo de la variable iteradora en la primera iteración?

   .. sourcecode:: python

       t = [9, "setter", 3, "wing spiker", 10, "middle blocker"]
       for z in t:
           print(z)


.. mchoice:: question6_100_8
   :answer_a: string
   :answer_b: lista
   :answer_c: tupla
   :answer_d: integer
   :answer_e: error, incapaz de iterar e inicializar la variable iteradora
   :feedback_a: Sí, el segundo elemento en t es una cadena.
   :feedback_b: Incorrecto, ese es el tipo del iterable, no de la variable iteradora.
   :feedback_c: Incorrecto, no hay una tupla en el código.
   :feedback_d: Incorrecto, piense en cómo se verá el ciclo for durante la segunda iteración.
   :feedback_e: Incorrecto, el bucle for está iterando sobre un objeto iterable.
   :correct: a
   :practice: T

   ¿Cuál es el tipo de la variable iteradora en la segunda iteración?

   .. sourcecode:: python

       t = [9, "setter", 3, "wing spiker", 10, "middle blocker"]
       for z in t:
           print(z)

.. mchoice:: question6_100_9
   :answer_a: string
   :answer_b: lista
   :answer_c: tupla
   :answer_d: integer
   :answer_e: error, incapaz de iterar e inicializar la variable iteradora
   :feedback_a: Sí, el último valor almacenado en la variable iterador es una cadena.
   :feedback_b: Incorrecto, no hay una lista en el código.
   :feedback_c: Incorrecto, no hay una tupla en el código.
   :feedback_d: Incorrecto, no hay un integer en el código.
   :feedback_e: Incorrecto, el bucle for está iterando sobre un objeto iterable.
   :correct: a
   :practice: T

   ¿Cuál es el tipo de la variable iteradora en la iteración final?

   .. sourcecode:: python

       red = "colors"
       for blue in red:
           print(blue)

A medida que avanza por la ventana de codelens, se le harán una serie de preguntas.

.. codelens:: clensQuestion6_100_10
   :question: ¿Cuál es el valor de la variable iteradora después de que se ejecuta la línea 3?
   :feedback: El valor de la variable iteradora se cambia dentro del ciclo for.
   :breakline: 3
   :correct: globals.val

   item = ["M", "I", "S", "S", "O", "U", "R", "I"]
   for val in item:
       val = val + "!"

.. codelens:: clensQuestion6_100_11
   :question: ¿Cuál es el valor de la variable iteradora después de que se ejecuta la línea 2?
   :feedback: Recuerde que el valor de la variable iteradora cambia cada vez.
   :breakline: 2
   :correct: globals.n

   for n in range(5):
       print(n)
