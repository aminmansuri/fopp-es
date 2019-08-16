..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-5-
   :start: 1

Una función que acumula
---------------------------

Ya hemos usado mucho la función ``len``. Si no fuera parte de Python, nuestras vidas como programadores habrían sido
mucho más difíciles.

Bueno, en realidad, no es mucho más difícil. Ahora que sabemos cómo definir funciones, podríamos definir ``len`` a nosotros mismos si
no existió. Anteriormente, hemos utilizado el patrón acumulador para contar el número de líneas en un archivo. Vamos a usar esa
misma idea y simplemente envolverla en una definición de función. Lo llamaremos ``mylen`` para distinguirlo del ``len`` real
que ya existe. En realidad *podríamos* llamarlo len, pero eso no sería una muy buena idea, porque reemplazaría
la función len original, y nuestra implementación puede no ser muy buena.

.. activecode:: ac11_5_1

   def mylen(seq):
       c = 0 # inicializar la variable de conteo a 0
       for _ in seq:
           c = c + 1   # incremente el contador para cada elemento en seq
       return c
      
   print(mylen("hola"))
   print(mylen([1, 2, 7]))


.. parsonsprob:: pp11_5_1

   Reorganice las declaraciones de código para que coincidan con la ventana de activecode anterior. (Este es un ejercicio para darse cuenta de dónde ocurre la sangría y dónde va la declaración de devolución.)
   
   -----
   def mylen(x):
   =====
       c = 0 # inicializar la variable de conteo a 0
   =====
       for y in x:
   =====
           c = c + 1   # incremente el contador para cada elemento en x
   =====
       return c
   =====      
   print(mylen("hola"))
   print(mylen([1, 2, 7]))

**Revisa tu entendimiento**

.. activecode:: ac11_5_2
   :language: python
   :autograde: unittest
   :practice: T

   **1.** Escriba una función llamada ``total`` que tome una lista de enteros como entrada y devuelva el valor total de todos esos enteros sumados.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(total([1, 2, 3, 4, 5]), 15, "Testing the total function on input [1, 2, 3, 4, 5].")
         self.assertEqual(total([0, 0, 0, 0]), 0, "Testing the total function on input [0, 0, 0, 0].")
         self.assertEqual(total([]), 0, "Testing the total function on input [].")
         self.assertEqual(total([2]), 2, "Testing the total function on input [2].")

   myTests().main() 

.. activecode:: ac11_5_3
   :language: python
   :autograde: unittest
   :practice: T

   **2.** Escriba una función llamada ``count`` que tome una lista de números como entrada y devuelva un recuento del número de elementos en la lista.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(count([]), 0, "Testing the function count with input []")
         self.assertEqual(count([1, 5, 9, -2, 9, 23]), 6, "Testing the function count with input [1, 5, 9, -2, 9, 23]")

   myTests().main()

