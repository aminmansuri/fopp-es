..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sequences-5-
   :start: 1

.. index::
    single: len function
    single: function; len
    single: runtime error
    single: negative index
    single: index; negative

Length
======

La función ``len``, cuando se aplica a una cadena, devuelve el número de caracteres en una cadena.

.. activecode:: ac5_5_1
    
    fruit = "Banana"
    print(len(fruit))
    

Para obtener la última letra de una cadena, puede tener la tentación de intentar algo como
esto:

.. activecode:: ac5_5_2
    
    fruit = "Banana"
    sz = len(fruit)
    last = fruit[sz]       # ERROR!
    print(last)

Eso no funcionará. Provoca el error de tiempo de ejecución ``IndexError: string index out of range``. La razón es
que no hay letra en la posición de índice 6 en ``"Banana"``. Desde que comenzamos a contar en cero, al
seis, los índices están numerados del 0 al 5. Para obtener el último carácter, tenemos que restar 1 de la longitud.
Pruébalo en el ejemplo anterior.

.. activecode:: ac5_5_3
    
    fruit = "Banana"
    sz = len(fruit)
    lastch = fruit[sz-1]
    print(lastch)

.. Alternativamente, en Python podemos usar ** índices negativos **, que cuentan hacia atrás desde el
.. final de la cadena. La expresión `` fruta [-1]`` produce la última letra,
.. ``fruit[-2]`` produce el penúltimo, y así sucesivamente. ¡Intentalo!

Normalmente, un programador de Python accederá al último caracter combinando
dos líneas de código desde arriba.

.. sourcecode:: python
    
    lastch = fruit[len(fruit)-1]

Al igual que con las cadenas, la función ``len`` devuelve la longitud de una lista (el número
de artículos en la lista). Sin embargo, como las listas pueden tener elementos que son secuencias (p. Ej., strings),
es importante tener en cuenta que ``len`` solo devuelve la longitud más alta.

.. activecode:: ac5_5_4

    alist =  ["hello", 2.0, 5]
    print(len(alist))
    print(len(alist[0]))

Tenga en cuenta que ``alist[0]`` es la cadena ``"hello"``, que tiene una longitud 5.

**Revisa tu entendimiento**

.. mchoice:: question5_5_1
   :answer_a: 11
   :answer_b: 12
   :correct: b
   :feedback_a: El espacio en blanco cuenta como un caracter.
   :feedback_b: Sí, hay 12 caracteres en el string.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python
   
      s = "python rocks"
      print(len(s))

.. mchoice:: question5_5_2 
   :answer_a: 4
   :answer_b: 5
   :correct: b
   :feedback_a: len devuelve el número real de elementos en la lista, no el valor de índice máximo.
   :feedback_b: Sí, hay 5 artículos en esta lista.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

     alist = [3, 67, "cat", 3.14, False]
     print(len(alist))
     
.. mchoice:: question5_5_3 
   :answer_a: 2
   :answer_b: 3
   :answer_c: 4
   :answer_d: 5
   :correct: b
   :feedback_a: La lista comienza con el segundo elemento de L e incluye todo hasta el último elemento, pero sin incluirlo.
   :feedback_b: Sí, hay 3 artículos en esta lista.
   :feedback_c: La lista comienza con el segundo elemento de L e incluye todo hasta el último elemento, pero sin incluirlo.
   :feedback_d: La lista comienza con el segundo elemento de L e incluye todo hasta el último elemento, pero sin incluirlo.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

     L = [0.34, '6', 'SI106', 'Python', -2]
     print(len(L[1:-1]))   

.. activecode:: ac5_5_5
   :language: python
   :autograde: unittest
   :practice: T

   Asigne el número de elementos en ``lst`` a la variable ``output``.
   ~~~~
   lst = ["hi", "morning", "dog", "506", "caterpillar", "balloons", 106, "yo-yo", "python", "moon", "water", "sleepy", "daffy", 45, "donald", "whiteboard", "glasses", "markers", "couches", "butterfly", "100", "magazine", "door", "picture", "window", ["Olympics", "handle"], "chair", "pages", "readings", "burger", "juggle", "craft", ["store", "poster", "board"], "laptop", "computer", "plates", "hotdog", "salad", "backpack", "zipper", "ring", "watch", "finger", "bags", "boxes", "pods", "peas", "apples", "horse", "guinea pig", "bowl", "EECS"]
   
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(output, 52, "Testing that output value is assigned to correct value.")

   myTests().main()
