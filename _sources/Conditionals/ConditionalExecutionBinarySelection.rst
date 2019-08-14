..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: condition-6-
   :start: 1

.. index:: heading, body, selection, if, else, pass, compound statement, conditional statement
   statement; if
   statement; pass
    
Ejecución condicional: selección binaria
----------------------------------------

.. video:: binaryselection
   :controls:
   :thumb: ../_static/binaryselection.png

   http://media.interactivepython.org/thinkcsVideos/binaryselection.mov
   http://media.interactivepython.org/thinkcsVideos/binaryselection.webm


Para escribir programas útiles, casi siempre necesitamos la capacidad de verificar
condiciones y cambiar el comportamiento del programa en consecuencia. **Declaraciones de selección**, a veces
también conocido como **declaraciones condicionales**, danos esta habilidad. La forma más simple de selección es la declaración **if statement**.
Esto a veces se conoce como **selección binaria** ya que hay dos posibles rutas de ejecución.

.. activecode:: ac7_6_1

    x = 15

    if x % 2 == 0:
        print(x, "incluso")
    else:
        print(x, "es impar")


La sintaxis para una declaración ``if`` se ve así:

.. sourcecode:: python

    if BOOLEAN EXPRESSION:
        STATEMENTS_1        # se ejecuta si la condición se evalúa como True
    else:
        STATEMENTS_2        # se ejecuta si la condición se evalúa como False

La expresión boolean después de la declaración ``if`` se llama **condición**.
Si es verdadero, se ejecutan las declaraciones sangradas. Si no, entonces las declaraciones
sangradas bajo la cláusula ``else`` ejecutarse.

.. sidebar::  Diagrama de flujo de una declaración **if** con un **else**

   .. image:: Figures/flowchart_if_else.png



Al igual que con la definición de función del último capítulo y otros compuestos
declaraciones como ``for``, la declaración ``if`` consiste en una línea de encabezado y un cuerpo. El encabezado de
la línea comienza con la palabra clave ``if`` seguida de una *expresión boolean* y termina con
dos puntos (:).

Las siguientes declaraciones sangradas se denominan **bloque**. La primera
declaración sin sangría marca el final del bloque.

Cada una de las declaraciones dentro del primer bloque de declaraciones se ejecutan en orden si el valor boolean
de la expresión se evalúa como ``True``. El primer bloque completo de declaraciones
se omite si la expresión boolean se evalúa como ``False``, y en su lugar
todas las declaraciones bajo la cláusula ``else`` se ejecutan.

No hay límite en el número de declaraciones que pueden aparecer bajo las dos cláusulas de una
declaración ``if``, pero debe haber al menos una declaración en cada bloque.


**Revisa tu entendimiento**

.. mchoice:: question7_6_1
   :answer_a: Solo uno.
   :answer_b: Cero o más.
   :answer_c: Uno o más.
   :answer_d: Uno o más, y cada uno debe contener el mismo número.
   :correct: c
   :feedback_a: Cada bloque también puede contener más de uno.
   :feedback_b: Cada bloque debe contener al menos una declaración.
   :feedback_c: Sí, un bloque debe contener al menos una declaración y puede tener muchas declaraciones.
   :feedback_d: Los bloques pueden contener diferentes números de declaraciones.
   :practice: T

   ¿Cuántas líneas de código pueden aparecer en el bloque de código sangrado debajo de las líneas if y else en un condicional?

.. mchoice:: question7_6_2
   :answer_a: TRUE
   :answer_b: FALSE
   :answer_c: TRUE en una línea y FALSE en la siguiente
   :answer_d: Nada será impreso
   :correct: b
   :feedback_a: El bloque if imprime TRUE, que solo se ejecuta si el condicional (en este caso, 4+5 == 10) es verdadero. En este caso 5+4 no es igual a 10.
   :feedback_b: Como 4+5==10 se evalúa como False, Python omitirá el bloque if y ejecutará la declaración en el bloque else.
   :feedback_c: Python nunca imprimirá tanto TRUE como FALSE porque solo ejecutará uno de los bloques if o block, pero no ambos.
   :feedback_d: Python siempre ejecutará el bloque if (si la condición es verdadera) o el bloque else (si la condición es falsa). Nunca saltaría sobre ambos bloques.
   :practice: T

   ¿Qué imprime el siguiente código? (elija de la salida a, b, c o nada)

   .. code-block:: python

     if (4 + 5 == 10):
         print("TRUE")
     else:
         print("FALSE")

.. mchoice:: question7_6_3
   :answer_a: Salida a
   :answer_b: Salida b
   :answer_c: Salida c
   :answer_d: Salida d
   :correct: c
   :feedback_a: Aunque TRUE se imprime después de que se completa la instrucción if-else, ambos bloques dentro de la instrucción if-else también imprimen algo. En este caso, Python debería haber omitido ambos bloques en la instrucción if-else, lo que nunca haría.
   :feedback_b: Debido a que hay un TRUE impreso después de que finaliza la instrucción if-else, Python siempre imprimirá TRUE como la última instrucción.
   :feedback_c: Python imprimirá FALSE desde dentro del bloque else (porque 5+4 no es igual a 10), y luego imprimirá TRUE después de que se complete la instrucción if-else.
   :feedback_d: Para imprimir estas tres líneas, Python tendría que ejecutar ambos bloques en la instrucción if-else, lo que nunca puede hacer.
   :practice: T

   ¿Qué imprime el siguiente código?

   .. code-block:: python

     if (4 + 5 == 10):
         print("TRUE")
     else:
         print("FALSE")
     print("TRUE")

   ::

      a. TRUE

      b.
         TRUE
         FALSE

      c.
         FALSE
         TRUE
      d.
         TRUE
         FALSE
         TRUE

.. activecode:: ac7_6_2
   :language: python
   :autograde: unittest
   :practice: T

   Escriba el código para asignar la cadena ``"You can apply to SI!"`` A ``output`` *if* la cadena ``"SI 106"`` está en la lista ``courses``. Si no está en ``courses``, asigne el valor ``"Take SI 106!"`` A la variable ``output``.
   ~~~~
   courses = ["ENGR 101", "SI 110", "ENG 125", "SI 106", "CHEM 130"]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(output, "You can apply to SI!", "Testing that output has the correct value, given the courses list provided")
         self.assertIn("if", self.getEditorText(), "Testing output (Don't worry about actual and expected values).")

   myTests().main()

.. activecode:: ac7_6_4
   :language: python
   :autograde: unittest
   :practice: T

   Cree una variable, ``b``, y asígnele el valor de ``15``. Luego, escriba el código para ver si el valor ``b`` es mayor que el de ``a``. Si es así, el valor de ``a`` debe multiplicarse por 2. Si el valor de ``b`` es menor o igual que ``a``, no debe suceder nada. Finalmente, cree la variable ``c`` y asígnele el valor de la suma de ``a`` y ``b``.
   ~~~~
   a = 20
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwoA(self):
         self.assertEqual(a, 20, "Testing that a has the correct value.")

      def testTwoB(self):
         self.assertEqual(c, 35, "Testing that c has the correct value.")

   myTests().main()
