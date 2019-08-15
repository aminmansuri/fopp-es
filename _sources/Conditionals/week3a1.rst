..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. Week 3 Assignment

Evaluación de capítulos
-----------------------

**Revisa tu entendimiento**

.. activecode:: assess_ps3_1_1_1
    :language: python
    :autograde: unittest
    :practice: T

    ``rainfall_mi`` es un string que contiene el número promedio de pulgadas de lluvia en Michigan por cada mes (en pulgadas) con cada mes separado por una coma.
    Escriba el código para calcular la cantidad de meses que tienen más de 3 pulgadas de lluvia. Almacene el resultado en la variable ``num_rainy_months``.
    En otras palabras, cuente la cantidad de elementos con valores ``> 3.0``.


    Las respuestas codificadas no recibirán crédito.
    ~~~~
    rainfall_mi = "1.65, 1.46, 2.05, 3.03, 3.35, 3.46, 2.83, 3.23, 3.5, 2.52, 2.8, 1.85"
    =====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertIn('for', self.getEditorText(), "Testing that your code has a for loop (Don't worry about actual and expected values).")
            self.assertEqual(num_rainy_months, 5, "Testing that num_rainy_months has the right value")

    myTests().main()

.. activecode:: assess_ps3_1_1_2
    :language: python
    :autograde: unittest
    :practice: T

    La variable ``sentence`` almacena una cadena. Escriba el código para determinar cuántas palabras en ``sentence`` comienzan y terminan con la misma letra, incluidas las palabras de una letra.
    Almacene el resultado en la variable ``same_letter_count``.


    Las respuestas codificadas no recibirán crédito.
    ~~~~
    sentence = "students flock to the arb for a variety of outdoor activities such as jogging and picnicking"

    # Escribe tu código aquí.


    ====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(same_letter_count, 2, "Checking that same_letter_count has the correct value")

    myTests().main()

.. activecode:: assess_ps3_1_1_3
    :language: python
    :autograde: unittest
    :practice: T

    Escriba el código para contar el número de strings en la lista ``items`` que tienen el caracter ``w``. Asigne ese número a la variable ``acc_num``.

    SUGERENCIA 1: ¡Usa el patrón de acumulación!

    SUGERENCIA 2: el operador ``in`` verifica si un substring está presente en un string.


    Las respuestas codificadas no recibirán crédito.
    ~~~~
    items = ["whirring", "wow!", "calendar", "wry", "glass", "", "llama","tumultuous","owing"]


    =====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertIn(' in ', self.getEditorText(), "Testing that you are using the in operator.")
            self.assertEqual(acc_num, 4, "Testing that acc_num has been set to the number of strings that have 'w' in them.")

    myTests().main()

.. activecode:: assess_ps3_1_1_4
    :language: python
    :autograde: unittest
    :practice: T

    Escriba un código que cuente la cantidad de palabras en ``sentence`` que contienen *ya sea* una "a" o una "e". Almacene el resultado en la variable ``num_a_or_e``.

    Nota 1: Asegúrese de no contar dos veces las palabras que contienen tanto una a como una e.

    SUGERENCIA 1: Use el operador ``in``.

    SUGERENCIA 2: Puede usar ``or`` o ``elif``.


    Las respuestas codificadas no recibirán crédito.
    ~~~~
    sentence = "python is a high level general purpose programming language that can be applied to many different classes of problems."


    =====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertIn(' in ', self.getEditorText(), "Testing that you are using the in operator.")
            self.assertEqual(num_a_or_e, 14, "Testing that num_a_or_e has been set to the correct number.")

    myTests().main()

.. activecode:: assess_ps3_1_1_5
    :language: python
    :autograde: unittest
    :practice: T

    Escriba un código que cuente el número de vocales en la oración ``s`` y asigne el resultado a la variable ``num_vowels``. Para este problema, las vocales son solo a, e, i, o, u. Sugerencia: use el operador ``in`` con ``vowels``.
    ~~~~
    s = "singing in the rain and playing in the rain are two entirely different situations but both can be fun"
    vowels = ['a','e','i','o','u']

    # Escribe tu código aquí


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
           self.assertEqual(num_vowels, 32, "Prueba si num_vowels está configurado correctamente")

        def testOneA(self):
           self.assertIn('for', self.getEditorText(), "Prueba de que está utilizando un bucle for.")

    myTests().main()

.. activecode:: assess_ac3_1_1_6
   :language: python
   :autograde: unittest
   :practice: T

   Cree un condicional para que si "Friendly" está en ``w``, entonces "Friendly is here!" debe asignarse a la variable ``wrd``. Si no es así, verifique si "Friend" está en ``w``. Si es así, la cadena "Friend is here!" debe asignarse a la variable ``wrd``, de lo contrario "No variation of friend is in here." debe asignarse a la variable ``wrd``. (También considere: ¿importa el orden de sus declaraciones condicionales para este problema? ¿Por qué?)
   ~~~~
   w = "Friendship is a wonderful human experience!"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(wrd, "Friend is here!", "Testing the value of wrd")
         self.assertIn("else", self.getEditorText(), "Checking that you used an else clause.")
         self.assertIn("elif", self.getEditorText(), "Checking that you used an elif clause.")

   myTests().main()

.. activecode:: assess_ac3_1_1_7
   :language: python
   :autograde: unittest
   :practice: T

   Hemos escrito condicionales para su uso. Cree la variable x y asígnele un número entero para que al final del código, a ``output`` se le asigne el string ``"Consistently working"``.
   ~~~~
   if x >= 10:
       output = "working"
   else:
       output = "Still working"
   if x > 12:
       output = "Always working"
   elif x < 7:
       output = "Forever working"
   else:
       output = "Consistently working"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(output, "Consistently working", "Testing the value of output")
      def testTwo(self):
         self.assertIn(x, [7,8,9,10,11,12], "Testing that x was assigned a correct number" )

   myTests().main()

.. activecode:: assess_ac3_1_1_8
   :language: python
   :autograde: unittest
   :practice: T

   Escriba el código de manera que si ``"STATS 250"`` está en la lista ``schedule``, entonces el string ``"You could be in Information Science!"`` se asigna a la variable ``resp``. De lo contrario, el string ``"That's too bad."`` Debe asignarse a la variable ``resp``.
   ~~~~
   schedule = ["SI 106", "STATS 250", "SI 110", "ENGLISH 124/125"]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(resp, "You could be in Information Science!", "Testing the value of resp given the schedule list provided.")
         self.assertIn("if", self.getEditorText(), "Testing that you used an if clause.")

   myTests().main()

.. activecode:: assess_ac3_1_1_9
   :language: python
   :autograde: unittest
   :practice: T

   Cree la variable ``z`` cuyo valor es ``30``. Escriba el código para ver si ``z`` es mayor que ``y``. Si es así, agregue 5 al valor de ``y``, de lo contrario no haga nada. Luego, multiplique ``z`` e ``y``, y asigne el valor resultante a la variable ``x``.
   ~~~~
   y = 22

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(x, 810, "Testing the value of x")
      def testTwo(self):
         self.assertEqual(z, 30, "Testing the value of z.")

   myTests().main()   

.. activecode:: assess_ac3_1_1_10
   :language: python
   :autograde: unittest
   :practice: T

   Para cada cadena en ``wrd_lst``, encuentre el número de caracteres en la cadena. Si el número de caracteres es inferior a 6, agregue 1 a ``accum`` para que, al final, ``accum`` contenga un número entero que represente el número total de palabras en la lista que tienen menos de 6 caracteres.
   ~~~~
   wrd_lst = ["Hello", "activecode", "Java", "C#", "Python", "HTML and CSS", "Javascript", "Swift", "php"]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(accum, 5, "Testing the value of accum")

   myTests().main()
