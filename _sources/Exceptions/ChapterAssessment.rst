..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


Evaluación del capítulo
=======================

.. activecode:: ac_exceptions_01
   :tags: Exceptions/intro-exceptions.rst
   :practice: T
   :topics: Exceptions/intro-exceptions.rst

   El siguiente código toma la lista de país, ``país``, y busca para ver si está en el diccionario ``oro`` que muestra algunos países que ganaron oro durante los Juegos Olímpicos. Sin embargo, este código actualmente no funciona. Agregue correctamente la cláusula try/except en el código para que llene correctamente la lista, ``country_gold``, con el número de oros ganados o la cadena "No obtuvo oro".
   ~~~~

   gold = {"US":46, "Fiji":1, "Great Britain":27, "Cuba":5, "Thailand":2, "China":26, "France":10}
   country = ["Fiji", "Chile", "Mexico", "France", "Norway", "US"]
   country_gold = []

   for x in country:
       country_gold.append(gold[x])
       country_gold.append("Did not get gold")

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOneA(self):
         self.assertEqual(country_gold, [1, 'Did not get gold', 'Did not get gold', 10, 'Did not get gold', 46], "Testing that country_gold is assigned to correct values")
      
   myTests().main()


.. activecode:: ac_exceptions_011
   :tags: Exceptions/intro-exceptions.rst

   Se proporciona un bucle con errores que intenta acumular algunos valores de algunos diccionarios. Inserte un try/except para que funcione el código.
   ~~~~

   di = [{"Puppies": 17, 'Kittens': 9, "Birds": 23, 'Fish': 90, "Hamsters": 49}, {"Puppies": 23, "Birds": 29, "Fish": 20, "Mice": 20, "Snakes": 7}, {"Fish": 203, "Hamsters": 93, "Snakes": 25, "Kittens": 89}, {"Birds": 20, "Puppies": 90, "Snakes": 21, "Fish": 10, "Kittens": 67}]
   total = 0
   for diction in di:
       total = total + diction['Puppies']

   print("Total number of puppies:", total)


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(total, 130, "Testing that total has the correct value.")

   myTests().main()


.. activecode:: ac_exceptions_02
   :tags:Exceptions/intro-exceptions.rst

   La lista, ``numb``, contiene enteros. escribe un código que llene la lista ``remainder`` con el resto de 36 dividido por cada número en ``numb``. Por ejemplo, el primer elemento debe ser 0, porque 36/6 no tiene resto. Si hay un error, haga que la cadena "Error" aparezca en el ``resto``.
   ~~~~

   numb = [6, 0, 36, 8, 2, 36, 0, 12, 60, 0, 45, 0, 3, 23]

   remainder = []

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOneA(self):
         self.assertEqual(remainder, [0, 'Error', 0, 4, 0, 0, 'Error', 0, 36, 'Error', 36, 'Error', 0, 13], "Testing that remainder is assigned to correct values.")
     
   myTests().main()

.. activecode:: ac_exceptions_021
   :tags: Exceptions/intro-exceptions.rst
   :practice: T
   :topics: Exceptions/intro-exceptions.rst

   Este código tiene errores, inserte un try/except para que el código funcione.
   ~~~~

   lst = [2,4,10,42,12,0,4,7,21,4,83,8,5,6,8,234,5,6,523,42,34,0,234,1,435,465,56,7,3,43,23]

   lst_three = []

   for num in lst:
       if 3 % num == 0:
           lst_three.append(num)


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(lst_three, [1,3], "Testing that lst_three has the correct values.")

   myTests().main()


.. activecode:: ac_exceptions_03
   :tags: Exceptions/intro-exceptions.rst
   :practice: T
   :topics: Exceptions/intro-exceptions.rst

   Escribe código que haga funcionar al código proveído con errores usando try/except. Cuando los códigos no funcionan en el try, agrega la cadena "Error" a la lista ``attempt``.
   ~~~~

   full_lst = ["ab", 'cde', 'fgh', 'i', 'jkml', 'nop', 'qr', 's', 'tv', 'wxy', 'z']

   attempt = []

   for elem in full_lst:
       attempt.append(elem[1])

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(attempt, ['b', 'd', 'g', 'Error', 'k', 'o', 'r', 'Error', 'v', 'x', 'Error'], "Testing that attempt has the correct values.")

   myTests().main()

.. activecode:: ac_exceptions_031
   :tags: Exceptions/intro-exceptions.rst
   :practice: T
   :topics: Exceptions/intro-exceptions.rst

   El siguiente código intenta agregar el tercer elemento de cada lista en ``conts`` a la nueva lista ``third_countries``. Actualmente, el código no funciona. Agregue una cláusula try/except para que el código se ejecute sin errores, y la cadena 'Continent no tiene 3 países' se agrega a ``países`` en lugar de producir un error.
   ~~~~

   conts = [['Spain', 'France', 'Greece', 'Portugal', 'Romania', 'Germany'], ['USA', 'Mexico', 'Canada'], ['Japan', 'China', 'Korea', 'Vietnam', 'Cambodia'], ['Argentina', 'Chile', 'Brazil', 'Ecuador', 'Uruguay', 'Venezuela'], ['Australia'], ['Zimbabwe', 'Morocco', 'Kenya', 'Ethiopa', 'South Africa'], ['Antarctica']]

   third_countries = []

   for c in conts: 
       third_countries.append(c[2])


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(third_countries, ['Greece', 'Canada', 'Korea', 'Brazil', 'Continent does not have 3 countries', 'Kenya', 'Continent does not have 3 countries'], "Testing that third_countries is created correctly.")

   myTests().main()   


.. activecode:: ac_exceptions_04
   :tags:Exceptions/intro-exceptions.rst
   :practice: T
   :topics: Exceptions/intro-exceptions.rst

   El siguiente código con errores imprime el valor del deporte en la lista ``deporte``. Use try/except para que el código se ejecute correctamente. Si el deporte no está en el diccionario, ``ppl_play``, agréguelo con el valor de 1.
   ~~~~

   sport = ["hockey", "basketball", "soccer", "tennis", "football", "baseball"]

   ppl_play = {"hockey":4, "soccer": 10, "football": 15, "tennis": 8}

   for x in sport:
      
        print(ppl_play[x])
       
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOneA(self):
         self.assertEqual(sorted(ppl_play.items()), [('baseball', 1), ('basketball', 1), ('football', 15), ('hockey', 4), ('soccer', 10), ('tennis', 8)], "Testing that ppl_play is assigned to correct values.")
     
   myTests().main()


.. activecode:: ac_exceptions_041
   :tags: Exceptions/intro-exceptions.rst
   :practice: T
   :topics: Exceptions/intro-exceptions.rst

   Se proporciona un bucle con errores que intenta acumular algunos valores de algunos diccionarios. Inserte un try/except para que pase el código. Si la clave no está allí, inicialícela en el diccionario y establezca el valor en cero.
   ~~~~

   di = [{"Puppies": 17, 'Kittens': 9, "Birds": 23, 'Fish': 90, "Hamsters": 49}, {"Puppies": 23, "Birds": 29, "Fish": 20, "Mice": 20, "Snakes": 7}, {"Fish": 203, "Hamsters": 93, "Snakes": 25, "Kittens": 89}, {"Birds": 20, "Puppies": 90, "Snakes": 21, "Fish": 10, "Kittens": 67}]
   total = 0
   for diction in di:
       total = total + diction['Puppies']

   print("Total number of puppies:", total)


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         accum = 0
         for diction in di:
              if 'Puppies' in diction:
                  accum += 1
         self.assertEqual(accum, 4, "Testing that every dictionary in di has the key 'Puppies'.")

   myTests().main()
