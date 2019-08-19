..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: tuples-2-
   :start: 1


Introducción
============

Ya has visto tuplas, un tipo de secuencia que funciona igual que las listas, excepto que son inmutables.

Cuando se trabaja con valores múltiples o nombres de variables múltiples, el intérprete de Python realiza el empaquetado y desempaquetado automático desde y hacia las tuplas, lo que permite algunas simplificaciones en el código que escribe.

Objetivos de aprendizaje
------------------------

Al final de este capítulo, podrá:

* Reconocer cuando el código está usando el empaquetado de tuplas implícito
* Utilice el empaquetado de tuplas implícito para devolver múltiples valores de una función
* Leer y escribir código que descomprime una tupla en múltiples variables


Empaquetado de Tuplas
======================

Donde sea que python espere un solo valor, si se proporcionan múltiples expresiones, separadas
por comas, se empaquetan **automáticamente** en una tupla. Por ejemplo, podríamos
he omitido los paréntesis al asignar una tupla a la variable julia por primera vez.

.. activecode:: ac13-1-1

    julia = ("Julia", "Roberts", 1967, "Duplicity", 2009, "Actress", "Atlanta, Georgia")
    # or equivalently
    julia = "Julia", "Roberts", 1967, "Duplicity", 2009, "Actress", "Atlanta, Georgia"
    print(julia[4])
    

**Revisa tu entendimiento**

.. mchoice:: question12_2_1
   :multiple_answers:
   :answer_a: print(julia['city'])
   :answer_b: print(julia[-1])
   :answer_c: print(julia(-1))
   :answer_d: print(julia(6))
   :answer_e: print(julia[7])
   :correct: b
   :feedback_a: julia es una tupla, no un diccionario; Los índices deben ser enteros.
   :feedback_b: [-1] selecciona el último elemento de la secuencia.
   :feedback_c: Indexa en tuplas usando corchetes. julia(-1) intentará tratar a julia como una llamada de función, con -1 como valor del parámetro.
   :feedback_d: Indexa en tuplas usando corchetes. julia(-1) intentará tratar a julia como una llamada de función, con -1 como valor del parámetro.
   :feedback_e: La indexación comienza en 0. y usted desea el séptimo elemento, que es julia[6]
   :practice: T

   ¿Cuál de las siguientes declaraciones generará Atlanta, Georgia?

.. activecode:: ac12_2_1
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **2.** Cree una tupla llamada ``práctica`` que tenga cuatro elementos: 'y', 'h', 'z' y 'x'.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(practice, ('y','h','z','x'), "Testing that pratice value is assigned to correct value.")

   myTests().main()

.. activecode:: ac12_2_2
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **3.** Cree una tupla llamada ``tup1`` que tenga tres elementos: 'a', 'b' y 'c'.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(tup1, ('a', 'b', 'c'), "Testing that tup1 was created correctly.")

   myTests().main()

.. activecode:: ac12_2_3
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **4.** Se proporciona una lista de tuplas. Cree otra lista llamada ``t_check`` que contenga el tercer elemento de cada tupla.
   ~~~~

   lst_tups = [('Articuno', 'Moltres', 'Zaptos'), ('Beedrill', 'Metapod', 'Charizard', 'Venasaur', 'Squirtle'), ('Oddish', 'Poliwag', 'Diglett', 'Bellsprout'), ('Ponyta', "Farfetch'd", "Tauros", 'Dragonite'), ('Hoothoot', 'Chikorita', 'Lanturn', 'Flaaffy', 'Unown', 'Teddiursa', 'Phanpy'), ('Loudred', 'Volbeat', 'Wailord', 'Seviper', 'Sealeo')]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(t_check, ['Zaptos', 'Charizard', 'Diglett', 'Tauros', 'Lanturn', 'Wailord'], "Testing that pratice value is assigned to correct value.")

   myTests().main()

.. activecode:: ac12_2_4
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **5.** A continuación, hemos proporcionado una lista de tuplas. Escriba un bucle for que guarde el segundo elemento de cada tupla en una lista llamada ``seconds``.
   ~~~~

   tups = [('a', 'b', 'c'), (8, 7, 6, 5), ('blue', 'green', 'yellow', 'orange', 'red'), (5.6, 9.99, 2.5, 8.2), ('squirrel', 'chipmunk')]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(seconds, ['b', 7, 'green', 9.99, 'chipmunk'], "Testing that seconds was created correctly.")

   myTests().main()
