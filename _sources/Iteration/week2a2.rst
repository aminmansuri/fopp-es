..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-12-
   :start: 1

.. Week 2 Assessment 2

Evaluación del capítulo
------------------------

**Revisa tu conocimiento**

.. activecode:: assess_ps_02_01
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Iteration/Stringsandforloops

    Escriba un bucle for para imprimir cada carácter de la cadena ``my_str`` en una línea separada.
    ~~~~
    my_str = "MICHIGAN"

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertIn('for', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
        self.assertIn("M\nI\nC\nH\nI\nG\nA\nN", self.getOutput(), "Testing output (Don't worry about actual and expected values).")

    myTests().main()


.. activecode:: assess_ps_02_02
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Iteration/Listsandforloops

    Escriba un bucle for para imprimir cada elemento de la lista ``several_things``. Luego, escriba *otro* bucle for para imprimir el TIPO de cada elemento de la lista ``varias_cosas``. Para completar este problema, debería haber escrito dos bucles for diferentes, cada uno de los cuales itera sobre la lista ``several_things``, pero cada uno de esos 2 bucles for debería tener un resultado diferente.
    ~~~~
    several_things = ["hello", 2, 4, 6.0, 7.5, 234352354, "the end", "", 99]

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
          self.assertIn('for', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
          str1 = "hello\n2\n4\n6.0\n7.5\n234352354\nthe end\n\n99\n<class 'str'>\n<class 'int'>\n<class 'int'>\n<class 'float'>\n<class 'float'>\n<class 'int'>\n<class 'str'>\n<class 'str'>\n<class 'int'>"
          str2 = "hello\n2\n4\n6.0\n7.5\n234352354\nthe end\n\n99\n<type 'str'>\n<type 'int'>\n<type 'int'>\n<type 'float'>\n<type 'float'>\n<type 'int'>\n<type 'str'>\n<type 'str'>\n<type 'int'>"
          self.assertTrue(str1 in self.getOutput() or str2 in self.getOutput(), "Testing output (Don't worry about actual and expected values).")

    myTests().main()


.. activecode:: assess_ps_02_03
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Iteration/Listsandforloops

    Escriba código que use iteración para imprimir **la longitud** de cada elemento de la lista almacenada en ``str_list``.
    ~~~~
    str_list = ["hello", "", "goodbye", "wonderful", "I love Python"]

    # Write your code here.
    =====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def test_output(self):
            self.assertIn("for", self.getEditorText(), "Testing whether you used a for loop (Don't worry about actual and expected values).")
            self.assertIn("5\n0\n7\n9\n13", self.getOutput(), "Testing output (Don't worry about actual and expected values).")

    myTests().main()


.. activecode:: assess_ps_02_04
    :language: python
    :autograde: unittest

    Escriba un programa que use el módulo de tortuga **y** un bucle for para dibujar algo. No tiene que ser complicado, pero dibuja algo diferente de lo que hemos hecho en el pasado. (Sugerencia: si está dibujando algo complicado, podría ser tedioso verlo dibujar una y otra vez. Intente configurar ``.speed(10)`` para que la tortuga dibuje rápido, o ``.speed(0)`` para que dibuje súper rápido sin animación).
    ~~~~
    import turtle




.. activecode:: assess_ps_02_05
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Iteration/TheAccumulatorPattern

    Escriba el código para contar el número de caracteres en ``original_str`` usando accumulation pattern y asigne la respuesta a una variable ``num_chars``. NO use la función ``len`` para resolver el problema (si la usa mientras está trabajando en este problema, ¡coméntelo después!)
    ~~~~
    original_str = "The quick brown rhino jumped over the extremely lazy fox."


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
           self.assertEqual(num_chars, len(original_str), "Testing whether num_chars_sent has the correct value")
           self.assertNotIn('len', self.getEditorText(), "Testing that you are not including the len function in your code. (Don't worry about Actual and Expected Values.)")

    myTests().main()

.. activecode:: assess_ps_02_07
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Iteration/TraversalandtheforLoopByIndex

    ``addition_str`` es una cadena con una lista de números separados por el signo ``+``. Escriba código que use accumulation pattern para tomar la suma de todos los números y lo asigna a ``sum_val`` (un número entero). (Debe usar la función ``.split("+")`` para dividir entre ``"+"`` y ``int()`` para convertir a un entero).

    ~~~~
    addition_str = "2+5+10+20"


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
           self.assertEqual(sum_val, 37, "Testing whether sum_val has the correct value")
           self.assertIn('split', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
           self.assertIn('int', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

    myTests().main()


.. activecode:: assess_ps_02_08
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Iteration/TraversalandtheforLoopByIndex

    ``week_temps_f`` es una cadena con una lista de temperaturas Fahrenheit separadas por el signo ``,``. Escriba código que utilice accumulation pattern para calcular el **promedio** (suma dividida por el número de elementos) y lo asigna a ``avg_temp``. No codifique su respuesta (es decir, haga que su código calcule tanto la suma como el número de elementos en ``week_temps_f``) (Debe usar la función ``.split(",")`` para dividir por ``","`` y ``float()`` para convertir el resultado a un float).

    ~~~~
    week_temps_f = "75.1,77.7,83.2,82.5,81.0,79.5,85.7"


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
            self.assertAlmostEqual(avg_temp, 80.67142857142858, 7, "Testing that avg_temp has the correct value")
            self.assertIn('split', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
            self.assertIn('float', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

    myTests().main()

.. activecode:: assess_ps_02_09
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Iteration/TraversalandtheforLoopByIndex

   Escriba código para crear una lista de números del 0 al 67 y asigne esa lista a la variable ``nums``. No hagas hard code en la lista.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(nums, range(68), "Testing that nums is a list that contains the correct elements.")

   myTests().main()