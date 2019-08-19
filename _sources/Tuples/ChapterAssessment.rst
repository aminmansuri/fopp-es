..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: tuples-8-
   :start: 1

Evaluación de capítulo
=======================

.. activecode:: ac12_8_1
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: Tuples/TuplePacking
      
   Crea una tupla llamada ``olympics`` con cuatro elementos: "Beijing", "Londres", "Río", "Tokio".
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(olympics, ('Beijing', 'London', 'Rio', 'Tokyo'), "Testing that olympics is assigned to correct values")

   myTests().main()


.. activecode:: ac12_8_2
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: Tuples/TuplePacking

   La lista a continuación, ``tuples_lst``, es una lista de tuplas. Cree una lista de los segundos elementos de cada tupla y asigne esta lista a la variable ``country``.
   ~~~~

   tuples_lst = [('Beijing', 'China', 2008), ('London', 'England', 2012), ('Rio', 'Brazil', 2016, 'Current'), ('Tokyo', 'Japan', 2020, 'Future')]
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(country, ['China', 'England', 'Brazil', 'Japan'], "Testing that third is assigned to correct values")

   myTests().main()

.. activecode:: ac12_8_3
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: Tuples/TuplePacking

   Con solo una línea de código, asigne las variables ``city``, ``country`` y ``year`` a los valores de la tupla ``olymp``.
   ~~~~

   olymp = ('Rio', 'Brazil', 2016)
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testThree(self):
         self.assertEqual(city, "Rio", "Testing that city is assigned to correct value.")
         self.assertEqual(country, "Brazil", "Testing that country is assigned to correct value.")
         self.assertEqual(year, 2016, "Testing that year is assigned to correct value.")

   myTests().main()

.. activecode:: ac12_8_4
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: Tuples/TuplesasReturnValues

   Defina una función llamada ``info`` con cinco parámetros: name, gender, age, bday_month y hometown. La función debería devolver una tupla con los cinco parámetros en ese orden.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFour(self):
         self.assertEqual(info("Sue", "Female", 20, "March", "Ann Arbor"), ("Sue", "Female", 20, "March", "Ann Arbor"), "Testing that info('Sue', 'Female', 20, 'March', 'Ann Arbor') returns('Sue', 'Female', 20, 'March', 'Ann Arbor')")

   myTests().main()

.. activecode:: ac12_8_5
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: Tuples/TupleAssignmentwithunpacking

   Se da el diccionario, ``gold``, que muestra el país y la cantidad de medallas de oro que han obtenido hasta ahora en los Juegos Olímpicos de 2016. Crea una lista, ``num_medals``, que contenga solo el número de medallas para cada país. Debe usar el método .items(). Nota: El método .items() proporciona una lista de tuplas. No utilice el método .keys().
   ~~~~

   gold = {'USA':31, 'Great Britain':19, 'China':19, 'Germany':13, 'Russia':12, 'Japan':10, 'France':8, 'Italy':8}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFive(self):
         self.assertEqual(sorted(num_medals), sorted([31, 19, 19, 13, 12, 10, 8, 8]), "Testing that num_medals is assigned to correct values.")
         self.assertNotIn('.keys()', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertIn('.items()', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('in gold:', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main()
