..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-19-
   :start: 1

.. Week 1 Assessment 2

Evaluación de capítulos
-----------------------

**Revisa tu entendimiento**

.. activecode:: assess_ps_01_01
    :include: assess_addl_functions
    :language: python
    :autograde: unittest
    :topics: SimplePythonData/FunctionCalls

    Hay una función que le brindamos en este problema llamada ``square``. Toma un entero y devuelve el cuadrado de ese valor entero. Escriba el código para asignar una variable llamada ``xyz`` al valor ``5*5`` (cinco al cuadrado). Use la función square, en lugar de simplemente multiplicar con ``*``.
    ~~~~
    xyz = ""

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
            self.assertEqual(type(xyz), type(3), "Comprobando el tipo de xyz")
            self.assertEqual(xyz, 25, "Comprobando si xyz es 25")
            self.assertIn('square', self.getEditorText(), "Probar 'square' está en su código. (No se preocupe por los valores reales y esperados.)")

    myTests().main()

.. activecode:: assess_ps_01_02
    :language: python
    :autograde: unittest
    :practice: T
    :topics: SimplePythonData/StatementsandExpressions

    Escriba el código para asignar el número de *caracteres* en la cadena ``rv`` a una variable ``num_chars``.
    ~~~~
    rv = """Había una vez una triste media noche, mientras reflexionaba, débil y cansado,
        Sobre muchos volúmenes pintorescos y curiosos de tradiciones olvidadas,
        Mientras asentía, casi durmiendo la siesta, de repente se escuchó un golpeteo,
        Como alguien golpeando suavemente, golpeando la puerta de mi habitación.
        'Soy un visitante, murmuré, tocando la puerta de mi habitación;
        Solo esto y nada más."""

    # ¡Escribe tu código aquí!

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
           self.assertEqual(num_chars, len(rv), "Prueba de que num_chars se ha establecido en la longitud de rv")

    myTests().main()


.. mchoice:: assess_question1_1_1_3
   :multiple_answers:
   :answer_a: a = len("hola bienvenido")
   :answer_b: a = 11 + 8
   :answer_c: a = len(z) + len(y)
   :answer_d: a = len("hola mundo") + len("bienvenido!")
   :answer_e: ninguno de los anteriores es hardcoding.
   :feedback_a: Aunque estamos usando la función len aquí, estamos codificando que len debería devolver la longitud. No estamos haciendo referencia a z o y.
   :feedback_b: Esto es hardcoding, estamos escribiendo el valor sin hacer referencia a z o y.
   :feedback_c: Esto no se considera hard coding. Estamos utilizando la función len para determinar la longitud de lo que está almacenado en z e y, que es una forma correcta de abordar este problema.
   :feedback_d: Aunque estamos usando la función len aquí, estamos codificando qué len debería devolver la longitud de cada vez que llamamos len. No estamos haciendo referencia a z o y.
   :feedback_e: Al menos una de estas soluciones se considera hardcoding. Echa otro vistazo.
   :correct: a,b,d
   :practice: T
   :topics: SimplePythonData/StatementsandExpressions

   El siguiente código inicializa dos variables, ``z`` e ``y``. Queremos asignar el número total de caracteres en ``z`` y en ``y`` a la variable ``a``. ¿Cuál de las siguientes soluciones, si hay alguna, se consideraría hard coding?

   .. sourcecode:: python

    z = "Hola Mundo"
    y = "Bienvenido!"

.. activecode:: assess_addl_functions
    :language: python
    :nopre:
    :hidecode:

    (Esta no es una pregunta de evaluación) El siguiente código define las funciones utilizadas por una de las preguntas anteriores. No modifique el código, pero no dude en echar un vistazo.

    ~~~~

    def square(num):
        return num**2
