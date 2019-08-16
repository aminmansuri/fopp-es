..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: dictionaries-9-
   :start: 1

Evaluación de capítulos
------------------------

Evaluación - Diccionarios
==========================

.. activecode:: ac10_9_1
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/intro-Dictionaries

   A mitad de camino durante los Juegos Olímpicos de Río, Estados Unidos tenía 70 medallas, Gran Bretaña tenía 38 medallas, China tenía 45 medallas, Rusia tenía 30 medallas y Alemania tenía 17 medallas. Cree un diccionario asignado a la variable ``medal_count`` con los nombres de los países como claves y el número de medallas que el país tenía como valor de cada clave.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(medal_count.items()), sorted([('China', 45), ('Germany', 17), ('Great Britain', 38), ('Russia', 30), ('United States', 70)]), "Testing that the medal_count dictionary has the correct key-value pairs")

   myTests().main()

.. activecode:: ac10_9_2
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/intro-Dictionaries

   Dado el diccionario ``swimmers``, agregue un par clave-valor adicional al diccionario con ``"Phelps"`` como clave y el número entero ``23`` como valor. No reescribas todo el diccionario.
   ~~~~

   swimmers = {'Manuel':4, 'Lochte':12, 'Adrian':7, 'Ledecky':5, 'Dirado':4}
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(sorted(swimmers.items()), sorted([('Adrian', 7), ('Dirado', 4), ('Manuel',4), ('Ledecky', 5), ('Lochte', 12), ('Phelps', 23)]), "Testing that swimmers is assigned to correct value.")

   myTests().main()

.. activecode:: ac10_9_3
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/intro-Dictionaries

   Agregue la cadena "hockey" como clave del diccionario ``sports_periods`` y asígnele el valor 3. No reescriba todo el diccionario.
   ~~~~

   sports_periods = {'baseball': 9, 'basketball': 4, 'soccer': 4, 'cricket': 2}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(sports_periods.items()), sorted([('baseball', 9), ("basketball", 4), ('soccer', 4), ('cricket', 2), ('hockey', 3)]), "Testing that sports_period was created correctly.")


   myTests().main()

.. activecode:: ac10_9_4
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/intro-Dictionaries

   El diccionario ``golds`` contiene información sobre cuántas medallas de oro ganó cada país en los Juegos Olímpicos de 2016. Pero hoy, España ganó 2 medallas de oro más. Actualice ``golds`` para reflejar esta información.
   ~~~~

   golds = {"Italy": 12, "USA": 33, "Brazil": 15, "China": 27, "Spain": 19, "Canada": 22, "Argentina": 8, "England": 29}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(golds.items()), sorted([("Italy", 12), ("USA", 33), ("Brazil", 15), ("China", 27), ("Spain", 21), ("Canada", 22), ("Argentina", 8), ("England", 29)]), "Testing that golds has been updated correctly.")

   myTests().main()


.. activecode:: ac10_9_5
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/Dictionarymethods

   Cree una lista de los países que están en el diccionario ``golds`` y asigne esa lista al nombre de la variable ``countries``. No hagas *hard code*.
   ~~~~

   golds = {"Italy": 12, "USA": 33, "Brazil": 15, "China": 27, "Spain": 19, "Canada": 22, "Argentina": 8, "England": 29}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(countries), sorted(["Italy", "USA", "Brazil", "China", "Spain", "Canada", "Argentina", "England"]), "Testing that countries has been created correctly.")

   myTests().main()


.. activecode:: ac10_9_6
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/intro-Dictionaries

   Se proporciona el diccionario, ``medal_count``, que enumera los países y sus respectivos recuentos de medallas en la mitad de los Juegos Olímpicos de Río 2016. Usando la mecánica del diccionario, asigne el valor de conteo de medallas para ``"Bielorrusia"`` a la variable ``bielorrusia``. No hagas *hardcode* en esto.
   ~~~~

   medal_count = {'United States': 70, 'Great Britain':38, 'China':45, 'Russia':30, 'Germany':17, 'Italy':22, 'France': 22, 'Japan':26, 'Australia':22, 'South Korea':14, 'Hungary':12, 'Netherlands':10, 'Spain':5, 'New Zealand':8, 'Canada':13, 'Kazakhstan':8, 'Colombia':4, 'Switzerland':5, 'Belgium':4, 'Thailand':4, 'Croatia':3, 'Iran':3, 'Jamaica':3, 'South Africa':7, 'Sweden':6, 'Denmark':7, 'North Korea':6, 'Kenya':4, 'Brazil':7, 'Belarus':4, 'Cuba':5, 'Poland':4, 'Romania':4, 'Slovenia':3, 'Argentina':2, 'Bahrain':2, 'Slovakia':2, 'Vietnam':2, 'Czech Republic':6, 'Uzbekistan':5}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testSix(self):
         self.assertEqual(belarus, 4, "Testing that belarus is assigned the correct value.")

   myTests().main()


.. activecode:: ac10_9_7
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/intro-Dictionaries

   El diccionario ``total_golds`` contiene el número total de medallas de oro que los países han ganado en el transcurso de la historia. Use la mecánica del diccionario para encontrar el número de oros que Chile ha ganado, y asigne ese número al nombre de la variable ``chile_golds``. ¡No hagas *hardcode* aquí!
   ~~~~

   total_golds = {"Italy": 114, "Germany": 782, "Pakistan": 10, "Sweden": 627, "USA": 2681, "Zimbabwe": 8, "Greece": 111, "Mongolia": 24, "Brazil": 108, "Croatia": 34, "Algeria": 15, "Switzerland": 323, "Yugoslavia": 87, "China": 526, "Egypt": 26, "Norway": 477, "Spain": 133, "Australia": 480, "Slovakia": 29, "Canada": 22, "New Zealand": 100, "Denmark": 180, "Chile": 13, "Argentina": 70, "Thailand": 24, "Cuba": 209, "Uganda": 7,  "England": 806, "Denmark": 180, "Ukraine": 122, "Bahamas": 12}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(chile_golds, 13, "Testing that chile_golds has been set correctly.")

   myTests().main()


.. activecode:: ac10_9_8
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/intro-Dictionaries

   Se proporciona un diccionario llamado ``US_medals`` que tiene los primeros 70 metales que Estados Unidos ganó en 2016, y en qué categoría lo ganó. Utilizando la mecánica del diccionario, asigne el valor de la clave ``"Fencing"`` a una variable ``fencing_value``. Recuerda, no codifiques esto.
   ~~~~

   US_medals = {"Swimming": 33, "Gymnastics": 6, "Track & Field": 6, "Tennis": 3, "Judo": 2, "Rowing": 2, "Shooting": 3, "Cycling - Road": 1, "Fencing": 4, "Diving": 2, "Archery": 2, "Cycling - Track": 1, "Equestrian": 2, "Golf": 1, "Weightlifting": 1}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(fencing_value, US_medals.get("Fencing"), "Testing that fencing_value was set correctly.")        

   myTests().main()

Evaluación - Acumulación de Diccionario
========================================

.. activecode:: ac10_9_9
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/AccumulatingResultsFromaDictionary

   El diccionario ``Junior`` muestra un horario para un semestre de tercer año. La clave es el nombre del curso y el valor es el número de créditos. Encuentre el número total de créditos tomados este semestre y asígnelo a la variable ``credits``. No haaga *hardcode* en esto: ¡use la acumulación de diccionario!
   ~~~~
   Junior = {'SI 206':4, 'SI 310':4, 'BL 300':3, 'TO 313':3, 'BCOM 350':1, 'MO 300':3}
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(credits, 18, "Testing that credits is assigned to correct values")

   myTests().main()

.. activecode:: ac10_9_10
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/AccumulatingResultsFromaDictionary

   Cree un diccionario, ``freq``, que muestre cada carácter en la cadena ``str1`` como la clave y su frecuencia como el valor.
   ~~~~
   str1 = "peter piper picked a peck of pickled peppers"
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(sorted(freq.items()), sorted([(' ', 7), ('a', 1), ('c', 3), ('d', 2), ('e', 8), ('f', 1), ('i', 3), ('k', 3), ('l', 1), ('o', 1), ('p', 9), ('r', 3), ('s', 1), ('t', 1)]), "Testing that freq is correct.")

   myTests().main()


.. activecode:: ac10_9_11
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/AccumulatingResultsFromaDictionary

   Se proporciona una cadena guardada en el nombre de la variable ``s1``. Cree un diccionario llamado ``counts`` que contenga cada letra en ``s1`` y la cantidad de veces que ocurra.
   ~~~~
   s1 = "hello"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(counts.items()), [('e', 1), ('h', 1), ('l', 2), ('o', 1)], "Testing that counts was created correctly.")

   myTests().main()

.. activecode:: ac10_9_12
   :language: python
   :autograde: unittest

   Cree un diccionario, ``freq_words``, que muestre cada palabra en la cadena ``str1`` como la clave y su frecuencia como el valor.
   ~~~~
   str1 = "I wish I wish with all my heart to fly with dragons in a land apart"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testThree(self):
         self.assertEqual(sorted(freq_words.items()), sorted([('a', 1), ('I', 2), ('wish', 2), ('with', 2), ('all', 1), ('my', 1), ('heart', 1), ('to', 1), ('fly', 1), ('dragons', 1), ('in', 1), ('land', 1), ('apart', 1)]), "Testing that freq_words was created correctly.")

   myTests().main()


.. activecode:: ac10_9_13
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/AccumulatingResultsFromaDictionary

   Cree un diccionario llamado ``wrd_d`` a partir de la cadena ``sent``, de modo que la clave sea una palabra y el valor sea cuántas veces haya visto esa palabra.
   ~~~~
   sent = "Singing in the rain and playing in the rain are two entirely different situations but both can be good"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(wrd_d.items()), sorted([('Singing', 1), ('in', 2), ('the', 2), ('rain', 2), ('and', 1), ('playing', 1), ('are', 1), ('two', 1), ('entirely', 1), ('different', 1), ('situations', 1), ('but', 1), ('both', 1), ('can', 1), ('be', 1), ('good', 1)]), "Testing that wrd_d has been created correctly.")

   myTests().main()


.. activecode:: ac10_9_14
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/AccumulatingtheBestKey

   Cree el diccionario ``characters`` que muestra cada carácter de la cadena ``sally`` y su frecuencia. Luego, encuentre la letra más frecuente basada en el diccionario. Asigne esta letra a la variable ``best_char``.
   ~~~~
   sally = "sally sells sea shells by the sea shore"
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFourA(self):
         self.assertEqual(sorted(characters.items()), sorted([('s', 8), ('o', 1), ('e', 6), ('t', 1), ('h', 3), ('a', 3), ('r', 1), ('l', 6), ('y', 2), (' ', 7), ('b', 1)]), "Testing that characters has correct values." )

      def testFourB(self):
         self.assertEqual(best_char, "s", "Testing that best_char is assigned to correct value.")

   myTests().main()

.. activecode:: ac10_9_15
   :language: python
   :autograde: unittest

   Haga lo mismo que arriba pero ahora encuentre la letra menos frecuente. Cree el diccionario ``characters`` que muestra cada carácter de la cadena ``sally`` y su frecuencia. Luego, encuentre la letra menos frecuente en la cadena y asigne la letra a la variable ``worts_char``.
   ~~~~
   sally = "sally sells sea shells by the sea shore and by the road"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFiveA(self):
         self.assertEqual(sorted(characters.items()), sorted([('s', 8), ('a', 5), ('l', 6), ('y', 3), (' ', 11), ('e', 7), ('h', 4), ('b', 2), ('t', 2), ('o', 2), ('r', 2), ('n', 1), ('d', 2)]), "Testing that characters has been updated correctly.")

      def testFourB(self):
         self.assertEqual(worst_char, "n", "Testing that worst_char is assigned to correct value.")

   myTests().main()

.. activecode:: ac10_9_16
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/AccumulatingResultsFromaDictionary

   Cree un diccionario llamado ``letter_counts`` que contenga cada letra y la cantidad de veces que aparece en ``string1``. **Desafío:** Las letras no deben contarse por separado como mayúsculas y minúsculas. En su lugar, todos ellos deben contarse como minúsculas.
   ~~~~
   string1 = "There is a tide in the affairs of men, Which taken at the flood, leads on to fortune. Omitted, all the voyage of their life is bound in shallows and in miseries. On such a full sea are we now afloat. And we must take the current when it serves, or lose our ventures."

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(letter_counts['t'], 19, "Testing that the letter 't' has the correct value.")

      def testTwo(self):
         self.assertEqual(letter_counts['w'], 6, "Testing that the letter 'w' has the correct value.")

      def testThree(self):
         self.assertEqual(letter_counts['o'], 17, "Testing that the letter 'o' has the correct value.")

      def testFour(self):
         self.assertEqual(letter_counts['a'], 17, "Testing that the letter 'a' has the correct value.")

   myTests().main()

.. activecode:: ac10_9_17
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Dictionaries/AccumulatingtheBestKey

   Cree un diccionario llamado ``low_d`` que haga un seguimiento de todos los caracteres en la cadena ``p`` y observe cuántas veces se vio cada carácter. Asegúrese de que no haya repeticiones de caracteres como teclas, de modo que "T" y "t" se vean como una "t", por ejemplo.
   ~~~~
   p = "Summer is a great time to go outside. You have to be careful of the sun though because of the heat."

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(low_d["s"], 5, "Testing the key s")
      def testThree(self):
         self.assertEqual(low_d["y"], 1, "Testing the key y")


   myTests().main()
