..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: advfuncs-5-
   :start: 1

Evaluación de capítulos
========================

.. activecode:: ac15_5_1
   :language: python
   :autograde: unittest
   :practice: T

   Cree una función llamada ``mult`` que tenga dos parámetros, el primero es obligatorio y debe ser un número entero, el segundo es un parámetro opcional que puede ser un número o una cadena pero cuyo valor predeterminado es 6. La función debe devolver el primer parámetro multiplicado por el segundo.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(mult(2), 12, "Testing that mult returns the correct value on input (2)")
         self.assertEqual(mult(5,3), 15, "Testing that mult returns the correct value on input (3,5)")
         self.assertEqual(mult(4,"hello"), "hellohellohellohello", "testing that mult returns the correct value on input (4, 'hello'")

   myTests().main()


.. activecode:: ac15_5_2
   :language: python
   :autograde: unittest
   :practice: T

   La siguiente función, ``greeting``, no funciona. Corrija el código para que se ejecute sin error. Esto solo requiere un cambio en la definición de la función.
   ~~~~

   def greeting(greeting="Hello ", name, excl="!"):
       return greeting + name + excl

   print(greeting("Bob"))
   print(greeting(""))
   print(greeting("Bob", excl="!!!"))
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(greeting("Bob"), "Hello Bob!", "Testing that greeting('Bob') returns 'Hello Bob!'.")
         self.assertEqual(greeting(""), "Hello !", "Testing that greeting('') return 'Hello !'.")

   myTests().main()


.. activecode:: ac15_5_3
   :language: python
   :autograde: unittest
   :practice: T

   A continuación se muestra una función, ``sum``, que no funciona. Cambie la definición de la función para que el código funcione. La función aún debe tener un parámetro requerido, ``intx``, y un parámetro opcional, ``intz`` con un valor de defualt de 5.
   ~~~~

   def sum(intz=5, intx):
       return intz + intx

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sum(8, intz = 2), 10, "Testing the function sum on inputs 8, 2.")
         self.assertEqual(sum(12), 17, "Testing the function sum on input 12.")

   myTests().main()

.. activecode:: ac15_5_4
   :language: python
   :autograde: unittest
   :practice: T

   Escriba una función, ``test``, que incluya tres parámetros: un integer es requerido, un valor booleano opcional cuyo valor predeterminado es ``True`` y un diccionario opcional, llamado ``dict1``, cuyo valor predeterminado es ``{2:3, 4:5, 6:8}``. Si el parámetro booleano es True, la función debería probar para ver si el entero es una clave en el diccionario. El valor de esa clave debería ser devuelto. Si el parámetro booleano es False, devuelve el valor booleano "False".
   ~~~~
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testThree(self):
         self.assertEqual(test(2), 3, "Testing that test(2) returns 3")
         self.assertEqual(test(4, False), False, "Testing that test(4, False) returns False")
         self.assertEqual(test(5, dict1 = {5:4, 2:1}), 4, "Testing that test(5, dict1 = {5:4, 2:1}) returns 4")

   myTests().main()

.. activecode:: ac15_5_5
   :language: python
   :autograde: unittest
   :practice: T

   Escriba una función llamada ``CheckIfIn`` que tome tres parámetros. El primero es un parámetro obligatorio, que debería ser una cadena. El segundo es un parámetro opcional llamado ``direction`` con un valor predeterminado de ``True``. El tercero es un parámetro opcional llamado ``d`` que tiene un valor predeterminado de ``{'apple': 2, 'pear': 1, 'fruit': 19, 'orange': 5, 'banana': 3, 'uvas': 2, 'sandía': 7}``. Escriba la función ``CheckIfIn`` para que cuando el segundo parámetro sea ``True``, verifique si el primer parámetro es una clave en el tercer parámetro; si es así, devuelve ``True``, de lo contrario devuelve ``False``.

   Pero si el segundo parámetro es ``False``, entonces la función debe verificar si el primer parámetro *no* es una clave del tercero. Si *no lo es*, la función debería devolver ``True`` en este caso, y si lo es, debería devolver ``False``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(checkingIfIn('grapes'), True, "Testing that checkingIfIn returns the correct boolean on input 'grapes'")
         self.assertEqual(checkingIfIn('carrots'), False, "Testing that checkingIfIn returns the correct boolean on input 'carrots'")
         self.assertEqual(checkingIfIn('grapes', False), False, "Testing that checkingIfIn returns the correct boolean on input ('grapes', False)")
         self.assertEqual(checkingIfIn('carrots', False), True, "Testing that checkingIfIn returns the correct boolean on input ('carrots', False)")
         self.assertEqual(checkingIfIn('grapes', d = {'carrots': 1, 'peas': 9, 'potatos': 8, 'corn': 32, 'beans': 1}), False, "Testing that checkingIfIn returns the correct boolean on input ('grapes', d = {'carrots': 1, 'peas': 9, 'potatos': 8, 'corn': 32, 'beans': 1})")
         self.assertEqual(checkingIfIn('peas', d = {'carrots': 1, 'peas': 9, 'potatos': 8, 'corn': 32, 'beans': 1}), True, "Testing that checkingIfIn returns the correct boolean on input ('peas', d = {'carrots': 1, 'peas': 9, 'potatos': 8, 'corn': 32, 'beans': 1})")
         self.assertEqual(checkingIfIn('peas', False, {'carrots': 1, 'peas': 9, 'potatos': 8, 'corn': 32, 'beans': 1}), False, "Testing that checkingIfIn returns the correct boolean on input ('peas', False, {'carrots': 1, 'peas': 9, 'potatos': 8, 'corn': 32, 'beans': 1})")
         self.assertEqual(checkingIfIn('apples', False, {'carrots': 1, 'peas': 9, 'potatos': 8, 'corn': 32, 'beans': 1}), True, "Testing that checkingIfIn returns the correct boolean on input ('apples', False, {'carrots': 1, 'peas': 9, 'potatos': 8, 'corn': 32, 'beans': 1})")

   myTests().main()

.. activecode:: ac15_5_6
   :language: python
   :autograde: unittest
   :practice: T

   Hemos proporcionado la función ``CheckIfIn`` de modo que si el primer parámetro de entrada está en el tercer parámetro de entrada del diccionario, la función devuelve ese valor y, de lo contrario, devuelve ``False``. Siga las instrucciones en la ventana de código activo para asignaciones de variables específicas.
   ~~~~

   def checkingIfIn(a, direction = True, d = {'apple': 2, 'pear': 1, 'fruit': 19, 'orange': 5, 'banana': 3, 'grapes': 2, 'watermelon': 7}):
       if direction == True:
           if a in d:
               return d[a]
           else:
               return False
       else:
           if a not in d:
               return True
           else:
               return d[a]

   # Llame a la función para que devuelva False y asigne esa función a la variable c_false

   # Llame a la función para que devuelva True y asígnela a la variable c_true

   # Llame a la función para que el valor de fruit se asigne a la variable fruit_ans

   # Llame a la función usando el primer y tercer parámetro para que el valor 8 se asigne a la variable param_check

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(c_false, False, "Testing that c_false has the correct value")
      def testTwo(self):
         self.assertEqual(c_true, True, "Testing that c_true has the correct value")
      def testThree(self):
         self.assertEqual(fruit_ans, 19, "Testing that fruit_ans has the correct value")
      def testFour(self):
         self.assertEqual(param_check, 8, "Testing that param_check has the correct value")
         

   myTests().main()
