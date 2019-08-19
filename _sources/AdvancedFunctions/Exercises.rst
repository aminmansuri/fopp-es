..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

.. qnum::
   :prefix: advfuncs-4-
   :start: 1

Ejercicios
-----------

.. question:: q16_4_1

    .. tabbed:: q1

        .. tab:: Question

           .. actex:: actex16_4_1

              1. Complete la lista de parámetros para g para que las invocaciones de g produzcan los valores de retorno especificados
              ~~~~ 

              def g():
                  return 2*x + y + z
              print(g(3))       # should output 10
              print(g(3, 2))    # should output 8
              print(g(3, 2, 1)) #should output 9

.. question:: q16_4_2

    .. tabbed:: q2

        .. tab:: Question

           .. actex:: actex16_4_2

              2. Defina una función llamada ``nums`` que tenga tres parámetros. El primer parámetro, un integer, debe ser requerido. Un segundo parámetro llamado ``mult_int`` debería ser opcional con un valor predeterminado de 5. El parámetro final, ``switch``, también debería ser opcional con un valor predeterminado de False. La función debe multiplicar los dos enteros y, si switch es True, debe cambiar el signo del producto antes de devolverlo.
              ~~~~ 

              def nums():
                  pass #remove this once you start writing the function

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(nums(5), 25, "Testing the function nums on input 5.")
                      self.assertEqual(nums(2, mult_int = 4), 8, "Testing the function nums on inputs 2, mult_int = 4.")
                      self.assertEqual(nums(3, switch = True), -15, "Testing the function nums on inputs 3, switch = True.")
                      self.assertEqual(nums(4, mult_int = 3, switch = True), -12, "Testing the function nums on inputs 4, mult_int = 3, switch = True.")
                      self.assertEqual(nums(0, switch = True), 0, "Testing the function nums on inputs 0, switch = True.")

              myTests().main()  

.. question:: q16_4_3

    .. tabbed:: q3

        .. tab:: Question

           .. actex:: actex16_4_3

              3. Escriba una función llamada ``juntos`` que tome tres parámetros, el primero es un parámetro requerido que es un número (entero o flotante), el segundo es un parámetro requerido que es una cadena y el tercero es un parámetro opcional cuyo valor predeterminado es " ". Lo que se devuelve es el primer parámetro, concatenado con el segundo, usando el tercero.
              ~~~~ 

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(together(12, 'cats'), '12 cats', "Testing that together returns the correct string on input (12, 'cats')")
                      self.assertEqual(together(17.3, 'birthday cakes'), '17.3 birthday cakes', "Testing that together returns the correct string on input (17.3, 'birthday cakes')")
                      self.assertEqual(together(3, 'dogs', ': '), '3: dogs', "Testing that together returns the correct string on input (3, 'dogs', ': ')")
                      self.assertEqual(together(493.3, 'beans', ' lima '), '493.3 lima beans', "Testing that together returns the correct string on input (493.3, 'beans', 'lima')")

              myTests().main()   
