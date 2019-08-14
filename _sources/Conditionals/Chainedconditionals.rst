..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: condition-9-
   :start: 1

.. index::
   single: chained conditional
   single: conditional; chained

Condicionales anidados
----------------------

Python proporciona una forma alternativa de escribir una sección anidada, como la que se muestra en la sección anterior.
Esto a veces se conoce como **condicional anidado**.

.. sourcecode:: python

    if x < y:
        print("x es menor que y")
    elif x > y:
        print("x es mayor que y")
    else:
        print("x e y son iguales")

El flujo de control se puede dibujar en una orientación diferente, pero el patrón resultante es idéntico al que se muestra arriba.

.. image:: Figures/flowchart_chained_conditional.png

``elif`` es una abreviatura de ``else if``. De nuevo, exactamente una rama será
ejecutado. No hay límite para el número de declaraciones ``elif``, sino solo uno
se permite en la declaración final ``else`` única (y opcional) y debe ser la última
rama en el comunicado.

.. image:: Figures/conditionals_overview.png

Cada condición se verifica en orden. Si el primero es falso, el siguiente está marcado,
y así. Si uno de ellos es verdadero, se ejecuta la rama correspondiente y la
declaración termina. Incluso si más de una condición es verdadera, solo la primera es verdadera
rama se ejecuta.

Aquí está el mismo programa que usa ``elif``.

.. activecode:: ac7_9_1

    x = 10
    y = 10

    if x < y:
        print("x es menor que y")
    elif x > y:
        print("x es mayor que y")
    else:
        print("x e y deben ser iguales")

La siguiente imagen resalta diferentes tipos de condicionales válidos que se pueden usar. Aunque hay otras
versiones de condicionales que Python puede entender (imagine una declaración if con veinte declaraciones elif), esas
otras versiones deben seguir el mismo orden que se ve a continuación.

.. image:: Figures/valid_conditionals.png
   :alt: shows a unary conditiona, a binary conditional, a conditional with if, elif, else, and a conditional with if, elif, and elif.

**Revisa tu entendimiento**

.. mchoice:: question7_9_1
   :answer_a: I únicamente
   :answer_b: II únicamente
   :answer_c: III únicamente
   :answer_d: II y III
   :answer_e: I, II, y III
   :correct: b
   :feedback_a: No puede usar una expresión Boolean después de otra.
   :feedback_b: Sí, II dará el mismo resultado.
   :feedback_c: No, III no dará el mismo resultado. La primera instrucción if será verdadera, pero la segunda será falsa, por lo que la parte else se ejecutará.
   :feedback_d: No, aunque II es correcto, III no dará el mismo resultado. Intentalo de nuevo.
   :feedback_e: No, en I no puedes tener una expresión Boolean después de otra cosa.
   :practice: T

   ¿Cuál de I, II y III a continuación da el mismo resultado que el siguiente bucle anidado?

   .. code-block:: python

     # instrucción if-else anidada
     x = -10
     if x < 0:
         print("El número negativo ",  x, " no es válido aquí.")
     else:
         if x > 0:
             print(x, " es un número positivo")
         else:
             print(x, " es 0")


   .. code-block:: python

     I.
     
     if x < 0:
         print("El número negativo ",  x, " no es válido aquí.")
     else (x > 0):
         print(x, " es un número positivo")
     else:
         print(x, " es 0")


   .. code-block:: python

     II.
     
     if x < 0:
         print("El número negativo ",  x, " no es válido aquí.")
     elif (x > 0):
         print(x, " es un número positivo")
     else:
         print(x, " es 0")

   .. code-block:: python

     III.
     
     if x < 0:
         print("El número negativo ",  x, " no es válido aquí.")
     if (x > 0):
         print(x, " es un número positivo")
     else:
         print(x, " es 0")

.. mchoice:: question7_9_2
   :answer_a: a
   :answer_b: b
   :answer_c: c
   :correct: c
   :feedback_a: Mientras que el valor en x es menor que el valor en y (3 es menor que 5) no es menor que el valor en z (3 no es menor que 2).
   :feedback_b: El valor en y no es menor que el valor en x (5 no es menor que 3).
   :feedback_c: Como las dos primeras expresiones booleanas son falsas, se ejecutará lo demás.
   :practice: T

   ¿Qué imprimirá el siguiente código si x = 3, y = 5, and z = 2?

   .. code-block:: python

     if x < y and x < z:
         print("a")
     elif y < x and y < z:
         print("b")
     else:
         print("c")

.. activecode:: ac7_9_2
   :language: python
   :autograde: unittest
   :practice: T

   Cree un condicional para encontrar si "false" está en el string ``str1``. Si es así, asigne a la variable ``output`` el string "False. You aren't you?". Verifique si "true" está en el string ``str1`` y, si es así, asigne "True! You are you!" a la variable ``output``. Si ninguno de los dos está en ``str1``, asigne "Neither true nor false!" a ``output``.
   ~~~~
   str1 = "Today you are you! That is truer than true! There is no one alive who is you-er than you!"
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testThree(self):
         self.assertEqual(output, "True! You are you!", "Testing that output has the correct value, given the str1 provided.")
         self.assertIn("else", self.getEditorText(), "Testing output (Don't worry about actual and expected values).")
         self.assertIn("elif", self.getEditorText(), "Testing output (Don't worry about actual and expected values).")

   myTests().main()

.. activecode:: ac7_9_4
   :language: python
   :autograde: unittest
   :practice: T

   Cree una lista vacía llamada ``resps``. Usando la lista ``percent_rain``, para cada porcentaje, si está por encima de 90, agregue el string 'Bring an umbrella.' a ``resps``, de lo contrario, si está por encima de 80, agregue la cadena 'Good for the flowers?' a ``resps``, de lo contrario, si está por encima de 50, agregue la cadena 'Watch out for clouds!' a ``resps``, de lo contrario, agregue la cadena 'Nice day!' a ``resps``. Nota: si está seguro de que tiene el problema correcto pero no pasa, entonces verifique que haya hecho coincidir las cadenas exactamente.
   ~~~~
   percent_rain = [94.3, 45, 100, 78, 16, 5.3, 79, 86]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(resps, ['Bring an umbrella.','Nice day!','Bring an umbrella.','Watch out for clouds!',"Nice day!",'Nice day!','Watch out for clouds!',"Good for the flowers?"], "Testing the value of resps")

   myTests().main()

.. activecode:: ac7_9_5
   :language: python
   :autograde: unittest
   :practice: T

   Hemos creado condicionales para su uso. No cambie las declaraciones condicionales proporcionadas. Encuentre un valor entero para ``x`` que hará que ``output`` mantenga los valores ``True`` y ``None``. (¡Dibujar diagramas o diagramas de flujo para usted puede ayudar!)
   ~~~~
   x =
   output = []

   if x > 63:
       output.append(True)
   elif x > 55:
       output.append(False)
   else: 
       output.append("Neither")

   if x > 67:
       output.append(True)
   else:
       output.append(None)

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testSixA(self):
         self.assertEqual(output, [True, None], "Testing that value of output is correct.")

      def testSixB(self):
         self.assertEqual(x in [64, 65, 66, 67], True, "Testing that value of x is reasonable for this problem")

   myTests().main()
