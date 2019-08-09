..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

.. qnum::
   :prefix: intro-12-
   :start: 1

Evaluación del capítulo
-----------------------

**Revisa tu conocimiento**

.. mchoice:: assess_question1_1_1
   :answer_a: Porque las computadoras son mejores resolviendo problemas.
   :answer_b: Para no tener que resolver el problema tú mismo.
   :answer_c: Para tener una solución general a un problema.
   :answer_d: Porque necesitas un conjunto de instrucciones para seguir.
   :feedback_a: Las computadoras no son necesariamente mejores para resolver problemas, aunque a menudo pueden ser más rápidas que los humanos. Además, los algoritmos se pueden usar para resolver problemas no relacionados con la computadora.
   :feedback_b: Si bien es beneficioso tener un conjunto de instrucciones que otros puedan seguir, esta no es la mejor respuesta. Al crear el algoritmo, resuelve un problema para usted y para los demás.
   :feedback_c: Sí, al crear una solución general, puede expresarla como un programa si lo desea, y luego usar una computadora para automatizar la ejecución.
   :feedback_d: Si bien es beneficioso tener un conjunto de instrucciones, ya que eso es lo que un algoritmo **es**, no es el **por qué** querríamos crear uno.
   :correct: c
   :practice: T
   :topics: GeneralIntro/Algorithms

   ¿Por qué crear un algoritmo?

.. activecode:: assess_question1_1_2
    :language: python
    :autograde: unittest

    Escriba el código para imprimir la frase "Hola mundo".
    ~~~~

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
            self.assertIn("Hello World", self.getOutput(), "Testing output (Don't worry about actual and expected values).")

    myTests().main()
