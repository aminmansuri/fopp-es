..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sequences-10-
   :start: 1

.. Week 2 Assessment 1

Evaluación de capítulos
-----------------------

**Revisa tu entendimiento**

.. mchoice:: assess_question2_1_1_1
   :answer_a: zpzpzpzpzp
   :answer_b: zzzzzppppp
   :answer_c: pzpzpzpzpz
   :answer_d: pppppzzzzz
   :answer_e: Ninguno de los anteriores, se producirá un error.
   :correct: c
   :feedback_a: El orden de concatenación importa.
   :feedback_b: Piense en el orden en que se ejecuta el programa, ¿qué ocurre primero?
   :feedback_c: Sí, porque let_two se puso antes de let, c tiene "pz" y luego se repite cinco veces.
   :feedback_d: Piense en el orden en que se ejecuta el programa, ¿qué ocurre primero?
   :feedback_e: Esta es la sintaxis correcta y no se producirán errores.
   :practice: T
   :topics: Sequences/ConcatenationandRepetition

   ¿Cuál será la salida para el siguiente código?
  
   .. sourcecode:: python

    let = "z"
    let_two = "p"
    c = let_two + let
    m = c*5
    print(m)

.. activecode:: assess_ac_2_1_1_2
    :autograde: unittest
    :language: python
    :practice: T
    :topics: Sequences/TheSliceOperator

    Escriba un programa que extraiga los últimos tres elementos de la lista``sports`` y lo asigne a la variable ``last``. Asegúrese de escribir su código para que funcione sin importar cuántos elementos haya en la lista.
    ~~~~
    sports = ['cricket', 'football', 'volleyball', 'baseball', 'softball', 'track and field', 'curling', 'ping pong', 'hockey']


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertEqual(last, ['curling', 'ping pong', 'hockey'], "Testing that the value of last is the last three items in sports.")
        self.assertNotIn("[6:]", self.getEditorText(), "Testing that your code would work no matter how many items. (Don't worry about actual and expected values).")
        

    myTests().main()

.. activecode:: assess_ac_2_1_1_3
    :autograde: unittest
    :language: python
    :practice: T
    :topics: Sequences/ConcatenationandRepetition

    Escriba un código que combine las siguientes variables para que la oración "You are doing a great job, keep it up!" se asigne a la variable ``message``. No edite los valores asignados a ``by``, ``az``, ``io`` o ``qy``.
    ~~~~
    by = "You are"
    az = "doing a great "
    io = "job"
    qy = "keep it up!"


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertEqual(by, 'You are', "Testing original variables.")
        self.assertEqual(az, 'doing a great ', "Testing original variables.")
        self.assertEqual(io, 'job', "Testing original variables.")
        self.assertEqual(qy, 'keep it up!', "Testing original variables.")
        self.assertEqual(message, 'You are doing a great job, keep it up!', "Testing that the value of message is what was expected.")
        self.assertNotIn("You are doing a great job, keep it up!", self.getEditorText(), "Testing for hardcoding (Don't worry about actual and expected values).")
        

    myTests().main()

.. mchoice:: assess_question2_1_1_4
   :answer_a: ['travel', 'lights', 'moon']
   :answer_b: ['world', 'travel', 'lights']
   :answer_c: ['travel', 'lights']
   :answer_d: ['world', 'travel']
   :correct: c 
   :feedback_a: Cuando tomamos una porción de algo, incluye el elemento en el primer índice y excluye el elemento en el segundo índice.
   :feedback_b: Cuando tomamos una porción de algo, incluye el elemento en el primer índice y excluye el elemento en el segundo índice. Además, Python es un lenguaje basado en índice cero.
   :feedback_c: Sí, python es un lenguaje basado en índice cero y los segmentos incluyen el primer índice y excluyen el segundo.
   :feedback_d: Python es un lenguaje basado en índice cero.
   :practice: T
   :topics: Sequences/TheSliceOperator

   ¿Cuál será la salida para el siguiente código?
   
   .. sourcecode:: python
   
    ls = ['run', 'world', 'travel', 'lights', 'moon', 'baseball', 'sea']
    new = ls[2:4]
    print(new)

.. mchoice:: assess_question2_1_1_5
   :answer_a: string
   :answer_b: integer
   :answer_c: float
   :answer_d: list
   :correct: d
   :feedback_a: No del todo, ¿está cortando o accediendo a un elemento?
   :feedback_b: ¿Qué está sucediendo en la declaración de asignación para m?
   :feedback_c: ¿Qué está sucediendo en la declaración de asignación para m?
   :feedback_d: Sí, un slice devuelve una lista sin importar el tamaño del slice.
   :practice: T
   :topics: Sequences/TheSliceOperator

   ¿Cuál es el tipo de dato de ``m``?
   
   .. sourcecode:: python

    l = ['w', '7', 0, 9]
    m = l[1:2]

.. mchoice:: assess_question2_1_1_6
   :answer_a: string
   :answer_b: integer
   :answer_c: float
   :answer_d: list
   :correct: a
   :feedback_a: Sí, las comillas alrededor del número significan que se trata de una cadena.
   :feedback_b: No del todo, mira de nuevo lo que se extrae.
   :feedback_c: No del todo, mira de nuevo lo que se extrae.
   :feedback_d: No del todo, ¿está cortando o accediendo a un elemento?
   :practice: T
   :topics: Sequences/IndexOperatorWorkingwiththeCharactersofaString

   ¿Cuál es el tipo de dato de ``m``?
   
   .. sourcecode:: python

    l = ['w', '7', 0, 9]
    m = l[1]

.. mchoice:: assess_question2_1_1_7
   :answer_a: string
   :answer_b: integer
   :answer_c: float
   :answer_d: list
   :correct: d
   :feedback_a: No exactamente; .split() devuelve una lista, cada uno de cuyos elementos es una cadena.
   :feedback_b: No del todo, mira de nuevo qué tipos están presentes y cuál es el resultado de .split().
   :feedback_c: No del todo, mira de nuevo qué tipos están presentes y cuál es el resultado de .split().
   :feedback_d: Sí, el método .split() devuelve una lista.
   :practice: T
   :topics: Sequences/SplitandJoin

   ¿Cuál es el tipo de dato de ``x``?
   
   .. sourcecode:: python

    b = "My, what a lovely day"
    x = b.split(',')

.. mchoice:: assess_question2_1_1_8
   :answer_a: string
   :answer_b: integer
   :answer_c: float
   :answer_d: list
   :correct: a
   :feedback_a: Sí, la cadena se divide en una lista, luego se vuelve a unir en una cadena, luego se vuelve a dividir y finalmente se vuelve a unir en una cadena.
   :feedback_b: No del todo, mira de nuevo qué tipos están presentes y cuál es el resultado de .split().
   :feedback_c: No del todo, mira de nuevo qué tipos están presentes y cuál es el resultado de .split().
   :feedback_d: No del todo, piensa en lo que devuelven .split() y .join().
   :practice: T
   :topics: Sequences/SplitandJoin

   ¿Cuál es el tipo de dato de ``a``?
   
   .. sourcecode:: python

    b = "My, what a lovely day"
    x = b.split(',')
    z = "".join(x)
    y = z.split()
    a = "".join(y)

.. activecode:: assess_ac2_1_1_9
    :autograde: unittest
    :language: python
    :practice: T
    :topics: Sequences/CountandIndex

    Escriba el código para determinar cuántos 9 hay en la lista ``nums`` y asigne ese valor a la variable ``how_many``. No use un bucle for para hacer esto.
    ~~~~
    nums = [4, 2, 23.4, 9, 545, 9, 1, 234.001, 5, 49, 8, 9 , 34, 52, 1, -2, 9.1, 4]


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertEqual(how_many, 3, "Testing that how_many is set correctly.")
        self.assertNotIn('for', self.getEditorText(), "Testing that you didn't use a for loop (Don't worry about actual and expected values).")

    myTests().main()

.. activecode:: assess_ac2_1_1_10
    :autograde: unittest
    :language: python
    :practice: T
    :topics: Sequences/CountandIndex

    Escriba el código que utiliza el corte para deshacerse del segundo 8, de modo que aquí solo hayan dos 8 en la lista vinculados a la variable `nums`.
    ~~~~
    nums = [4, 2, 8, 23.4, 8, 9, 545, 9, 1, 234.001, 5, 49, 8, 9 , 34, 52, 1, -2, 9.1, 4]


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertEqual(nums, [4, 2, 8, 23.4, 9, 545, 9, 1, 234.001, 5, 49, 8, 9 , 34, 52, 1, -2, 9.1, 4], "Testing that nums is set correctly.")

    myTests().main()

.. activecode:: access_ac_2_1_1_11
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Sequences/IndexOperatorWorkingwiththeCharactersofaString
   
   Asigne el último elemento de ``lst`` a la variable ``end_elem``. Haga esto para que funcione sin importar cuánto dure.
   ~~~~
   lst = ["hi", "goodbye", "python", "106", "506", 91, ['all', 'Paul', 'Jackie', "UMSI", 1, "Stephen", 4.5], 109, "chair", "pizza", "wolverine", 2017, 3.92, 1817, "account", "readings", "papers", 12, "facebook", "twitter", 193.2, "snapchat", "leaders and the best", "social", "1986", 9, 29, "holiday", ["women", "olympics", "gold", "rio", 21, "2016", "men"], "26trombones"]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(end_elem, lst[-1], "Testing that end_elem has the correct element assigned.")

   myTests().main()

.. activecode:: access_ac_2_1_1_12
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Sequences/Length
   
   Asigne el número de elementos en ``lst`` a la variable ``num_lst``.
   ~~~~
   lst = ["hi", "goodbye", "python", "106", "506", 91, ['all', 'Paul', 'Jackie', "UMSI", 1, "Stephen", 4.5], 109, "chair", "pizza", "wolverine", 2017, 3.92, 1817, "account", "readings", "papers", 12, "facebook", "twitter", 193.2, "snapchat", "leaders and the best", "social", "1986", 9, 29, "holiday", ["women", "olympics", "gold", "rio", 21, "2016", "men"], "26trombones"]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(num_lst, 30, "Testing that num_lst has the correct length assigned.")

   myTests().main()

.. activecode:: assess_ac_2_1_1_13
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Sequences/SplitandJoin

   Cree una variable llamada ``wrds`` y asígnele una lista cuyos elementos sean las palabras en la cadena ``sent``. No te preocupes por la puntuación.
   ~~~~
   sent = "The bicentennial for our university was in 2017"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(wrds, sent.split(), "Testing that wrds has been correctly assigned.")

   myTests().main()
