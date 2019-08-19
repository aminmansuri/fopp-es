..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: tuples-3-
   :start: 1

.. index::
    single: tuple; return value
    return; tuple

Tuplas como Valores de Retorno
------------------------------

Las funciones pueden devolver tuplas como valores de retorno. Esto es muy útil. A menudo queremos saber lo más alto y lo mejor de un bateador
puntaje más bajo, o queremos encontrar la media y la desviación estándar, o queremos saber el año, el mes y el
día, o si estamos haciendo algunos modelos ecológicos, podemos querer saber la cantidad de conejos y la cantidad de lobos en
una isla en un momento dado En cada caso, una función (que solo puede devolver un solo valor), puede crear una tupla única que contiene múltiples elementos.

Por ejemplo, podríamos escribir una función que devuelva tanto el área como la circunferencia de un círculo de radio r.

.. activecode:: ac12_3_1

    
    def circleInfo(r):
        """ Return (circumference, area) of a circle of radius r """
        c = 2 * 3.14159 * r
        a = 3.14159 * r * r
        return (c, a)

    print(circleInfo(10))

Una vez más, podemos aprovechar el empaque para que el código se vea un poco más legible en la línea 4

.. activecode:: ac12_3_2

    
    def circleInfo(r):
        """ Return (circumference, area) of a circle of radius r """
        c = 2 * 3.14159 * r
        a = 3.14159 * r * r
        return c, a

    print(circleInfo(10))

**Revisa tu Entendimiento**

.. activecode:: ac12_3_3
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **1.** Defina una función llamada ``information`` que tome como entrada, las variables ``name``, ``birth_year``, ``fav_color`` y ``hometown``. Debería devolver una tupla de estas variables en este orden.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(information("Sarah", 1996, "purple", "St. Louis"), ("Sarah", 1996, "purple", "St. Louis"), "Testing that information returns the correct tuple on input ('Sarah', 1996, 'purple', 'St. Louis')")

   myTests().main()

.. activecode:: ac12_3_4
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **2.** Defina una función llamada ``info`` con los siguientes parámetros obligatorios: ``name``, ``age``, ``birth_year``, ``year_in_college`` y ``hometown``. La función debe devolver una tupla que contiene toda la información ingresada.
   ~~~~

   def info():

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(info(name='Tina', age=20, birth_year=1996, year_in_college='sophomore', hometown='Detroit'), ('Tina', 20, 1996, 'sophomore', 'Detroit'), "Testing the function info on input: name='Tina', age=20, birth_year=1996, year_in_college='sophomore', hometown='Detroit'.")

   myTests().main()
