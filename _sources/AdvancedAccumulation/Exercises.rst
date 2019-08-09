..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

.. qnum::
   :prefix: AdAccum-6-
   :start: 1 

Ejercicios
----------


.. question:: q21_6_1

    .. tabbed:: q1

        .. tab:: Question

           .. actex:: ac21_6_1

              Escriba un código equivalente usando map en lugar de manual accumulation a continuación y asígnelo a la variable ``test``.
              ~~~~

              things = [3, 5, -4, 7]
   
              accum = []
              for thing in things:
                  accum.append(thing+1)
              print(accum)

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(test, [4, 6, -3, 8], "Testing whether test has been correctly defined.")
                      self.assertIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_2

    .. tabbed:: q2

        .. tab:: Question

           .. actex:: ac21_6_2

              Use manual accumulation para definir la función lengths a continuación.
              ~~~~

              def lengths(strings):
                  """lengths takes a list of strings as input and returns a list of numbers that are the lengths
                  of strings in the input list. Use manual accumulation!"""
                  # fill in this function's definition to make the test pass.
   
              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(lengths(["Hello", "hi", "bye"]), [5, 2, 3], "Testing whether lengths has been correctly defined.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_3

    .. tabbed:: q3

        .. tab:: Question

           .. actex:: ac21_6_3

              Ahora define lengths usando map.
              ~~~~
              def lengths(strings):
                  """lengths takes a list of strings as input and returns a list of numbers that are the lengths
                   of strings in the input list. Use map!"""
                   # fill in this function's definition to make the test pass.

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(lengths(["Hello", "hi", "bye"]), [5, 2, 3], "Testing whether lengths has been correctly defined.")
                      self.assertIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_4

    .. tabbed:: q4

        .. tab:: Question

           .. actex:: ac21_6_4

              Ahora define lengths usando list comprehension.
              ~~~~ 

              def lengths(strings):
                  """lengths takes a list of strings as input and returns a list of numbers that are the lengths
                  of strings in the input list. Use a list comprehension!"""
                  # fill in this function's definition to make the test pass.

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(lengths(["Hello", "hi", "bye"]), [5, 2, 3], "Testing whether lengths has been correctly defined.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()
   
.. question:: q21_6_5

    .. tabbed:: q5

        .. tab:: Question

           .. actex:: ac21_6_5

              Escriba una función llamada positives_Acc que reciba una lista de números como entrada (como [3, -1, 5, 7]) y devuelva una lista de solo los números positivos, [3, 5, 7], mediante manual accumulation.
              ~~~~ 

              things = [3, 5, -4, 7]
              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      things = [3, 5, -4, 7]
                      self.assertEqual(positives_Acc(things), [3, 5, 7], "Testing whether positives_Acc has been correctly defined.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_6

    .. tabbed:: q6

        .. tab:: Question

           .. actex:: ac21_6_6

              Escribe una función llamada positives_Fil que recibe una lista de cosas como entrada y devuelve una lista que contiene solo las cosas positivas, [3, 5, 7], utilizando la función filter.
              ~~~~ 

              things = [3, 5, -4, 7]
              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      things = [3, 5, -4, 7]
                      self.assertEqual(positives_Fil(things), [3, 5, 7], "Testing whether positives_Fil has been correctly defined.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_7

    .. tabbed:: q7

        .. tab:: Question

           .. actex:: ac21_6_7

              Escriba una función llamada positives_Li_Com que reciba una lista de cosas como entrada y devuelva una lista de solo las cosas positivas, [3, 5, 7], usando list comprehension.
              ~~~~ 

              things = [3, 5, -4, 7]
              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      things = [3, 5, -4, 7]
                      self.assertEqual(positives_Li_Com(things), [3, 5, 7], "Testing whether positives_Li_Com has been correctly defined.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_8

    .. tabbed:: q8

        .. tab:: Question

           .. actex:: ac21_6_8

              Define longwords usando manual accumulation.
              ~~~~ 

              def longwords(strings):
                  """Return a shorter list of strings containing only the strings with more than four characters. Use manual accumulation."""
                  # write your code here

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(longwords(["Hello", "hi", "bye", "wonderful"]), ["Hello", "wonderful"], "Testing whether longwords has been correctly defined.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_9

    .. tabbed:: q9

        .. tab:: Question

           .. actex:: ac21_6_9

              Define longwords usando filter.
              ~~~~ 

              def longwords_Fil(strings):
                  """Return a shorter list of strings containing only the strings with more than four characters. Use the filter function."""
                  # write your code here

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(longwords_Fil(["Hello", "hi", "bye", "wonderful"]), ["Hello", "wonderful"], "Testing whether longwords_Fil has been correctly defined.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_10

    .. tabbed:: q10

        .. tab:: Question

           .. actex:: ac21_6_10

              Define longwords usando list comprehension.
              ~~~~ 

              def longwords_Li_Comp(strings):
                  """Return a shorter list of strings containing only the strings with more than four characters. Use a list comprehension."""
                  # write your code here
              
              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                   def testOne(self):
                       self.assertEqual(longwords_Li_Comp(["Hello", "hi", "bye", "wonderful"]), ["Hello", "wonderful"], "Testing whether longwords_Li_Comp has been correctly defined.")
                       self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                       self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_11

    .. tabbed:: q11

        .. tab:: Question

           .. actex:: ac21_6_11

              Escribe una función llamada ``longlengths`` que devuelve las longitudes de las cadenas que tienen al menos 4 caracteres. Inténtalo usando list comprehension.
              ~~~~ 

              def longlengths(strings):
                  return None

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(longlengths(["Hello", "hi", "bye", "wonderful"]), [5, 9], "Testing whether longlengths has been correctly defined.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_12

    .. tabbed:: q12

        .. tab:: Question

           .. actex:: ac21_6_12

              Escribe una función llamada ``longlengths`` que devuelve las longitudes de esas cadenas que tienen al menos 4 caracteres. Inténtalo usando map and filter.
              ~~~~ 

              def longlengths(strings):
                  return None

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(longlengths(["Hello", "hi", "bye", "wonderful"]), [5, 9], "Testing whether longlengths has been correctly defined.")
                      self.assertIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_13

    .. tabbed:: q13

        .. tab:: Question

           .. actex:: ac21_6_13

              Escribe una función que tome una lista de números y devuelva la suma de los cuadrados de todos los números. Inténtalo usando un accumulator pattern.
              ~~~~ 

              def sumSquares(L):
                  return None

              nums = [3, 2, 2, -1, 1]

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                       self.assertEqual(sumSquares(nums), 19, "Testing whether sumSquares has been correctly defined.")
                       self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                       self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                       self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_14

    .. tabbed:: q14

        .. tab:: Question

           .. actex:: ac21_6_14

              Escribe una función que tome una lista de números y devuelva la suma de los cuadrados de todos los números. Inténtalo usando map y sum.
              ~~~~ 

              def sumSquares(L):
                  return None

              nums = [3, 2, 2, -1, 1]

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(sumSquares(nums), 19, "Testing whether sumSquares has been correctly defined.")
                      self.assertIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_15

    .. tabbed:: q15

        .. tab:: Question

           .. actex:: ac21_6_15

              Use la función zip para tomar las listas a continuación y convertirlas en una lista de tuplas, con todos los primeros elementos en la primera tupla, etc.
              ~~~~ 

              L1 = [1, 2, 3, 4]
              L2 = [4, 3, 2, 3]
              L3 = [0, 5, 0, 5]
   
              tups = []

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(tups, [(1, 4, 0), (2, 3, 5), (3, 2, 0), (4, 3, 5)], "Testing whether tups has been correctly defined.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_16

    .. tabbed:: q16

        .. tab:: Question

           .. actex:: ac21_6_16

              Use zip y map o list comprehension para hacer una lista que consista en el valor máximo para cada posición. Para L1, L2 y L3, terminaría con una lista [4, 5, 3, 5].
              ~~~~ 

              L1 = [1, 2, 3, 4]
              L2 = [4, 3, 2, 3]
              L3 = [0, 5, 0, 5]
   
              maxs = []

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(maxs, [4, 5, 3, 5], "Testing whether maxs has been correctly defined.")

              myTests().main()

.. question:: q21_6_17

    .. tabbed:: q17

        .. tab:: Question

           .. actex:: ac21_6_17

              Escribe código para asignar a la variable ``compri_sample`` Todos los valores de la clave en el diccionario ``tester`` si son Juniors. Hazlo usando list comprehension.
              ~~~~ 

              tester = {'info': [{"name": "Lauren", 'class standing': 'Junior', 'major': "Information Science"},{'name': 'Ayo', 'class standing': "Bachelor's", 'major': 'Information Science'}, {'name': 'Kathryn', 'class standing': 'Senior', 'major': 'Sociology'}, {'name': 'Nick', 'class standing': 'Junior', 'major': 'Computer Science'}, {'name': 'Gladys', 'class standing': 'Sophomore', 'major': 'History'}, {'name': 'Adam', 'major': 'Violin Performance', 'class standing': 'Senior'}]}

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(sorted(compri_sample), sorted(['Lauren', 'Nick']), "Testing that compri_sample has the correct values.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_18

    .. tabbed:: q18

        .. tab:: Question

           .. actex:: ac21_6_18

              **Desafío** El bucle for anidado incluye una lista de listas y combina los elementos en una sola lista. Haga lo mismo usando list comprehension para la lista ``L``. Asignarlo a la variable ``result2``.
              ~~~~ 

              def onelist(lst):
                  result = []
                  for each_list in lst:
                      for item in each_list:
                          result.append(item)
                  return result

              L = [["hi", "bye"], ["hello", "goodbye"], ["hola", "adios", "bonjour", "au revoir"]]

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testSeven(self):
                      self.assertEqual(result2, ['hi', 'bye', 'hello', 'goodbye', 'hola', 'adios', 'bonjour', 'au revoir'], "Testing that result2 is assigned to correct values")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
      
              myTests().main()

.. question:: q21_6_19

    .. tabbed:: q19

        .. tab:: Question

           .. actex:: ac21_6_19

              **Desafío:** Escribir código para asignar a la variable ``class_sched`` todos los valores de la clave ``important classes``. Hazlo usando list comprehension.
              ~~~~ 

              tester = {'info': [
                       {"name": "Lauren", 'class standing': 'Junior', 'major': "Information Science", 'important classes': ['SI 106', 'ENGLISH 125', 'SI 110', 'AMCULT 202']},
                       {'name': 'Ayo', 'class standing': "Bachelor's", 'major': 'Information Science', "important classes": ['SI 106', 'SI 410', 'PSYCH 111']}, 
                       {'name': 'Kathryn', 'class standing': 'Senior', 'major': 'Sociology', 'important classes': ['WOMENSTD 220', 'SOC 101', 'ENS 384']}, 
                       {'name': 'Nick', 'class standing': 'Junior', 'major': 'Computer Science', "important classes": ['SOC 101', 'AMCULT 334', 'EECS 281']}, 
                       {'name': 'Gladys', 'class standing': 'Sophomore', 'major': 'History', 'important classes': ['ENGLISH 125', 'HIST 259', 'ENGLISH 130']}, 
                       {'name': 'Adam', 'major': 'Violin Performance', 'class standing': 'Senior', 'important classes': ['PIANO 101', 'STUDIO 300', 'THEORY 229', 'MUSC 356']}]}


              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(sorted(class_sched), sorted(['SI 106', 'ENGLISH 125', 'SI 110', 'AMCULT 202','SI 106', 'SI 410', 'PSYCH 111', 'WOMENSTD 220', 'SOC 101', 'ENS 384', 'SOC 101', 'AMCULT 334', 'EECS 281', 'ENGLISH 125', 'HIST 259', 'ENGLISH 130', 'PIANO 101', 'STUDIO 300', 'THEORY 229', 'MUSC 356']), "Testing that class_sched has the correct list.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main()

.. question:: q21_6_20

    .. tabbed:: q20

        .. tab:: Question

           .. actex:: ac21_6_20

              **Desafío:** A continuación, proporcionamos una lista de listas que contienen números. Utilizando list comprehension, cree una nueva lista ``threes`` que contenga todos los números de la lista original que sean divisibles por 3. Esto se puede lograr en una línea de código.
              ~~~~ 

              nums = [[4, 3, 12, 10], [8, 7, 6], [5, 18, 15, 7, 11], [9, 4], [24, 20, 17], [3, 5]]

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(threes, [3, 12, 6, 18, 15, 9, 24, 3], "Testing that threes was created correctly.")
                      self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
                      self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

              myTests().main() 
