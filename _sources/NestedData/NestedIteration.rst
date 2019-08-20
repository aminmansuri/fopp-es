..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: nested-3-
   :start: 1

Iteración Anidada
------------------

Cuando haya anidado estructuras de datos, especialmente listas y/o diccionarios, con frecuencia necesitará
bucles for anidados para atravesarlas.

.. activecode:: ac17_4_1

    nested1 = [['a', 'b', 'c'],['d', 'e'],['f', 'g', 'h']]
    for x in nested1:
        print("level1: ")
        for y in x:
            print("     level2: " + y)

La línea 3 se ejecuta una vez para cada lista de nivel superior, tres veces en total. Con cada sublista,
la línea 5 se ejecuta una vez para cada elemento en la sublista.
Intente recorrerlo en Codelens para asegurarse de comprender lo que hace la iteración anidada.

.. codelens:: clens17_4_1
    :python: py3

    nested1 = [['a', 'b', 'c'],['d', 'e'],['f', 'g', 'h']]
    for x in nested1:
        print("level1: ")
        for y in x:
            print("    level2: " + y)

**Revisa tu Entendimiento**

.. parsonsprob:: pp17_4_1

   Ahora intente reorganizar estos fragmentos de código para hacer una función que cuente todos los elementos *leaf* en una lista anidada como nested1 arriba, los elementos en el nivel más bajo de anidamiento (8 de ellos en nested1).
   -----
   def count_leaves(n):
   =====
       count = 0
   =====
       for L in n:
   =====
           for x in L:
   =====
               count = count + 1
   =====
       return count   

.. activecode:: ac17_4_2
   :language: python
   :autograde: unittest
   :practice: T

   **2.** A continuación, proporcionamos una lista de listas que contienen información sobre personas. Escriba el código para crear una nueva lista que contenga el apellido de cada persona y guarde esa lista como ``last_names``.

   ~~~~

   info = [['Tina', 'Turner', 1939, 'singer'], ['Matt', 'Damon', 1970, 'actor'], ['Kristen', 'Wiig', 1973, 'comedian'], ['Michael', 'Phelps', 1985, 'swimmer'], ['Barack', 'Obama', 1961, 'president']]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(last_names, ['Turner', 'Damon', 'Wiig', 'Phelps', 'Obama'], "Testing that last_names was created correctly.")

   myTests().main() 

.. activecode:: ac17_4_3
   :language: python
   :autograde: unittest
   :practice: T

   **3.** A continuación, proporcionamos una lista de listas llamadas ``L``. Use la iteración anidada para guardar cada cadena que contenga "b" en una nueva lista llamada ``b_strings``.

   ~~~~

   L = [['apples', 'bananas', 'oranges', 'blueberries', 'lemons'], ['carrots', 'peas', 'cucumbers', 'green beans'], ['root beer', 'smoothies', 'cranberry juice']]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(b_strings, ['bananas', 'blueberries', 'cucumbers', 'green beans', 'root beer', 'cranberry juice'], "Testing that b_strings was created correctly.")

   myTests().main() 
