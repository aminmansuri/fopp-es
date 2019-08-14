..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-9-
   :start: 1

Patrón de Acumulación con Listas
----------------------------------

Podemos acumular valores en una lista en lugar de acumular un solo valor numérico. Considerar para
ejemplo, el siguiente programa que transforma una lista en una nueva lista al cuadrar cada uno de los valores.

.. activecode:: ac8_9_1

   nums = [3, 5, 8]
   accum = []
   for w in nums:
       x = w**2
       accum.append(x)
   print(accum)

Aquí, **inicializamos** la variable del acumulador para que sea una lista vacía, en la línea 2.

**iteramos** a través de la secuencia (línea 3). En cada iteración transformamos el elemento cuadrándolo (línea 4).

El paso **actualización** agrega el nuevo elemento a la lista que se almacena en la variable del acumulador
(línea 5). La actualización ocurre usando .append(), que muta la lista en lugar de usar un
reasignación En cambio, podríamos haber escrito ``accum = accum + [x]``, o ``accum += [x]``. En cualquiera
caso, necesitaríamos concatenar una lista que contiene x, no solo x en sí misma.

Al final, hemos acumulado una nueva lista de la misma longitud que la original, pero con cada elemento.
transformado en un nuevo elemento. Esto se llama una operación de mapeo, y la revisaremos en un capítulo posterior.

Observe cómo esto difiere de mutar la lista original, como vio en una sección anterior.

**Revisa tu entendimiento**

.. mchoice:: question8_9_1
   :answer_a: [4,2,8,6,5]
   :answer_b: [4,2,8,6,5,5]
   :answer_c: [9,7,13,11,10]
   :answer_d: Error, no puedes concatenar dentro de un append.
   :correct: c
   :feedback_a: 5 se agrega a cada elemento antes de ejecutar el append.
   :feedback_b: Hay demasiados elementos en esta lista. Solo se realizan 5 operaciones de adición.
   :feedback_c: Sí, el bucle for procesa cada elemento de la lista. 5 se agrega antes de agregarse a blist.
   :feedback_d: 5 se agrega a cada elemento antes de realizar la operación de agregar.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?

   .. code-block:: python

     alist = [4,2,8,6,5]
     blist = [ ]
     for item in alist:
        blist.append(item+5)
     print(blist)

.. mchoice:: question8_9_2
   :answer_a: [8,5,14,9,6]
   :answer_b: [8,5,14,9,6,12]
   :answer_c: [3,0,9,4,1,7,5]
   :answer_d: Error, no puede concatenar dentro de un append.
   :correct: b
   :feedback_a: ¡No olvides el último artículo!
   :feedback_b: Sí, el bucle for procesa cada elemento en lst. 5 se agrega antes de agregar lst[i] a blist.
   :feedback_c: 5 se agrega a cada elemento antes de realizar la operación append.
   :feedback_d: Está bien tener una expresión compleja dentro de la llamada al método append. La expresión `lst[i]+5` se evalúa completamente antes de realizar la operación append.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?

   .. code-block:: python

     lst= [3,0,9,4,1,7]
     new_list=[]
     for i in range(len(lst)):
        new_list.append(lst[i]+5)
     print(new_list)

.. activecode:: ac8_9_2
   :language: python
   :autograde: unittest
   :practice: T

   2. Para cada palabra en la lista ``verbs``, agregue una terminación -ing. Guarde esta nueva lista en una nueva lista llamada ``ing``.
   ~~~~
   verbs = ["kayak", "cry", "walk", "eat", "drink", "fly"]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testSix(self):
         self.assertEqual(ing, ['kayaking', 'crying', 'walking', 'eating', 'drinking', 'flying'], "Testing that the variable ing has the correct value.")

   myTests().main()

.. activecode:: ac8_9_3
   :language: python
   :autograde: unittest
   :practice: T

   Dada la lista de números, ``numbs``, cree una nueva lista de esos mismos números aumentados en 5. Guarde esta nueva lista en la variable ``newlist``.
   ~~~~
   numbs = [5, 10, 15, 20, 25]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFour(self):
         self.assertEqual(newlist, [10, 15, 20, 25, 30], "Testing that the newlist value contains the correct elements.")

   myTests().main()

.. activecode:: ac8_9_4
   :language: python
   :autograde: unittest
   :practice: T

   **Desafío** Ahora haga lo mismo que en el problema anterior, pero no cree una nueva lista. Sobrescriba la lista ``numbs`` para que cada uno de los números originales se incremente en 5.
   ~~~~
   numbs = [5, 10, 15, 20, 25]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFive(self):
         self.assertEqual(numbs, [10, 15, 20, 25, 30], "Testing that numbs is assigned to correct values.")

   myTests().main()

.. activecode:: ac8_9_5
   :language: python
   :autograde: unittest
   :practice: T

   Para cada número en ``lst_nums``, multiplique ese número por 2 y agréguelo a una nueva lista llamada ``larger_nums``.
   ~~~~
   lst_nums = [4, 29, 5.3, 10, 2, 1817, 1967, 9, 31.32]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(larger_nums, [8, 58, 10.6, 20, 4, 3634, 3934, 18, 62.64], "Testing that larger_nums has been created correctly." )

   myTests().main()

