..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: dictionaries-6-
   :start: 1

Acumulando Resultados de un Diccionario
-----------------------------------------

Así como hemos iterado a través de los elementos de una lista para acumular un resultado,
También podemos iterar a través de las teclas en un diccionario, acumulando un resultado que puede
dependerá de los valores asociados con cada una de las claves.

Por ejemplo, supongamos que queremos calcular una puntuación de Scrabble para el Estudio en el texto Scarlet.
Cada aparición de la letra 'e' gana un punto, pero 'q' gana 10. Tenemos
un segundo diccionario, almacenado en la variable ``letter_values``. Ahora, para calcular el
puntaje total, comenzamos un acumulador en 0 y pasamos por cada una de las letras en el diccionario.
Para cada una de esas letras que tiene un valor de letra (sin puntos para espacios,
puntuación, mayúsculas, etc.), agregamos al puntaje total.

.. activecode:: ac10_6_1

   f = open('scarlet2.txt', 'r')
   txt = f.read()
   # ahora txt es un String larga que contiene todos los caracteres
   x = {} # comenzar con un diccionario vacío
   for c in txt:
       if c not in x:
           # no hemos visto este caracter antes, así que inicializa un contador para él
           x[c] = 0
      
       #lo hayamos visto antes o no, incremente su contador
       x[c] = x[c] + 1

   letter_values = {'a': 1, 'b': 3, 'c': 3, 'd': 2, 'e': 1, 'f':4, 'g': 2, 'h':4, 'i':1, 'j':8, 'k':5, 'l':1, 'm':3, 'n':1, 'o':1, 'p':3, 'q':10, 'r':1, 's':1, 't':1, 'u':1, 'v':8, 'w':4, 'x':8, 'y':4, 'z':10}
   
   tot = 0
   for y in x:
       if y in letter_values:
           tot = tot + letter_values[y] * x[y]

   print(tot)

La línea 18 es la complicada. Estamos actualizando la variable tot para que tenga su número anterior más el puntaje de la letra actual por el número de apariciones de esa letra.
Intente cambiar algunos de los valores de las letras y vea cómo afecta el total. Intenta cambiar txt para que sea solo una palabra que puedas jugar en Scrabble.

**Revisa tu entendimiento**

.. activecode:: ac10_6_2
   :language: python
   :autograde: unittest
   :practice: T

   **1.** El diccionario ``viajar`` contiene el número de países dentro de cada continente al que Jackie ha viajado. Encuentre el número total de países en los que Jackie ha estado y guarde este número en el nombre de la variable ``total``. ¡*No hagas hard code aquí*!
   ~~~~
   travel = {"North America": 2, "Europe": 8, "South America": 3, "Asia": 4, "Africa":1, "Antarctica": 0, "Australia": 1}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(total, 19, "Testing that total is correct.")

   myTests().main()

.. activecode:: ac10_6_3
   :language: python
   :autograde: unittest
   :practice: T

   **2.** ``schedule`` es un diccionario donde el nombre de una clase es clave y su valor es cuántos créditos valió. Revise y acumule el número total de créditos que se han obtenido hasta el momento y asígnelo a la variable ``total_credits``. Ho hagas *hard code*.
   ~~~~
   schedule = {"UARTS 150": 3, "SPANISH 103": 4, "ENGLISH 125": 4, "SI 110": 4, "ENS 356": 2, "WOMENSTD 240": 4, "SI 106": 4, "BIO 118": 3, "SPANISH 231": 4, "PSYCH 111": 4, "LING 111": 3, "SPANISH 232": 4, "STATS 250": 4, "SI 206": 4, "COGSCI 200": 4, "AMCULT 202": 4, "ANTHRO 101": 4}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(total_credits, 63, "Testing that total_credits has the correct value.")

   myTests().main()


.. datafile:: scarlet2.txt
   :fromfile: scarlet.txt
   :hide:
