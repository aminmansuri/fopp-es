..  Copyright (C)  Lauren Murphy, Susan Doong, Haley Yaremych, Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sort-7-
   :start: 1

Evaluación de capítulos
=======================

.. activecode:: ac18_7_1
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Sorting/Optionalkeyparameter

   Ordene la siguiente cadena alfabéticamente, **de z hasta a**, y asígnela a la variable ``sorted_letters``.
   ~~~~
   letters = "alwnfiwaksuezlaeiajsdl"
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted_letters, sorted(letters, reverse = True), "Testing that sorted_letters has the correct value.")

   myTests().main()


.. activecode:: ac18_7_2
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Sorting/Optionalreverseparameter

   Ordene la lista a continuación, ``animals``, en orden alfabético, a-z. Guarde la nueva lista como ``animals_sorted``.
   ~~~~

   animals = ['elephant', 'cat', 'moose', 'antelope', 'elk', 'rabbit', 'zebra', 'yak', 'salamander', 'deer', 'otter', 'minx', 'giraffe', 'goat', 'cow', 'tiger', 'bear']

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(animals_sorted, ['antelope', 'bear', 'cat', 'cow', 'deer', 'elephant', 'elk', 'giraffe', 'goat', 'minx', 'moose', 'otter', 'rabbit', 'salamander', 'tiger', 'yak', 'zebra'], "Testing that animals_sorted was created correctly.")

   myTests().main()

.. activecode:: assess_ac18_7_2a
    :language: python
    :practice: T
    :topics: Sorting/intro-SortingwithSortandSorted

    Escriba el código para reorganizar los strings en la lista ``winners`` para que estén en orden alfabético por nombre de la A a la Z.
    ~~~~
    winners = ['Kazuo Ishiguro', 'Rainer Weiss', 'Youyou Tu', 'Malala Yousafzai', 'Alice Munro', 'Alvin E. Roth']


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertEqual(winners, ['Alice Munro', 'Alvin E. Roth', 'Kazuo Ishiguro', 'Malala Yousafzai', 'Rainer Weiss', 'Youyou Tu'], "Testing that winners is set correctly.")

    myTests().main()

.. activecode:: assess_ac18_7_2b
    :language: python
    :practice: T
    :topics: Sorting/Optionalreverseparameter

    Escriba el código para cambiar el orden de la lista de ``winners``' de modo que ahora sea de Z a A, por nombre. Asigne esta lista a la variable ``z_winners``.
    ~~~~
    winners = ['Alice Munro', 'Alvin E. Roth', 'Kazuo Ishiguro', 'Malala Yousafzai', 'Rainer Weiss', 'Youyou Tu']


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertEqual(z_winners, ['Youyou Tu','Rainer Weiss', 'Malala Yousafzai','Kazuo Ishiguro', 'Alvin E. Roth', 'Alice Munro'], "Testing that z_winners is set correctly.")

    myTests().main()


.. activecode:: assess_ac18_7_2c
    :language: python
    :practice: T
    :topics: Sorting/Optionalkeyparameter

    Escriba el código para cambiar el orden de la lista de ``winners`` de modo que ahora sea de la A a la Z por *apellido*. Asigne esta lista a la variable ``z_winners``.
    ~~~~
    winners = ['Alice Munro', 'Alvin E. Roth', 'Kazuo Ishiguro', 'Malala Yousafzai', 'Rainer Weiss', 'Youyou Tu']


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertEqual(z_winners, ['Kazuo Ishiguro', 'Alice Munro', 'Alvin E. Roth', 'Youyou Tu', 'Rainer Weiss', 'Malala Yousafzai'], "Testing that z_winners is set correctly.")

    myTests().main()


.. activecode:: ac18_7_3
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Sorting/SortingaDictionary

   El diccionario, ``medals``, muestra el recuento de medallas para seis países durante los Juegos Olímpicos de Río. Ordene los nombres de los países para que aparezcan alfabéticamente. Guarde esta lista en la variable ``alphabetical``.
   ~~~~

   medals = {'Japan':41, 'Russia':56, 'South Korea':21, 'United States':121, 'Germany':42, 'China':70}
   
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(alphabetical, sorted(medals.keys()), "Testing that alphabetical value is assigned to correct values.")

   myTests().main()

.. activecode:: ac18_7_4
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Sorting/SortingaDictionary

   Dado el mismo diccionario, ``medals``, ahora ordena por el recuento de medallas. Guarde los tres países con el mayor recuento de medallas en la lista, ``top_three``.
   ~~~~

   medals = {'Japan':41, 'Russia':56, 'South Korea':21, 'United States':121, 'Germany':42, 'China':70}
   
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testThree(self):
         self.assertEqual(top_three, sorted(medals, key = lambda x: medals[x], reverse = True)[:3], "Testing that top_three value is assigned to correct values.")

   myTests().main()

.. activecode:: ac18_7_5
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Sorting/SortingaDictionary

   Hemos proporcionado el diccionario ``groceries``. Debe devolver una lista de sus claves, pero deben ordenarse por sus valores, de mayor a menor. Guarde la nueva lista como ``most_needed``.
   ~~~~

   groceries = {'apples': 5, 'pasta': 3, 'carrots': 12, 'orange juice': 2, 'bananas': 8, 'popcorn': 1, 'salsa': 3, 'cereal': 4, 'coffee': 5, 'granola bars': 15, 'onions': 7, 'rice': 1, 'peanut butter': 2, 'spinach': 9}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(most_needed, ['granola bars', 'carrots', 'spinach', 'bananas', 'onions', 'coffee', 'apples', 'cereal', 'salsa', 'pasta', 'peanut butter', 'orange juice', 'rice', 'popcorn'], "Testing that most_needed was created correctly.")

   myTests().main() 


.. activecode:: ac18_7_6
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Sorting/Optionalkeyparameter

   Cree una función llamada ``last_four`` que tome un número de ID y devuelva los últimos cuatro dígitos. Por ejemplo, el número 17573005 debería devolver 3005. Luego, use esta función para ordenar la lista de identificadores almacenados en la variable, ``ids``, de menor a mayor. Guarde esta lista ordenada en la variable, ``sorted_ids``. Sugerencia: recuerde que solo se pueden indexar cadenas, por lo que es posible que se necesiten conversiones.
   ~~~~

   def last_four(x):


   ids = [17573005, 17572342, 17579000, 17570002, 17572345, 17579329]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFour(self):
         self.assertEqual(sorted_ids, sorted(ids, key = last_four), "Testing that sorted_ids is assigned to correct values.")

   myTests().main()

.. activecode:: ac18_7_7
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Sorting/Optionalkeyparameter

   Ordene la lista ``ids`` por los últimos cuatro dígitos de cada id. Haga esto usando lambda y no usando una función definida. Guarde esta lista ordenada en la variable ``sorted_id``.
   ~~~~

   ids = [17573005, 17572342, 17579000, 17570002, 17572345, 17579329]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFive(self):
         self.assertEqual(sorted_id, [17570002, 17572342, 17572345, 17573005, 17579000, 17579329], "Testing that sorted_id is assigned to correct value.")
         self.assertIn("lambda", self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main()


.. activecode:: ac18_7_8
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Sorting/Optionalkeyparameter

   Ordene la siguiente lista por la segunda letra de la a a la z de cada elemento. Hazlo usando lambda. Asigne el valor resultante a la variable ``lambda_sort``.
   ~~~~

   ex_lst = ['hi', 'how are you', 'bye', 'apple', 'zebra', 'dance']

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(lambda_sort, sorted(ex_lst, key = lambda z: z[1]), "Testing that lambda_sort has the correct value.")
         self.assertIn("lambda", self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main()

