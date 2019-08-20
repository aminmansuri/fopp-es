..  Copyright (C) Lauren Murphy, Susan Doong, Haley Yaremych, Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: nested-6-
   :start: 1

Evaluación del Capítulo
=======================

.. activecode:: ac17_6_1
   :language: python
   :autograde: unittest
   :practice: T
   :topics: NestedData/ListswithComplexItems

   La variable ``nested`` contiene una lista anidada. Asigne 'snake' a la variable ``output``  usando indexación.

   ~~~~

   nested = [['dog', 'cat', 'horse'], ['frog', 'turtle', 'snake', 'gecko'], ['hamster', 'gerbil', 'rat', 'ferret']]
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(output, "snake", "Testing that output is assigned to correct value")

   myTests().main()

.. activecode:: ac17_6_2
   :language: python
   :autograde: unittest
   :practice: T
   :topics: NestedData/ListswithComplexItems

   A continuación, se proporciona una lista de listas. Use in y not en pruebas para crear variables con valores booleanos. Ver comentarios para más instrucciones.

   ~~~~

   lst = [['apple', 'orange', 'banana'], [5, 6, 7, 8, 9.9, 10], ['green', 'yellow', 'purple', 'red']]

   # Prueba para ver si 'yellow' está en la tercera lista de lst. Guarda en la variable ``yellow``


   #Pruebe para ver si 4 está en la segunda lista de lst. Guardar en la variable ``four``


   #Pruebe para ver si 'orange' está en el primer elemento de lst. Guardar en variable ``orange``
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(yellow, True, "Testing that yellow is assigned to correct value")
      def testTwoB(self):
         self.assertEqual(four, False, "Testing that four is assigned to correct value")
      def testTwoC(self):
         self.assertEqual(orange, True, "Testing that orange is assigned to correct value")

   myTests().main()

.. activecode:: ac17_6_3
   :language: python
   :autograde: unittest
   :practice: T
   :topics: NestedData/ListswithComplexItems

   A continuación, proporcionamos una lista de listas. Úselo en declaraciones para crear variables con valores booleanos; consulte la ventana ActiveCode para obtener más instrucciones.

   ~~~~

   L = [[5, 8, 7], ['hello', 'hi', 'hola'], [6.6, 1.54, 3.99], ['small', 'large']]

   # Pruebe si 'hola' está en la lista L. Guardar en la variable test1

   # Prueba si [5, 8, 7] está en la lista L. Guardar en la variable test2

   # Prueba si 6.6 está en el tercer elemento de la lista L. Guardar en la variable test3

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testA(self):
         self.assertEqual(test1, False, "Testing that test1 has the correct value.")
      def testB(self):
         self.assertEqual(test2, True, "Testing that test2 has the correct value.")
      def testC(self):
         self.assertEqual(test3, True, "Testing that test3 has the correct value.")

   myTests().main()  


.. activecode:: ac17_6_4
   :language: python
   :autograde: unittest
   :practice: T
   :topics: NestedData/NestedDictionaries

   Se proporciona una estructura de datos anidada. Siga las instrucciones en los comentarios a continuación. No hagas *hard code*.

   ~~~~

   nested = {'data': ['finding', 23, ['exercises', 'hangout', 34]], 'window': ['part', 'whole', [], 'sum', ['math', 'calculus', 'algebra', 'geometry', 'statistics',['physics', 'chemistry', 'biology']]]}

   # Verifique si los datos de la cadena son una clave anidada, si es así, asigne True a los datos variables, de lo contrario, asigne False.

   # Compruebe si el número entero 24 está en el valor de los datos clave, si se asigna a la variable veinticuatro el valor de Verdadero, de lo contrario, Falso.

   # Verifique que la cadena 'entera' no esté en el valor de la ventana clave. Si no es así, asigne a la variable entera el valor de Verdadero, de lo contrario, Falso.

   # Verifique si la cadena 'física' es una clave en el diccionario anidado. Si es así, asigne a la variable física, el valor de Verdadero, de lo contrario, Falso.

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(data, True, "Testing that data has the correct value.")
      def testTwo(self):
         self.assertEqual(twentyfour, False, "Testing that twentyfour has the correct value.")
      def testThree(self):
         self.assertEqual(whole, False, "Testing that whole has the correct value.")
      def testFour(self):
         self.assertEqual(physics, False, "Testing that physics has the correct value.")

   myTests().main()


.. activecode:: ac17_6_5
   :language: python
   :autograde: unittest
   :practice: T
   :topics: NestedData/NestedDictionaries

   La variable ``nested_d`` contiene un diccionario anidado con los recuentos de medallas de oro para los cuatro principales países en los últimos tres Juegos Olímpicos. Asigne el valor del recuento de medallas de oro de Gran Bretaña de los Juegos Olímpicos de Londres a la variable ``london_gold``. Usar indexación. No hagas *hardcode*.

   ~~~~

   nested_d = {'Beijing':{'China':51, 'USA':36, 'Russia':22, 'Great Britain':19}, 'London':{'USA':46, 'China':38, 'Great Britain':29, 'Russia':22}, 'Rio':{'USA':35, 'Great Britain':22, 'China':20, 'Germany':13}}
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(london_gold, 29, "Testing that london_gold is assigned to correct value")

   myTests().main()


.. activecode:: ac17_6_6
   :language: python
   :autograde: unittest
   :practice: T
   :topics: NestedData/NestedDictionaries

   A continuación, proporcionamos un diccionario anidado. Indexe en el diccionario para crear las variables que hemos enumerado en la ventana ActiveCode.

   ~~~~

   sports = {'swimming': ['butterfly', 'breaststroke', 'backstroke', 'freestyle'], 'diving': ['springboard', 'platform', 'synchronized'], 'track': ['sprint', 'distance', 'jumps', 'throws'], 'gymnastics': {'women':['vault', 'floor', 'uneven bars', 'balance beam'], 'men': ['vault', 'parallel bars', 'floor', 'rings']}}

   # Asignar la cadena 'backstroke' al nombre v1

   # Asignar la cadena 'platform' al nombre v2

   # Asigne la lista ['vault', 'floor', 'uneven bars', 'balance beam'] al nombre v3

   # Asignar la cadena 'rings' al nombre v4

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testA(self):
         self.assertEqual(v1, 'backstroke', "Testing that v1 was created correctly.")
         self.assertNotIn("v1 = 'backstroke'", self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('v1 = "backstroke"', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
      def testB(self):
         self.assertEqual(v2, 'platform', "Testing that v2 was created correctly.")
         self.assertNotIn('v2 = "platform"', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn("v2 = 'platform'", self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
      def testC(self):
         self.assertEqual(v3, ['vault', 'floor', 'uneven bars', 'balance beam'], "Testing that v3 was created correctly.")
         self.assertNotIn("v3 = ['vault', 'floor', 'uneven bars', 'balance beam']", self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
      def testD(self):
         self.assertEqual(v4, 'rings', "Testing that v4 was created correctly.")
         self.assertNotIn("v4 = 'rings'", self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('v4 = "rings"', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main() 


.. activecode:: ac17_6_7
   :language: python
   :autograde: unittest
   :practice: T
   :topics: NestedData/NestedIteration

   Dado el diccionario, ``nested_d``, guarde el recuento de medallas para los EE. UU. De las tres Olimpiadas en el diccionario en la lista ``US_count``.

   ~~~~

   nested_d = {'Beijing':{'China':51, 'USA':36, 'Russia':22, 'Great Britain':19}, 'London':{'USA':46, 'China':38, 'Great Britain':29, 'Russia':22}, 'Rio':{'USA':35, 'Great Britain':22, 'China':20, 'Germany':13}}

   US_count = []
      

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFour(self):
         self.assertEqual(sorted(US_count), [35, 36, 46], "Testing that US_count is assigned to correct values.")

   myTests().main()


.. activecode:: ac17_6_8
   :language: python
   :autograde: unittest
   :practice: T
   :topics: NestedData/NestedIteration

   Repite el contenido de ``l_of_l`` y asigna el tercer elemento de la sublista a una nueva lista llamada ``third``.

   ~~~~

   l_of_l = [['purple', 'mauve', 'blue'], ['red', 'maroon', 'blood orange', 'crimson'], ['sea green', 'cornflower', 'lavender', 'indigo'], ['yellow', 'amarillo', 'mac n cheese', 'golden rod']]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(third, ['blue', 'blood orange', 'lavender', 'mac n cheese'], "Testing that third has the correct list assigned to it.")

   myTests().main()


.. activecode:: ac17_6_9
   :language: python
   :autograde: unittest
   :practice: T
   :topics: NestedData/NestedIteration

   A continuación se incluye una lista de listas de atletas. Cree una lista, ``t``, que guarde solo el nombre del atleta si contiene la letra "t". Si no contiene la letra "t", guarde el nombre del atleta en la lista ``other``.

   ~~~~

   athletes = [['Phelps', 'Lochte', 'Schooling', 'Ledecky', 'Franklin'], ['Felix', 'Bolt', 'Gardner', 'Eaton'], ['Biles', 'Douglas', 'Hamm', 'Raisman', 'Mikulak', 'Dalton']]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFive(self):
         self.assertEqual(t, ['Lochte', 'Bolt', 'Eaton', 'Dalton'], "Testing that t is assigned to correct values.")
      def testFiveA(self):
         self.assertEqual(other, ['Phelps', 'Schooling', 'Ledecky', 'Franklin', 'Felix', 'Gardner', 'Biles', 'Douglas', 'Hamm', 'Raisman', 'Mikulak'], "Testing that other is assigned to correct values.")

   myTests().main()
