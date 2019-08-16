..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-11-
   :start: 1

👩‍💻  Estrategias para Accumulator Pattern
============================================

Cuándo Usarlo
--------------

Cuando los niños se encuentran por primera vez con problemas de palabras en sus clases de matemáticas, les resulta difícil traducir esas palabras en expresiones aritméticas que implican suma, resta, multiplicación y división. Los profesores ofrecen heurística. Si el problema dice "cuántos ... en total", ese es un problema adicional. Si dice "cuántos quedan", será un problema de resta.

Aprender a usar el patrón acumulador puede ser igualmente confuso. El primer paso es reconocer algo en el enunciado del problema que sugiere un patrón de acumulación. Aquí hay algunos. Es posible que desee intentar agregar algunos más.

+----------------+----------------------+
| Phrase         | Accumulation Pattern |
+----------------+----------------------+
| how many       | count accumulation   |
+----------------+                      +
| how frequently |                      |
+----------------+----------------------+
| total          | sum accumulation     |
+----------------+----------------------+
| a list of      | list accumulation    |
+----------------+----------------------+
| concatenate    |                      |
+----------------+  string accumulation +
| join together  |                      |
+----------------+----------------------+
+----------------+----------------------+

Por ejemplo, si el problema es calcular la distancia total recorrida en una serie de viajes pequeños, querrás acumular una suma. Si el problema es hacer una lista de los cubos de todos los números del 1 al 25, desea una acumulación de la lista, comenzando con una lista vacía y agregando un cubo más cada vez. Si el problema es hacer una lista separada por comas de todas las personas invitadas a una fiesta, debe pensar en concatenarlas; podría comenzar con una cadena vacía y concatenar a una persona más en cada iteración a través de una lista de nombres.

Antes de escribirlo
--------------------

Antes de escribir cualquier código, le recomendamos que primero responda las siguientes preguntas:

- ¿A través de qué secuencia iterarás mientras acumulas un resultado? Podría ser un rango de números, las letras en una cadena o alguna lista existente que tenga como una lista de nombres.

- ¿Qué tipo de valor acumularás? Si su resultado final será un número, su acumulador comenzará con un número y siempre tendrá un número aunque se actualice cada vez. Del mismo modo, si su resultado final será una lista, comience con una lista. Si su resultado final será una cadena, probablemente quiera comenzar con una cadena; otra opción es acumular una lista de cadenas y luego usar el método `.join ()` al final para concatenarlos todos juntos.

Recomendamos escribir sus respuestas a estas preguntas en un comentario. Cuando encuentre errores y tenga que buscar cosas, le ayudará a recordar lo que estaba tratando de implementar. A veces, solo escribir el comentario puede ayudarlo a darse cuenta de un problema potencial y evitarlo antes de escribir cualquier código.

Elegir buenos nombres de variables de acumulador e iterador
-------------------------------------------------------------

El último consejo con respecto a las estrategias de acumulación debe ser intencional al elegir nombres de variables para
acumulador e iterador de variables. Un buen nombre puede ayudarlo a recordar cuál es el valor asignado a la variable como
así como lo que debería tener al final de su código. Si bien puede ser tentador al principio usar un nombre corto de variable,
como ``a`` o ``x``, si encuentra algún error o mira su código más tarde, puede tener problemas para entender lo que
destinado a hacer y lo que su código está haciendo realmente.

Para la variable acumuladora, una cosa que puede ayudar es hacer que el nombre de la variable termine con "so_far". El prefijo puede ser algo que te ayude a recordar lo que se supone que debes terminar. Por ejemplo: `count_so_far`, `total_so_far` o `cubes_so_far`.

Como se mencionó anteriormente en un segmento anterior de El camino del Programador:ref:`naming_variables_in_for_loops`, la variable iterador debe ser un sustantivo singular. Debe describir qué elemento de la secuencia original, no cuál será el elemento del resultado final. Por ejemplo, cuando acumule los cubos de los números del 1 al 25, no escriba `for num in range(25):`. En su lugar, escriba `for num in range (25):`. Si nombra la variable iteradora `cube` corre el riesgo de confundirse de que ya ha sido cubicada, cuando esa es una operación que todavía tiene que escribir en su código.

**Revisa tu entendimiento**

.. mchoice:: question8_11_1
   :answer_a: Sí; "guardar... a una lista"
   :answer_b: Yes; "agregar 'ed' al final de la palabra"
   :answer_c: No
   :feedback_a: ¡Correcto!
   :feedback_b: No del todo: estas palabras no necesariamente significan que queremos acumular las nuevas cadenas en una nueva variable.
   :feedback_c: ¡En este caso, sería bueno usar un accumulation pattern!
   :correct: a
   :practice: T

   ¿El siguiente mensaje requiere un patrón de acumulación? Si es así, ¿qué palabras indican eso? Para cada cadena en ``wrds``, agregue 'ed' al final de la palabra (paraconjugar la palabra en tiempo pasado). Guarde estas palabras en tiempo pasado en una lista llamada ``past_wrds``.

.. mchoice:: question8_11_2
   :answer_a: Sí; "para resumir"
   :answer_b: Sí; "números en la lista"
   :answer_c: No
   :feedback_a: ¡Correcto!
   :feedback_b: No del todo, estas palabras no necesariamente significan que queremos hacer una acumulación de suma.
   :feedback_c: ¡En este caso, un patrón de acumulación sería bueno para usar!
   :correct: a
   :practice: T

   ¿El siguiente mensaje requiere un patrón de acumulación? Si es así, ¿qué palabras indican eso? Escriba el código para resumir todos los números en la lista ``seat_counts``. Almacene ese número en la variable ``total_seat_counts``.

.. mchoice:: question8_11_3
   :answer_a: Sí; "imprimir cada uno"
   :answer_b: Sí; "en una línea separada"
   :answer_c: No
   :feedback_a: Incorrecto, este aviso no necesita usar el patrón de acumulación.
   :feedback_b: Incorrecto, este aviso no necesita usar el patrón de acumulación.
   :feedback_c: ¡Correcto!
   :correct: c
   :practice: T

   ¿El siguiente mensaje requiere un patrón de acumulación? Si es así, ¿qué palabras indican eso? Escriba el código para imprimir cada carácter de la cadena ``my_str`` en una línea separada.

.. mchoice:: question8_11_4
   :answer_a: Sí; "vocales en la oración"
   :answer_b: Sí; "código que contará"
   :answer_c: No
   :feedback_a: No del todo, estas palabras no necesariamente significan que queremos hacer una acumulación de suma.
   :feedback_b: ¡Correcto!
   :feedback_c: ¡En este caso, un patrón de acumulación sería bueno para usar!
   :correct: b
   :practice: T

   ¿El siguiente mensaje requiere un patrón de acumulación? Si es así, ¿qué palabras indican eso? Escriba un código que cuente el número de vocales en la oración ``s`` y asigne el resultado a la variable ``num_vowels``.

.. mchoice:: question8_11_5
   :answer_a: string
   :answer_b: list
   :answer_c: integer
   :answer_d: ninguno, no hay variable acumuladora.
   :feedback_a: Incorrecto, ese no es el mejor tipo para la variable del acumulador.
   :feedback_b: Incorrecto, ese no es el mejor tipo para la variable del acumulador.
   :feedback_c: Sí, porque queremos hacer un seguimiento de un número.
   :feedback_d: Incorrecto, necesitaremos una variable acumuladora.
   :correct: c
   :practice: T

   ¿Qué tipo se debe usar para la variable acumuladora en el siguiente mensaje? Escriba un código que cuente el número de vocales en la oración ``s`` y asigne el resultado a la variable ``num_vowels``.

.. mchoice:: question8_11_6
   :answer_a: num_vowels
   :answer_b: s
   :answer_c: the prompt does not say
   :feedback_a: No, esa es la variable acumuladora.
   :feedback_b: Sí, esa es la secuencia por la que iterarás.
   :feedback_c: It is stated in the prompt.
   :correct: b
   :practice: T

   ¿A través de qué secuencia iterará mientras acumula un resultado en el siguiente mensaje? Escriba un código que cuente el número de vocales en la oración ``s`` y asigne el resultado a la variable ``num_vowels``.

.. mchoice:: question8_11_7
   :answer_a: string
   :answer_b: list
   :answer_c: integer
   :answer_d: ninguno, no hay variable acumuladora.
   :feedback_a: Incorrecto, ese no es el mejor tipo para la variable del acumulador.
   :feedback_b: Sí, porque queremos una nueva lista al final del código.
   :feedback_c: Incorrecto, ese no es el mejor tipo para la variable del acumulador.
   :feedback_d: Incorrecto, necesitaremos una variable acumuladora.
   :correct: b
   :practice: T

   ¿Qué tipo se debe usar para la variable acumuladora en el siguiente mensaje? Para cada cadena en ``wrds``, agregue 'ed' al final de la palabra (para conjugar la palabra en tiempo pasado). Guarde estas palabras en tiempo pasado en una lista llamada ``past_wrds``.

.. mchoice:: question8_11_8
   :answer_a: wrds
   :answer_b: past_wrds
   :answer_c: the prompt does not say
   :feedback_a: Sí, esa es la secuencia por la que iterarás.
   :feedback_b: No, esa es la variable acumuladora.
   :feedback_c: It is stated in the prompt.
   :correct: a
   :practice: T

   ¿A través de qué secuencia iterará mientras acumula un resultado en el siguiente mensaje? Para cada cadena en ``wrds``, agregue 'ed' al final de la palabra (para conjugar la palabra en tiempo pasado). Guarde estas palabras en tiempo pasado en una lista llamada ``past_wrds``.

.. mchoice:: question8_11_9
   :answer_a: string
   :answer_b: list
   :answer_c: integer
   :answer_d: ninguno, no hay variable acumuladora.
   :feedback_a: Incorrecto, ese no es el mejor tipo para la variable del acumulador.
   :feedback_b: Incorrecto, ese no es el mejor tipo para la variable del acumulador.
   :feedback_c: Sí, porque queremos hacer un seguimiento de un número.
   :feedback_d: Incorrecto, necesitaremos una variable acumuladora.
   :correct: c
   :practice: T

   ¿Qué tipo se debe usar para la variable acumuladora en el siguiente mensaje? Escriba el código para resumir todos los números en la lista ``seat_counts``. Almacene ese número en la variable ``total_seat_counts``.

.. mchoice:: question8_11_10
   :answer_a: seat_counts
   :answer_b: total_seat_counts
   :answer_c: the prompt does not say
   :feedback_a: Sí, esa es la secuencia por la que iterarás.
   :feedback_b: No, esa es la variable acumuladora.
   :feedback_c: It is stated in the prompt.
   :correct: a
   :practice: T

    ¿A través de qué secuencia iterará mientras acumula un resultado en el siguiente mensaje? Escriba el código para resumir todos los números en la lista ``seat_counts``. Almacene ese número en la variable ``total_seat_counts``.

.. mchoice:: question8_11_11
   :answer_a: string
   :answer_b: list
   :answer_c: integer
   :answer_d: ninguno, no hay variable acumuladora.
   :feedback_a: Incorrecto, no debería haber una variable acumuladora.
   :feedback_b: Incorrecto, no debería haber una variable acumuladora.
   :feedback_c: Incorrecto, no debería haber una variable acumuladora.
   :feedback_d: Correcto, porque este mensaje no requiere un patrón acumulador.
   :correct: d
   :practice: T

   ¿Qué tipo se debe usar para la variable acumuladora en el siguiente mensaje? Escriba el código para imprimir cada carácter de la cadena ``my_str`` en una línea separada.

.. mchoice:: question8_11_12
   :answer_a: my_str
   :answer_b: my_str.split()
   :answer_c: the prompt does not say
   :feedback_a: Sí, esa es la secuencia por la que iterarás.
   :feedback_b: Cperder, pero lea el mensaje nuevamente: ¿decía iterar a través de las palabras?
   :feedback_c: It is stated in the prompt.
   :correct: a
   :practice: T

   ¿A través de qué secuencia iterará mientras acumula un resultado en el siguiente mensaje? Escriba el código para imprimir cada carácter de la cadena ``my_str`` en una línea separada.

.. mchoice:: question8_11_13
   :answer_a: Variable Acumuladora: wrds_so_far     ; Variable Iteradora: wrd
   :answer_b: Variable Acumuladora: wrds_so_far     ; Variable Iteradora: x
   :answer_c: Variable Acumuladora: changed_wrds    ; Variable Iteradora: ed
   :feedback_a: Sí, esta es la combinación más clara de variables de acumulador e iterador.
   :feedback_b: La variable iteradora no es la más clara aquí, algo más puede ser mejor.
   :feedback_c: La variable iteradora no es la más clara aquí
   :correct: a
   :practice: T

   ¿Cuáles de estas son buenas alternativas a la variable del acumulador y los nombres de las variables del iterador para el siguiente mensaje? Para cada cadena en ``wrds``, agregue 'ed' al final de la palabra (para hacer que la palabra en tiempo pasado). Guarde estas palabras en tiempo pasado en una lista llamada ``past_wrds``.

.. mchoice:: question8_11_14
   :answer_a: Variable Acumuladora: count_so_far  ; Variable Iteradora: l
   :answer_b: Variable Acumuladora: total_so_far  ; Variable Iteradora: letter
   :answer_c: Variable Acumuladora: n_v           ; Variable Iteradora: letter
   :feedback_a: Aunque la variable acumuladora es buena, la variable iteradora no está muy clara.
   :feedback_b: ¡Sí! Tanto la variable del acumulador como la del iterador son claras.
   :feedback_c: Aunque la variable iteradora es buena, la variable acumuladora no es muy clara.
   :correct: b
   :practice: T

   ¿Cuáles de estas son buenas alternativas a la variable del acumulador y los nombres de las variables del iterador para el siguiente mensaje? Escriba un código que cuente el número de vocales en la oración ``s`` y asigne el resultado a la variable ``num_vowels``.

.. mchoice:: question8_11_15
   :answer_a: Variable Acumuladora: total_so_far        ; Variable Iteradora: seat
   :answer_b: Variable Acumuladora: total_seats_so_far  ; Variable Iteradora: seat_count
   :answer_c: Variable Acumuladora: count               ; Variable Iteradora: n
   :feedback_a: Aunque la variable del acumulador es buena, la variable del iterador no es lo suficientemente clara.
   :feedback_b: Sí, esta es la combinación más clara.
   :feedback_c: Ni el acumulador ni la variable iterador son lo suficientemente claros. La variable del acumulador es mejor, pero podría ser más clara.
   :correct: b
   :practice: T

   ¿Cuáles de estas son buenas alternativas a la variable del acumulador y los nombres de las variables del iterador para el siguiente mensaje? Escriba el código para resumir todos los números en la lista ``seat_counts``. Almacene ese número en la variable ``total_seat_counts``.

.. mchoice:: question8_11_16
   :answer_a: Variable Acumuladora: character_so_far    ; Variable Iteradora: char
   :answer_b: Variable Acumuladora: no variable needed  ; Variable Iteradora: c
   :answer_c: Variable Acumuladora: no variable needed  ; Variable Iteradora: char
   :feedback_a: Incorrecto, no hay variable de acumulador necesaria
   :feedback_b: Aunque no se necesita una variable acumuladora, la variable iteradora no es lo suficientemente clara
   :feedback_c: Sí, no se necesita una variable acumuladora y la variable iteradora es clara (char es una forma abreviada de character)
   :correct: c
   :practice: T

   ¿Cuáles de estas son buenas alternativas a la variable del acumulador y los nombres de las variables del iterador para el siguiente mensaje? Escriba el código para imprimir cada carácter de la cadena ``my_str`` en una línea separada.
