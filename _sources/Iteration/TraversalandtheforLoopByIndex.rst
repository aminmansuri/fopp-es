..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _for_by_index:

.. qnum::
   :prefix: moreiter-6-
   :start: 1

Recorrido y bucle ``for``: Por índice
--------------------------------------

También es posible iterar a través de los *índices* de una cadena o secuencia. El bucle ``for`` puede usarse para
iterar sobre estas posiciones. Estas posiciones se pueden usar junto con el operador de indexación para acceder al individuo
caracteres en la cadena. Podemos usar **Enumerate**, una función incorporada de Python, para facilitar este proceso porque
nos permite recorrer algo y tener un contador automático.

.. activecode:: ac14_6_1
 
   for counter, item in enumerate(['apple', 'pear', 'apricot', 'cherry', 'peach']):
       print(counter, item)

Al usar la función de enumerar, podemos imprimir un contador que nos indica la posición de un elemento en una lista. Podríamos hacer
esto nosotros mismos, pero esto nos salva de tener que hacer eso. Las posiciones de índice en la lista son 0, 1, 2, 3 y 4. Esto es
exactamente la misma secuencia de enteros que se almacenan en ``contador`` cada vez que se itera el ciclo. La primera vez a través del
bucle, ``counter`` será 0 y se imprimirá "apple". Luego, ``contador`` se reasignará a 1 y se mostrará "pera". Esto continuará
hasta que la lista haya finalizado, de modo que el valor final para ``contador`` sea 4 y el valor final de ``elemento`` sea "durazno".

Convenientemente, también podemos usar la función ``range`` para generar automáticamente los índices de los caracteres.

.. activecode:: ac14_6_4

   x = range(5)
   print(type(x))
   print(x)

Para que la iteración sea más general, podemos usar la función ``len`` para proporcionar el límite de ``range``. Esto es
Un patrón muy común para atravesar cualquier secuencia por posición. Asegúrese de entender por qué se comporta la función de rango
correctamente cuando se usa ``len`` de la cadena como su valor de parámetro.

.. activecode:: ac14_6_5

   fruit = ['apple', 'pear', 'apricot', 'cherry', 'peach']
   for n in range(len(fruit)):
       print(n, fruit[n])

También puede notar que la iteración por posición le permite al programador controlar la dirección del recorrido cambiando
La secuencia de valores de índice.

.. codelens:: clens14_6_2
    :python: py3

    fruit = ['apple', 'pear', 'apricot', 'cherry', 'peach']
    for idx in [0, 2, 4, 3, 1]:
        print(fruit[idx])

**Revisa tu entendimiento**

.. mchoice:: question14_6_1
   :answer_a: 0
   :answer_b: 1
   :answer_c: 2
   :answer_d: 3
   :answer_e: 6
   :correct: d
   :feedback_a: idx % 2 is 0 siempre que idx sea par
   :feedback_b: idx % 2 is 0 siempre que idx sea par
   :feedback_c: idx % 2 is 0 siempre que idx sea par
   :feedback_d: idx % 2 is 0 siempre que idx sea par
   :feedback_e: idx % 2 is 0 siempre que idx sea par
   :practice: T

   ¿Cuántas veces se imprime la letra p en las siguientes afirmaciones?
   
   .. code-block:: python

      s = "python"
      for idx in range(len(s)):
         print(s[idx % 2])
