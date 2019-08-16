..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-15-
   :start: 1

Evaluación de capítulos
=======================

.. activecode:: ac11_15_1
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Returningavaluefromafunction

   Escriba una función llamada ``int_return`` que toma un entero como entrada y devuelve el mismo entero.
   ~~~~
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(int_return(10), 10, "Testing that function int_return(10) returns 10")

   myTests().main()

.. activecode:: ac11_15_2
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Returningavaluefromafunction

   Escriba una función llamada ``add`` que tome cualquier número como entrada y devuelva esa suma con 2 agregados.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(add(-2), 0, "Testing that add(-2) returns 0")
         self.assertEqual(add(6), 8, "Testing that add(6) returns 8")
         self.assertEqual(add(4), 6, "Testing that add(4) returns 6")

   myTests().main()

.. activecode:: ac11_15_3
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Returningavaluefromafunction

   Escriba una función llamada ``change`` que tome cualquier string, agregue "Nice to meet you!" al final del argumento dado, y devuelve ese nuevo string.
   ~~~~
   
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testThree(self):
         self.assertEqual(change("I'm Bob. "), "I'm Bob. Nice to meet you!", "Tests that change('I'm Bob. '') returns 'I'm Bob. Nice to meet you!'")   
         self.assertEqual(change(""), "Nice to meet you!", "Tests that change() returns 'Nice to meet you!'")

   myTests().main()

.. activecode:: ac11_15_4
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Afunctionthataccumulates

   Escriba una función, ``accum``, que toma una lista de enteros como entrada y devuelve la suma de esos enteros.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFourA(self):
         self.assertEqual(accum([5]), 5, "Tests that accum([5]) returns 5")
         self.assertEqual(accum([]), 0, "Tests that accum([]) returns 0")
         self.assertEqual(accum([2,4,6,8]), 20, "Tests that accum([2,4,6,8]) returns 20")

   myTests().main()

.. activecode:: ac11_15_5
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Returningavaluefromafunction

   Escriba una función, ``length``, que tome una lista como entrada. Si la longitud de la lista es mayor o igual a 5, devuelva "Longer than 5". Si la longitud es inferior a 5, devuelva "Less than 5".
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFive(self):
         self.assertEqual(length([]), "Less than 5", "Tests that length([]) returns 'Less than 5'")
         self.assertEqual(length([2, 2]), "Less than 5", "Tests that length([2, 2]) returns 'Less than 5'")
         self.assertEqual(length([4, 4, 4, 3, 5, 6, 7, 8, 9]), "Longer than 5", "Tests that length([4, 4, 4, 3, 5, 6, 7, 8, 9]) returns 'Longer than 5'")
         self.assertEqual(length([1, 1, 1, 1, 1]), "Longer than 5", "Tests that length([1, 1, 1, 1, 1]) returns 'Longer than 5'")

   myTests().main()

.. activecode:: ac11_15_6
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Functionscancallotherfunctions

   Necesitará escribir dos funciones para este problema. La primera función, ``divide`` que toma cualquier número y devuelve ese mismo número dividido por 2. La segunda función llamada ``sum`` debe tomar cualquier número, dividirlo por 2 y agregar 6. Debería devolver esto un nuevo número. Debe llamar a la función ``divide`` dentro de la función ``sum``. No te preocupes por los decimales.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testSixA(self):
         self.assertEqual(divide(4), 2, "Tests that divide(4) returns 2")
      def testSixB(self):
         self.assertEqual(sum(4), 8, "Tests that sum(4) returns 8")
         self.assertEqual(sum(2), 7, "Tests that sum(2) returns 7")
         self.assertEqual(sum(-6), 3, "Tests that sum(-6) returns 3")
         self.assertEqual(sum(0), 6, "Tests that sum(0) returns 6")

   myTests().main()
