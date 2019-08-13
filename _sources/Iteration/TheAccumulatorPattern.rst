..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-6-
   :start: 1

.. _accum_pattern:
      
El Patrón de Accumulator
==========================

Un "patrón" de programación común es atravesar una secuencia, **acumulando** un valor a medida que avanzamos,
como la suma hasta el momento o el máximo hasta el momento. De esa manera, al final del recorrido tenemos
acumulado un solo valor, como la suma total de todos los artículos o el artículo más grande.

La anatomía del patrón de acumulación incluye:
    - **inicializando** una variable de "acumulador" a un valor inicial (como 0 si se acumula una suma)
    - **iterando** (por ejemplo, atravesando los elementos en una secuencia)
    - **actualizando** la variable acumuladora en cada iteración (es decir, al procesar cada elemento en la secuencia)

Por ejemplo, considere el siguiente código, que calcula la suma de los números en una lista.

.. activecode:: ac6_6_1

   nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
   accum = 0
   for w in nums:
       accum = accum + w
   print(accum)

En el programa anterior, observe que la variable ``acumular`` comienza con un valor de 0.
A continuación, la iteración se realiza 10 veces. Dentro del bucle for, se produce la actualización.
``w`` tiene el valor del elemento actual (1 la primera vez, luego 2, luego 3, etc.).
A ``acumular`` se le reasigna un nuevo valor que es el valor anterior más el valor actual de ``w``.

Este patrón de iterar la actualización de una variable se conoce comúnmente como
**accumulator pattern**. Nos referimos a la variable como el **accumulator**. Este patrón aparecerá
una y otra vez. Recuerde que la clave para que funcione correctamente es asegurarse de
inicialice la variable antes de comenzar la iteración. Una vez dentro de la iteración, se requiere
que actualizas el acumulador.

Aquí está el mismo programa en codelens. Vaya paso a paso a través de la función y vea el "total acumulado"
como resultado.

.. codelens:: clens6_6_1
   :python: py3

   nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
   accum = 0
   for w in nums:
      accum = accum + w
   print(accum)


.. note::

    ¿Qué pasaría si sangramos el extracto acumulado de impresión? ¿No es seguro? Haz una predicción, luego pruébalo y descúbrelo.

También podemos utilizar la función de rango en esta situación. Anteriormente, lo has visto utilizado cuando queríamos dibujar
Tortuga. Allí lo usamos para iterar un cierto número de veces. Sin embargo, podemos hacer más que eso. La función ``rango``
toma al menos una entrada, que debería ser un número entero, y devuelve una lista siempre que sea su entrada. Si bien puedes proporcionar
dos entradas, nos enfocaremos en usar el rango con solo una entrada. Con una entrada, el rango comenzará en cero y subirá a, pero
no incluye - la entrada. Aquí están los ejemplos:

.. activecode:: ac6_8_10

    print("range(5): ")
    for i in range(5):
        print(i)

    print("range(0,5): ")
    for i in range(0, 5):
        print(i)

    # Notice the casting of `range` to the `list`
    print(list(range(5)))
    print(list(range(0,5)))

    # Note: `range` function is already casted as `list` in the textbook
    print(range(5))





Una cosa importante que debe saber sobre la función de rango en python3 es que si queremos usarla fuera de la iteración,
tiene que lanzarlo como una lista usando ``list ()``. Dentro del libro de texto notarás que ``rango`` funciona con o sin
lanzarlo como una lista, pero es mejor que intentes acostumbrarte a lanzarlo como una lista. Así es como podría usar la función de rango en el problema anterior.

.. activecode:: ac6_6_2

   accum = 0
   for w in range(11):
       accum = accum + w
   print(accum)

   # or, if you use two inputs for the range function

   sec_accum = 0
   for w in range(1,11):
       sec_accum = sec_accum + w
   print(sec_accum)

Debido a que la función de rango es exclusiva del número final, tenemos que usar 11 como entrada de la función.

Podemos usar el patrón de acumulación para contar el número de algo o para resumir un total. los
los ejemplos anteriores solo cubren cómo obtener la suma de una lista, pero también podemos contar cuántos elementos hay
en la lista si quisiéramos.

.. activecode:: ac6_6_3

   nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
   count = 0
   for w in nums:
       count = count + 1
   print(count)

En este ejemplo, no utilizamos ``w`` a pesar de que la variable iteradora (variable de bucle) es una parte necesaria de
construyendo un bucle for. En lugar de agregar el valor de ``w`` a ``contar``, le agregamos un 1,
porque estamos incrementando el valor de contar cuando iteramos cada vez a través del ciclo. Aunque en
En este escenario podríamos haber utilizado la función ``len``, hay otros casos más adelante donde len
no será útil pero aún tendremos que contar.

**Revisa tu entendimiento**

.. mchoice:: question6_6_1
   :answer_a: Imprimirá 10 en lugar de 55
   :answer_b: Causará un error de tiempo de ejecución
   :answer_c: Imprimirá 0 en lugar de 55
   :correct: a
   :feedback_a: La variable acum se restablecerá a 0 cada vez a través del bucle. Luego agregará el elemento actual. Solo contará el último artículo.
   :feedback_b: Las declaraciones de asignación son perfectamente legales dentro de los bucles y no causarán un error.
   :feedback_c: Buen pensamiento: la variable acum se restablecerá a 0 cada vez a través del bucle. Pero luego agrega el elemento actual.
   :practice: T

   Considere el siguiente código:

   .. code-block:: python

      nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
      for w in nums:
         accum = 0
         accum = accum + w
      print(accum)
   
   ¿Qué sucede si pones la inicialización de acum dentro del ciclo for como la primera instrucción en el bucle?

.. parsonsprob:: pp6_6_1

   Reorganice las instrucciones de código para que el programa sume los primeros n números impares donde el usuario proporciona n.
   -----
   n = int(input('How many odd numbers would you like to add together?'))
   thesum = 0
   oddnumber = 1
   =====
   for counter in range(n):
   =====
      thesum = thesum + oddnumber
      oddnumber = oddnumber + 2
   =====
   print(thesum)

.. activecode:: ac6_6_4
   :language: python
   :autograde: unittest
   :practice: T

   Escriba código para crear una lista de enteros del 0 al 52 y asigne esa lista a la variable ``números``. Debería usar una función especial de Python: no escriba la lista completa usted mismo. SUGERENCIA: ¡Puedes hacer esto en una línea de código!
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(numbers, range(53), "Testing that numbers is a list that contains the correct elements.")

   myTests().main()

.. activecode:: ac6_6_10
   :language: python
   :autograde: unittest
   :practice: T

   Cuente el número de caracteres en la cadena ``str1``. No use ``len()``. Guarde el número en la variable ``numb``.
   ~~~~
   str1 = "I like nonsense, it wakes up the brain cells. Fantasy is a necessary ingredient in living."

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testEight(self):
         self.assertEqual(numbs, 90, "Testing that numbs is assigned to correct values.")
         self.assertNotIn("len(", self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main()

.. activecode:: ac6_8_9
   :language: python
   :autograde: unittest
   :practice: T

   Cree una lista de números del 0 al 40 y asigne esta lista a la variable ``números``. Luego, acumule el total de los valores de la lista y asigne esa suma a la variable ``sum1``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testNineA(self):
         self.assertEqual(numbers, [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40], "Testing that numbers is assigned to correct values.")

      def testNineB(self):
         self.assertEqual(sum1, 820, "Testing that sum1 has the correct value.")

   myTests().main() 
