..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: AdAccum-3-
   :start: 1

Filter
-------

Ahora considere otro patrón común: revisar una lista y conservar solo aquellos elementos que cumplan ciertos criterios.
Esto se llama filtro.

.. activecode:: ac21_3_1

   def keep_evens(nums):
       new_list = []
       for num in nums:
           if num % 2 == 0:
               new_list.append(num)
       return new_list
      
   print(keep_evens([3, 4, 6, 7, 0, 1]))

Nuevamente, este patrón es tan común que Python ofrece una forma más compacta y general de hacerlo, la función ``filter``.
``filter`` toma dos argumentos, una función condicional y una secuencia. La función toma un elemento y devuelve True si el elemento cumple la condición.
Es llamado automáticamente para cada elemento de la secuencia. No tiene que inicializar un acumulador o iterar con un bucle for.

.. activecode:: ac21_3_2

   def keep_evens(nums):
       new_seq = filter(lambda num: num % 2 == 0, nums)
       return list(new_seq)
      
   print(keep_evens([3, 4, 6, 7, 0, 1]))

**Revisa tu entendimiento**

.. activecode:: ac21_3_3
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **1.** Escribe código para asignar a la variable ``filter_testing`` todos los elementos en lst_check que contienen una w usando filter.
   ~~~~

   lst_check = ['plums', 'watermelon', 'kiwi', 'strawberries', 'blueberries', 'peaches', 'apples', 'mangos', 'papaya']

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(filter_testing, ['watermelon', 'kiwi', 'strawberries'], "Testing that filter_testing has the correct values.")
         self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")


   myTests().main()

.. activecode:: ac21_3_4
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **2.** Usando filter, filtra ``lst`` para que solo contenga palabras que tengan la letra "o". Asignarlo a la variable ``lst2``. No hagas *hardcode* aquí.
   ~~~~

   lst = ["witch", "halloween", "pumpkin", "cat", "candy", "wagon", "moon"]
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(lst2, ['halloween', 'wagon', 'moon'], "Testing that lst is assigned to correct values.")
         self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")


   myTests().main()
