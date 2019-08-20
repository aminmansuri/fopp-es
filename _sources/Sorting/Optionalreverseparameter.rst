..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sort-2-
   :start: 1

Parámetro inverso opcional
--------------------------

La función ordenada toma algunos parámetros opcionales (consulte la página Parámetros opcionales). El primer parámetro opcional es
una función clave, que se describirá en la siguiente sección. El segundo parámetro opcional es un valor Boolean que
determina si se deben ordenar los elementos en orden inverso. Por defecto, es False, pero si lo configura en True, la lista aparecerá
ordenada en orden inverso.

.. activecode:: ac18_2_1

    L2 = ["Cherry", "Apple", "Blueberry"]
    print(sorted(L2, reverse=True))
    
.. note::

    Esta es una situación en la que es conveniente utilizar el mecanismo de palabras clave para proporcionar parámetros opcionales. Es
    posible proporcionar el valor True para el parámetro inverso sin nombrar ese parámetro, pero entonces tendríamos
    para proporcionar un valor para el segundo parámetro también, en lugar de permitir que se use el valor predeterminado del parámetro. Nosotros
    habríamos tenido que escribir ``sorted(L2, None, True)``. Eso es mucho más difícil para los humanos de leer y entender.


**Revisa tu entendimiendo**

.. activecode:: ac18_2_2
   :language: python
   :autograde: unittest
   :practice: T

   **1.** Ordene la lista, ``lst``, de mayor a menor. Guarde esta nueva lista en la variable ``lst_sorted``.
   ~~~~

   lst = [3, 5, 1, 6, 7, 2, 9, -2, 5]
   
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(lst_sorted, sorted(lst, reverse=True), "Testing that lst_sorted value is assigned to correct values.")

   myTests().main()
