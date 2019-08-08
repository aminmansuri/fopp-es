..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _map_chap:

.. qnum::
   :prefix: AdAccum-2-
   :start: 1

Map
---

Anteriormente se le introdujo a acumular una lista transformando cada uno de los elementos. Aquí revisamos ese patrón.

La siguiente función produce una nueva lista con cada elemento en la lista original duplicado. Es un ejemplo de mapeo,
desde la lista original a una nueva lista de la misma longitud, donde cada elemento se duplica.

.. activecode:: ac21_2_1
    
    def doubleStuff(a_list):
        """ Return a new list in which contains doubles of the elements in a_list. """
        new_list = []
        for value in a_list:
            new_elem = 2 * value
            new_list.append(new_elem)
        return new_list
    
    things = [2, 5, 9]
    print(things)
    things = doubleStuff(things)
    print(things)

La función doubleStuff es un ejemplo de accumulator pattern, en particular el patrón de mapeo.
En la línea 3, ``new_list`` se inicializa. En la línea 5, se produce el valor duplicado para el artículo actual y en la línea 6 se agrega a
la lista que estamos acumulando. La línea 7 se ejecuta después de haber procesado todos los elementos de la lista original y devuelve
``new_list``. Una vez más, codelens nos ayuda a ver las referencias y objetos reales a medida que se pasan y devuelven.

.. codelens:: clens21_2_1
    :python: py3

    def doubleStuff(a_list):
        """ Return a new list in which contains doubles of the elements in a_list. """
        new_list = []
        for value in a_list:
            new_elem = 2 * value
            new_list.append(new_elem)
        return new_list

    things = [2, 5, 9]
    things = doubleStuff(things)

Este patrón de cálculo es tan común que Python ofrece una forma más general de hacer *mapeos* mappings, la función ``map``, que
deja más claro cuál es la estructura general del cálculo. ``map`` toma dos argumentos, una función y una secuencia.
La función es el mapeador que transforma elementos. Se aplica automáticamente a cada elemento de la secuencia, usted
no tiene que inicializar un acumulador o iterar con un ciclo for en absoluto.

.. note::

    Técnicamente, en un intérprete adecuado de Python 3, la función ``map`` produce un "iterador", que es como una lista pero
    produce los elementos a medida que se necesitan. En la mayoría de los lugares en Python donde puede usar una lista (por ejemplo, en un bucle for) puede
    usar un "iterador" como si en realidad fuera una lista. Así que probablemente nunca notarás la diferencia. Si alguna vez realmente
    necesita una lista, puede convertir explícitamente la salida del mapa en una lista: ``list(map(...))``. En el entorno de runestone, ``mapa`` en realidad devuelve una lista real, pero para hacer que este código sea compatible con un entorno completo de Python, siempre lo convertimos en una lista.

Como lo hicimos al pasar una función como parámetro a la función ``sorted``, podemos especificar una función para pasar a ``mapa``
ya sea refiriéndose a una función por su nombre o proporcionando una expresión lambda.

.. activecode:: ac21_2_2

   def triple(value):
       return 3*value
      
   def tripleStuff(a_list):
       new_seq = map(triple, a_list)
       return list(new_seq)

   def quadrupleStuff(a_list):
       new_seq = map(lambda value: 4*value, a_list)
       return list(new_seq)
      
   things = [2, 5, 9]
   things3 = tripleStuff(things)
   print(things3)
   things4 = quadrupleStuff(things)
   print(things4)

Una vez que nos acostumbremos a usar la función ``map``, ya no es necesario definir funciones como
``tripleStuff`` y ``quadrupleStuff``.

.. activecode:: ac21_2_3

   things = [2, 5, 9]
   
   things4 = map((lambda value: 4*value), things)
   print(list(things4))
   
   # O todo en una línea
   print(list(map((lambda value: 5*value), [1, 2, 3])))


**Revisa tu entendimiento**

.. activecode:: ac21_2_4
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **1.** Usando map, crear una lista asignada a la variable ``greeting_doubled`` que doble a cada elemento en la lista ``lst``.
   ~~~~

   lst = [["hi", "bye"], "hello", "goodbye", [9, 2], 4]
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOneA(self):
         self.assertEqual(greeting_doubled, [['hi', 'bye', 'hi', 'bye'], 'hellohello', 'goodbyegoodbye', [9, 2, 9, 2], 8], "Testing that greeting_doubled is assigned to correct values")
         self.assertIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")


   myTests().main()

.. activecode:: ac21_2_5
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **2.** A continuación, proporcionamos una lista de cadenas llamada ``abbrevs``. Use map para producir una nueva lista llamada ``abbrevs_upper`` que contiene las mismas cadenas en mayúsculas.
   ~~~~

   abbrevs = ["usa", "esp", "chn", "jpn", "mex", "can", "rus", "rsa", "jam"]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(abbrevs_upper, ["USA", "ESP", "CHN", "JPN", "MEX", "CAN", "RUS", "RSA", "JAM"], "Testing that abbrevs_upper is correct.")
         self.assertIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")


   myTests().main()
