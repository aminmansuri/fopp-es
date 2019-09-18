..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: condition-10-
   :start: 1

Patrón Acumulador con condicionales
-----------------------------------

A veces, cuando estamos acumulando, no queremos agregar a nuestro acumulador cada vez que iteramos.
Considere, por ejemplo, el siguiente programa que cuenta el número de letras en una frase.

.. activecode:: ac7_10_1

   phrase = "What a wonderful day to schedule"
   tot = 0
   for char in phrase:
       if char != " ":
           tot = tot + 1
   print(tot)

Aquí, **inicializamos** la variable del acumulador para que sea cero en la línea dos.

**Iteramos** a través de la secuencia (línea 3).

El paso **actualización** ocurre en dos partes. Primero, verificamos si el valor de ``char`` no es un espacio. Si
no es un espacio, entonces actualizamos el valor de nuestra variable acumuladora ``tot`` (en la línea 6) agregando uno a
eso. Si ese condicional demuestra ser falso, lo que significa que char *es* un espacio, entonces no actualizamos ``tot``
y continúa el ciclo for. Podríamos haber escrito ``tot = tot + 1`` o ``tot += 1``, igual está bien.

Al final, hemos acumulado el número total de letras en la frase. Sin usar el condicional,
solo hubiéramos podido contar cuántos caracteres hay en la cadena y no hubiéramos podido
diferenciar entre espacios y no espacios.

Podemos usar condicionales para contar también si determinados elementos están en una cadena o lista. El siguiente código encuentra todas las apariciones de vocales en el siguiente string.

.. activecode:: ac7_10_2

    s = "what if we went to the zoo"
    x = 0
    for i in s:
        if i in ['a', 'e', 'i', 'o', 'u']:
            x += 1
    print(x)

También podemos usar ``==`` para ejecutar una operación similar. Aquí, verificaremos si el personaje sobre el que estamos iterando es
una "o". Si es una "o", actualizaremos nuestro contador.

.. image:: Figures/accum_o.gif
   :alt: un gif que muestra un código para verificar que "o" está en la frase "onomatopeya".

Acumulando el valor máximo
~~~~~~~~~~~~~~~~~~~~~~~~~~

También podemos usar el patrón de acumulación con condicionales para encontrar el valor máximo o mínimo. En vez de
continuando acumulando el valor del acumulador como lo hemos hecho al contar o encontrar una suma, podemos reasignar el
acumulador variable a un valor diferente.

El siguiente ejemplo muestra cómo podemos obtener el valor máximo de una lista de enteros.

.. activecode:: ac7_10_3

   nums = [9, 3, 8, 11, 5, 29, 2]
   best_num = 0
   for n in nums:
       if n > best_num:
           best_num = n
   print(best_num)

Aquí, inicializamos best_num a cero, suponiendo que no hay números negativos en la lista.

En el bucle for, verificamos si el valor actual de n es mayor que el valor actual de ``best_num``.
Si es así, entonces queremos **actualizar** ``best_num`` para que ahora se le asigne el número más alto. De lo contrario,
no hace nada y continuar el ciclo for.

Puede notar que la estructura actual podría ser un problema. Si los números fueran todos negativos, ¿qué le podría
pasar a nuestro código? ¿Qué pasaría si estuviéramos buscando el número más pequeño pero inicializamos ``best_num`` con
cero? Para solucionar este problema, podemos inicializar la variable del acumulador usando uno de los números en
lista.

.. activecode:: ac7_10_4

   nums = [9, 3, 8, 11, 5, 29, 2]
   best_num = nums[0]
   for n in nums:
       if n > best_num:
           best_num = n
   print(best_num)

Lo único que cambiamos fue el valor de ``best_num`` en la línea 2 para que el valor de ``best_num`` sea el
primer elemento en ``nums`` ¡pero el resultado sigue siendo el mismo!

**Revisa tu entendimiento**

.. mchoice:: question7_10_1
   :answer_a: 2
   :answer_b: 5
   :answer_c: 0
   :answer_d: Hay un error en el código, por lo que no puede ejecutarse.
   :correct: b
   :feedback_a: Aunque solo se encuentran dos de las letras de la lista, las contamos cada vez que aparecen.
   :feedback_b: Sí, agregamos a x cada vez que encontramos una letra en la lista.
   :feedback_c: Verifique nuevamente lo que está evaluando el condicional. El valor de i será un carácter en la cadena s, entonces, ¿qué sucederá en la instrucción if?
   :feedback_d: No hay errores en este código.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?

   .. code-block:: python

     s = "We are learning!"
     x = 0
     for i in s:
         if i in ['a', 'b', 'c', 'd', 'e']:
             x += 1
     print(x)

.. mchoice:: question7_10_2
   :answer_a: 10
   :answer_b: 1
   :answer_c: 0
   :answer_d: Hay un error en el código, por lo que no puede ejecutarse.
   :correct: c
   :feedback_a: No exactamente. ¿Qué es la verificación condicional?
   :feedback_b: min_value se estableció en un número menor que cualquiera de los números de la lista, por lo que nunca se actualizó en el ciclo for.
   :feedback_c: Sí, min_value se configuró en un número menor que cualquiera de los números de la lista, por lo que nunca se actualizó en el ciclo for.
   :feedback_d: El código no tiene un error que impida su ejecución.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?

   .. code-block:: python

     list= [5, 2, 1, 4, 9, 10]
     min_value = 0
     for item in list:
        if item < min_value:
            min_value = item
     print(min_value)

.. activecode:: ac7_10_5
   :language: python
   :autograde: unittest
   :practice: T
      
   Para cada string de la lista ``words``, encuentre el número de caracteres en la cadena. Si el número de caracteres en la cadena es mayor que 3, agregue 1 a la variable ``num_words`` para que ``num_words`` termine con el número total de palabras con más de 3 caracteres.
   ~~~~
   words = ["water", "chair", "pen", "basket", "hi", "car"]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFive(self):
         self.assertEqual(num_words, 3, "Testing that num_words has the correct value.")

   myTests().main()

.. activecode:: ac7_10_7
   :language: python
   :autograde: unittest
   :practice: T

   **Desafío** Para cada palabra en ``words``, agregue 'd' al final de la palabra si la palabra termina en "e" para hacerla en tiempo pasado. De lo contrario, agregue 'ed' para hacerlo en tiempo pasado. Guarde estas palabras en tiempo pasado en una lista llamada ``past_tense``.
   ~~~~
   words = ["adopt", "bake", "beam", "confide", "grill", "plant", "time", "wave", "wish"]
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testNine(self):
         self.assertEqual(past_tense, ['adopted', 'baked', 'beamed', 'confided', 'grilled', 'planted', 'timed', 'waved', 'wished'], "Testing that the past_tense list is correct.")
         self.assertIn("else", self.getEditorText(), "Testing output (Don't worry about actual and expected values).")
         self.assertIn("for", self.getEditorText(), "Testing output (Don't worry about actual and expected values).")

   myTests().main()
