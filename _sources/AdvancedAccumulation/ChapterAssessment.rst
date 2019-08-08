..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: AdAccum-7-
   :start: 1

Evaluación del capítulo
=======================

.. activecode:: ac21_7_1
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: AdvancedAccumulation/map

   Escribie código para asignar a la variable ``map_testing`` todos los elementos en lst_check mientras agregas la cadena "Fruit: " al comienzo de cada elemento usando mapeo.
   ~~~~

   lst_check = ['plums', 'watermelon', 'kiwi', 'strawberries', 'blueberries', 'peaches', 'apples', 'mangos', 'papaya']

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(map_testing, ['Fruit: plums', 'Fruit: watermelon', 'Fruit: kiwi', 'Fruit: strawberries', 'Fruit: blueberries', 'Fruit: peaches', 'Fruit: apples', 'Fruit: mangos', 'Fruit: papaya'], "Testing that map_testing has the correct values.")
         self.assertIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")


   myTests().main()

.. activecode:: ac21_7_2
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: AdvancedAccumulation/filter

   A continuación, proporcionamos una lista de cadenas llamada ``countries``. Use el filtro para producir una lista llamada ``b_countries`` que solo contiene las cadenas de ``countries`` que comienzan con B.
   ~~~~

   countries = ['Canada', 'Mexico', 'Brazil', 'Chile', 'Denmark', 'Botswana', 'Spain', 'Britain', 'Portugal', 'Russia', 'Thailand', 'Bangladesh', 'Nigeria', 'Argentina', 'Belarus', 'Laos', 'Australia', 'Panama', 'Egypt', 'Morocco', 'Switzerland', 'Belgium']

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(b_countries, ['Brazil', 'Botswana', 'Britain', 'Bangladesh', 'Belarus', 'Belgium'], "Testing that b_countries is correct.")
         self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")


   myTests().main()

.. activecode:: ac21_7_3
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: AdvancedAccumulation/listcomp

   A continuación, proporcionamos una lista de tuplas que contienen los nombres de los personajes de Game of Thrones. Usando list comprehension, cree una lista de cadenas llamada ``first_names`` que contenga solo los nombres de todos en la lista original.
   ~~~~

   people = [('Snow', 'Jon'), ('Lannister', 'Cersei'), ('Stark', 'Arya'), ('Stark', 'Robb'), ('Lannister', 'Jamie'), ('Targaryen', 'Daenerys'), ('Stark', 'Sansa'), ('Tyrell', 'Margaery'), ('Stark', 'Eddard'), ('Lannister', 'Tyrion'), ('Baratheon', 'Joffrey'), ('Bolton', 'Ramsey'), ('Baelish', 'Peter')]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(first_names, ['Jon', 'Cersei', 'Arya', 'Robb', 'Jamie', 'Daenerys', 'Sansa', 'Margaery', 'Eddard', 'Tyrion', 'Joffrey', 'Ramsey', 'Peter'], "Testing that first_names is correct.")
         self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main() 


.. activecode:: ac21_7_4
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: AdvancedAccumulation/listcomp

   Use list comprehension para crear una lista llamada ``lst2`` que duplica cada elemento en la lista, ``lst``.
   ~~~~

   lst = [["hi", "bye"], "hello", "goodbye", [9, 2], 4]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFiveA(self):
         self.assertEqual(lst2, [['hi', 'bye', 'hi', 'bye'], 'hellohello', 'goodbyegoodbye', [9, 2, 9, 2], 8], "Testing that  lst2 is assigned to correct values")
         self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
      
   myTests().main()

.. activecode:: ac21_7_5
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: AdvancedAccumulation/listcomp

   A continuación, proporcionamos una lista de tuplas que contienen los nombres de los estudiantes y sus calificaciones finales en PYTHON 101. Utilizando list comprehension, cree una nueva lista ``aprobada`` que contenga los nombres de los estudiantes que aprobaron la clase (obtuvieron una calificación final de 70 o más).
   ~~~~

   students = [('Tommy', 95), ('Linda', 63), ('Carl', 70), ('Bob', 100), ('Raymond', 50), ('Sue', 75)]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(passed, ['Tommy', 'Carl', 'Bob', 'Sue'], "Testing that passed is correct.")
         self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main() 

.. activecode:: ac21_7_6
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: AdvancedAccumulation/zip

   Escribe código usando zip y filter para que estas listas (l1 y l2) se combinen en una gran lista y se asignen a la variable ``opuestos`` si ambos tienen más de 3 caracteres cada uno.
   ~~~~
   
   l1 = ['left', 'up', 'front']
   l2 = ['right', 'down', 'back']

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(opposites, [('left','right'), ('front','back')], "Testing that opposites has the correct list of tuples.")
         self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")


   myTests().main()

.. activecode:: ac21_7_7
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   :topics: AdvancedAccumulation/zip

   A continuación, proporcionamos una lista ``species`` y una lista ``population``. Use zip para combinar estas listas en una lista de tuplas llamada ``pop_info``. A partir de esta lista, cree una nueva lista llamada ``endangered`` que contenga los nombres de las especies cuyas poblaciones están por debajo de 2500.
   ~~~~

   species = ['golden retriever', 'white tailed deer', 'black rhino', 'brown squirrel', 'field mouse', 'orangutan', 'sumatran elephant', 'rainbow trout', 'black bear', 'blue whale', 'water moccasin', 'giant panda', 'green turtle', 'blue jay', 'japanese beetle']

   population = [10000, 90000, 1000, 2000000, 500000, 500, 1200, 8000, 12000, 2300, 7500, 100, 1800, 9500, 125000]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(pop_info, [('golden retriever', 10000), ('white tailed deer', 90000), ('black rhino', 1000), ('brown squirrel', 2000000), ('field mouse', 500000), ('orangutan', 500), ('sumatran elephant', 1200), ('rainbow trout', 8000), ('black bear', 12000), ('blue whale', 2300), ('water moccasin', 7500), ('giant panda', 100), ('green turtle', 1800), ('blue jay', 9500), ('japanese beetle', 125000)], "Testing that pop_info was created correctly.")
      def testTwo(self): 
         self.assertEqual(endangered, ['black rhino', 'orangutan', 'sumatran elephant', 'blue whale', 'giant panda', 'green turtle'], "Testing that endangered was created correctly.")
      def testThree(self):
         self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main()   
