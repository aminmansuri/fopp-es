..  Copyright (C)  Jaclyn Cohen, Lauren Murphy, Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Evalución del Capítulo
=======================

.. activecode:: ac_ch13_01
   :practice: T
   :topics: Classes/ImprovingourConstructor.rst
   :tags: Classes/ImprovingourConstructor.rst

   Defina una clase llamada ``Bike`` que acepte una cadena y un float como entrada, y asigne esas entradas respectivamente a dos variables de instancia, ``color`` y ``price``. Asigne a la variable ``testOne`` una instancia de ``Bike`` cuyo color sea **azul** y cuyo precio sea **89.99**. Asigne a la variable ``testTwo`` una instancia de Bike cuyo color sea **púrpura** y cuyo precio sea **25.0**.
   ~~~~


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(testOne.color, "blue", "Testing that testOne has the correct color assigned.")
         self.assertEqual(testOne.price, 89.99, "Testing that testOne has the correct price assigned.")

      def testTwo(self):
         self.assertEqual(testTwo.color, "purple", "Testing that testTwo has the correct color assigned.")
         self.assertEqual(testTwo.price, 25.0, "Testing that testTwo has the correct color assigned.")

   myTests().main()

.. activecode:: ac_ch13_021
   :practice: T
   :topics: Classes/AddingOtherMethodstoourClass.rst
   :tags: Classes/ImprovingourConstructor.rst, Classes/AddingOtherMethodstoourClass.rst

   Cree una clase llamada ``AppleBasket`` cuyo constructor acepte dos entradas: una cadena que representa un color y un número que representa una cantidad de manzanas. El constructor debe inicializar dos variables de instancia: ``apple_color`` y ``apple_quantity``. Escriba un método de clase llamado ``increase`` que aumente la cantidad en ``1`` cada vez que se invoque. También debe escribir un método ``__str__`` para esta clase que devuelva una cadena del formato: ``"Una canasta de manzanas [la cantidad va aquí] [el color va aquí]".``"Una canasta de 4 manzanas rojas".`` O ``"Una canasta de 50 manzanas azules". ``(¡Escribir un código de prueba que cree instancias y asigne valores a las variables puede ayudarlo a resolver este problema!)``
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         tester = AppleBasket("red",4)
         self.assertEqual(tester.apple_quantity, 4, "Testing the initialization of the apple_quantity inst var.")
      def testTwo(self):   
         tester = AppleBasket("red",4)
         tester.increase()
         self.assertEqual(tester.apple_quantity, 5, "Testing the increase method")
      def testThree(self):
         tester = AppleBasket("green",17)
         self.assertEqual(tester.__str__(),"A basket of 17 green apples.")


   myTests().main()  


.. activecode:: ac_ch13_03
   :practice: T
   :topics: Classes/AddingOtherMethodstoourClass.rst
   :tags: Classes/AddingOtherMethodstoourClass.rst, Classes/ImprovingourConstructor.rst, Classes/ConvertinganObjecttoaString.rst

   Defina una clase llamada ``BankAccount`` que acepte el nombre que desea asociar con su cuenta bancaria en una cadena y un número entero que represente la cantidad de dinero en la cuenta. El constructor debe inicializar dos variables de instancia de esas entradas: ``name`` y ``amt``. Agregue un método de cadena para que cuando imprima una instancia de ``BankAccount``, vea ``"Su cuenta, [el nombre va aquí], tiene [start_amt va aquí] dólares"``. Cree una instancia de esta clase con ``"Bob"`` como el nombre y ``100`` como la cantidad. Guarde esto en la variable ``t1``.
   ~~~~

   

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(t1.__str__(), "Your account, Bob, has 100 dollars.", "Testing that t1 is assigned to correct value")

   myTests().main()
