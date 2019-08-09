..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".
 
.. qnum::
   :prefix: AdAccum-5-
   :start: 1 
    
Zip
---
 
Otro patrón común con listas, además de accumulation, es recorrer un par de listas (o varias listas), haciendo
algo con todos los primeros elementos, luego algo con todos los segundos elementos, y así sucesivamente. Por ejemplo, dados dos
listas de números, puede sumarlos por pares, tomando [3, 4, 5] y [1, 2, 3] para obtener [4, 6, 8].

Una forma de hacerlo con un bucle for es recorrer los posibles valores de índice.

.. activecode:: ac21_5_1

   L1 = [3, 4, 5]
   L2 = [1, 2, 3]
   L3 = []
   
   for i in range(len(L1)):
       L3.append(L1[i] + L2[i])
   
   print(L3)
      
Ya has visto esta idea anteriormente para recorrer los elementos en una sola lista. En muchos otros lenguajes de programación.
esa es realmente la única forma de recorrer los elementos de una lista. En Python, sin embargo, nos hemos acostumbrado al ciclo for
donde la variable de iteración está vinculada sucesivamente a cada elemento de la lista, en lugar de solo a un número que se utiliza como
posición o índice en la lista.

¿No podemos hacer algo similar con pares de listas? Resulta que sí podemos.

La función ``zip`` toma varias listas y las convierte en una lista de tuplas (en realidad, un iterador, pero funcionan como
listas para los propósitos más prácticos), emparejar todos los primeros elementos como una tupla, todos los segundos elementos como otra tupla, y así.
Luego podemos iterar a través de esas tuplas y realizar alguna operación en todos los primeros elementos, todos los segundos, etc.

.. activecode:: ac21_5_2

   L1 = [3, 4, 5]
   L2 = [1, 2, 3]
   L4 = list(zip(L1, L2))
   print(L4)

Esto es lo que sucede cuando recorres las tuplas.
   
.. activecode:: ac21_5_3

   L1 = [3, 4, 5]
   L2 = [1, 2, 3]
   L3 = []
   L4 = list(zip(L1, L2))

   for (x1, x2) in L4:
       L3.append(x1+x2)
   
   print(L3)

O, simplificando y usando list comprehension:

.. activecode:: ac21_5_4

   L1 = [3, 4, 5]
   L2 = [1, 2, 3]
   L3 = [x1 + x2 for (x1, x2) in list(zip(L1, L2))]
   print(L3)
   
O, usando ``map`` y no desempacando la tupla (nuestro entorno en línea tiene problemas para desempacar la tupla en una expresión lambda):

.. activecode:: ac21_5_5

   L1 = [3, 4, 5]
   L2 = [1, 2, 3]
   L3 = map(lambda x: x[0] + x[1], zip(L1, L2))
   print(L3)

Considere una función llamada possible, que determina si una palabra aún es posible jugar en un juego de ahorcado, dadas las conjeturas que se han hecho y el estado actual de la palabra en blanco.

A continuación ofrecemos una función que cumple ese propósito.

.. activecode:: ac21_5_6

   def possible(word, blanked, guesses_made):
       if len(word) != len(blanked):
           return False
       for i in range(len(word)):
           bc = blanked[i]
           wc = word[i]
           if bc == '_' and wc in guesses_made:
               return False
           elif bc != '_' and bc != wc:
               return False
       return True
   
   print(possible("wonderwall", "_on__r__ll", "otnqurl"))
   print(possible("wonderwall", "_on__r__ll", "wotnqurl"))

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(possible("HELLO", "_ELL_", "ELJ"), True, "Testing whether possible has been correctly defined.")
         self.assertEqual(possible("HELLO", "_ELL_", "ELJH"), False, "Testing whether possible has been correctly defined.")
         self.assertEqual(possible("HELLO", "_E___", "ELJ"), False, "Testing whether possible has been correctly defined.")

   myTests().main()

Sin embargo, podemos reescribir eso usando ``zip``, para hacerlo un poco más comprensible.

.. activecode:: ac21_5_7

   def possible(word, blanked, guesses_made):
       if len(word) != len(blanked):
           return False
       for (bc, wc) in zip(blanked, word):
           if bc == '_' and wc in guesses_made:
               return False
           elif bc != '_' and bc != wc:
               return False
       return True

   print(possible("wonderwall", "_on__r__ll", "otnqurl"))
   print(possible("wonderwall", "_on__r__ll", "wotnqurl"))
   
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(possible("HELLO", "_ELL_", "ELJ"), True, "Testing whether possible has been correctly defined.")
         self.assertEqual(possible("HELLO", "_ELL_", "ELJH"), False, "Testing whether possible has been correctly defined.")
         self.assertEqual(possible("HELLO", "_E___", "ELJ"), False, "Testing whether possible has been correctly defined.")

   myTests().main()        

**Revisa tu entendimiento**

.. activecode:: ac21_5_8
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T
   
   **1.** Hemos proporcionado dos listas de números, ``L1`` y ``L2``. Utilizando zip y list comprehension, cree una nueva lista, ``L3``, que sume los dos números si el número de ``L1`` es mayor que 10 y el número de ``L2`` es menor que 5. Esto se puede lograr en una línea de código.
   ~~~~

   L1 = [1, 5, 2, 16, 32, 3, 54, 8, 100]
   L2 = [1, 3, 10, 2, 42, 2, 3, 4, 3]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testSix(self):
         self.assertEqual(L3, [18, 57, 103], "Testing that L3 is assigned to correct values")
         self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
      
   myTests().main()

