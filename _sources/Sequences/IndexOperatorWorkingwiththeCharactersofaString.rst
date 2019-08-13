..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sequences-3-
   :start: 1

.. index:: 
   single: [ ]; string indexing
   index; string
   string; index

Operador Index: trabajar con los caracteres de una cadena
--------------------------------------------------------------

El **operador de indexación** (Python usa corchetes para encerrar el índice)
selecciona un solo carácter de una cadena. Se accede a los caracteres por su posición o
valor del índice. Por ejemplo, en la cadena que se muestra a continuación, los 14 caracteres están indexados de izquierda a derecha
de la posición 0 a la posición 13.

.. image:: Figures/indexvalues.png
   :alt: index values

También se da el caso de que las posiciones se nombran de derecha a izquierda usando números negativos donde -1 es
el índice más a la derecha y así sucesivamente. Tenga en cuenta que el carácter en el índice 6 (o -8) es el carácter en blanco.

.. activecode:: ac5_3_1
    
    school = "Luther College"
    m = school[2]
    print(m)
    
    lastchar = school[-1]
    print(lastchar)

La expresión ``school[2]`` selecciona el carácter en el índice 2 de ``school`` y crea una nueva
cadena que contiene solo este carácter. La variable ``m`` se refiere al resultado.

La letra en el índice cero de ``"Luther College"`` es ``L``. Entonces en
posición ``[2]`` tenemos la letra ``t``.

Si desea la letra cero-eth de una cadena, simplemente ponga 0 o cualquier expresión
con el valor 0, entre paréntesis. Puede darle una oportunidad

La expresión entre paréntesis se llama **index**. Un índice especifica un miembro
de una colección ordenada. En este caso, la colección de caracteres en la cadena. El índice
*indica* qué caracter quieres. Puede ser cualquier número entero o
expresión, siempre que se evalúe como un valor de índice válido.

Tenga en cuenta que la indexación devuelve una *cadena* --- Python no tiene ningún tipo especial para un solo carácter.
Es solo una cadena de longitud 1.

Operador de índice: acceso a elementos de una lista o tupla
===========================================================

La sintaxis para acceder a los elementos de una lista o tupla es la misma que la sintaxis para
accediendo a los caracteres de una cadena. Usamos el operador de índice (``[]`` --no para
confundirse con una lista vacía). La expresión dentro de los corchetes especifica
el índice. Recuerde que los índices comienzan en 0. Se puede usar cualquier expresión entera
como índice y al igual que con las cadenas, los valores de índice negativos localizarán elementos de la derecha en su lugar
de desde la izquierda.

Cuando decimos el primer, tercer o enésimo carácter de una secuencia, generalmente queremos decir contar de la manera habitual, comenzando con 1. El enésimo carácter y el carácter AT INDEX n son diferentes entonces: el enésimo carácter está en el índice n-1. ¡Asegúrate de tener claro lo que quieres decir!

Intente predecir lo que se imprimirá con el siguiente código y luego ejecútelo para verificar su
predicción. (En realidad, es una buena idea hacerlo siempre con los ejemplos de código.
aprenderá mucho más si se obliga a hacer una predicción antes de ver la salida)

.. activecode:: ac5_3_2
    
    numbers = [17, 123, 87, 34, 66, 8398, 44]
    print(numbers[2])
    print(numbers[9-8])
    print(numbers[-2])


.. activecode:: ac5_3_3

    prices = (1.99, 2.00, 5.50, 20.95, 100.98)
    print(prices[0])
    print(prices[-1])
    print(prices[3-5])

**Revisa tu entendimiento**

.. mchoice:: question5_3_1
   :answer_a: t
   :answer_b: h
   :answer_c: c
   :answer_d: Error, no puede usar el operador [ ] con una cadena.
   :correct: b
   :feedback_a: Las ubicaciones de índice no comienzan con 1, comienzan con 0.
   :feedback_b: Sí, las ubicaciones de índice comienzan con 0.
   :feedback_c: s[-3] devolvería c, contando de derecha a izquierda.
   :feedback_d: [ ] es el operador de índice.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
      
   .. code-block:: python
   
      s = "python rocks"
      print(s[3])

.. mchoice:: question5_3_2
   :answer_a: tr
   :answer_b: to
   :answer_c: ps
   :answer_d: nn
   :answer_e: Error, no puede usar el operador [ ] con el operador +.
   :correct: b
   :feedback_a: Casi, t está en la posición 2, contando de izquierda a derecha a partir de 0; pero r está en -5, contando de derecha a izquierda a partir de -1.
   :feedback_b: Para -4 cuentas de derecha a izquierda, comenzando con -1.
   :feedback_c: p está en la ubicación 0, no en 2.
   :feedback_d: n está en la ubicación 5, no en la 2.
   :feedback_e: El operador [ ] devuelve una cadena que se puede concatenar con otra cadena.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python
   
      s = "python rocks"
      print(s[2] + s[-4])

.. mchoice:: question5_3_3
   :answer_a: [ ]
   :answer_b: 3.14
   :answer_c: False
   :answer_d: "dog"
   :correct: b
   :feedback_a: La lista vacía está en el índice 4.
   :feedback_b: Sí, 3.14 está en el índice 5 ya que comenzamos a contar en 0 y las sublistas cuentan como un elemento.
   :feedback_c: Falso está en el índice 6.
   :feedback_d: Mire nuevamente, el elemento en el índice 3 es una lista. Esta lista solo cuenta como un elemento.
   :practice: T
   
   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

     alist = [3, 67, "cat", [56, 57, "dog"], [ ], 3.14, False]
     print(alist[5])

.. activecode:: ac5_3_4
   :language: python
   :autograde: unittest
   :practice: T

   Asigne el valor del elemento 34 de ``lst`` a la variable ``output``.
   ~~~~
   lst = ["hi", "morning", "dog", "506", "caterpillar", "balloons", 106, "yo-yo", "python", "moon", "water", "sleepy", "daffy", 45, "donald", "whiteboard", "glasses", "markers", "couches", "butterfly", "100", "magazine", "door", "picture", "window", ["Olympics", "handle"], "chair", "pages", "readings", "burger", "juggle", "craft", ["store", "poster", "board"], "laptop", "computer", "plates", "hotdog", "salad", "backpack", "zipper", "ring", "watch", "finger", "bags", "boxes", "pods", "peas", "apples", "horse", "guinea pig", "bowl", "EECS"]
   
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(output, "laptop", "Testing that output value is assigned to correct value.")

   myTests().main()

.. activecode:: ac5_3_5
   :language: python
   :autograde: unittest
   :practice: T
   
   Asigne el valor del elemento 23 de ``l`` a la variable ``checking``.
   ~~~~
   l = ("hi", "goodbye", "python", "106", "506", 91, ['all', 'Paul', 'Jackie', "UMSI", 1, "Stephen", 4.5], 109, "chair", "pizza", "wolverine", 2017, 3.92, 1817, "account", "readings", "papers", 12, "facebook", "twitter", 193.2, "snapchat", "leaders and the best", "social", "1986", 9, 29, "holiday", ["women", "olympics", "gold", "rio", 21, "2016", "men"], "26trombones")

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(checking, "leaders and the best", "Testing that checking has the correct element assigned.")

   myTests().main()

.. activecode:: ac5_3_6
   :language: python
   :autograde: unittest
   :practice: T

   Asigne el valor del último carácter de ``lst`` a la variable ``output``. Haga esto para que la longitud de lst no importe.
   ~~~~
   lst = "Every chess or checkers game begins from the same position and has a finite number of moves that can be played. While the number of possible scenarios and moves is quite large, it is still possible for computers to calculate that number and even be programmed to respond well against a human player..."
   
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testThree(self):
         self.assertEqual(output, ".", "Testing that output value is assigned to correct value.")

   myTests().main()

.. note::
   ¿Por qué el conteo comienza en 0 yendo de izquierda a derecha, pero en -1 yendo de derecha a izquierda? Bueno, la indexación que comienza en 0
   tiene una larga historia en ciencias de la computación que tiene que ver con algunos detalles de implementación de bajo nivel que no veremos.
   Para indexar de derecha a izquierda, puede parecer natural hacer lo análogo
   y comenzar en -0. Desafortunadamente, -0 es lo mismo que 0, por lo que s[-0] no puede ser el último elemento. Recuerda, ¿nosotros
   dijimos que los lenguajes de programación son lenguajes formales donde los detalles importan y
   todo se toma literalmente?
