..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: dictionaries-7-
   :start: 1

.. _accumulating_best_key:

Acumulando la mejor clave
--------------------------
               
Ahora, ¿qué pasa si queremos encontrar la *clave* asociada con el valor máximo? Sería bueno solo encontrar
el valor máximo como se indica arriba, y luego busque la clave asociada, pero los diccionarios no funcionan
de esa manera. Puede buscar el valor asociado con una clave, pero no la clave asociada con un valor.
(El motivo es que puede haber más de una clave que tenga el mismo valor).

El truco es hacer que el acumulador haga un seguimiento de la mejor clave hasta ahora en lugar del mejor valor hasta ahora.
Para simplificar, supongamos que hay al menos dos claves en el diccionario. Entonces, similar a nuestro
primera versión de calcular el máximo de una lista, podemos inicializar la mejor clave hasta ahora para ser la primera clave,
y recorrer las teclas, reemplazando la mejor hasta ahora cada vez que encontremos una mejor.

En el ejercicio a continuación, hemos proporcionado un código esqueleto. Vea si puede completarlo. Se proporciona una respuesta,
pero aprenderá más si intenta escribirlo usted mismo primero.

.. tabbed:: q0

   .. tab:: Question

      Escriba un programa que encuentre la clave en un diccionario que tenga el valor máximo. Si
      dos teclas tienen el mismo valor máximo, está bien imprimir cualquiera de las dos. Llenar
      en el código esqueleto
      
      .. actex:: ac10_7_1

         d = {'a': 194, 'b': 54, 'c':34, 'd': 44, 'e': 312, 'full':31}
         
         ks = d.keys()
         # iniciliza la variable best_key_so_far para que sea la primera clave en d
         for k in ks:
             # comprobar si el valor asociado con la clave actual es
             # mayor que el valor asociado con best_key_so_far
             # si es así, guarde la clave actual como la mejor hasta ahora
            
         print("key " + best_key_so_far + " Tiene el valor más alto, " + str(d[best_key_so_far]))
   
   .. tab:: Answer 
   
      .. activecode:: answer10_7_1
      
         d = {'a': 194, 'b': 54, 'c':34, 'd': 44, 'e': 312, 'full':31}
         
         ks = d.keys()
         best_key_so_far = list(ks)[0]  # Tiene que convertir ks en una lista real antes de usar [] para seleccionar un elemento
         for k in ks:
             if d[k] > d[best_key_so_far]:
                 best_key_so_far = k
            
         print("key " + best_key_so_far + " tiene el valor más alto, " + str(d[best_key_so_far]))
         
**Revisa tu entendimiento**

.. activecode:: ac10_7_2
   :language: python
   :autograde: unittest
   :practice: T

   **1.** Cree un diccionario llamado ``d`` que haga un seguimiento de todos los caracteres en la cadena ``placement`` y observe cuántas veces se vio cada carácter. Luego, encuentre la clave con el valor más bajo en este diccionario y asigne esa clave a ``min_value``.
   ~~~~
   placement = "Beaches are cool places to visit in spring however the Mackinaw Bridge is near. Most people visit Mackinaw later since the island is a cool place to explore."

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(d.keys()), sorted(['B', 'e', 'a', 'c', 'h', 's', ' ', 'r', 'o', 'l', 'p', 't', 'v', 'i', 'n', 'g', 'w', 'M', 'k', 'd', '.', 'x']), "Testing the keys were created correctly")
         self.assertEqual(sorted(d.values()), sorted([2, 17, 12, 8, 4, 10, 27, 7, 10, 8, 6, 8, 3, 13, 7, 2, 3, 3, 2, 2, 2, 1]), "Testing the values were created correctly")
      def testTwo(self):
         self.assertEqual(min_value, "x", "Testing that min_value has been correctly assigned")

   myTests().main()

.. activecode:: ac10_7_3
   :language: python
   :autograde: unittest
   :practice: T

   **5.** Cree un diccionario llamado ``lett_d`` que haga un seguimiento de todos los caracteres en la cadena ``product`` y observe cuántas veces se vio cada carácter. Luego, encuentre la clave con el valor más alto en este diccionario y asigne esa clave a ``max_value``.
   ~~~~
   product = "iphone and android phones"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(lett_d.items()), sorted([('h', 2), ('a', 2), (' ', 3), ('n', 4), ('d', 3), ('o', 3), ('i', 2), ('p', 2), ('e', 2), ('r', 1), ('s', 1)]), "Testing that lett_d has been created correctly.")
      def testTwo(self):
         self.assertEqual(max_value, "n", "Testing that max_value has been correctly assigned")

   myTests().main()
